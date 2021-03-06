---
title: 如何：向三维模型应用绘图
ms.date: 03/30/2017
helpviewer_keywords:
- drawings [WPF], applying to 3-D models
- 3-D models [WPF], applying drawings to
ms.assetid: 68357577-b7fc-446e-8be9-a8cc7df3a350
ms.openlocfilehash: 26a84d963cac3b5c23617bfaa23279021e29c07a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559052"
---
# <a name="how-to-apply-a-drawing-to-a-3-d-model"></a>如何：向三维模型应用绘图
此示例演示如何使用<xref:System.Windows.Media.DrawingBrush>作为<xref:System.Windows.Media.Media3D.Material>应用于[!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)]模型。  
  
 下面的代码定义<xref:System.Windows.Media.DrawingGroup>作为内容<xref:System.Windows.Media.DrawingBrush>。  <xref:System.Windows.Media.DrawingBrush>被设置为<xref:System.Windows.Media.Media3D.DiffuseMaterial.Brush%2A>属性<xref:System.Windows.Media.Media3D.DiffuseMaterial>应用于[!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)]平面。  
  
 **注意：** 通常是需要定义复杂的对象和类似如下绘图的值作为可重复使用和简化你的代码的资源。 请参阅[XAML 资源](../../../../docs/framework/wpf/advanced/xaml-resources.md)有关详细信息。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialinline1)]  
  
## <a name="example"></a>示例  
 下面的代码演示了整个示例。  
  
 [!code-xaml[3DGallery_snip#ApplyDrawingToMaterialExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ApplyDrawingToMaterialExample.xaml#applydrawingtomaterialexamplewholepage)]  
  
## <a name="see-also"></a>请参阅  
 [XAML 资源](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [创建 3D 场景](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Drawing 对象概述](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [3D 图形概述](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
