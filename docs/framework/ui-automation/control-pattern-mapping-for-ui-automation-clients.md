---
title: Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
ms.openlocfilehash: 689e649343c93d0670c6870098a09f61097f4fb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180227"
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
> Ta dokumentacja jest przeznaczona dla deweloperów [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] programu .NET <xref:System.Windows.Automation> Framework, którzy chcą używać klas zarządzanych zdefiniowanych w obszarze nazw. Aby uzyskać najnowsze [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]informacje na temat interfejsu [API automatyzacji systemu Windows: Automatyzacja interfejsu użytkownika](/windows/win32/winauto/entry-uiauto-win32).  
  
 W tym temacie wymieniono typy formantów i skojarzone z nimi wzorce kontroli.  
  
 W poniższej tabeli wzorce kontroli są podzielone na następujące kategorie:  
  
- Obsługiwane. Formant musi obsługiwać ten wzorzec sterowania.  
  
- Obsługa warunkowa. Formant może obsługiwać ten wzorzec kontroli w zależności od stanu formantu.  
  
- Bez pomocy technicznej. Formant nie obsługuje tego wzorca sterowania; formantów niestandardowych może obsługiwać ten wzorzec kontroli.  
  
> [!NOTE]
> Niektóre formanty mają warunkową obsługę kilku wzorców kontroli w zależności od funkcjonalności formantu. Na przykład formant elementu menu ma <xref:System.Windows.Automation.InvokePattern> <xref:System.Windows.Automation.ExpandCollapsePattern>warunkową <xref:System.Windows.Automation.TogglePattern>obsługę <xref:System.Windows.Automation.SelectionItemPattern> wzorca , , lub formantu, w zależności od jego funkcji w formancie menu.  
  
<a name="control_mapping_clients"></a>
## <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów  
  
|Typ sterowania|Obsługiwane|Pomoc techniczna warunkowa|Nieobsługiwane|  
|------------------|---------------|-------------------------|-------------------|  
|Button|Brak|Wywoływanie, przełączanie, rozwijanie zwijania|Brak|  
|Kalendarz|Siatka, Tabela|Wybór, Przewijanie|Wartość|  
|Pole wyboru|przełączanie|Brak|Brak|  
|pole kombi|Rozwiń zwiń|Wybór, Wartość|Scroll|  
|siatka danych|Siatka|Przewijanie, zaznaczanie, tabela|Brak|  
|Element danych|SelectionItem|Rozwiń zwiń, Element siatki, Przewiń element, Tabela, Przełącznik, Wartość|Brak|  
|Dokument|Tekst|Przewijanie, wartość|Brak|  
|Edytuj|Brak|Tekst, wartość zakresu, wartość|Brak|  
|Grupa|Brak|Rozwiń zwiń|Brak|  
|Nagłówek|Brak|Przekształcanie|Brak|  
|element nagłówka|Brak|Przekształcanie, wywoływanie|Brak|  
|Hyperlink|Invoke|Wartość|Brak|  
|Image (Obraz)|Brak|Element siatki, element tabeli|Wywoływanie, element zaznaczenia|  
|List|Brak|Siatka, widok wielokrotny, przewijanie, zaznaczanie|Tabela|  
|Element listy|SelectionItem|Rozwiń zwijanie, element siatki, wywoływanie, przewijanie elementu, przełącznik, wartość|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Rozwiń zwijanie, dokowanie, przekształcanie|Brak|  
|Element menu|Brak|Rozwiń zwijanie, wywoływanie, element zaznaczenia, przełączanie|Brak|  
|Pane|Brak|Dock. Przewijanie, przekształcanie|Okno|  
|pasek postępu|Brak|Wartość zakresu, wartość|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Suwak|Brak|Wartość zakresu, wybór, wartość|Brak|  
|pokrętło|Brak|Wartość zakresu, wybór, wartość|Brak|  
|przycisk podziału|Wywoływanie, rozwijanie zwijania|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|Invoke|  
|Tabela|Siatka, Zapas siatki, Tabela, Element tabeli|Brak|Brak|  
|Tekst|Brak|Element siatki, Element tabeli, Tekst|Wartość|  
|Thumb|Przekształcanie|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Pasek narzędzi|Brak|Dok, rozwiń zwijanie, przekształcanie|Brak|  
|Etykietka narzędzia|Brak|Tekst, Okno|Brak|  
|Drzewo|Brak|Przewijanie, wybór|Brak|  
|element drzewa|Rozwiń zwiń|Wywoływanie, przewijanie elementu, element zaznaczenia, przełączanie|Brak|  
|Okno|Transformacja, Okno|Dock|Brak|  
  
> [!NOTE]
> Jeśli typ formantu nie ma obsługiwanych wzorców kontroli na liście, ale ma jeden lub więcej wzorców kontroli obsługiwane warunkowo, a następnie jeden z tych wzorców kontroli warunkowej będą obsługiwane przez cały czas.  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd automatyzacji interfejsu użytkownika](ui-automation-overview.md)
