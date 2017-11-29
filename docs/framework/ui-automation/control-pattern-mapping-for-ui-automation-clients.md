---
title: "Mapowanie wzorców formantów dla klientów automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, for UI Automation clients
- UI Automation, clients, control patterns for
ms.assetid: 8b81645b-8be3-4e26-9c98-4fb0fceca06b
caps.latest.revision: "18"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 31beb7ab9a978f5bb379a3c1d61c90c19c26ca6b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="control-pattern-mapping-for-ui-automation-clients"></a>Mapowanie wzorców kontrolek dla klientów automatyzacji interfejsu użytkownika
> [!NOTE]
>  Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw. Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Ten temat zawiera listę typów kontroli oraz ich wzorce skojarzonym formancie.  
  
 Poniższa tabela umożliwia organizowanie wzorce formantów na następujące kategorie:  
  
-   Obsługiwane. Kontrolka musi obsługiwać tego wzorca formantu.  
  
-   Obsługa warunkowego. Formant może obsługiwać tego wzorca kontrolki, w zależności od stanu formantu.  
  
-   Nieobsługiwane. Formant nie obsługuje tego wzorca formantu; Formanty niestandardowe mogą obsługiwać tego wzorca formantu.  
  
> [!NOTE]
>  Niektóre formanty mają warunkowego obsługę kilku wzorców formantu w zależności od funkcji formantu. Na przykład kontrolki elementu menu ma warunkowego obsługę <xref:System.Windows.Automation.InvokePattern>, <xref:System.Windows.Automation.ExpandCollapsePattern>, <xref:System.Windows.Automation.TogglePattern>, lub <xref:System.Windows.Automation.SelectionItemPattern> — wzorzec kontrolki, w zależności od jej funkcji w formancie menu.  
  
<a name="control_mapping_clients"></a>   
## <a name="ui-automation-control-patterns-for-clients"></a>Wzorce kontrolek automatyzacji interfejsu użytkownika dla klientów  
  
|Typ formantu|Obsługiwane|Obsługa warunkowe|Nieobsługiwane|  
|------------------|---------------|-------------------------|-------------------|  
|Przycisk|Brak|Wywołanie przełącznik, a następnie rozwiń zwiń|Brak|  
|Kalendarz|Siatki, tabeli|Wybór, przewijania|Wartość|  
|Pole wyboru|przełączanie|Brak|Brak|  
|pole kombi|Rozwiń węzeł Zwiń|Wybór, wartość|Scroll|  
|siatka danych|Siatka|Tabela przewijania, wybór,|Brak|  
|Element danych|SelectionItem|Rozwiń Zwiń, elementu siatki, element przewijania, tabeli, Przełącz, wartość|Brak|  
|dokument|Tekst|Przewiń, wartość|Brak|  
|Edytowanie|Brak|Wartość tekstową, wartość zakresu|Brak|  
|Grupa|Brak|Rozwiń węzeł Zwiń|Brak|  
|nagłówek|Brak|Transformacja|Brak|  
|element nagłówka|Brak|Przekształć, wywołaj|Brak|  
|Hyperlink|wywoływanie|Wartość|Brak|  
|Obraz|Brak|Element siatki, element tabeli|Wywołanie elementu zaznaczenia|  
|Lista|Brak|Przewijania siatki, wiele widoku, wybór|tabela|  
|Element listy|SelectionItem|Rozwiń węzeł Zwiń, elementu siatki Invoke, przewiń elementu, Przełącz, wartość|Brak|  
|Menu|Brak|Brak|Brak|  
|pasek menu|Brak|Rozwiń węzeł Zwiń, dokowania, transformacji|Brak|  
|Element menu|Brak|Rozwiń Zwiń, wywołania elementu wyboru Przełącz|Brak|  
|Pane|Brak|Dokowania. Przewiń, transformacja|Okno|  
|pasek postępu|Brak|Wartość zakresu, wartość|Brak|  
|przycisk radiowy|SelectionItem|Brak|przełączanie|  
|pasek przewijania|Brak|wartość zakresu|Scroll|  
|Separator|Brak|Brak|Brak|  
|Suwak|Brak|Zakres, wybór, wartość|Brak|  
|pokrętło|Brak|Zakres, wybór, wartość|Brak|  
|przycisk podziału|Wywołanie, Rozwiń Zwiń|Brak|Brak|  
|pasek stanu|Brak|Siatka|Brak|  
|Tab|Wybór|Scroll|Brak|  
|element karty|SelectionItem|Brak|wywoływanie|  
|tabela|Siatki elementów siatki, tabeli, element tabeli|Brak|Brak|  
|Tekst|Brak|Tekst elementu, element tabeli siatki|Wartość|  
|Thumb|Transformacja|Brak|Brak|  
|pasek tytułu|Brak|Brak|Brak|  
|Pasek narzędzi|Brak|Dokowanie, Rozwiń Zwiń, Przekształć|Brak|  
|Etykietka narzędzia|Brak|Tekst, okno|Brak|  
|Drzewo|Brak|Przewiń, wybór|Brak|  
|element drzewa|Rozwiń węzeł Zwiń|Wywołanie elementu przewijania SelectionItem, Przełącz|Brak|  
|Okno|Przekształcanie, okno|Doku.|Brak|  
  
> [!NOTE]
>  Jeśli typ formantu nie wzorców formantu obsługiwanych na liście, ale ma co najmniej jeden wzorców formantu warunkowo obsługiwane będą jeden z tych wzorców formantu warunkowego obsługiwane przez cały czas.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-overview.md)
