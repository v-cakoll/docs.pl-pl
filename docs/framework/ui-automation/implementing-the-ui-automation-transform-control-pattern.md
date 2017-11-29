---
title: "Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
caps.latest.revision: "14"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: df871c7f7214a6135db2493972dd76f41ce31aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementacja wzorca kontrolki przekształcania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITransformProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.TransformPattern> — Wzorzec formantu jest używana do obsługi formantów, które można przenieść, rozmiaru lub obracać dwuwymiarowa miejsce. Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Implementacja — wskazówki i konwencje  
 Gdy implementacja wzorca kontrolki przekształcania, należy zwrócić uwagę następujące wskazówki i konwencje:  
  
-   Obsługa tego wzorca formantu nie jest ograniczona do obiektów na pulpicie. Ten wzorzec formantu również musi obsługiwane przez element podrzędny obiektu kontenera, gdy elementy podrzędne można przenieść, zmiany rozmiaru lub obracać za darmo w granicach kontenera.  
  
-   Obiekt nie można przenosić, zmiany rozmiaru ani obracać lokalizacji ekranu wynikowy będzie można całkowicie poza współrzędne swojego kontenera i w związku z tym niedostępne do klawiatury lub myszy (na przykład w przypadku, gdy okno najwyższego poziomu zostanie przesunięty ekranem lub a obiekt podrzędny zostanie przeniesiona poza granice tego kontenera okienka ekranu). W takich przypadkach obiekt znajduje się maksymalnie zbliżony współrzędne ekranu żądanego możliwie z góry lub lewej współrzędne zastąpiona w granicach kontenera.  
  
-   Monitor wielu systemów Jeśli obiekt jest przenoszony, po zmianie rozmiaru lub obrócony całkowicie poza współrzędne ekranu pulpitu połączonych obiektu jest umieszczona na podstawowy monitor maksymalnie zbliżony żądanego współrzędne, jak to możliwe.  
  
-   Wszystkie parametry i wartości właściwości są niezależne od ustawień regionalnych i bezwzględne.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Wymagane elementy ITransformProvider  
 Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Brak|  
  
 Wzorzec ten formant nie ma żadnych zdarzeń skojarzone.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawców należy zgłosić następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> ma wartość false.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce formantów automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
