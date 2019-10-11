---
ms.openlocfilehash: e476039ff9c8d33f54a2f7e4371dc09a3be557c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237424"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="7db3d-101">Microsoft. VisualBasic. Stałychs. vbNewLine jest przestarzała</span><span class="sxs-lookup"><span data-stu-id="7db3d-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="7db3d-102">Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> jest oznaczona jako [przestarzała](xref:System.ObsoleteAttribute) , rozpoczynając od platformy .net Core 3,0 wersja zapoznawcza 8.</span><span class="sxs-lookup"><span data-stu-id="7db3d-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7db3d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="7db3d-103">Version introduced</span></span>

<span data-ttu-id="7db3d-104">3,0 wersja zapoznawcza 8</span><span class="sxs-lookup"><span data-stu-id="7db3d-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="7db3d-105">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="7db3d-105">Change description</span></span>

<span data-ttu-id="7db3d-106">Począwszy od platformy .NET Core 3,0 w wersji zapoznawczej 8, [przestarzały](xref:System.ObsoleteAttribute) atrybut został zastosowany do stałej <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="7db3d-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="7db3d-107">Użycie stałej powoduje wygenerowanie ostrzeżenia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="7db3d-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="7db3d-108">W poprzednich wersjach programu .NET Core i .NET Framework nie została oznaczona jako przestarzała.</span><span class="sxs-lookup"><span data-stu-id="7db3d-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="7db3d-109">Ta zmiana została wprowadzona w celu obsługi Visual Basic jako języka dla tworzenia wielu platform.</span><span class="sxs-lookup"><span data-stu-id="7db3d-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="7db3d-110">Stała `vbNewLine` jest równoważna z `\r\n`, sekwencją znaków nowego wiersza w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="7db3d-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="7db3d-111">W systemach opartych na systemie UNIX znak nowego wiersza jest `\n`.</span><span class="sxs-lookup"><span data-stu-id="7db3d-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="7db3d-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="7db3d-112">Recommended action</span></span>

<span data-ttu-id="7db3d-113">Komunikat o [nieaktualnym](xref:System.ObsoleteAttribute) atrybucie dla `vbNewLine` obejmuje następujące zalecenia:</span><span class="sxs-lookup"><span data-stu-id="7db3d-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="7db3d-114">W przypadku powrotu karetki i wysuwu wiersza Użyj [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span><span class="sxs-lookup"><span data-stu-id="7db3d-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="7db3d-115">W przypadku wiersza bieżącej platformy Użyj <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7db3d-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="7db3d-116">Kategoria</span><span class="sxs-lookup"><span data-stu-id="7db3d-116">Category</span></span>

<span data-ttu-id="7db3d-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7db3d-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7db3d-118">Narażone interfejsy API</span><span class="sxs-lookup"><span data-stu-id="7db3d-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
