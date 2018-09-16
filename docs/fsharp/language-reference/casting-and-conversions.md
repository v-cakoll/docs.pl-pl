---
title: Rzutowanie i konwersje (F#)
description: 'Dowiedz się, jak programowania języka F # zapewnia operatory konwersji konwersje arytmetyczne między różnych typów pierwotnych.'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677934"
---
# <a name="casting-and-conversions-f"></a>Rzutowanie i konwersje (F#)

W tym temacie opisano obsługę konwersje typów języka F #.

## <a name="arithmetic-types"></a>Typy arytmetyczne

F # zawiera operatory konwersji dla konwersji arytmetycznych między różnych typów pierwotnych, takich jak między liczb całkowitych i zmiennoprzecinkowych typów. Sprawdzeniu operatory konwersji liczbę całkowitą i char i unchecked formularze; zmiennoprzecinkowy operatorów i `enum` nie obsługują operatora konwersji. Unchecked formularze są definiowane w `Microsoft.FSharp.Core.Operators` i sprawdzonych formularze są definiowane w `Microsoft.FSharp.Core.Operators.Checked`. Checked formularzy sprawdzaj przepełnienie i wygenerować wyjątek czasu wykonywania, jeśli wartość wynikowa przekracza limit typu docelowego.

Każda z tych operatorów ma taką samą nazwę jak nazwa typu miejsca docelowego. Na przykład, w następujący kod, w którym typy są jawnie adnotację, `byte` pojawia się z dwóch różne znaczenie. Pierwsze wystąpienie jest typem, a drugą jest wartość operatora konwersji.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

W poniższej tabeli przedstawiono operatory konwersji zdefiniowane w języku F #.

|Operator|Opis|
|--------|-----------|
|`byte`|Konwertuj na wartość bajtu, 8-bitowy typ bez znaku.|
|`sbyte`|Konwertuj na bajt oznaczony.|
|`int16`|Konwertuj na wartość całkowita 16-bitowych.|
|`uint16`|Konwertuj na wartość 16-bitowa liczba całkowita bez znaku.|
|`int32, int`|Konwertuj na wartość całkowita 32-bitowych.|
|`uint32`|Konwertuj na 32-bitowa liczba całkowita bez znaku.|
|`int64`|Konwertuj na wartość całkowita 64-bitowych.|
|`uint64`|Konwertuj na wartość 64-bitowej nieoznaczonej liczby całkowitej.|
|`nativeint`|Konwertuj na wartość całkowitą natywnych.|
|`unativeint`|Konwertuj na wartość całkowitą bez znaku natywnych.|
|`float, double`|Konwertuj na IEEE podwójnej precyzji 64-bitowych, liczba zmiennoprzecinkowa.|
|`float32, single`|Konwertuj na IEEE pojedynczej precyzji 32-bitowa liczba zmiennoprzecinkowa.|
|`decimal`|Konwertuj na `System.Decimal`.|
|`char`|Konwertuj na `System.Char`, znaków Unicode.|
|`enum`|Konwertuj na typ wyliczany.|
Oprócz wbudowanych typów pierwotnych, można użyć tych operatorów z typami, które implementują `op_Explicit` lub `op_Implicit` metod z odpowiednią sygnaturą. Na przykład `int` operatora konwersji współpracuje z dowolnego typu, który udostępnia metodę statyczną `op_Explicit` która przyjmuje typ jako parametr i zwraca `int`. Jako specjalne wyjątek ogólną zasadą, że typem zwracanym nie mogą być przeciążone metody, można to zrobić `op_Explicit` i `op_Implicit`.

## <a name="enumerated-types"></a>Typy wyliczone

`enum` Operator jest ogólny operator, który przyjmuje jeden parametr typu, który reprezentuje typ `enum` do przekonwertowania na. Gdy są konwertowane na typ wyliczany, wpisz wnioskowania próbuje określić typ `enum` , którą chcesz przekonwertować. W poniższym przykładzie zmienna `col1` nie jest jawnie oznaczona, ale jego typ jest wnioskowany z nowszych testu równości. W związku z tym, kompilator może wywnioskować, jest konwertowane na `Color` wyliczenia. Alternatywnie, można podać adnotacji typu, podobnie jak w przypadku `col2` w poniższym przykładzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

Typ wyliczeniowy docelowym można również określić jawnie, co parametr typu zgodnie z poniższym kodem:

```fsharp
let col3 = enum<Color> 3
```

Należy pamiętać, wyliczenia rzutuje pracy, tylko wtedy, gdy podstawowy typ wyliczenia jest niezgodny z typem konwersji. W poniższym kodzie konwersji nie powiedzie się skompilować z powodu niezgodności między `int32` i `uint32`.

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

Aby uzyskać więcej informacji, zobacz [wyliczenia](enumerations.md).

## <a name="casting-object-types"></a>Rzutowanie typów obiektów

Konwersja między typami w hierarchii obiektów ma podstawowe znaczenie dla programowania obiektowego. Istnieją dwa podstawowe rodzaje konwersje: rzutowanie w górę (Rzutowanie rozszerzające) i rzutowanie w dół (rzutowanie). Rzutowanie hierarchii oznacza rzutowanie z odwołaniem pochodnego obiektu do obiektu podstawowego odwołania. Takie rzutowanie jest gwarantowane tak długo, jak klasy bazowej znajduje się w hierarchii dziedziczenia klasy pochodnej. Rzutowanie w dół hierarchii z obiektu podstawowego odwołania do odwołanie do obiektu pochodnej, zakończy się powodzeniem, tylko wtedy, gdy obiekt jest rzeczywiście wystąpienia typu odpowiedniego miejsca docelowego (derived) lub typ pochodzący od typu miejsca docelowego.

F # zawiera operatory dla tych typów konwersji. `:>` Operator rzutuje w hierarchii i `:?>` rzutuje operatora w dół hierarchii.

### <a name="upcasting"></a>Rzutowanie rozszerzające

W wielu językach obiektowych Rzutowanie rozszerzające jest niejawne; w języku F # zasady są nieco inne. Rzutowanie rozszerzające jest stosowane automatycznie, gdy argument jest przekazywany do metody typu obiektu. W przypadku funkcji powiązanych z umożliwiają w module Rzutowanie rozszerzające nie jest jednak automatyczne, chyba że typ parametru jest zadeklarowany jako typ elastyczne. Aby uzyskać więcej informacji, zobacz [typy elastyczne](flexible-Types.md).

`:>` Operator wykonuje statyczną rzutowania, co oznacza, że sukces rzutowanie jest określana w czasie kompilacji. Jeśli rzutowania, który używa `:>` kompiluje pomyślnie, jest prawidłowy rzutowania i ma nie ryzyko wystąpienia awarii w czasie wykonywania.

Można również użyć `upcast` operatora w celu wykonania takich konwersji. Poniższe wyrażenie określa konwersji w hierarchii:

```fsharp
upcast expression
```

Gdy używasz upcast — operator, kompilator spróbuje wywnioskować typu, który jest konwertowane na z kontekstu. Jeśli kompilator nie może określić typu docelowego, kompilator zgłosi błąd.

### <a name="downcasting"></a>Rzutowanie

`:?>` Operator wykonuje dynamiczny rzutowania, co oznacza, że sukces rzutowanie jest określana w czasie wykonywania. Rzutowania, który używa `:?>` operator nie jest sprawdzana w czasie kompilacji; ale w czasie wykonywania, zostanie podjęta próba rzutowanie do określonego typu. Jeśli obiekt jest zgodny z typem docelowym, rzutowanie zakończy się pomyślnie. Jeśli obiekt nie jest zgodny z typem docelowym, środowisko uruchomieniowe zgłasza `InvalidCastException`.

Można również użyć `downcast` operatora w celu wykonania konwersji typu dynamicznego. Poniższe wyrażenie określa konwersji w dół hierarchii do typu, który jest wnioskowany z kontekstu programu:

```fsharp
downcast expression
```

Jak w przypadku `upcast` operatora, jeśli kompilator nie można wywnioskować typu konkretnego docelowego z kontekstu, zgłasza błąd.

Poniższy kod ilustruje sposób korzystania z `:>` i `:?>` operatorów. Kod pokazuje, że `:?>` operator najlepiej jest używany, gdy wiadomo, że konwersja kończy się pomyślnie, ponieważ w wyniku weryfikacji zgłasza wyjątek `InvalidCastException` Jeśli konwersja nie powiedzie się. Jeśli nie wiesz, że konwersja powiedzie się, test typ, który używa `match` lepiej jest wyrażenia, ponieważ eliminuje narzut generowania wyjątku.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

Ponieważ operatory ogólny `downcast` i `upcast` polegają na wnioskowanie o typie, aby określić typ argumentów i w powyższym kodzie, można zastąpić

```fsharp
let base1 = d1 :> Base1
```

with

```fsharp
let base1 = upcast d1
```

W poprzednim kodzie typ argumentu i zwracane typy są `Derived1` i `Base1`, odpowiednio.

Aby uzyskać więcej informacji na temat testów typ zobacz [wyrażenia dopasowań](match-Expressions.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
