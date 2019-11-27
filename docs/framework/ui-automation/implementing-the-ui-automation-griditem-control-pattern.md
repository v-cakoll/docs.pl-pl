---
title: Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: 832a53e072afc5533f2eeb7feb0cc326771cf23d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435254"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementacja wzorca kontrolki GridItem dla automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych klas [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdefiniowanych w przestrzeni nazw <xref:System.Windows.Automation>. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie przedstawiono wytyczne i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>, w tym informacje o właściwościach. Linki do dodatkowych odwołań znajdują się na końcu przeglądu.  
  
 <xref:System.Windows.Automation.GridItemPattern> wzorzec kontroli służy do obsługi poszczególnych formantów podrzędnych kontenerów, które implementują <xref:System.Windows.Automation.Provider.IGridProvider>. Aby zapoznać się z przykładami formantów implementujących ten wzorzec kontrolek, zobacz [Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Wytyczne i konwencje dotyczące implementacji  
 Podczas wdrażania <xref:System.Windows.Automation.Provider.IGridProvider>należy zwrócić uwagę na następujące wytyczne i konwencje:  
  
- Współrzędne siatki są równe zero, a lewa górna komórka ma współrzędne (0, 0).  
  
- Scalone komórki będą raportować <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> i <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> właściwości na podstawie ich źródłowej komórki zakotwiczenia zdefiniowanej przez dostawcę automatyzacji interfejsu użytkownika. Zwykle jest to pierwszy wiersz lub kolumna najwyższego poziomu.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider> nie zapewnia aktywnego manipulowania siatką, taką jak scalanie lub dzielenie komórek.  
  
- Kontrolki implementujące <xref:System.Windows.Automation.Provider.IGridItemProvider> mogą być zwykle przenoszone (oznacza to, że klient automatyzacji interfejsu użytkownika można przenieść do sąsiednich kontrolek) przy użyciu klawiatury.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Wymagane elementy członkowskie dla IGridItemProvider  
 Do zaimplementowania <xref:System.Windows.Automation.Provider.IGridItemProvider>są wymagane następujące właściwości i metody.  
  
|Wymagane elementy członkowskie|Typ elementu członkowskiego|Uwagi|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Właściwość|Brak|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Właściwość|Brak|  
  
 Ten wzorzec kontroli nie ma skojarzonych metod lub zdarzeń.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Wyjątki  
 Ten wzorzec kontrolki nie ma żadnych skojarzonych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorce kontrolek automatyzacji interfejsu użytkownika — omówienie](ui-automation-control-patterns-overview.md)
- [Obsługa wzorców kontrolek dostawcy automatyzacji interfejsu użytkownika](support-control-patterns-in-a-ui-automation-provider.md)
- [Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów](ui-automation-control-patterns-for-clients.md)
- [Implementacja wzorca kontrolki siatki automatyzacji interfejsu użytkownika](implementing-the-ui-automation-grid-control-pattern.md)
- [Przegląd drzewa automatyzacji interfejsu użytkownika](ui-automation-tree-overview.md)
- [Używanie buforowania w automatyzacji interfejsu użytkownika](use-caching-in-ui-automation.md)
