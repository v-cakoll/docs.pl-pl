---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181994"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="1ef9d-101">Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="1ef9d-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="1ef9d-102">Stała jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) , począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8. <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="1ef9d-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1ef9d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1ef9d-103">Version introduced</span></span>

<span data-ttu-id="1ef9d-104">.NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="1ef9d-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="1ef9d-105">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="1ef9d-105">Details</span></span>

<span data-ttu-id="1ef9d-106">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> został zastosowany do stałej.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="1ef9d-107">Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="1ef9d-108">W poprzednich wersjach programu .NET Core i .NET Framework nie została oznaczona jako przestarzała.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="1ef9d-109">Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="1ef9d-110">Stała jest równoznaczna z `\r\n`sekwencją znaków nowego wiersza w systemie Windows. `vbNewLine`</span><span class="sxs-lookup"><span data-stu-id="1ef9d-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="1ef9d-111">W systemach opartych na systemie UNIX znak nowego wiersza `\n`to.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="1ef9d-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="1ef9d-112">Recommended action</span></span>

<span data-ttu-id="1ef9d-113">Komunikat o [przestarzałym](xref:System.ObsoleteAttribute) atrybucie `vbNewLine` dla programu zawiera następujące zalecenia:</span><span class="sxs-lookup"><span data-stu-id="1ef9d-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="1ef9d-114">W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="1ef9d-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="1ef9d-115">W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1ef9d-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="1ef9d-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1ef9d-116">Category</span></span>

<span data-ttu-id="1ef9d-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1ef9d-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1ef9d-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1ef9d-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

