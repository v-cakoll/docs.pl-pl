---
title: Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 829df66f49d5df5f5c8cf8d2b6cfa74f0a2172dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101136"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczona dla deweloperów .NET Framework, którzy chcą używać zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [Windows Automation API: Automatyzacja interfejsu użytkownika](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera listę typów formantów oraz ich wzorce skojarzonego formantu.  
  
 Poniższa tabela służy do organizowania wzorców kontrolek na następujące kategorie:  
  
-   Obsługiwane. Kontrolka musi obsługiwać tego wzorca kontrolki.  
  
-   Obsługa warunkowe. Formant może obsługiwać tego wzorca kontrolki, w zależności od stanu kontrolki.  
  
-   Nieobsługiwane. Kontrolka nie obsługuje tego wzorca kontrolki; Kontrolki niestandardowe mogą obsługiwać tego wzorca kontrolki.  
  
> [!NOTE]
>  Niektóre kontrolki zostały warunkowego obsługę kilku wzorców kontrolek, w zależności od funkcji kontroli. Na przykład, kontrolki elementu menu ma warunkowego obsługę <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, lub <xref:System.Windows.Automation.SelectionItemPattern> — wzorzec kontrolki, w zależności od jego funkcji w kontrolce menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów  
  
|Typ formantu|Obsługiwane|Obsługa warunkowe|Nieobsługiwane|  
|------------------|---------------|-------------------------|-------------------|  
|Przycisk|Brak|Wywoływanie przełączania, rozwijanie i zwijanie|Brak|  
|Kalendarz|Siatka, tabeli|Wybór i przewijania|Wartość|  
|Pole wyboru|przełączanie|Brak|Brak|  
|pole kombi|Rozwijanie i zwijanie|Wybór, wartość|Scroll|  
|siatka danych|Siatka|Tabela przewijania, wybór|Brak|  
|Element danych|SelectionItem|Rozwiń Zwiń element siatki, element przewijania, tabeli, przełącznika, wartość|Brak|  
|dokument|Tekst|Przewijanie, wartość|Brak|  
|Edytowanie|Brak|Wartość tekstowa, wartość zakresu|Brak|  
|Grupa|Brak|Rozwijanie i zwijanie|Brak|  
|nagłówek|Brak|Transformacja|Brak|  
|element nagłówka|Brak|Przekształcanie, wywołaj|Brak|  
|Hyperlink|wywoływanie|Wartość|Brak|  
|Obraz|Brak|Element siatki, element tabeli|Wywołaj element wyboru|  
|Lista|Brak|Siatki, wiele widok przewijania, wybór|tabela|  
|Element listy|SelectionItem|Rozwijanie i zwijanie, element siatki wywołania, przewiń elementu przełączać, wartość|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Rozwiń Zwiń, doku, przekształcenia|Brak|  
|Element menu|Brak|Rozwijanie i zwijanie, wywołaj element wyboru Przełącz|Brak|  
|Pane|Brak|Dokowania. Przewiń w transformacji|Okno|  
|pasek postępu|Brak|Zakres wartości, wartości|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Suwak|Brak|Wartość wartości, wybór zakresu|Brak|  
|pokrętło|Brak|Wartość wartości, wybór zakresu|Brak|  
|przycisk podziału|Wywoływanie, rozwijanie i zwijanie|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|wywoływanie|  
|tabela|Siatka, element siatki w tabeli i element tabeli|Brak|Brak|  
|Tekst|Brak|Tekst elementu, element tabeli siatki|Wartość|  
|Thumb|Transformacja|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Pasek narzędzi|Brak|Dokowanie, rozwijanie i zwijanie, przekształcania|Brak|  
|Etykietka narzędzia|Brak|Tekst, okno|Brak|  
|Drzewo|Brak|Przewijanie i wybieranie|Brak|  
|element drzewa|Rozwijanie i zwijanie|Wywołaj element przewijania, Przełącz zaznaczenie elementu|Brak|  
|Okno|Przekształcanie, okno|Dock|Brak|  
  
> [!NOTE]
>  Jeśli typ kontrolki ma nie wzorce obsługiwanych kontrolki, na liście, ale ma jeden lub kilka wzorców kontrolki warunkowo obsługiwane, a następnie będą jedną z tych wzorców kontrolek warunkowego obsługiwane na wszystkich razy.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
