---
title: Właściwości (F#)
description: 'Więcej informacji na temat języka F # właściwości, które są elementami członkowskimi, które reprezentują wartości skojarzone z obiektem.'
ms.date: 05/16/2016
ms.openlocfilehash: 7aa71b1801b44fedcb420b824078004c6c240dc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566164"
---
# <a name="properties"></a><span data-ttu-id="706bd-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="706bd-103">Properties</span></span>

<span data-ttu-id="706bd-104">*Właściwości* są elementy członkowskie, które reprezentują wartości skojarzone z obiektem.</span><span class="sxs-lookup"><span data-stu-id="706bd-104">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="706bd-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="706bd-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="706bd-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="706bd-106">Remarks</span></span>
<span data-ttu-id="706bd-107">Reprezentuje właściwości "ma" relacji w programowanie zorientowane obiektowo reprezentujący dane skojarzone z wystąpień obiektu lub, w przypadku statycznej właściwości, z typem.</span><span class="sxs-lookup"><span data-stu-id="706bd-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="706bd-108">Można zadeklarować właściwości na dwa sposoby, w zależności od tego, czy mają być jawnie określić wartości podstawowej (nazywanych również magazynu zapasowego) dla właściwości lub jeśli chcesz zezwolić kompilator, aby automatycznie wygenerować magazynu zapasowego dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="706bd-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="706bd-109">Ogólnie rzecz biorąc należy używać dokładniejsze sposób, jeśli właściwość ma nieuproszczone implementacji oraz sposób automatyczne, gdy właściwość jest tylko proste otoki dla wartości lub zmiennej.</span><span class="sxs-lookup"><span data-stu-id="706bd-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="706bd-110">Aby jawnie deklarować właściwość, należy użyć `member` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="706bd-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="706bd-111">Ta składnia deklaratywne następuje składnię, która określa `get` i `set` metody o nazwie *metody dostępu*.</span><span class="sxs-lookup"><span data-stu-id="706bd-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="706bd-112">Różne rodzaje jawnej składni wyświetlone w sekcji składni są używane dla właściwości tylko do odczytu i zapisu — tylko do odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="706bd-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="706bd-113">Dla właściwości tylko do odczytu, możesz określić, tylko `get` metody; dla właściwości tylko do zapisu, zdefiniuj tylko `set` metody.</span><span class="sxs-lookup"><span data-stu-id="706bd-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="706bd-114">Należy pamiętać, że jeśli właściwość ma zarówno atrybut `get` i `set` metody dostępu, alternatywne składni można określić atrybuty i modyfikatory dostępności, które są inne dla każdego dostępu, jak to pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="706bd-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="706bd-115">Dla właściwości odczytu/zapisu, które mają zarówno `get` i `set` metoda, kolejność `get` i `set` można wycofać.</span><span class="sxs-lookup"><span data-stu-id="706bd-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="706bd-116">Alternatywnie można udostępnić składni wyświetlany dla `get` tylko i składni wyświetlany dla `set` zamiast połączoną składnię.</span><span class="sxs-lookup"><span data-stu-id="706bd-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="706bd-117">W ten sposób ułatwia komentarz jednostki `get` lub `set` metody, jeśli jest to coś, może być konieczne w celu.</span><span class="sxs-lookup"><span data-stu-id="706bd-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="706bd-118">Ta alternatywa dla użycia połączoną składnię przedstawiono w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="706bd-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="706bd-119">Prywatne wartości blokady dane dla właściwości są nazywane *magazyny kopii*.</span><span class="sxs-lookup"><span data-stu-id="706bd-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="706bd-120">Aby kompilator automatycznie twórz magazynu zapasowego, użyj słowa kluczowe `member val`, Pomiń własny identyfikator, a następnie podaj wyrażenie zainicjować właściwość.</span><span class="sxs-lookup"><span data-stu-id="706bd-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="706bd-121">Jeśli właściwość ma być modyfikowalna, obejmują `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="706bd-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="706bd-122">Na przykład następujący typ klasy zawiera dwie automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="706bd-123">`Property1` jest tylko do odczytu które jest inicjowane z argumentem dostarczonym do podstawowego konstruktora i `Property2` jest można ustawić właściwości zainicjowana na pusty ciąg:</span><span class="sxs-lookup"><span data-stu-id="706bd-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="706bd-124">Automatycznie implementowanej właściwości są część inicjowania typu, więc muszą być uwzględnione przed inne definicje elementu członkowskiego, tak jak `let` powiązania i `do` powiązania w definicji typu.</span><span class="sxs-lookup"><span data-stu-id="706bd-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="706bd-125">Należy pamiętać, że wyrażenie, które inicjuje automatycznie implementowanej właściwości jest obliczane tylko po zainicjowaniu, a nie każdorazowego uzyskiwania dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="706bd-126">Jest to zachowanie w przeciwieństwie do zachowania jawnie implementowana właściwość.</span><span class="sxs-lookup"><span data-stu-id="706bd-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="706bd-127">Co to oznacza to, jest to, że kod do zainicjowania te właściwości są dodawane do konstruktora klasy.</span><span class="sxs-lookup"><span data-stu-id="706bd-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="706bd-128">Rozważmy następujący kod, który pokazuje tej różnicy:</span><span class="sxs-lookup"><span data-stu-id="706bd-128">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="706bd-129">**Output**</span><span class="sxs-lookup"><span data-stu-id="706bd-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="706bd-130">Dane wyjściowe poprzedni kod pokazuje, że wartość AutoProperty jest bez zmian po wywołaniu wielokrotnie, natomiast ExplicitProperty zmienia zawsze, gdy jest ona wywoływana.</span><span class="sxs-lookup"><span data-stu-id="706bd-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="706bd-131">Oznacza to, że wyrażenie dla automatycznie implementowanej właściwości nie jest następuje za każdym razem, jako metoda pobierająca właściwości jawne.</span><span class="sxs-lookup"><span data-stu-id="706bd-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="706bd-132">Istnieją pewne biblioteki, takich jak Entity Framework (`System.Data.Entity`) który wykonywać operacje niestandardowe w konstruktorów klasy podstawowej, które nie działają prawidłowo w przypadku inicjowania automatycznie implementowanej właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="706bd-133">W takim wypadku spróbuj użyć jawnego właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="706bd-134">Właściwości mogą być elementami członkowskimi klas, struktur, rozłączne, rekordy, interfejsów i rozszerzenia typu i może być także definiowane w wyrażeniach obiektów.</span><span class="sxs-lookup"><span data-stu-id="706bd-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="706bd-135">Atrybuty można zastosować do właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="706bd-136">Aby zastosować atrybut do właściwości, należy zapisać atrybut w osobnym wierszu przed właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="706bd-137">Aby uzyskać więcej informacji, zobacz [atrybutów](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="706bd-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="706bd-138">Domyślnie właściwości są publiczne.</span><span class="sxs-lookup"><span data-stu-id="706bd-138">By default, properties are public.</span></span> <span data-ttu-id="706bd-139">Modyfikatory dostępności można również będą stosowane do właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="706bd-140">Aby zastosować modyfikator dostępności, dodaj go bezpośrednio przed nazwę właściwości, jeśli jest on przeznaczony do stosowania zarówno `get` i `set` metod; Dodaj go przed `get` i `set` słów kluczowych w przypadku różnych ułatwień dostępu wymagany w przypadku każdej metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="706bd-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="706bd-141">*Modyfikator dostępności* może być jedną z następujących czynności: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="706bd-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="706bd-142">Aby uzyskać więcej informacji, zobacz [kontroli dostępu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="706bd-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="706bd-143">Implementacje właściwości są wykonywane zawsze, gdy właściwość jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="706bd-143">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="706bd-144">Statyczne i wystąpienia właściwości</span><span class="sxs-lookup"><span data-stu-id="706bd-144">Static and Instance Properties</span></span>
<span data-ttu-id="706bd-145">Właściwości mogą być statyczne lub wystąpienia właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="706bd-146">Właściwości statyczne mogą być wywoływane bez wystąpienia i są używane dla wartości skojarzone z typem, a nie z poszczególnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="706bd-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="706bd-147">W przypadku statycznej właściwości pominąć własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="706bd-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="706bd-148">Wymagany dla właściwości wystąpienia jest własny identyfikator.</span><span class="sxs-lookup"><span data-stu-id="706bd-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="706bd-149">Następujące definicja właściwość statyczna jest oparta na scenariusz, w którym zostały pola statycznego `myStaticValue` czyli magazynu zapasowego dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="706bd-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="706bd-150">Właściwości można też tablicy, w którym to przypadku są nazywane *właściwości indeksowanych*.</span><span class="sxs-lookup"><span data-stu-id="706bd-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="706bd-151">Aby uzyskać więcej informacji, zobacz [właściwości indeksowanych](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="706bd-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="706bd-152">Adnotacja typu dla właściwości</span><span class="sxs-lookup"><span data-stu-id="706bd-152">Type Annotation for Properties</span></span>
<span data-ttu-id="706bd-153">W wielu przypadkach kompilator ma za mało informacji do wywnioskowania typu właściwość z typu magazynu zapasowego, ale typ można ustawić jawnie przez dodanie adnotacji typu.</span><span class="sxs-lookup"><span data-stu-id="706bd-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="706bd-154">Za pomocą właściwości metod dostępu set</span><span class="sxs-lookup"><span data-stu-id="706bd-154">Using Property set Accessors</span></span>
<span data-ttu-id="706bd-155">Można ustawić właściwości, które zapewniają `set` metody dostępu za pomocą `<-` operatora.</span><span class="sxs-lookup"><span data-stu-id="706bd-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="706bd-156">Dane wyjściowe **20**.</span><span class="sxs-lookup"><span data-stu-id="706bd-156">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="706bd-157">Właściwości abstrakcyjne</span><span class="sxs-lookup"><span data-stu-id="706bd-157">Abstract Properties</span></span>
<span data-ttu-id="706bd-158">Właściwości mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="706bd-158">Properties can be abstract.</span></span> <span data-ttu-id="706bd-159">Podobnie jak w przypadku metod `abstract` oznacza brak wysyłki wirtualny skojarzony z właściwością.</span><span class="sxs-lookup"><span data-stu-id="706bd-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="706bd-160">Właściwości abstrakcyjne mogą być naprawdę abstrakcyjne, oznacza to, bez definicji w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="706bd-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="706bd-161">Klasa, która zawiera właściwość elementu w związku z tym jest klasą abstrakcyjną.</span><span class="sxs-lookup"><span data-stu-id="706bd-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="706bd-162">Alternatywnie abstrakcyjny tylko może oznaczać, że właściwość jest wirtualna i w takim przypadku definicji musi występować w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="706bd-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="706bd-163">Należy pamiętać, że właściwości abstrakcyjne nie może być prywatny, a jeśli jedną metodę dostępu jest abstrakcyjna, druga musi również być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="706bd-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="706bd-164">Aby uzyskać więcej informacji na temat klas abstrakcyjnych, zobacz [klas abstrakcyjnych](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="706bd-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="706bd-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="706bd-165">See Also</span></span>
[<span data-ttu-id="706bd-166">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="706bd-166">Members</span></span>](index.md)

[<span data-ttu-id="706bd-167">Metody</span><span class="sxs-lookup"><span data-stu-id="706bd-167">Methods</span></span>](methods.md)
