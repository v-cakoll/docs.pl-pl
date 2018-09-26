---
title: Właściwości (F#)
description: 'Więcej informacji na temat F # właściwości, które są elementami członkowskimi, które reprezentują wartości skojarzonych z obiektem.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209876"
---
# <a name="properties"></a>Właściwości

*Właściwości* są elementami członkowskimi, które reprezentują wartości skojarzonych z obiektem.

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

Właściwości reprezentują "zawiera" relacji w programowanie zorientowane obiektowo, reprezentujący dane, który jest skojarzony z wystąpieniami obiektu lub, w przypadku statycznej właściwości, z typem.

Można zadeklarować właściwości na dwa sposoby, w zależności od tego, czy chcesz jawnie określić podstawową wartość (nazywane również magazyn zapasowy) dla właściwości lub jeśli chcesz umożliwić kompilatorowi automatyczne generowanie magazyn zapasowy. Ogólnie rzecz biorąc należy użyć dokładniejsze sposób, jeśli właściwość ma nieuproszczone implementacji i automatyczny sposób, gdy właściwość jest tylko proste otoka wartość lub zmienną. Aby jawnie zadeklarować właściwości, użyj `member` — słowo kluczowe. Następuje po tej składni deklaratywnej składni, która określa `get` i `set` metody o nazwie *Akcesory*. Różne rodzaje jawnej składni przedstawione w sekcji składni są używane do właściwości tylko do odczytu i zapisu — tylko do odczytu/zapisu. Dla właściwości tylko do odczytu, należy zdefiniować tylko `get` metody; dla właściwości tylko do zapisu, zdefiniuj jedynie `set` metody. Należy pamiętać, że jeśli właściwość ma jednocześnie `get` i `set` metod dostępu, alternatywnej składni można określić atrybuty i modyfikatory dostępności, które różnią się dla każdej metody dostępu, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

Dla właściwości odczytu/zapisu, które mają zarówno `get` i `set` metody, kolejność `get` i `set` można cofnąć. Alternatywnie, możesz podać składni przedstawionej na `get` tylko i składni przedstawionej na `set` zamiast połączoną składnię. W ten sposób sprawia, że łatwiej komentarz osoby `get` lub `set` metody, jeśli jest coś, co może być konieczne. Zamiast tego połączoną składnię pozwalającą przedstawiono w poniższym kodzie.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

Prywatne wartości danych dla właściwości są nazywane blokady *kopii magazynów*. Aby kompilator automatycznie tworzyć magazyn zapasowy, należy używać słów kluczowych `member val`, Pomiń własny identyfikator, a następnie podaj wyrażenie można zainicjować właściwości. Jeśli właściwość ma być modyfikowalny, Uwzględnij `with get, set`. Na przykład następujący typ klasy zawiera dwie automatycznie implementowanej właściwości. `Property1` jest tylko do odczytu i jest inicjowany do argumentu dostarczane do konstruktora podstawowego i `Property2` jest konfigurowalną właściwość zainicjowana na pusty ciąg:

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

Automatycznie implementowanych właściwości są częścią inicjowania typu, więc muszą być uwzględnione przed inne definicje elementu członkowskiego, podobnie jak `let` powiązania i `do` powiązania w definicji typu. Należy pamiętać, że wyrażenie, które inicjuje automatycznie implementowanej właściwości jest oceniane tylko po zainicjowaniu, a nie za każdym razem, gdy uzyskano dostęp do właściwości. To zachowanie jest w przeciwieństwie do zachowania jawnie implementowanej właściwości. Skutecznie oznacza to, że kod, aby zainicjować tych właściwości jest dodawany do konstruktora klasy. Należy wziąć pod uwagę następujący kod, który pokazuje różnicę:

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

**Output**

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

Dane wyjściowe dla poprzedniego kodu pokazuje, że wartość AutoProperty jest niezmieniony po wywołaniu wielokrotnie, natomiast ExplicitProperty zmienia za każdym razem, które jest wywoływane. W tym przykładzie pokazano wyrażenie dla automatycznie implementowanej właściwości nie jest oceniany za każdym razem jest metoda pobierająca właściwości jawnego.

>[!WARNING]
Istnieją pewne bibliotek, takich jak Entity Framework (`System.Data.Entity`) które wykonują operacje niestandardowe w Konstruktory klasy bazowej, które nie działają prawidłowo w przypadku inicjowania automatycznie implementowanych właściwości. W takich przypadkach Użyj jawnego właściwości.

Właściwości mogą być składowymi typu klasy, struktury, związki dyskryminowane, rekordy, interfejsy i rozszerzeń typu i można także definiować w wyrażeniach obiektu.

Atrybuty można zastosować do właściwości. Aby zastosować atrybut do właściwości, Zapisywanie atrybutu w osobnym wierszu przed właściwości. Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).

Właściwości są domyślnie publiczne. Modyfikatory dostępności można również będą stosowane do właściwości. Do zastosowania modyfikatora dostępności, dodaj go bezpośrednio przed nazwę właściwości, jeśli jest on przeznaczony do stosowania zarówno `get` i `set` metod; Dodaj przed `get` i `set` słów kluczowych, jeśli jest różnej dostępności wymagane dla każdej metody dostępu. *Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`. Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).

Implementacje właściwości są wykonywane za każdym razem, którego uzyskano dostęp do właściwości.

## <a name="static-and-instance-properties"></a>Statyczne i właściwości instancji

Właściwości mogą być statyczne lub wystąpienia właściwości. Właściwości statyczne mogą być wywoływane bez wystąpienia i są używane dla wartości skojarzonej z typem, nie za pomocą poszczególnych obiektów. W przypadku statycznej właściwości pominąć własny identyfikator. Własny identyfikator jest wymagany dla właściwości wystąpienia.

Następująca definicja właściwość statyczna opiera się na scenariuszu, w którym masz pole statyczne `myStaticValue` oznacza to magazyn zapasowy właściwości.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

Właściwości można też tablicy, w którym to przypadku są one nazywane *właściwości indeksowanych*. Aby uzyskać więcej informacji, zobacz [właściwości indeksowanych](indexed-properties.md).

## <a name="type-annotation-for-properties"></a>Adnotacja typu dla właściwości

W wielu przypadkach kompilator ma za mało informacji do wywnioskowania typu właściwość z typu magazynu pomocniczego tak, ale można ustawić typ jawnie dodając adnotację typu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a>Przy użyciu właściwości zestawu metod dostępu

Można ustawić właściwości, które zapewniają `set` metod dostępu za pomocą `<-` operatora.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

Dane wyjściowe są **20**.

## <a name="abstract-properties"></a>Właściwości abstrakcyjne

Właściwości mogą być abstrakcyjne. Podobnie jak w przypadku metod, `abstract` po prostu oznacza, że istnieje wysyłania wirtualne, skojarzony z właściwością. Właściwości abstrakcyjne mogą być naprawdę abstrakcyjne, oznacza to, bez definicji w tej samej klasie. Klasa, która zawiera takie właściwości, w związku z tym jest klasą abstrakcyjną. Alternatywnie abstrakcyjny po prostu może oznaczać, czy właściwość jest wirtualna, a w takim przypadku definicję musi znajdować się w tej samej klasy. Należy pamiętać, że właściwości abstrakcyjne nie mogą być prywatne i jeśli jedną metodę dostępu są abstrakcyjne, druga również musi być abstrakcyjna. Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [klasy abstrakcyjne](../abstract-classes.md).

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a>Zobacz także

- [Elementy członkowskie](index.md)
- [Metody](methods.md)
