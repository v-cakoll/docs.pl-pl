---
title: Implementacja wzorca formantu MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
ms.openlocfilehash: 5c875794a3d6fb0325bf282bc0f4b903aa29de07
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674292"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które zapewniają i można przełączać się między wiele reprezentacji ten sam zestaw kontrolek informacji lub podrzędnej.  
  
 Kontrolki udostępniające wiele widoków przykłady widok listy (które można wyświetlić jego zawartość jako miniatury, Kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (koła, wiersz, pasek, wartość komórki przy użyciu formuły) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentów (normalny, układu strony sieci Web Drukuj układu, układu do czytania, kontur), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendarza (rok, miesiąc, tydzień, dzień), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] skórki. Obsługiwane widoki są określane przez dewelopera kontrolek i są specyficzne dla każdego formantu.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki widoku wielu, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> również powinny być zrealizowane w kontenerze, który zarządza bieżący widok, jeśli jest inny niż formant, który zawiera bieżący widok. Na przykład Eksploratora Windows zawiera kontrolkę listy do bieżącej zawartości folderu, kiedy widoku dla kontrolki jest zarządzana z poziomu aplikacji w Eksploratorze Windows.  
  
-   Formant, który jest w stanie sortowania jego zawartość nie jest uważany za obsługuje wiele widoków.  
  
-   Kolekcja widoków muszą być identyczne w wystąpieniach.  
  
-   Wyświetlanie nazw musi być odpowiednia do stosowania w zamiany tekstu na mowę, Braille'a i inne aplikacje czytelny dla człowieka.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Wymagane elementy IMultipleViewProvider  
 Poniższe właściwości i metod są wymagane do wykonania IMultipleViewProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Brak|  
  
 Brak zdarzeń skojarzonych z tym — wzorzec kontrolki.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawca musi zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest elementem członkowskim kolekcji obsługiwane widoki.|  
  
## <a name="see-also"></a>Zobacz także
- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
