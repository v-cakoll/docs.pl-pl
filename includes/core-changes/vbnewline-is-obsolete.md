---
ms.openlocfilehash: 2a0ebcf61fd96df6d2235962c1f1e9cac3fb22e6
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988501"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="32fd3-101">Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="32fd3-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="32fd3-102">Stała jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) w .NET Framework, ale atrybut nie był wcześniej w bibliotece .NET Core 3,0. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="32fd3-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) in .NET Framework, but the attribute was missing previously in the .NET Core 3.0 library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32fd3-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="32fd3-103">Version introduced</span></span>

<span data-ttu-id="32fd3-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="32fd3-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="32fd3-105">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="32fd3-105">Details</span></span>

<span data-ttu-id="32fd3-106">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> został zastosowany do `vbNewLine` stałej, która jest zgodna z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="32fd3-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant to conform to `vbNewLine` in the .NET Framework.</span></span> <span data-ttu-id="32fd3-107">`vbNewLine` Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="32fd3-107">Use of the `vbNewLine` constant produces a compiler warning.</span></span> 

<span data-ttu-id="32fd3-108">W poprzednich wersjach programu .NET Core program `vbNewLine` nie wygenerował ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="32fd3-108">In previous versions of .NET Core, `vbNewLine` did not produce a compiler warning.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32fd3-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="32fd3-109">Recommended action</span></span>

<span data-ttu-id="32fd3-110">Komunikat o [przestarzałym](xref:System.ObsoleteAttribute) atrybucie `vbNewLine` dla programu zawiera następujące zalecenia:</span><span class="sxs-lookup"><span data-stu-id="32fd3-110">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="32fd3-111">W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="32fd3-111">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="32fd3-112">W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32fd3-112">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="32fd3-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="32fd3-113">Category</span></span>

<span data-ttu-id="32fd3-114">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32fd3-114">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32fd3-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="32fd3-115">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

