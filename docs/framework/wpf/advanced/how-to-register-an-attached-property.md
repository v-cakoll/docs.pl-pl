---
title: "Jak zarejestrować dołączoną właściwość"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37c727eee7b56473808fec06ea42044fc742f7f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-register-an-attached-property"></a>Jak zarejestrować dołączoną właściwość
W tym przykładzie pokazano, jak zarejestrować dołączona właściwość i zapewnia metody dostępu publicznego, dzięki czemu można użyć właściwości zarówno [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod. Dołączone właściwości są koncepcji składni zdefiniowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Najbardziej dołączonych właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy również są zaimplementowane jako właściwości zależności. Można użyć właściwości zależności na dowolnym <xref:System.Windows.DependencyObject> typów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zarejestrować dołączona właściwość jako właściwość zależności, przy użyciu <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Klasa dostawcy ma możliwość zapewnienia domyślne metadane dla właściwości, która ma zastosowanie, gdy jest używana w innej klasy, chyba że tej klasy zastępuje metadane. W tym przykładzie wartość domyślną `IsBubbleSource` właściwość jest ustawiona na `false`.  
  
 Klasa dostawcy dla właściwości dołączonej (nawet jeśli nie jest zarejestrowany jako właściwość zależności), należy podać statyczne get i metody dostępu set, które postępuj zgodnie z konwencją nazewnictwa `Set` *[AttachedPropertyName]* i `Get` *[AttachedPropertyName]*. Te metody dostępu są wymagane, aby działający [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika rozpoznać właściwości jako atrybut w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i rozwiąż odpowiednie typy.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.DependencyProperty>  
 [Przegląd właściwości zależności](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Niestandardowe właściwości zależności](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
