---
title: Enum — Instrukcja (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
ms.openlocfilehash: fa97a374d4570e014222bf44844271b3394453da
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830074"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="faf81-102">Enum — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="faf81-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="faf81-103">Deklaruje wyliczenie i definiuje wartości jego członków.</span><span class="sxs-lookup"><span data-stu-id="faf81-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="faf81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="faf81-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="faf81-105">Części</span><span class="sxs-lookup"><span data-stu-id="faf81-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="faf81-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="faf81-106">Optional.</span></span> <span data-ttu-id="faf81-107">Lista atrybutów, które są stosowane do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="faf81-108">Należy ująć [listę atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="faf81-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="faf81-109"><xref:System.FlagsAttribute> Atrybut wskazuje, że wartość instancja wyliczenia może zawierać wiele elementów członkowskich wyliczenia i że każdy element członkowski reprezentuje pole bitowe wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="faf81-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="faf81-110">Optional.</span></span> <span data-ttu-id="faf81-111">Określa, jaki kod może uzyskać dostęp do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="faf81-112">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="faf81-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="faf81-113">Public</span><span class="sxs-lookup"><span data-stu-id="faf81-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="faf81-114">Protected</span><span class="sxs-lookup"><span data-stu-id="faf81-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="faf81-115">Friend</span><span class="sxs-lookup"><span data-stu-id="faf81-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="faf81-116">Private</span><span class="sxs-lookup"><span data-stu-id="faf81-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="faf81-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="faf81-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="faf81-118">Private Protected</span><span class="sxs-lookup"><span data-stu-id="faf81-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="faf81-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="faf81-119">Optional.</span></span> <span data-ttu-id="faf81-120">Określa, że to wyliczenie programistyczny ponownie deklaruje i ukrywa o identycznej nazwie elementu programistycznego lub zestaw przeciążonych elementów w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="faf81-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="faf81-121">Można określić [cieni](../../../visual-basic/language-reference/modifiers/shadows.md) tylko w przypadku samego wyliczenia, a nie na jedną z jej członków.</span><span class="sxs-lookup"><span data-stu-id="faf81-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="faf81-122">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="faf81-122">Required.</span></span> <span data-ttu-id="faf81-123">Nazwa wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-123">Name of the enumeration.</span></span> <span data-ttu-id="faf81-124">Informacje na temat prawidłowych nazw można zobaczyć [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="faf81-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="faf81-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="faf81-125">Optional.</span></span> <span data-ttu-id="faf81-126">Typ danych wyliczenie i jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="faf81-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="faf81-127">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="faf81-127">Required.</span></span> <span data-ttu-id="faf81-128">Lista stałe element członkowski został zadeklarowany w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="faf81-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="faf81-129">Wiele elementów członkowskich pojawiają się na poszczególnych źródła wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="faf81-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="faf81-130">Każdy `member` ma następujące składni i części: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="faf81-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="faf81-131">Część</span><span class="sxs-lookup"><span data-stu-id="faf81-131">Part</span></span>|<span data-ttu-id="faf81-132">Opis</span><span class="sxs-lookup"><span data-stu-id="faf81-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="faf81-133">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="faf81-133">Required.</span></span> <span data-ttu-id="faf81-134">Nazwa tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="faf81-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="faf81-135">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="faf81-135">Optional.</span></span> <span data-ttu-id="faf81-136">Wyrażenie jest obliczane w czasie kompilacji i przypisane do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="faf81-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="faf81-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="faf81-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="faf81-138">Kończy blok `Enum`.</span><span class="sxs-lookup"><span data-stu-id="faf81-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="faf81-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="faf81-139">Remarks</span></span>  
 <span data-ttu-id="faf81-140">Jeśli masz zestaw niezmiennych wartości, które są logicznie powiązane ze sobą, można zdefiniować je ze sobą w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="faf81-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="faf81-141">Dzięki temu nazw opisowych dla wyliczenia i jej elementów członkowskich, które są łatwiejsze do zapamiętania niż ich wartości.</span><span class="sxs-lookup"><span data-stu-id="faf81-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="faf81-142">Elementy członkowskie wyliczenia można następnie użyć w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="faf81-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="faf81-143">Zalety używania wyliczenia obejmują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="faf81-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="faf81-144">Zmniejsza błędy spowodowane Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="faf81-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="faf81-145">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="faf81-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="faf81-146">Sprawia, że kod łatwiejsza do odczytania, co oznacza, że jest mniej prawdopodobne, że błędy będą wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="faf81-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="faf81-147">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="faf81-147">Ensures forward compatibility.</span></span> <span data-ttu-id="faf81-148">Jeśli używasz wyliczenia, kod jest mniej prawdopodobne zakończyć się niepowodzeniem, jeśli w przyszłości ktoś zmienia wartości odpowiadające nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="faf81-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="faf81-149">Wyliczenie ma nazwę odpowiedniego typu danych i zestaw elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="faf81-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="faf81-150">Każdy element członkowski reprezentuje stałą.</span><span class="sxs-lookup"><span data-stu-id="faf81-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="faf81-151">To wyliczenie zadeklarowane na poziomie klasy, struktury, modułu lub interfejsu, poza dowolnej procedury *elementu członkowskiego wyliczenia*.</span><span class="sxs-lookup"><span data-stu-id="faf81-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="faf81-152">Jest on członkiem klasy, struktury, modułu lub interfejs, który deklaruje ją.</span><span class="sxs-lookup"><span data-stu-id="faf81-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="faf81-153">Element członkowski wyliczenia jest możliwy z dowolnego miejsca w obrębie klasy, struktury, modułu lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="faf81-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="faf81-154">Kod poza klasą, struktury lub modułu musi kwalifikować nazwy wyliczenia elementu członkowskiego z nazwą tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="faf81-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="faf81-155">Aby uniknąć konieczności używać w pełni kwalifikowanych nazw, dodając [Importy](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji do pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="faf81-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="faf81-156">Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasy, struktury, modułu lub interfejsu, jest członkiem obszaru nazw, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="faf81-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="faf81-157">*Kontekst deklaracji* dla wyliczenia musi być plikiem źródłowym, przestrzeń nazw, klasy, struktury, modułu lub interfejsu, a nie może być procedurą.</span><span class="sxs-lookup"><span data-stu-id="faf81-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="faf81-158">Aby uzyskać więcej informacji, zobacz [Kontekst deklaracji i domyślne poziomy dostępu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="faf81-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="faf81-159">Atrybuty można zastosować do wyliczenia jako całości, ale nie do swoich elementów członkowskich indywidualnie.</span><span class="sxs-lookup"><span data-stu-id="faf81-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="faf81-160">Atrybut przyczynia się informacji metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="faf81-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="faf81-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="faf81-161">Data Type</span></span>  
 <span data-ttu-id="faf81-162">`Enum` Instrukcji można zadeklarować wyliczenie typu danych.</span><span class="sxs-lookup"><span data-stu-id="faf81-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="faf81-163">Każdy element członkowski ma typ danych wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="faf81-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="faf81-164">Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort`.</span><span class="sxs-lookup"><span data-stu-id="faf81-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="faf81-165">Jeśli nie określisz `datatype` wyliczenia, każdy element członkowski ma typ danych jego `initializer`.</span><span class="sxs-lookup"><span data-stu-id="faf81-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="faf81-166">Jeśli określisz zarówno `datatype` i `initializer`, typ danych `initializer` musi być konwertowany na `datatype`.</span><span class="sxs-lookup"><span data-stu-id="faf81-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="faf81-167">Jeśli żadna `datatype` ani `initializer` jest obecny, wartość domyślna to typ danych `Integer`.</span><span class="sxs-lookup"><span data-stu-id="faf81-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="faf81-168">Inicjowanie elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="faf81-168">Initializing Members</span></span>  
 <span data-ttu-id="faf81-169">`Enum` Instrukcji można zainicjować zawartość wybranych członków w `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="faf81-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="faf81-170">Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia można przypisać do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="faf81-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="faf81-171">Jeśli nie określisz `initializer` dla elementu członkowskiego, Visual Basic inicjuje go do zera (jeśli jest on pierwszy `member` w `memberlist`), lub wartość większą o jeden niż bezpośrednio poprzedzający `member`.</span><span class="sxs-lookup"><span data-stu-id="faf81-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="faf81-172">Wyrażenie podane w każdym `initializer` może być dowolną kombinacją literały, inne stałe, które są już zdefiniowane i elementów członkowskich wyliczenia, które są już zdefiniowane, łącznie z poprzednim elementem tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="faf81-173">Za pomocą operatorów arytmetycznych i logicznych połączyć takie elementy.</span><span class="sxs-lookup"><span data-stu-id="faf81-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="faf81-174">Nie można używać zmiennych lub funkcji w `initializer`.</span><span class="sxs-lookup"><span data-stu-id="faf81-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="faf81-175">Jednak można użyć słowa kluczowe konwersji takich jak `CByte` i `CShort`.</span><span class="sxs-lookup"><span data-stu-id="faf81-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="faf81-176">Można również użyć `AscW` Jeśli wywołasz ze stałą `String` lub `Char` argumentu, ponieważ mogą być obliczane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="faf81-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="faf81-177">Wyliczenia nie może mieć różne wartości zmiennoprzecinkowe.</span><span class="sxs-lookup"><span data-stu-id="faf81-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="faf81-178">Jeśli członek nie zostanie przypisana wartość zmiennoprzecinkowa i `Option Strict` jest włączona, występuje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="faf81-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="faf81-179">Jeśli `Option Strict` jest wyłączone, wartość jest automatycznie konwertowany do `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="faf81-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="faf81-180">Jeśli wartość elementu członkowskiego przekracza dopuszczalny zakres dla odpowiedniego typu danych lub zainicjować dowolnego elementu członkowskiego na wartość maksymalną dozwoloną przez odpowiedniego typu danych, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="faf81-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="faf81-181">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="faf81-181">Modifiers</span></span>  
 <span data-ttu-id="faf81-182">Klasy, struktury, moduł i domyślnie wyliczenia elementu członkowskiego interfejsu publicznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="faf81-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="faf81-183">Poziomy dostępu można zmienić za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="faf81-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="faf81-184">Namespace domyślnie wyliczenia Członkowskiego dostęp zaprzyjaźniony.</span><span class="sxs-lookup"><span data-stu-id="faf81-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="faf81-185">Można dostosować ich poziomy dostępu do publicznego, ale nie do prywatnych lub chronionych.</span><span class="sxs-lookup"><span data-stu-id="faf81-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="faf81-186">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="faf81-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="faf81-187">Wszystkie elementy członkowskie wyliczenia mają dostęp publiczny i nie można użyć dowolnego modyfikatory dostępu na nich.</span><span class="sxs-lookup"><span data-stu-id="faf81-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="faf81-188">Jednak jeśli samego wyliczenia ma bardziej ograniczony poziom dostępu, wyliczenie określony poziom dostępu ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="faf81-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="faf81-189">Domyślnie wszystkie wyliczenia są typy i ich pól są stałymi.</span><span class="sxs-lookup"><span data-stu-id="faf81-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="faf81-190">W związku z tym `Shared`, `Static`, i `ReadOnly` słów kluczowych nie można użyć podczas deklarowania wyliczania lub jego składowych.</span><span class="sxs-lookup"><span data-stu-id="faf81-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="faf81-191">Przypisywanie wielu wartości</span><span class="sxs-lookup"><span data-stu-id="faf81-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="faf81-192">Wyliczenia zazwyczaj reprezentują wartości wzajemnie się wykluczają.</span><span class="sxs-lookup"><span data-stu-id="faf81-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="faf81-193">Jeśli dołączysz <xref:System.FlagsAttribute> atrybutu w `Enum` deklaracji, można zamiast tego przypisać wielu wartości do wystąpienia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="faf81-194"><xref:System.FlagsAttribute> Atrybut określa, że wyliczenie być traktowane jako pole bitowe, czyli zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="faf81-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="faf81-195">Są to tak zwane *bitowe* wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="faf81-196">Podczas deklarowania wyliczania, przy użyciu <xref:System.FlagsAttribute> atrybutu, zalecamy użycie potęgi 2, który jest, 1, 2, 4, 8, 16 i tak dalej dla wartości.</span><span class="sxs-lookup"><span data-stu-id="faf81-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="faf81-197">Zalecamy również, czy można "None" nazwy elementu członkowskiego, w których wartość jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="faf81-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="faf81-198">Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="faf81-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faf81-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-199">Example</span></span>  
 <span data-ttu-id="faf81-200">Poniższy przykład pokazuje, jak używać `Enum` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="faf81-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="faf81-201">Należy zauważyć, że składowa jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.</span><span class="sxs-lookup"><span data-stu-id="faf81-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="faf81-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-202">Example</span></span>  
 <span data-ttu-id="faf81-203">W poniższym przykładzie metody znajduje się poza `Egg` klasy.</span><span class="sxs-lookup"><span data-stu-id="faf81-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="faf81-204">W związku z tym `EggSizeEnum` jest w pełni kwalifikowany jako `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="faf81-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]  
  
## <a name="example"></a><span data-ttu-id="faf81-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-205">Example</span></span>  
 <span data-ttu-id="faf81-206">W poniższym przykładzie użyto `Enum` instrukcji, aby zdefiniować zestaw powiązanych nazwanych stałych.</span><span class="sxs-lookup"><span data-stu-id="faf81-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="faf81-207">W tym przypadku wartości są kolory, których można projektować formularzach wprowadzania danych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="faf81-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]  
  
## <a name="example"></a><span data-ttu-id="faf81-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-208">Example</span></span>  
 <span data-ttu-id="faf81-209">Poniższy przykład przedstawia wartości, które zawierają zarówno dodatnie i ujemne liczby.</span><span class="sxs-lookup"><span data-stu-id="faf81-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]  
  
## <a name="example"></a><span data-ttu-id="faf81-210">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-210">Example</span></span>  
 <span data-ttu-id="faf81-211">W poniższym przykładzie `As` klauzuli służy do określania `datatype` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="faf81-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-212">Example</span></span>  
 <span data-ttu-id="faf81-213">Poniższy przykład przedstawia sposób użycia bitowego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="faf81-214">Wiele wartości można przypisać do wystąpienia bitowe wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="faf81-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="faf81-215">`Enum` Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że wyliczenia mogą być traktowane jako zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="faf81-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]  
  
## <a name="example"></a><span data-ttu-id="faf81-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="faf81-216">Example</span></span>  
 <span data-ttu-id="faf81-217">Poniższy przykład wykonuje iterację za pomocą wyliczania.</span><span class="sxs-lookup"><span data-stu-id="faf81-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="faf81-218">Używa ona <xref:System.Enum.GetNames%2A> metodę, aby pobrać tablicę nazwy elementów członkowskich z wyliczenia i <xref:System.Enum.GetValues%2A> do pobrania tablicy wartości elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="faf81-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]  
  
## <a name="see-also"></a><span data-ttu-id="faf81-219">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="faf81-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="faf81-220">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="faf81-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="faf81-221">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="faf81-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)
- [<span data-ttu-id="faf81-222">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="faf81-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="faf81-223">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="faf81-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="faf81-224">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="faf81-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
