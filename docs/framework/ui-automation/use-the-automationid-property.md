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
ms.openlocfilehash: 7a172db8bcb626d78a24b546147b4e32f20f5d83
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291348"
---
# <a name="use-the-automationid-property"></a>Użyj właściwości AutomationID
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperzy, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] można znaleźć w temacie [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera scenariusze i przykładowy kod, który pokazuje, jak i kiedy <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> może być używany do lokalizowania elementu w drzewie [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jednoznacznie identyfikuje element automatyzacji interfejsu użytkownika na podstawie jego elementów równorzędnych. Aby uzyskać więcej informacji na temat identyfikatorów właściwości związanych z identyfikacją kontroli, zobacz [Omówienie właściwości automatyzacji interfejsu użytkownika](ui-automation-properties-overview.md).  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> nie gwarantuje unikatowej tożsamości w całym drzewie; zwykle potrzebuje informacji o kontenerach i zakresach. Na przykład aplikacja może zawierać formant menu z wieloma elementami menu najwyższego poziomu, które z kolei mają wiele elementów menu podrzędnych. Te elementy menu pomocniczego mogą być identyfikowane przez schemat generyczny, taki jak "Item1 —", "Item 2" i tak dalej, co umożliwia duplikowanie identyfikatorów dla elementów podrzędnych w elementach menu najwyższego poziomu.  
  
## <a name="scenarios"></a>Scenariusze  
 Zidentyfikowano trzy scenariusze aplikacji klienckiej automatyzacji interfejsu użytkownika, które wymagają użycia <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> w celu uzyskania dokładnych i spójnych wyników podczas wyszukiwania elementów.  
  
> [!NOTE]
> <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> jest obsługiwany przez wszystkie elementy automatyzacji interfejsu użytkownika w widoku sterowania z wyjątkiem okien aplikacji najwyższego poziomu, elementy automatyzacji interfejsu użytkownika pochodzące z kontrolek [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], które nie mają identyfikatora lub X:UID — oraz elementy automatyzacji interfejsu użytkownika pochodzące z formantów [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], które nie są mieć identyfikator kontrolki.  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>Użyj unikatowego i wykrywalnego AutomationID do zlokalizowania określonego elementu w drzewie automatyzacji interfejsu użytkownika  
  
- Użyj narzędzia takiego jak interfejs użytkownika Spy, aby zgłosić <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> elementu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zainteresowania. Tę wartość można następnie skopiować i wkleić do aplikacji klienckiej, takiej jak skrypt testowy dla kolejnych zautomatyzowanych testów. Takie podejście zmniejsza i upraszcza kod niezbędny do identyfikowania i lokalizowania elementu w czasie wykonywania.  
  
> [!CAUTION]
> Ogólnie rzecz biorąc, należy podjąć próbę uzyskania tylko bezpośrednich elementów podrzędnych <xref:System.Windows.Automation.AutomationElement.RootElement%2A>. Wyszukiwanie elementów podrzędnych może przechodzić przez setki lub nawet tysiące elementów, co może spowodować przepełnienie stosu. Jeśli próbujesz uzyskać określony element na niższym poziomie, należy rozpocząć wyszukiwanie od okna aplikacji lub kontenera na niższym poziomie.  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki trwałej do powrotu do wcześniej zidentyfikowanego elementu AutomationElement  
  
- Aplikacje klienckie, z prostych skryptów testowych do niezawodnych narzędzi do nagrywania i odtwarzania, mogą wymagać dostępu do elementów, które nie są aktualnie tworzone, takie jak okno dialogowe Otwieranie pliku lub element menu, w związku z czym nie istnieją w drzewie automatyzacji interfejsu użytkownika. Można tworzyć wystąpienia tych elementów tylko przez odtworzenie lub "odtwarzanie", konkretną sekwencję akcji interfejsu użytkownika za pomocą właściwości automatyzacji interfejsu użytkownika, takich jak AutomationID, wzorce formantów i detektory zdarzeń.
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>Użyj ścieżki względnej, aby powrócić do wcześniej zidentyfikowanego elementu AutomationElement  
  
- W pewnych okolicznościach, ponieważ AutomationID jest gwarantowany wyłącznie jako unikatowy wśród elementów równorzędnych, wiele elementów w drzewie automatyzacji interfejsu użytkownika może mieć identyczne wartości właściwości AutomationID. W takich sytuacjach elementy mogą być jednoznacznie identyfikowane na podstawie elementu nadrzędnego i, w razie potrzeby, do dziadka. Na przykład deweloper może udostępnić pasek menu z wieloma elementami menu każdy z wieloma elementami menu podrzędnymi, w których elementy podrzędne są identyfikowane za pomocą sekwencyjnych AutomationID, takich jak "Item1 —", "Item2 —" i tak dalej. Każdy element menu może być następnie jednoznacznie identyfikowany przez jego AutomationID oraz AutomationID jego elementu nadrzędnego i, w razie potrzeby, jego nadrzędnym.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Znajdź element automatyzacji interfejsu użytkownika na podstawie warunku właściwości](find-a-ui-automation-element-based-on-a-property-condition.md)
