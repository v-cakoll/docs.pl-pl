---
title: Określanie w pełni kwalifikowanych nazw typów
ms.date: 02/21/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- languages, grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc8395492992c22da3c635f0de010516127f9be4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793006"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="47f45-102">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="47f45-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="47f45-103">Należy określić nazwy typów, które mają prawidłowe dane wejściowe do różnych operacji odbicia.</span><span class="sxs-lookup"><span data-stu-id="47f45-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="47f45-104">W pełni kwalifikowaną nazwę typu składa się z specyfikacja nazwy zestawu, specyfikacji przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="47f45-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="47f45-105">Specyfikacje nazwy typu są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47f45-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="47f45-106">Gramatyka dla nazwy typów</span><span class="sxs-lookup"><span data-stu-id="47f45-106">Grammar for type names</span></span>

 <span data-ttu-id="47f45-107">Gramatyka definiuje składni języków formalnych.</span><span class="sxs-lookup"><span data-stu-id="47f45-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="47f45-108">Poniższa tabela zawiera listę leksykalne reguły, które opisują rozpoznawanie prawidłowych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="47f45-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="47f45-109">Terminali (te elementy, które nie są dodatkowo obniżaniu) są wyświetlane w wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="47f45-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="47f45-110">Symboli nieterminalnych (te elementy, które są dodatkowo obniżaniu) są wyświetlane w ciągach znaków, jak i pojedynczo cudzysłowach, ale apostrof (') nie jest częścią składni sam.</span><span class="sxs-lookup"><span data-stu-id="47f45-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="47f45-111">Znaku kreski pionowej (&#124;) oznacza reguły, które mają reguły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="47f45-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

<!-- markdownlint-disable MD010 -->
```antlr
TypeSpec
    : ReferenceTypeSpec
    | SimpleTypeSpec
    ;

ReferenceTypeSpec
    : SimpleTypeSpec '&'
    ;

SimpleTypeSpec
    : PointerTypeSpec
    | GenericTypeSpec
    | TypeName
    ;

GenericTypeSpec
   : SimpleTypeSpec ` NUMBER

PointerTypeSpec
    : SimpleTypeSpec '*'
    ;

ArrayTypeSpec
    : SimpleTypeSpec '[ReflectionDimension]'
    | SimpleTypeSpec '[ReflectionEmitDimension]'
    ;

ReflectionDimension
    : '*'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

ReflectionEmitDimension
    : '*'
    | Number '..' Number
    | Number '…'
    | ReflectionDimension ',' ReflectionDimension
    | NOTOKEN
    ;

Number
    : [0-9]+
    ;

TypeName
    : NamespaceTypeName
    | NamespaceTypeName ',' AssemblyNameSpec
    ;

NamespaceTypeName
    : NestedTypeName
    | NamespaceSpec '.' NestedTypeName
    ;

NestedTypeName
    : IDENTIFIER
    | NestedTypeName '+' IDENTIFIER
    ;

NamespaceSpec
    : IDENTIFIER
    | NamespaceSpec '.' IDENTIFIER
    ;

AssemblyNameSpec
    : IDENTIFIER
    | IDENTIFIER ',' AssemblyProperties
    ;

AssemblyProperties
    : AssemblyProperty
    | AssemblyProperties ',' AssemblyProperty
    ;

AssemblyProperty
    : AssemblyPropertyName '=' AssemblyPropertyValue
    ;
```
<!-- markdownlint-enable MD010 -->

## <a name="specifying-special-characters"></a><span data-ttu-id="47f45-112">Określania znaków specjalnych</span><span class="sxs-lookup"><span data-stu-id="47f45-112">Specifying special characters</span></span>

<span data-ttu-id="47f45-113">W nazwie typu identyfikator jest Dowolna prawidłowa nazwa określona w zasadach języka.</span><span class="sxs-lookup"><span data-stu-id="47f45-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="47f45-114">Użyj ukośnik odwrotny (\\) jako znak ucieczki, aby oddzielić następujące generatory kodów, gdy jest używana jako część IDENTYFIKATORA.</span><span class="sxs-lookup"><span data-stu-id="47f45-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="47f45-115">Token</span><span class="sxs-lookup"><span data-stu-id="47f45-115">Token</span></span>|<span data-ttu-id="47f45-116">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="47f45-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="47f45-117">\\,</span><span class="sxs-lookup"><span data-stu-id="47f45-117">\\,</span></span>|<span data-ttu-id="47f45-118">Separator zestawu.</span><span class="sxs-lookup"><span data-stu-id="47f45-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="47f45-119">Separator typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="47f45-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="47f45-120">Typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="47f45-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="47f45-121">Typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="47f45-121">Pointer type.</span></span>|
|<span data-ttu-id="47f45-122">\\[</span><span class="sxs-lookup"><span data-stu-id="47f45-122">\\[</span></span>|<span data-ttu-id="47f45-123">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="47f45-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="47f45-124">\\]</span><span class="sxs-lookup"><span data-stu-id="47f45-124">\\]</span></span>|<span data-ttu-id="47f45-125">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="47f45-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="47f45-126">\\.</span><span class="sxs-lookup"><span data-stu-id="47f45-126">\\.</span></span>|<span data-ttu-id="47f45-127">Użyj ukośnik odwrotny przed kropką, tylko wtedy, gdy kropka jest używana w specyfikacji tablicy.</span><span class="sxs-lookup"><span data-stu-id="47f45-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="47f45-128">Okresy w NamespaceSpec nie przyjmują ukośnik odwrotny.</span><span class="sxs-lookup"><span data-stu-id="47f45-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="47f45-129">\\\|Ukośnik odwrotny w razie jako ciąg literału.</span><span class="sxs-lookup"><span data-stu-id="47f45-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="47f45-130">Należy pamiętać, że TypeSpec wszystkie składniki z wyjątkiem AssemblyNameSpec, spacje są istotne.</span><span class="sxs-lookup"><span data-stu-id="47f45-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="47f45-131">W AssemblyNameSpec spacje przed separatorem ',' są istotne, ale spacje po separatorze ',' są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="47f45-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="47f45-132">Odbicie klasy takie jak <xref:System.Type.FullName%2A?displayProperty=nameWithType>, wróć zniekształcone nazwy, nazwa zwróconego mogą być używane w wywołaniu <xref:System.Type.GetType%2A>, jak w `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="47f45-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="47f45-133">Na przykład może być w pełni kwalifikowana nazwa typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="47f45-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="47f45-134">Jeśli przestrzeń nazw `Ozzy.Out+Back`, a następnie znak plus musi być poprzedzony znakiem ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="47f45-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="47f45-135">W przeciwnym razie analizatora będzie zinterpretuje ją jako separator zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="47f45-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="47f45-136">Odbicie emituje ten ciąg w kodowaniu `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="47f45-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="47f45-137">Określanie nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="47f45-137">Specifying assembly names</span></span>

<span data-ttu-id="47f45-138">Minimalnych wymaganych informacji w specyfikacja nazwy zestawu jest tekstowa Nazwa zestawu (identyfikator).</span><span class="sxs-lookup"><span data-stu-id="47f45-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="47f45-139">Możesz wykonać identyfikator listę rozdzielonych przecinkami pary właściwość/wartość, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="47f45-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="47f45-140">Nazewnictwa identyfikatorów należy stosować reguły nazewnictwa plików.</span><span class="sxs-lookup"><span data-stu-id="47f45-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="47f45-141">Identyfikator jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="47f45-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="47f45-142">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="47f45-142">Property name</span></span>|<span data-ttu-id="47f45-143">Opis</span><span class="sxs-lookup"><span data-stu-id="47f45-143">Description</span></span>|<span data-ttu-id="47f45-144">Dopuszczalne wartości</span><span class="sxs-lookup"><span data-stu-id="47f45-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="47f45-145">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="47f45-145">**Version**</span></span>|<span data-ttu-id="47f45-146">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="47f45-146">Assembly version number</span></span>|<span data-ttu-id="47f45-147">*Główna.pomocnicza.kompilacja.poprawka*, gdzie *głównych*, *pomocnicza*, *kompilacji*, i *poprawki* są liczbami całkowitymi od 0 i 65535 (włącznie).</span><span class="sxs-lookup"><span data-stu-id="47f45-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="47f45-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="47f45-148">**PublicKey**</span></span>|<span data-ttu-id="47f45-149">Klucz publiczny pełnej</span><span class="sxs-lookup"><span data-stu-id="47f45-149">Full public key</span></span>|<span data-ttu-id="47f45-150">Wartość klucza pełnej publicznego w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="47f45-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="47f45-151">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="47f45-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="47f45-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="47f45-152">**PublicKeyToken**</span></span>|<span data-ttu-id="47f45-153">Token klucza publicznego (8-bajtowych skrót klucza publicznego pełnej)</span><span class="sxs-lookup"><span data-stu-id="47f45-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="47f45-154">Wartość tokenu klucza publicznego w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="47f45-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="47f45-155">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="47f45-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="47f45-156">**Kultury**</span><span class="sxs-lookup"><span data-stu-id="47f45-156">**Culture**</span></span>|<span data-ttu-id="47f45-157">Język zestawu</span><span class="sxs-lookup"><span data-stu-id="47f45-157">Assembly culture</span></span>|<span data-ttu-id="47f45-158">Kultura zestawu w formacie RFC 1766 lub "węgla" zestawy niezależny od języka (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="47f45-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="47f45-159">**Custom**</span><span class="sxs-lookup"><span data-stu-id="47f45-159">**Custom**</span></span>|<span data-ttu-id="47f45-160">Niestandardowe duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="47f45-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="47f45-161">Obecnie jest on używany tylko w zestawów generowanych przez [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="47f45-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="47f45-162">Niestandardowy ciąg jest używany przez narzędzie Native Image Generator, by powiadomić pamięci podręcznej zestawów, czy zestaw instalowany jest obraz macierzysty i dlatego ma być zainstalowany w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="47f45-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="47f45-163">Skrót ciągu zap.</span><span class="sxs-lookup"><span data-stu-id="47f45-163">Also called a zap string.</span></span>|

<span data-ttu-id="47f45-164">W poniższym przykładzie przedstawiono **AssemblyName** po prostu nazwanego zestawu przy użyciu domyślnej kultury.</span><span class="sxs-lookup"><span data-stu-id="47f45-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="47f45-165">Poniższy przykład przedstawia w pełni określone odwołanie dla zestawu o silnej nazwie z kulturą "en".</span><span class="sxs-lookup"><span data-stu-id="47f45-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="47f45-166">W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, które mogą zostać zrealizowane przez silne lub po prostu nazwanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="47f45-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="47f45-167">W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, muszą być spełnione, po prostu nazwanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="47f45-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="47f45-168">W poniższych przykładach każdego pokazano częściowo określoną **AssemblyName**, muszą być spełnione przez zestaw o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="47f45-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="47f45-169">Określanie typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="47f45-169">Specifying generic types</span></span>

<span data-ttu-id="47f45-170">SimpleTypeSpec\`numer reprezentuje to otwarty typ ogólny z od 1 do *n* parametrów typu genetycznego.</span><span class="sxs-lookup"><span data-stu-id="47f45-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="47f45-171">Na przykład, można pobrać odwołania do otwarty typ ogólny listy\<T > lub zamknięty typ ogólny List\<ciągu >, użyj ``Type.GetType("System.Collections.Generic.List`1")`` można pobrać odwołania do typu ogólnego słownika\<TKey, TValue >, użyj ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span><span class="sxs-lookup"><span data-stu-id="47f45-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="47f45-172">Określenie wskaźników</span><span class="sxs-lookup"><span data-stu-id="47f45-172">Specifying pointers</span></span>

<span data-ttu-id="47f45-173">SimpleTypeSpec \* reprezentuje niezarządzanym wskaźnikiem.</span><span class="sxs-lookup"><span data-stu-id="47f45-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="47f45-174">Na przykład, aby uzyskać wskaźnik do typu MyType, użyj `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="47f45-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="47f45-175">Aby uzyskać wskaźnik do wskaźnika do typu MyType, użyj `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="47f45-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="47f45-176">Określanie odwołania</span><span class="sxs-lookup"><span data-stu-id="47f45-176">Specifying references</span></span>

<span data-ttu-id="47f45-177">SimpleTypeSpec & reprezentuje zarządzane wskaźnika lub odwołania.</span><span class="sxs-lookup"><span data-stu-id="47f45-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="47f45-178">Na przykład, aby uzyskać odwołanie do typu MyType, należy użyć `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="47f45-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="47f45-179">Należy pamiętać, że w przeciwieństwie do wskaźników, odwołań są ograniczone do jednego poziomu.</span><span class="sxs-lookup"><span data-stu-id="47f45-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="47f45-180">Określanie tablic</span><span class="sxs-lookup"><span data-stu-id="47f45-180">Specifying arrays</span></span>

<span data-ttu-id="47f45-181">W gramatyka BNF ReflectionEmitDimension ma zastosowanie tylko w definicjach niekompletnego typu pobrany przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47f45-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="47f45-182">Definicje niekompletnego typu <xref:System.Reflection.Emit.TypeBuilder> tworzony przy użyciu obiektów <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na którym <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="47f45-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="47f45-183">ReflectionDimension może służyć do pobrania żadnych definicji typu, który został wykonany, to znaczy, typ, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="47f45-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="47f45-184">Tablice są dostępne w odbiciu, określając rangę tablicy:</span><span class="sxs-lookup"><span data-stu-id="47f45-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="47f45-185">`Type.GetType("MyArray[]")` pobiera tablicy jednowymiarowej, za pomocą 0 dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="47f45-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="47f45-186">`Type.GetType("MyArray[*]")` pobiera tablicy jednowymiarowej, za pomocą nieznany dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="47f45-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="47f45-187">`Type.GetType("MyArray[][]")` Pobiera tablicę dwuwymiarową tablicę.</span><span class="sxs-lookup"><span data-stu-id="47f45-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="47f45-188">`Type.GetType("MyArray[*,*]")` i `Type.GetType("MyArray[,]")` pobiera prostokątnej dwuwymiarowej tablicy przy użyciu nieznanego dolne granice.</span><span class="sxs-lookup"><span data-stu-id="47f45-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="47f45-189">Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]`, ale dla tablic wielowymiarowych dwóch notacji są równoważne.</span><span class="sxs-lookup"><span data-stu-id="47f45-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="47f45-190">Oznacza to, że `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` daje w wyniku **true**.</span><span class="sxs-lookup"><span data-stu-id="47f45-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="47f45-191">Aby uzyskać **ModuleBuilder.GetType**, `MyArray[0..5]` wskazuje tablicy jednowymiarowej, o rozmiarze 6, niższe powiązane 0.</span><span class="sxs-lookup"><span data-stu-id="47f45-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="47f45-192">`MyArray[4…]` Wskazuje tablicy jednowymiarowej, o nieznanym rozmiarze i dolnej granicy 4.</span><span class="sxs-lookup"><span data-stu-id="47f45-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="47f45-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47f45-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="47f45-194">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="47f45-194">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
