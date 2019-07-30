---
title: Typy ogólne
description: Dowiedz się, F# jak używać funkcji i typów ogólnych, które umożliwiają pisanie kodu, który działa z różnymi typami bez powtarzania kodu.
ms.date: 05/16/2016
ms.openlocfilehash: 47eed0b8e074cfb591e6d8e2c382b9ea6a6e97f0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630608"
---
# <a name="generics"></a>Typy ogólne

F#wartości funkcji, metody, właściwości i typy agregujące, takie jak klasy, rekordy i Unii rozłącznych, mogą być *Ogólne*. Konstrukcje generyczne zawierają co najmniej jeden parametr typu, który jest zwykle dostarczany przez użytkownika konstrukcji ogólnej. Funkcje i typy ogólne umożliwiają pisanie kodu, który działa z różnymi typami bez powtarzania kodu dla każdego typu. Uczynienie kodu generycznego może być proste F#w, ponieważ często kod jest niejawnie wnioskowany jako ogólny przez wnioskowanie typu kompilatora i automatyczne mechanizmy generalize.

## <a name="syntax"></a>Składnia

```fsharp
// Explicitly generic function.
let function-name<type-parameters> parameter-list =
function-body

// Explicitly generic method.
[ static ] member object-identifer.method-name<type-parameters> parameter-list [ return-type ] =
method-body

// Explicitly generic class, record, interface, structure,
// or discriminated union.
type type-name<type-parameters> type-definition
```

## <a name="remarks"></a>Uwagi

Deklaracja jawnej funkcji ogólnej lub typu jest znacznie taka sama jak w przypadku funkcji niegenerycznej lub typu, z wyjątkiem specyfikacji (i użycia) parametrów typu w nawiasach kątowych po nazwie funkcji lub typu.

Deklaracje są często niejawnie rodzajowe. Jeśli nie określisz w pełni typu każdego parametru, który jest używany do redagowania funkcji lub typu, kompilator próbuje wnioskować o typie każdego parametru, wartości i zmiennej z kodu, który napiszesz. Aby uzyskać więcej informacji, zobacz wnioskowanie o [typie](../type-inference.md). Jeśli kod typu lub funkcji nie ogranicza w inny sposób typów parametrów, funkcja lub typ są niejawnie rodzajowe. Ten proces nosi nazwę *automatycznego uogólniania*. Istnieją pewne ograniczenia dotyczące automatycznego uogólniania. Jeśli na przykład F# kompilator nie może wywnioskować typów dla konstrukcji ogólnej, kompilator zgłosi błąd, który odwołuje się do ograniczenia o nazwie *ograniczenia wartości*. W takim przypadku może być konieczne dodanie adnotacji typu. Aby uzyskać więcej informacji o automatycznym uogólnieniu i ograniczeniu wartości oraz sposobie zmiany kodu w celu rozwiązania problemu, zobacz [Automatyczne uogólnianie](automatic-generalization.md).

W poprzedniej składni *Typ-parametry* jest rozdzielaną przecinkami listą parametrów, które reprezentują nieznane typy, z których każdy zaczyna się od pojedynczego znaku cudzysłowu, opcjonalnie z klauzulą ograniczenia, która dodatkowo ogranicza typy, które mogą być używane dla tego typu konstruktora. Aby poznać składnię klauzul ograniczenia różnych rodzajów i inne informacje o ograniczeniach, zobacz [ograniczenia](constraints.md).

*Definicja typu* w składni jest taka sama jak definicja typu dla typu innego niż ogólny. Obejmuje ona parametry konstruktora dla typu klasy, klauzulę opcjonalną `as` , znak równości, pola rekordu `inherit` , klauzulę, opcje dla Unii `let` rozłącznych i `do` powiązania, definicje elementów członkowskich, i wszystkie inne dozwolone w definicji typu nieogólnego.

Inne elementy składni są takie same jak dla funkcji i typów innych niż ogólne. Na przykład *obiekt-identyfikator* to identyfikator reprezentujący zawierający go obiekt.

Właściwości, pola i konstruktory nie mogą być bardziej ogólne niż typ otaczający. Ponadto wartości w module nie mogą być ogólne.

## <a name="implicitly-generic-constructs"></a>Niejawnie konstrukcje ogólne

Gdy F# kompilator wnioskuje typy w kodzie, automatycznie traktuje wszystkie funkcje, które mogą być generyczne jako ogólne. W przypadku określenia typu jawnie, takiego jak typ parametru, można zapobiec automatycznemu generalizacji.

W poniższym przykładzie `makeList` kodu jest ogólny, nawet mimo że ani jego parametry nie są jawnie zadeklarowane jako ogólne.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Podpis funkcji jest wywnioskowany jako `'a -> 'a -> 'a list`. Należy zauważyć `a` , `b` że i w tym przykładzie są wywnioskowane w celu uzyskania tego samego typu. Jest to spowodowane tym, że są one uwzględnione na liście razem, a wszystkie elementy listy muszą być tego samego typu.

Możesz również uczynić funkcję ogólną przy użyciu składni pojedynczego cudzysłowu w adnotacji typu, aby wskazać, że typ parametru jest parametrem typu ogólnego. W poniższym kodzie `function1` jest ogólny, ponieważ jego parametry są zadeklarowane w ten sposób jako parametry typu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Jawne konstrukcje generyczne

Można również wykonać funkcję ogólną, jawnie deklarując jej parametry typu w nawiasach kątowych (`<type-parameter>`). Ilustruje to poniższy kod.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Korzystanie z konstrukcji ogólnych

W przypadku korzystania z funkcji ogólnych lub metod, może nie trzeba określać argumentów typu. Kompilator używa wnioskowania o typie do wnioskowania odpowiednich argumentów typu. Jeśli nadal występuje niejednoznaczność, można podać argumenty typu w nawiasach kątowych, oddzielając wiele argumentów typu przecinkami.

Poniższy kod przedstawia użycie funkcji, które są zdefiniowane w poprzednich sekcjach.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Istnieją dwa sposoby odwoływania się do typu ogólnego według nazwy. Na przykład `list<int>` i `int list` są dwa sposoby odwoływania się do typu `list` ogólnego, który ma jeden argument `int`typu. Ten drugi formularz jest stosowany do Konwencji tylko z wbudowanymi F# typami, takimi `list` jak `option`i. Jeśli istnieje wiele argumentów typu, zazwyczaj używana jest składnia `Dictionary<int, string>` , ale można również użyć składni. `(int, string) Dictionary`

## <a name="wildcards-as-type-arguments"></a>Symbole wieloznaczne jako argumenty typu

Aby określić, że argument typu powinien być wywnioskowany przez kompilator, można użyć znaku podkreślenia lub symbolu wieloznacznego (`_`) zamiast argumentu nazwanego typu. Jest to pokazane w poniższym kodzie.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Ograniczenia w typach ogólnych i funkcjach

W definicji typu ogólnego lub funkcji można używać tylko tych konstrukcji, które są znane jako dostępne dla parametru typu ogólnego. Jest to wymagane, aby umożliwić weryfikację wywołań funkcji i metod w czasie kompilacji. Jeśli jawnie deklarujesz parametry typu, możesz zastosować jawne ograniczenie do parametru typu ogólnego, aby powiadomić kompilator, że niektóre metody i funkcje są dostępne. Jeśli jednak zezwolisz F# kompilatorowi na wnioskowanie o typach parametrów ogólnych, określisz odpowiednie ograniczenia. Aby uzyskać więcej informacji, zobacz [ograniczenia](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu

Istnieją dwa rodzaje parametrów typu, które mogą być używane w F# programach. Pierwsze są parametry typu ogólnego, które opisano w poprzednich sekcjach. Ten pierwszy rodzaj parametru typu jest odpowiednikiem parametrów typu ogólnego, które są używane w językach takich jak Visual Basic i C#. Inny rodzaj parametru typu jest specyficzny dla F# i jest określany jako *parametr typu statycznie rozpoznany*. Aby uzyskać informacje o tych konstrukcjach, zobacz [statycznie rozpoznane parametry typu](statically-resolved-type-parameters.md).

## <a name="examples"></a>Przykłady

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka](../index.md)
- [Typy](../fsharp-types.md)
- [Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)
- [Typy ogólne w .NET Framework](~/docs/standard/generics/index.md)
- [Automatyczna generalizacja](automatic-generalization.md)
- [Ograniczenia](constraints.md)
