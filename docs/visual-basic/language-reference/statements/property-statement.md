---
title: "Property — Instrukcja"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af4666ecb059f141480be2295055644537819293
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="property-statement"></a><span data-ttu-id="df845-102">Property — Instrukcja</span><span class="sxs-lookup"><span data-stu-id="df845-102">Property Statement</span></span>
<span data-ttu-id="df845-103">Deklaruje nazwę właściwości i procedury właściwości używane do przechowywania i pobierania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df845-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df845-104">Syntax</span></span>  
  
```  
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
  
## <a name="parts"></a><span data-ttu-id="df845-105">Części</span><span class="sxs-lookup"><span data-stu-id="df845-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="df845-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-106">Optional.</span></span> <span data-ttu-id="df845-107">Lista atrybutów, które mają zastosowanie do tej właściwości lub `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="df845-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="df845-108">Zobacz [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="df845-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="df845-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-109">Optional.</span></span> <span data-ttu-id="df845-110">Określa, że ta właściwość jest właściwością domyślną dla klasy lub struktury, na którym jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="df845-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="df845-111">Właściwości domyślne musi akceptować parametry i można ustawić i pobrać bez określania nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="df845-112">Jeśli można zadeklarować właściwości jako `Default`, nie można użyć `Private` na właściwość lub jedną z procedur jego właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="df845-113">Opcjonalnie na `Property` instrukcji i co najwyżej jeden z `Get` i `Set` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="df845-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="df845-114">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="df845-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="df845-115">Publiczna</span><span class="sxs-lookup"><span data-stu-id="df845-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="df845-116">Chronione</span><span class="sxs-lookup"><span data-stu-id="df845-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="df845-117">Friend</span><span class="sxs-lookup"><span data-stu-id="df845-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="df845-118">Prywatne</span><span class="sxs-lookup"><span data-stu-id="df845-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="df845-119">Zobacz [poziomy w języku Visual Basic dostępu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="df845-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="df845-120">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-120">Optional.</span></span> <span data-ttu-id="df845-121">Może to być jedna z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="df845-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="df845-122">Przeciążenia</span><span class="sxs-lookup"><span data-stu-id="df845-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="df845-123">Zastąpienia</span><span class="sxs-lookup"><span data-stu-id="df845-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="df845-124">Możliwym do zastąpienia</span><span class="sxs-lookup"><span data-stu-id="df845-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="df845-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="df845-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="df845-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="df845-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="df845-127">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-127">Optional.</span></span> <span data-ttu-id="df845-128">Zobacz [udostępnionych](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="df845-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="df845-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-129">Optional.</span></span> <span data-ttu-id="df845-130">Zobacz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="df845-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="df845-131">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-131">Optional.</span></span> <span data-ttu-id="df845-132">Zobacz [tylko do odczytu](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="df845-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="df845-133">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-133">Optional.</span></span> <span data-ttu-id="df845-134">Zobacz [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="df845-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="df845-135">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-135">Optional.</span></span> <span data-ttu-id="df845-136">Zobacz [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="df845-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="df845-137">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="df845-137">Required.</span></span> <span data-ttu-id="df845-138">Nazwa właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-138">Name of the property.</span></span> <span data-ttu-id="df845-139">Zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="df845-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="df845-140">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-140">Optional.</span></span> <span data-ttu-id="df845-141">Lista nazwy zmiennych lokalnych reprezentujący parametry tej właściwości i możliwe dodatkowe parametry `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="df845-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="df845-142">Zobacz [listy parametrów](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="df845-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="df845-143">Jeśli wymagane `Option``Strict` jest `On`.</span><span class="sxs-lookup"><span data-stu-id="df845-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="df845-144">Typ danych wartości zwracanej przez tę właściwość.</span><span class="sxs-lookup"><span data-stu-id="df845-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="df845-145">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-145">Optional.</span></span> <span data-ttu-id="df845-146">Wskazuje, że ta właściwość implementuje jednej lub więcej właściwości, każdą z nich zdefiniowane w interfejsie zaimplementowany przez klasę lub strukturę zawierającego tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="df845-147">Zobacz [implementuje instrukcji](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="df845-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="df845-148">Jeśli wymagane `Implements` podano.</span><span class="sxs-lookup"><span data-stu-id="df845-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="df845-149">Lista właściwości implementowana.</span><span class="sxs-lookup"><span data-stu-id="df845-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="df845-150">Każdy `implementedproperty` ma następujące składni i części:</span><span class="sxs-lookup"><span data-stu-id="df845-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="df845-151">Część</span><span class="sxs-lookup"><span data-stu-id="df845-151">Part</span></span>|<span data-ttu-id="df845-152">Opis</span><span class="sxs-lookup"><span data-stu-id="df845-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="df845-153">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="df845-153">Required.</span></span> <span data-ttu-id="df845-154">Nazwa interfejsu implementowanego przez tę właściwość zawierającego klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="df845-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="df845-155">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="df845-155">Required.</span></span> <span data-ttu-id="df845-156">Nazwa, przez którą właściwość jest zdefiniowana w `interface`.</span><span class="sxs-lookup"><span data-stu-id="df845-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="df845-157">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-157">Optional.</span></span> <span data-ttu-id="df845-158">Wymagane, jeśli właściwość jest oznaczona jako `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="df845-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="df845-159">Uruchamia `Get` procedury właściwości, która służy do zwracania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="df845-160">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-160">Optional.</span></span> <span data-ttu-id="df845-161">Blok instrukcji do uruchomienia w ramach `Get` lub `Set` procedury.</span><span class="sxs-lookup"><span data-stu-id="df845-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="df845-162">Kończy `Get` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="df845-163">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="df845-163">Optional.</span></span> <span data-ttu-id="df845-164">Wymagane, jeśli właściwość jest oznaczona jako `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="df845-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="df845-165">Uruchamia `Set` procedury właściwości, która jest używana do przechowywania wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="df845-166">Kończy `Set` procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="df845-167">Kończy definicję tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df845-168">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df845-168">Remarks</span></span>  
 <span data-ttu-id="df845-169">`Property` Instrukcji wprowadzono deklaracji właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="df845-170">Może mieć właściwości `Get` procedury (tylko do odczytu), `Set` procedura (tylko do zapisu) lub obu (odczytu i zapisu).</span><span class="sxs-lookup"><span data-stu-id="df845-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="df845-171">Można pominąć `Get` i `Set` procedury w przypadku przy użyciu automatycznie implementowanych właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="df845-172">Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="df845-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="df845-173">Można użyć `Property` tylko na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="df845-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="df845-174">Oznacza to, że *kontekście deklaracji* właściwość musi być klasy, struktury, modułu lub interfejsu i nie może być plik źródłowy, przestrzeni nazw, procedurę lub blok.</span><span class="sxs-lookup"><span data-stu-id="df845-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="df845-175">Aby uzyskać więcej informacji, zobacz [kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="df845-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="df845-176">Domyślnie właściwości używają dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="df845-176">By default, properties use public access.</span></span> <span data-ttu-id="df845-177">Można dostosować poziom dostępu do właściwości z modyfikatora dostępu w `Property` instrukcji i opcjonalnie można dostosować jedną z procedur jej właściwości na bardziej restrykcyjne poziom dostępu.</span><span class="sxs-lookup"><span data-stu-id="df845-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="df845-178">Visual Basic przekazuje parametr `Set` procedury podczas przypisania właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="df845-179">Jeśli nie podasz parametru `Set`, zintegrowane środowisko programistyczne (IDE) używa niejawnego parametru o nazwie `value`.</span><span class="sxs-lookup"><span data-stu-id="df845-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="df845-180">Ten parametr zawiera wartość do przypisania do właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="df845-181">Zazwyczaj przechowywać tę wartość w zmiennej lokalnej prywatnych i przywrócić go przy każdym `Get` procedura jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="df845-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="df845-182">Reguły</span><span class="sxs-lookup"><span data-stu-id="df845-182">Rules</span></span>  
  
-   <span data-ttu-id="df845-183">**Mieszanymi poziomami dostępu.**</span><span class="sxs-lookup"><span data-stu-id="df845-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="df845-184">Jeśli definiujesz właściwości odczytu / zapisu, można opcjonalnie określić poziom dostępu różnych jednego `Get` lub `Set` procedura, ale nie oba.</span><span class="sxs-lookup"><span data-stu-id="df845-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="df845-185">Jeśli to zrobisz, poziom dostępu do procedury musi być bardziej restrykcyjny niż poziom dostępu do właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="df845-186">Na przykład, jeśli właściwość jest zadeklarowany jako `Friend`, mogą zadeklarować `Set` procedury `Private`, ale nie `Public`.</span><span class="sxs-lookup"><span data-stu-id="df845-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="df845-187">Jeśli definiujesz `ReadOnly` lub `WriteOnly` właściwości, procedura jednej właściwości (`Get` lub `Set`odpowiednio) reprezentuje wszystkie właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="df845-188">Nie można zadeklarować poziom dostępu różnych dla takiej procedury, ponieważ który ustawiał dwa poziomy dostępu dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="df845-189">**Typ zwracany.**</span><span class="sxs-lookup"><span data-stu-id="df845-189">**Return Type.**</span></span> <span data-ttu-id="df845-190">`Property` Instrukcji można zadeklarować typu danych zwracanych wartości.</span><span class="sxs-lookup"><span data-stu-id="df845-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="df845-191">Można określić dowolny typ danych lub nazwa wyliczenia, struktury, klasy lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="df845-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="df845-192">Jeśli nie określisz `returntype`, zwraca właściwość `Object`.</span><span class="sxs-lookup"><span data-stu-id="df845-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="df845-193">**Implementacja.**</span><span class="sxs-lookup"><span data-stu-id="df845-193">**Implementation.**</span></span> <span data-ttu-id="df845-194">Jeśli ta właściwość używa `Implements` — słowo kluczowe, zawierające klasy lub struktury musi mieć `Implements` instrukcji bezpośrednio po jego `Class` lub `Structure` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df845-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="df845-195">`Implements` Instrukcja musi zawierać każdego interfejsu w `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="df845-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="df845-196">Jednak nazwy za pomocą którego definiuje interfejs `Property` (w `definedname`) musi być taka sama jak nazwa tej właściwości (w `name`).</span><span class="sxs-lookup"><span data-stu-id="df845-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="df845-197">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="df845-197">Behavior</span></span>  
  
-   <span data-ttu-id="df845-198">**Zwracanie z procedury właściwości.**</span><span class="sxs-lookup"><span data-stu-id="df845-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="df845-199">Gdy `Get` lub `Set` procedura zwraca do kodu wywołującego, wykonanie będzie kontynuowane przy użyciu instrukcji następującej po instrukcji, która wywołała go.</span><span class="sxs-lookup"><span data-stu-id="df845-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="df845-200">`Exit Property` i `Return` instrukcje spowodować natychmiastowe wyjścia z procedury właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="df845-201">Dowolną liczbę `Exit Property` i `Return` instrukcje mogą występować w dowolnym miejscu w procedurze, a można mieszać `Exit Property` i `Return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="df845-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="df845-202">**Wartość zwracana.**</span><span class="sxs-lookup"><span data-stu-id="df845-202">**Return Value.**</span></span> <span data-ttu-id="df845-203">Zwraca wartość z `Get` procedury, można przypisać wartości do nazwy właściwości lub dołączyć go w `Return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="df845-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="df845-204">Poniższy przykład przypisuje wartość zwracana do nazwy właściwości `quoteForTheDay` , a następnie używa `Exit Property` instrukcji do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="df845-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="df845-205">Jeśli używasz `Exit Property` bez przypisywanie wartości do `name`, `Get` procedury zwraca wartość domyślna dla typu danych właściwości.</span><span class="sxs-lookup"><span data-stu-id="df845-205">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="df845-206">`Return` Instrukcja w tym samym czasie przypisuje `Get` procedura zwraca wartość i kończy procedurę.</span><span class="sxs-lookup"><span data-stu-id="df845-206">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="df845-207">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="df845-207">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="df845-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="df845-208">Example</span></span>  
 <span data-ttu-id="df845-209">Poniższy przykład deklaruje właściwości w klasie.</span><span class="sxs-lookup"><span data-stu-id="df845-209">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="df845-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df845-210">See Also</span></span>  
 [<span data-ttu-id="df845-211">Właściwości zaimplementowane automatycznie</span><span class="sxs-lookup"><span data-stu-id="df845-211">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="df845-212">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="df845-212">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="df845-213">Get — instrukcja</span><span class="sxs-lookup"><span data-stu-id="df845-213">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="df845-214">Set — instrukcja</span><span class="sxs-lookup"><span data-stu-id="df845-214">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="df845-215">Listy parametrów</span><span class="sxs-lookup"><span data-stu-id="df845-215">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="df845-216">Domyślne</span><span class="sxs-lookup"><span data-stu-id="df845-216">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
