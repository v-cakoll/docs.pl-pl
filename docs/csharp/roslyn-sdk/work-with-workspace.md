---
title: Współpraca z modelem obszaru roboczego zestawu .NET Compiler Platform SDK
description: To omówienie zawiera informacje o typie używanym do wykonywania zapytań i manipulowania obszarem roboczym oraz projektami dla kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: a2e69129a869707eaec3516310a72f1fc918ca26
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346910"
---
# <a name="work-with-a-workspace"></a>Korzystanie z obszaru roboczego

Warstwa **obszarów roboczych** jest punktem początkowym do przeprowadzania analizy kodu i refaktoryzacji całego rozwiązania. W ramach tej warstwy interfejs API obszaru roboczego pomaga w organizowaniu wszystkich informacji o projektach w rozwiązaniu w jednym modelu obiektów, co zapewnia bezpośredni dostęp do modeli obiektów warstwy kompilatora, takich jak tekst źródłowy, drzewa składniowe, modele semantyczne i kompilacje bez potrzeby analizowania plików, konfigurowania opcji lub zarządzania zależnościami między projektami. 

Środowiska hosta, takie jak środowisko IDE, udostępniają obszar roboczy odpowiadający otwartemu rozwiązaniu. Istnieje również możliwość użycia tego modelu poza IDE przez po prostu załadowanie pliku rozwiązania.

## <a name="workspace"></a>Obszar roboczy

Obszar roboczy to aktywna reprezentacja Twojego rozwiązania jako kolekcja projektów, z których każda jest kolekcją dokumentów. Obszar roboczy jest zwykle powiązany ze środowiskiem hosta, które stale zmieniają się jako typy użytkowników lub manipulowanie właściwościami. 

<xref:Microsoft.CodeAnalysis.Workspace> zapewnia dostęp do bieżącego modelu rozwiązania. Gdy wystąpi zmiana w środowisku hosta, obszar roboczy uruchamia odpowiednie zdarzenia, a właściwość <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> jest aktualizowana. Na przykład, gdy użytkownik wpisze w edytorze tekstu odpowiadający jednemu z dokumentów źródłowych, w obszarze roboczym jest używane zdarzenie do sygnalizowania, że ogólny model rozwiązania został zmieniony i który dokument został zmodyfikowany. Następnie można reagować na te zmiany, analizując nowy model pod kątem poprawności, wyróżniania obszarów istotnych lub sugestii zmiany kodu. 

Można również tworzyć autonomiczne obszary robocze, które są odłączone od środowiska hosta lub używane w aplikacji, która nie ma środowiska hosta.

## <a name="solutions-projects-documents"></a>Rozwiązania, projekty, dokumenty

Mimo że obszar roboczy może ulec zmianie przy każdym naciśnięciu klawisza, można współpracować z modelem rozwiązania w izolacji. 

Rozwiązanie jest niezmiennym modelem projektów i dokumentów. Oznacza to, że model może być współużytkowany bez blokowania lub duplikowania. Po uzyskaniu wystąpienia rozwiązania z właściwości <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> to wystąpienie nigdy nie zmieni się. Jednak podobnie jak w przypadku drzew składni i kompilacji, można modyfikować rozwiązania, tworząc nowe wystąpienia na podstawie istniejących rozwiązań i konkretnych zmian. Aby można było uwzględnić zmiany w obszarze roboczym, należy jawnie zastosować zmienione rozwiązanie z powrotem do obszaru roboczego.

Projekt jest częścią ogólnego niezmiennego modelu rozwiązania. Reprezentuje wszystkie dokumenty kodu źródłowego, opcje analizy i kompilacji oraz odwołania do zestawu i projektu do projektu. Z projektu można uzyskać dostęp do odpowiedniej kompilacji bez konieczności określania zależności projektu lub analizowania plików źródłowych.

Dokument jest również częścią ogólnego niezmiennego modelu rozwiązania. Dokument reprezentuje pojedynczy plik źródłowy, z którego można uzyskać dostęp do tekstu pliku, drzewa składni i modelu semantycznego.

Na poniższym diagramie przedstawiono sposób odnoszący się do środowiska hosta, narzędzi i sposobu wprowadzania zmian w obszarze roboczym.

![relacje między różnymi elementami obszaru roboczego zawierającego projekty i pliki źródłowe](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Podsumowanie

Roslyn uwidacznia zestaw interfejsów API kompilatora i interfejsów API obszarów roboczych, które udostępniają bogate informacje o kodzie źródłowym i mają pełną wierność w językach C# i Visual Basic.  Zestaw .NET Compiler Platform SDK znacząco obniża barierę do wprowadzenia do tworzenia narzędzi i aplikacji ukierunkowanych na kod. Tworzy wiele możliwości innowacji w obszarach, takich jak meta-programowanie, generowanie kodu i przekształcanie, interaktywne użycie języków C# i Visual Basic oraz osadzanie C# i Visual Basic w językach specyficznych dla domeny.  
