---
title: Implementacja wzorca formantu przekształcania automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Transform
- Transform control pattern
- UI Automation, Transform control pattern
ms.assetid: 5f49d843-5845-4800-9d9c-56ce0d146844
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 6f193380619d5e75eaacebe00f602a3716d91ddf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564315"
---
# <a name="implementing-the-ui-automation-transform-control-pattern"></a>Implementacja wzorca kontrolki przekształcania automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: automatyzacji interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.ITransformProvider>, wraz z informacjami dotyczącymi właściwości, metody i zdarzenia. Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.  
  
 <xref:System.Windows.Automation.TransformPattern> — Wzorzec kontrolki jest używana do obsługi formantów, które mogą być przenoszone, rozmiaru lub obrócone w przestrzeni dwuwymiarowej. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Jeśli implementacja wzorca kontrolki przekształcania, należy zwrócić uwagę następujących wytycznych i konwencje:  
  
-   Obsługa tego wzorca kontrolki nie jest ograniczona do obiektów na pulpicie. Ten wzorzec kontroli muszą być obsługiwane przez element podrzędny obiektu kontenera, jeśli elementy podrzędne mogą być przeniesione, rozmiaru lub obracać za darmo w granicach kontenera.  
  
-   Obiekt nie można przenosić, ze zmienionym rozmiarem ani obrócone w taki sposób, że jej lokalizacja wynikowa ekranu będzie całkowicie przekraczających współrzędne jego kontenera i w związku z tym niedostępne do klawiatury lub myszy (na przykład w przypadku, gdy okno jest przesuwany ekranem lub w obiekt podrzędny zostanie przeniesiona poza granice kontenera okienka ekranu). W takich przypadkach obiekt jest umieszczany była jak najbliżej współrzędne ekranu żądanego możliwie z góry lub lewej współrzędne zastąpiona w granicach kontenera.  
  
-   Systemów wielu monitorów Jeśli obiekt zostanie przeniesiony, o zmienionym rozmiarze lub obrócony całkowicie poza współrzędne ekranu pulpitu połączonego obiektu jest umieszczony na podstawowy monitor była jak najbliżej żądanego współrzędne, jak to możliwe.  
  
-   Wszystkie parametry i wartości właściwości są bezwzględne i niezależne od ustawień regionalnych.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-itransformprovider"></a>Wymagane elementy ITransformProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanMove%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanResize%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.CanRotate%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A>|Metoda|Brak|  
|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A>|Metoda|Brak|  
  
 Ten wzorzec formantu nie ma żadnych skojarzonych zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Dostawcy należy zgłaszać następujące wyjątki.  
  
|Typ wyjątku|Warunek|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Move%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanMoveProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Resize%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanResizeProperty> ma wartość false.|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.ITransformProvider.Rotate%2A><br /><br /> -Jeśli <xref:System.Windows.Automation.TransformPatternIdentifiers.CanRotateProperty> ma wartość false.|  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
