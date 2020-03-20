---
title: Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 9decb617e30a340d3e73e911f7848110de5599e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180170"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne <xref:System.Windows.Automation.Provider.IMultipleViewProvider>i konwencje dotyczące implementacji, w tym informacje o zdarzeniach i właściwościach. Łącza do dodatkowych odwołań są wyświetlane na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.MultipleViewPattern> formantu jest używany do obsługi formantów, które zapewniają i są w stanie przełączać się między wieloma reprezentacjami tego samego zestawu informacji lub formantów podrzędnych.  
  
 Przykłady formantów, które mogą prezentować wiele widoków, obejmują widok listy (który może wyświetlać jego zawartość jako miniatury, kafelki, ikony lub szczegóły), wykresy programu Microsoft Excel (kołowy, liniowy, słupkowy, wartość komórki z formułą), dokumenty programu Microsoft Word (normalny, układ sieci Web, drukowanie układ, układ odczytu, konspekt), kalendarz programu Microsoft Outlook (rok, miesiąc, tydzień, dzień) i skórki programu Microsoft Windows Media Player. Obsługiwane widoki są określane przez dewelopera formantu i są specyficzne dla każdego formantu.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące wdrażania  
 Podczas implementowania wzorca formantu widoku wielokrotnego należy zwrócić uwagę na następujące wskazówki i konwencje:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>należy również zaimplementować w kontenerze, który zarządza bieżącym widokiem, jeśli różni się od formantu, który zapewnia bieżący widok. Na przykład Eksplorator Windows zawiera kontrolkę Lista bieżącej zawartości folderu, podczas gdy widok formantu jest zarządzany za pomocą aplikacji Eksploratora Windows.  
  
- Formant, który jest w stanie posortować jego zawartość nie jest uważany za obsługę wielu widoków.  
  
- Kolekcja widoków musi być identyczna w różnych wystąpieniach.  
  
- Nazwy widoków muszą być odpowiednie do użytku w aplikacjach zamiany tekstu na mowę, brajlach i innych aplikacjach czytelnych dla człowieka.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>
## <a name="required-members-for-imultipleviewprovider"></a>Wymagane elementy członkowskie dla imultipleViewProvider  
 Następujące właściwości i metody są wymagane do implementowania IMultipleViewProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Brak|  
  
 Nie ma żadnych zdarzeń skojarzonych z tym wzorcem formantu.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Wyjątki  
 Dostawca musi zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest członkiem kolekcji obsługiwanych widoków.|  
  
## <a name="see-also"></a>Zobacz też

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
