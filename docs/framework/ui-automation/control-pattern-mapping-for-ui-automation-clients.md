---
title: Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: cfd8e5dbe34df7b947646c714a360cf56b0435a4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043859"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych <xref:System.Windows.Automation> w przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programie, [Zobacz interfejs API usługi Windows Automation: Automatyzacja](https://go.microsoft.com/fwlink/?LinkID=156746)interfejsu użytkownika.  
  
 Ten temat zawiera listę typów formantów i skojarzonych z nimi wzorców kontrolek.  
  
 W poniższej tabeli przedstawiono Wzorce formantów w następujących kategoriach:  
  
- Obsługiwał. Kontrolka musi obsługiwać ten wzorzec kontrolki.  
  
- Obsługa warunkowa. Kontrolka może obsługiwać ten wzorzec kontrolki w zależności od stanu formantu.  
  
- Nieobsługiwane. Formant nie obsługuje tego wzorca kontrolki; formanty niestandardowe mogą obsługiwać ten wzorzec kontrolki.  
  
> [!NOTE]
> Niektóre kontrolki mają warunkową obsługę kilku wzorców kontroli w zależności od funkcjonalności formantu. Na przykład kontrolka element menu ma obsługę <xref:System.Windows.Automation.InvokePattern>warunkową dla wzorca, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, lub <xref:System.Windows.Automation.SelectionItemPattern> formantu, w zależności od jego funkcji w kontrolce menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów  
  
|Typ formantu|Obsługiwane|Obsługa warunkowa|Nieobsługiwane|  
|------------------|---------------|-------------------------|-------------------|  
|Przycisk|Brak|Invoke, Przełącz, Rozwiń Zwiń|Brak|  
|Kalendarz|Siatka, tabela|Zaznaczenie, przewijanie|Wartość|  
|Pole wyboru|przełączanie|Brak|Brak|  
|pole kombi|Rozwiń Zwiń|Wybór, wartość|Scroll|  
|siatka danych|Siatka|Przewijanie, Zaznaczanie, tabela|Brak|  
|Element danych|SelectionItem|Rozwiń Zwiń, element siatki, element przewijania, tabela, przełącznik, wartość|Brak|  
|dokument|Tekst|Przewijanie, wartość|Brak|  
|Edytowanie|Brak|Tekst, wartość zakresu, wartość|Brak|  
|Grupa|Brak|Rozwiń Zwiń|Brak|  
|nagłówek|Brak|Transformacja|Brak|  
|element nagłówka|Brak|Przekształcanie, wywoływanie|Brak|  
|Hyperlink|wywoływanie|Wartość|Brak|  
|Obraz|Brak|Element siatki, element tabeli|Invoke, element zaznaczenia|  
|Lista|Brak|Siatka, wiele widoków, przewijanie, Zaznaczanie|tabela|  
|Element listy|SelectionItem|Rozwiń Zwiń, element siatki, wywołaj, przewiń element, przełącznik, wartość|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Rozwiń Zwiń, Zadokuj, Przekształć|Brak|  
|Element menu|Brak|Rozwiń Zwiń, wywołaj, zaznacz element, przełącz|Brak|  
|Pane|Brak|Zadokuj. Przewiń, Przekształć|Okno|  
|pasek postępu|Brak|Wartość zakresu, wartość|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Suwak|Brak|Wartość zakresu, wybór, wartość|Brak|  
|pokrętło|Brak|Wartość zakresu, wybór, wartość|Brak|  
|przycisk podziału|Invoke, rozwiń przycisk Zwiń|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|wywoływanie|  
|tabela|Siatka, element siatki, tabela, element tabeli|Brak|Brak|  
|Tekst|Brak|Element siatki, element tabeli, tekst|Wartość|  
|Thumb|Transformacja|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Pasek narzędzi|Brak|Zadokuj, rozwiń, Przekształć|Brak|  
|Etykietka narzędzia|Brak|Tekst, okno|Brak|  
|Drzewo|Brak|Przewiń, zaznacz|Brak|  
|element drzewa|Rozwiń Zwiń|Invoke, przewijanie elementu, Zaznaczanie elementu, przełączanie|Brak|  
|Okno|Przekształcanie, okno|Zadokuj|Brak|  
  
> [!NOTE]
> Jeśli typ formantu nie zawiera żadnych obsługiwanych wzorców kontroli, ale ma jeden lub więcej nieobsługiwanych warunkowo wzorców kontroli, jeden z tych wzorców kontroli warunkowej będzie obsługiwany przez cały czas.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
