---
title: Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
description: Wyświetl tabelę mapowania wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika. Akcje dla niektórych typów formantów mogą być obsługiwane, warunkowo obsługiwane lub nieobsługiwane.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 7673ce4ac88cc36a7c35e2e946a31d23b2ce6eca
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164183"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla .NET Framework deweloperów, którzy chcą korzystać z zarządzanych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , zobacz [interfejs API usługi Windows Automation: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 Ten temat zawiera listę typów formantów i skojarzonych z nimi wzorców kontrolek.  
  
 W poniższej tabeli przedstawiono Wzorce formantów w następujących kategoriach:  
  
- Obsługiwane. Kontrolka musi obsługiwać ten wzorzec kontrolki.  
  
- Obsługa warunkowa. Kontrolka może obsługiwać ten wzorzec kontrolki w zależności od stanu formantu.  
  
- Nieobsługiwane. Formant nie obsługuje tego wzorca kontrolki; formanty niestandardowe mogą obsługiwać ten wzorzec kontrolki.  
  
> [!NOTE]
> Niektóre kontrolki mają warunkową obsługę kilku wzorców kontroli w zależności od funkcjonalności formantu. Na przykład kontrolka element menu ma obsługę warunkową dla <xref:System.Windows.Automation.InvokePattern> wzorca, <xref:System.Windows.Automation.ExpandCollapsePattern> , <xref:System.Windows.Automation.TogglePattern> , lub <xref:System.Windows.Automation.SelectionItemPattern> formantu, w zależności od jego funkcji w kontrolce menu.  
  
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
|Dokument|Tekst|Przewijanie, wartość|Brak|  
|Edytuj|Brak|Tekst, wartość zakresu, wartość|Brak|  
|Grupa|Brak|Rozwiń Zwiń|Brak|  
|Nagłówek|Brak|Przekształcanie|Brak|  
|element nagłówka|Brak|Przekształcanie, wywoływanie|Brak|  
|Hyperlink|Invoke|Wartość|Brak|  
|Image (Obraz)|Brak|Element siatki, element tabeli|Invoke, element zaznaczenia|  
|Lista|Brak|Siatka, wiele widoków, przewijanie, Zaznaczanie|Tabela|  
|Element listy|SelectionItem|Rozwiń Zwiń, element siatki, wywołaj, przewiń element, przełącznik, wartość|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Rozwiń Zwiń, Zadokuj, Przekształć|Brak|  
|Element menu|Brak|Rozwiń Zwiń, wywołaj, zaznacz element, przełącz|Brak|  
|Pane|Brak|Zadokuj. Przewiń, Przekształć|Okno|  
|pasek postępu|Brak|Wartość zakresu, wartość|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Slider|Brak|Wartość zakresu, wybór, wartość|Brak|  
|pokrętło|Brak|Wartość zakresu, wybór, wartość|Brak|  
|przycisk podziału|Invoke, rozwiń przycisk Zwiń|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|Invoke|  
|Tabela|Siatka, element siatki, tabela, element tabeli|Brak|Brak|  
|Tekst|Brak|Element siatki, element tabeli, tekst|Wartość|  
|Thumb|Przekształcanie|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Pasek narzędzi|Brak|Zadokuj, rozwiń, Przekształć|Brak|  
|Etykietka narzędzia|Brak|Tekst, okno|Brak|  
|Drzewo|Brak|Przewiń, zaznacz|Brak|  
|element drzewa|Rozwiń Zwiń|Invoke, przewijanie elementu, Zaznaczanie elementu, przełączanie|Brak|  
|Okno|Przekształcanie, okno|Dock|Brak|  
  
> [!NOTE]
> Jeśli typ formantu nie zawiera żadnych obsługiwanych wzorców kontroli, ale ma jeden lub więcej nieobsługiwanych warunkowo wzorców kontroli, jeden z tych wzorców kontroli warunkowej będzie obsługiwany przez cały czas.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
