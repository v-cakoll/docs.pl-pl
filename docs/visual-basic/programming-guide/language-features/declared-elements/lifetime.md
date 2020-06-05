---
title: Okres istnienia
ms.date: 07/20/2015
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
ms.openlocfilehash: 377f0e0b5240c3da931dc4af5439aba8924f1e81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357144"
---
# <a name="lifetime-in-visual-basic"></a>Okres istnienia w Visual Basic
Okres *istnienia* zadeklarowanego elementu to okres czasu, w którym jest dostępny do użycia. Zmienne są jedynymi elementami, które mają okres istnienia. W tym celu kompilator traktuje parametry procedury i funkcja zwraca jako specjalne przypadki zmiennych. Okres istnienia zmiennej reprezentuje okres czasu, w którym może być przechowywana wartość. Jego wartość może ulec zmianie w okresie istnienia, ale zawsze utrzymuje pewną wartość.  
  
## <a name="different-lifetimes"></a>Różne okresy istnienia  
 *Zmienna członkowska* (zadeklarowana na poziomie modułu, poza żadną procedurą) zazwyczaj ma ten sam okres istnienia co element, w którym jest zadeklarowany. Zmienna nieudostępniona zadeklarowana w klasie lub strukturze istnieje jako oddzielna kopia dla każdego wystąpienia klasy lub struktury, w której jest zadeklarowana. Każda taka zmienna ma ten sam okres istnienia, co jego wystąpienie. Jednak `Shared` zmienna ma tylko jeden okres istnienia, który jest cały czas działania aplikacji.  
  
 *Zmienna lokalna* (zadeklarowana wewnątrz procedury) istnieje tylko w czasie, gdy procedura, w której jest zadeklarowana, jest uruchomiona. Dotyczy to również parametrów tej procedury oraz zwracanych funkcji. Jeśli jednak ta procedura wywołuje inne procedury, zmienne lokalne zachowują swoje wartości podczas działania wywoływanych procedur.  
  
## <a name="beginning-of-lifetime"></a>Początek okresu istnienia  
 Okres istnienia zmiennej lokalnej rozpoczyna się, gdy kontrola przechodzi do procedury, w której jest zadeklarowana. Każda zmienna lokalna jest inicjowana do wartości domyślnej dla swojego typu danych, gdy tylko procedura zacznie działać. Gdy procedura napotka `Dim` instrukcję, która określa wartości początkowe, ustawia te zmienne na te wartości, nawet jeśli kod został już przypisany do innych wartości.  
  
 Każdy element członkowski zmiennej struktury jest inicjowany tak, jakby była to oddzielna zmienna. Podobnie każdy element zmiennej tablicowej jest inicjowany indywidualnie.  
  
 Zmienne zadeklarowane w bloku wewnątrz procedury (takie jak `For` Pętla) są inicjowane we wpisie do procedury. Te inicjalizacje zaczną obowiązywać niezależnie od tego, czy kod kiedykolwiek wykonuje blok.  
  
## <a name="end-of-lifetime"></a>Koniec okresu istnienia  
 Po zakończeniu procedury, wartości zmiennych lokalnych nie są zachowywane i Visual Basic odzyskania pamięci. Przy następnym wywołaniu procedury wszystkie jej zmienne lokalne są tworzone ponownie i inicjowane ponownie.  
  
 Gdy wystąpienie klasy lub struktury kończy się, jego nieudostępniona zmienne utraciły pamięć i ich wartości. Każde nowe wystąpienie klasy lub struktury tworzy i ponownie inicjuje swoje zmienne nieudostępnione. Jednak `Shared` zmienne są zachowywane do momentu zatrzymania działania aplikacji.  
  
## <a name="extension-of-lifetime"></a>Przedłużenie okresu istnienia  
 Jeśli zadeklarujesz zmienną lokalną za pomocą `Static` słowa kluczowego, jego okres istnienia jest dłuższy niż czas wykonywania procedury. W poniższej tabeli przedstawiono sposób, w jaki procedura deklaracji procedury określa, jak długo `Static` występuje zmienna.  
  
|Lokalizacja i udostępnianie procedury|Rozpoczyna się okres istnienia zmiennej statycznej|Koniec okresu istnienia zmiennej statycznej|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|W module (domyślnie udostępniony)|Przy pierwszym wywołaniu procedury|Gdy aplikacja przestanie działać|  
|W klasie, `Shared` (procedura nie jest składową wystąpienia)|Przy pierwszym wywołaniu procedury w konkretnym wystąpieniu lub w samej nazwie klasy lub struktury|Gdy aplikacja przestanie działać|  
|W wystąpieniu klasy, not `Shared` (procedura jest członkiem wystąpienia)|Przy pierwszym wywołaniu procedury w konkretnym wystąpieniu|Gdy wystąpienie zostanie wydane na potrzeby wyrzucania elementów bezużytecznych (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Zmienne statyczne o tej samej nazwie  
 Można zadeklarować zmienne statyczne o tej samej nazwie w więcej niż jednej procedurze. W takim przypadku kompilator Visual Basic traktuje każdą taką zmienną jako oddzielny element. Inicjalizacja jednej z tych zmiennych nie wpływa na wartości innych. Ta sama zasada ma zastosowanie, jeśli zdefiniujesz procedurę z zestawem przeciążeń i deklarujesz zmienną statyczną o tej samej nazwie w każdym przeciążeniu.  
  
## <a name="containing-elements-for-static-variables"></a>Zawierający elementy zmiennych statycznych  
 Można zadeklarować statyczną zmienną lokalną w obrębie klasy, czyli wewnątrz procedury w tej klasie. Nie można jednak zadeklarować statycznej zmiennej lokalnej w strukturze jako członka struktury lub jako zmiennej lokalnej procedury w tej strukturze.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład deklaruje zmienną ze słowem kluczowym [static](../../../language-reference/modifiers/static.md) . (Należy zauważyć, że słowo kluczowe nie jest potrzebne, `Dim` gdy [instrukcja Dim](../../../language-reference/statements/dim-statement.md) używa modyfikatora, takiego jak `Static` ).  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Komentarze  
 W poprzednim przykładzie zmienna `applesSold` nadal istnieje po `runningTotal` powrocie procedury do kodu wywołującego. Przy następnym `runningTotal` wywołaniu zostanie `applesSold` zachowana poprzednio obliczona wartość.  
  
 Jeśli `applesSold` zostały zadeklarowane bez użycia `Static` , poprzednie wartości skumulowane nie byłyby zachowywane dla wywołań do `runningTotal` . Przy następnym `runningTotal` wywołaniu zostanie `applesSold` on ponownie utworzony i zainicjowany na 0, a `runningTotal` po prostu zwróci tę samą wartość, z którą został wywołany.  
  
### <a name="compile-the-code"></a>Kompiluj kod  
 Można zainicjować wartość statycznej zmiennej lokalnej w ramach swojej deklaracji. Jeśli zadeklarujesz tablicę `Static` , możesz zainicjować jej rangę (liczbę wymiarów), długość każdego wymiaru oraz wartości poszczególnych elementów.  
  
### <a name="security"></a>Zabezpieczenia  
 W poprzednim przykładzie można utworzyć ten sam okres istnienia przez zadeklarowanie `applesSold` na poziomie modułu. Jeśli jednak w ten sposób Zmieniono zakres zmiennej, procedura nie będzie miała już wyłącznego dostępu do niej. Ponieważ inne procedury mogą uzyskać dostęp `applesSold` i zmienić jego wartość, suma uruchamiania może być niezawodna, a kod może być trudniejszy do utrzymania.  
  
## <a name="see-also"></a>Zobacz też

- [Shared](../../../language-reference/modifiers/shared.md)
- [Nothing](../../../language-reference/nothing.md)
- [Nazwy zadeklarowanych elementów](declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](references-to-declared-elements.md)
- [Zakres w Visual Basic](scope.md)
- [Poziomy dostępu w Visual Basic](access-levels.md)
- [Zmienne](../variables/index.md)
- [Deklaracja zmiennej](../variables/variable-declaration.md)
- [Rozwiązywanie problemów związanych z typami danych](../data-types/troubleshooting-data-types.md)
- [Ruchom](../../../language-reference/modifiers/static.md)
