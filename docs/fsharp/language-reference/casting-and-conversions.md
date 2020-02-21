---
title: Rzutowanie i konwersje
description: Dowiedz się F# , jak język programowania zapewnia operatory konwersji dla konwersji arytmetycznych między różnymi typami pierwotnymi.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543589"
---
# <a name="casting-and-conversions-f"></a>Rzutowanie i konwersje (F#)

W tym temacie opisano obsługę konwersji typów w F#.

## <a name="arithmetic-types"></a>Typy arytmetyczne

F#zapewnia operatory konwersji dla konwersji arytmetycznych między różnymi typami pierwotnymi, takimi jak między liczbami całkowitymi i zmiennoprzecinkowymi. Operatory konwersji całek i char mają sprawdzone i niesprawdzone formularze; Operatory zmiennoprzecinkowe i operator konwersji `enum` nie. Niesprawdzone formularze są zdefiniowane w `Microsoft.FSharp.Core.Operators`, a zaznaczone formularze są zdefiniowane w `Microsoft.FSharp.Core.Operators.Checked`. Sprawdzone formularze sprawdzają przepełnienie i generują wyjątek czasu wykonywania, jeśli wartość wyników przekracza limity typu docelowego.

Każdy z tych operatorów ma taką samą nazwę jak nazwa typu docelowego. Na przykład, w poniższym kodzie, w którym typy są jawnie adnotacje, `byte` pojawia się z dwoma różnymi znaczeniami. Pierwsze wystąpienie jest typem, a drugi jest operatorem konwersji.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

W poniższej tabeli przedstawiono operatory konwersji zdefiniowane w F#.

|Operator|Opis|
|--------|-----------|
|`byte`|Konwertuj na bajt, 8-bitowy typ unsigned.|
|`sbyte`|Konwertuj na bajt ze znakiem.|
|`int16`|Konwertuj na 16-bitową liczbę całkowitą ze znakiem.|
|`uint16`|Konwertuj na 16-bitową liczbę całkowitą bez znaku.|
|`int32, int`|Konwertuj na 32-bitową liczbę całkowitą ze znakiem.|
|`uint32`|Konwertuj na 32-bitową liczbę całkowitą bez znaku.|
|`int64`|Konwertuj na 64-bitową liczbę całkowitą ze znakiem.|
|`uint64`|Konwertuj na 64-bitową liczbę całkowitą bez znaku.|
|`nativeint`|Konwertuj na natywną liczbę całkowitą.|
|`unativeint`|Konwertuj na nieniepodpisana liczbę całkowitą.|
|`float, double`|Konwertuj na 64-bitową liczbę zmiennoprzecinkową IEEE o podwójnej precyzji.|
|`float32, single`|Konwertuj na 32-bitową liczbę zmiennoprzecinkową IEEE o pojedynczej precyzji.|
|`decimal`|Konwertuj na `System.Decimal`.|
|`char`|Konwertuj na `System.Char`, znak Unicode.|
|`enum`|Konwertuj na typ wyliczeniowy.|

Oprócz wbudowanych typów pierwotnych można używać tych operatorów z typami, które implementują `op_Explicit` lub `op_Implicit` metody z odpowiednimi sygnaturami. Na przykład operator konwersji `int` działa z dowolnym typem, który udostępnia metodę statyczną `op_Explicit`, która przyjmuje typ jako parametr i zwraca `int`. Jako specjalny wyjątek do ogólnej reguły, że metody nie mogą być przeciążone przez zwracany typ, można to zrobić dla `op_Explicit` i `op_Implicit`.

## <a name="enumerated-types"></a>Typy wyliczeniowe

Operator `enum` jest operatorem ogólnym, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` do przekonwertowania. Podczas konwertowania na typ wyliczeniowy, wnioskowanie typu próbuje określić typ `enum`, do którego chcesz dokonać konwersji. W poniższym przykładzie zmienna `col1` nie jest jawnie oznaczona adnotacją, ale jej typ jest wnioskowany z późniejszego testu równości. W związku z tym kompilator może wywnioskować, że jest konwertowany na Wyliczenie `Color`. Alternatywnie można podać adnotację typu, tak jak w przypadku `col2` w poniższym przykładzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Można również określić typ wyliczenia docelowego jawnie jako parametr typu, jak w poniższym kodzie:

```fsharp
let col3 = enum<Color> 3
```

Należy zauważyć, że rzutowania wyliczenia działa tylko wtedy, gdy typ podstawowy wyliczenia jest zgodny z konwertowanym typem. W poniższym kodzie konwersja nie zostanie skompilowana z powodu niezgodności między `int32` i `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).

## <a name="casting-object-types"></a>Rzutowanie typów obiektów

Konwersja między typami w hierarchii obiektów jest podstawowa dla programowania zorientowanego obiektowo. Istnieją dwa podstawowe typy konwersji: Rzutowanie w górę (Rzutowanie) i Rzutowanie w dół (Rzutowanie). Rzutowanie hierarchii oznacza rzutowanie z odwołania do obiektu pochodnego na odwołanie do obiektu podstawowego. Takie Rzutowanie jest gwarantowane, o ile Klasa bazowa znajduje się w hierarchii dziedziczenia klasy pochodnej. Rzutowanie w dół hierarchii, od odwołania do obiektu podstawowego do odwołania do obiektu pochodnego, powiedzie się tylko wtedy, gdy obiekt faktycznie jest wystąpieniem poprawnego typu docelowego (pochodnego) lub typu pochodnego od typu docelowego.

F#dostarcza operatory dla tego typu konwersji. Operator `:>` rzutuje hierarchię, a operator `:?>` rzutuje hierarchię.

### <a name="upcasting"></a>Rzutowanie

W wielu językach zorientowanych obiektowo Rzutowanie jest niejawne; w F#programie reguły są nieco inne. Rzutowanie jest stosowane automatycznie podczas przekazywania argumentów do metod w typie obiektu. Jednak w przypadku funkcji z ograniczeniami w module przerzutowanie nie jest automatyczne, chyba że typ parametru jest zadeklarowany jako typ elastyczny. Aby uzyskać więcej informacji, zobacz [Typy elastyczne](flexible-Types.md).

Operator `:>` wykonuje statyczne rzutowanie, co oznacza, że powodzenie rzutowania jest określane w czasie kompilacji. Jeśli rzutowanie, które używa `:>` kompiluje się pomyślnie, jest prawidłowym rzutem i nie ma żadnej szansy błędu w czasie wykonywania.

Można również użyć operatora `upcast`, aby wykonać taką konwersję. Następujące wyrażenie określa konwersję w górę hierarchii:

```fsharp
upcast expression
```

Gdy używasz operatora przerzutowania, kompilator próbuje wywnioskować typ, który jest konwertowany na podstawie kontekstu. Jeśli kompilator nie może określić typu docelowego, kompilator zgłosi błąd. Może być wymagana adnotacja typu.

### <a name="downcasting"></a>Rzutowanie

Operator `:?>` wykonuje rzutowanie dynamiczne, co oznacza, że powodzenie rzutowania jest określane w czasie wykonywania. Rzutowanie używające operatora `:?>` nie jest sprawdzane w czasie kompilacji; ale w czasie wykonywania jest podejmowana próba rzutowania na określony typ. Jeśli obiekt jest zgodny z typem docelowym, Rzutowanie powiedzie się. Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe wywołuje `InvalidCastException`.

Można również użyć operatora `downcast`, aby przeprowadzić konwersję typu dynamicznego. Następujące wyrażenie określa konwersję w dół hierarchii do typu, który jest wywnioskowany z kontekstu programu:

```fsharp
downcast expression
```

Jak dla operatora `upcast`, jeśli kompilator nie może wywnioskować określonego typu docelowego z kontekstu, zgłasza błąd. Może być wymagana adnotacja typu.

Poniższy kod ilustruje użycie operatorów `:>` i `:?>`. Kod ilustruje, że operator `:?>` jest najlepiej używany, gdy wiadomo, że konwersja powiedzie się, ponieważ generuje `InvalidCastException`, jeśli konwersja nie powiedzie się. Jeśli nie wiesz, że konwersja powiedzie się, test typu, który używa wyrażenia `match`, jest lepszy, ponieważ pozwala uniknąć narzutu na generowanie wyjątku.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Ponieważ operatory generyczne `downcast` i `upcast` polegają na wnioskach o typie w celu określenia argumentu i zwracanego typu, w powyższym kodzie można zastąpić

```fsharp
let base1 = d1 :> Base1
```

elementem

```fsharp
let base1: Base1 = upcast d1
```

Należy zauważyć, że adnotacja typu jest wymagana, ponieważ `upcast` przez siebie sama nie mogła ustalić klasy bazowej.

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka F#](index.md)
