---
title: "Określanie w pełni kwalifikowanych nazw typów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- reflection, fully qualified type names
- names [.NET Framework], assemblies
- tokens
- BNF
- assemblies [.NET Framework], names
- Backus-Naur form
- languages, BNF grammar
- fully qualified type names
- type names
- special characters
- IDENTIFIER
ms.assetid: d90b1e39-9115-4f2a-81c0-05e7e74e5580
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e19aebbeee7fd65e27704af49185a1b8d48b9639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="specifying-fully-qualified-type-names"></a><span data-ttu-id="78a4f-102">Określanie w pełni kwalifikowanych nazw typów</span><span class="sxs-lookup"><span data-stu-id="78a4f-102">Specifying Fully Qualified Type Names</span></span>
<span data-ttu-id="78a4f-103">Należy określić nazwy typów ma prawidłową wartość wejściową do różnych operacji odbicia.</span><span class="sxs-lookup"><span data-stu-id="78a4f-103">You must specify type names to have valid input to various reflection operations.</span></span> <span data-ttu-id="78a4f-104">Nazwa FQDN typu, który składa się z specyfikacja nazwy zestawu specyfikacji przestrzeni nazw i nazwę typu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-104">A fully qualified type name consists of an assembly name specification, a namespace specification, and a type name.</span></span> <span data-ttu-id="78a4f-105">Specyfikacje nazwy typów są używane przez metody takie jak <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, i <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78a4f-105">Type name specifications are used by methods such as <xref:System.Type.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Module.GetType%2A?displayProperty=nameWithType>, <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>, and <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="backus-naur-form-grammar-for-type-names"></a><span data-ttu-id="78a4f-106">Formularz Backus-Naur formularza gramatyki dla nazw typów</span><span class="sxs-lookup"><span data-stu-id="78a4f-106">Backus-Naur Form Grammar for Type Names</span></span>  
 <span data-ttu-id="78a4f-107">Formularz Backus-naur (BNF) definiuje składni posiadanie języków.</span><span class="sxs-lookup"><span data-stu-id="78a4f-107">The Backus-Naur form (BNF) defines the syntax of formal languages.</span></span> <span data-ttu-id="78a4f-108">W poniższej tabeli wymieniono reguły leksykalne BNF, które opisują jak rozpoznać prawidłowy wejściowy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-108">The following table lists BNF lexical rules that describe how to recognize a valid input.</span></span> <span data-ttu-id="78a4f-109">Terminali (tych elementów, które nie są dodatkowo możliwym do zredukowania) są wyświetlane w wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="78a4f-109">Terminals (those elements that are not further reducible) are shown in all uppercase letters.</span></span> <span data-ttu-id="78a4f-110">Symboli nieterminalnych (tych elementów, które są dodatkowo możliwym do zredukowania) są wyświetlane w ciągach wielkie i małe litery, lub oddzielnie w cudzysłowie, ale apostrofu (') nie jest częścią sama składnia.</span><span class="sxs-lookup"><span data-stu-id="78a4f-110">Nonterminals (those elements that are further reducible) are shown in mixed-case or singly quoted strings, but the single quote (') is not a part of the syntax itself.</span></span> <span data-ttu-id="78a4f-111">Znaku kreski pionowej (&#124;) określa reguły, które mają reguł podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="78a4f-111">The pipe character (&#124;) denotes rules that have subrules.</span></span>  
  
|<span data-ttu-id="78a4f-112">Gramatyka BNF z w pełni kwalifikowane nazwy typów</span><span class="sxs-lookup"><span data-stu-id="78a4f-112">BNF grammar of fully qualified type names</span></span>|  
|-----------------------------------------------|  
|<span data-ttu-id="78a4f-113">Element TypeSpec: = ReferenceTypeSpec</span><span class="sxs-lookup"><span data-stu-id="78a4f-113">TypeSpec                          :=   ReferenceTypeSpec</span></span><br /><br /> <span data-ttu-id="78a4f-114">&#124;     SimpleTypeSpec</span><span class="sxs-lookup"><span data-stu-id="78a4f-114">&#124;     SimpleTypeSpec</span></span>|  
|<span data-ttu-id="78a4f-115">ReferenceTypeSpec: = SimpleTypeSpec 'i'</span><span class="sxs-lookup"><span data-stu-id="78a4f-115">ReferenceTypeSpec            :=   SimpleTypeSpec '&'</span></span>|  
|<span data-ttu-id="78a4f-116">SimpleTypeSpec: = PointerTypeSpec</span><span class="sxs-lookup"><span data-stu-id="78a4f-116">SimpleTypeSpec                :=   PointerTypeSpec</span></span><br /><br /> <span data-ttu-id="78a4f-117">&#124;     ArrayTypeSpec</span><span class="sxs-lookup"><span data-stu-id="78a4f-117">&#124;     ArrayTypeSpec</span></span><br /><br /> <span data-ttu-id="78a4f-118">&#124;     Właściwość TypeName</span><span class="sxs-lookup"><span data-stu-id="78a4f-118">&#124;     TypeName</span></span>|  
|<span data-ttu-id="78a4f-119">PointerTypeSpec: = SimpleTypeSpec "*"</span><span class="sxs-lookup"><span data-stu-id="78a4f-119">PointerTypeSpec                :=   SimpleTypeSpec '*'</span></span>|  
|<span data-ttu-id="78a4f-120">ArrayTypeSpec: = SimpleTypeSpec [ReflectionDimension]</span><span class="sxs-lookup"><span data-stu-id="78a4f-120">ArrayTypeSpec                  :=   SimpleTypeSpec '[ReflectionDimension]'</span></span><br /><br /> <span data-ttu-id="78a4f-121">&#124;     SimpleTypeSpec [ReflectionEmitDimension]</span><span class="sxs-lookup"><span data-stu-id="78a4f-121">&#124;     SimpleTypeSpec '[ReflectionEmitDimension]'</span></span>|  
|<span data-ttu-id="78a4f-122">ReflectionDimension: = "*"</span><span class="sxs-lookup"><span data-stu-id="78a4f-122">ReflectionDimension           :=   '*'</span></span><br /><br /> <span data-ttu-id="78a4f-123">&#124;     ReflectionDimension ReflectionDimension ","</span><span class="sxs-lookup"><span data-stu-id="78a4f-123">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="78a4f-124">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="78a4f-124">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="78a4f-125">ReflectionEmitDimension: = "*"</span><span class="sxs-lookup"><span data-stu-id="78a4f-125">ReflectionEmitDimension    :=   '*'</span></span><br /><br /> <span data-ttu-id="78a4f-126">&#124;     Numer ".."</span><span class="sxs-lookup"><span data-stu-id="78a4f-126">&#124;     Number '..'</span></span> <span data-ttu-id="78a4f-127">Wartość liczbowa</span><span class="sxs-lookup"><span data-stu-id="78a4f-127">Number</span></span><br /><br /> <span data-ttu-id="78a4f-128">&#124;     Numer "..."</span><span class="sxs-lookup"><span data-stu-id="78a4f-128">&#124;     Number '…'</span></span><br /><br /> <span data-ttu-id="78a4f-129">&#124;     ReflectionDimension ReflectionDimension ","</span><span class="sxs-lookup"><span data-stu-id="78a4f-129">&#124;     ReflectionDimension ',' ReflectionDimension</span></span><br /><br /> <span data-ttu-id="78a4f-130">&#124;     NOTOKEN</span><span class="sxs-lookup"><span data-stu-id="78a4f-130">&#124;     NOTOKEN</span></span>|  
|<span data-ttu-id="78a4f-131">Liczba: = [0-9] +</span><span class="sxs-lookup"><span data-stu-id="78a4f-131">Number                            :=   [0-9]+</span></span>|  
|<span data-ttu-id="78a4f-132">Właściwość TypeName: = NamespaceTypeName</span><span class="sxs-lookup"><span data-stu-id="78a4f-132">TypeName                         :=   NamespaceTypeName</span></span><br /><br /> <span data-ttu-id="78a4f-133">&#124;     NamespaceTypeName AssemblyNameSpec ","</span><span class="sxs-lookup"><span data-stu-id="78a4f-133">&#124;     NamespaceTypeName ',' AssemblyNameSpec</span></span>|  
|<span data-ttu-id="78a4f-134">NamespaceTypeName: = NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="78a4f-134">NamespaceTypeName        :=   NestedTypeName</span></span><br /><br /> <span data-ttu-id="78a4f-135">&#124;     NamespaceSpec "." NestedTypeName</span><span class="sxs-lookup"><span data-stu-id="78a4f-135">&#124;     NamespaceSpec '.' NestedTypeName</span></span>|  
|<span data-ttu-id="78a4f-136">NestedTypeName: identyfikator =</span><span class="sxs-lookup"><span data-stu-id="78a4f-136">NestedTypeName               :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="78a4f-137">&#124;     NestedTypeName identyfikator "+"</span><span class="sxs-lookup"><span data-stu-id="78a4f-137">&#124;     NestedTypeName '+' IDENTIFIER</span></span>|  
|<span data-ttu-id="78a4f-138">NamespaceSpec: identyfikator =</span><span class="sxs-lookup"><span data-stu-id="78a4f-138">NamespaceSpec                 :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="78a4f-139">&#124;     NamespaceSpec "." IDENTYFIKATOR</span><span class="sxs-lookup"><span data-stu-id="78a4f-139">&#124;     NamespaceSpec '.' IDENTIFIER</span></span>|  
|<span data-ttu-id="78a4f-140">AssemblyNameSpec: identyfikator =</span><span class="sxs-lookup"><span data-stu-id="78a4f-140">AssemblyNameSpec           :=   IDENTIFIER</span></span><br /><br /> <span data-ttu-id="78a4f-141">&#124;     Identyfikator AssemblyProperties ","</span><span class="sxs-lookup"><span data-stu-id="78a4f-141">&#124;     IDENTIFIER ',' AssemblyProperties</span></span>|  
|<span data-ttu-id="78a4f-142">AssemblyProperties: = AssemblyProperty</span><span class="sxs-lookup"><span data-stu-id="78a4f-142">AssemblyProperties            :=   AssemblyProperty</span></span><br /><br /> <span data-ttu-id="78a4f-143">&#124;     AssemblyProperties AssemblyProperty ","</span><span class="sxs-lookup"><span data-stu-id="78a4f-143">&#124;     AssemblyProperties ',' AssemblyProperty</span></span>|  
|<span data-ttu-id="78a4f-144">AssemblyProperty: = AssemblyPropertyValue AssemblyPropertyName "="</span><span class="sxs-lookup"><span data-stu-id="78a4f-144">AssemblyProperty              :=   AssemblyPropertyName '=' AssemblyPropertyValue</span></span>|  
  
## <a name="specifying-special-characters"></a><span data-ttu-id="78a4f-145">Określanie znaki specjalne</span><span class="sxs-lookup"><span data-stu-id="78a4f-145">Specifying Special Characters</span></span>  
 <span data-ttu-id="78a4f-146">W nazwie typu identyfikator jest żadnych prawidłowej nazwy określane przez reguły języka.</span><span class="sxs-lookup"><span data-stu-id="78a4f-146">In a type name, IDENTIFIER is any valid name determined by the rules of a language.</span></span>  
  
 <span data-ttu-id="78a4f-147">Użyj kreska ułamkowa odwrócona (\\) jako znaku ucieczki w celu rozdzielenia następujących tokenów, gdy jest używany jako część IDENTYFIKATORA.</span><span class="sxs-lookup"><span data-stu-id="78a4f-147">Use the backslash (\\) as an escape character to separate the following tokens when used as part of IDENTIFIER.</span></span>  
  
|<span data-ttu-id="78a4f-148">Token</span><span class="sxs-lookup"><span data-stu-id="78a4f-148">Token</span></span>|<span data-ttu-id="78a4f-149">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="78a4f-149">Meaning</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="78a4f-150">\\,</span><span class="sxs-lookup"><span data-stu-id="78a4f-150">\\,</span></span>|<span data-ttu-id="78a4f-151">Separator zestawu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-151">Assembly separator.</span></span>|  
|\\+|<span data-ttu-id="78a4f-152">Separator typu zagnieżdżonego.</span><span class="sxs-lookup"><span data-stu-id="78a4f-152">Nested type separator.</span></span>|  
|\\&|<span data-ttu-id="78a4f-153">Typ odwołania.</span><span class="sxs-lookup"><span data-stu-id="78a4f-153">Reference type.</span></span>|  
|\\*|<span data-ttu-id="78a4f-154">Typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="78a4f-154">Pointer type.</span></span>|  
|<span data-ttu-id="78a4f-155">\\[</span><span class="sxs-lookup"><span data-stu-id="78a4f-155">\\[</span></span>|<span data-ttu-id="78a4f-156">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-156">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="78a4f-157">\\]</span><span class="sxs-lookup"><span data-stu-id="78a4f-157">\\]</span></span>|<span data-ttu-id="78a4f-158">Ogranicznik wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-158">Array dimension delimiter.</span></span>|  
|<span data-ttu-id="78a4f-159">\\.,</span><span class="sxs-lookup"><span data-stu-id="78a4f-159">\\.</span></span>|<span data-ttu-id="78a4f-160">Użyj ukośniku odwrotnym przed kropką tylko wtedy, gdy okres jest używany w specyfikacji tablicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-160">Use the backslash before a period only if the period is used in an array specification.</span></span> <span data-ttu-id="78a4f-161">Kropki w NamespaceSpec nie przyjmują ukośniku odwrotnym.</span><span class="sxs-lookup"><span data-stu-id="78a4f-161">Periods in NamespaceSpec do not take the backslash.</span></span>|  
|\\\|<span data-ttu-id="78a4f-162">Ukośnik odwrotny, w razie potrzeby jako ciąg literału.</span><span class="sxs-lookup"><span data-stu-id="78a4f-162">Backslash when needed as a string literal.</span></span>|  
  
 <span data-ttu-id="78a4f-163">Należy pamiętać, że we wszystkich składnikach elementu TypeSpec z wyjątkiem AssemblyNameSpec mają zastosowanie spacji.</span><span class="sxs-lookup"><span data-stu-id="78a4f-163">Note that in all TypeSpec components except AssemblyNameSpec, spaces are relevant.</span></span> <span data-ttu-id="78a4f-164">W AssemblyNameSpec mają zastosowanie spacji przed separatorem ',', ale spacje po separatorze "," są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="78a4f-164">In the AssemblyNameSpec, spaces before the ',' separator are relevant, but spaces after the ',' separator are ignored.</span></span>  
  
 <span data-ttu-id="78a4f-165">Odbicie klas, takich jak <xref:System.Type.FullName%2A?displayProperty=nameWithType>, wróć nazwa zniekształcona zwrócona nazwa może być używana w wywołaniu <xref:System.Type.GetType%2A>, jak w `MyType.GetType(myType.FullName)`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-165">Reflection classes, such as <xref:System.Type.FullName%2A?displayProperty=nameWithType>, return the mangled name so that the returned name can be used in a call to <xref:System.Type.GetType%2A>, as in `MyType.GetType(myType.FullName)`.</span></span>  
  
 <span data-ttu-id="78a4f-166">Na przykład może być w pełni kwalifikowana nazwa typu `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-166">For example, the fully qualified name for a type might be `Ozzy.OutBack.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
 <span data-ttu-id="78a4f-167">Jeśli przestrzeń nazw zostały `Ozzy.Out+Back`, a następnie znak plus musi być poprzedzony ukośnikiem.</span><span class="sxs-lookup"><span data-stu-id="78a4f-167">If the namespace were `Ozzy.Out+Back`, then the plus sign must be preceded by a backslash.</span></span> <span data-ttu-id="78a4f-168">W przeciwnym razie analizator może zinterpretować go jako separator zagnieżdżenia.</span><span class="sxs-lookup"><span data-stu-id="78a4f-168">Otherwise, the parser would interpret it as a nesting separator.</span></span> <span data-ttu-id="78a4f-169">Odbicie emituje tego ciągu jako `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-169">Reflection emits this string as `Ozzy.Out\+Back.Kangaroo+Wallaby,MyAssembly`.</span></span>  
  
## <a name="specifying-assembly-names"></a><span data-ttu-id="78a4f-170">Określanie nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="78a4f-170">Specifying Assembly Names</span></span>  
 <span data-ttu-id="78a4f-171">Minimalną ilość informacji w specyfikacji nazwy zestawu wymagany jest nazwą tekstową (IDENTIFIER) zestawu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-171">The minimum information required in an assembly name specification is the textual name (IDENTIFIER) of the assembly.</span></span> <span data-ttu-id="78a4f-172">Rozdzielana przecinkami lista par właściwości i wartości zgodnie z opisem w poniższej tabeli można wykonać identyfikator.</span><span class="sxs-lookup"><span data-stu-id="78a4f-172">You can follow the IDENTIFIER by a comma-separated list of property/value pairs as described in the following table.</span></span> <span data-ttu-id="78a4f-173">Identyfikator nazwy należy stosować reguły nazewnictwa plików.</span><span class="sxs-lookup"><span data-stu-id="78a4f-173">IDENTIFIER naming should follow the rules for file naming.</span></span> <span data-ttu-id="78a4f-174">Identyfikator jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="78a4f-174">The IDENTIFIER is case-insensitive.</span></span>  
  
|<span data-ttu-id="78a4f-175">Nazwa właściwości</span><span class="sxs-lookup"><span data-stu-id="78a4f-175">Property name</span></span>|<span data-ttu-id="78a4f-176">Opis</span><span class="sxs-lookup"><span data-stu-id="78a4f-176">Description</span></span>|<span data-ttu-id="78a4f-177">Dopuszczalne wartości</span><span class="sxs-lookup"><span data-stu-id="78a4f-177">Allowable values</span></span>|  
|-------------------|-----------------|----------------------|  
|<span data-ttu-id="78a4f-178">**Wersja**</span><span class="sxs-lookup"><span data-stu-id="78a4f-178">**Version**</span></span>|<span data-ttu-id="78a4f-179">Numer wersji zestawu</span><span class="sxs-lookup"><span data-stu-id="78a4f-179">Assembly version number</span></span>|<span data-ttu-id="78a4f-180">*Główna.pomocnicza.kompilacja.poprawka*, gdzie *głównych*, *pomocnicza*, *kompilacji*, i *poprawki* są liczbami całkowitymi od 0 i 65535 włącznie.</span><span class="sxs-lookup"><span data-stu-id="78a4f-180">*Major.Minor.Build.Revision*, where *Major*, *Minor*, *Build*, and *Revision* are integers between 0 and 65535 inclusive.</span></span>|  
|<span data-ttu-id="78a4f-181">**PublicKey**</span><span class="sxs-lookup"><span data-stu-id="78a4f-181">**PublicKey**</span></span>|<span data-ttu-id="78a4f-182">Klucz publiczny pełnej</span><span class="sxs-lookup"><span data-stu-id="78a4f-182">Full public key</span></span>|<span data-ttu-id="78a4f-183">Wartość pełnej publiczny klucz w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-183">String value of full public key in hexadecimal format.</span></span> <span data-ttu-id="78a4f-184">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="78a4f-184">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="78a4f-185">**PublicKeyToken**</span><span class="sxs-lookup"><span data-stu-id="78a4f-185">**PublicKeyToken**</span></span>|<span data-ttu-id="78a4f-186">Token klucza publicznego (8-bajtowych skrótu klucza publicznego pełna)</span><span class="sxs-lookup"><span data-stu-id="78a4f-186">Public key token (8-byte hash of the full public key)</span></span>|<span data-ttu-id="78a4f-187">Wartość tokenu klucza publicznego w formacie szesnastkowym ciągu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-187">String value of public key token in hexadecimal format.</span></span> <span data-ttu-id="78a4f-188">Określ odwołanie o wartości null (**nic** w języku Visual Basic) Aby jawnie wskazać zestaw prywatny.</span><span class="sxs-lookup"><span data-stu-id="78a4f-188">Specify a null reference (**Nothing** in Visual Basic) to explicitly indicate a private assembly.</span></span>|  
|<span data-ttu-id="78a4f-189">**Kultury**</span><span class="sxs-lookup"><span data-stu-id="78a4f-189">**Culture**</span></span>|<span data-ttu-id="78a4f-190">Kultura zestawu</span><span class="sxs-lookup"><span data-stu-id="78a4f-190">Assembly culture</span></span>|<span data-ttu-id="78a4f-191">Kultura zestawu w formacie RFC 1766 lub "neutralne" dla zestawów niezależny od języka (nonsatellite).</span><span class="sxs-lookup"><span data-stu-id="78a4f-191">Culture of the assembly in RFC-1766 format, or "neutral" for language-independent (nonsatellite) assemblies.</span></span>|  
|<span data-ttu-id="78a4f-192">**Niestandardowy**</span><span class="sxs-lookup"><span data-stu-id="78a4f-192">**Custom**</span></span>|<span data-ttu-id="78a4f-193">Niestandardowe dużego obiektu binarnego (BLOB).</span><span class="sxs-lookup"><span data-stu-id="78a4f-193">Custom binary large object (BLOB).</span></span> <span data-ttu-id="78a4f-194">To jest aktualnie używana tylko zestawów generowanych przez [Generator obrazu natywnego (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span><span class="sxs-lookup"><span data-stu-id="78a4f-194">This is currently used only in assemblies generated by the [Native Image Generator (Ngen)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).</span></span>|<span data-ttu-id="78a4f-195">Niestandardowy ciąg używany przez narzędzie Generator obrazu natywnego do powiadamiania pamięci podręcznej zestawów zestawu instalowany jest obrazu macierzystego czy w związku z tym ma zostać zainstalowany w pamięci podręcznej obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="78a4f-195">Custom string used by the Native Image Generator tool to notify the assembly cache that the assembly being installed is a native image, and is therefore to be installed in the native image cache.</span></span> <span data-ttu-id="78a4f-196">Skrót ciągu zap.</span><span class="sxs-lookup"><span data-stu-id="78a4f-196">Also called a zap string.</span></span>|  
  
 <span data-ttu-id="78a4f-197">W poniższym przykładzie przedstawiono **AssemblyName** po prostu nazwane zestawu z domyślną kulturę.</span><span class="sxs-lookup"><span data-stu-id="78a4f-197">The following example shows an **AssemblyName** for a simply named assembly with default culture.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=""   
```  
  
 <span data-ttu-id="78a4f-198">W poniższym przykładzie przedstawiono pełni podane odwołanie do zestawu o silnej nazwie z kulturą "en".</span><span class="sxs-lookup"><span data-stu-id="78a4f-198">The following example shows a fully specified reference for a strongly named assembly with culture "en".</span></span>  
  
```csharp  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0   
```  
  
 <span data-ttu-id="78a4f-199">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, który może zostać wykonane przez silne lub po prostu nazwane zestawu.</span><span class="sxs-lookup"><span data-stu-id="78a4f-199">The following examples each show a partially specified **AssemblyName**, which can be satisfied by either a strong or a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto  
com.microsoft.crypto, Culture=""  
com.microsoft.crypto, Culture=en   
```  
  
 <span data-ttu-id="78a4f-200">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez po prostu nazwany zestaw.</span><span class="sxs-lookup"><span data-stu-id="78a4f-200">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a simply named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=null   
com.microsoft.crypto, Culture=en, PublicKeyToken=null  
```  
  
 <span data-ttu-id="78a4f-201">W poniższych przykładach każdego pokazano częściowo określony **AssemblyName**, muszą być spełnione przez zestaw o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="78a4f-201">The following examples each show a partially specified **AssemblyName**, which must be satisfied by a strongly named assembly.</span></span>  
  
```csharp  
com.microsoft.crypto, Culture="", PublicKeyToken=a5d015c7d5a0b012  
com.microsoft.crypto, Culture=en, PublicKeyToken=a5d015c7d5a0b012,  
    Version=1.0.0.0  
```  
  
## <a name="specifying-pointers"></a><span data-ttu-id="78a4f-202">Określenie wskaźników</span><span class="sxs-lookup"><span data-stu-id="78a4f-202">Specifying Pointers</span></span>  
 <span data-ttu-id="78a4f-203">SimpleTypeSpec * reprezentuje niezarządzanego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="78a4f-203">SimpleTypeSpec* represents an unmanaged pointer.</span></span> <span data-ttu-id="78a4f-204">Na przykład otrzymywać wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType*")`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-204">For example, to get a pointer to type MyType, use `Type.GetType("MyType*")`.</span></span> <span data-ttu-id="78a4f-205">Aby otrzymywać wskaźnik na wskaźnik do typu Mojtyp, należy użyć `Type.GetType("MyType**")`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-205">To get a pointer to a pointer to type MyType, use `Type.GetType("MyType**")`.</span></span>  
  
## <a name="specifying-references"></a><span data-ttu-id="78a4f-206">Określanie odwołań</span><span class="sxs-lookup"><span data-stu-id="78a4f-206">Specifying References</span></span>  
 <span data-ttu-id="78a4f-207">SimpleTypeSpec & reprezentuje zarządzanych wskaźnik lub odwołanie.</span><span class="sxs-lookup"><span data-stu-id="78a4f-207">SimpleTypeSpec & represents a managed pointer or reference.</span></span> <span data-ttu-id="78a4f-208">Na przykład, aby pobrać odwołanie do typu Mojtyp, należy użyć `Type.GetType("MyType &")`.</span><span class="sxs-lookup"><span data-stu-id="78a4f-208">For example, to get a reference to type MyType, use `Type.GetType("MyType &")`.</span></span> <span data-ttu-id="78a4f-209">Należy pamiętać, że w przeciwieństwie do wskaźników, odwołania mogą zawierać maksymalnie jeden poziom.</span><span class="sxs-lookup"><span data-stu-id="78a4f-209">Note that unlike pointers, references are limited to one level.</span></span>  
  
## <a name="specifying-arrays"></a><span data-ttu-id="78a4f-210">Określanie tablic</span><span class="sxs-lookup"><span data-stu-id="78a4f-210">Specifying Arrays</span></span>  
 <span data-ttu-id="78a4f-211">W gramatyka BNF ReflectionEmitDimension ma zastosowanie tylko do niekompletnego typu definicje pobrany przy użyciu <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="78a4f-211">In the BNF Grammar, ReflectionEmitDimension only applies to incomplete type definitions retrieved using <xref:System.Reflection.Emit.ModuleBuilder.GetType%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="78a4f-212">Definicje niekompletnego typu <xref:System.Reflection.Emit.TypeBuilder> obiekty utworzone za pomocą <xref:System.Reflection.Emit?displayProperty=nameWithType> , ale na którym <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> nie została wywołana.</span><span class="sxs-lookup"><span data-stu-id="78a4f-212">Incomplete type definitions are <xref:System.Reflection.Emit.TypeBuilder> objects constructed using <xref:System.Reflection.Emit?displayProperty=nameWithType> but on which <xref:System.Reflection.Emit.TypeBuilder.CreateType%2A?displayProperty=nameWithType> has not been called.</span></span> <span data-ttu-id="78a4f-213">ReflectionDimension można pobrać żadnych definicji typu, która została zakończona, oznacza to, typu, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="78a4f-213">ReflectionDimension can be used to retrieve any type definition that has been completed, that is, a type that has been loaded.</span></span>  
  
 <span data-ttu-id="78a4f-214">Tablice są dostępne w odbicia, określając rangą tablicy:</span><span class="sxs-lookup"><span data-stu-id="78a4f-214">Arrays are accessed in reflection by specifying the rank of the array:</span></span>  
  
-   <span data-ttu-id="78a4f-215">`Type.GetType("MyArray[]")`pobiera tablicy jednowymiarowej z 0 dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-215">`Type.GetType("MyArray[]")` gets a single-dimension array with 0 lower bound.</span></span>  
  
-   <span data-ttu-id="78a4f-216">`Type.GetType("MyArray[*]")`pobiera tablicy jednowymiarowej z nieznanego dolnej granicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-216">`Type.GetType("MyArray[*]")` gets a single-dimension array with unknown lower bound.</span></span>  
  
-   <span data-ttu-id="78a4f-217">`Type.GetType("MyArray[][]")`pobiera tablicy jest tablicą dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="78a4f-217">`Type.GetType("MyArray[][]")` gets a two-dimensional array's array.</span></span>  
  
-   <span data-ttu-id="78a4f-218">`Type.GetType("MyArray[*,*]")`i `Type.GetType("MyArray[,]")` pobiera prostokątny tablicą dwuwymiarową z nieznanego dolne granice tablicy.</span><span class="sxs-lookup"><span data-stu-id="78a4f-218">`Type.GetType("MyArray[*,*]")` and `Type.GetType("MyArray[,]")` gets a rectangular two-dimensional array with unknown lower bounds.</span></span>  
  
 <span data-ttu-id="78a4f-219">Należy pamiętać, że z punktu widzenia środowiska uruchomieniowego, `MyArray[] != MyArray[*]`, ale dla tablic wielowymiarowych są równoważne dwóch notacji.</span><span class="sxs-lookup"><span data-stu-id="78a4f-219">Note that from a runtime point of view, `MyArray[] != MyArray[*]`, but for multidimensional arrays, the two notations are equivalent.</span></span> <span data-ttu-id="78a4f-220">Oznacza to `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` daje w wyniku **true**.</span><span class="sxs-lookup"><span data-stu-id="78a4f-220">That is, `Type.GetType("MyArray [,]") == Type.GetType("MyArray[*,*]")` evaluates to **true**.</span></span>  
  
 <span data-ttu-id="78a4f-221">Aby uzyskać **ModuleBuilder.GetType**, `MyArray[0..5]` wskazuje tablicy jednowymiarowej, o rozmiarze 6 niższe powiązane 0.</span><span class="sxs-lookup"><span data-stu-id="78a4f-221">For **ModuleBuilder.GetType**, `MyArray[0..5]` indicates a single-dimension array with size 6, lower bound 0.</span></span> <span data-ttu-id="78a4f-222">`MyArray[4…]`Wskazuje jednowymiarowej tablicy o nieznanym rozmiarze i dolną granicę 4.</span><span class="sxs-lookup"><span data-stu-id="78a4f-222">`MyArray[4…]` indicates a single-dimension array of unknown size and lower bound 4.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a4f-223">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78a4f-223">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 <xref:System.Reflection.Emit.ModuleBuilder>  
 <xref:System.Reflection.Emit.TypeBuilder>  
 <xref:System.Type.FullName%2A?displayProperty=nameWithType>  
 <xref:System.Type.GetType%2A?displayProperty=nameWithType>  
 <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="78a4f-224">Wyświetlanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="78a4f-224">Viewing Type Information</span></span>](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
