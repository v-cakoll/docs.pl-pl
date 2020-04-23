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
ms.openlocfilehash: 707c71482196d789ed9a88db34af048ec57734fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130034"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="f9935-102">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="f9935-102">Specifying fully qualified type names</span></span>

<span data-ttu-id="f9935-103">Musisz określić nazwy typów, aby mieć prawidłowe dane wejściowe różnych operacji odbicia.</span><span class="sxs-lookup"><span data-stu-id="f9935-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="f9935-104">W pełni kwalifikowana nazwa typu zawiera specyfikację nazwy zestawu, specyfikację przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="f9935-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="f9935-105">Specyfikacje nazw typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f9935-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="f9935-106">Gramatyka nazw typów</span><span class="sxs-lookup"><span data-stu-id="f9935-106">Grammar for type names</span></span>

 <span data-ttu-id="f9935-107">Gramatyka definiuje składnię języków formalnych.</span><span class="sxs-lookup"><span data-stu-id="f9935-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="f9935-108">W poniższej tabeli wymieniono reguły leksykalne opisujące sposób rozpoznawania prawidłowych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="f9935-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="f9935-109">W przypadku terminali (te elementy, które nie są jeszcze możliwe do zredukowania), są wyświetlane wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="f9935-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="f9935-110">Nieterminale (te elementy, które są dalsze możliwe do zredukowania) są wyświetlane w postaci ciągów z rozróżnianą wielkością liter lub z pojedynczą cudzysłowem, ale pojedynczy cudzysłów (') nie jest częścią samej składni.</span><span class="sxs-lookup"><span data-stu-id="f9935-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="f9935-111">Znak potoku (&#124;) oznacza reguły mające reguły subrules.</span><span class="sxs-lookup"><span data-stu-id="f9935-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="f9935-112">Określanie znaków specjalnych</span><span class="sxs-lookup"><span data-stu-id="f9935-112">Specifying special characters</span></span>

<span data-ttu-id="f9935-113">W nazwie typu identyfikator to dowolna prawidłowa nazwa określona przez reguły języka.</span><span class="sxs-lookup"><span data-stu-id="f9935-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="f9935-114">Użyj ukośnika odwrotnego\\() jako znaku ucieczki, aby oddzielić następujące tokeny, gdy są używane jako część identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="f9935-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="f9935-115">Token</span><span class="sxs-lookup"><span data-stu-id="f9935-115">Token</span></span>|<span data-ttu-id="f9935-116">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="f9935-116">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="f9935-117">\\,</span><span class="sxs-lookup"><span data-stu-id="f9935-117">\\,</span></span>|<span data-ttu-id="f9935-118">Separator zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9935-118">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="f9935-119">Zagnieżdżony Separator typu.</span><span class="sxs-lookup"><span data-stu-id="f9935-119">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="f9935-120">Typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="f9935-120">Reference type.</span></span>|
|\\*|<span data-ttu-id="f9935-121">Typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f9935-121">Pointer type.</span></span>|
|<span data-ttu-id="f9935-122">\\[</span><span class="sxs-lookup"><span data-stu-id="f9935-122">\\[</span></span>|<span data-ttu-id="f9935-123">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9935-123">Array dimension delimiter.</span></span>|
|<span data-ttu-id="f9935-124">\\]</span><span class="sxs-lookup"><span data-stu-id="f9935-124">\\]</span></span>|<span data-ttu-id="f9935-125">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9935-125">Array dimension delimiter.</span></span>|
|<span data-ttu-id="f9935-126">\\.</span><span class="sxs-lookup"><span data-stu-id="f9935-126">\\.</span></span>|<span data-ttu-id="f9935-127">Użyj ukośnika odwrotnego przed kropką, tylko jeśli okres jest używany w specyfikacji tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9935-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="f9935-128">Okresy w NamespaceSpec nie przyjmują ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f9935-128">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="f9935-129">\\\|Ukośnik odwrotny, gdy jest wymagany jako literał ciągu.</span><span class="sxs-lookup"><span data-stu-id="f9935-129">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="f9935-130">Należy pamiętać, że we wszystkich składnikach TypeSpec z wyjątkiem AssemblyNameSpec, spacje są istotne.</span><span class="sxs-lookup"><span data-stu-id="f9935-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="f9935-131">W AssemblyNameSpec, spacje przed separatorem ', ' są istotne, ale spacje po separatorze ', ' są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="f9935-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="f9935-132">Klasy odbicia, takie <xref:System.Type.FullName%2A?displayProperty=nameWithType>jak, zwracają nazwę zniekształcona, aby można było użyć zwracanej nazwy w wywołaniu do <xref:System.Type.GetType%2A>, jako w. `MyType.GetType(myType.FullName)`</span><span class="sxs-lookup"><span data-stu-id="f9935-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="f9935-133">Na przykład w pełni kwalifikowana nazwa dla typu może być `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="f9935-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="f9935-134">Jeśli przestrzeń nazw była `Ozzy.Out+Back`, znak plus musi być poprzedzony ukośnikiem odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="f9935-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="f9935-135">W przeciwnym razie Analizator interpretuje go jako separator zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="f9935-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="f9935-136">Odbicie emituje ten ciąg `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`jako.</span><span class="sxs-lookup"><span data-stu-id="f9935-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="f9935-137">Określanie nazw zestawów</span><span class="sxs-lookup"><span data-stu-id="f9935-137">Specifying assembly names</span></span>

<span data-ttu-id="f9935-138">Minimalnymi informacjami wymaganymi w specyfikacji nazwy zestawu jest nazwa tekstowa (identyfikator) zestawu.</span><span class="sxs-lookup"><span data-stu-id="f9935-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="f9935-139">Identyfikator można obsłużyć rozdzielaną przecinkami listą par właściwości/wartości, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f9935-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="f9935-140">Nazewnictwo identyfikatorów powinno być zgodne z regułami dotyczącymi nazewnictwa plików.</span><span class="sxs-lookup"><span data-stu-id="f9935-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="f9935-141">W IDENTYFIKATORze nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="f9935-141">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="f9935-142">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="f9935-142">Property name</span></span>|<span data-ttu-id="f9935-143">Opis</span><span class="sxs-lookup"><span data-stu-id="f9935-143">Description</span></span>|<span data-ttu-id="f9935-144">Dozwolone wartości</span><span class="sxs-lookup"><span data-stu-id="f9935-144">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="f9935-145">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="f9935-145">**Version**</span></span>|<span data-ttu-id="f9935-146">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="f9935-146">Assembly version number</span></span>|<span data-ttu-id="f9935-147">*Główna. pomocnicza. kompilacja. poprawka*, gdzie *główna*, *pomocnicza*, *kompilacja*i *poprawka* są liczbami całkowitymi z zakresu od 0 do 65535 włącznie.</span><span class="sxs-lookup"><span data-stu-id="f9935-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="f9935-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="f9935-148">**PublicKey**</span></span>|<span data-ttu-id="f9935-149">Pełny klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="f9935-149">Full public key</span></span>|<span data-ttu-id="f9935-150">Wartość ciągu pełnego klucza publicznego w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="f9935-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="f9935-151">Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.</span><span class="sxs-lookup"><span data-stu-id="f9935-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="f9935-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="f9935-152">**PublicKeyToken**</span></span>|<span data-ttu-id="f9935-153">Token klucza publicznego (skrót 8-bajtowy pełnego klucza publicznego)</span><span class="sxs-lookup"><span data-stu-id="f9935-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="f9935-154">Wartość ciągu tokenu klucza publicznego w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="f9935-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="f9935-155">Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.</span><span class="sxs-lookup"><span data-stu-id="f9935-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="f9935-156">**Dziedzinie**</span><span class="sxs-lookup"><span data-stu-id="f9935-156">**Culture**</span></span>|<span data-ttu-id="f9935-157">Kultura zestawu</span><span class="sxs-lookup"><span data-stu-id="f9935-157">Assembly culture</span></span>|<span data-ttu-id="f9935-158">Kultura zestawu w formacie RFC-1766 lub "neutralna" dla zestawów niezależnych od języka (niesatelity).</span><span class="sxs-lookup"><span data-stu-id="f9935-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="f9935-159">**Niestandardowy**</span><span class="sxs-lookup"><span data-stu-id="f9935-159">**Custom**</span></span>|<span data-ttu-id="f9935-160">Niestandardowy duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="f9935-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="f9935-161">Jest to obecnie używane tylko w zestawach wygenerowanych przez [Generator obrazu natywnego (Ngen)](../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="f9935-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="f9935-162">Niestandardowy ciąg używany przez Narzędzie Generator obrazu macierzystego do powiadamiania pamięci podręcznej zestawów, że instalowany zestaw jest obrazem natywnym i dlatego jest instalowany w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="f9935-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="f9935-163">Nazywana również ciągiem zap.</span><span class="sxs-lookup"><span data-stu-id="f9935-163">Also called a zap string.</span></span>|

<span data-ttu-id="f9935-164">W poniższym przykładzie pokazano element **AssemblyName** dla jednoplikowego zestawu z domyślną kulturą.</span><span class="sxs-lookup"><span data-stu-id="f9935-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="f9935-165">W poniższym przykładzie pokazano w pełni określone odwołanie do zestawu o silnej nazwie z kulturą "pl".</span><span class="sxs-lookup"><span data-stu-id="f9935-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="f9935-166">W poniższych przykładach pokazano częściowo określony element **AssemblyName**, który może być spełniony przez silną lub jednoplikowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="f9935-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="f9935-167">Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez zestaw po prostu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="f9935-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="f9935-168">Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez silnie nazwany zestaw.</span><span class="sxs-lookup"><span data-stu-id="f9935-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="f9935-169">Określanie typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="f9935-169">Specifying generic types</span></span>

<span data-ttu-id="f9935-170">SimpleTypeSpec\`numer reprezentuje otwarty typ ogólny z od 1 do *n* parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="f9935-170">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="f9935-171">Aby na przykład uzyskać odwołanie do\<listy otwartych typów ogólnych T> lub zamkniętego ciągu listy\<typów ogólnych>, użyj ``Type.GetType("System.Collections.Generic.List`1")`` , aby uzyskać odwołanie do słownika\<typu ogólnego TKey, TValue>, użyj. ``Type.GetType("System.Collections.Generic.Dictionary`2")``</span><span class="sxs-lookup"><span data-stu-id="f9935-171">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="f9935-172">Określanie wskaźników</span><span class="sxs-lookup"><span data-stu-id="f9935-172">Specifying pointers</span></span>

<span data-ttu-id="f9935-173">SimpleTypeSpec \* reprezentuje niezarządzany wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="f9935-173">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="f9935-174">Na przykład aby uzyskać wskaźnik do typu MyType, użyj `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="f9935-174">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="f9935-175">Aby uzyskać wskaźnik do wskaźnika do typu MyType, użyj `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="f9935-175">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="f9935-176">Określanie odwołań</span><span class="sxs-lookup"><span data-stu-id="f9935-176">Specifying references</span></span>

<span data-ttu-id="f9935-177">SimpleTypeSpec & reprezentuje zarządzany wskaźnik lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="f9935-177">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="f9935-178">Na przykład aby uzyskać odwołanie do typu MyType, użyj `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="f9935-178">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="f9935-179">Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania są ograniczone do jednego poziomu.</span><span class="sxs-lookup"><span data-stu-id="f9935-179">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="f9935-180">Określanie tablic</span><span class="sxs-lookup"><span data-stu-id="f9935-180">Specifying arrays</span></span>

<span data-ttu-id="f9935-181">W BNF gramatyki ReflectionEmitDimension dotyczy tylko niekompletnych definicji typów pobranych przy <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>użyciu.</span><span class="sxs-lookup"><span data-stu-id="f9935-181">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f9935-182">Niekompletne definicje typów <xref:System.Reflection.Emit.TypeBuilder> są obiektami zbudowanymi przy <xref:System.Reflection.Emit?displayProperty=nameWithType> użyciu <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> polecenia, ale nie zostały wywołane.</span><span class="sxs-lookup"><span data-stu-id="f9935-182">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="f9935-183">ReflectionDimension można użyć do pobrania dowolnej definicji typu, która została ukończona, czyli typu, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="f9935-183">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="f9935-184">Tablice są dostępne w odbiciu, określając rangę tablicy:</span><span class="sxs-lookup"><span data-stu-id="f9935-184">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="f9935-185">`Type.GetType("MyArray[]")`Pobiera tablicę o pojedynczym wymiarze z dolną granicą 0.</span><span class="sxs-lookup"><span data-stu-id="f9935-185">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="f9935-186">`Type.GetType("MyArray[*]")`Pobiera tablicę o pojedynczym wymiarze z nieznanym dolnym granicą.</span><span class="sxs-lookup"><span data-stu-id="f9935-186">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="f9935-187">`Type.GetType("MyArray[][]")`Pobiera tablicę dwuwymiarową tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9935-187">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="f9935-188">`Type.GetType("MyArray[*,*]")`i `Type.GetType("MyArray[,]")` pobiera prostokątną dwuwymiarową tablicę z nieznanymi dolnymi granicami.</span><span class="sxs-lookup"><span data-stu-id="f9935-188">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="f9935-189">Należy pamiętać, że z punktu `MyArray[] != MyArray[*]`widzenia środowiska uruchomieniowego, ale dla tablic wielowymiarowych, dwie notacji są równoważne.</span><span class="sxs-lookup"><span data-stu-id="f9935-189">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="f9935-190">Oznacza to, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` że program zwraca **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="f9935-190">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="f9935-191">Dla **ModuleBuilder. GetType** `MyArray[0..5]` wskazuje tablicę jednowymiarową z rozmiarem 6, dolną granicą 0.</span><span class="sxs-lookup"><span data-stu-id="f9935-191">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="f9935-192">`MyArray[4…]`wskazuje tablicę z jednym wymiarem o nieznanym rozmiarze i dolną granicę 4.</span><span class="sxs-lookup"><span data-stu-id="f9935-192">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="f9935-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9935-193">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="f9935-194">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="f9935-194">Viewing Type Information</span></span>](viewing-type-information.md)
