---
title: 如何：对 SolidColorBrush 的颜色或不透明度进行动画处理
ms.date: 03/30/2017
helpviewer_keywords:
- SolidColorBrush [WPF], animating color of
- colors [WPF], animating
- opacity [WPF], animating
- animation [WPF], color of SolidColorBrush
- animation [WPF], opacity of SolidColorBrush
- SolidColorBrush [WPF], animating opacity of
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
ms.openlocfilehash: 2457bdb794d81e7c482f735cad4ade34564328e2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559313"
---
# <a name="how-to-animate-the-color-or-opacity-of-a-solidcolorbrush"></a>如何：对 SolidColorBrush 的颜色或不透明度进行动画处理
此示例演示如何进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>和<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
## <a name="example"></a>示例  
 下面的示例使用三个动画要进行动画处理<xref:System.Windows.Media.SolidColorBrush.Color%2A>和<xref:System.Windows.Media.Brush.Opacity%2A>的<xref:System.Windows.Media.SolidColorBrush>。  
  
-   第一个动画， <xref:System.Windows.Media.Animation.ColorAnimation>，更改到画笔的颜色<xref:System.Windows.Media.Colors.Gray%2A>当鼠标进入矩形。  
  
-   下一步的动画，另一个<xref:System.Windows.Media.Animation.ColorAnimation>，更改到画笔的颜色<xref:System.Windows.Media.Colors.Orange%2A>当鼠标离开矩形。  
  
-   最后一个动画， <xref:System.Windows.Media.Animation.DoubleAnimation>，当按下鼠标左键时，更改画笔的不透明度为 0.0。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 有关更完整示例中，其中说明了如何进行动画处理不同类型的画笔，请参阅[画笔示例](http://go.microsoft.com/fwlink/?LinkID=159973)。 有关动画的详细信息，请参阅[动画概述](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)。  
  
 与其他动画示例保持一致，对于此示例的代码版本使用<xref:System.Windows.Media.Animation.Storyboard>要应用它们的动画对象。 但是，当应用单个动画在代码中的，这是使用简单得多<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>方法而不是使用<xref:System.Windows.Media.Animation.Storyboard>。 有关示例，请参阅[在不使用情节提要的情况下对属性进行动画处理](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)。  
  
## <a name="see-also"></a>请参阅  
 [动画概述](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [演示图板概述](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [画笔示例](http://go.microsoft.com/fwlink/?LinkID=159973)
