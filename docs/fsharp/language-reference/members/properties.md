---
title: Właściwości (F#)
description: 'Więcej informacji na temat F # właściwości, które są elementami członkowskimi, które reprezentują wartości skojarzonych z obiektem.'
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207567"
---
# <a name="properties"></a><span data-ttu-id="5b7fd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5b7fd-103">Properties</span></span>

<span data-ttu-id="5b7fd-104">*Właściwości* są elementami członkowskimi, które reprezentują wartości skojarzonych z obiektem.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="5b7fd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b7fd-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="5b7fd-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b7fd-106">Remarks</span></span>

<span data-ttu-id="5b7fd-107">Właściwości reprezentują "zawiera" relacji w programowanie zorientowane obiektowo, reprezentujący dane, który jest skojarzony z wystąpieniami obiektu lub, w przypadku statycznej właściwości, z typem.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="5b7fd-108">Można zadeklarować właściwości na dwa sposoby, w zależności od tego, czy chcesz jawnie określić podstawową wartość (nazywane również magazyn zapasowy) dla właściwości lub jeśli chcesz umożliwić kompilatorowi automatyczne generowanie magazyn zapasowy.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="5b7fd-109">Ogólnie rzecz biorąc należy użyć dokładniejsze sposób, jeśli właściwość ma nieuproszczone implementacji i automatyczny sposób, gdy właściwość jest tylko proste otoka wartość lub zmienną.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="5b7fd-110">Aby jawnie zadeklarować właściwości, użyj `member` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="5b7fd-111">Następuje po tej składni deklaratywnej składni, która określa `get` i `set` metody o nazwie *Akcesory*.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="5b7fd-112">Różne rodzaje jawnej składni przedstawione w sekcji składni są używane do właściwości tylko do odczytu i zapisu — tylko do odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="5b7fd-113">Dla właściwości tylko do odczytu, należy zdefiniować tylko `get` metody; dla właściwości tylko do zapisu, zdefiniuj jedynie `set` metody.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="5b7fd-114">Należy pamiętać, że jeśli właściwość ma jednocześnie `get` i `set` metod dostępu, alternatywnej składni można określić atrybuty i modyfikatory dostępności, które różnią się dla każdej metody dostępu, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="5b7fd-115">Dla właściwości odczytu/zapisu, które mają zarówno `get` i `set` metody, kolejność `get` i `set` można cofnąć.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="5b7fd-116">Alternatywnie, możesz podać składni przedstawionej na `get` tylko i składni przedstawionej na `set` zamiast połączoną składnię.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="5b7fd-117">W ten sposób sprawia, że łatwiej komentarz osoby `get` lub `set` metody, jeśli jest coś, co może być konieczne.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="5b7fd-118">Zamiast tego połączoną składnię pozwalającą przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="5b7fd-119">Prywatne wartości danych dla właściwości są nazywane blokady *kopii magazynów*.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="5b7fd-120">Aby kompilator automatycznie tworzyć magazyn zapasowy, należy używać słów kluczowych `member val`, Pomiń własny identyfikator, a następnie podaj wyrażenie można zainicjować właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="5b7fd-121">Jeśli właściwość ma być modyfikowalny, Uwzględnij `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="5b7fd-122">Na przykład następujący typ klasy zawiera dwie automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="5b7fd-123">`Property1` jest tylko do odczytu i jest inicjowany do argumentu dostarczane do konstruktora podstawowego i `Property2` jest konfigurowalną właściwość zainicjowana na pusty ciąg:</span><span class="sxs-lookup"><span data-stu-id="5b7fd-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="5b7fd-124">Automatycznie implementowanych właściwości są częścią inicjowania typu, więc muszą być uwzględnione przed inne definicje elementu członkowskiego, podobnie jak `let` powiązania i `do` powiązania w definicji typu.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="5b7fd-125">Należy pamiętać, że wyrażenie, które inicjuje automatycznie implementowanej właściwości jest oceniane tylko po zainicjowaniu, a nie za każdym razem, gdy uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="5b7fd-126">To zachowanie jest w przeciwieństwie do zachowania jawnie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="5b7fd-127">Skutecznie oznacza to, że kod, aby zainicjować tych właściwości jest dodawany do konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="5b7fd-128">Należy wziąć pod uwagę następujący kod, który pokazuje różnicę:</span><span class="sxs-lookup"><span data-stu-id="5b7fd-128">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="5b7fd-129">**Output**</span><span class="sxs-lookup"><span data-stu-id="5b7fd-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="5b7fd-130">Dane wyjściowe dla poprzedniego kodu pokazuje, że wartość AutoProperty jest niezmieniony po wywołaniu wielokrotnie, natomiast ExplicitProperty zmienia za każdym razem, które jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="5b7fd-131">W tym przykładzie pokazano wyrażenie dla automatycznie implementowanej właściwości nie jest oceniany za każdym razem jest metoda pobierająca właściwości jawnego.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
<span data-ttu-id="5b7fd-132">Istnieją pewne bibliotek, takich jak Entity Framework (`System.Data.Entity`) które wykonują operacje niestandardowe w Konstruktory klasy bazowej, które nie działają prawidłowo w przypadku inicjowania automatycznie implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="5b7fd-133">W takich przypadkach Użyj jawnego właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="5b7fd-134">Właściwości mogą być składowymi typu klasy, struktury, związki dyskryminowane, rekordy, interfejsy i rozszerzeń typu i można także definiować w wyrażeniach obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="5b7fd-135">Atrybuty można zastosować do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="5b7fd-136">Aby zastosować atrybut do właściwości, Zapisywanie atrybutu w osobnym wierszu przed właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="5b7fd-137">Aby uzyskać więcej informacji, zobacz [atrybuty](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5b7fd-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="5b7fd-138">Właściwości są domyślnie publiczne.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-138">By default, properties are public.</span></span> <span data-ttu-id="5b7fd-139">Modyfikatory dostępności można również będą stosowane do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="5b7fd-140">Do zastosowania modyfikatora dostępności, dodaj go bezpośrednio przed nazwę właściwości, jeśli jest on przeznaczony do stosowania zarówno `get` i `set` metod; Dodaj przed `get` i `set` słów kluczowych, jeśli jest różnej dostępności wymagane dla każdej metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="5b7fd-141">*Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="5b7fd-142">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b7fd-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="5b7fd-143">Implementacje właściwości są wykonywane za każdym razem, którego uzyskano dostęp do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="5b7fd-144">Statyczne i właściwości instancji</span><span class="sxs-lookup"><span data-stu-id="5b7fd-144">Static and Instance Properties</span></span>

<span data-ttu-id="5b7fd-145">Właściwości mogą być statyczne lub wystąpienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="5b7fd-146">Właściwości statyczne mogą być wywoływane bez wystąpienia i są używane dla wartości skojarzonej z typem, nie za pomocą poszczególnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="5b7fd-147">W przypadku statycznej właściwości pominąć własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="5b7fd-148">Własny identyfikator jest wymagany dla właściwości wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="5b7fd-149">Następująca definicja właściwość statyczna opiera się na scenariuszu, w którym masz pole statyczne `myStaticValue` oznacza to magazyn zapasowy właściwości.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="5b7fd-150">Właściwości można też tablicy, w którym to przypadku są one nazywane *właściwości indeksowanych*.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="5b7fd-151">Aby uzyskać więcej informacji, zobacz [właściwości indeksowanych](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5b7fd-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="5b7fd-152">Adnotacja typu dla właściwości</span><span class="sxs-lookup"><span data-stu-id="5b7fd-152">Type Annotation for Properties</span></span>

<span data-ttu-id="5b7fd-153">W wielu przypadkach kompilator ma za mało informacji do wywnioskowania typu właściwość z typu magazynu pomocniczego tak, ale można ustawić typ jawnie dodając adnotację typu.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="5b7fd-154">Przy użyciu właściwości zestawu metod dostępu</span><span class="sxs-lookup"><span data-stu-id="5b7fd-154">Using Property set Accessors</span></span>

<span data-ttu-id="5b7fd-155">Można ustawić właściwości, które zapewniają `set` metod dostępu za pomocą `<-` operatora.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="5b7fd-156">Dane wyjściowe są **20**.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="5b7fd-157">Właściwości abstrakcyjne</span><span class="sxs-lookup"><span data-stu-id="5b7fd-157">Abstract Properties</span></span>

<span data-ttu-id="5b7fd-158">Właściwości mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-158">Properties can be abstract.</span></span> <span data-ttu-id="5b7fd-159">Podobnie jak w przypadku metod, `abstract` po prostu oznacza, że istnieje wysyłania wirtualne, skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="5b7fd-160">Właściwości abstrakcyjne mogą być naprawdę abstrakcyjne, oznacza to, bez definicji w tej samej klasie.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="5b7fd-161">Klasa, która zawiera takie właściwości, w związku z tym jest klasą abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="5b7fd-162">Alternatywnie abstrakcyjny po prostu może oznaczać, czy właściwość jest wirtualna, a w takim przypadku definicję musi znajdować się w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="5b7fd-163">Należy pamiętać, że właściwości abstrakcyjne nie mogą być prywatne i jeśli jedną metodę dostępu są abstrakcyjne, druga również musi być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="5b7fd-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="5b7fd-164">Aby uzyskać więcej informacji na temat klasy abstrakcyjne, zobacz [klasy abstrakcyjne](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="5b7fd-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="5b7fd-165">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b7fd-165">See also</span></span>

- [<span data-ttu-id="5b7fd-166">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5b7fd-166">Members</span></span>](index.md)
- [<span data-ttu-id="5b7fd-167">Metody</span><span class="sxs-lookup"><span data-stu-id="5b7fd-167">Methods</span></span>](methods.md)
