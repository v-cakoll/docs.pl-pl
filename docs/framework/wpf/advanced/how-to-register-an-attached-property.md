---
title: 'Instrukcje: Zarejestruj dołączoną właściwość'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- attached properties [WPF], registering
- registering attached properties [WPF]
ms.assetid: eb47bd94-0451-4f8d-8fb6-95f7812ac05b
ms.openlocfilehash: 3cbbc8a1ea8419df408cda76de3459be9464a100
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377719"
---
# <a name="how-to-register-an-attached-property"></a>Instrukcje: Zarejestruj dołączoną właściwość
W tym przykładzie pokazano, jak zarejestrować dołączoną właściwość i podaj publiczne metody dostępu, tak, aby można było używać właściwości w obu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] i kod. Dołączone właściwości to pojęcie składni zdefiniowane przez [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Najbardziej dołączonych właściwości [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] typy również są implementowane jako właściwości zależności. Można użyć właściwości zależności na dowolnym <xref:System.Windows.DependencyObject> typów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zarejestrować dołączoną właściwość jako właściwość zależności za pomocą <xref:System.Windows.DependencyProperty.RegisterAttached%2A> metody. Klasa dostawcy ma możliwość związanych z udostępnianiem domyślne metadane dla właściwości, która ma zastosowanie, gdy jest używana w innej klasy, chyba że ta klasa zastępuje metadanych. W tym przykładzie wartość domyślną `IsBubbleSource` właściwość jest ustawiona na `false`.  
  
 Klasa dostawcy dołączone właściwości (nawet jeśli nie jest zarejestrowany jako właściwość zależności) należy podać get statycznych i metod dostępu set, które przestrzegać konwencji nazewnictwa `Set` *[AttachedPropertyName]* i `Get` *[AttachedPropertyName]*. Te metody dostępu są wymagane, aby działający [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] czytnika rozpoznać właściwości jako atrybut w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] i rozwiąż odpowiednie typy.  
  
 [!code-csharp[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#registerattachedbubbler)]
 [!code-vb[WPFAquariumSln#RegisterAttachedBubbler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#registerattachedbubbler)]  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.DependencyProperty>
- [Przegląd właściwości zależności](dependency-properties-overview.md)
- [Niestandardowe właściwości zależności](custom-dependency-properties.md)
- [Tematy z instrukcjami](properties-how-to-topics.md)
