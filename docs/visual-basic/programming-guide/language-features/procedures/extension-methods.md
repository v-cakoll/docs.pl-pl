---
title: Metody rozszerzeń
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: a88756fce9137f89db1b6b8b007d528e98381830
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74341175"
---
# <a name="extension-methods-visual-basic"></a>Metody rozszerzeń (Visual Basic)

Metody rozszerzające pozwalają deweloperom dodawać niestandardowe funkcje do typów danych, które są już zdefiniowane bez tworzenia nowego typu pochodnego. Metody rozszerzające umożliwiają napisanie metody, która może być wywoływana, tak jakby była to metoda wystąpienia istniejącego typu.

## <a name="remarks"></a>Uwagi

Metoda rozszerzenia może być tylko procedurą `Sub` lub `Function`. Nie można zdefiniować właściwości rozszerzenia, pola lub zdarzenia. Wszystkie metody rozszerzenia muszą być oznaczone atrybutem rozszerzenia `<Extension>` z przestrzeni nazw <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> i muszą być zdefiniowane w [module](../../../language-reference/statements/module-statement.md). Jeśli Metoda rozszerzenia jest zdefiniowana poza modułem, kompilator Visual Basic generuje błąd [BC36551](../../../misc/bc36551.md), "metody rozszerzające można definiować tylko w modułach".

Pierwszy parametr w definicji metody rozszerzenia określa typ danych, które rozszerza Metoda. Gdy metoda jest uruchamiana, pierwszy parametr jest powiązany z wystąpieniem typu danych, który wywołuje metodę.

Atrybut `Extension` może być stosowany tylko do Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md)lub [`Function`](../../../language-reference/statements/function-statement.md). Jeśli zastosujesz go do `Class` lub `Structure`, kompilator Visual Basic generuje błąd [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), atrybut "Extension" może być stosowany tylko do deklaracji "module", "Sub" lub "Function".

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano `Print` rozszerzenia <xref:System.String> typu danych. Metoda używa `Console.WriteLine`, aby wyświetlić ciąg. Parametr metody `Print`, `aString`, określa, że metoda rozszerza klasę <xref:System.String>.

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

Zauważ, że definicja metody rozszerzenia jest oznaczona za pomocą atrybutu rozszerzenia `<Extension()>`. Oznaczanie modułu, w którym jest zdefiniowana Metoda jest opcjonalne, ale każda Metoda rozszerzenia musi być oznaczona. Aby można było uzyskać dostęp do atrybutu rozszerzenia, należy zaimportować <xref:System.Runtime.CompilerServices>.

Metody rozszerzające mogą być deklarowane tylko w modułach. Zazwyczaj moduł, w którym jest zdefiniowana Metoda rozszerzająca, nie jest tym samym modułem, w którym jest wywoływana. Zamiast tego moduł, który zawiera metodę rozszerzenia, jest importowany, jeśli musi być, aby wprowadzić go do zakresu. Gdy moduł, który zawiera `Print` należy do zakresu, Metoda może zostać wywołana, tak jakby była metodą zwykłego wystąpienia, która nie przyjmuje argumentów, takich jak `ToUpper`:

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

W następnym przykładzie `PrintAndPunctuate`, jest również rozszerzeniem <xref:System.String>, ten czas został zdefiniowany przez dwa parametry. Pierwszy parametr, `aString`, określa, że Metoda rozszerzenia rozszerza <xref:System.String>. Drugi parametr, `punc`, ma być ciągiem znaków interpunkcyjnych, które są przenoszone jako argument, gdy wywoływana jest metoda. Metoda wyświetla ciąg, po którym następuje znak interpunkcji.

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

Metoda jest wywoływana przez wysłanie w argumencie ciągu dla `punc`: `example.PrintAndPunctuate(".")`

Poniższy przykład pokazuje `Print` i `PrintAndPunctuate` zdefiniowane i wywoływane. <xref:System.Runtime.CompilerServices> jest importowany w module definicji w celu umożliwienia dostępu do atrybutu rozszerzenia.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

Następnie metody rozszerzające są wprowadzane do zakresu i wywoływane:

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

Wszystko, co jest wymagane, aby można było uruchamiać te lub podobne metody rozszerzające, jest w zakresie. Jeśli moduł, który zawiera metodę rozszerzenia, znajduje się w zakresie, jest widoczny w IntelliSense i może być wywoływany tak, jakby był zwykłą metodą wystąpienia.

Zwróć uwagę, że gdy metody są wywoływane, żaden argument nie jest wysyłany w przypadku pierwszego parametru. Parametry `aString` w poprzednich definicjach metod są powiązane z `example`, wystąpieniem `String`, które je wywołuje. Kompilator będzie używać `example` jako argumentu wysłanego do pierwszego parametru.

Jeśli wywoływana jest metoda rozszerzająca dla obiektu, który jest ustawiony na `Nothing`, Metoda rozszerzenia zostanie wykonana. Nie dotyczy to zwykłych metod wystąpienia. Można jawnie sprawdzić `Nothing` w metodzie rozszerzenia.

## <a name="types-that-can-be-extended"></a>Typy, które można rozszerzyć

Można zdefiniować metodę rozszerzenia dla większości typów, które mogą być reprezentowane na liście parametrów Visual Basic, w tym następujące:

- Klasy (typy referencyjne)
- Struktury (typy wartości)
- Interfejsy
- Delegaty
- Argumenty ByRef i ByVal
- Parametry metody ogólnej
- Tablice

Ponieważ pierwszy parametr określa typ danych, które rozszerza Metoda rozszerzenia, jest wymagany i nie może być opcjonalny. Z tego powodu parametry `Optional` i `ParamArray` parametry nie mogą być pierwszym parametrem na liście parametrów.

Metody rozszerzające nie są brane pod uwagę w późnych powiązaniach. W poniższym przykładzie instrukcja `anObject.PrintMe()` wywołuje wyjątek <xref:System.MissingMemberException>, ten sam wyjątek, który jest wyświetlany, jeśli druga definicja metody rozszerzenia `PrintMe` została usunięta.

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a>Najlepsze rozwiązania

Metody rozszerzające zapewniają wygodny i zaawansowany sposób rozszerzania istniejącego typu. Aby jednak użyć ich pomyślnie, należy wziąć pod uwagę pewne kwestie. Te zagadnienia dotyczą głównie autorów bibliotek klas, ale mogą mieć wpływ na dowolną aplikację korzystającą z metod rozszerzających.

Ogólnie rzecz biorąc, metody rozszerzające dodawane do typów, które nie są własnością, są bardziej podatne na metody rozszerzające, które są dodawane do kontrolowanych typów. Wiele rzeczy może wystąpić w klasach, które nie są właścicielami, które mogą zakłócać metody rozszerzenia.

- Jeśli istnieje jakikolwiek dostępny element członkowski wystąpienia, który ma sygnaturę zgodną z argumentami w instrukcji wywołującej, bez konwersji zawężających wymagane z argumentu do parametru, metoda wystąpienia zostanie użyta w preferencjach do dowolnej metody rozszerzenia. W związku z tym, Jeśli odpowiednia metoda wystąpienia jest dodawana do klasy w pewnym momencie, istniejący element członkowski rozszerzenia, na którym bazuje, może stać się niedostępny.

- Autor metody rozszerzenia nie może uniemożliwić innym programistom pisanie sprzecznych metod rozszerzenia, które mogą mieć pierwszeństwo przed oryginalnym rozszerzeniem.

- Niezawodność można poprawić, umieszczając metody rozszerzające w ich własnym obszarze nazw. Odbiorcy biblioteki mogą następnie dołączyć przestrzeń nazw lub wykluczyć ją lub wybrać między przestrzeniami nazw, niezależnie od reszty biblioteki.

- Może być bezpieczniejsze, aby można było zwiększyć interfejsy niż w celu zwiększenia klas, zwłaszcza jeśli nie jesteś własnością interfejsu lub klasy. Zmiana w interfejsie ma wpływ na każdą klasę, która ją implementuje. W związku z tym autor może być mniej prawdopodobnie dodawać lub zmieniać metody w interfejsie. Jeśli jednak Klasa implementuje dwa interfejsy, które mają metody rozszerzające o tej samej sygnaturze, żadna metoda rozszerzająca nie jest widoczna.

- Rozwiń najbardziej konkretny typ. W hierarchii typów, jeśli wybierzesz typ, z którego pochodzą wiele innych typów, istnieją warstwy możliwości do wprowadzenia metod wystąpienia lub innych metod rozszerzających, które mogą zakłócać pracę.

## <a name="extension-methods-instance-methods-and-properties"></a>Metody rozszerzające, metody wystąpień i właściwości

Gdy metoda wystąpienia w zakresie ma sygnaturę zgodną z argumentami instrukcji wywołującej, metoda wystąpienia jest wybierana w preferencjach dla dowolnej metody rozszerzenia. Metoda wystąpienia ma pierwszeństwo, nawet jeśli Metoda rozszerzenia jest lepszym dopasowaniem. W poniższym przykładzie `ExampleClass` zawiera metodę wystąpienia o nazwie `ExampleMethod`, która ma jeden parametr typu `Integer`. Metoda rozszerzająca `ExampleMethod` rozszerza `ExampleClass`i ma jeden parametr typu `Long`.

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

Pierwsze wywołanie `ExampleMethod` w poniższym kodzie wywołuje metodę rozszerzenia, ponieważ `arg1` jest `Long` i jest zgodny tylko z parametrem `Long` w metodzie rozszerzenia. Drugie wywołanie `ExampleMethod` ma `Integer` argument, `arg2`i wywołuje metodę wystąpienia.

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

Teraz należy odwrócić typy danych parametrów w dwóch metodach:

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

Tym razem kod w `Main` wywołuje metodę wystąpienia jednocześnie. Wynika to z faktu, że zarówno `arg1`, jak i `arg2` mają konwersję rozszerzającą do `Long`, a metoda wystąpienia ma pierwszeństwo przed metodą rozszerzenia w obu przypadkach.

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

W związku z tym Metoda rozszerzająca nie może zastąpić istniejącej metody wystąpienia. Jednak jeśli Metoda rozszerzenia ma taką samą nazwę jak metoda wystąpienia, ale podpisy nie powodują konfliktu, można uzyskać dostęp do obu metod. Na przykład jeśli Klasa `ExampleClass` zawiera metodę o nazwie `ExampleMethod`, która nie przyjmuje argumentów, metody rozszerzające o tej samej nazwie, ale różne podpisy są dozwolone, jak pokazano w poniższym kodzie.

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

Dane wyjściowe z tego kodu są następujące:

```console
Extension method
Instance method
```

Sytuacja jest prostsza z właściwościami: Jeśli Metoda rozszerzenia ma taką samą nazwę jak właściwość klasy, która rozszerza, Metoda rozszerzenia nie jest widoczna i nie można uzyskać do niej dostępu.

## <a name="extension-method-precedence"></a>Pierwszeństwo metody rozszerzenia

Gdy dwie metody rozszerzające, które mają identyczne podpisy są w zakresie i są dostępne, zostanie wywołana wartość o wyższym priorytecie. Pierwszeństwo metody rozszerzenia opiera się na mechanizmie używanym do przenoszenia metody do zakresu. Na poniższej liście przedstawiono hierarchię pierwszeństwa, od najwyższego do najniższego.

1. Metody rozszerzające zdefiniowane wewnątrz bieżącego modułu.

2. Metody rozszerzające zdefiniowane wewnątrz typów danych w bieżącej przestrzeni nazw lub w jednym z jej obiektów nadrzędnych, z podrzędnymi przestrzeniami nazw mającymi wyższy priorytet niż nadrzędne przestrzenie nazw.

3. Metody rozszerzające zdefiniowane wewnątrz dowolnego typu Importy w bieżącym pliku.

4. Metody rozszerzające zdefiniowane wewnątrz dowolnego importu przestrzeni nazw w bieżącym pliku.

5. Metody rozszerzające zdefiniowane wewnątrz dowolnego typu importu na poziomie projektu.

6. Metody rozszerzające zdefiniowane wewnątrz dowolnego importu przestrzeni nazw na poziomie projektu.

Jeśli pierwszeństwo nie rozwiąże niejednoznaczności, można użyć w pełni kwalifikowanej nazwy, aby określić wywoływaną metodę. Jeśli `Print` Metoda w poprzednim przykładzie jest zdefiniowana w module o nazwie `StringExtensions`, w pełni kwalifikowana nazwa jest `StringExtensions.Print(example)` zamiast `example.Print()`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Metody rozszerzeń](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Module, instrukcja](../../../language-reference/statements/module-statement.md)
- [Parametry i argumenty procedur](procedure-parameters-and-arguments.md)
- [Parametry opcjonalne](optional-parameters.md)
- [Tablice parametrów](parameter-arrays.md)
- [Przegląd atrybutów](../../concepts/attributes/index.md)
- [Zakres w Visual Basic](../declared-elements/scope.md)
