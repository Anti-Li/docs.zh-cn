---
title: 连接字符串语法
ms.date: 05/22/2018
ms.assetid: 0977aeee-04d1-4cce-bbed-750c77fce06e
ms.openlocfilehash: 1df49a9ed5d45a1a1ee50145ff036c98ec72cca8
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/24/2018
ms.locfileid: "34472745"
---
# <a name="connection-string-syntax"></a>连接字符串语法
每个 .NET Framework 数据提供程序都有一个继承自 `Connection` 的 <xref:System.Data.Common.DbConnection> 对象，以及一个提供程序特定的 <xref:System.Data.Common.DbConnection.ConnectionString%2A> 属性。 每个提供程序的特定连接字符串语法记录在其 `ConnectionString` 属性中。 下表列出了 .NET Framework 中包含的四个数据提供程序。  
  
|.NET Framework data provider — .NET Framework 数据提供程序|描述|  
|----------------------------------|-----------------|  
|<xref:System.Data.SqlClient>|提供 Microsoft SQL Server 的数据访问。 有关连接字符串语法的更多信息，请参见 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A>。|  
|<xref:System.Data.OleDb>|提供对使用 OLE DB 公开的数据源中的数据的访问。 有关连接字符串语法的更多信息，请参见 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A>。|  
|<xref:System.Data.Odbc>|提供对使用 ODBC 公开的数据源中数据的访问。 有关连接字符串语法的更多信息，请参见 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A>。|  
|<xref:System.Data.OracleClient>|提供对 Oracle 8.1.7 或更高版本中数据的访问。 有关连接字符串语法的更多信息，请参见 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。|  
  
## <a name="connection-string-builders"></a>连接字符串生成器  
 ADO.NET 2.0 为 .NET Framework 数据提供程序引入了以下连接字符串生成器。  
  
-   <xref:System.Data.SqlClient.SqlConnectionStringBuilder>  
  
-   <xref:System.Data.OleDb.OleDbConnectionStringBuilder>  
  
-   <xref:System.Data.Odbc.OdbcConnectionStringBuilder>  
  
-   <xref:System.Data.OracleClient.OracleConnectionStringBuilder>  
  
 连接字符串生成器使你可以在运行时构造具有有效语法的连接字符串，从而不必在代码中手动串联连接字符串值。 有关详细信息，请参阅[连接字符串生成器](../../../../docs/framework/data/adonet/connection-string-builders.md)。  

## <a name="windows-authentication"></a>Windows 身份验证  
 我们建议使用 Windows 身份验证 (有时称为*集成安全性*) 连接到支持它的数据源。 连接字符串中使用的语法根据提供程序的不同而不同。 下表演示用于 .NET Framework 数据提供程序的 Windows 身份验证语法。  
  
|提供程序|语法|  
|--------------|------------|  
|`SqlClient`|`Integrated Security=true;`<br /><br /> `-- or --`<br /><br /> `Integrated Security=SSPI;`|  
|`OleDb`|`Integrated Security=SSPI;`|  
|`Odbc`|`Trusted_Connection=yes;`|  
|`OracleClient`|`Integrated Security=yes;`|  
  
> [!NOTE]
>  `Integrated Security=true` 用于 `OleDb` 提供程序时会引发异常。  
  
## <a name="sqlclient-connection-strings"></a>SqlClient 连接字符串  
<xref:System.Data.SqlClient.SqlConnection> 连接字符串的语法记录在 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 属性中。 您可以使用 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 属性来获取或设置 SQL Server 数据库的连接字符串。 如果您需要连接到早期版本的 SQL Server，则必须使用适用于 OleDb 的 .NET Framework 数据提供程序 (<xref:System.Data.OleDb>)。 大多数连接字符串关键字还会在 <xref:System.Data.SqlClient.SqlConnectionStringBuilder> 中映射为属性。  

> [!IMPORTANT]
>  默认设置`Persist Security Info`关键字是`false`。 如果将其设置为 `true` 或 `yes`，则允许在打开连接后通过连接获取安全敏感信息（包括用户 ID 和密码）。 保留`Persist Security Info`设置为`false`以确保不受信任的源没有访问敏感的连接字符串信息。  

### <a name="windows-authentication-with-sqlclient"></a>使用 SqlClient 的 Windows 身份验证 
 每个以下形式的语法使用 Windows 身份验证连接到**AdventureWorks**的本地服务器上的数据库。  
  
```  
"Persist Security Info=False;Integrated Security=true;  
    Initial Catalog=AdventureWorks;Server=MSSQL1"  
"Persist Security Info=False;Integrated Security=SSPI;  
    database=AdventureWorks;server=(local)"  
"Persist Security Info=False;Trusted_Connection=True;  
    database=AdventureWorks;server=(local)"  
```  
  
### <a name="sql-server-authentication-with-sqlclient"></a>使用 SqlClient 的 SQL Server 身份验证   
 Windows 身份验证是用于连接到 SQL Server 的首选方法。 但是，如果需要 SQL Server 身份验证，请使用下列语法来指定用户名和密码。 在此示例中，星号用来表示有效用户名和密码。  
  
```  
"Persist Security Info=False;User ID=*****;Password=*****;Initial Catalog=AdventureWorks;Server=MySqlServer"  
```  

当你连接到 Azure SQL 数据库或 Azure SQL 数据仓库，并提供格式中的登录名`user@servername`，请确保`servername`于此登录中的值与提供的值匹配`Server=`。

> [!NOTE]
>  Windows 身份验证优先于 SQL Server 登录。 如果您同时指定 Integrated Security=true 以及用户名和密码，将忽略用户名和密码，而使用 Windows 身份验证。  

### <a name="connect-to-a-named-instance-of-sql-server"></a>连接到 SQL Server 的命名实例
若要连接到 SQL Server 的命名实例，使用*服务器名称 \ 实例名称*语法。  
  
```  
Data Source=MySqlServer\MSSQL1;"  
```  
 
在生成连接字符串时，您还可以将 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A> 的 `SqlConnectionStringBuilder` 属性设置为实例名。 <xref:System.Data.SqlClient.SqlConnection.DataSource%2A> 对象的 <xref:System.Data.SqlClient.SqlConnection> 属性是只读的。  
  
### <a name="type-system-version-changes"></a>类型系统版本更改  
 `Type System Version`中的关键字<xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType>指定 SQL Server 类型的客户端表示形式。 有关 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=nameWithType> 关键字的更多信息，请参见 `Type System Version`。  
  
## <a name="connecting-and-attaching-to-sql-server-express-user-instances"></a>连接并附加到 SQL Server Express 用户实例  
 用户实例是 SQL Server Express 中的一个功能。 它们允许以最低权限的本地 Windows 帐户运行的用户附加并运行 SQL Server 数据库，而无需具有管理权限。 使用用户 Windows 凭据执行用户实例，而不是作为服务执行用户实例。  
  
 使用用户实例的详细信息，请参阅[SQL Server Express 用户实例](../../../../docs/framework/data/adonet/sql/sql-server-express-user-instances.md)。  
  
## <a name="using-trustservercertificate"></a>使用 TrustServerCertificate  
 `TrustServerCertificate`关键字无效，仅当连接到 SQL Server 实例使用有效的证书。 当 `TrustServerCertificate` 设置为 `true` 时，传输层将使用 SSL 来加密通道并跳过证书链以验证信任。  
  
```  
"TrustServerCertificate=true;"   
```  
  
> [!NOTE]
>  如果 `TrustServerCertificate` 设置为 `true` 并已启动加密，将使用对服务器指定的加密级别，即使 `Encrypt` 在连接字符串中被设置为 `false`。 否则连接将会失败。  
  
### <a name="enabling-encryption"></a>启用加密  
 若要启用加密证书不设置后在服务器上，**强制协议加密**和**信任服务器证书**选项必须设置在 SQL Server 配置管理器中。 在此情况下，如果未向服务器提供可验证的证书，加密将使用未经验证的自签名服务器证书。  
  
 应用程序设置无法降低在 SQL Server 中配置的安全级别，但可以增强安全级别。 应用程序可以通过设置请求加密`TrustServerCertificate`和`Encrypt`关键字`true`，从而保证，加密进行，即使尚未设置服务器证书和**强制协议加密**尚未配置客户端。 但是，如果未在客户端配置中启用 `TrustServerCertificate`，则仍需要提供服务器证书。  
  
 下表描述了各种情况。  
  
|“强制协议加密”客户端设置|“信任服务器证书”客户端设置|“密加/使用数据加密”连接字符串/属性|“信任服务器证书”连接字符串/特性|结果|  
|----------------------------------------------|---------------------------------------------|-------------------------------------------------------------------|-----------------------------------------------------------|------------|  
|No|不可用|否（默认值）|忽略|不加密。|  
|No|不可用|是|否（默认值）|只有在具有可验证的服务器证书的情况下才能进行加密，否则连接尝试将失败。|  
|No|不可用|是|是|加密始终发生，但可能会使用自签名的服务器证书。|  
|是|No|忽略|忽略|只有在可验证服务器证书，则会发生加密否则，连接尝试失败。|  
|是|是|否（默认值）|忽略|加密始终发生，但可能会使用自签名的服务器证书。|  
|是|是|是|否（默认值）|只有在可验证服务器证书，则会发生加密否则，连接尝试失败。|  
|是|是|是|是|加密始终发生，但可能会使用自签名的服务器证书。|  
  
 有关详细信息，请参阅[使用未经验证的加密](http://go.microsoft.com/fwlink/?LinkId=120500)SQL Server 联机丛书中。  
  
## <a name="oledb-connection-strings"></a>OleDb 连接字符串  
 通过 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A> 的 <xref:System.Data.OleDb.OleDbConnection> 属性，您可以获取或设置 OLE DB 数据源（如 Microsoft Access）的连接字符串。 也可以使用 `OleDb` 类在运行时创建一个 <xref:System.Data.OleDb.OleDbConnectionStringBuilder> 连接字符串。  
  
### <a name="oledb-connection-string-syntax"></a>OleDb 连接字符串语法  
 必须为 <xref:System.Data.OleDb.OleDbConnection> 连接字符串指定提供程序名称。 下列连接字符串使用 Jet 提供程序连接到 Microsoft Access 数据库。 请注意，如果数据库未受到保护（默认值），可选择 `User ID` 和 `Password` 关键字。  
  
```   
Provider=Microsoft.Jet.OLEDB.4.0; Data Source=d:\Northwind.mdb;User ID=Admin;Password=;   
```  
  
 如果使用用户级安全保护 Jet 数据库，则必须提供工作组信息文件 (.mdw) 的位置。 工作组信息文件用于验证连接字符串中显示的凭据。  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=d:\Northwind.mdb;Jet OLEDB:System Database=d:\NorthwindSystem.mdw;User ID=*****;Password=*****;  
```  
  
> [!IMPORTANT]
>  可以提供的连接信息**OleDbConnection**在通用数据链接 (UDL) 文件; 但是，应避免这样做。 UDL 文件未加密，会以明文形式公开连接字符串信息。 因为 UDL 文件对您的应用程序来说是一个基于文件的外部资源，所以无法使用 .NET Framework 保护该文件。 不支持 UDL 文件**SqlClient**。  
  
### <a name="using-datadirectory-to-connect-to-accessjet"></a>使用 DataDirectory 连接到 Access/Jet  
 `DataDirectory` 不是 `SqlClient` 独占的。 它还可以用于 <xref:System.Data.OleDb> 和 <xref:System.Data.Odbc> .NET 数据提供程序。 下面的 <xref:System.Data.OleDb.OleDbConnection> 字符串示例演示连接到应用程序 app_data 文件夹中的 Northwind.mdb 所需的语法。 系统数据库 (System.mdw) 也存储在该位置。  
  
```  
"Provider=Microsoft.Jet.OLEDB.4.0;  
Data Source=|DataDirectory|\Northwind.mdb;  
Jet OLEDB:System Database=|DataDirectory|\System.mdw;"  
```  
  
> [!IMPORTANT]
>  如果 Access/Jet 数据库未受到保护，则不需要在连接字符串中指定系统数据库的位置。 默认情况下安全性为关，所有用户可作为内置管理员用户使用空白密码进行连接。 即使在正确实现用户级安全时，Jet 数据库仍很容易受到攻击。 由于 Access/Jet 数据库的基于文件的安全性架构存在固有弱点，因此不建议在 Access/Jet 数据库中存储敏感信息。  
  
### <a name="connecting-to-excel"></a>连接到 Excel  
 Microsoft Jet 提供程序用于连接到 Excel 工作簿。 下列连接字符串中的 `Extended Properties` 关键字会设置特定于 Excel 的属性。 “HDR=Yes;”指示第一行包含列名称，但不包含数据；“IMEX=1;”指示驱动程序始终将“intermixed”数据列作为文本进行读取。  
  
```  
Provider=Microsoft.Jet.OLEDB.4.0;Data Source=D:\MyExcel.xls;Extended Properties=""Excel 8.0;HDR=Yes;IMEX=1""  
```  
  
 请注意，`Extended Properties` 所需的双引号字符还必须包含在双引号中。  
  
### <a name="data-shape-provider-connection-string-syntax"></a>Data Shape 提供程序连接字符串语法  
 在使用 Microsoft Data Shape 提供程序时，请同时使用 `Provider` 和 `Data Provider` 关键字。 下面的示例使用 Shape 提供程序连接到 SQL Server 的本地实例。  
  
```  
"Provider=MSDataShape;Data Provider=SQLOLEDB;Data Source=(local);Initial Catalog=pubs;Integrated Security=SSPI;"   
```  
  
## <a name="odbc-connection-strings"></a>Odbc 连接字符串  
 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A> 的 <xref:System.Data.Odbc.OdbcConnection> 属性允许您获取或设置 OLE DB 数据源的连接字符串或。 <xref:System.Data.Odbc.OdbcConnectionStringBuilder> 也支持 Odbc 连接字符串。  
  
 下列连接字符串使用 Microsoft 文本驱动程序。  
  
```  
Driver={Microsoft Text Driver (*.txt; *.csv)};DBQ=d:\bin  
```  
  
### <a name="using-datadirectory-to-connect-to-visual-foxpro"></a>使用 DataDirectory 连接到 Visual FoxPro  
 下面的 <xref:System.Data.Odbc.OdbcConnection> 连接字符串示例演示如何使用 `DataDirectory` 连接到 Microsoft Visual FoxPro 文件。  
  
```  
"Driver={Microsoft Visual FoxPro Driver};  
SourceDB=|DataDirectory|\MyData.DBC;SourceType=DBC;"  
```  
  
## <a name="oracle-connection-strings"></a>Oracle 连接字符串  
 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A> 的 <xref:System.Data.OracleClient.OracleConnection> 属性允许您获取或设置 OLE DB 数据源的连接字符串或。 <xref:System.Data.OracleClient.OracleConnectionStringBuilder> 也支持 Oracle 连接字符串。  
  
```  
Data Source=Oracle9i;User ID=*****;Password=*****;  
```  
  
 有关 ODBC 连接字符串语法的更多信息，请参见 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A>。  
  
## <a name="see-also"></a>请参阅  
 [连接字符串](../../../../docs/framework/data/adonet/connection-strings.md)  
 [连接到数据源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [ADO.NET 托管提供程序和数据集开发人员中心](http://go.microsoft.com/fwlink/?LinkId=217917)
