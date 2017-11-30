---
title: "Typy ogólne (F#)"
description: "Dowiedz się, jak używać funkcje ogólne F # i typy, które umożliwiają pisania kodu, który współpracuje z różnymi typami bez powtarzania kodu."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a9f2e2ee-bcb1-4ce3-8531-850aa183040f
ms.openlocfilehash: e7a5712fddf4d372d1ada86927f50e394a59a410
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="generics"></a>Typy ogólne

Funkcja F # wartości, metody, właściwości oraz typy agregacji, takich jak klasy, rejestruje i mogą być rozłączne *ogólnego*. Konstrukcje ogólnego zawiera co najmniej jeden parametr typu, który zazwyczaj jest podany przez użytkownika Ogólna konstrukcja. Funkcje ogólne i typy umożliwiają pisania kodu, który współpracuje z różnymi typami bez powtarzania kod dla każdego typu. Tworzenie Kod rodzajowy może być proste w F #, ponieważ często kodu jest niejawnie wywnioskować, aby wartość była ogólna wnioskowanie o typie kompilatora i mechanizmów automatyczna Generalizacja.


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
Deklaracja jawnie ogólnego funkcja lub typ jest inny niż ogólny funkcja lub typ, z wyjątkiem specyfikacji (i użyj) parametrów typu w nawiasach ostrych po nazwie funkcji lub typu.

Deklaracje są często niejawnie ogólnego. Jeśli nie zostanie całkowicie typu co parametr, który służy do tworzenia funkcji lub typu, kompilator próbuje wnioskować o typie każdego parametru, wartość oraz zmiennej tworzonego kodu. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie](../type-inference.md). Jeśli kod typu lub funkcji nie inaczej ograniczyć typami parametrów, funkcji lub typu jest niejawnie rodzajowa. Ten proces nosi nazwę *automatyczna Generalizacja*. Istnieją pewne ograniczenia na automatyczna Generalizacja. Na przykład w przypadku nie można wywnioskować typów dla Ogólna konstrukcja kompilator języka F #, kompilator zgłasza błąd, który odwołuje się do ograniczenia o nazwie *wartość ograniczenia*. W takim przypadku należy dodać niektóre adnotacji typu. Aby uzyskać więcej informacji na temat automatyczna Generalizacja i ograniczenie wartości oraz jak zmienić swój kod, aby rozwiązać problem, zobacz [automatyczna Generalizacja](automatic-generalization.md).

W poprzednich składni *parametry typu* jest rozdzielaną przecinkami listę parametrów, które reprezentują nieznanych typów, z których każdy rozpoczyna się od pojedynczego cudzysłowu, opcjonalnie z klauzula constraint ograniczającego dodatkowe typy mogą można użyć dla tego parametru typu. Składni ograniczenia klauzule różnego rodzaju oraz inne informacje o ograniczeniach, zobacz [ograniczenia](constraints.md).

*Definicji typu* w składni jest taka sama jak definicji typu dla typu nieogólnego. Zawiera parametry konstruktora dla typu klasy, opcjonalny `as` klauzuli, symbol taki sam, pola rekordu `inherit` klauzuli, wybór rozróżnianą Unię `let` i `do` powiązań, definicji elementu członkowskiego i nic więcej w definicji typu nieogólnego.

Inne elementy składni są takie same jak te funkcje nieogólnego i typów. Na przykład *identyfikator obiektu* jest identyfikatorem, który reprezentuje samego obiektu zawierającego.

Właściwości, pól i konstruktory nie może być bardziej ogólne niż typ otaczający. Ponadto w module nie mogą być ogólne.


## <a name="implicitly-generic-constructs"></a>Konstrukcje niejawnie ogólny
Gdy kompilator języka F # wnioskuje typów w kodzie, automatycznie traktuje dowolnej funkcji, które mogą być ogólne jako ogólnego. Jeśli jawnie określić typ takich jak parametr typu, możesz zapobiec automatyczna Generalizacja.

W poniższym przykładzie kodu `makeList` jest rodzajowy, nawet jeśli ten plik ani jego parametrów są jawnie deklarować jako ogólnego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1700.fs)]

Podpis funkcji jest wywnioskowany jako `'a -> 'a -> 'a list`. Należy pamiętać, że `a` i `b` w tym przykładzie są wartością tego samego typu. Jest tak, ponieważ są one razem uwzględnione na liście, a wszystkie elementy listy muszą być tego samego typu.

Możesz również wprowadzić funkcję ogólnego za pomocą składni pojedynczego cudzysłowu w adnotację typu, aby wskazać, że parametr typu jest parametr typu ogólnego. W poniższym kodzie `function1` jest rodzajowy, ponieważ jego parametrów są zadeklarowane w ten sposób jako parametrów typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1701.fs)]
    
## <a name="explicitly-generic-constructs"></a>Konstrukcje jawnie ogólny
Można również ustawić funkcję ogólnego przez zadeklarowanie jawnie swoich parametrów typu w nawiasach ostrych (`<type-parameter>`). Ilustruje to poniższy kod.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1703.fs)]
    
## <a name="using-generic-constructs"></a>Przy użyciu zwykłego konstrukcji
Korzystając z funkcji ogólnego lub metody, nie masz określić argumenty typu. Kompilator używa wnioskowanie o typie można wywnioskować argumentów odpowiedniego typu. Jeśli nadal niejednoznaczności, można podać argumentów typu w nawiasy, oddzielając przecinkami wiele argumentów typu.

Poniższy kod przedstawia użycie funkcji, które są zdefiniowane w poprzednich sekcjach.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1702.fs)]
    
>[!NOTE]
Istnieją dwa sposoby odwołuje się do typu ogólnego według nazwy. Na przykład `list<int>` i `int list` są dwa sposoby odwołuje się do typu ogólnego `list` mający jednym typem argumentu `int`. Ostatni formularz jest powszechnie używana tylko z wbudowanych typów F # takich jak `list` i `option`. Jeśli istnieje wiele argumentów typu, zwykle jest używana składnia `Dictionary<int, string>` , ale można również używać składni `(int, string) Dictionary`.

## <a name="wildcards-as-type-arguments"></a>Symboli wieloznacznych jako argumentów typu
Aby określić, że argument typu powinny być zakładane przez kompilator, można użyć znaku podkreślenia lub symbolu wieloznacznego (`_`), zamiast argumentu nazwanego typu. Przedstawiono to w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1704.fs)]
    
## <a name="constraints-in-generic-types-and-functions"></a>Ograniczenia ogólne typy i funkcje
W ogólnym typie lub definicji funkcji można użyć tylko tych konstrukcji, które są dostępne na parametr typu ogólnego. Jest to wymagane w celu włączenia weryfikacji wywołania funkcji i metody w czasie kompilacji. Parametry typu jest jawnie zadeklarowana, można zastosować jawne ograniczenia parametru typu ogólnego, aby powiadomić kompilator niektórych metod i funkcje są dostępne. Jednak jeśli zezwolisz wnioskować Twojej typy parametrów ogólnych kompilator języka F # zostanie określone odpowiednie ograniczenia dla Ciebie. Aby uzyskać więcej informacji, zobacz [ograniczenia](constraints.md).


## <a name="statically-resolved-type-parameters"></a>Statycznie rozwiązywane parametry typu
Istnieją dwa rodzaje parametrów typu, których można użyć w programach F #. Pierwszy są parametry typu ogólnego określonych w poprzednich sekcjach. Tego rodzaju pierwszy parametr typu jest odpowiednikiem parametry typu ogólnego, które są używane w językach takich jak Visual Basic i C#. Inny rodzaj typu parametru są specyficzne dla języka F # i jest nazywany *parametr typu statycznie rozwiązywane*. Informacje o tych konstrukcji, zobacz [statycznie rozwiązane parametrów typu](statically-resolved-type-parameters.md).


## <a name="examples"></a>Przykłady
[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1705.fs)]
    
## <a name="see-also"></a>Zobacz też
[Odwołanie językowe](../index.md)

[Typy](../fsharp-types.md)

[Statycznie rozwiązywane parametry typu](statically-resolved-type-parameters.md)

[Typy ogólne w programie .NET Framework](~/docs/standard/generics/index.md)

[Automatyczna Generalizacja](automatic-generalization.md)

[Ograniczenia](constraints.md)
