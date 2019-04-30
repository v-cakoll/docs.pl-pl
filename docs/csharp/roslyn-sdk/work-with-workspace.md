---
title: Praca z modelem obszaru roboczego zestawu SDK platformy kompilatora .NET
description: W tym omówieniu przedstawiono opis tego typu, którego używasz do wykonywania zapytań i manipulowania obszar roboczy i projekty kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 7d450b31cbf2c83c79552d1ace3a1ae692bfdd88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706513"
---
# <a name="work-with-a-workspace"></a>Korzystanie z obszaru roboczego

**Obszary robocze** warstwa jest punktem wyjścia do wykonywania analizy kodu i refaktoryzacji za pośrednictwem całego rozwiązania. W tej warstwie API obszaru roboczego pomaga w organizowania wszystkie informacje dotyczące projektów w rozwiązaniu do pojedynczego obiektu modelu, umożliwiamy Ci bezpośredni dostęp do modeli obiektów warstwy kompilatora, takich jak tekst źródłowy, drzewa składni semantycznych modeli i kompilacje, bez konieczności przeanalizować plików, skonfiguruj opcje lub Zarządzaj współzależności między projektami. 

Środowiska hosta, takich jak środowisko IDE zapewniają obszaru roboczego dla Ciebie odpowiadający otwartego rozwiązania. Istnieje również możliwość użycia tego modelu poza środowisko IDE, po prostu ładowanie pliku rozwiązania.

## <a name="workspace"></a>Obszar roboczy

Obszar roboczy jest aktywny reprezentację w postaci rozwiązania jako kolekcja projektów, każda grupa zawiera kolekcję dokumentów. Obszar roboczy jest zazwyczaj powiązane środowisko hosta, która nieustannie jako typy użytkowników, lub zmienia właściwości. 

<xref:Microsoft.CodeAnalysis.Workspace> Zapewnia dostęp do bieżącego modelu rozwiązania. W przypadku zmiany w środowisku hosta obszaru roboczego generowane pokrewnych zdarzeń oraz <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> zaktualizować właściwości. Na przykład po użytkownik wpisze w edytorze tekstów, odpowiadające dokumentów źródłowych, obszar roboczy używa zdarzenia do sygnalizowania, że zmienił się ogólnym modelu rozwiązania i który dokument został zmodyfikowany. Te zmiany mogą reagować następnie przez analizowanie nowego modelu pod kątem poprawności, w celu wyróżnienia obszarów o znaczeniu lub dokonywania sugestię dotyczącą zmiany w kodzie. 

Można również utworzyć autonomiczny obszary robocze, które są odłączone od środowiska hosta lub używane w aplikacji, która ma żadnego środowiska hosta.

## <a name="solutions-projects-documents"></a>Rozwiązania, projekty, dokumentów

Za każdym razem, gdy zostanie naciśnięty, może zmienić obszar roboczy, ale możesz pracować z modelem rozwiązania w izolacji. 

Rozwiązanie to niezmienne model projektów i dokumentów. Oznacza to, że modelu mogą być udostępniane bez blokowania lub dublowania. Po uzyskaniu wystąpienia rozwiązania <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> właściwości tego wystąpienia nigdy nie ulegnie zmianie. Jednak takie jak przy użyciu drzewa składni i kompilacji, można zmodyfikować rozwiązania tworząc nowe wystąpienia na podstawie istniejących rozwiązań i określonych zmian. Aby uzyskać obszar, aby odzwierciedlać wprowadzone zmiany, że wyraźnie zastosujesz zmienionego rozwiązania do obszaru roboczego.

Projekt jest częścią modelu rozwiązania ogólną niezmienne. Reprezentuje wszystkie dokumenty kodu źródłowego, opcje analizy i kompilacja i zarówno zestaw i odwołania projekt projekt. Z poziomu projektu możesz uzyskać dostęp odpowiednich kompilacji, bez konieczności określenia zależności projektu lub przeanalizować plików źródłowych.

Dokument jest również częścią modelu rozwiązania ogólną niezmienne. Dokument reprezentuje plik pojedyncze źródło, z którego można uzyskać dostęp tekst pliku, w drzewie składni i semantycznego modelu.

Poniższy diagram jest reprezentacją jak obszar roboczy odnosi się do hosta, środowisko, narzędzia i jak zostały wprowadzone zmiany.

![relacje między różne elementy obszaru roboczego zawierającego projektów i plików źródłowych](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Podsumowanie

Roslyn ujawnia zestaw kompilatora interfejsów API i interfejsów API obszarów roboczych, która zapewnia bogate informacje o kodzie źródłowym i ma pełną zgodność z C# i języków Visual Basic.  Zestaw SDK platformy kompilatora .NET znacznie zmniejsza barierę dla tworzenia skoncentrowane na kodzie narzędzi i aplikacji. Tworzy wiele możliwości do innowacji w obszarach, takich jak meta-programowania, generowanie kodu i transformacji, interaktywne korzystanie z języków C# i VB i osadzanie języka C# i VB w języki specyficzne dla domeny.  
