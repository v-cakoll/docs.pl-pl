---
title: "Wskazówki dotyczące formatowania kodu (F#)"
description: "Dowiedz się wskazówki dotyczące formatowania wcięcia kodu dla języka czytelności, estetykę, normalizacji i kompilacji programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3f79717c-f84e-448d-9ce4-90e40a644ba1
ms.openlocfilehash: cc56c67f356b99defd8dc28770f87be1f58443c5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="code-formatting-guidelines"></a>Wskazówki dotyczące formatowania kodu

W tym temacie przedstawiono wskazówki wcięcia kodu języka F #. Ponieważ języka F # jest wrażliwe na podziały wiersza i wcięcia, go nie jest tylko problem czytelności, estetycznych problem lub kodowania problem normalizacji poprawnie formatowania kodu. Należy sformatować kodu poprawnie na jej poprawnej kompilacji.


## <a name="general-rules-for-indentation"></a>Zasady ogólne dotyczące wcięcie
Gdy wymagana jest wcięcie, należy użyć spacje, tabulatory nie. Wymagana jest co najmniej jedną przestrzeń. Organizacja może utworzyć standardów kodowania, aby określić liczbę spacji dla wcięć; Typowy jest trzech lub czterech spacji wcięcia na każdym poziomie, gdzie występuje wcięcia. Można skonfigurować programu Visual Studio, aby dopasować standardów wcięcia w organizacji, zmieniając opcje w `Options` okno dialogowe, które jest dostępne po `Tools` menu. W `Text Editor` węzła, rozwiń węzeł `F#` , a następnie kliknij przycisk `Tabs`. Opis dostępnych opcji, zobacz [opcje, Edytor tekstu, wszystkie języki, karty](https://msdn.microsoft.com/library/7sffa753.aspx).

Ogólnie rzecz biorąc gdy kompilator kodu, przechowuje wewnętrznego stosu, który wskazuje bieżący poziom zagnieżdżenia. Gdy tworzone jest wcięcie kodu, nowy poziom zagnieżdżenia jest utworzone lub wypychana na tym stosu wewnętrznego. Po zakończeniu konstrukcję poziom jest zdjęte ze stosu. Wcięcie jest jednym ze sposobów sygnalizuje koniec poziomu i pop stosu wewnętrznego, ale niektórych tokenów również zostać zdjęte ze stosu, takich jak poziom `end` — słowo kluczowe, lub zamykający nawias klamrowy lub nawias.

Kod w wielowierszowym konstrukcji, takich jak definicją typu definicji funkcji `try...with` konstrukcję i zapętlenia konstrukcje, musi wcięty względem wiersza otwierania konstrukcji. Pierwszy wiersz z wcięciami ustanawia pozycję w kolumnie dla kolejnych kodu w tej samej konstrukcji. Poziom wcięcia jest nazywany *kontekstu*. Pozycja kolumny Ustawia minimalną kolumny, określany jako *wiersza poza*, dla kolejnych wierszy kodu, które znajdują się w tym samym kontekście. W przypadku napotkania wiersz kodu wcięta mniej niż ta pozycja kolumny ustalonych, kompilator zakłada zakończył kontekstu i czy możesz są teraz generowanie kodu na następny poziom, poprzedni kontekst. Termin *poza* jest używany do opisu stanu, w którym wiersz kodu wyzwala koniec konstrukcję, ponieważ nie jest wystarczająco daleko wcięcia. Innymi słowy kod z lewej strony poza linii jest poza. W kodzie poprawnie wcięta możesz korzystać z reguły poza aby odróżniać koniec konstrukcji. Jeśli używasz wcięcia nieprawidłowo, poza warunek może spowodować, że kompilator ostrzeżenie lub może doprowadzić do nieprawidłowej interpretacji kodu.

Poza wiersze są określane w następujący sposób.


- `=` Token skojarzony z `let` wprowadza poza wiersza w kolumnie pierwszego tokena po `=` logowania.


- W `if...then...else` wyrażenia, pozycja kolumny pierwszy token po `then` — słowo kluczowe lub `else` — słowo kluczowe wprowadza poza wiersza.


- W `try...with` wyrażenia, pierwszy token po `try` wprowadza poza wiersza.


- W `match` wyrażenia, pierwszy token po `with` i pierwszy token po każdym poleceniu `->` wprowadzenie poza wierszy.


- Pierwszy token po `with` jako typ rozszerzenia wprowadza poza wiersza.


- Pierwszy token po otwierający nawias klamrowy lub nawias lub po `begin` — słowo kluczowe, wprowadza poza wiersza.


- Pierwszy znak w słowa kluczowe `let`, `if`, i `module` wprowadzenie poza wierszy.


Poniższe przykłady kodu przedstawiają reguły wcięcia. W tym miejscu wydruku instrukcje korzystają z wcięcie Aby skojarzyć je z odpowiedniego kontekstu. Za każdym razem, gdy wcięcie przewiduje, kontekst jest zdjęte ze stosu, jak i przywraca poprzedni kontekst. W związku z tym miejscem jest wydrukowany na końcu każdej iteracji; "Gotowe"! tylko jest drukowany jeden raz, ponieważ poza Wcięcie określa, że nie jest w pętli. Drukowanie ciągu "Context najwyższego poziomu" nie jest częścią funkcji. W związku z tym wydrukowaniem najpierw podczas statycznego inicjowania przed wywołaniem funkcji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet1.fs)]

Dane wyjściowe są następujące:

```
Top-level context

(Negative number) Zero 1 2 3 Done!
```

Po przerwaniu długie wiersze kontynuacji wiersza musi wcięty między konstrukcja otaczającej. Na przykład argumenty funkcji muszą wcięty między pierwszym znakiem nazwy funkcji, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet2.fs)]

Istnieją wyjątki od tych reguł, zgodnie z opisem w następnej sekcji.


## <a name="indentation-in-modules"></a>Wcięcia w modułach
Kod w lokalnym module musi być wcięty względem modułu, ale kod w module najwyższego poziomu nie musi być wcięta. Nie masz elementy Namespace wcięcia.

W poniższych przykładach kodu ilustrację.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet3.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet4.fs)]

Aby uzyskać więcej informacji, zobacz [modułów](modules.md).


## <a name="exceptions-to-the-basic-indentation-rules"></a>Wyjątki reguł wcięcia podstawowe
Zasady, zgodnie z opisem w poprzedniej sekcji, to czy kod w wielowierszowym konstrukcje musi być wcięty względem wcięcie pierwszego wiersza konstrukcji i koniec konstrukcja jest określany przez podczas pierwszego wiersza poza. Wyjątek od reguł dotyczących gdy end sytuacjach jest, że niektóre konstrukcje, takich jak `try...with` wyrażenia `if...then...else` wyrażenie i stosowania `and` Składnia deklaracji wzajemnie funkcje rekursywne lub typów, ma wiele części. Wcięcie nowsze składniki, takie jak `then` i `else` w `if...then...else` wyrażenie w tym samym poziomie jako token, który rozpoczyna się wyrażenie, ale zamiast wskazujący punktu końcowego do kontekstu, reprezentuje następnej części tego samego kontekstu. W związku z tym `if...then...else` wyrażenie można napisać tak jak w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet5.fs)]

Wyjątek poza reguły dotyczą tylko `then` i `else` słów kluczowych. W związku z tym mimo że nie jest błąd wcięcia `then` i `else` Ponadto nieudanym wcięcie wierszy kodu w `then` bloku generuje ostrzeżenie. Jest to zilustrowane w następujących wierszach kodu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet6.fs)]
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet7.fs)]

Dla kodu `else` dotyczy blok, dodatkowe reguły specjalne. Ostrzeżenie w poprzednim przykładzie występuje tylko w kodzie w `then` bloku, a nie na kod w `else` bloku. Dzięki temu można napisać kod, który sprawdza bez wymuszania reszty kod funkcję, która może znajdować się w różnych warunków na początku funkcji `else` bloku wcięcia. W związku z tym można napisać następujące bez tworzenia ostrzeżenie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet8.fs)]

Kolejny wyjątek do reguły, który zakończy się kontekst wiersza nie jest wcięty, ile poprzedniego wiersza jest infiksu operatorów, takich jak `+` i `|>`. Wiersze rozpoczynające się infiksu operatory są dozwolone, aby rozpocząć `(1 + oplength)` kolumn przed normalnej pozycji bez wyzwalania punktu końcowego do kontekstu, gdzie `oplength` jest liczba znaków, które tworzą operatora. Powoduje to pierwszy token po operatorze, aby były wyrównane z poprzedniego wiersza.

Na przykład w poniższym kodzie `+` symboli może być wcięta dwie kolumny krótszym niż poprzedniego wiersza.

[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet9.fs)]

Chociaż wcięcia zwykle zwiększa się wraz ze wzrostem wyższy poziom zagnieżdżenia, istnieje kilka konstrukcji, w których kompilator pozwala na zresetowanie wcięcie do dolnej położenie kolumny.

Konstrukcje, które zezwala na resetowanie położenia kolumny są następujące:


- Treść funkcji anonimowych. W poniższym kodzie wydruku wyrażenie rozpoczyna się od pozycji w kolumnie, która jest dostępne na lewo od `fun` — słowo kluczowe. Jednak wiersz nie może rozpoczynać się w kolumnie z lewej strony początek poprzedniego poziomu wcięcia (to znaczy po lewej `L` w `List`).
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet10.fs)]

- Konstrukcje ujęta w nawiasy lub przez `begin` i `end` w `then` lub `else` zablokować z `if...then...else` wyrażenia, pod warunkiem wcięcie nie jest nie mniejszy niż pozycja kolumny `if` — słowo kluczowe. Ten wyjątek umożliwia stylu kodowania, w którym nawias otwierający lub `begin` jest używany na końcu wiersza po `then` lub `else`.


- Treści modułów, klasy, interfejsy i struktur rozdzielone `begin...end`, `{...}`, `class...end`, lub `interface...end`. Dzięki temu stylu, w którym kluczowego otwarcia definicji typu może być na tym samym wierszu co nazwa typu bez wymuszania całej treści być wcięta między otwierania — słowo kluczowe.
[!code-fsharp[Main](../../../samples/snippets/fsharp/code-formatting/snippet13.fs)]


## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F #](index.md)
