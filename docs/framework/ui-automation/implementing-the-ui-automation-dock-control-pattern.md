---
title: Implementacja wzorca formantu dokowania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, dock
- dock control pattern
- UI Automation, dock control pattern
ms.assetid: ea3d2212-7c8e-4dd7-bf08-73141ca2d4fb
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e04814885ae0963d4da99acecf00dc646ecc96f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400734"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementacja wzorca kontrolki dokowania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IDockProvider>, wraz z informacjami o właściwościach. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.DockPattern> — Wzorzec formantu jest używany do udostępnienia właściwości dock formantu dokowania kontenera. Kontener dokowania jest formant, który pozwala na poziomie i w pionie, Rozmieść elementy podrzędne względem siebie. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Kontener dokowania z zadokowanych dwa działania podrzędne. ] (../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Dokowanie przykład z programu Visual Studio, gdy okno "Klasy widok" jest DockPosition.Right i w oknie "Lista błędów" jest DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca formantu dokowania, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider> nie ujawnia żadnych właściwości dokowania kontenera ani właściwości formantów, które są zadokowane sąsiadujące bieżącego formantu w kontenerze dokowania.  
  
-   Formanty są zadokowane względem siebie na podstawie ich bieżącego zamówienia z; wyższe ich kolejności umieszczania, dalej są umieszczane z określonej krawędzi dokowania kontenera.  
  
-   Jeśli rozmiaru kontenera dokowania żadnych zadokowanych formantów w kontenerze będzie można zmienić ich pozycji opróżnić do tej samej granicy, do której zostały pierwotnie zadokowane. Formantów dokowanych również zmienić rozmiar do wypełnienia dowolnego miejsca w kontenerze według dokowania zachowanie ich <xref:System.Windows.Automation.DockPosition>. Na przykład jeśli <xref:System.Windows.Automation.DockPosition.Top> określono lewej i prawej stronie formantu zostanie rozwinięty w celu wypełnienia dowolnego dostępnego miejsca. Jeśli <xref:System.Windows.Automation.DockPosition.Fill> jest określona, wszystkie cztery strony formantu zostanie rozwinięty w celu wypełnienia dowolnego dostępnego miejsca.  
  
-   W systemie monitor wielu formantów powinien dock do lewej lub prawej strony bieżącego monitora. Jeśli nie jest to możliwe, powinny one zostało zadokowane do lewej monitora lewej lub prawej krawędzi monitor po prawej stronie.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Wymagane elementy IDockProvider  
 Poniższe właściwości i metody są wymagane do implementowania interfejsu IDockProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Brak|  
  
 Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> — Gdy formantu nie jest w stanie wykonać styl dokowania żądanej.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
