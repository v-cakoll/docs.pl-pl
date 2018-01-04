---
title: "Użyj właściwości AutomationID"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 969ab4f3c63571488c66c8a505df3969fcd788e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="use-the-automationid-property"></a>Użyj właściwości AutomationID
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera scenariusze i przykładowy kod, które pokazują, jak i kiedy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> może służyć do zlokalizowania w elemencie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>Unikatowy identyfikator elementu automatyzacji interfejsu użytkownika z jego elementów równorzędnych. Aby uzyskać więcej informacji na identyfikatorach właściwości związane z kontroli identyfikacji, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>nie gwarantuje unikatową tożsamość w drzewie; potrzebuje zazwyczaj kontenera i informacje o zakresie użyteczne. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei ma wiele elementów menu podrzędnego. Te elementy menu dodatkowej mogą zostać zidentyfikowane na podstawie ogólnego schemat, takiego jak "Item1", "Elementu 2" i tak dalej, dzięki czemu zduplikowane identyfikatory elementów podrzędnych dla elementów menu najwyższego poziomu.  
  
## <a name="scenarios"></a>Scenariusze  
 Trzy podstawowe scenariusze aplikacji klienta automatyzacji interfejsu użytkownika zostały określone, które wymagają użycia <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> do osiągnięcia dokładne i spójne wyniki podczas wyszukiwania elementów.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>jest obsługiwana przez wszystkie elementy automatyzacji interfejsu użytkownika w widoku kontrolki z wyjątkiem najwyższego poziomu aplikacji systemu windows, elementach automatyzacji interfejsu użytkownika pochodzące z [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] formantów, które nie mają Identyfikatora lub x: Uid i elementów automatyzacji interfejsu użytkownika pochodzące z [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] formantów, które nie ma identyfikatora formantu.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Użyj AutomationID unikatowy i wykrywalny można znaleźć określonego elementu w drzewie automatyzacji interfejsu użytkownika  
  
-   Za pomocą narzędzia, takie jak [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] do raportu <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element zainteresowań. Ta wartość może następnie można kopiować i wklejać do aplikacji klienckiej, takich jak skrypt testu dla testów automatycznych kolejne. Takie podejście zmniejsza i upraszcza niezbędne do identyfikowania i Znajdź element w czasie wykonywania kodu.  
  
> [!CAUTION]
>  Ogólnie rzecz biorąc, należy uzyskać tylko bezpośrednimi elementami podrzędnymi <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukiwanie elementów podrzędnych może wykonać iterację setki lub nawet tysiące elementów, co prawdopodobnie przepełnienia stosu. Jeśli próbujesz uzyskać określonego elementu na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontener na niższym poziomie.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki trwałe aby powrócić do poprzednio zidentyfikowanych Obiekt AutomationElement  
  
-   Aplikacje klienckie ze prosty test skryptów niezawodny rekordu i narzędzia odtwarzania mogą wymagać dostępu do elementów, które są nie obecnie wystąpienia, takich jak plik Otwórz okno dialogowe, lub elementu menu i dlatego nie istnieją w drzewie automatyzacji interfejsu użytkownika. Te elementy można wdrożyć tylko odtwarzanie, lub "Odtwarzanie", określonej sekwencji [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] akcje za pośrednictwem [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, takie jak AutomationID, wzorców formantu i odbiorników zdarzeń. Zobacz [testu z przykładowym skrypcie Generator](http://msdn.microsoft.com/en-us/028467fd-2980-4691-9522-0131dcef23a0) na przykład, który używa [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] generowania skryptów testu oparte na interakcję użytkownika z [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)].  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki względnej, aby powrócić do poprzednio zidentyfikowanych Obiekt AutomationElement  
  
-   W pewnych okolicznościach ponieważ AutomationID tylko gwarantuje to unikatowa wśród elementów równorzędnych, wiele elementów w drzewie automatyzacji interfejsu użytkownika może mieć wartości właściwości AutomationID identyczne. W takich sytuacjach elementy mogą być identyfikowane oparte na element nadrzędny i, jeśli to konieczne, nadrzędny. Na przykład deweloper może zapewnić paska menu wielu pozycji menu każdego z wielu podrzędnych elementów menu, której elementy podrzędne są oznaczone symbolem sekwencyjnych AutomationID na przykład "Item1", "Item2" i tak dalej. Każdy element menu może następnie unikatowo identyfikowana przez jego AutomationID wraz z AutomationID nadrzędnego i, jeśli to konieczne, jego nadrzędny.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
