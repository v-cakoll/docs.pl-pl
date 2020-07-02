---
ms.openlocfilehash: 0bd90b3d479a7e0897aaf78b7718ae156a4a239f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620194"
---
### <a name="assemblies-compiled-with-regexcompiletoassembly-breaks-between-40-and-45"></a><span data-ttu-id="7798e-101">Zestawy skompilowane z wyrażeniem regularnym. CompileToAssembly są rozdzielonymi między 4,0 i 4,5</span><span class="sxs-lookup"><span data-stu-id="7798e-101">Assemblies compiled with Regex.CompileToAssembly breaks between 4.0 and 4.5</span></span>

#### <a name="details"></a><span data-ttu-id="7798e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7798e-102">Details</span></span>

<span data-ttu-id="7798e-103">Jeśli zestaw skompilowanych wyrażeń regularnych jest skompilowany przy użyciu .NET Framework 4,5, ale jest przeznaczony dla .NET Framework 4, próba użycia jednego z wyrażeń regularnych w tym zestawie w systemie z zainstalowanym programem .NET Framework 4 zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7798e-103">If an assembly of compiled regular expressions is built with the .NET Framework 4.5 but targets the .NET Framework 4, attempting to use one of the regular expressions in that assembly on a system with .NET Framework 4 installed throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7798e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7798e-104">Suggestion</span></span>

<span data-ttu-id="7798e-105">Aby obejść ten problem, można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="7798e-105">To work around this problem, you can do either of the following:</span></span><ul><li><span data-ttu-id="7798e-106">Kompiluj zestaw zawierający wyrażenia regularne z .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="7798e-106">Build the assembly that contains the regular expressions with the .NET Framework 4.</span></span></li><li><span data-ttu-id="7798e-107">Użyj interpretowanego wyrażenia regularnego.</span><span class="sxs-lookup"><span data-stu-id="7798e-107">Use an interpreted regular expression.</span></span></li></ul>

| <span data-ttu-id="7798e-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7798e-108">Name</span></span>    | <span data-ttu-id="7798e-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="7798e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7798e-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="7798e-110">Scope</span></span>   |<span data-ttu-id="7798e-111">Mały</span><span class="sxs-lookup"><span data-stu-id="7798e-111">Minor</span></span>|
|<span data-ttu-id="7798e-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="7798e-112">Version</span></span>|<span data-ttu-id="7798e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="7798e-113">4.5</span></span>|
|<span data-ttu-id="7798e-114">Typ</span><span class="sxs-lookup"><span data-stu-id="7798e-114">Type</span></span>|<span data-ttu-id="7798e-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7798e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7798e-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7798e-116">Affected APIs</span></span>

-<xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName)?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[])?displayProperty=nameWithType></li><li><xref:System.Text.RegularExpressions.Regex.CompileToAssembly(System.Text.RegularExpressions.RegexCompilationInfo[],System.Reflection.AssemblyName,System.Reflection.Emit.CustomAttributeBuilder[],System.String)?displayProperty=nameWithType></li></ul>|
