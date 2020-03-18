---
title: Praca z modelem obszaru roboczego sdk platformy kompilatora .NET
description: Ten przegląd zawiera zrozumienie typu używanego do wykonywania zapytań i manipulowania obszarem roboczym i projektami dla kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: d21873b132d5f0788033693a319e556feeac59a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156886"
---
# <a name="work-with-a-workspace"></a>Korzystanie z obszaru roboczego

Warstwa **Obszary robocze** jest punktem wyjścia do analizy kodu i refaktoryzacji w całym rozwiązaniu. W tej warstwie interfejs API obszaru roboczego pomaga w organizowaniu wszystkich informacji o projektach w rozwiązaniu w model jednego obiektu, oferując bezpośredni dostęp do modeli obiektów warstwy kompilatora, takich jak tekst źródłowy, drzewa składni, modele semantyczne i kompilacje bez konieczności analizowania plików, konfigurowania opcji lub zarządzania zależnościami między projektami.

Środowiska hosta, takie jak IDE, zapewniają obszar roboczy odpowiadający otwartemu rozwiązaniu. Istnieje również możliwość użycia tego modelu poza IDE po prostu ładując plik rozwiązania.

## <a name="workspace"></a>Workspace

Obszar roboczy jest aktywną reprezentacją rozwiązania jako kolekcji projektów, z których każdy ma kolekcję dokumentów. Obszar roboczy jest zazwyczaj powiązany ze środowiskiem hosta, które stale się zmienia jako typy użytkowników lub manipuluje właściwościami.

Zapewnia <xref:Microsoft.CodeAnalysis.Workspace> dostęp do bieżącego modelu rozwiązania. Po wystąpieniu zmiany w środowisku hosta obszar roboczy <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> uruchamia odpowiednie zdarzenia, a właściwość jest aktualizowana. Na przykład gdy użytkownik wpisze w edytorze tekstu odpowiadającym jednemu z dokumentów źródłowych, obszar roboczy używa zdarzenia, aby zasygnalizować, że ogólny model rozwiązania został zmieniony i który dokument został zmodyfikowany. Następnie można reagować na te zmiany, analizując nowy model poprawności, wyróżniając obszary o znaczeniu lub sugerując zmianę kodu.

Można również utworzyć autonomiczne obszary robocze, które są odłączone od środowiska hosta lub używane w aplikacji, która nie ma środowiska hosta.

## <a name="solutions-projects-documents"></a>Rozwiązania, projekty, dokumenty

Mimo że obszar roboczy może ulec zmianie za każdym razem, gdy klawisz jest naciśnięty, można pracować z modelem rozwiązania w izolacji.

Rozwiązanie jest niezmiennym modelem projektów i dokumentów. Oznacza to, że model może być współużytkowany bez blokowania lub duplikacji. Po uzyskaniu wystąpienia rozwiązania <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> z właściwości, to wystąpienie nigdy się nie zmieni. Jednak podobnie jak w przypadku drzew składni i kompilacji, można modyfikować rozwiązania, tworząc nowe wystąpienia na podstawie istniejących rozwiązań i określonych zmian. Aby uzyskać obszar roboczy, aby odzwierciedlić zmiany, należy jawnie zastosować zmienione rozwiązanie z powrotem do obszaru roboczego.

Projekt jest częścią ogólnego modelu rozwiązania niezmienne. Reprezentuje wszystkie dokumenty kodu źródłowego, analizować i kompilacji opcji i zarówno odniesienia do zestawu i projektu do projektu. Z projektu można uzyskać dostęp do odpowiedniej kompilacji bez konieczności określania zależności projektu lub analizować pliki źródłowe.

Dokument jest również częścią ogólnego modelu rozwiązania niezmienne. Dokument reprezentuje pojedynczy plik źródłowy, z którego można uzyskać dostęp do tekstu pliku, drzewa składni i modelu semantycznego.

Na poniższym diagramie przedstawiono sposób, w jaki obszar roboczy odnosi się do środowiska hosta, narzędzi i sposobu wprowadzania edycjacji.

![relacje między różnymi elementami obszaru roboczego zawierającego projekty i pliki źródłowe](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Podsumowanie

Roslyn udostępnia zestaw interfejsów API kompilatora i obszarów roboczych interfejsów API, który zawiera bogate informacje o kodzie źródłowym i który ma pełną wierność z językami Języka C# i Visual Basic.  Zestaw SDK platformy kompilatora .NET znacznie obniża barierę wejścia do tworzenia narzędzi i aplikacji zorientowanych na kod. Stwarza wiele możliwości innowacji w obszarach, takich jak meta-programowania, generowania kodu i transformacji, interaktywne użycie języków Języka C# i Visual Basic i osadzania Języka C# i Visual Basic w językach specyficznych dla domeny.  
