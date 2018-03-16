---
title: "Określanie w pełni kwalifikowanych nazw typów"
ms.custom: 
ms.date: 03/14/2018
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e31e6e0284de44768b2faad7bcf84d5be343e479
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="34b54-102">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="34b54-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="34b54-103">Należy określić nazwy typów ma prawidłową wartość wejściową do różnych operacji odbicia.</span><span class="sxs-lookup"><span data-stu-id="34b54-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="34b54-104">Nazwa FQDN typu, który składa się z specyfikacja nazwy zestawu specyfikacji przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="34b54-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="34b54-105">Specyfikacje nazwy typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34b54-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="grammar-for-type-names"></a><span data-ttu-id="34b54-106">Gramatyka dla nazw typów</span><span class="sxs-lookup"><span data-stu-id="34b54-106">Grammar for Type Names</span></span>  
 <span data-ttu-id="34b54-107">Gramatyka definiuje składni posiadanie języków.</span><span class="sxs-lookup"><span data-stu-id="34b54-107">The grammar defines the syntax of formal languages.</span></span> <span data-ttu-id="34b54-108">W poniższej tabeli wymieniono leksykalne reguły, które opisują jak rozpoznać prawidłowych danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="34b54-108">The following table lists lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="34b54-109">Terminali (tych elementów, które nie są dodatkowo możliwym do zredukowania) są wyświetlane w wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="34b54-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="34b54-110">Symboli nieterminalnych (tych elementów, które są dodatkowo możliwym do zredukowania) są wyświetlane w ciągach wielkie i małe litery, lub oddzielnie w cudzysłowie, ale apostrofu (') nie jest częścią sama składnia.</span><span class="sxs-lookup"><span data-stu-id="34b54-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="34b54-111">Znaku kreski pionowej (&#124;) oznacza reguły, które mają reguł podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="34b54-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  

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
    | ArrayTypeSpec
    | TypeName
    ;

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

## <a name="specifying-special-characters"></a><span data-ttu-id="34b54-112">Określanie znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="34b54-112">Specifying Special Characters</span></span>  
 <span data-ttu-id="34b54-113">W nazwie typu identyfikator jest żadnych prawidłowej nazwy określane przez reguły języka.</span><span class="sxs-lookup"><span data-stu-id="34b54-113">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="34b54-114">Użyj kreska ułamkowa odwrócona (\\) jako znaku ucieczki w celu rozdzielenia następujących tokenów, gdy jest używany jako część IDENTYFIKATORA.</span><span class="sxs-lookup"><span data-stu-id="34b54-114">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="34b54-115">Token</span><span class="sxs-lookup"><span data-stu-id="34b54-115">Token</span></span>|<span data-ttu-id="34b54-116">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="34b54-116">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="34b54-117">\\,</span><span class="sxs-lookup"><span data-stu-id="34b54-117">\\,</span></span>|<span data-ttu-id="34b54-118">Separator zestawu.</span><span class="sxs-lookup"><span data-stu-id="34b54-118">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="34b54-119">Separator typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="34b54-119">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="34b54-120">Typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="34b54-120">Reference type.</span></span>|  
|\\*|<span data-ttu-id="34b54-121">Typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="34b54-121">Pointer type.</span></span>|  
|<span data-ttu-id="34b54-122">\\[</span><span class="sxs-lookup"><span data-stu-id="34b54-122">\\[</span></span>|<span data-ttu-id="34b54-123">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-123">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="34b54-124">\\]</span><span class="sxs-lookup"><span data-stu-id="34b54-124">\\]</span></span>|<span data-ttu-id="34b54-125">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-125">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="34b54-126">\\.</span><span class="sxs-lookup"><span data-stu-id="34b54-126">\\.</span></span>|<span data-ttu-id="34b54-127">Użyj ukośniku odwrotnym przed kropką tylko wtedy, gdy okres jest używany w specyfikacji tablicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-127">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="34b54-128">Kropki w NamespaceSpec nie przyjmują ukośniku odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="34b54-128">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|<span data-ttu-id="34b54-129">\\\|Ukośnik odwrotny, w razie potrzeby jako ciąg literału.</span><span class="sxs-lookup"><span data-stu-id="34b54-129">\\\|Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="34b54-130">Należy pamiętać, że we wszystkich składnikach elementu TypeSpec z wyjątkiem AssemblyNameSpec mają zastosowanie spacji.</span><span class="sxs-lookup"><span data-stu-id="34b54-130">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="34b54-131">W AssemblyNameSpec mają zastosowanie spacji przed separatorem ',', ale spacje po separatorze "," są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="34b54-131">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="34b54-132">Odbicie klas, takich jak <xref:System.Type.FullName%2A?displayProperty=nameWithType>, wróć nazwa zniekształcona zwrócona nazwa może być używana w wywołaniu <xref:System.Type.GetType%2A>, jak w `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="34b54-132">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="34b54-133">Na przykład może być w pełni kwalifikowana nazwa typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="34b54-133">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="34b54-134">Jeśli przestrzeń nazw zostały `Ozzy.Out+Back`, a następnie znak plus musi być poprzedzony ukośnikiem.</span><span class="sxs-lookup"><span data-stu-id="34b54-134">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="34b54-135">W przeciwnym razie analizator może zinterpretować go jako separator zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="34b54-135">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="34b54-136">Odbicie emituje tego ciągu jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="34b54-136">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="34b54-137">Określanie nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="34b54-137">Specifying Assembly Names</span></span>  
 <span data-ttu-id="34b54-138">Minimalną ilość informacji w specyfikacji nazwy zestawu wymagany jest nazwą tekstową (IDENTIFIER) zestawu.</span><span class="sxs-lookup"><span data-stu-id="34b54-138">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="34b54-139">Rozdzielana przecinkami lista par właściwości i wartości zgodnie z opisem w poniższej tabeli można wykonać identyfikator.</span><span class="sxs-lookup"><span data-stu-id="34b54-139">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="34b54-140">Identyfikator nazwy należy stosować reguły nazewnictwa plików.</span><span class="sxs-lookup"><span data-stu-id="34b54-140">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="34b54-141">Identyfikator jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="34b54-141">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="34b54-142">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="34b54-142">Property name</span></span>|<span data-ttu-id="34b54-143">Opis</span><span class="sxs-lookup"><span data-stu-id="34b54-143">Description</span></span>|<span data-ttu-id="34b54-144">Dopuszczalne wartości</span><span class="sxs-lookup"><span data-stu-id="34b54-144">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="34b54-145">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="34b54-145">**Version**</span></span>|<span data-ttu-id="34b54-146">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="34b54-146">Assembly version number</span></span>|<span data-ttu-id="34b54-147">*Główna.pomocnicza.kompilacja.poprawka*, gdzie *głównych*, *pomocnicza*, *kompilacji*, i *poprawki* są liczbami całkowitymi od 0 i 65535 włącznie.</span><span class="sxs-lookup"><span data-stu-id="34b54-147">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="34b54-148">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="34b54-148">**PublicKey**</span></span>|<span data-ttu-id="34b54-149">Klucz publiczny pełnej</span><span class="sxs-lookup"><span data-stu-id="34b54-149">Full public key</span></span>|<span data-ttu-id="34b54-150">Wartość pełnej publiczny klucz w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="34b54-150">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="34b54-151">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="34b54-151">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="34b54-152">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="34b54-152">**PublicKeyToken**</span></span>|<span data-ttu-id="34b54-153">Token klucza publicznego (8-bajtowych skrótu klucza publicznego pełna)</span><span class="sxs-lookup"><span data-stu-id="34b54-153">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="34b54-154">Wartość tokenu klucza publicznego w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="34b54-154">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="34b54-155">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="34b54-155">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="34b54-156">**Kultury**</span><span class="sxs-lookup"><span data-stu-id="34b54-156">**Culture**</span></span>|<span data-ttu-id="34b54-157">Kultura zestawu</span><span class="sxs-lookup"><span data-stu-id="34b54-157">Assembly culture</span></span>|<span data-ttu-id="34b54-158">Kultura zestawu w formacie RFC 1766 lub "neutralne" dla zestawów niezależny od języka (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="34b54-158">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="34b54-159">**Niestandardowy**</span><span class="sxs-lookup"><span data-stu-id="34b54-159">**Custom**</span></span>|<span data-ttu-id="34b54-160">Niestandardowe dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="34b54-160">Custom binary large object (BLOB).</span></span> <span data-ttu-id="34b54-161">To jest aktualnie używana tylko zestawów generowanych przez [Generator obrazu natywnego (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="34b54-161">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="34b54-162">Niestandardowy ciąg używany przez narzędzie Generator obrazu natywnego do powiadamiania pamięci podręcznej zestawów zestawu instalowany jest obrazu macierzystego czy w związku z tym ma zostać zainstalowany w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="34b54-162">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="34b54-163">Skrót ciągu zap.</span><span class="sxs-lookup"><span data-stu-id="34b54-163">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="34b54-164">W poniższym przykładzie przedstawiono **AssemblyName** po prostu nazwane zestawu z domyślną kulturę.</span><span class="sxs-lookup"><span data-stu-id="34b54-164">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="34b54-165">W poniższym przykładzie przedstawiono pełni podane odwołanie do zestawu o silnej nazwie z kulturą "en".</span><span class="sxs-lookup"><span data-stu-id="34b54-165">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="34b54-166">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, który może zostać wykonane przez silne lub po prostu nazwane zestawu.</span><span class="sxs-lookup"><span data-stu-id="34b54-166">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="34b54-167">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez po prostu nazwany zestaw.</span><span class="sxs-lookup"><span data-stu-id="34b54-167">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="34b54-168">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez zestaw o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="34b54-168">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="34b54-169">Określenie wskaźników</span><span class="sxs-lookup"><span data-stu-id="34b54-169">Specifying Pointers</span></span>  
 <span data-ttu-id="34b54-170">SimpleTypeSpec \* reprezentuje niezarządzanego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="34b54-170">SimpleTypeSpec\* represents an unmanaged pointer.</span></span> <span data-ttu-id="34b54-171">Na przykład otrzymywać wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="34b54-171">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="34b54-172">Aby otrzymywać wskaźnik na wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="34b54-172">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="34b54-173">Określanie odwołań</span><span class="sxs-lookup"><span data-stu-id="34b54-173">Specifying References</span></span>  
 <span data-ttu-id="34b54-174">SimpleTypeSpec & reprezentuje zarządzanych wskaźnik lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="34b54-174">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="34b54-175">Na przykład, aby pobrać odwołanie do typu Mojtyp, należy użyć `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="34b54-175">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="34b54-176">Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania mogą zawierać maksymalnie jeden poziom.</span><span class="sxs-lookup"><span data-stu-id="34b54-176">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="34b54-177">Określanie tablic</span><span class="sxs-lookup"><span data-stu-id="34b54-177">Specifying Arrays</span></span>  
 <span data-ttu-id="34b54-178">W gramatyka BNF ReflectionEmitDimension ma zastosowanie tylko do niekompletnego typu definicje pobrany przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34b54-178">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="34b54-179">Definicje niekompletnego typu <xref:System.Reflection.Emit.TypeBuilder> obiekty utworzone za pomocą <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na którym <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="34b54-179">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="34b54-180">ReflectionDimension można pobrać żadnych definicji typu, która została zakończona, oznacza to, typu, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="34b54-180">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="34b54-181">Tablice są dostępne w odbicia, określając rangą tablicy:</span><span class="sxs-lookup"><span data-stu-id="34b54-181">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="34b54-182">`Type.GetType("MyArray[]")` pobiera tablicy jednowymiarowej z 0 dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-182">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="34b54-183">`Type.GetType("MyArray[*]")` pobiera tablicy jednowymiarowej z nieznanego dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-183">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="34b54-184">`Type.GetType("MyArray[][]")` pobiera tablicy jest tablicą dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="34b54-184">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="34b54-185">`Type.GetType("MyArray[*,*]")` i `Type.GetType("MyArray[,]")` pobiera prostokątny tablicą dwuwymiarową z nieznanego dolne granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="34b54-185">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="34b54-186">Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]`, ale dla tablic wielowymiarowych są równoważne dwóch notacji.</span><span class="sxs-lookup"><span data-stu-id="34b54-186">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="34b54-187">Oznacza to `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` daje w wyniku **true**.</span><span class="sxs-lookup"><span data-stu-id="34b54-187">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="34b54-188">Aby uzyskać **ModuleBuilder.GetType**, `MyArray[0..5]` wskazuje tablicy jednowymiarowej, o rozmiarze 6 niższe powiązane 0.</span><span class="sxs-lookup"><span data-stu-id="34b54-188">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="34b54-189">`MyArray[4…]` Wskazuje jednowymiarowej tablicy o nieznanym rozmiarze i dolną granicę 4.</span><span class="sxs-lookup"><span data-stu-id="34b54-189">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34b54-190">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34b54-190">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="34b54-191">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="34b54-191">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
