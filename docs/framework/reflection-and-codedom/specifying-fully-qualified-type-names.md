---
title: Określanie w pełni kwalifikowanych nazw typów
description: Aby uzyskać prawidłowe dane wejściowe operacji odbicia, należy użyć w pełni kwalifikowanych nazw typów, które mają specyfikacje nazw zestawów, specyfikacje przestrzeni nazw i nazwy typów.
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
ms.openlocfilehash: ff33b6abd31a82c6b80aa794564c5c48648cde63
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865232"
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="03f93-103">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="03f93-103">Specifying fully qualified type names</span></span>

<span data-ttu-id="03f93-104">Musisz określić nazwy typów, aby mieć prawidłowe dane wejściowe różnych operacji odbicia.</span><span class="sxs-lookup"><span data-stu-id="03f93-104">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="03f93-105">W pełni kwalifikowana nazwa typu zawiera specyfikację nazwy zestawu, specyfikację przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="03f93-105">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="03f93-106">Specyfikacje nazw typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType> , <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType> , <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> , i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="03f93-106">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>

## <a name="grammar-for-type-names"></a><span data-ttu-id="03f93-107">Gramatyka nazw typów</span><span class="sxs-lookup"><span data-stu-id="03f93-107">Grammar for type names</span></span>

 <span data-ttu-id="03f93-108">Gramatyka definiuje składnię języków formalnych.</span><span class="sxs-lookup"><span data-stu-id="03f93-108">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="03f93-109">W poniższej tabeli wymieniono reguły leksykalne opisujące sposób rozpoznawania prawidłowych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="03f93-109">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="03f93-110">W przypadku terminali (te elementy, które nie są jeszcze możliwe do zredukowania), są wyświetlane wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="03f93-110">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="03f93-111">Nieterminale (te elementy, które są dalsze możliwe do zredukowania) są wyświetlane w postaci ciągów z rozróżnianą wielkością liter lub z pojedynczą cudzysłowem, ale pojedynczy cudzysłów (') nie jest częścią samej składni.</span><span class="sxs-lookup"><span data-stu-id="03f93-111">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="03f93-112">Znak potoku (&#124;) oznacza reguły mające reguły subrules.</span><span class="sxs-lookup"><span data-stu-id="03f93-112">The pipe character (&#124;) denotes rules that have subrules.</span></span>

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

## <a name="specifying-special-characters"></a><span data-ttu-id="03f93-113">Określanie znaków specjalnych</span><span class="sxs-lookup"><span data-stu-id="03f93-113">Specifying special characters</span></span>

<span data-ttu-id="03f93-114">W nazwie typu identyfikator to dowolna prawidłowa nazwa określona przez reguły języka.</span><span class="sxs-lookup"><span data-stu-id="03f93-114">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>

<span data-ttu-id="03f93-115">Użyj ukośnika odwrotnego ( \\ ) jako znaku ucieczki, aby oddzielić następujące tokeny, gdy są używane jako część identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="03f93-115">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>

|<span data-ttu-id="03f93-116">Token</span><span class="sxs-lookup"><span data-stu-id="03f93-116">Token</span></span>|<span data-ttu-id="03f93-117">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="03f93-117">Meaning</span></span>|
|-----------|-------------|
|<span data-ttu-id="03f93-118">\\,</span><span class="sxs-lookup"><span data-stu-id="03f93-118">\\,</span></span>|<span data-ttu-id="03f93-119">Separator zestawu.</span><span class="sxs-lookup"><span data-stu-id="03f93-119">Assembly separator.</span></span>|
|\\+|<span data-ttu-id="03f93-120">Zagnieżdżony Separator typu.</span><span class="sxs-lookup"><span data-stu-id="03f93-120">Nested type separator.</span></span>|
|\\&|<span data-ttu-id="03f93-121">Typ referencyjny.</span><span class="sxs-lookup"><span data-stu-id="03f93-121">Reference type.</span></span>|
|\\*|<span data-ttu-id="03f93-122">Typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="03f93-122">Pointer type.</span></span>|
|<span data-ttu-id="03f93-123">\\[</span><span class="sxs-lookup"><span data-stu-id="03f93-123">\\[</span></span>|<span data-ttu-id="03f93-124">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="03f93-124">Array dimension delimiter.</span></span>|
|<span data-ttu-id="03f93-125">\\]</span><span class="sxs-lookup"><span data-stu-id="03f93-125">\\]</span></span>|<span data-ttu-id="03f93-126">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="03f93-126">Array dimension delimiter.</span></span>|
|<span data-ttu-id="03f93-127">\\.</span><span class="sxs-lookup"><span data-stu-id="03f93-127">\\.</span></span>|<span data-ttu-id="03f93-128">Użyj ukośnika odwrotnego przed kropką, tylko jeśli okres jest używany w specyfikacji tablicy.</span><span class="sxs-lookup"><span data-stu-id="03f93-128">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="03f93-129">Okresy w NamespaceSpec nie przyjmują ukośnika odwrotnego.</span><span class="sxs-lookup"><span data-stu-id="03f93-129">Periods in NamespaceSpec do not take the backslash.</span></span>|
|<span data-ttu-id="03f93-130">\\\|Ukośnik odwrotny, gdy jest wymagany jako literał ciągu.</span><span class="sxs-lookup"><span data-stu-id="03f93-130">\\\|Backslash when needed as a string literal.</span></span>|

<span data-ttu-id="03f93-131">Należy pamiętać, że we wszystkich składnikach TypeSpec z wyjątkiem AssemblyNameSpec, spacje są istotne.</span><span class="sxs-lookup"><span data-stu-id="03f93-131">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="03f93-132">W AssemblyNameSpec, spacje przed separatorem ', ' są istotne, ale spacje po separatorze ', ' są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="03f93-132">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>

<span data-ttu-id="03f93-133">Klasy odbicia, takie jak <xref:System.Type.FullName%2A?displayProperty=nameWithType> , zwracają nazwę zniekształcona, aby można było użyć zwracanej nazwy w wywołaniu do <xref:System.Type.GetType%2A> , jako w `MyType.GetType(myType.FullName)` .</span><span class="sxs-lookup"><span data-stu-id="03f93-133">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>

<span data-ttu-id="03f93-134">Na przykład w pełni kwalifikowana nazwa dla typu może być `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly` .</span><span class="sxs-lookup"><span data-stu-id="03f93-134">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>

<span data-ttu-id="03f93-135">Jeśli przestrzeń nazw była `Ozzy.Out+Back` , znak plus musi być poprzedzony ukośnikiem odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="03f93-135">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="03f93-136">W przeciwnym razie Analizator interpretuje go jako separator zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="03f93-136">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="03f93-137">Odbicie emituje ten ciąg jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly` .</span><span class="sxs-lookup"><span data-stu-id="03f93-137">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>

## <a name="specifying-assembly-names"></a><span data-ttu-id="03f93-138">Określanie nazw zestawów</span><span class="sxs-lookup"><span data-stu-id="03f93-138">Specifying assembly names</span></span>

<span data-ttu-id="03f93-139">Minimalnymi informacjami wymaganymi w specyfikacji nazwy zestawu jest nazwa tekstowa (identyfikator) zestawu.</span><span class="sxs-lookup"><span data-stu-id="03f93-139">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="03f93-140">Identyfikator można obsłużyć rozdzielaną przecinkami listą par właściwości/wartości, zgodnie z opisem w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="03f93-140">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="03f93-141">Nazewnictwo identyfikatorów powinno być zgodne z regułami dotyczącymi nazewnictwa plików.</span><span class="sxs-lookup"><span data-stu-id="03f93-141">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="03f93-142">W IDENTYFIKATORze nie jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="03f93-142">The IDENTIFIER is case-insensitive.</span></span>

|<span data-ttu-id="03f93-143">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="03f93-143">Property name</span></span>|<span data-ttu-id="03f93-144">Opis</span><span class="sxs-lookup"><span data-stu-id="03f93-144">Description</span></span>|<span data-ttu-id="03f93-145">Dozwolone wartości</span><span class="sxs-lookup"><span data-stu-id="03f93-145">Allowable values</span></span>|
|-------------------|-----------------|----------------------|
|<span data-ttu-id="03f93-146">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="03f93-146">**Version**</span></span>|<span data-ttu-id="03f93-147">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="03f93-147">Assembly version number</span></span>|<span data-ttu-id="03f93-148">*Główna. pomocnicza. kompilacja. poprawka*, gdzie *główna*, *pomocnicza*, *kompilacja*i *poprawka* są liczbami całkowitymi z zakresu od 0 do 65535 włącznie.</span><span class="sxs-lookup"><span data-stu-id="03f93-148">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|
|<span data-ttu-id="03f93-149">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="03f93-149">**PublicKey**</span></span>|<span data-ttu-id="03f93-150">Pełny klucz publiczny</span><span class="sxs-lookup"><span data-stu-id="03f93-150">Full public key</span></span>|<span data-ttu-id="03f93-151">Wartość ciągu pełnego klucza publicznego w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="03f93-151">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="03f93-152">Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.</span><span class="sxs-lookup"><span data-stu-id="03f93-152">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="03f93-153">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="03f93-153">**PublicKeyToken**</span></span>|<span data-ttu-id="03f93-154">Token klucza publicznego (skrót 8-bajtowy pełnego klucza publicznego)</span><span class="sxs-lookup"><span data-stu-id="03f93-154">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="03f93-155">Wartość ciągu tokenu klucza publicznego w formacie szesnastkowym.</span><span class="sxs-lookup"><span data-stu-id="03f93-155">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="03f93-156">Określ odwołanie o wartości null (**Nothing** w Visual Basic), aby jawnie wskazać prywatny zestaw.</span><span class="sxs-lookup"><span data-stu-id="03f93-156">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|
|<span data-ttu-id="03f93-157">**Kultura**</span><span class="sxs-lookup"><span data-stu-id="03f93-157">**Culture**</span></span>|<span data-ttu-id="03f93-158">Kultura zestawu</span><span class="sxs-lookup"><span data-stu-id="03f93-158">Assembly culture</span></span>|<span data-ttu-id="03f93-159">Kultura zestawu w formacie RFC-1766 lub "neutralna" dla zestawów niezależnych od języka (niesatelity).</span><span class="sxs-lookup"><span data-stu-id="03f93-159">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|
|<span data-ttu-id="03f93-160">**Niestandardowe**</span><span class="sxs-lookup"><span data-stu-id="03f93-160">**Custom**</span></span>|<span data-ttu-id="03f93-161">Niestandardowy duży obiekt binarny (BLOB).</span><span class="sxs-lookup"><span data-stu-id="03f93-161">Custom binary large object (BLOB).</span></span> <span data-ttu-id="03f93-162">Jest to obecnie używane tylko w zestawach wygenerowanych przez [Generator obrazu natywnego (Ngen)](../tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="03f93-162">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="03f93-163">Niestandardowy ciąg używany przez Narzędzie Generator obrazu macierzystego do powiadamiania pamięci podręcznej zestawów, że instalowany zestaw jest obrazem natywnym i dlatego jest instalowany w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="03f93-163">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="03f93-164">Nazywana również ciągiem zap.</span><span class="sxs-lookup"><span data-stu-id="03f93-164">Also called a zap string.</span></span>|

<span data-ttu-id="03f93-165">W poniższym przykładzie pokazano element **AssemblyName** dla jednoplikowego zestawu z domyślną kulturą.</span><span class="sxs-lookup"><span data-stu-id="03f93-165">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>

```csharp
com.microsoft.crypto, Culture=""
```

<span data-ttu-id="03f93-166">W poniższym przykładzie pokazano w pełni określone odwołanie do zestawu o silnej nazwie z kulturą "pl".</span><span class="sxs-lookup"><span data-stu-id="03f93-166">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>

```csharp
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

<span data-ttu-id="03f93-167">W poniższych przykładach pokazano częściowo określony element **AssemblyName**, który może być spełniony przez silną lub jednoplikowy zestaw.</span><span class="sxs-lookup"><span data-stu-id="03f93-167">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>

```csharp
com.microsoft.crypto
com.microsoft.crypto, Culture=""
com.microsoft.crypto, Culture=en
```

<span data-ttu-id="03f93-168">Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez zestaw po prostu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="03f93-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=null
com.microsoft.crypto, Culture=en, PublicKeyToken=null
```

<span data-ttu-id="03f93-169">Poniższe przykłady pokazują częściowo określony element **AssemblyName**, który musi być spełniony przez silnie nazwany zestaw.</span><span class="sxs-lookup"><span data-stu-id="03f93-169">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>

```csharp
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,
    Version=1.0.0.0
```

## <a name="specifying-generic-types"></a><span data-ttu-id="03f93-170">Określanie typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="03f93-170">Specifying generic types</span></span>

<span data-ttu-id="03f93-171">SimpleTypeSpec \` numer reprezentuje otwarty typ ogólny z od 1 do *n* parametrów typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="03f93-171">SimpleTypeSpec\`NUMBER represents an open generic type with from 1 to *n* generic type parameters.</span></span> <span data-ttu-id="03f93-172">Aby na przykład uzyskać odwołanie do listy otwartych typów ogólnych \<T> lub zamkniętej listy typów ogólnych \<String> , użyj parametru, ``Type.GetType("System.Collections.Generic.List`1")`` Aby uzyskać odwołanie do słownika typu ogólnego \<TKey,TValue> , użyj ``Type.GetType("System.Collections.Generic.Dictionary`2")`` .</span><span class="sxs-lookup"><span data-stu-id="03f93-172">For example, to get reference to the open generic type List\<T> or the closed generic type List\<String>, use ``Type.GetType("System.Collections.Generic.List`1")`` To get a reference to the generic type Dictionary\<TKey,TValue>, use ``Type.GetType("System.Collections.Generic.Dictionary`2")``.</span></span>

## <a name="specifying-pointers"></a><span data-ttu-id="03f93-173">Określanie wskaźników</span><span class="sxs-lookup"><span data-stu-id="03f93-173">Specifying pointers</span></span>

<span data-ttu-id="03f93-174">SimpleTypeSpec \* reprezentuje niezarządzany wskaźnik.</span><span class="sxs-lookup"><span data-stu-id="03f93-174">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="03f93-175">Na przykład aby uzyskać wskaźnik do typu MyType, użyj `Type.GetType("MyType*")` .</span><span class="sxs-lookup"><span data-stu-id="03f93-175">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="03f93-176">Aby uzyskać wskaźnik do wskaźnika do typu MyType, użyj `Type.GetType("MyType**")` .</span><span class="sxs-lookup"><span data-stu-id="03f93-176">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>

## <a name="specifying-references"></a><span data-ttu-id="03f93-177">Określanie odwołań</span><span class="sxs-lookup"><span data-stu-id="03f93-177">Specifying references</span></span>

<span data-ttu-id="03f93-178">SimpleTypeSpec & reprezentuje zarządzany wskaźnik lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="03f93-178">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="03f93-179">Na przykład aby uzyskać odwołanie do typu MyType, użyj `Type.GetType("MyType &")` .</span><span class="sxs-lookup"><span data-stu-id="03f93-179">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="03f93-180">Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania są ograniczone do jednego poziomu.</span><span class="sxs-lookup"><span data-stu-id="03f93-180">Note that unlike pointers, references are limited to one level.</span></span>

## <a name="specifying-arrays"></a><span data-ttu-id="03f93-181">Określanie tablic</span><span class="sxs-lookup"><span data-stu-id="03f93-181">Specifying arrays</span></span>

<span data-ttu-id="03f93-182">W BNF gramatyki ReflectionEmitDimension dotyczy tylko niekompletnych definicji typów pobranych przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="03f93-182">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="03f93-183">Niekompletne definicje typów są <xref:System.Reflection.Emit.TypeBuilder> obiektami zbudowanymi przy użyciu polecenia <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie zostały wywołane.</span><span class="sxs-lookup"><span data-stu-id="03f93-183">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="03f93-184">ReflectionDimension można użyć do pobrania dowolnej definicji typu, która została ukończona, czyli typu, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="03f93-184">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>

<span data-ttu-id="03f93-185">Tablice są dostępne w odbiciu, określając rangę tablicy:</span><span class="sxs-lookup"><span data-stu-id="03f93-185">Arrays are accessed in reflection by specifying the rank of the array:</span></span>

- <span data-ttu-id="03f93-186">`Type.GetType("MyArray[]")`Pobiera tablicę o pojedynczym wymiarze z dolną granicą 0.</span><span class="sxs-lookup"><span data-stu-id="03f93-186">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>

- <span data-ttu-id="03f93-187">`Type.GetType("MyArray[*]")`Pobiera tablicę o pojedynczym wymiarze z nieznanym dolnym granicą.</span><span class="sxs-lookup"><span data-stu-id="03f93-187">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>
- <span data-ttu-id="03f93-188">`Type.GetType("MyArray[][]")`Pobiera tablicę dwuwymiarową tablicy.</span><span class="sxs-lookup"><span data-stu-id="03f93-188">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>

- <span data-ttu-id="03f93-189">`Type.GetType("MyArray[*,*]")`i `Type.GetType("MyArray[,]")` Pobiera prostokątną dwuwymiarową tablicę z nieznanymi dolnymi granicami.</span><span class="sxs-lookup"><span data-stu-id="03f93-189">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>

<span data-ttu-id="03f93-190">Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]` ale dla tablic wielowymiarowych, dwie notacji są równoważne.</span><span class="sxs-lookup"><span data-stu-id="03f93-190">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="03f93-191">Oznacza to, że program `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` zwraca **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="03f93-191">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>

<span data-ttu-id="03f93-192">Dla **ModuleBuilder. GetType** `MyArray[0..5]` wskazuje tablicę jednowymiarową z rozmiarem 6, dolną granicą 0.</span><span class="sxs-lookup"><span data-stu-id="03f93-192">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="03f93-193">`MyArray[4…]`wskazuje tablicę z jednym wymiarem o nieznanym rozmiarze i dolną granicę 4.</span><span class="sxs-lookup"><span data-stu-id="03f93-193">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="03f93-194">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="03f93-194">See also</span></span>

- <xref:System.Reflection.AssemblyName>
- <xref:System.Reflection.Emit.ModuleBuilder>
- <xref:System.Reflection.Emit.TypeBuilder>
- <xref:System.Type.FullName%2A?displayProperty=nameWithType>
- <xref:System.Type.GetType%2A?displayProperty=nameWithType>
- <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>
- [<span data-ttu-id="03f93-195">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="03f93-195">Viewing Type Information</span></span>](viewing-type-information.md)
