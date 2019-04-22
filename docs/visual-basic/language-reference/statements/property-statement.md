---
title: Property — instrukcja (Visual Basic)
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
ms.openlocfilehash: 7b2d388cbcd1995178adf4102520ecaa1c9b1889
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814193"
---
# <a name="property-statement"></a><span data-ttu-id="5ef0c-102">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="5ef0c-102">Property Statement</span></span>
<span data-ttu-id="5ef0c-103">Deklaruje nazwę właściwości i procedury właściwości używane do przechowywania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ef0c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5ef0c-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="5ef0c-105">Części</span><span class="sxs-lookup"><span data-stu-id="5ef0c-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="5ef0c-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-106">Optional.</span></span> <span data-ttu-id="5ef0c-107">Lista atrybutów, które są stosowane do tej właściwości lub `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="5ef0c-108">Zobacz temat [Lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="5ef0c-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-109">Optional.</span></span> <span data-ttu-id="5ef0c-110">Określa, że ta właściwość jest właściwością domyślną dla klasy lub struktury, na którym jest zdefiniowana.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="5ef0c-111">Domyślne właściwości muszą akceptować parametry można ustawić i pobrać bez określenia nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="5ef0c-112">Jeśli zadeklarować właściwości jako `Default`, nie można użyć `Private` na właściwość lub jednej z jego procedur właściwość.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="5ef0c-113">Opcjonalnie na `Property` instrukcji i co najwyżej jeden z `Get` i `Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="5ef0c-114">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5ef0c-115">Public</span><span class="sxs-lookup"><span data-stu-id="5ef0c-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="5ef0c-116">Protected</span><span class="sxs-lookup"><span data-stu-id="5ef0c-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="5ef0c-117">Friend</span><span class="sxs-lookup"><span data-stu-id="5ef0c-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="5ef0c-118">Private</span><span class="sxs-lookup"><span data-stu-id="5ef0c-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="5ef0c-119">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5ef0c-119">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md) 

    - [<span data-ttu-id="5ef0c-120">Private Protected</span><span class="sxs-lookup"><span data-stu-id="5ef0c-120">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="5ef0c-121">Zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-121">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="5ef0c-122">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-122">Optional.</span></span> <span data-ttu-id="5ef0c-123">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-123">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="5ef0c-124">Overloads</span><span class="sxs-lookup"><span data-stu-id="5ef0c-124">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="5ef0c-125">Overrides</span><span class="sxs-lookup"><span data-stu-id="5ef0c-125">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="5ef0c-126">Overridable</span><span class="sxs-lookup"><span data-stu-id="5ef0c-126">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="5ef0c-127">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="5ef0c-127">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="5ef0c-128">MustOverride</span><span class="sxs-lookup"><span data-stu-id="5ef0c-128">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="5ef0c-129">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-129">Optional.</span></span> <span data-ttu-id="5ef0c-130">Zobacz [udostępnione](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-130">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="5ef0c-131">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-131">Optional.</span></span> <span data-ttu-id="5ef0c-132">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-132">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="5ef0c-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-133">Optional.</span></span> <span data-ttu-id="5ef0c-134">Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-134">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="5ef0c-135">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-135">Optional.</span></span> <span data-ttu-id="5ef0c-136">Zobacz [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-136">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="5ef0c-137">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-137">Optional.</span></span> <span data-ttu-id="5ef0c-138">Zobacz [iteratora](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-138">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="5ef0c-139">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-139">Required.</span></span> <span data-ttu-id="5ef0c-140">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-140">Name of the property.</span></span> <span data-ttu-id="5ef0c-141">Zobacz [Zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-141">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="5ef0c-142">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-142">Optional.</span></span> <span data-ttu-id="5ef0c-143">Lista reprezentującą parametry tej właściwości i możliwe dodatkowe parametry nazwy zmiennych lokalnych `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-143">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="5ef0c-144">Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-144">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="5ef0c-145">Jeśli wymagane `Option Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-145">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="5ef0c-146">Typ danych wartości zwracanej przez tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-146">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="5ef0c-147">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-147">Optional.</span></span> <span data-ttu-id="5ef0c-148">Wskazuje, że ta właściwość implementuje jedną lub więcej właściwości, każdy z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierający tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-148">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="5ef0c-149">Zobacz [Implements, instrukcja](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-149">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="5ef0c-150">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-150">Required if `Implements` is supplied.</span></span> <span data-ttu-id="5ef0c-151">Lista właściwości, które są zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-151">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="5ef0c-152">Każdy `implementedproperty` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="5ef0c-152">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="5ef0c-153">Część</span><span class="sxs-lookup"><span data-stu-id="5ef0c-153">Part</span></span>|<span data-ttu-id="5ef0c-154">Opis</span><span class="sxs-lookup"><span data-stu-id="5ef0c-154">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="5ef0c-155">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-155">Required.</span></span> <span data-ttu-id="5ef0c-156">Nazwa interfejsu implementowany przez tę właściwość zawierający klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-156">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="5ef0c-157">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-157">Required.</span></span> <span data-ttu-id="5ef0c-158">Nazwa, przez którą właściwość jest zdefiniowana w `interface`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-158">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="5ef0c-159">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-159">Optional.</span></span> <span data-ttu-id="5ef0c-160">Wymagane, jeśli właściwość jest oznaczona `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-160">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="5ef0c-161">Uruchamia `Get` procedury właściwość, która służy do zwracania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-161">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="5ef0c-162">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-162">Optional.</span></span> <span data-ttu-id="5ef0c-163">Blok instrukcji do uruchomienia w ramach `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-163">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="5ef0c-164">Kończy `Get` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-164">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="5ef0c-165">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-165">Optional.</span></span> <span data-ttu-id="5ef0c-166">Wymagane, jeśli właściwość jest oznaczona `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-166">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="5ef0c-167">Uruchamia `Set` procedury właściwości, który jest używany do przechowywania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-167">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="5ef0c-168">Kończy `Set` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-168">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="5ef0c-169">Kończy definicję tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-169">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ef0c-170">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5ef0c-170">Remarks</span></span>  
 <span data-ttu-id="5ef0c-171">`Property` Instrukcji wprowadza deklaracja właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-171">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="5ef0c-172">Właściwość może mieć `Get` (tylko odczyt), procedury `Set` procedury (tylko do zapisu) lub obu (odczyt zapis).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-172">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="5ef0c-173">Możesz pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-173">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="5ef0c-174">Aby uzyskać więcej informacji, zobacz [implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-174">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="5ef0c-175">Możesz użyć `Property` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-175">You can use `Property` only at class level.</span></span> <span data-ttu-id="5ef0c-176">Oznacza to, że *kontekst deklaracji* dla właściwości muszą być klasy, struktury, modułu lub interfejsu, a nie może być plik źródłowy, przestrzeń nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-176">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="5ef0c-177">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-177">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="5ef0c-178">Domyślnie właściwości używają dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-178">By default, properties use public access.</span></span> <span data-ttu-id="5ef0c-179">Możesz dostosować poziom dostępu do właściwości przy użyciu modyfikatora dostępu na `Property` instrukcji, a opcjonalnie dostosować jeden z jego właściwości procedury bardziej restrykcyjny poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-179">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="5ef0c-180">Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-180">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="5ef0c-181">Jeśli parametr nie zostanie podana `Set`, zintegrowanego środowiska programistycznego (IDE) korzysta z niejawny parametr o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-181">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="5ef0c-182">Ten parametr zawiera wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-182">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="5ef0c-183">Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatne i przywrócić go zawsze wtedy, gdy `Get` procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-183">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="5ef0c-184">reguły</span><span class="sxs-lookup"><span data-stu-id="5ef0c-184">Rules</span></span>  
  
-   <span data-ttu-id="5ef0c-185">**Mieszanymi poziomami dostępu.**</span><span class="sxs-lookup"><span data-stu-id="5ef0c-185">**Mixed Access Levels.**</span></span> <span data-ttu-id="5ef0c-186">Jeśli zamierzasz zdefiniować właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu do różnych dla dowolnego `Get` lub `Set` procedury, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-186">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="5ef0c-187">Jeśli to zrobisz, procedura poziom dostępu musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-187">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="5ef0c-188">Na przykład, jeśli właściwość jest zadeklarowana `Friend`, można zadeklarować `Set` procedury `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-188">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="5ef0c-189">Jeśli definiujesz `ReadOnly` lub `WriteOnly` właściwość, procedura pojedynczej właściwości (`Get` lub `Set`odpowiednio) reprezentuje wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-189">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="5ef0c-190">Nie można zadeklarować na poziom dostępu innej procedury, ponieważ, ustawić dwa poziomy dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-190">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="5ef0c-191">**Typ zwracany.**</span><span class="sxs-lookup"><span data-stu-id="5ef0c-191">**Return Type.**</span></span> <span data-ttu-id="5ef0c-192">`Property` Instrukcji można zadeklarować typ danych zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-192">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="5ef0c-193">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-193">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="5ef0c-194">Jeśli nie określisz `returntype`, zwraca właściwości `Object`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-194">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="5ef0c-195">**Implementacja.**</span><span class="sxs-lookup"><span data-stu-id="5ef0c-195">**Implementation.**</span></span> <span data-ttu-id="5ef0c-196">Jeśli ta właściwość używa `Implements` — słowo kluczowe, zawierający klasy lub struktury, musi mieć `Implements` instrukcji natychmiast po jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-196">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="5ef0c-197">`Implements` Instrukcja musi zawierać każdy interfejs określony w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-197">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="5ef0c-198">Jednak nazwy za pomocą którego interfejs definiuje `Property` (w `definedname`) musi być taka sama jak nazwa tej właściwości (w `name`).</span><span class="sxs-lookup"><span data-stu-id="5ef0c-198">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="5ef0c-199">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="5ef0c-199">Behavior</span></span>  
  
-   <span data-ttu-id="5ef0c-200">**Zwracanie z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="5ef0c-200">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="5ef0c-201">Gdy `Get` lub `Set` procedury zwraca do kodu wywołującego, wykonywanie jest kontynuowane przy użyciu instrukcji następującej po instrukcji, które je wywołało.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-201">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="5ef0c-202">`Exit Property` i `Return` instrukcji powodują natychmiastowego wyjścia z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-202">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="5ef0c-203">Dowolną liczbę `Exit Property` i `Return` instrukcji może występować w dowolnym miejscu w ramach procedury i możesz mieszać `Exit Property` i `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-203">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="5ef0c-204">**Zwraca wartość.**</span><span class="sxs-lookup"><span data-stu-id="5ef0c-204">**Return Value.**</span></span> <span data-ttu-id="5ef0c-205">Aby zwrócić wartość z zakresu od `Get` procedury, można przypisać wartości do danej nazwy właściwości lub uwzględnić go w `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-205">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="5ef0c-206">Poniższy przykład przypisuje wartość zwracaną do danej nazwy właściwości `quoteForTheDay` , a następnie używa `Exit Property` instrukcji, aby zwrócić.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-206">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     <span data-ttu-id="5ef0c-207">Jeśli używasz `Exit Property` bez przypisywania wartości do `name`, `Get` procedura zwraca wartość domyślna dla typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="5ef0c-208">`Return` Przypisuje instrukcji w tym samym czasie `Get` procedury zwracać wartości i kończy procedurę.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="5ef0c-209">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-209">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="5ef0c-210">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ef0c-210">Example</span></span>  
 <span data-ttu-id="5ef0c-211">Poniższy przykład deklaruje właściwości w klasie.</span><span class="sxs-lookup"><span data-stu-id="5ef0c-211">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="5ef0c-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5ef0c-212">See also</span></span>

- [<span data-ttu-id="5ef0c-213">Właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="5ef0c-213">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)
- [<span data-ttu-id="5ef0c-214">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="5ef0c-214">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="5ef0c-215">Get, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5ef0c-215">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="5ef0c-216">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5ef0c-216">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
- [<span data-ttu-id="5ef0c-217">Lista parametrów</span><span class="sxs-lookup"><span data-stu-id="5ef0c-217">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)
- [<span data-ttu-id="5ef0c-218">Default</span><span class="sxs-lookup"><span data-stu-id="5ef0c-218">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
