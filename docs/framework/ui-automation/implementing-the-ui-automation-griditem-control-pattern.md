---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 932eb0af6afbe958695d5c084d2cb0c0bc188830
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176621"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, w tym informacji o właściwościach. Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.  
  
 <xref:System.Windows.Automation.GridItemPattern> — Wzorzec kontrolki jest używana do obsługi formantów podrzędnych poszczególnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>. Przykłady formantów, które implementują wzorzec tej kontrolki, zobacz [kontroli wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne dotyczące implementacji i konwencje  
 Podczas implementowania <xref:System.Windows.Automation.Provider.IGridProvider>, należy pamiętać o następujących wytycznych i konwencje:  
  
-   Współrzędne siatki zaczynają się od zera za pomocą lewa górna komórka o współrzędnych (0, 0).  
  
-   Scalone komórki, będą zgłaszać ich <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich podstawowej zakotwiczenia komórki zgodnie z definicją w dostawcy automatyzacji interfejsu użytkownika. Zazwyczaj będzie najwyższego poziomu i skrajnie po lewej stronie wiersza lub kolumny.  
  
-   <xref:System.Windows.Automation.Provider.IGridItemProvider> nie wymaga aktywnego manipulowania siatki, takie jak scalanie lub podział komórek.  
  
-   Określa, które implementują <xref:System.Windows.Automation.Provider.IGridItemProvider> można zwykle te typy można przemierzać (klientów automatyzacji interfejsu użytkownika może przechodzić do kontrolek sąsiadujące) przy użyciu klawiatury.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Wymagane elementy IGridItemProvider  
 Poniższe właściwości i metod wymaganych do implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Właściwość|Brak|  
  
 Ten wzorzec kontroli nie ma skojarzonych z nim metod lub zdarzenia.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontroli ma skojarzone generują żadnych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
