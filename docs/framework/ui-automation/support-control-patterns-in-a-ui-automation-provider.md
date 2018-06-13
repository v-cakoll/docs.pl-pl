---
title: Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, supporting in UI Automation provider
- UI Automation, supporting control patterns in provider
ms.assetid: 0d635c35-ffa8-4dc8-bbc9-12fcd5445776
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0c7ca4507ce5e7d2f6f295caace23134a8a6d492
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398997"
---
# <a name="support-control-patterns-in-a-ui-automation-provider"></a>Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono sposób zaimplementować jeden lub kilka wzorców formantu w dostawcy automatyzacji interfejsu użytkownika tak, aby aplikacje klienckie można manipulować formantów i Pobierz dane z nich.  
  
### <a name="support-control-patterns"></a>Obsługa wzorców formantów  
  
1.  Implementowanie odpowiednich interfejsów dla wzorców kontrolki, które element powinien obsługiwać, takich jak <xref:System.Windows.Automation.Provider.IInvokeProvider> dla <xref:System.Windows.Automation.InvokePattern>.  
  
2.  Zwraca obiekt zawierający implementacji interfejsu każdego formantu w implementacji <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A?displayProperty=nameWithType>  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia implementację <xref:System.Windows.Automation.Provider.ISelectionProvider> pola niestandardowe listy pojedynczego wyboru. Zwraca właściwości trzy, a pobiera obecnie wybrany element.  
  
 [!code-csharp[UIAFragmentProvider_snip#119](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListPattern.cs#119)]
 [!code-vb[UIAFragmentProvider_snip#119](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListPattern.vb#119)]  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia implementację <xref:System.Windows.Automation.Provider.IRawElementProviderSimple.GetPatternProvider%2A> zwracającą Implementacja klasy <xref:System.Windows.Automation.Provider.ISelectionProvider>. Większość formanty pola listy czy obsługuje inne wzorce również, ale w tym przykładzie odwołanie o wartości null (`Nothing` w programie Microsoft Visual Basic .NET) jest zwracane są wszystkie identyfikatory wzorca.  
  
 [!code-csharp[UIAFragmentProvider_snip#120](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAFragmentProvider_snip/CSharp/ListFragment.cs#120)]
 [!code-vb[UIAFragmentProvider_snip#120](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAFragmentProvider_snip/VisualBasic/ListFragment.vb#120)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd dostawców automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-providers-overview.md)  
 [Implementacja dostawcy automatyzacji interfejsu użytkownika po stronie serwera](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
