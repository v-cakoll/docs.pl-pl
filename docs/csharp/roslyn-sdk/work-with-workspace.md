---
title: Praca z zestawu SDK platformy kompilatora .NET modelu obszaru roboczego
description: Ten przegląd zawiera opis używanego do wykonywania zapytań i modyfikowania obszaru roboczego i projekty dla kodu typu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 7d450b31cbf2c83c79552d1ace3a1ae692bfdd88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33354806"
---
# <a name="work-with-a-workspace"></a>Praca z obszaru roboczego

**Obszarów roboczych** warstwa jest punkt początkowy podczas analizy kodu i refaktoryzacji za pośrednictwem całego rozwiązania. W tej warstwie API obszaru roboczego pomaga w organizowanie wszystkie informacje dotyczące projektów w rozwiązaniu do pojedynczego obiektu modelu, oferty można bezpośredni dostęp do modeli obiektów warstwy kompilatora tekst źródłowy, drzewa składni, semantycznych modeli i kompilacje, bez konieczności analizy plików, skonfiguruj opcje lub zarządzać współzależności między projektami. 

Host środowiskach, takich jak IDE, podaj obszaru roboczego dla Ciebie odpowiadający otwartego rozwiązania. Jest również możliwe po prostu podczas ładowania pliku rozwiązania za pomocą tego modelu poza IDE.

## <a name="workspace"></a>Obszar roboczy

Obszar roboczy jest active reprezentacja rozwiązania jako kolekcja projektów, każda z kolekcji dokumentów. Obszar roboczy jest zwykle powiązany środowisku hosta, który jest ciągle zmieniana jako typy użytkownika lub zmienia właściwości. 

<xref:Microsoft.CodeAnalysis.Workspace> Zapewnia dostęp do bieżącego modelu rozwiązania. W przypadku zmiany w środowisku hosta obszaru roboczego generowane odpowiednie zdarzenia i <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> właściwość jest aktualizowana. Na przykład gdy typy użytkownika w edytorze tekstów odpowiadającego dokumentów źródłowych, obszaru roboczego używa zdarzenia sygnalizują, zmiana modelu ogólnego rozwiązania, który dokument został zmodyfikowany. Można następnie reagują tych zmian, analizowanie nowy model pod kątem poprawności, wyróżnianie obszarów istotności lub czyniąc sugestię zmiany kodu. 

Można również utworzyć autonomiczny obszarów roboczych, które są odłączone od środowiska hosta lub w aplikacji, która ma nie środowisku hosta.

## <a name="solutions-projects-documents"></a>Rozwiązania, projekty, dokumentów

Obszar roboczy może zmienić za każdym razem, gdy zostanie naciśnięty klawisz, ale można pracować z modelem rozwiązania osobno. 

Rozwiązanie jest niezmienialny modelu projektów i dokumentów. Oznacza to, że modelu mogą być współużytkowane bez blokowania lub dublowania. Po uzyskaniu wystąpieniem rozwiązania z <xref:Microsoft.CodeAnalysis.Workspace.CurrentSolution?displayProperty=nameWithType> właściwości, to wystąpienie zostanie nigdy nie ulegną zmianie. Jednak takie jak z drzewa składni i kompilacji, można zmodyfikować rozwiązania, tworząc nowe wystąpienia na podstawie istniejących rozwiązań i określonych zmian. Aby uzyskać obszar roboczy, aby odzwierciedlić zmiany, należy jawnie zastosować zmienione rozwiązania powrót do obszaru roboczego.

Projekt jest częścią modelu ogólne niezmienne rozwiązania. Reprezentuje wszystkie dokumenty kodu źródłowego, analizy i kompilacja opcji oraz zarówno zestawu i odwołania projektu do projektu. Z projektem można uzyskać dostępu do odpowiedniego kompilacji bez konieczności określania zależności projektu lub analizy plików źródłowych.

Dokument jest również częścią modelu ogólne niezmienne rozwiązania. Dokument reprezentuje plik jednego źródła, z którego można uzyskać dostępu do tekstu pliku, drzewa składni i modelu semantycznego.

Poniższy diagram to reprezentacja powiązań obszaru roboczego do hosta środowiska, narzędzia i jak zostały wprowadzone zmiany.

![relacje między różnych elementów obszaru roboczego zawierające projekty i plików źródłowych](media/work-with-workspace/workspace-obj-relations.png)

## <a name="summary"></a>Podsumowanie

Roslyn udostępnia zestaw kompilatora interfejsów API i interfejsów API obszarów roboczych, zapewniający zaawansowanych informacji na temat kodu źródłowego, na którym jest pełną zgodność z C# i Visual Basic języków.  Zestaw SDK platformy .NET kompilatora znacznie zmniejsza barierę tworzenia fokus kodu narzędzi i aplikacji. Tworzy wiele możliwości innowacji w obszarach, takich jak meta-programowania, generowanie kodu i przekształcenie interakcyjne używają w językach C# i VB i osadzania C# i VB w określonych języków domeny.  
