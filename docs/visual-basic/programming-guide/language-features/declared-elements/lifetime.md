---
title: Okres istnienia w Visual Basic
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
ms.openlocfilehash: 7a8730834c5241ddb1271d689cdda8942741f15f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61917933"
---
# <a name="lifetime-in-visual-basic"></a>Okres istnienia w Visual Basic
*Okres istnienia* zadeklarowanych elementów to okres, podczas którego jest dostępny do użytku. Zmienne są tylko elementy, które mają okres istnienia. W tym celu kompilator traktuje parametry procedury, a funkcja zwraca jako specjalnych przypadków zmiennych. Okres istnienia zmiennej reprezentuje czas, w którym może zawierać wartości. Wartość można zmienić za pośrednictwem jego okres istnienia, ale zawsze zawiera niektóre wartości.  
  
## <a name="different-lifetimes"></a>Różne okresy istnienia  
 A *zmiennej składowej* (zadeklarowane na poziomie modułu, poza dowolnej procedury) zwykle ma ten sam okres istnienia jako element, w którym jest zdeklarowana. Nieudostępnionych Zmienna zadeklarowana w klasie lub strukturze istnieje jako oddzielna kopia dla każdego wystąpienia klasy lub struktury, w którym jest zdeklarowana. Każda takie zmienna ma ten sam okres istnienia jako jego wystąpienia. Jednak `Shared` zmienna ma tylko jednego okresu istnienia, który jest ważny przez cały czas działania aplikacji.  
  
 A *zmienna lokalna* (zadeklarowana wewnątrz procedury) istnieje tylko w czasie wykonywania procedury, w którym jest zdeklarowana. Dotyczy to również, aby parametry tej procedury i zwrot funkcji. Jednak jeśli tej procedury nie wywoła innych procedur, zmienne lokalne zachowują swoje wartości podczas wykonywania wywołanej procedury.  
  
## <a name="beginning-of-lifetime"></a>Początek okresu istnienia  
 Okres istnienia zmiennej lokalnej rozpoczyna się, gdy kontrolka przechodzi procedury, w której jest zadeklarowana. Co lokalne zmienna jest inicjowana na wartość domyślną dla tego typu danych, jak rozpoczyna się procedura uruchamiania. Kiedy napotka procedury `Dim` instrukcję, która określa wartości początkowe, ustawia tych zmiennych te wartości, nawet jeśli kod ma już przypisany inne wartości do nich.  
  
 Każdy element członkowski zmiennej struktury jest inicjowany, tak jakby osobnej zmiennej. Podobnie każdy element zmienną tablicową jest inicjowany indywidualnie.  
  
 Zmienne zadeklarowane wewnątrz bloku wewnątrz procedury (takie jak `For` pętli) są inicjowane przy uruchamianiu procedury. Te inicjalizacje zaczęły obowiązywać, czy nigdy nie wykonuje bloku kodu.  
  
## <a name="end-of-lifetime"></a>Koniec okresu istnienia  
 Podczas procedury składowanej, wartości jego zmienne lokalne nie są zachowywane i Visual Basic odzyskuje ich pamięci. Przy następnym wywołaniu procedury, jego zmienne lokalne są tworzone od nowa i ponownie zainicjować.  
  
 Kończy działanie wystąpienia klasy lub struktury, jego zmiennych nieudostępnionych utratę ich pamięci i ich wartości. Każde nowe wystąpienie klasy lub struktury, tworzy i ponownie inicjuje jego zmiennych nieudostępnionych. Jednak `Shared` zmienne są zachowywane, dopóki aplikacja przestaje działać.  
  
## <a name="extension-of-lifetime"></a>Przedłużenie okresu istnienia  
 Jeśli deklarowana zmienna lokalna o `Static` — słowo kluczowe, jego okres istnienia jest dłuższy niż czas wykonywania jego procedury. W poniższej tabeli przedstawiono, jak deklaracja procedury określa, jak długo `Static` istnieje zmienna.  
  
|Udostępnianie i procedury lokalizacji|Rozpoczyna się statyczny okres istnienia zmiennych|Kończy się statyczny okres istnienia zmiennych|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|W module (udostępnione domyślnie)|Procedura jest wywoływana po raz pierwszy|Gdy aplikacja przestaje działać|  
|W klasie `Shared` (procedury nie jest składową wystąpienia ")|Po raz pierwszy procedura jest wywoływana na konkretne wystąpienie lub sama nazwa klasy lub struktury|Gdy aplikacja przestaje działać|  
|W wystąpieniu klasy nie `Shared` (procedura jest składową wystąpienia)|Po raz pierwszy procedura jest wywoływana w ramach określonego wystąpienia|Po zwolnieniu wystąpienie do wyrzucania elementów bezużytecznych (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Zmienne statyczne o takiej samej nazwie  
 Można zadeklarować zmienne statyczne o tej samej nazwie w więcej niż jednej procedury. Jeśli to zrobisz, kompilator Visual Basic traktuje takich zmiennych, jako oddzielny element. Inicjalizacja jednego z tych zmiennych nie ma wpływu na inne wartości. Takie same w przypadku zdefiniowania procedury z zestawem przeciążenia i Zadeklaruj zmienną statyczną o tej samej nazwie w poszczególnych przeciążeń.  
  
## <a name="containing-elements-for-static-variables"></a>Zawierający elementy statyczne zmienne  
 Oznacza to, zmiennej lokalnej statycznej w obrębie klasy, można zadeklarować wewnątrz procedury w tej klasie. Jednak nie można zadeklarować zmiennej lokalnej statycznej w ramach struktury, jako element członkowski struktury lub zmiennej lokalnej procedury w tej strukturze.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład deklaruje zmienną z [statyczne](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe. (Należy pamiętać, że nie ma potrzeby `Dim` — słowo kluczowe podczas [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) używa modyfikujący, takich jak `Static`.)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#13)]  
  
### <a name="comments"></a>Komentarze  
 W poprzednim przykładzie, zmienna `applesSold` nadal istnieje po procedurze `runningTotal` powraca do kodu wywołującego. Przy następnym `runningTotal` jest wywoływana, `applesSold` zachowuje jej wcześniej obliczoną wartość.  
  
 Jeśli `applesSold` zadeklarowana bez użycia `Static`, poprzednie wartości łączne może nie zostać zachowane przez wywołania `runningTotal`. Przy następnym `runningTotal` została wywołana `applesSold` czy zostały odtworzone i inicjowane na wartość 0, i `runningTotal` będzie po prostu zwracane taką samą wartość, z którą została wywołana.  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Można zainicjować wartość zmiennej lokalnej statycznej w ramach swojej deklaracji. Jeśli deklaruje tablicę jako `Static`, można zainicjować jego randze (liczba wymiarów), długość każdego wymiaru i wartości poszczególnych elementów.  
  
### <a name="security"></a>Zabezpieczenia  
 W poprzednim przykładzie, może utworzyć ten sam okres istnienia, deklarując `applesSold` na poziomie modułu. Jeśli zmieniono zakres zmiennej w ten sposób, jednak procedury będzie już wyłączny dostęp do niego. Ponieważ można uzyskać dostępu do innych procedur `applesSold` i zmień jej wartość sumy mogą być zawodne i kod może być trudne do utrzymania.  
  
## <a name="see-also"></a>Zobacz także

- [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)
- [Nothing](../../../../visual-basic/language-reference/nothing.md)
- [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
