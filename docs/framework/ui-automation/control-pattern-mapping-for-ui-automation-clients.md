---
title: Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 48298cb8d89958c701d7150aeb497e82d565bde1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433862"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
> This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace. For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).  
  
 This topic lists control types and their associated control patterns.  
  
 The following table organizes the control patterns into the following categories:  
  
- Supported. The control must support this control pattern.  
  
- Conditional support. The control may support this control pattern depending on the state of the control.  
  
- Nieobsługiwane. The control does not support this control pattern; custom controls may support this control pattern.  
  
> [!NOTE]
> Some controls have conditional support for several control patterns depending on the functionality of the control. For example, the menu item control has conditional support for the <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, or <xref:System.Windows.Automation.SelectionItemPattern> control pattern, depending on its function in the menu control.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów  
  
|Control Type|Obsługiwane|Conditional Support|Nieobsługiwane|  
|------------------|---------------|-------------------------|-------------------|  
|Przycisk|Brak|Invoke, Toggle, Expand Collapse|Brak|  
|Kalendarz|Grid, Table|Selection, Scroll|Wartość|  
|Check Box|przełączanie|Brak|Brak|  
|pole kombi|Expand Collapse|Selection, Value|Scroll|  
|siatka danych|Siatka|Scroll, Selection, Table|Brak|  
|Element danych|SelectionItem|Expand Collapse, Grid Item, Scroll Item, Table, Toggle, Value|Brak|  
|dokument|Tekst|Scroll, Value|Brak|  
|Edytowanie|Brak|Text, Range Value, Value|Brak|  
|Grupa|Brak|Expand Collapse|Brak|  
|nagłówek|Brak|Transformacja|Brak|  
|element nagłówka|Brak|Transform, Invoke|Brak|  
|Hyperlink|wywoływanie|Wartość|Brak|  
|Obraz|Brak|Grid Item, Table Item|Invoke, Selection Item|  
|Lista|Brak|Grid, Multiple View, Scroll, Selection|tabela|  
|List Item|SelectionItem|Expand Collapse, Grid Item, Invoke, Scroll Item, Toggle, Value|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Expand Collapse, Dock, Transform|Brak|  
|Element menu|Brak|Expand Collapse, Invoke, Selection Item, Toggle|Brak|  
|Pane|Brak|Dock. Scroll, Transform|Okno|  
|pasek postępu|Brak|Range Value, Value|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Suwak|Brak|Range Value, Selection, Value|Brak|  
|pokrętło|Brak|Range Value, Selection, Value|Brak|  
|przycisk podziału|Invoke, Expand Collapse|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|wywoływanie|  
|tabela|Grid, Grid Item, Table, Table Item|Brak|Brak|  
|Tekst|Brak|Grid Item, Table Item, Text|Wartość|  
|Thumb|Transformacja|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Tool Bar|Brak|Dock, Expand Collapse, Transform|Brak|  
|Tool Tip|Brak|Text, Window|Brak|  
|Drzewo|Brak|Scroll, Selection|Brak|  
|element drzewa|Expand Collapse|Invoke, Scroll Item, Selection Item, Toggle|Brak|  
|Okno|Transform, Window|Dock|Brak|  
  
> [!NOTE]
> If a control type has no supported control patterns listed but has one or more conditionally-supported control patterns, then one of those conditional control patterns will be supported at all times.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
