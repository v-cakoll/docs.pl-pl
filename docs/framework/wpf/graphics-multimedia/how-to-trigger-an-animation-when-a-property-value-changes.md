---
title: "Jak wyzwolić animację kiedy ulega zmianie wartość właściwości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Jak wyzwolić animację kiedy ulega zmianie wartość właściwości
Ten przykład przedstawia sposób użycia <xref:System.Windows.Trigger> uruchomić <xref:System.Windows.Media.Animation.Storyboard> podczas zmiany wartości właściwości. Można użyć <xref:System.Windows.Trigger> wewnątrz <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, lub <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Trigger> do animowania <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> po jego <xref:System.Windows.UIElement.IsMouseOver%2A> staje się właściwość `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Animacje zastosowane przez właściwość <xref:System.Windows.Trigger> obiekty zachowują się w sposób bardziej złożone niż <xref:System.Windows.EventTrigger> animacje lub animacje uruchomić za pomocą <xref:System.Windows.Media.Animation.Storyboard> metod.  Ich "przekazaniem" animacji zdefiniowany przez inne <xref:System.Windows.Trigger> obiektów, ale tworzą z <xref:System.Windows.EventTrigger> i animacje wyzwalane metody.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Trigger>  
 [Omówienie techniki animacji właściwość](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Scenorys — omówienie](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
