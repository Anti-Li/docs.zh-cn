---
title: 类型缩写 (F#)
description: '了解有关 F # 类型缩写为类型以使代码更易于读取指定的更有意义的名称。'
ms.date: 05/16/2016
ms.openlocfilehash: e222caa41a20a64071c94cffea6ea7b2bec8eb22
ms.sourcegitcommit: ff1d40507b3eb6e2185478e37c66c66be6de46f1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/11/2018
ms.locfileid: "34058947"
---
# <a name="type-abbreviations"></a>类型缩写

A*类型缩写*是的别名或类型的备用名称。

## <a name="syntax"></a>语法

```fsharp
type [accessibility-modifier] type-abbreviation = type-name
```

## <a name="remarks"></a>备注
类型缩写可用于为指定类型的更有意义的名称，以使代码易于阅读。 你还可以使用它们创建为原本不方便，写出的类型的易于使用的名称。此外，你可以使用类型缩写要更加轻松地更改基础类型，而无需更改使用类型的所有代码。 下面是简单类型缩写。

类型缩写的可访问性默认为`public`。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2301.fs)]

类型缩写可以包含泛型参数，如以下代码所示。

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2302.fs)]

在前面的代码中，`Transform`是表示采用单个参数的任何类型的函数的类型缩写，将返回相同类型的单个值。

在.NET Framework MSIL 代码中，不会保留类型缩写。 因此，当使用来自另一种.NET Framework 语言的 F # 程序集时，你必须使用类型缩写的基础类型名称。

类型缩写还可上的度量单位。 有关详细信息，请参阅[度量单位](units-of-measure.md)。


## <a name="see-also"></a>请参阅
[F# 语言参考](index.md)

