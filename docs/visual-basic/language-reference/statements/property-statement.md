---
title: Property — Instrukcja
ms.date: 05/12/2018
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
ms.openlocfilehash: 80bce2442d96ecb9c548a88c8e5ee44c6258473b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346757"
---
# <a name="property-statement"></a><span data-ttu-id="8cd29-102">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="8cd29-102">Property Statement</span></span>

<span data-ttu-id="8cd29-103">Deklaruje nazwę właściwości i procedury właściwości używane do przechowywania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cd29-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8cd29-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
    [ <attributelist> ] [ accessmodifier ] Get
        [ statements ]
    End Get
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )
        [ statements ]
    End Set
End Property
- or -
[ <attributelist> ] [ Default ] [ accessmodifier ]
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]
```

## <a name="parts"></a><span data-ttu-id="8cd29-105">Części</span><span class="sxs-lookup"><span data-stu-id="8cd29-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="8cd29-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-106">Optional.</span></span> <span data-ttu-id="8cd29-107">Lista atrybutów, które są stosowane do tej właściwości lub `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="8cd29-108">Zobacz [listę atrybutów](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-108">See [Attribute List](attribute-list.md).</span></span>

- `Default`

  <span data-ttu-id="8cd29-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-109">Optional.</span></span> <span data-ttu-id="8cd29-110">Określa, że ta właściwość jest właściwością domyślną klasy lub struktury, w której jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="8cd29-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="8cd29-111">Właściwości domyślne muszą akceptować parametry i mogą być ustawiane i pobierane bez określenia nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="8cd29-112">W przypadku deklarowania właściwości jako `Default`nie można użyć `Private` we właściwości lub jednej z jej procedur właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>

- `accessmodifier`

  <span data-ttu-id="8cd29-113">Opcjonalne w instrukcji `Property` i na co najmniej jednej instrukcji `Get` i `Set`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="8cd29-114">Może to być jeden z następujących modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="8cd29-114">Can be one of the following:</span></span>

  - [<span data-ttu-id="8cd29-115">Public</span><span class="sxs-lookup"><span data-stu-id="8cd29-115">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="8cd29-116">Protected</span><span class="sxs-lookup"><span data-stu-id="8cd29-116">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="8cd29-117">Friend</span><span class="sxs-lookup"><span data-stu-id="8cd29-117">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="8cd29-118">Private</span><span class="sxs-lookup"><span data-stu-id="8cd29-118">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="8cd29-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="8cd29-119">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="8cd29-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="8cd29-120">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="8cd29-121">Zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-121">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `propertymodifiers`

  <span data-ttu-id="8cd29-122">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-122">Optional.</span></span> <span data-ttu-id="8cd29-123">Może to być jeden z następujących modyfikatorów dostępu:</span><span class="sxs-lookup"><span data-stu-id="8cd29-123">Can be one of the following:</span></span>

  - [<span data-ttu-id="8cd29-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="8cd29-124">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="8cd29-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="8cd29-125">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="8cd29-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="8cd29-126">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="8cd29-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="8cd29-127">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="8cd29-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="8cd29-128">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="8cd29-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-129">Optional.</span></span> <span data-ttu-id="8cd29-130">Zobacz [udostępnianie](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-130">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="8cd29-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-131">Optional.</span></span> <span data-ttu-id="8cd29-132">Zobacz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-132">See [Shadows](../modifiers/shadows.md).</span></span>

- `ReadOnly`

  <span data-ttu-id="8cd29-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-133">Optional.</span></span> <span data-ttu-id="8cd29-134">Zobacz [tylko do odczytu](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-134">See [ReadOnly](../modifiers/readonly.md).</span></span>

- `WriteOnly`

  <span data-ttu-id="8cd29-135">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-135">Optional.</span></span> <span data-ttu-id="8cd29-136">Zobacz [WriteOnly](../modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-136">See [WriteOnly](../modifiers/writeonly.md).</span></span>

- `Iterator`

  <span data-ttu-id="8cd29-137">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-137">Optional.</span></span> <span data-ttu-id="8cd29-138">Zobacz [iterator](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-138">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="8cd29-139">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8cd29-139">Required.</span></span> <span data-ttu-id="8cd29-140">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-140">Name of the property.</span></span> <span data-ttu-id="8cd29-141">Zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-141">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `parameterlist`

  <span data-ttu-id="8cd29-142">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-142">Optional.</span></span> <span data-ttu-id="8cd29-143">Lista nazw zmiennych lokalnych reprezentujących parametry tej właściwości oraz możliwe dodatkowe parametry procedury `Set`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="8cd29-144">Zobacz [listę parametrów](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-144">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="8cd29-145">Wymagane, jeśli `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="8cd29-146">Typ danych wartości zwracanej przez tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="8cd29-146">Data type of the value returned by this property.</span></span>

- `Implements`

  <span data-ttu-id="8cd29-147">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-147">Optional.</span></span> <span data-ttu-id="8cd29-148">Wskazuje, że ta właściwość implementuje jedną lub więcej właściwości, każda zdefiniowana w interfejsie implementowanym przez tę właściwość zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="8cd29-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="8cd29-149">Zobacz [instrukcja Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-149">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="8cd29-150">Wymagane, jeśli podano `Implements`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="8cd29-151">Lista implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-151">List of properties being implemented.</span></span>

  `implementedproperty [ , implementedproperty ... ]`

  <span data-ttu-id="8cd29-152">Każda `implementedproperty` ma następującą składnię i części:</span><span class="sxs-lookup"><span data-stu-id="8cd29-152">Each `implementedproperty` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="8cd29-153">Części</span><span class="sxs-lookup"><span data-stu-id="8cd29-153">Part</span></span>|<span data-ttu-id="8cd29-154">Opis</span><span class="sxs-lookup"><span data-stu-id="8cd29-154">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="8cd29-155">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8cd29-155">Required.</span></span> <span data-ttu-id="8cd29-156">Nazwa interfejsu implementowanego przez tę właściwość zawierającą klasę lub strukturę.</span><span class="sxs-lookup"><span data-stu-id="8cd29-156">Name of an interface implemented by this property's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="8cd29-157">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="8cd29-157">Required.</span></span> <span data-ttu-id="8cd29-158">Nazwa, przez którą właściwość jest zdefiniowana w `interface`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-158">Name by which the property is defined in `interface`.</span></span>|

- `Get`

  <span data-ttu-id="8cd29-159">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-159">Optional.</span></span> <span data-ttu-id="8cd29-160">Wymagane, jeśli właściwość jest oznaczona `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-160">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="8cd29-161">Uruchamia procedurę właściwości `Get`, która jest używana do zwracania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  <span data-ttu-id="8cd29-162">Instrukcja `Get` nie jest używana z właściwościami, które są [implementowane](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-162">The `Get` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `statements`

  <span data-ttu-id="8cd29-163">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-163">Optional.</span></span> <span data-ttu-id="8cd29-164">Blok instrukcji do uruchomienia w ramach procedury `Get` lub `Set`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-164">Block of statements to run within the `Get` or `Set` procedure.</span></span>

- `End Get`

  <span data-ttu-id="8cd29-165">Kończy procedurę właściwości `Get`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-165">Terminates the `Get` property procedure.</span></span>

- `Set`

  <span data-ttu-id="8cd29-166">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="8cd29-166">Optional.</span></span> <span data-ttu-id="8cd29-167">Wymagane, jeśli właściwość jest oznaczona `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-167">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="8cd29-168">Uruchamia procedurę właściwości `Set`, która jest używana do przechowywania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-168">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  <span data-ttu-id="8cd29-169">Instrukcja `Set` nie jest używana z właściwościami, które są [implementowane](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-169">The `Set` statement is not used with [auto-implemented properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

- `End Set`

  <span data-ttu-id="8cd29-170">Kończy procedurę właściwości `Set`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-170">Terminates the `Set` property procedure.</span></span>

- `End Property`

  <span data-ttu-id="8cd29-171">Kończy definicję tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-171">Terminates the definition of this property.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cd29-172">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8cd29-172">Remarks</span></span>

<span data-ttu-id="8cd29-173">Instrukcja `Property` wprowadza deklarację właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-173">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="8cd29-174">Właściwość może mieć procedurę `Get` (tylko do odczytu), procedurę `Set` (tylko zapis) lub obie (odczyt i zapis).</span><span class="sxs-lookup"><span data-stu-id="8cd29-174">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="8cd29-175">Możesz pominąć `Get` i `Set` procedury w przypadku użycia właściwości, która jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="8cd29-175">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="8cd29-176">Aby uzyskać więcej informacji, zobacz [zaimplementowane właściwości](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-176">For more information, see [Auto-Implemented Properties](../../programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>

<span data-ttu-id="8cd29-177">`Property` można użyć tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="8cd29-177">You can use `Property` only at class level.</span></span> <span data-ttu-id="8cd29-178">Oznacza to, że *kontekst deklaracji* właściwości musi być klasą, strukturą, modułem lub interfejsem i nie może być plikiem źródłowym, przestrzenią nazw, procedurą lub blokiem.</span><span class="sxs-lookup"><span data-stu-id="8cd29-178">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="8cd29-179">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8cd29-179">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="8cd29-180">Domyślnie właściwości używają publicznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="8cd29-180">By default, properties use public access.</span></span> <span data-ttu-id="8cd29-181">Poziom dostępu do właściwości można dostosować za pomocą modyfikatora dostępu w instrukcji `Property` i opcjonalnie można dostosować jedną z jej procedur właściwości do bardziej restrykcyjnego poziomu dostępu.</span><span class="sxs-lookup"><span data-stu-id="8cd29-181">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>

<span data-ttu-id="8cd29-182">Visual Basic przekazuje parametr do procedury `Set` podczas przypisywania właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-182">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="8cd29-183">Jeśli nie podasz parametru dla `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-183">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="8cd29-184">Ten parametr zawiera wartość, która ma zostać przypisana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-184">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="8cd29-185">Zwykle ta wartość jest przechowywana w prywatnej zmiennej lokalnej i zwracana przy każdym wywołaniu procedury `Get`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-185">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>

## <a name="rules"></a><span data-ttu-id="8cd29-186">Reguły</span><span class="sxs-lookup"><span data-stu-id="8cd29-186">Rules</span></span>

- <span data-ttu-id="8cd29-187">**Mieszane poziomy dostępu.**</span><span class="sxs-lookup"><span data-stu-id="8cd29-187">**Mixed Access Levels.**</span></span> <span data-ttu-id="8cd29-188">W przypadku definiowania właściwości do odczytu i zapisu można opcjonalnie określić inny poziom dostępu dla `Get` lub procedury `Set`, ale nie dla obu tych opcji.</span><span class="sxs-lookup"><span data-stu-id="8cd29-188">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="8cd29-189">W takim przypadku poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-189">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="8cd29-190">Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować procedurę `Set` `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-190">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>

  <span data-ttu-id="8cd29-191">Jeśli definiujesz Właściwość `ReadOnly` lub `WriteOnly`, procedura pojedynczej właściwości (odpowiednio`Get` lub `Set`) reprezentuje wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-191">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="8cd29-192">Nie można zadeklarować innego poziomu dostępu dla takiej procedury, ponieważ spowodowałoby to ustawienie dwóch poziomów dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-192">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>

- <span data-ttu-id="8cd29-193">**Typ zwracany.**</span><span class="sxs-lookup"><span data-stu-id="8cd29-193">**Return Type.**</span></span> <span data-ttu-id="8cd29-194">Instrukcja `Property` może deklarować typ danych zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-194">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="8cd29-195">Można określić dowolny typ danych lub nazwę wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="8cd29-195">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>

  <span data-ttu-id="8cd29-196">Jeśli nie określisz `returntype`, właściwość zwróci `Object`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-196">If you do not specify `returntype`, the property returns `Object`.</span></span>

- <span data-ttu-id="8cd29-197">**Realizacji.**</span><span class="sxs-lookup"><span data-stu-id="8cd29-197">**Implementation.**</span></span> <span data-ttu-id="8cd29-198">Jeśli ta właściwość używa słowa kluczowego `Implements`, zawierająca klasę lub strukturę musi mieć instrukcję `Implements` bezpośrednio po instrukcji `Class` lub `Structure`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-198">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="8cd29-199">Instrukcja `Implements` musi zawierać każdy interfejs określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-199">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="8cd29-200">Jednak nazwa, za pomocą której interfejs definiuje `Property` (w `definedname`), nie musi być taka sama jak nazwa tej właściwości (w `name`).</span><span class="sxs-lookup"><span data-stu-id="8cd29-200">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>

## <a name="behavior"></a><span data-ttu-id="8cd29-201">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="8cd29-201">Behavior</span></span>

- <span data-ttu-id="8cd29-202">**Powrót z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="8cd29-202">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="8cd29-203">Gdy procedura `Get` lub `Set` powraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po wywołaniu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8cd29-203">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>

  <span data-ttu-id="8cd29-204">Instrukcje `Exit Property` i `Return` powodują natychmiastowe wyjście z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-204">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="8cd29-205">Dowolna liczba instrukcji `Exit Property` i `Return` może występować w dowolnym miejscu procedury i można mieszać instrukcje `Exit Property` i `Return`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-205">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>

- <span data-ttu-id="8cd29-206">**Wartość zwracana.**</span><span class="sxs-lookup"><span data-stu-id="8cd29-206">**Return Value.**</span></span> <span data-ttu-id="8cd29-207">Aby zwrócić wartość z procedury `Get`, można przypisać wartość do nazwy właściwości lub włączyć ją w instrukcji `Return`.</span><span class="sxs-lookup"><span data-stu-id="8cd29-207">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="8cd29-208">Poniższy przykład przypisuje wartość zwracaną do nazwy właściwości `quoteForTheDay` a następnie używa instrukcji `Exit Property` do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="8cd29-208">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]

  <span data-ttu-id="8cd29-209">Jeśli używasz `Exit Property` bez przypisywania wartości do `name`, procedura `Get` zwróci wartość domyślną dla typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="8cd29-209">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>

  <span data-ttu-id="8cd29-210">Instrukcja `Return` w tym samym czasie przypisuje `Get`ą wartość procedury i kończy procedurę.</span><span class="sxs-lookup"><span data-stu-id="8cd29-210">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="8cd29-211">Poniższy przykład pokazuje.</span><span class="sxs-lookup"><span data-stu-id="8cd29-211">The following example shows this.</span></span>

  [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]

  [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]

## <a name="example"></a><span data-ttu-id="8cd29-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="8cd29-212">Example</span></span>

<span data-ttu-id="8cd29-213">Poniższy przykład deklaruje właściwość w klasie.</span><span class="sxs-lookup"><span data-stu-id="8cd29-213">The following example declares a property in a class.</span></span>

[!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="8cd29-214">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8cd29-214">See also</span></span>

- [<span data-ttu-id="8cd29-215">Właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="8cd29-215">Auto-Implemented Properties</span></span>](../../programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="8cd29-216">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="8cd29-216">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="8cd29-217">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8cd29-217">Get Statement</span></span>](get-statement.md)
- [<span data-ttu-id="8cd29-218">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="8cd29-218">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="8cd29-219">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="8cd29-219">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="8cd29-220">Default</span><span class="sxs-lookup"><span data-stu-id="8cd29-220">Default</span></span>](../modifiers/default.md)
