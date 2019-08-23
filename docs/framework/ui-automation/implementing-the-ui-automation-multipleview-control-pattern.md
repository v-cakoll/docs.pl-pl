---
title: Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 6a77b81cab34b1824b23b1e3e050ecf034ab7700
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932170"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 W tym temacie przedstawiono wskazówki i konwencje <xref:System.Windows.Automation.Provider.IMultipleViewProvider>dotyczące wdrażania, w tym informacje o zdarzeniach i właściwościach. Linki do dodatkowych odwołań znajdują się na końcu tematu.  
  
 Wzorzec <xref:System.Windows.Automation.MultipleViewPattern> kontrolki służy do obsługi kontrolek, które zapewniają i mogą przełączać się między wieloma reprezentacjami tego samego zestawu informacji lub formantów podrzędnych.  
  
 Przykłady kontrolek, które mogą przedstawić wiele widoków, obejmują widok listy (który może wyświetlać jego zawartość jako miniatury, kafelki, ikony lub szczegóły [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] ), wykresy (wykres kołowy, liniowy, słupkowy, wartość [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] komórki z formułą), dokumenty (normalne, układ sieci Web, Układ wydruku, układ do czytania, konspekt), Kalendarz programu Microsoft Outlook (rok, miesiąc, tydzień, dzień) [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] i karnacje. Obsługiwane widoki są określane przez dewelopera kontroli i są specyficzne dla każdej kontrolki.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas implementowania wzorca kontroli wielu widoków należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- <xref:System.Windows.Automation.Provider.IMultipleViewProvider>należy również zaimplementować w kontenerze, który zarządza bieżącym widokiem, jeśli różni się od kontrolki, która udostępnia bieżący widok. Na przykład Eksplorator Windows zawiera kontrolkę listy dla zawartości bieżącego folderu, podczas gdy widok dla kontrolki jest zarządzany przez aplikację Eksplorator Windows.  
  
- Kontrolka, która może sortować zawartość, nie jest uważana za obsługę wielu widoków.  
  
- Kolekcja widoków musi być taka sama w różnych wystąpieniach.  
  
- Nazwy widoków muszą być odpowiednie do użycia w zamiana tekstu na mowę, w języku Braille'a i w innych aplikacjach do czytania przez człowieka.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Wymagane elementy członkowskie dla IMultipleViewProvider  
 Do zaimplementowania IMultipleViewProvider są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Brak|  
  
 Z tym wzorcem kontroli nie są skojarzone żadne zdarzenia.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawca musi zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> Gdy lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest elementem członkowskim kolekcji obsługiwane widoki.|  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
