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
ms.openlocfilehash: 89de51f2551437d102ccdc5a0f1ff5f23b53e47f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="7c0b1-102">Enum — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c0b1-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="7c0b1-103">Deklaruje wyliczenie i definiuje wartości jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c0b1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c0b1-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="7c0b1-105">Części</span><span class="sxs-lookup"><span data-stu-id="7c0b1-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="7c0b1-106">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-106">Optional.</span></span> <span data-ttu-id="7c0b1-107">Lista atrybutów, które są stosowane do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="7c0b1-108">Musisz ją ująć [lista atrybutów](../../../visual-basic/language-reference/statements/attribute-list.md) w nawiasy ("`<`"i"`>`").</span><span class="sxs-lookup"><span data-stu-id="7c0b1-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="7c0b1-109"><xref:System.FlagsAttribute> Atrybut wskazuje, że wartości wyliczenia wystąpienia może zawierać wiele elementy członkowskie wyliczenia i że każdy element członkowski reprezentuje pole bitowe wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="7c0b1-110">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-110">Optional.</span></span> <span data-ttu-id="7c0b1-111">Określa, jaki kod mogą uzyskiwać dostęp do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="7c0b1-112">Może to być jeden z następujących elementów:</span><span class="sxs-lookup"><span data-stu-id="7c0b1-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="7c0b1-113">Public</span><span class="sxs-lookup"><span data-stu-id="7c0b1-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="7c0b1-114">Protected</span><span class="sxs-lookup"><span data-stu-id="7c0b1-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="7c0b1-115">Friend</span><span class="sxs-lookup"><span data-stu-id="7c0b1-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="7c0b1-116">Private</span><span class="sxs-lookup"><span data-stu-id="7c0b1-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="7c0b1-117">Można określić `Protected``Friend` się zezwolić na dostęp z kodu w obrębie klasy wyliczenia, klasy pochodnej lub tego samego zestawu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="7c0b1-118">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-118">Optional.</span></span> <span data-ttu-id="7c0b1-119">Określa, że to wyliczenie programistyczny ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zbiór elementów przeciążona w klasie podstawowej.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="7c0b1-120">Można określić [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) tylko na wyliczenie samego, nie na żadnym z jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="7c0b1-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-121">Required.</span></span> <span data-ttu-id="7c0b1-122">Nazwa wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-122">Name of the enumeration.</span></span> <span data-ttu-id="7c0b1-123">Uzyskać informacji o prawidłowych nazw, zobacz [zadeklarowane nazwy elementów](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7c0b1-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="7c0b1-124">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-124">Optional.</span></span> <span data-ttu-id="7c0b1-125">Typ danych wyliczenia i wszyscy jej członkowie.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="7c0b1-126">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-126">Required.</span></span> <span data-ttu-id="7c0b1-127">Lista stałe element członkowski został zadeklarowany w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="7c0b1-128">Wiele elementów członkowskich są wyświetlane na poszczególnych źródła wierszy kodu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="7c0b1-129">Każdy `member` ma następujące składni i części: `[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="7c0b1-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="7c0b1-130">Część</span><span class="sxs-lookup"><span data-stu-id="7c0b1-130">Part</span></span>|<span data-ttu-id="7c0b1-131">Opis</span><span class="sxs-lookup"><span data-stu-id="7c0b1-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="7c0b1-132">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-132">Required.</span></span> <span data-ttu-id="7c0b1-133">Nazwa tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="7c0b1-134">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-134">Optional.</span></span> <span data-ttu-id="7c0b1-135">Wyrażenie, które jest obliczane w czasie kompilacji i przypisane do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="7c0b1-136">`End``Enum`</span><span class="sxs-lookup"><span data-stu-id="7c0b1-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="7c0b1-137">Kończy blok `Enum`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c0b1-138">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c0b1-138">Remarks</span></span>  
 <span data-ttu-id="7c0b1-139">Jeśli masz zestaw wartości niezmiennych, logicznie powiązanych ze sobą, należy je zdefiniować w razem w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="7c0b1-140">Zapewnia to znaczące nazwy dla wyliczenia i jej elementów członkowskich, które są łatwiejsze do zapamiętania niż ich wartości.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="7c0b1-141">Elementy członkowskie wyliczenia można następnie użyć w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="7c0b1-142">Korzyści wynikające ze stosowania wyliczenia są następujące:</span><span class="sxs-lookup"><span data-stu-id="7c0b1-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="7c0b1-143">Zmniejsza liczbę błędów spowodowanych przez Transponowanie lub błędne liczby.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="7c0b1-144">Można łatwo zmienić wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="7c0b1-145">Powoduje, że kod czytelności, co oznacza, że jest mniej prawdopodobne, że błędy zostaną wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="7c0b1-146">Zapewnia zgodność z nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-146">Ensures forward compatibility.</span></span> <span data-ttu-id="7c0b1-147">Jeśli używasz wyliczenia, kod jest mniej prawdopodobne się niepowodzeniem, jeśli w przyszłości użytkownik wprowadza zmiany wartości odpowiadających nazwy elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="7c0b1-148">Wyliczenie ma nazwę, podstawowym typem danych i zestaw elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="7c0b1-149">Każdy element członkowski reprezentuje stałą.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="7c0b1-150">To wyliczenie zadeklarowane na klasy, struktury, modułu lub poziom interfejsu poza dowolnej procedury *elementu członkowskiego wyliczenia*.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="7c0b1-151">Jest elementem członkowskim klasy, struktury, modułu lub interfejsu, który deklaruje go.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="7c0b1-152">Element członkowski wyliczenia można uzyskać z dowolnego miejsca w obrębie klasy, struktury, modułu lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="7c0b1-153">Kod poza klasą, strukturą lub modułu muszą nazwy wyliczenia elementu członkowskiego z nazwą tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="7c0b1-154">Aby uniknąć konieczności używania w pełni kwalifikowane nazwy przez dodanie [importów](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instrukcji do pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="7c0b1-155">Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasy, struktury, modułu lub interfejsu, jest członkiem przestrzeni nazw, w których występuje.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="7c0b1-156">*Kontekście deklaracji* wyliczenia musi być pliku źródłowego, przestrzeni nazw, klasy, struktury, modułu lub interfejsu i nie może być procedury.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="7c0b1-157">Aby uzyskać więcej informacji, zobacz [Declaration Contexts and Default Access Level](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md) (Kontekst deklaracji i domyślne poziomy dostępu).</span><span class="sxs-lookup"><span data-stu-id="7c0b1-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="7c0b1-158">Można zastosować atrybutów do wyliczenia jako całość, ale nie do jego elementów członkowskich pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="7c0b1-159">Atrybut wspiera informacje dotyczące metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="7c0b1-160">Typ danych</span><span class="sxs-lookup"><span data-stu-id="7c0b1-160">Data Type</span></span>  
 <span data-ttu-id="7c0b1-161">`Enum` Instrukcji można zadeklarować typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="7c0b1-162">Każdy element członkowski ma typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="7c0b1-163">Można określić `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, lub `UShort`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="7c0b1-164">Jeśli nie określisz `datatype` wyliczenia, każdy element członkowski ma typ danych jego `initializer`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="7c0b1-165">Jeśli możesz określić ich obu `datatype` i `initializer`, typ danych miary `initializer` musi być możliwe do przekonwertowania na `datatype`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="7c0b1-166">Jeśli żadna `datatype` ani `initializer` ma typ danych wartości domyślnych do `Integer`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="7c0b1-167">Podczas inicjowania elementów członkowskich</span><span class="sxs-lookup"><span data-stu-id="7c0b1-167">Initializing Members</span></span>  
 <span data-ttu-id="7c0b1-168">`Enum` Instrukcji można zainicjować zawartość wybranych członków w `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="7c0b1-169">Możesz użyć `initializer` umożliwiają określanie wartości wyrażenia w można przypisać do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="7c0b1-170">Jeśli nie określisz `initializer` dla elementu członkowskiego języka Visual Basic inicjowane albo zero (jeśli jest pierwszy `member` w `memberlist`), lub wartość większą o jeden niż bezpośrednio przed `member`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="7c0b1-171">Wyrażenie podane w każdym `initializer` może być dowolną kombinacją literały, inne stałe, które zostały już zdefiniowane i elementy członkowskie wyliczenia, które zostały już zdefiniowane, włączając poprzedni element członkowski tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="7c0b1-172">Operatory arytmetyczne i logiczne umożliwia łączenie takich elementów.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="7c0b1-173">Nie można używać zmiennych lub funkcje w `initializer`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="7c0b1-174">Jednak takie jak można użyć słowa kluczowe konwersji `CByte` i `CShort`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="7c0b1-175">Można również użyć `AscW` połączeń ze stałą `String` lub `Char` argumentu, ponieważ może zostać oceniony w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="7c0b1-176">Wyliczenia nie może mieć wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="7c0b1-177">Jeśli element członkowski jest przypisywana wartość zmiennoprzecinkowa i `Option Strict` ma wartość on, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="7c0b1-178">Jeśli `Option Strict` jest wyłączony, wartość jest automatycznie konwertowany do `Enum` typu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="7c0b1-179">Jeśli wartość elementu członkowskiego przekracza dopuszczalny zakres dla odpowiedniego typu danych lub zainicjować członków do maksymalna wartość dozwolona przez podstawowy typ danych, kompilator zgłasza błąd.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="7c0b1-180">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="7c0b1-180">Modifiers</span></span>  
 <span data-ttu-id="7c0b1-181">Klasy, struktury, moduł i domyślnie wyliczenia elementu członkowskiego interfejsu dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="7c0b1-182">Poziomy dostępu modułów można dostosować za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="7c0b1-183">Namespace elementu członkowskiego wyliczenia domyślną wartość przyjaznego dostępu.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="7c0b1-184">Można dostosować ich poziomy dostępu publicznego, ale nie prywatne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="7c0b1-185">Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7c0b1-185">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="7c0b1-186">Wszystkie elementy członkowskie wyliczenia mają dostęp publiczny i nie można użyć dowolnego modyfikatorów dostępu na nich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="7c0b1-187">Jednak jeśli wyliczenia sam bardziej ograniczony poziom dostępu, wyliczenie określony poziom dostępu ma priorytet.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="7c0b1-188">Domyślnie wszystkie wyliczenia są typy i ich pola są stałe.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="7c0b1-189">W związku z tym `Shared`, `Static`, i `ReadOnly` nie można użyć słowa kluczowe przy deklarowaniu wyliczenie lub jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="7c0b1-190">Przypisywanie wielu wartości</span><span class="sxs-lookup"><span data-stu-id="7c0b1-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="7c0b1-191">Wyliczenia zazwyczaj reprezentują wartości wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="7c0b1-192">W tym <xref:System.FlagsAttribute> atrybutu w `Enum` deklaracji, zamiast tego do można przypisać wielu wartości wystąpienia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="7c0b1-193"><xref:System.FlagsAttribute> Atrybut określa, że wyliczenia być traktowane jako pole bitowe, czyli zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="7c0b1-194">Są one nazywane *bitowe* wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="7c0b1-195">Gdy zadeklarować wyliczenia za pomocą <xref:System.FlagsAttribute> atrybutu, firma Microsoft zaleca użycie potęgami liczby 2, który jest, 1, 2, 4, 8, 16 i tak dalej dla wartości.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="7c0b1-196">Ponadto zaleca się "None" nazwę elementu członkowskiego, którego wartość jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="7c0b1-197">Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c0b1-198">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-198">Example</span></span>  
 <span data-ttu-id="7c0b1-199">Poniższy przykład przedstawia użycie `Enum` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="7c0b1-200">Należy pamiętać, że element członkowski jest określany jako `EggSizeEnum.Medium`, a nie jako `Medium`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-201">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-201">Example</span></span>  
 <span data-ttu-id="7c0b1-202">W poniższym przykładzie metody jest poza `Egg` klasy.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-202">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="7c0b1-203">W związku z tym `EggSizeEnum` jest w pełni kwalifikowany jako `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-203">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-204">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-204">Example</span></span>  
 <span data-ttu-id="7c0b1-205">W poniższym przykładzie użyto `Enum` instrukcję, aby zdefiniować powiązany zestaw o nazwie wartości stałych.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-205">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="7c0b1-206">W tym przypadku wartości są kolorów, które można wybrać do projektowania formularzy zapis danych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-206">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-207">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-207">Example</span></span>  
 <span data-ttu-id="7c0b1-208">W poniższym przykładzie przedstawiono wartości, które obejmują zarówno dodatnią, a liczby ujemne.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-208">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-209">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-209">Example</span></span>  
 <span data-ttu-id="7c0b1-210">W poniższym przykładzie `As` klauzuli służy do określania `datatype` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-210">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-211">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-211">Example</span></span>  
 <span data-ttu-id="7c0b1-212">Poniższy przykład przedstawia sposób korzystania z bitowego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-212">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="7c0b1-213">Wiele wartości można przypisać do wystąpienia z bitowego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-213">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="7c0b1-214">`Enum` Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że wyliczenia może być traktowana jako zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-214">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="7c0b1-215">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c0b1-215">Example</span></span>  
 <span data-ttu-id="7c0b1-216">Poniższy przykład iterację wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-216">The following example iterates through an enumeration.</span></span> <span data-ttu-id="7c0b1-217">Używa <xref:System.Enum.GetNames%2A> metoda pobierania tablicę nazw elementów członkowskich z wyliczenia, i <xref:System.Enum.GetValues%2A> do pobrania tablicy wartości elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="7c0b1-217">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7c0b1-218">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7c0b1-218">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="7c0b1-219">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0b1-219">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="7c0b1-220">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7c0b1-220">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="7c0b1-221">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="7c0b1-221">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="7c0b1-222">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="7c0b1-222">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="7c0b1-223">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7c0b1-223">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
