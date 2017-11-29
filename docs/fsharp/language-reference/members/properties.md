---
title: "Właściwości (F#)"
description: "Więcej informacji na temat języka F # właściwości, które są elementami członkowskimi, które reprezentują wartości skojarzone z obiektem."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a>Właściwości

*Właściwości* są elementy członkowskie, które reprezentują wartości skojarzone z obiektem.


## <a name="syntax"></a>Składnia

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a>Uwagi
Reprezentuje właściwości "ma" relacji w programowanie zorientowane obiektowo reprezentujący dane skojarzone z wystąpień obiektu lub, w przypadku statycznej właściwości, z typem.

Można zadeklarować właściwości na dwa sposoby, w zależności od tego, czy mają być jawnie określić wartości podstawowej (nazywanych również magazynu zapasowego) dla właściwości lub jeśli chcesz zezwolić kompilator, aby automatycznie wygenerować magazynu zapasowego dla Ciebie. Ogólnie rzecz biorąc należy używać dokładniejsze sposób, jeśli właściwość ma nieuproszczone implementacji oraz sposób automatyczne, gdy właściwość jest tylko proste otoki dla wartości lub zmiennej. Aby jawnie deklarować właściwość, należy użyć `member` — słowo kluczowe. Ta składnia deklaratywne następuje składnię, która określa `get` i `set` metody o nazwie *metody dostępu*. Różne rodzaje jawnej składni wyświetlone w sekcji składni są używane dla właściwości tylko do odczytu i zapisu — tylko do odczytu i zapisu. Dla właściwości tylko do odczytu, możesz określić, tylko `get` metody; dla właściwości tylko do zapisu, zdefiniuj tylko `set` metody. Należy pamiętać, że jeśli właściwość ma zarówno atrybut `get` i `set` metody dostępu, alternatywne składni można określić atrybuty i modyfikatory dostępności, które są inne dla każdego dostępu, jak to pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Dla właściwości odczytu/zapisu, które mają zarówno `get` i `set` metoda, kolejność `get` i `set` można wycofać. Alternatywnie można udostępnić składni wyświetlany dla `get` tylko i składni wyświetlany dla `set` zamiast połączoną składnię. W ten sposób ułatwia komentarz jednostki `get` lub `set` metody, jeśli jest to coś, może być konieczne w celu. Ta alternatywa dla użycia połączoną składnię przedstawiono w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Prywatne wartości blokady dane dla właściwości są nazywane *magazyny kopii*. Aby kompilator automatycznie twórz magazynu zapasowego, użyj słowa kluczowe `member val`, Pomiń własny identyfikator, a następnie podaj wyrażenie zainicjować właściwość. Jeśli właściwość ma być modyfikowalna, obejmują `with get, set`. Na przykład następujący typ klasy zawiera dwie automatycznie implementowanej właściwości. `Property1`jest tylko do odczytu które jest inicjowane z argumentem dostarczonym do podstawowego konstruktora i `Property2` jest można ustawić właściwości zainicjowana na pusty ciąg:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Automatycznie implementowanej właściwości są część inicjowania typu, więc muszą być uwzględnione przed inne definicje elementu członkowskiego, tak jak `let` powiązania i `do` powiązania w definicji typu. Należy pamiętać, że wyrażenie, które inicjuje automatycznie implementowanej właściwości jest obliczane tylko po zainicjowaniu, a nie każdorazowego uzyskiwania dostępu do właściwości. Jest to zachowanie w przeciwieństwie do zachowania jawnie implementowana właściwość. Co to oznacza to, jest to, że kod do zainicjowania te właściwości są dodawane do konstruktora klasy. Rozważmy następujący kod, który pokazuje tej różnicy:

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

**Dane wyjściowe**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

Dane wyjściowe poprzedni kod pokazuje, że wartość AutoProperty jest bez zmian po wywołaniu wielokrotnie, natomiast ExplicitProperty zmienia zawsze, gdy jest ona wywoływana. Oznacza to, że wyrażenie dla automatycznie implementowanej właściwości nie jest następuje za każdym razem, jako metoda pobierająca właściwości jawne.


>[!WARNING]
Istnieją pewne biblioteki, takich jak Entity Framework (`System.Data.Entity`) który wykonywać operacje niestandardowe w konstruktorów klasy podstawowej, które nie działają prawidłowo w przypadku inicjowania automatycznie implementowanej właściwości. W takim wypadku spróbuj użyć jawnego właściwości.

Właściwości mogą być elementami członkowskimi klas, struktur, rozłączne, rekordy, interfejsów i rozszerzenia typu i może być także definiowane w wyrażeniach obiektów.

Atrybuty można zastosować do właściwości. Aby zastosować atrybut do właściwości, należy zapisać atrybut w osobnym wierszu przed właściwości. Aby uzyskać więcej informacji, zobacz [atrybutów](../attributes.md).

Domyślnie właściwości są publiczne. Modyfikatory dostępności można również będą stosowane do właściwości. Aby zastosować modyfikator dostępności, dodaj go bezpośrednio przed nazwę właściwości, jeśli jest on przeznaczony do stosowania zarówno `get` i `set` metod; Dodaj go przed `get` i `set` słów kluczowych w przypadku różnych ułatwień dostępu wymagany w przypadku każdej metody dostępu. *Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).

Implementacje właściwości są wykonywane zawsze, gdy właściwość jest dostępna.


## <a name="static-and-instance-properties"></a>Statyczne i wystąpienia właściwości
Właściwości mogą być statyczne lub wystąpienia właściwości. Właściwości statyczne mogą być wywoływane bez wystąpienia i są używane dla wartości skojarzone z typem, a nie z poszczególnych obiektów. W przypadku statycznej właściwości pominąć własny identyfikator. Wymagany dla właściwości wystąpienia jest własny identyfikator.

Następujące definicja właściwość statyczna jest oparta na scenariusz, w którym zostały pola statycznego `myStaticValue` czyli magazynu zapasowego dla właściwości.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Właściwości można też tablicy, w którym to przypadku są nazywane *właściwości indeksowanych*. Aby uzyskać więcej informacji, zobacz [właściwości indeksowanych](indexed-properties.md).


## <a name="type-annotation-for-properties"></a>Adnotacja typu dla właściwości
W wielu przypadkach kompilator ma za mało informacji do wywnioskowania typu właściwość z typu magazynu zapasowego, ale typ można ustawić jawnie przez dodanie adnotacji typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Za pomocą właściwości metod dostępu set
Można ustawić właściwości, które zapewniają `set` metody dostępu za pomocą `<-` operatora.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Dane wyjściowe **20**.


## <a name="abstract-properties"></a>Właściwości abstrakcyjne
Właściwości mogą być abstrakcyjne. Podobnie jak w przypadku metod `abstract` oznacza brak wysyłki wirtualny skojarzony z właściwością. Właściwości abstrakcyjne mogą być naprawdę abstrakcyjne, oznacza to, bez definicji w tej samej klasy. Klasa, która zawiera właściwość elementu w związku z tym jest klasą abstrakcyjną. Alternatywnie abstrakcyjny tylko może oznaczać, że właściwość jest wirtualna i w takim przypadku definicji musi występować w tej samej klasy. Należy pamiętać, że właściwości abstrakcyjne nie może być prywatny, a jeśli jedną metodę dostępu jest abstrakcyjna, druga musi również być abstrakcyjne. Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klas abstrakcyjnych](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Zobacz też
[Elementy członkowskie](index.md)

[Metody](methods.md)
