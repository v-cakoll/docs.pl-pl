---
title: Implementacja wzorca formantu MultipleView dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, MultipleView control pattern
- MultipleView control pattern
- control patterns, MultipleView
ms.assetid: 5bf1b248-ffee-48c8-9613-0b134bbe9f6a
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 777f529b3b925a965b24cf1a4b38b9d3b9adae7b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408382"
---
# <a name="implementing-the-ui-automation-multipleview-control-pattern"></a>Implementacja wzorca kontrolki MultipleView dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IMultipleViewProvider>, wraz z informacjami dotyczącymi zdarzeń i właściwości. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.MultipleViewPattern> — Wzorzec formantu jest używana do obsługi formantów, które zapewniają i można przełączać się między wiele reprezentacje ten sam zestaw informacji formantów podrzędnych.  
  
 Kontrolki udostępniające wiele widoków przykłady widok listy (które można wyświetlić jego zawartość jako miniatury, Kafelki, ikony lub szczegóły), [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] wykresów (kołowego, wiersz, pasek, wartość komórki z formułą) [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] dokumentów (normalny, układ sieci Web Drukowanie układu, układ do czytania, konspektu), [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)] kalendarza (rok, miesiąc, tydzień, dzień), a [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)] karnacji. Obsługiwane widoki są określane przez dewelopera kontrolek i są specyficzne dla każdego formantu.  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca kontrolki widoku wielu, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   <xref:System.Windows.Automation.Provider.IMultipleViewProvider> powinny zostać wdrożone również na kontenerze, który zarządza bieżący widok, jeśli różni się od formant, który umożliwia bieżącego widoku. Na przykład Eksploratora Windows zawiera formant listy bieżącej zawartości folderu, gdy wyświetlanie formantu odbywa się z aplikacji Eksploratora Windows.  
  
-   Formant, który może sortować jego zawartość nie jest uważana za obsługuje wiele widoków.  
  
-   Kolekcja widoków muszą być identyczne w wystąpieniach.  
  
-   Wyświetlanie nazw musi być odpowiednie do użycia w tekst na mowę, Braille'a i innych aplikacjach zrozumiałą dla użytkownika.  
  
<a name="Required_Members_for_IMultipleViewProvider"></a>   
## <a name="required-members-for-imultipleviewprovider"></a>Wymagane elementy IMultipleViewProvider  
 Poniższe właściwości i metody są wymagane do wykonania IMultipleViewProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.CurrentView%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetSupportedViews%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A>|Metoda|Brak|  
  
 Brak zdarzeń skojarzonych z tym — wzorzec formantu.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawca musi zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.ArgumentException>|Gdy albo <xref:System.Windows.Automation.Provider.IMultipleViewProvider.SetCurrentView%2A> lub <xref:System.Windows.Automation.Provider.IMultipleViewProvider.GetViewName%2A> jest wywoływana z parametrem, który nie jest członkiem kolekcji obsługiwane widoki.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
