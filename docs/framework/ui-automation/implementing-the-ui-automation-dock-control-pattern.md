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
ms.openlocfilehash: 875a9f3a20b7bb5e66ecf3f6b5e3b3cf229e2bf9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481068"
---
# <a name="implementing-the-ui-automation-dock-control-pattern"></a>Implementacja wzorca kontrolki dokowania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IDockProvider>, w tym informacji o właściwościach. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.DockPattern> — Wzorzec kontrolki jest używany do udostępnienia właściwości dock kontrolki w kontenerze dokowania. Kontener dokowania jest formant, który pozwala rozmieścić elementy podrzędne w poziomie i w pionie, względem siebie. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
 ![Kontener dokowania z dwójką dzieci zadokowany. ](../../../docs/framework/ui-automation/media/uia-dockpattern-dockingexample.PNG "UIA_DockPattern_DockingExample")  
Dokowanie przykładu z programu Visual Studio, gdy okno "W widoku klas" jest DockPosition.Right i okno "Lista błędów" to DockPosition.Bottom  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki dokowania, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   <xref:System.Windows.Automation.Provider.IDockProvider> nie ujawnia żadnych właściwości dokowania kontenera ani właściwości elementów sterujących, które są zadokowane przylegające do bieżącego formantu w kontenerze dokowania.  
  
-   Formanty są zadokowane względem siebie oparte na ich bieżącego porządek; wyższe ich kolejności z umieszczania, wskazujemy są oni umieszczani od określonej granicy dokowania kontenera.  
  
-   Jeśli rozmiar będzie dokowania kontenera, wszelkie zadokowanych kontrolek w kontenerze będzie przeniesiony opróżnić do tej samej granicy, do której zostały pierwotnie zadokowany. Zadokowanych formantów również zmienić rozmiar, aby wypełnić miejsce w kontenerze zgodnie z zachowaniem dokowania ich <xref:System.Windows.Automation.DockPosition>. Na przykład jeśli <xref:System.Windows.Automation.DockPosition.Top> jest określony, lewej i prawej stronie formantu zostanie rozwinięte, aby wypełnić dostępne miejsce. Jeśli <xref:System.Windows.Automation.DockPosition.Fill> określono wszystkich czterech krawędzi kontrolki zostanie rozwinięte, aby wypełnić dostępne miejsce.  
  
-   W systemie wielu monitorów kontrolki powinien zadokować do lewej lub prawej strony bieżącego monitora. Jeśli nie jest to możliwe, powinny one zadokować się po lewej stronie monitor skrajnej lewej lub prawej krawędzi monitor po prawej stronie.  
  
<a name="Required_Members_for_IDockProvider"></a>   
## <a name="required-members-for-idockprovider"></a>Wymagane elementy IDockProvider  
 Poniższe właściwości i metod są wymagane do implementowania interfejsu IDockProvider.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IDockProvider.DockPosition%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IDockProvider.SetDockPosition%2A><br /><br /> — W przypadku kontrolki nie jest w stanie wykonać styl dokowania żądanej.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
