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
ms.openlocfilehash: 7cac4d5bde9ec617a1877a0605dc6dbab67ddf7f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
ms.locfileid: "34234019"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="47eca-102">Enum — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47eca-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="47eca-103">Deklaruje wyliczenie i definiuje wartości jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="47eca-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47eca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47eca-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="47eca-105">Części</span><span class="sxs-lookup"><span data-stu-id="47eca-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="47eca-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47eca-106">Optional.</span></span> <span data-ttu-id="47eca-107">Lista atrybutów, które są stosowane do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="47eca-108">Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="47eca-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="47eca-109"><xref:System.FlagsAttribute> Atrybut wskazuje, że wartości wyliczenia wystąpienia może zawierać wiele elementy członkowskie wyliczenia i że każdy element członkowski reprezentuje pole bitowe wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="47eca-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47eca-110">Optional.</span></span> <span data-ttu-id="47eca-111">Określa, jaki kod mogą uzyskiwać dostęp do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="47eca-112">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="47eca-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="47eca-113">Public</span><span class="sxs-lookup"><span data-stu-id="47eca-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="47eca-114">Protected</span><span class="sxs-lookup"><span data-stu-id="47eca-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="47eca-115">Friend</span><span class="sxs-lookup"><span data-stu-id="47eca-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="47eca-116">Private</span><span class="sxs-lookup"><span data-stu-id="47eca-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    - [<span data-ttu-id="47eca-117">Friend chronionych</span><span class="sxs-lookup"><span data-stu-id="47eca-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)
    
    - [<span data-ttu-id="47eca-118">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="47eca-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

-   `Shadows`  
  
     <span data-ttu-id="47eca-119">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47eca-119">Optional.</span></span> <span data-ttu-id="47eca-120">Określa, że to wyliczenie programistyczny ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="47eca-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="47eca-121">Można określić [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) tylko na wyliczenie samego, nie na żadnym z jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="47eca-121">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="47eca-122">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="47eca-122">Required.</span></span> <span data-ttu-id="47eca-123">Nazwa wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-123">Name of the enumeration.</span></span> <span data-ttu-id="47eca-124">Uzyskać informacji o prawidłowych nazw, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="47eca-124">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="47eca-125">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47eca-125">Optional.</span></span> <span data-ttu-id="47eca-126">Typ danych wyliczenia i wszyscy jej członkowie.</span><span class="sxs-lookup"><span data-stu-id="47eca-126">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="47eca-127">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="47eca-127">Required.</span></span> <span data-ttu-id="47eca-128">Lista stałe element członkowski został zadeklarowany w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="47eca-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="47eca-129">Wiele elementów członkowskich są wyświetlane na poszczególnych źródła wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="47eca-129">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="47eca-130">Każdy `member` ma następujące składni i części: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="47eca-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="47eca-131">Część</span><span class="sxs-lookup"><span data-stu-id="47eca-131">Part</span></span>|<span data-ttu-id="47eca-132">Opis</span><span class="sxs-lookup"><span data-stu-id="47eca-132">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="47eca-133">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="47eca-133">Required.</span></span> <span data-ttu-id="47eca-134">Nazwa tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="47eca-134">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="47eca-135">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="47eca-135">Optional.</span></span> <span data-ttu-id="47eca-136">Wyrażenie, które jest obliczane w czasie kompilacji i przypisane do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="47eca-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="47eca-137">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="47eca-137">`End` `Enum`</span></span>  
  
     <span data-ttu-id="47eca-138">Kończy blok `Enum`.</span><span class="sxs-lookup"><span data-stu-id="47eca-138">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="47eca-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47eca-139">Remarks</span></span>  
 <span data-ttu-id="47eca-140">Jeśli masz zestaw wartości niezmiennych, logicznie powiązanych ze sobą, należy je zdefiniować w razem w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="47eca-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="47eca-141">Zapewnia to znaczące nazwy dla wyliczenia i jej elementów członkowskich, które są łatwiejsze do zapamiętania niż ich wartości.</span><span class="sxs-lookup"><span data-stu-id="47eca-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="47eca-142">Elementy członkowskie wyliczenia można następnie użyć w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="47eca-142">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="47eca-143">Korzyści wynikające ze stosowania wyliczenia są następujące:</span><span class="sxs-lookup"><span data-stu-id="47eca-143">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="47eca-144">Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="47eca-144">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="47eca-145">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="47eca-145">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="47eca-146">Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy zostaną wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="47eca-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="47eca-147">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="47eca-147">Ensures forward compatibility.</span></span> <span data-ttu-id="47eca-148">Jeśli używasz wyliczenia, kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="47eca-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="47eca-149">Wyliczenie ma nazwę, podstawowym typem danych i zestaw elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="47eca-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="47eca-150">Każdy element członkowski reprezentuje stałą.</span><span class="sxs-lookup"><span data-stu-id="47eca-150">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="47eca-151">To wyliczenie zadeklarowane na klasy, struktury, modułu lub poziom interfejsu poza dowolnej procedury *elementu członkowskiego wyliczenia*.</span><span class="sxs-lookup"><span data-stu-id="47eca-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="47eca-152">Jest elementem członkowskim klasy, struktury, modułu lub interfejsu, który deklaruje go.</span><span class="sxs-lookup"><span data-stu-id="47eca-152">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="47eca-153">Element członkowski wyliczenia można uzyskać z dowolnego miejsca w obrębie klasy, struktury, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="47eca-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="47eca-154">Kod poza klasą, strukturą lub modułu muszą nazwy wyliczenia elementu członkowskiego z nazwą tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="47eca-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="47eca-155">Aby uniknąć konieczności używania w pełni kwalifikowane nazwy przez dodanie [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji do pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="47eca-155">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="47eca-156">Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasy, struktury, modułu lub interfejsu, jest członkiem przestrzeni nazw, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="47eca-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="47eca-157">*Kontekście deklaracji* wyliczenia musi być pliku źródłowego, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedury.</span><span class="sxs-lookup"><span data-stu-id="47eca-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="47eca-158">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="47eca-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="47eca-159">Można zastosować atrybutów do wyliczenia jako całość, ale nie do jego elementów członkowskich pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="47eca-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="47eca-160">Atrybut wspiera informacje dotyczące metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="47eca-160">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="47eca-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="47eca-161">Data Type</span></span>  
 <span data-ttu-id="47eca-162">`Enum` Instrukcji można zadeklarować typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="47eca-163">Każdy element członkowski ma typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="47eca-164">Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort`.</span><span class="sxs-lookup"><span data-stu-id="47eca-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="47eca-165">Jeśli nie określisz `datatype` wyliczenia, każdy element członkowski ma typ danych jego `initializer`.</span><span class="sxs-lookup"><span data-stu-id="47eca-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="47eca-166">Jeśli możesz określić ich obu `datatype` i `initializer`, typ danych miary `initializer` musi być możliwe do przekonwertowania na `datatype`.</span><span class="sxs-lookup"><span data-stu-id="47eca-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="47eca-167">Jeśli żadna `datatype` ani `initializer` ma typ danych wartości domyślnych do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="47eca-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="47eca-168">Podczas inicjowania elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="47eca-168">Initializing Members</span></span>  
 <span data-ttu-id="47eca-169">`Enum` Instrukcji można zainicjować zawartość wybranych członków w `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="47eca-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="47eca-170">Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia w można przypisać do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="47eca-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="47eca-171">Jeśli nie określisz `initializer` dla elementu członkowskiego języka Visual Basic inicjowane albo zero (jeśli jest pierwszy `member` w `memberlist`), lub wartość większą o jeden niż bezpośrednio przed `member`.</span><span class="sxs-lookup"><span data-stu-id="47eca-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="47eca-172">Wyrażenie podane w każdym `initializer` może być dowolną kombinacją literały, inne stałe, które zostały już zdefiniowane i elementy członkowskie wyliczenia, które zostały już zdefiniowane, włączając poprzedni element członkowski tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="47eca-173">Operatory arytmetyczne i logiczne umożliwia łączenie takich elementów.</span><span class="sxs-lookup"><span data-stu-id="47eca-173">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="47eca-174">Nie można używać zmiennych lub funkcje w `initializer`.</span><span class="sxs-lookup"><span data-stu-id="47eca-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="47eca-175">Jednak takie jak można użyć słowa kluczowe konwersji `CByte` i `CShort`.</span><span class="sxs-lookup"><span data-stu-id="47eca-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="47eca-176">Można również użyć `AscW` połączeń ze stałą `String` lub `Char` argumentu, ponieważ może zostać oceniony w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="47eca-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="47eca-177">Wyliczenia nie może mieć wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="47eca-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="47eca-178">Jeśli element członkowski jest przypisywana wartość zmiennoprzecinkowa i `Option Strict` ma wartość on, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="47eca-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="47eca-179">Jeśli `Option Strict` jest wyłączony, wartość jest automatycznie konwertowany do `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="47eca-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="47eca-180">Jeśli wartość elementu członkowskiego przekracza dopuszczalny zakres dla odpowiedniego typu danych lub zainicjować członków do maksymalna wartość dozwolona przez podstawowy typ danych, kompilator zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="47eca-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="47eca-181">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="47eca-181">Modifiers</span></span>  
 <span data-ttu-id="47eca-182">Klasy, struktury, moduł i domyślnie wyliczenia elementu członkowskiego interfejsu dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="47eca-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="47eca-183">Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="47eca-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="47eca-184">Namespace elementu członkowskiego wyliczenia domyślną wartość przyjaznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="47eca-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="47eca-185">Można dostosować ich poziomy dostępu publicznego, ale nie prywatne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="47eca-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="47eca-186">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="47eca-186">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="47eca-187">Wszystkie elementy członkowskie wyliczenia mają dostęp publiczny i nie można użyć dowolnego modyfikatorów dostępu na nich.</span><span class="sxs-lookup"><span data-stu-id="47eca-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="47eca-188">Jednak jeśli wyliczenia sam bardziej ograniczony poziom dostępu, wyliczenie określony poziom dostępu ma priorytet.</span><span class="sxs-lookup"><span data-stu-id="47eca-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="47eca-189">Domyślnie wszystkie wyliczenia są typy i ich pola są stałe.</span><span class="sxs-lookup"><span data-stu-id="47eca-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="47eca-190">W związku z tym `Shared`, `Static`, i `ReadOnly` nie można użyć słowa kluczowe przy deklarowaniu wyliczenie lub jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="47eca-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="47eca-191">Przypisywanie wielu wartości</span><span class="sxs-lookup"><span data-stu-id="47eca-191">Assigning Multiple Values</span></span>  
 <span data-ttu-id="47eca-192">Wyliczenia zazwyczaj reprezentują wartości wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="47eca-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="47eca-193">W tym <xref:System.FlagsAttribute> atrybutu w `Enum` deklaracji, zamiast tego do można przypisać wielu wartości wystąpienia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="47eca-194"><xref:System.FlagsAttribute> Atrybut określa, że wyliczenia być traktowane jako pole bitowe, czyli zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="47eca-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="47eca-195">Są one nazywane *bitowe* wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-195">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="47eca-196">Gdy zadeklarować wyliczenia za pomocą <xref:System.FlagsAttribute> atrybutu, firma Microsoft zaleca użycie potęgami liczby 2, który jest, 1, 2, 4, 8, 16 i tak dalej dla wartości.</span><span class="sxs-lookup"><span data-stu-id="47eca-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="47eca-197">Ponadto zaleca się "None" nazwę elementu członkowskiego, którego wartość jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="47eca-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="47eca-198">Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="47eca-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47eca-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-199">Example</span></span>  
 <span data-ttu-id="47eca-200">Poniższy przykład przedstawia użycie `Enum` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="47eca-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="47eca-201">Należy pamiętać, że element członkowski jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.</span><span class="sxs-lookup"><span data-stu-id="47eca-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-202">Example</span></span>  
 <span data-ttu-id="47eca-203">W poniższym przykładzie metody jest poza `Egg` klasy.</span><span class="sxs-lookup"><span data-stu-id="47eca-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="47eca-204">W związku z tym `EggSizeEnum` jest w pełni kwalifikowany jako `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="47eca-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-205">Example</span></span>  
 <span data-ttu-id="47eca-206">W poniższym przykładzie użyto `Enum` instrukcję, aby zdefiniować powiązany zestaw o nazwie wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="47eca-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="47eca-207">W tym przypadku wartości są kolorów, które można wybrać do projektowania formularzy zapis danych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="47eca-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-208">Example</span></span>  
 <span data-ttu-id="47eca-209">W poniższym przykładzie przedstawiono wartości, które obejmują zarówno dodatnią, a liczby ujemne.</span><span class="sxs-lookup"><span data-stu-id="47eca-209">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-210">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-210">Example</span></span>  
 <span data-ttu-id="47eca-211">W poniższym przykładzie `As` klauzuli służy do określania `datatype` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-212">Example</span></span>  
 <span data-ttu-id="47eca-213">Poniższy przykład przedstawia sposób korzystania z bitowego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="47eca-214">Wiele wartości można przypisać do wystąpienia z bitowego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="47eca-215">`Enum` Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że wyliczenia może być traktowana jako zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="47eca-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="47eca-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="47eca-216">Example</span></span>  
 <span data-ttu-id="47eca-217">Poniższy przykład iterację wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="47eca-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="47eca-218">Używa <xref:System.Enum.GetNames%2A> metoda pobierania tablicę nazw elementów członkowskich z wyliczenia, i <xref:System.Enum.GetValues%2A> do pobrania tablicy wartości elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="47eca-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="47eca-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47eca-219">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="47eca-220">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47eca-220">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="47eca-221">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47eca-221">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="47eca-222">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="47eca-222">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="47eca-223">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="47eca-223">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="47eca-224">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="47eca-224">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
