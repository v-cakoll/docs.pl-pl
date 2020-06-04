---
title: Enum, instrukcja
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
ms.openlocfilehash: 976cc68d67c69ec86918962ab2dd3406d15aed9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404735"
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="5af61-102">Enum — Instrukcja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5af61-102">Enum Statement (Visual Basic)</span></span>

<span data-ttu-id="5af61-103">Deklaruje Wyliczenie i definiuje wartości jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-103">Declares an enumeration and defines the values of its members.</span></span>

## <a name="syntax"></a><span data-ttu-id="5af61-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5af61-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]
Enum enumerationname [ As datatype ]
   memberlist
End Enum
```

## <a name="parts"></a><span data-ttu-id="5af61-105">Części</span><span class="sxs-lookup"><span data-stu-id="5af61-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="5af61-106">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5af61-106">Optional.</span></span> <span data-ttu-id="5af61-107">Lista atrybutów, które są stosowane do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="5af61-108">Należy ująć [listę atrybutów](attribute-list.md) w nawiasy kątowe (" `<` " i " `>` ").</span><span class="sxs-lookup"><span data-stu-id="5af61-108">You must enclose the [attribute list](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

  <span data-ttu-id="5af61-109">Ten <xref:System.FlagsAttribute> atrybut wskazuje, że wartość wystąpienia wyliczenia może zawierać wiele elementów członkowskich wyliczenia i że każdy element członkowski reprezentuje pole bitowe w wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>

- `accessmodifier`

  <span data-ttu-id="5af61-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5af61-110">Optional.</span></span> <span data-ttu-id="5af61-111">Określa kod, który może uzyskać dostęp do tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="5af61-112">Może być jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="5af61-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="5af61-113">Społeczeństwo</span><span class="sxs-lookup"><span data-stu-id="5af61-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="5af61-114">Chronione</span><span class="sxs-lookup"><span data-stu-id="5af61-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="5af61-115">Osoby</span><span class="sxs-lookup"><span data-stu-id="5af61-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="5af61-116">Użytek</span><span class="sxs-lookup"><span data-stu-id="5af61-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="5af61-117">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="5af61-117">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="5af61-118">Prywatne chronione</span><span class="sxs-lookup"><span data-stu-id="5af61-118">Private Protected</span></span>](../modifiers/private-protected.md)

- `Shadows`

  <span data-ttu-id="5af61-119">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5af61-119">Optional.</span></span> <span data-ttu-id="5af61-120">Określa, że to Wyliczenie ponownie deklaruje i ukrywa element programowania o identycznej nazwie lub zestaw przeciążonych elementów w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="5af61-120">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="5af61-121">Można określić tylko [cienie](../modifiers/shadows.md) na samym wyliczeniu, a nie na żadnym z jej elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-121">You can specify [Shadows](../modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>

- `enumerationname`

  <span data-ttu-id="5af61-122">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5af61-122">Required.</span></span> <span data-ttu-id="5af61-123">Nazwa wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-123">Name of the enumeration.</span></span> <span data-ttu-id="5af61-124">Aby uzyskać informacje o prawidłowych nazwach, zobacz [zadeklarowane nazwy elementów](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="5af61-124">For information on valid names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `datatype`

  <span data-ttu-id="5af61-125">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5af61-125">Optional.</span></span> <span data-ttu-id="5af61-126">Typ danych wyliczenia i wszystkie jego elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="5af61-126">Data type of the enumeration and all its members.</span></span>

- `memberlist`

  <span data-ttu-id="5af61-127">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5af61-127">Required.</span></span> <span data-ttu-id="5af61-128">Lista stałych elementów członkowskich, które są zadeklarowane w tej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5af61-128">List of member constants being declared in this statement.</span></span> <span data-ttu-id="5af61-129">W poszczególnych wierszach kodu źródłowego są wyświetlane wiele elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-129">Multiple members appear on individual source code lines.</span></span>

  <span data-ttu-id="5af61-130">Każda `member` z nich ma następującą składnię i części:`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="5af61-130">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>

  |<span data-ttu-id="5af61-131">Część</span><span class="sxs-lookup"><span data-stu-id="5af61-131">Part</span></span>|<span data-ttu-id="5af61-132">Opis</span><span class="sxs-lookup"><span data-stu-id="5af61-132">Description</span></span>|
  |---|---|
  |`membername`|<span data-ttu-id="5af61-133">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="5af61-133">Required.</span></span> <span data-ttu-id="5af61-134">Nazwa tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5af61-134">Name of this member.</span></span>|
  |`initializer`|<span data-ttu-id="5af61-135">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="5af61-135">Optional.</span></span> <span data-ttu-id="5af61-136">Wyrażenie, które jest oceniane w czasie kompilacji i przypisane do tego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5af61-136">Expression that is evaluated at compile time and assigned to this member.</span></span>|

- <span data-ttu-id="5af61-137">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="5af61-137">`End` `Enum`</span></span>

  <span data-ttu-id="5af61-138">Kończy `Enum` blok.</span><span class="sxs-lookup"><span data-stu-id="5af61-138">Terminates the `Enum` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="5af61-139">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5af61-139">Remarks</span></span>

<span data-ttu-id="5af61-140">Jeśli masz zestaw niezmienionych wartości, które są ze sobą logicznie powiązane, możesz zdefiniować je razem w wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="5af61-140">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="5af61-141">Zapewnia to zrozumiałe nazwy dla wyliczenia i jego członków, które są łatwiejsze do zapamiętania niż ich wartości.</span><span class="sxs-lookup"><span data-stu-id="5af61-141">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="5af61-142">Następnie można używać elementów członkowskich wyliczenia w wielu miejscach w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5af61-142">You can then use the enumeration members in many places in your code.</span></span>

<span data-ttu-id="5af61-143">Zalety korzystania z wyliczeń obejmują następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5af61-143">The benefits of using enumerations include the following:</span></span>

- <span data-ttu-id="5af61-144">Zmniejsza liczbę błędów spowodowanych przez transpozycję lub błędne wpisanie numerów.</span><span class="sxs-lookup"><span data-stu-id="5af61-144">Reduces errors caused by transposing or mistyping numbers.</span></span>

- <span data-ttu-id="5af61-145">Ułatwia zmianę wartości w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="5af61-145">Makes it easy to change values in the future.</span></span>

- <span data-ttu-id="5af61-146">Sprawia, że kod jest łatwiejszy do odczytania, co oznacza, że błędy będą wprowadzane.</span><span class="sxs-lookup"><span data-stu-id="5af61-146">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>

- <span data-ttu-id="5af61-147">Zapewnia zgodność dalej.</span><span class="sxs-lookup"><span data-stu-id="5af61-147">Ensures forward compatibility.</span></span> <span data-ttu-id="5af61-148">W przypadku korzystania z wyliczeń kod jest mniej prawdopodobnie niepowodzeniem, jeśli w przyszłości ktoś zmieni wartości odpowiadające nazwom członków.</span><span class="sxs-lookup"><span data-stu-id="5af61-148">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>

<span data-ttu-id="5af61-149">Wyliczenie ma nazwę, podstawowy typ danych i zestaw elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-149">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="5af61-150">Każdy element członkowski reprezentuje stałą.</span><span class="sxs-lookup"><span data-stu-id="5af61-150">Each member represents a constant.</span></span>

<span data-ttu-id="5af61-151">Wyliczenie zadeklarowane na poziomie klasy, struktury, modułu lub interfejsu, poza żadną procedurą, jest *wyliczeniem elementu członkowskiego*.</span><span class="sxs-lookup"><span data-stu-id="5af61-151">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="5af61-152">Jest członkiem klasy, struktury, modułu lub interfejsu, który go deklaruje.</span><span class="sxs-lookup"><span data-stu-id="5af61-152">It is a member of the class, structure, module, or interface that declares it.</span></span>

<span data-ttu-id="5af61-153">Do wyliczania elementów członkowskich można uzyskiwać dostęp z dowolnego miejsca w swojej klasie, strukturze, module lub interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5af61-153">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="5af61-154">Kod poza klasą, strukturą lub modułem musi kwalifikować nazwę wyliczenia elementu członkowskiego o nazwie tej klasy, struktury lub modułu.</span><span class="sxs-lookup"><span data-stu-id="5af61-154">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="5af61-155">Można uniknąć konieczności używania w pełni kwalifikowanych nazw przez dodanie instrukcji [Imports](imports-statement-net-namespace-and-type.md) do pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="5af61-155">You can avoid the need to use fully qualified names by adding an [Imports](imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>

<span data-ttu-id="5af61-156">Wyliczenie zadeklarowane na poziomie przestrzeni nazw, poza klasą, strukturą, modułem lub interfejsem, jest członkiem przestrzeni nazw, w której występuje.</span><span class="sxs-lookup"><span data-stu-id="5af61-156">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>

<span data-ttu-id="5af61-157">*Kontekst deklaracji* wyliczenia musi być plikiem źródłowym, przestrzenią nazw, klasą, strukturą, modułem lub interfejsem i nie może być procedurą.</span><span class="sxs-lookup"><span data-stu-id="5af61-157">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="5af61-158">Aby uzyskać więcej informacji, zobacz [konteksty deklaracji i domyślne poziomy dostępu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5af61-158">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="5af61-159">Atrybuty można zastosować do wyliczenia jako całości, ale nie do elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-159">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="5af61-160">Atrybut tworzy informacje w metadanych zestawu.</span><span class="sxs-lookup"><span data-stu-id="5af61-160">An attribute contributes information to the assembly's metadata.</span></span>

## <a name="data-type"></a><span data-ttu-id="5af61-161">Typ danych</span><span class="sxs-lookup"><span data-stu-id="5af61-161">Data Type</span></span>

<span data-ttu-id="5af61-162">`Enum`Instrukcja może deklarować typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-162">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="5af61-163">Każdy element członkowski Pobiera typ danych wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-163">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="5af61-164">Można określić,,,,,, `Byte` `Integer` `Long` `SByte` `Short` `UInteger` `ULong` lub `UShort` .</span><span class="sxs-lookup"><span data-stu-id="5af61-164">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>

<span data-ttu-id="5af61-165">Jeśli nie określisz `datatype` dla wyliczenia, każdy element członkowski Pobiera typ danych `initializer` .</span><span class="sxs-lookup"><span data-stu-id="5af61-165">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="5af61-166">Jeśli określisz oba elementy `datatype` i `initializer` , typ danych `initializer` musi być konwertowany na `datatype` .</span><span class="sxs-lookup"><span data-stu-id="5af61-166">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="5af61-167">Jeśli ani `datatype` nie `initializer` jest obecny, typ danych jest wartością domyślną `Integer` .</span><span class="sxs-lookup"><span data-stu-id="5af61-167">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>

## <a name="initializing-members"></a><span data-ttu-id="5af61-168">Inicjowanie członków</span><span class="sxs-lookup"><span data-stu-id="5af61-168">Initializing Members</span></span>

<span data-ttu-id="5af61-169">`Enum`Instrukcja może inicjować zawartość wybranych elementów członkowskich w `memberlist` .</span><span class="sxs-lookup"><span data-stu-id="5af61-169">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="5af61-170">Używasz, `initializer` Aby podać wyrażenie, które ma zostać przypisane do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="5af61-170">You use `initializer` to supply an expression to be assigned to the member.</span></span>

<span data-ttu-id="5af61-171">Jeśli nie określisz `initializer` dla elementu członkowskiego, Visual Basic Inicjuje to zero (jeśli jest to pierwsze `member` w `memberlist` ) lub wartość większą o jeden niż ta, która jest bezpośrednio Poprzednia `member` .</span><span class="sxs-lookup"><span data-stu-id="5af61-171">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>

<span data-ttu-id="5af61-172">Wyrażenie podane w każdym z nich `initializer` może być dowolną kombinacją literałów, innych stałych, które są już zdefiniowane, oraz składowych wyliczenia, które są już zdefiniowane, włącznie z poprzednią składową tego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-172">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="5af61-173">Do łączenia takich elementów można używać operatorów arytmetycznych i logicznych.</span><span class="sxs-lookup"><span data-stu-id="5af61-173">You can use arithmetic and logical operators to combine such elements.</span></span>

<span data-ttu-id="5af61-174">W programie nie można używać zmiennych ani funkcji `initializer` .</span><span class="sxs-lookup"><span data-stu-id="5af61-174">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="5af61-175">Można jednak użyć słów kluczowych konwersji, takich jak `CByte` i `CShort` .</span><span class="sxs-lookup"><span data-stu-id="5af61-175">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="5af61-176">Można również użyć `AscW` , jeśli wywołasz ją z stałą `String` lub `Char` argumentem, ponieważ może być oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="5af61-176">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>

<span data-ttu-id="5af61-177">Wyliczenia nie mogą mieć wartości zmiennoprzecinkowych.</span><span class="sxs-lookup"><span data-stu-id="5af61-177">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="5af61-178">Jeśli element członkowski ma przypisaną wartość zmiennoprzecinkową i `Option Strict` jest ustawiony na on, wystąpi błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="5af61-178">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="5af61-179">Jeśli `Option Strict` jest wyłączona, wartość jest automatycznie konwertowana na `Enum` Typ.</span><span class="sxs-lookup"><span data-stu-id="5af61-179">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>

<span data-ttu-id="5af61-180">Jeśli wartość elementu członkowskiego przekracza dozwolony zakres dla bazowego typu danych lub jeśli zainicjujesz dowolny element członkowski do wartości maksymalnej dozwolonej przez typ danych, kompilator zgłosi błąd.</span><span class="sxs-lookup"><span data-stu-id="5af61-180">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>

## <a name="modifiers"></a><span data-ttu-id="5af61-181">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="5af61-181">Modifiers</span></span>

<span data-ttu-id="5af61-182">Wyliczenia klasy, struktury, modułu i elementu członkowskiego interfejsu są domyślne dla dostępu publicznego.</span><span class="sxs-lookup"><span data-stu-id="5af61-182">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="5af61-183">Możesz dostosować ich poziomy dostępu za pomocą modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="5af61-183">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="5af61-184">Wyliczenie elementu członkowskiego przestrzeni nazw domyślnie ma dostęp do znajomych.</span><span class="sxs-lookup"><span data-stu-id="5af61-184">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="5af61-185">Poziom dostępu można dostosować do publicznego, ale nie do prywatnego lub chronionego.</span><span class="sxs-lookup"><span data-stu-id="5af61-185">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="5af61-186">Aby uzyskać więcej informacji, zobacz [poziomy dostępu w Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="5af61-186">For more information, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="5af61-187">Wszyscy członkowie wyliczenia mają dostęp publiczny i nie można używać żadnych modyfikatorów dostępu.</span><span class="sxs-lookup"><span data-stu-id="5af61-187">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="5af61-188">Jeśli jednak Wyliczenie ma bardziej ograniczony poziom dostępu, pierwszeństwo ma określony poziom dostępu do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-188">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>

<span data-ttu-id="5af61-189">Domyślnie wszystkie wyliczenia są typami i ich pola są stałymi.</span><span class="sxs-lookup"><span data-stu-id="5af61-189">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="5af61-190">W związku z tym `Shared` `Static` `ReadOnly` słowa kluczowe, i nie mogą być używane podczas deklarowania wyliczenia lub jego elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-190">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>

## <a name="assigning-multiple-values"></a><span data-ttu-id="5af61-191">Przypisywanie wielu wartości</span><span class="sxs-lookup"><span data-stu-id="5af61-191">Assigning Multiple Values</span></span>

<span data-ttu-id="5af61-192">Wyliczenia zazwyczaj reprezentują wzajemnie wykluczające się wartości.</span><span class="sxs-lookup"><span data-stu-id="5af61-192">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="5af61-193">Dołączając <xref:System.FlagsAttribute> atrybut w `Enum` deklaracji, można zamiast tego przypisać wiele wartości do wystąpienia wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-193">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="5af61-194">Ten <xref:System.FlagsAttribute> atrybut określa, że Wyliczenie ma być traktowane jako pole bitowe, czyli zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="5af61-194">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="5af61-195">Są one nazywane wyliczaniem *bitowym* .</span><span class="sxs-lookup"><span data-stu-id="5af61-195">These are called *bitwise* enumerations.</span></span>

<span data-ttu-id="5af61-196">W przypadku deklarowania wyliczenia przy użyciu <xref:System.FlagsAttribute> atrybutu zalecamy użycie uprawnień 2, czyli 1, 2, 4, 8, 16 itd., dla wartości.</span><span class="sxs-lookup"><span data-stu-id="5af61-196">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="5af61-197">Zalecamy również, aby wartość "none" była nazwą elementu członkowskiego, którego wartością jest 0.</span><span class="sxs-lookup"><span data-stu-id="5af61-197">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="5af61-198">Aby uzyskać dodatkowe wskazówki, zobacz <xref:System.FlagsAttribute> i <xref:System.Enum> .</span><span class="sxs-lookup"><span data-stu-id="5af61-198">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>

## <a name="example"></a><span data-ttu-id="5af61-199">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-199">Example</span></span>

<span data-ttu-id="5af61-200">Poniższy przykład pokazuje, jak używać `Enum` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5af61-200">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="5af61-201">Należy zauważyć, że element członkowski jest określany jako `EggSizeEnum.Medium` , a nie jako `Medium` .</span><span class="sxs-lookup"><span data-stu-id="5af61-201">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>

[!code-vb[VbEnumsTask#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#41)]

## <a name="example"></a><span data-ttu-id="5af61-202">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-202">Example</span></span>

<span data-ttu-id="5af61-203">Metoda w poniższym przykładzie znajduje się poza `Egg` klasą.</span><span class="sxs-lookup"><span data-stu-id="5af61-203">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="5af61-204">W związku z tym, `EggSizeEnum` jest w pełni kwalifikowana jako `Egg.EggSizeEnum` .</span><span class="sxs-lookup"><span data-stu-id="5af61-204">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>

[!code-vb[VbEnumsTask#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#42)]

## <a name="example"></a><span data-ttu-id="5af61-205">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-205">Example</span></span>

<span data-ttu-id="5af61-206">Poniższy przykład używa `Enum` instrukcji w celu zdefiniowania powiązanego zestawu nazwanych stałych wartości.</span><span class="sxs-lookup"><span data-stu-id="5af61-206">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="5af61-207">W takim przypadku wartości są kolorami, które można wybrać do projektowania formularzy wprowadzania danych dla bazy danych.</span><span class="sxs-lookup"><span data-stu-id="5af61-207">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>

[!code-vb[VbEnumsTask#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#30)]

## <a name="example"></a><span data-ttu-id="5af61-208">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-208">Example</span></span>

<span data-ttu-id="5af61-209">Poniższy przykład pokazuje wartości, które zawierają zarówno liczbę dodatnią, jak i ujemną.</span><span class="sxs-lookup"><span data-stu-id="5af61-209">The following example shows values that include both positive and negative numbers.</span></span>

[!code-vb[VbEnumsTask#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#31)]

## <a name="example"></a><span data-ttu-id="5af61-210">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-210">Example</span></span>

<span data-ttu-id="5af61-211">W poniższym przykładzie `As` klauzula służy do określenia `datatype` wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="5af61-211">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>

[!code-vb[VbEnumsTask#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#6)]

## <a name="example"></a><span data-ttu-id="5af61-212">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-212">Example</span></span>

<span data-ttu-id="5af61-213">Poniższy przykład pokazuje, jak używać wyliczenia bitowego.</span><span class="sxs-lookup"><span data-stu-id="5af61-213">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="5af61-214">Do wystąpienia wyliczenia bitowego można przypisać wiele wartości.</span><span class="sxs-lookup"><span data-stu-id="5af61-214">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="5af61-215">`Enum`Deklaracja zawiera <xref:System.FlagsAttribute> atrybut, który wskazuje, że Wyliczenie może być traktowane jako zestaw flag.</span><span class="sxs-lookup"><span data-stu-id="5af61-215">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>

[!code-vb[VbEnumsTask#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#61)]

## <a name="example"></a><span data-ttu-id="5af61-216">Przykład</span><span class="sxs-lookup"><span data-stu-id="5af61-216">Example</span></span>

<span data-ttu-id="5af61-217">Poniższy przykład wykonuje iterację przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="5af61-217">The following example iterates through an enumeration.</span></span> <span data-ttu-id="5af61-218">Używa metody, <xref:System.Enum.GetNames%2A> Aby pobrać tablicę nazw elementów członkowskich z wyliczenia i <xref:System.Enum.GetValues%2A> pobrać tablicę wartości elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="5af61-218">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>

[!code-vb[VbEnumsTask#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class1.vb#51)]

## <a name="see-also"></a><span data-ttu-id="5af61-219">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5af61-219">See also</span></span>

- <xref:System.Enum>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- [<span data-ttu-id="5af61-220">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5af61-220">Const Statement</span></span>](const-statement.md)
- [<span data-ttu-id="5af61-221">Dim, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5af61-221">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="5af61-222">Konwersje jawne i niejawne</span><span class="sxs-lookup"><span data-stu-id="5af61-222">Implicit and Explicit Conversions</span></span>](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5af61-223">Funkcje konwersji typu</span><span class="sxs-lookup"><span data-stu-id="5af61-223">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="5af61-224">Stałe i wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5af61-224">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
