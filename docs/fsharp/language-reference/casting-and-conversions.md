---
title: Rzutowanie i konwersje (F#)
description: 'Dowiedz się, jak język programowania w języku F # przewiduje operatory konwersji konwersje arytmetyczne między różnych typów pierwotnych.'
keywords: 'Visual f #, f #, funkcjonalności programowania'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: db30db67-da21-4206-bf0c-9211bd3cb22f
ms.openlocfilehash: df8352b0dd8651f1480515311454a218ea79b971
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="casting-and-conversions-f"></a>Rzutowanie i konwersje (F#)

W tym temacie opisano obsługę konwersje typów w języku F #.

## <a name="arithmetic-types"></a>Typów arytmetycznych
F # zawiera operatory konwersji konwersje arytmetyczne między różne typy pierwotne, takich jak między liczb całkowitych i zmiennoprzecinkowych typów. Operatory konwersji typu całkowitego lub char zaznaczono i niezaznaczone formularze; zmiennoprzecinkowy operatory i `enum` operatora konwersji nie. Zaznaczenie opcji formularze są definiowane w `Microsoft.FSharp.Core.Operators` i zaznaczone formularze są definiowane w `Microsoft.FSharp.Core.Operators.Checked`. Checked formularzy sprawdzaj przepełnienie i Generuj wyjątek czasu wykonywania, jeśli wartość wynikową przekracza limity typu docelowego.

Każdy z tych operatorów ma taką samą nazwę jak nazwa typu docelowego. Na przykład w następującym kodem, w którym mają jawnie adnotacje typów, `byte` pojawi się z dwóch różnych znaczenie. Pierwsze wystąpienie znajduje się typ, a drugą jest wartość operatora konwersji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

W poniższej tabeli przedstawiono operatory konwersji zdefiniowany w języku F #.

|Operator|Opis|
|--------|-----------|
|`byte`|Konwertuj na bajt, 8-bitowego typu bez znaku.|
|`sbyte`|Konwertuj na bajtu ze znakiem.|
|`int16`|Konwertuj na 16-bitową liczbę całkowitą ze znakiem.|
|`uint16`|Konwertuj na 16-bitową liczbę całkowitą bez znaku.|
|`int32, int`|Konwertuj na 32-bitowej podpisanej liczby całkowitej.|
|`uint32`|Konwertuj na 32-bitowej liczby całkowitej bez znaku.|
|`int64`|Konwertuj na 64-bitowej podpisanej liczby całkowitej.|
|`uint64`|Konwertuj na 64-bitowej liczby całkowitej bez znaku.|
|`nativeint`|Konwertuj natywnego wartości całkowitej.|
|`unativeint`|Konwertuj na liczbę całkowitą bez znaku macierzystego.|
|`float, double`|Konwertuj na 64-bitowych IEEE podwójnej precyzji, liczba zmiennoprzecinkowa.|
|`float32, single`|Konwertuj na 32-bitowych IEEE pojedynczej precyzji, liczba zmiennoprzecinkowa.|
|`decimal`|Konwertuj na `System.Decimal`.|
|`char`|Konwertuj na `System.Char`, znaków Unicode.|
|`enum`|Konwertuj na typ wyliczeniowy.|
Oprócz wbudowanych typów pierwotnych, obu operatorów można używać z typów, które implementują `op_Explicit` lub `op_Implicit` metod z odpowiednim podpisem. Na przykład `int` operatora konwersji współpracuje z dowolnego typu, który udostępnia metodę statyczną `op_Explicit` który przyjmuje jako parametr typu i zwraca `int`. Specjalne wyjątku do zasady, że metody nie może zostać przeciążony przez typ zwracany, możesz to zrobić `op_Explicit` i `op_Implicit`.

## <a name="enumerated-types"></a>Typy wyliczane
`enum` Operator jest ogólny operator, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` można przekonwertować na. Podczas konwertowania na typ wyliczeniowy, wpisz wnioskowania spróbuje określić typ `enum` , który chcesz przekonwertować. W poniższym przykładzie zmienna `col1` nie ma jawnie adnotacji, ale jego typ jest wywnioskowany na podstawie nowsze testu równości. W związku z tym kompilator można wywnioskować, że przekonwertowania na `Color` wyliczenia. Alternatywnie możesz podać adnotację typu, jak `col2` w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
Docelowy typ wyliczenia można również określić jawnie jako parametr typu, zgodnie z poniższym kodem:

```fsharp
let col3 = enum<Color> 3
```

Należy zwrócić uwagę, czy wyliczenia rzutuje pracy tylko, jeśli typ podstawowy wyliczenia jest niezgodny z typem konwersji. W poniższym kodzie konwersji nie powiedzie się skompilować z powodu niezgodności między `int32` i `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).

## <a name="casting-object-types"></a>Rzutowanie typów obiektów
Konwersja między typami w hierarchii obiektów jest niezbędne, aby programowanie zorientowane obiektowo. Istnieją dwa typy podstawowe konwersji: rzutowanie w górę (rzutowanie w górę) i rzutowanie w dół (rzutowanie w dół). Rzutowanie w górę hierarchii oznacza rzutowanie obiektu pochodnego odwołanie do odwołania obiektu podstawowego. Takie rzutowanie jest gwarantowane tak długo, jak klasa podstawowa jest w hierarchii dziedziczenia klasy pochodnej. Rzutowanie w dół hierarchii z odwołaniem obiektu podstawowego odwołania do obiektu pochodnego powiedzie się tylko wtedy, gdy obiekt jest rzeczywiście wystąpienia typu poprawny docelowy (ustalona) lub typu pochodzącego od typu docelowego.

F # zawiera operatory dla tych typów konwersji. `:>` Operator rzutowań w hierarchii i `:?>` operator rzutowań w dół hierarchii.

### <a name="upcasting"></a>Rzutowanie w górę
W wielu językach zorientowane obiektowo rzutowanie w górę jest niejawnie; w języku F # reguły są nieco inne. Rzutowanie w górę jest stosowana automatycznie, gdy argument jest przekazywany do metody typu obiektu. Jednak powiązane z let funkcji w module, rzutowanie w górę nie jest automatyczne, jeśli typ parametru jest zadeklarowany jako typ elastyczne. Aby uzyskać więcej informacji, zobacz [typy elastyczne](flexible-Types.md).

`:>` Operator wykonuje statycznego rzutowania, co oznacza, że powodzenie rzutowanie jest określana w czasie kompilacji. Jeśli rzutowania, która używa `:>` kompiluje pomyślnie, jest prawidłową rzutowania i ma bez możliwości błąd w czasie wykonywania.

Można również użyć `upcast` operatora, aby wykonać takie konwersji. Poniższe wyrażenie określa konwersji w hierarchii:

```fsharp
upcast expression
```

Jeśli używasz upcast — operator kompilator próbuje wnioskować o typie, który ma zostać zmieniony na w kontekście. Jeśli nie można określić typ docelowy jest kompilatora, kompilator zgłasza błąd.

### <a name="downcasting"></a>Rzutowanie w dół
`:?>` Operator wykonuje dynamicznym rzutowania, co oznacza, że powodzenie rzutowanie jest określana w czasie wykonywania. Rzutowanie, która używa `:?>` operator nie jest zaznaczone pole w czasie kompilacji; ale w czasie wykonywania, próby rzutowanie do określonego typu. Jeśli obiekt jest zgodny z typem docelowym, rzutowanie zakończy się pomyślnie. Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe zgłasza `InvalidCastException`.

Można również użyć `downcast` operatora, aby dokonać konwersji typu dynamicznego. Poniższe wyrażenie określa konwersji w dół hierarchii do typu, który jest wywnioskowany na podstawie kontekstu program:

```fsharp
downcast expression
```

Jak w przypadku `upcast` operatora, jeśli kompilator nie można wnioskować o typie docelowej określonej w kontekście zgłasza błąd.

Poniższy kod przedstawia użycie `:>` i `:?>` operatorów. Kod ilustruje, który `:?>` operator najlepiej jest używany, gdy wiesz, że konwersja kończy się pomyślnie, ponieważ zgłasza `InvalidCastException` Jeśli konwersji nie powiedzie się. Jeśli nie wiesz, że konwersji powiedzie się, test typu, który używa `match` wyrażenie jest lepszym rozwiązaniem, ponieważ pozwala ona na uniknięcie koszty generowania wyjątku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Ponieważ operatory ogólnego `downcast` i `upcast` polegać na wnioskowanie o typie, aby określić typ argumentów i w powyższym kodzie, możesz zastąpić

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
let base1 = upcast d1
```

W poprzednim kodzie typ argumentu i zwracane typy są `Derived1` i `Base1`odpowiednio.

Aby uzyskać więcej informacji o testach typu, zobacz [wyrażenia dopasowania](match-Expressions.md).

## <a name="see-also"></a>Zobacz też
[Dokumentacja języka F#](index.md)
