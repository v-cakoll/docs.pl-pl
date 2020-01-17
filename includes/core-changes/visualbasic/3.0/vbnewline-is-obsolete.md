---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116367"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="91d0d-101">Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="91d0d-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="91d0d-102">Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>a jest oznaczona jako [\[przestarzałe\]](xref:System.ObsoleteAttribute) począwszy od platformy .net Core 3,0 wersja zapoznawcza 8.</span><span class="sxs-lookup"><span data-stu-id="91d0d-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="91d0d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="91d0d-103">Version introduced</span></span>

<span data-ttu-id="91d0d-104">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="91d0d-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="91d0d-105">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="91d0d-105">Change description</span></span>

<span data-ttu-id="91d0d-106">Począwszy od programu .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do stałej <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="91d0d-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="91d0d-107">Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="91d0d-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="91d0d-108">W .NET Framework i poprzednich wersjach programu .NET Core nie została oznaczona jako przestarzała.</span><span class="sxs-lookup"><span data-stu-id="91d0d-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="91d0d-109">Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform.</span><span class="sxs-lookup"><span data-stu-id="91d0d-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="91d0d-110">Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine> jest równoznaczna z `\r\n`, sekwencją znaków nowego wiersza w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="91d0d-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="91d0d-111">W systemach opartych na systemie UNIX znak nowego wiersza jest `\n`.</span><span class="sxs-lookup"><span data-stu-id="91d0d-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="91d0d-112">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="91d0d-112">Recommended action</span></span>

<span data-ttu-id="91d0d-113">Komunikat o [nieaktualnym](xref:System.ObsoleteAttribute) atrybucie dla <xref:Microsoft.VisualBasic.Constants.vbNewLine> zawiera następujące zalecenia:</span><span class="sxs-lookup"><span data-stu-id="91d0d-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="91d0d-114">W przypadku powrotu karetki i wysuwu wiersza Użyj <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span><span class="sxs-lookup"><span data-stu-id="91d0d-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="91d0d-115">W przypadku wiersza dla bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="91d0d-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="91d0d-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="91d0d-116">Category</span></span>

<span data-ttu-id="91d0d-117">Język Visual Basic</span><span class="sxs-lookup"><span data-stu-id="91d0d-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="91d0d-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="91d0d-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
