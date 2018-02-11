---
title: "Spójne kolekcje w języku Visual Basic"
ms.custom: 
ms.date: 04/23/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- tuples [Visual Basic]
ms.assetid: 3e66cd1b-3432-4e1d-8c37-5ebacae8f53f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2653b9dc8a6ecbcb718c20be8bd6275edf4cfb6e
ms.sourcegitcommit: be1fb5d9447ad459bef22b91a91c72e3e0b2d916
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2018
---
# <a name="tuples-visual-basic"></a><span data-ttu-id="98be2-102">Krotki (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98be2-102">Tuples (Visual Basic)</span></span>

<span data-ttu-id="98be2-103">Począwszy od programu Visual Basic 2017 języka Visual Basic udostępnia wbudowaną obsługę krotek, która umożliwia tworzenie krotek i uzyskiwanie dostępu do elementów krotek łatwiejsze.</span><span class="sxs-lookup"><span data-stu-id="98be2-103">Starting with Visual Basic 2017, the Visual Basic language offers built-in support for tuples that makes creating tuples and accessing the elements of tuples easier.</span></span> <span data-ttu-id="98be2-104">Krotka jest strukturą lekki danych, która ma określoną liczbę i sekwencja wartości.</span><span class="sxs-lookup"><span data-stu-id="98be2-104">A tuple is a light-weight data structure that has a specific number and sequence of values.</span></span> <span data-ttu-id="98be2-105">W przypadku wystąpienia spójnej kolekcji, należy zdefiniować liczbę i typ danych w każdej wartości (lub elementu).</span><span class="sxs-lookup"><span data-stu-id="98be2-105">When you instantiate the tuple, you define the number and the data type of each value (or element).</span></span> <span data-ttu-id="98be2-106">Na przykład krotki 2 (lub parę) zawiera dwa elementy.</span><span class="sxs-lookup"><span data-stu-id="98be2-106">For example, a 2-tuple (or pair) has two elements.</span></span> <span data-ttu-id="98be2-107">Może być pierwszym `Boolean` wartości, podczas gdy druga `String`.</span><span class="sxs-lookup"><span data-stu-id="98be2-107">The first might be a `Boolean` value, while the second is a `String`.</span></span> <span data-ttu-id="98be2-108">Ponieważ spójne kolekcje ułatwiają przechowywanie wielu wartości w jednym obiekcie, często są one używane jako lekkie sposób zwrócenia wiele wartości z metody.</span><span class="sxs-lookup"><span data-stu-id="98be2-108">Because tuples make it easy to store multiple values in a single object, they are often used as a lightweight way to return multiple values from a method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98be2-109">Obsługa krotki wymaga <xref:System.ValueTuple> typu.</span><span class="sxs-lookup"><span data-stu-id="98be2-109">Tuple support requires the <xref:System.ValueTuple> type.</span></span> <span data-ttu-id="98be2-110">.NET Framework 4.7 nie jest zainstalowany, należy dodać pakiet NuGet `System.ValueTuple`, która jest dostępna w galerii NuGet.</span><span class="sxs-lookup"><span data-stu-id="98be2-110">If the .NET Framework 4.7 is not installed, you must add the NuGet package `System.ValueTuple`, which is available on the NuGet Gallery.</span></span> <span data-ttu-id="98be2-111">Bez tego pakietu może wystąpić błąd kompilacji podobne do "Wstępnie zdefiniowany typ"ValueTuple(Of,,,)"nie został zdefiniowany ani zaimportowany."</span><span class="sxs-lookup"><span data-stu-id="98be2-111">Without this package, you may get a compilation error similar to, "Predefined type 'ValueTuple(Of,,,)' is not defined or imported."</span></span>

## <a name="instantiating-and-using-a-tuple"></a><span data-ttu-id="98be2-112">Tworzenie wystąpień i przy użyciu spójnych kolekcji</span><span class="sxs-lookup"><span data-stu-id="98be2-112">Instantiating and using a tuple</span></span>

<span data-ttu-id="98be2-113">Umieszczając nawiasami wiadomości błyskawicznych wartości rozdzielanych przecinkami Utwórz wystąpienie spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-113">You instantiate a tuple by enclosing its comma-delimited values im parentheses.</span></span> <span data-ttu-id="98be2-114">Każdy z tych wartości staje się pole spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-114">Each of those values then becomes a field of the tuple.</span></span> <span data-ttu-id="98be2-115">Na przykład poniższy kod definiuje triple (lub krotki 3) z `Date` jako wartość pierwszego `String` jako jego, a `Boolean` jako jego innych.</span><span class="sxs-lookup"><span data-stu-id="98be2-115">For example, the following code defines a triple (or 3-tuple) with a `Date` as its first value, a `String` as its second, and a `Boolean` as its third.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#1)]

<span data-ttu-id="98be2-116">Domyślnie nazwa każdego pola w krotce składa się z ciągu `Item` wraz z pozycji na podstawie jednego pola w spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-116">By default, the name of each field in a tuple consists of the string `Item` along with the field's one-based position in the tuple.</span></span> <span data-ttu-id="98be2-117">Dla tego krotki 3 `Date` pole jest `Item1`, `String` pole jest `Item2`i `Boolean` pole jest `Item3`.</span><span class="sxs-lookup"><span data-stu-id="98be2-117">For this 3-tuple, the `Date` field is `Item1`, the `String` field is `Item2`, and the `Boolean` field is `Item3`.</span></span> <span data-ttu-id="98be2-118">W poniższym przykładzie przedstawiono wartości pól spójna kolekcja znajdująca się w poprzednim wierszu kodu</span><span class="sxs-lookup"><span data-stu-id="98be2-118">The following example displays the values of fields of the tuple instantiated in the previous line of code</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#2)]

<span data-ttu-id="98be2-119">Pola spójnych kolekcji Visual Basic są odczytu i zapisu; Po krotka został uruchomiony, można modyfikować jej wartości.</span><span class="sxs-lookup"><span data-stu-id="98be2-119">The fields of a Visual Basic tuple are read-write; after you've instantiated a tuple, you can modify its values.</span></span> <span data-ttu-id="98be2-120">Poniższy przykład modyfikuje dwie z trzech pól krotki utworzony w poprzednim przykładzie i wyświetla wyniki.</span><span class="sxs-lookup"><span data-stu-id="98be2-120">The following example modifies two of the three fields of the tuple created in the previous example and displays the result.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#3)]

## <a name="instantiating-and-using-a-named-tuple"></a><span data-ttu-id="98be2-121">Tworzenie wystąpień i przy użyciu spójnej kolekcji o nazwie</span><span class="sxs-lookup"><span data-stu-id="98be2-121">Instantiating and using a named tuple</span></span>

<span data-ttu-id="98be2-122">Zamiast przy użyciu domyślnych nazw pól spójnej kolekcji, można utworzyć wystąpienia *o nazwie krotki* przez przypisanie własne nazwy elementów spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-122">Rather than using default names for a tuple's fields, you can instantiate a *named tuple* by assigning your own names to the tuple's elements.</span></span> <span data-ttu-id="98be2-123">Pola krotki mają dostęp przy użyciu nazw przypisane *lub* przez domyślne nazwy.</span><span class="sxs-lookup"><span data-stu-id="98be2-123">The tuple's fields can then be accessed by their assigned names *or* by their default names.</span></span> <span data-ttu-id="98be2-124">Poniższy przykład tworzy wystąpienie tego samego krotki 3 jak poprzednio, z wyjątkiem tego, że jawnie nazwy pierwsze pole `EventDate`, drugi `Name`, a trzeci `IsHoliday`.</span><span class="sxs-lookup"><span data-stu-id="98be2-124">The following example instantiates the same 3-tuple as previously, except that it explicitly names the first field `EventDate`, the second `Name`, and the third `IsHoliday`.</span></span> <span data-ttu-id="98be2-125">Następnie wyświetla wartości pól, modyfikuje je i ponownie wyświetla wartości pól.</span><span class="sxs-lookup"><span data-stu-id="98be2-125">It then displays the field values, modifies them, and displays the field values again.</span></span>

[!code-vb[Instantiate](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple1.vb#4)]

## <a name="inferred-tuple-element-names"></a><span data-ttu-id="98be2-126">Nazwy elementów wywnioskowanych spójnej kolekcji</span><span class="sxs-lookup"><span data-stu-id="98be2-126">Inferred tuple element names</span></span>

<span data-ttu-id="98be2-127">Począwszy od 15 ustęp 3 Visual Basic, Visual Basic można wywnioskować nazwy elementów krotki; nie masz ich jawnie przypisać.</span><span class="sxs-lookup"><span data-stu-id="98be2-127">Starting with Visual Basic 15.3, Visual Basic can infer the names of tuple elements; you do not have to assign them explicitly.</span></span> <span data-ttu-id="98be2-128">Wywnioskowane krotki nazwy są przydatne, gdy zainicjować spójną kolekcję z zestawu zmiennych i ma być taka sama jak nazwa zmiennej nazwy elementu spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-128">Inferred tuple names are useful when you initialize a tuple from a set of variables, and you want the tuple element name to be the same as the variable name.</span></span> 

<span data-ttu-id="98be2-129">Poniższy przykład tworzy `stateInfo` elementy, o nazwie spójnej kolekcji, która zawiera trzy jawnie `state`, `stateName`, i `capital`.</span><span class="sxs-lookup"><span data-stu-id="98be2-129">The following example creates a `stateInfo` tuple that contains three explicitly named elements, `state`, `stateName`, and `capital`.</span></span> <span data-ttu-id="98be2-130">Należy zauważyć, że w nazw elementów, instrukcja inicjowania spójnej kolekcji po prostu przypisuje elementy o wartości zmiennych o identycznej nazwie.</span><span class="sxs-lookup"><span data-stu-id="98be2-130">Note that, in naming the elements, the tuple initialization statement simply assigns the named elements the values of the identically named variables.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#1)]
 
<span data-ttu-id="98be2-131">Ponieważ elementy i zmienne mają taką samą nazwę, kompilator Visual Basic można wywnioskować nazwy pól, jak w poniższym przykładzie pokazano.</span><span class="sxs-lookup"><span data-stu-id="98be2-131">Because elements and variables have the same name, the Visual Basic compiler can infer the names of the fields, as the following example shows.</span></span>

[!code-vb[ExplicitlyNamed](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/named-tuples/program.vb#2)]

<span data-ttu-id="98be2-132">Aby włączyć nazwy elementów interred spójnej kolekcji, należy zdefiniować wersji kompilatora Visual Basic do użycia w projekcie języka Visual Basic (\*.vbproj) plików:</span><span class="sxs-lookup"><span data-stu-id="98be2-132">To enable interred tuple element names, you must define the version of the Visual Basic compiler to use in your Visual Basic project (\*.vbproj) file:</span></span> 

```xml 
<PropertyGroup> 
  <LangVersion>15.3</LangVersion> 
</PropertyGroup> 

The version number can be any version of the Visual Basic compiler starting with 15.3. Rather than hard-coding a specific compiler version, you can also specify "Latest" as the value of `LangVersion` to compile with the most recent version of the Visual Basic compiler installed on your system.

In some cases, the Visual Basic compiler cannot infer the tuple element name from the candidate name, and the tuple field can only be referenced using its default name, such as `Item1`, `Item2`, etc. These include:

- The candidate name is the same as the name of a tuple member, such as `Item3`, `Rest`, or `ToString`.

- The candidate name is duplicated in the tuple.
 
When field name inference fails, Visual Basic does not generate a compiler error, nor is an exception thrown at runtime. Instead, tuple fields must be referenced by their predefined names, such as `Item1` and `Item2`. 
  
## Tuples versus structures

A Visual Basic tuple is a value type that is an instance of one of the a **System.ValueTuple** generic types. For example, the `holiday` tuple defined in the previous example is an instance of the <xref:System.ValueTuple%603> structure. It is designed to be a lightweight container for data. Since the tuple aims to make it easy to create an object with multiple data items, it lacks some of the features that a custom structure might have. These include:

- Customer members. You cannot define your own properties, methods, or events for a tuple.

- Validation. You cannot validate the data assigned to fields.

- Immutability. Visual Basic tuples are mutable. In contrast, a custom structure allows you to control whether an instance is mutable or immutable.

If custom members, property and field validation, or immutability are important, you should use the Visual Basic [Structure](../../../language-reference/statements/structure-statement.md) statement to define a custom value type.

A Visual Basic tuple does inherit the members of its **ValueTuple** type. In addition to its fields, these include the following methods:

| Member | Description |
| ---|---|
| CompareTo | Compares the current tuple to another tuple with the same number of elements. |
| Equals | Determines whether the current tuple is equal to another tuple or object. |
| GetHashCode | Calculates the hash code for the current instance. |
| ToString | Returns the string representation of this tuple, which takes the form `(Item1, Item2...)`, where `Item1` and `Item2` represent the values of the tuple's fields. |

In addition, the **ValueTuple** types implement <xref:System.Collections.IStructuralComparable> and <xref:System.Collections.IStructuralEquatable> interfaces, which allow you to define customer comparers.

## Assignment and tuples

Visual Basic supports assignment between tuple types that have the same number of fields. The field types can be converted if one of the following is true:

- The source and target field are of the same type.

- A widening (or implicit) conversion of the source type to the target type is defined. 

- `Option Strict` is `On`, and a narrowing (or explicit) conversion of the source type to the target type is defined. This conversion can throw an exception if the source value is outside the range of the target type.

Other conversions are not considered for assignments. Let's look at the kinds of assignments that are allowed between tuple types.

Consider these variables used in the following examples:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#1)]

The first two variables, `unnamed` and `anonymous`, do not have semantic names provided for the fields. Their field names are the default `Item1` and `Item2`. The last two variables, `named` and `differentName` have semantic field names. Note that these two tuples have different names for the fields.

All four of these tuples have the same number of fields (referred to as 'arity'), and the types of those fields are identical. Therefore, all of these assignments work:

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#2)]

Notice that the names of the tuples are not assigned. The values of the fields are assigned following the order of the fields in the tuple.

Finally, notice that we can assign the `named` tuple to the `conversion` tuple, even though the first field of `named` is an `Integer`, and the first field of `conversion` is a `Long`. This assignment succeeds because converting an `Integer` to a `Long` is a widening conversion.

[!code-vb[Assign](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple3.vb#3)]

Tuples with different numbers of fields are not assignable:

```vb
' Does not compile.
' VB30311: Value of type '(Integer, Integer, Integer)' cannot be converted
'          to '(Answer As Integer, Message As String)'
var differentShape = (1, 2, 3)
named = differentShape
```

## <a name="tuples-as-method-return-values"></a><span data-ttu-id="98be2-133">Wartości zwracane krotek jako — metoda</span><span class="sxs-lookup"><span data-stu-id="98be2-133">Tuples as method return values</span></span>

<span data-ttu-id="98be2-134">Metoda może zwracać tylko jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="98be2-134">A method can return only a single value.</span></span> <span data-ttu-id="98be2-135">Często jednak chcesz wywołania metody, aby zwrócić wielu wartości.</span><span class="sxs-lookup"><span data-stu-id="98be2-135">Frequently, though, you'd like a method call to return multiple values.</span></span> <span data-ttu-id="98be2-136">Istnieje kilka sposobów obejścia tego ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="98be2-136">There are several ways to work around this limitation:</span></span>

- <span data-ttu-id="98be2-137">Możesz tworzyć niestandardowe klasy lub struktury którego właściwości lub pola reprezentują wartości zwracanych przez metodę.</span><span class="sxs-lookup"><span data-stu-id="98be2-137">You can create a custom class or structure whose properties or fields represent values returned by the method.</span></span> <span data-ttu-id="98be2-138">W związku z tym jest to rozwiązanie ogromnych; wymaga zdefiniowania typu niestandardowego, którego jedynym celem jest można pobrać wartości z wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="98be2-138">Thus is a heavyweight solution; it requires that you define a custom type whose only purpose is to retrieve values from a method call.</span></span>

- <span data-ttu-id="98be2-139">Zwraca pojedynczą wartość z metody i pozostałe wartości zwracane przez przekazywanie ich poprzez odwołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="98be2-139">You can return a single value from the method, and return the remaining values by passing them by reference to the method.</span></span> <span data-ttu-id="98be2-140">Obejmuje to obciążenie tworzenia wystąpienia w zmiennej i ryzyka nieodwracalne nadpisanie wartość zmiennej, który jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="98be2-140">This involves the overhead of instantiating a variable and risks inadvertently overwriting the value of the variable that you pass by reference.</span></span>

- <span data-ttu-id="98be2-141">Można użyć spójnej kolekcji, która to lekkie rozwiązanie do pobierania wiele wartości zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="98be2-141">You can use a tuple, which provides a lightweight solution to retrieving multiple return values.</span></span>

<span data-ttu-id="98be2-142">Na przykład **TryParse** metod .NET powrotu `Boolean` wartość, która wskazuje, czy podczas analizowania operacja zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98be2-142">For example, the **TryParse** methods in .NET return a `Boolean` value that indicates whether the parsing operation succeeded.</span></span> <span data-ttu-id="98be2-143">Wynik operacji przetwarzania jest zwracana w zmiennej przekazywana przez odwołanie do metody.</span><span class="sxs-lookup"><span data-stu-id="98be2-143">The result of the parsing operation is returned in a variable passed by reference to the method.</span></span> <span data-ttu-id="98be2-144">Zazwyczaj wywołanie metodę analizowania, takich jak <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> wygląda podobnie do następującego:</span><span class="sxs-lookup"><span data-stu-id="98be2-144">Normally, a call to the a parsing method such as <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> looks like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#1)]

<span data-ttu-id="98be2-145">Zostanie zwrócona krotka z przetwarzaniem operacji, jeśli firma Microsoft zawijać wywołanie <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metody własnej metody.</span><span class="sxs-lookup"><span data-stu-id="98be2-145">We can return a tuple from the parsing operation if we wrap the call to the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method in our own method.</span></span> <span data-ttu-id="98be2-146">W poniższym przykładzie `NumericLibrary.ParseInteger` wywołania <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> metodę i zwraca spójną kolekcję o nazwie z dwoma elementami.</span><span class="sxs-lookup"><span data-stu-id="98be2-146">In the following example, `NumericLibrary.ParseInteger` calls the <xref:System.Int32.TryParse%2A?displayProperty=nameWithType> method and returns a named tuple with two elements.</span></span> 

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#2)]

<span data-ttu-id="98be2-147">Następnie można wywołać metody z kodu podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="98be2-147">You can then call the method with code like the following:</span></span>

[!code-vb[Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple-returns.vb#3)]

## <a name="visual-basic-tuples-and-tuples-in-the-net-framework"></a><span data-ttu-id="98be2-148">Krotki Visual Basic i spójnych kolekcji w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="98be2-148">Visual Basic tuples and tuples in the .NET Framework</span></span>

<span data-ttu-id="98be2-149">Krotka Visual Basic jest wystąpienie jednego z **System.ValueTuple** typów ogólnych, które zostały wprowadzone w .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="98be2-149">A Visual Basic tuple is an instance of one of the **System.ValueTuple** generic types, which were introduced in the .NET Framework 4.7.</span></span> <span data-ttu-id="98be2-150">.NET Framework obejmuje również zestaw ogólny **System.Tuple** klasy.</span><span class="sxs-lookup"><span data-stu-id="98be2-150">The .NET Framework also includes a set of generic **System.Tuple** classes.</span></span> <span data-ttu-id="98be2-151">Te klasy jednak różnić się od krotek Visual Basic i **System.ValueTuple** typów ogólnych na kilka sposobów:</span><span class="sxs-lookup"><span data-stu-id="98be2-151">These classes, however, differ from Visual Basic tuples and the **System.ValueTuple** generic types in a number of ways:</span></span>

- <span data-ttu-id="98be2-152">Elementy **krotki** klasy są właściwości o nazwie `Item1`, `Item2`i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="98be2-152">The elements of the **Tuple** classes are properties named `Item1`, `Item2`, and so on.</span></span> <span data-ttu-id="98be2-153">W Visual Basic krotek i **ValueTuple** pola są typy elementów spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="98be2-153">In Visual Basic tuples and the **ValueTuple** types, tuple elements are fields.</span></span>

- <span data-ttu-id="98be2-154">Nie można przypisać łatwy do rozpoznania nazwy elementów **krotki** wystąpienia lub **ValueTuple** wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="98be2-154">You cannot assign meaningful names to the elements of a **Tuple** instance or of a **ValueTuple** instance.</span></span> <span data-ttu-id="98be2-155">Visual Basic umożliwia przypisanie nazw, które komunikują się znaczenie pola.</span><span class="sxs-lookup"><span data-stu-id="98be2-155">Visual Basic allows you to assign names that communicate the meaning of the fields.</span></span>

- <span data-ttu-id="98be2-156">Właściwości **krotki** wystąpienia są tylko do odczytu; spójne kolekcje są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="98be2-156">The properties of a **Tuple** instance are read-only; the tuples are immutable.</span></span> <span data-ttu-id="98be2-157">W Visual Basic krotek i **ValueTuple** typów, pól krotki są odczytu i zapisu; spójne kolekcje są modyfikowalne.</span><span class="sxs-lookup"><span data-stu-id="98be2-157">In Visual Basic tuples and the **ValueTuple** types, tuple fields are read-write; the tuples are mutable.</span></span>

- <span data-ttu-id="98be2-158">Ogólnego **krotki** typy są typy referencyjne.</span><span class="sxs-lookup"><span data-stu-id="98be2-158">The generic **Tuple** types are reference types.</span></span> <span data-ttu-id="98be2-159">Korzystanie z tych **krotki** typy oznacza Alokacja obiektów.</span><span class="sxs-lookup"><span data-stu-id="98be2-159">Using these **Tuple** types means allocating objects.</span></span> <span data-ttu-id="98be2-160">Na gorąco ścieżki to ma zauważalnego wpływu na wydajność aplikacji.</span><span class="sxs-lookup"><span data-stu-id="98be2-160">On hot paths, this can have a measurable impact on your application's performance.</span></span> <span data-ttu-id="98be2-161">Krotki Visual Basic i **ValueTuple** typy są typami wartości.</span><span class="sxs-lookup"><span data-stu-id="98be2-161">Visual Basic tuples and the **ValueTuple** types are value types.</span></span>

<span data-ttu-id="98be2-162">Metody rozszerzenia w <xref:System.TupleExtensions> klasy ułatwia konwersję między krotek Visual Basic .NET **krotki** obiektów.</span><span class="sxs-lookup"><span data-stu-id="98be2-162">Extension methods in the <xref:System.TupleExtensions> class make it easy to convert between Visual Basic tuples and .NET **Tuple** objects.</span></span> <span data-ttu-id="98be2-163">**ToTuple** metoda konwertuje spójnych kolekcji Visual Basic .NET **krotki** obiektu i **ToValueTuple** metoda konwertuje .NET **krotki** obiekt do spójnych kolekcji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="98be2-163">The **ToTuple** method converts a Visual Basic tuple to a .NET **Tuple** object, and the **ToValueTuple** method converts a .NET **Tuple** object to a Visual Basic tuple.</span></span>

<span data-ttu-id="98be2-164">Poniższy przykład tworzy spójną kolekcję, konwertuje ją na .NET **krotki** obiektu i konwertuje ją z powrotem do spójnych kolekcji Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="98be2-164">The following example creates a tuple, converts it to a .NET **Tuple** object, and converts it back to a Visual Basic tuple.</span></span> <span data-ttu-id="98be2-165">Przykład następnie porównuje to krotki z oryginału, aby upewnić się, że są one takie same.</span><span class="sxs-lookup"><span data-stu-id="98be2-165">The example then compares this tuple with the original one to ensure that they are equal.</span></span>

[!code-vb[Convert](../../../../../samples/snippets/visualbasic/programming-guide/language-features/data-types/tuple2.vb#1)]

## <a name="see-also"></a><span data-ttu-id="98be2-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98be2-166">See also</span></span>

[<span data-ttu-id="98be2-167">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98be2-167">Visual Basic Language Reference</span></span>](index.md)  
