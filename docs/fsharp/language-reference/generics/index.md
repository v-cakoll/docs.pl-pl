---
title: Typy ogólne
description: Dowiedz się, jak używać F# ogólne funkcje i typy, które umożliwiają pisanie kodu działającego z różnymi typami bez konieczności użycia kodu.
ms.date: 05/16/2016
ms.openlocfilehash: e30b00343e48d3a8abd51f62c003ba0d1984db18
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641852"
---
# <a name="generics"></a>Typy ogólne

F#Funkcja wartości metod, właściwości i typy zagregowane, takie jak klasy, rejestruje i związki dyskryminowane mogą być *ogólny*. Konstrukcje ogólnego zawiera co najmniej jeden parametr typu, zwykle jest ona dostarczana przez użytkownika ogólnego konstrukcji. Ogólne funkcje i typy umożliwiają pisanie kodu działającego z różnymi typami bez powtarzania kodu dla każdego typu. Wprowadzanie kodu ogólny może okazać się proste w F#, ponieważ często kodu niejawnie wywnioskowana jest ogólny wnioskowanie o typie kompilatora i automatyczna Generalizacja mechanizmów.

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

Deklaracja jawnie ogólna funkcja lub typ znacznie jest podobne do funkcji nieogólnego lub typu, z wyjątkiem specyfikacji (i użyj) parametrami typu, w nawiasy ostre po nazwie funkcji lub typu.

Deklaracje często są niejawnie ogólnego. Jeśli nie zostanie całkowicie typ każdego parametru, który jest używany do tworzenia, funkcja lub typ, kompilator spróbuje wywnioskować typ każdego parametru, wartość i zmienną z tworzonego kodu. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie](../type-inference.md). Jeśli kod dla typu lub funkcji nie inny sposób ograniczyć typy parametrów, funkcja lub typ jest niejawnie ogólnego. Proces ten nosi nazwę *automatyczna Generalizacja*. Istnieją pewne ograniczenia na automatyczna Generalizacja. Na przykład jeśli F# kompilator nie można wywnioskować typów ogólnych konstrukcji, kompilator zgłasza błąd, który odwołuje się do ograniczenia, o nazwie *wartość ograniczenia*. W takiej sytuacji może być konieczne dodawania niektórych adnotacji typu. Aby uzyskać więcej informacji na temat automatyczna Generalizacja i ograniczenie wartości oraz zmian w kodzie, aby rozwiązać ten problem, zobacz [automatyczna Generalizacja](automatic-generalization.md).

W poprzedniej składni *parametrów typu* jest rozdzielaną przecinkami listę parametrów, które reprezentują nieznane typy, które zaczyna się od pojedynczego cudzysłowu, opcjonalnie z klauzulą ograniczenia, który dodatkowo ogranicza typy mogą można użyć dla tego parametru typu. Składnia klauzule ograniczenie różnych rodzajów oraz inne informacje o ograniczeniach, zobacz [ograniczenia](constraints.md).

*Definicji typu* w składni jest taka sama jak definicji typu dla typu nieogólnego. Zawiera parametry konstruktora dla typu klasy, opcjonalny `as` klauzuli, symbol taki sam, pola rekordu `inherit` klauzuli, opcje złożenia dyskryminowanego `let` i `do` powiązania, definicje elementów członkowskich i jeszcze jakieś dozwolone w definicji typu nieogólnego.

Inne elementy składni są takie same jak w przypadku funkcji innych niż ogólne i typów. Na przykład *identyfikator obiektu* jest identyfikatorem, który reprezentuje sam obiekt zawierający.

Właściwości, pola i konstruktory nie może być bardziej ogólny niż typ otaczający. Ponadto w module nie mogą być ogólne.

## <a name="implicitly-generic-constructs"></a>Konstrukcje niejawnie ogólny

Gdy F# kompilator wnioskuje typów w kodzie, automatycznie traktuje dowolnej funkcji, które mogą być rodzajowe jako ogólnego. Jeśli jawnie określić typ takich jak parametr typu, możesz zapobiec automatyczna Generalizacja.

W poniższym przykładzie kodu `makeList` jest ogólny, mimo że ten plik ani jego parametry są jawnie zadeklarowane jako ogólnego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Podpis funkcji wywnioskowana jest `'a -> 'a -> 'a list`. Należy pamiętać, że `a` i `b` w tym przykładzie są wnioskowane mieć tego samego typu. Jest tak, ponieważ są one ze sobą uwzględnione na liście, a wszystkie elementy listy muszą być tego samego typu.

Istnieje również możliwość funkcji ogólnego przy użyciu składni znak pojedynczego cudzysłowu w adnotacji typu, aby wskazać, że typ parametru jest parametr typu ogólnego. W poniższym kodzie `function1` jest ogólna, ponieważ jego parametry są deklarowane w ten sposób jako parametrów typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]

## <a name="explicitly-generic-constructs"></a>Konstrukcje jawnie ogólny

Można również ustawić jako funkcja ogólnego jawnie deklarując jego parametrów typu w nawiasy ostre (`<type-parameter>`). Ilustruje to poniższy kod.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]

## <a name="using-generic-constructs"></a>Za pomocą zwykłego konstrukcji

Gdy używasz funkcji ogólnego lub metody, może nie należy określić argumenty typu. Kompilator używa wnioskowanie o typie wywnioskowania odpowiednie argumenty typu. Jeśli jest nadal niejednoznaczność, można podać argumentów typu w nawiasy ostre, oddziel przecinkami wiele argumentów typu.

Poniższy kod przedstawia korzystania z funkcji, które są zdefiniowane w poprzednich sekcjach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]

> [!NOTE]
> Istnieją dwa sposoby, aby odwołać się do typu ogólnego według nazwy. Na przykład `list<int>` i `int list` do odwoływania się do typu ogólnego na dwa sposoby `list` ma argument typu pojedynczego `int`. Drugim formularzu powszechnie jest używana tylko z wbudowanych F# typy takie jak `list` i `option`. Jeśli istnieje wiele argumentów typu, zwykle użyć składni `Dictionary<int, string>` , ale można również używać składni `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Symboli wieloznacznych jako argumentów typu

Aby określić, że argument typu powinny być zakładane przez kompilator, można użyć znaku podkreślenia lub symbol wieloznaczny (`_`), zamiast argumentu typu nazwanego. Jest to pokazane w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]

## <a name="constraints-in-generic-types-and-functions"></a>Ograniczenia typów rodzajowych i funkcji

W ogólnym typie lub definicji funkcji można użyć tylko konstrukcji, które są znane jako dostępne na parametr typu ogólnego. Jest to wymagane, aby włączyć weryfikację wywołań funkcji i metody w czasie kompilacji. Parametry typu jest jawnie zadeklarowana, mogą dotyczyć jawne ograniczenie parametru typu ogólnego do powiadamiania kompilator, że niektóre metody i funkcje są dostępne. Jednak jeśli zezwolisz programowi F# kompilatorowi wywnioskowania swoje typy parametrów ogólnych określi ograniczenia odpowiedni dla Ciebie. Aby uzyskać więcej informacji, zobacz [ograniczenia](constraints.md).

## <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu

Istnieją dwa rodzaje parametrów typu, które mogą być używane w F# programów. Pierwszy to parametry typu ogólnego rodzaju opisanych w poprzednich sekcjach. Ten pierwszy rodzaj parametru typu jest odpowiednikiem parametrów typu ogólnego, które są używane w językach takich jak Visual Basic i C#. Inny rodzaj parametru typu zależy od F# i jest określany jako *statystycznie rozpoznany typ parametru*. Aby uzyskać informacji na temat te konstrukcje, zobacz [statycznie rozwiązywanych parametrach typu](statically-resolved-type-parameters.md).

## <a name="examples"></a>Przykłady

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka](../index.md)
- [Typy](../fsharp-types.md)
- [Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)
- [Typy ogólne w .NET Framework](~/docs/standard/generics/index.md)
- [Automatyczna generalizacja](automatic-generalization.md)
- [Ograniczenia](constraints.md)
