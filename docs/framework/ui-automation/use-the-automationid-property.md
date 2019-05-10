---
title: Użyj właściwości AutomationID
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
ms.openlocfilehash: 543717873f3ef6d0d44c5bcbbef013817c06357c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583580"
---
# <a name="use-the-automationid-property"></a>Użyj właściwości AutomationID
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera scenariusze i przykładowy kod, aby pokazać, jak i kiedy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> może służyć do zlokalizowania elementu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa.  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jednoznacznie identyfikuje element automatyzacji interfejsu użytkownika z jego elementów równorzędnych. Aby uzyskać więcej informacji na temat identyfikatorów właściwości związane z kontrolować identyfikacji, zobacz [Przegląd właściwości automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie gwarantuje unikatową tożsamość w drzewie; Zazwyczaj potrzebuje kontenera i informacje o zakresie były przydatne. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei ma wiele elementów menu podrzędne. Te elementy menu dodatkowej mogą być określane przez ogólny schemat, takiego jak item1 "—", "Element 2" i tak dalej, umożliwiając zduplikowanych identyfikatorów dla dzieci różnych elementów menu górnego poziomu.  
  
## <a name="scenarios"></a>Scenariusze  
 Trzy podstawowe scenariusze aplikacji klienta automatyzacji interfejsu użytkownika zostały określone, które korzystają z <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> Aby uzyskać dokładne i spójne wyniki, podczas wyszukiwania elementów.  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jest obsługiwany przez wszystkie elementy automatyzacji interfejsu użytkownika w widoku kontrolki, z wyjątkiem okien najwyższego poziomu aplikacji, po elementach automatyzacji interfejsu użytkownika pochodną [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] formantów, które nie mają Identyfikatora lub x: Uid i pochodną po elementach automatyzacji interfejsu użytkownika [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] formantów, które nie masz identyfikator kontrolki.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Należy użyć AutomationID unikatowe i wykrywalny, aby zlokalizować określonego elementu drzewa automatyzacji interfejsu użytkownika  
  
- Użyj narzędzia takiego jak [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] do raportu <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> z [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] element zainteresowania. Ta wartość może następnie skopiowane i wklejone do aplikacji klienckiej, takich jak skrypt testu dla kolejnych testów automatycznych. Takie podejście zmniejsza i upraszcza kod wymagany do identyfikowania i lokalizowania elementu w czasie wykonywania.  
  
> [!CAUTION]
>  Ogólnie rzecz biorąc, należy spróbować uzyskać tylko bezpośrednie elementy podrzędne <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukaj elementy podrzędne mogą wykonać iterację setek lub nawet tysięcy elementów, które prawdopodobnie spowodowało przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie z okna aplikacji lub kontenerów na niższym poziomie.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki trwały, aby powrócić do wcześniej zidentyfikowane obiektu AutomationElement  
  
- Aplikacje klienckie, ze skryptów prosty test niezawodne rejestrowanie i narzędzia odtwarzania może wymagać dostępu do elementów, które się nie aktualnie wystąpienia, takie jak plik Otwórz okno dialogowe lub elementu menu i dlatego nie istnieją w drzewa automatyzacji interfejsu użytkownika. Te elementy mogą być tylko utworzone przez odtwarzanie, lub "odtwarzania", określonej kolejności akcji UI za pomocą właściwości automatyzacji interfejsu użytkownika, takie jak AutomationID, wzorców kontrolek i detektory zdarzenia.
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki względnej, aby powrócić do wcześniej zidentyfikowane obiektu AutomationElement  
  
- W pewnych okolicznościach ponieważ AutomationID tylko musi być unikatowa wśród elementów równorzędnych, wiele elementy drzewa automatyzacji interfejsu użytkownika mogą mieć identycznych wartości właściwości AutomationID. W takich sytuacjach elementy można unikatowo zidentyfikować oparte na element nadrzędny i, jeśli to konieczne, nadrzędnych. Na przykład deweloperzy mogą korzystać pasek menu z wieloma elementami menu każdego z wiele podrzędnych elementów menu, w którym elementy podrzędne są identyfikowane przez sekwencyjnego AutomationID firmy takie jak "Item1 —", "Item2 —" i tak dalej. Każdy element menu może następnie jednoznacznie zidentyfikować przez jego AutomationID wraz z AutomationID jego elementu nadrzędnego i, jeśli to konieczne, jej nadrzędnych.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
