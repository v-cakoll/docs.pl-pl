---
title: Okres istnienia w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 14a75a2c3af52f63051d02df9341faf19c3b76c7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="lifetime-in-visual-basic"></a>Okres istnienia w Visual Basic
*Okres istnienia* elementu zadeklarowane jest okres, w którym jest dostępny do użytku. Zmienne są tylko elementy, które mają cykl życia. W tym celu kompilator traktuje parametry procedury i funkcja zwraca jako szczególnych przypadkach zmiennych. Okres istnienia zmiennej, która reprezentuje okres, w którym można zapisać wartości. Wartość można zmienić jego okresu istnienia, ale zawsze zawiera niektóre wartości.  
  
## <a name="different-lifetimes"></a>Różne okresy istnienia  
 A *zmiennej członkowskiej* (zadeklarowane na poziomie modułu, poza dowolnej procedury) zwykle ma tego samego istnienia jako element, w którym jest zadeklarowany. Udostępniana Zmienna zadeklarowana w klasie lub strukturze istnieje jako oddzielna kopia dla każdego wystąpienia klasy lub struktury, w którym jest zadeklarowany. Każdej z takich zmiennej ma tego samego czas istnienia jako jego wystąpienia. Jednak `Shared` zmienna ma tylko jeden okres istnienia, który jest ważny przez cały czas, aplikacja jest uruchomiona.  
  
 A *zmiennej lokalnej* (zadeklarowana wewnątrz procedury) istnieje tylko w czasie wykonywania procedury, w którym jest zadeklarowany. Dotyczy to również parametry tej procedury i zwrot funkcji. Jednak jeśli tej procedury wywołuje innych procedur, zmienne lokalne przechowywać ich wartości podczas wykonywania procedury o nazwie.  
  
## <a name="beginning-of-lifetime"></a>Początek okresu istnienia  
 Okres istnienia zmiennej lokalnej uruchamia się, gdy formant przechodzi procedury, w którym jest zadeklarowany. Co lokalnego zmienna jest ustawiana na wartość domyślną dla tego typu danych, natychmiast rozpoczyna się procedura uruchomiona. Gdy wystąpi procedury `Dim` instrukcji, która określa wartości początkowej, ustawia tych zmiennych tych wartości, nawet jeśli kod ma już przypisanego inne wartości.  
  
 Każdy element członkowski zmiennej struktury został zainicjowany, tak jakby był on osobnej zmiennej. Podobnie każdy element tablicy zmiennej zainicjowano pojedynczo.  
  
 Zmienne zadeklarowane w bloku wewnątrz procedury (takie jak `For` pętli) są inicjowane przy wejściu do procedury. Te inicjalizacji zaczynają obowiązywać, czy kod kiedykolwiek wykonuje bloku.  
  
## <a name="end-of-lifetime"></a>Koniec okresu istnienia  
 Podczas procedury składowanej, wartości jego zmiennych lokalnych nie są zachowywane, a ich pamięci zwraca Visual Basic. Podczas następnego wywołania tej procedury, jego zmiennych lokalnych są nowo utworzone i zainicjowane ponownie.  
  
 Gdy zakończenie wystąpienia klasy lub struktury, udostępniana zmienne utratę ich pamięci i ich wartości. Każde nowe wystąpienie klasy lub struktury, tworzy i ponownie inicjuje udostępniana zmienne. Jednak `Shared` zmienne są zachowywane, dopóki aplikacja przestanie działać.  
  
## <a name="extension-of-lifetime"></a>Rozszerzenia okresu istnienia  
 Deklarowanie zmiennej lokalnej o `Static` — słowo kluczowe, jego okres istnienia jest dłuższy niż czas wykonania jego procedury. W poniższej tabeli przedstawiono sposób deklaracji procedury określa, jak długo `Static` istnieje zmienna.  
  
|Udostępnianie i procedury lokalizacji|Rozpoczyna się statycznych zmiennych okres istnienia|Kończy statycznych zmiennych okres istnienia|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|W module (domyślnie udostępnione)|Procedura jest wywoływana po raz pierwszy|Gdy aplikacja przestaje działać|  
|W klasie `Shared` (procedury nie ma elementu członkowskiego wystąpienia)|Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu lub na nazwę klasy lub struktury, sama|Gdy aplikacja przestaje działać|  
|W wystąpieniu klasy nie `Shared` (procedura jest elementu członkowskiego wystąpienia)|Po raz pierwszy procedura jest wywoływana w ramach określonego wystąpienia|Po zwolnieniu wystąpienie dla wyrzucanie elementów bezużytecznych (GC)|  
  
## <a name="static-variables-of-the-same-name"></a>Zmienne statyczne o takiej samej nazwie  
 Można deklarować statycznych zmiennych o takiej samej nazwie w więcej niż jednej procedury. Jeśli to zrobisz, kompilator Visual Basic uwzględnia każdej takie zmiennej jako oddzielny element. Inicjowanie jednej z tych zmiennych nie ma wpływu na inne wartości. Takie same w przypadku zdefiniowania procedury z zestawem przeciążenia ani deklarować statyczna zmienna o takiej samej nazwie w każdym przeciążenia.  
  
## <a name="containing-elements-for-static-variables"></a>Zawierający elementy zmienne statyczne  
 Statyczna zmienna lokalna w obrębie klasy, mogą zadeklarować oznacza to, wewnątrz procedury w tej klasie. Jednak statyczna zmienna lokalna w strukturze nie można zadeklarować jako element członkowski struktury lub jako zmienną lokalną, procedura w tej struktury.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 Poniższy przykład deklaruje zmienną z [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe. (Należy pamiętać, że nie ma potrzeby `Dim` — słowo kluczowe podczas [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) korzysta z takich jak modyfikujący `Static`.)  
  
### <a name="code"></a>Kod  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a>Komentarze  
 W powyższym przykładzie zmienna `applesSold` zachowany po procedurze `runningTotal` zwraca do wywołującego kodu. Przy następnym `runningTotal` jest nazywany `applesSold` zachowuje jej wcześniej obliczoną wartość.  
  
 Jeśli `applesSold` zadeklarowano bez użycia `Static`, poprzednie wartości wszystkich może nie zostać zachowane w wywołaniach `runningTotal`. Przy następnym `runningTotal` została wywołana, `applesSold` czy zostały odtworzone i ustawiana na 0, a `runningTotal` czy po prostu zwracane taką samą wartość, z którą została wywołana.  
  
### <a name="compiling-the-code"></a>Kompilowanie kodu  
 Można zainicjować wartość statyczna zmienna lokalna jako części swojej deklaracji. W przypadku tablicy jako `Static`, można zainicjować jego ranking (liczba wymiarów), długość każdego wymiaru i wartości poszczególne elementy.  
  
### <a name="security"></a>Zabezpieczenia  
 W poprzednim przykładzie, można utworzyć sam cykl życia przez zadeklarowanie `applesSold` na poziomie modułu. Po zmianie zakresu zmiennej w ten sposób jednak procedura będzie już wyłączny dostęp do niego. Ponieważ można uzyskać dostępu do innych procedur `applesSold` i zmień jego wartość, sumę bieżącą może być zawodne i kod może być bardziej trudne w utrzymaniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Nazwy zadeklarowanych elementów](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odwołania do elementów zadeklarowanych](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Zakres w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Poziomy dostępu w Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Zmienne](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Rozwiązywanie problemów związanych z typami danych](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Static](../../../../visual-basic/language-reference/modifiers/static.md)
