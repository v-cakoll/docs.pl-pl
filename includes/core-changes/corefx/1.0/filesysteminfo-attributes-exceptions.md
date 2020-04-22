---
ms.openlocfilehash: 2ea9abca7578c2ddf92712a1c597f8f1ff4a5c0c
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021822"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="b3006-101">NieautoryzowaneaccessException generowane przez FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="b3006-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="b3006-102">W .NET Core <xref:System.UnauthorizedAccessException> jest generowany, gdy wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b3006-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b3006-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="b3006-103">Change description</span></span>

<span data-ttu-id="b3006-104">W .NET Framework <xref:System.ArgumentException> jest generowany, gdy wywołujący próbuje ustawić <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> wartość atrybutu pliku, ale nie ma uprawnień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="b3006-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="b3006-105">W .NET Core <xref:System.UnauthorizedAccessException> zamiast tego jest wyrzucany.</span><span class="sxs-lookup"><span data-stu-id="b3006-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="b3006-106">(W .NET Core <xref:System.ArgumentException> program .NET Core jest nadal generowany, jeśli wywołujący próbuje ustawić nieprawidłowy atrybut pliku).</span><span class="sxs-lookup"><span data-stu-id="b3006-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b3006-107">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="b3006-107">Version introduced</span></span>

<span data-ttu-id="b3006-108">1.0</span><span class="sxs-lookup"><span data-stu-id="b3006-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b3006-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="b3006-109">Recommended action</span></span>

<span data-ttu-id="b3006-110">Zmodyfikuj wszystkie `catch` instrukcje, aby złapać <xref:System.UnauthorizedAccessException> zamiast lub oprócz , <xref:System.ArgumentException>w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="b3006-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="b3006-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="b3006-111">Category</span></span>

<span data-ttu-id="b3006-112">Podstawowe biblioteki .NET</span><span class="sxs-lookup"><span data-stu-id="b3006-112">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3006-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b3006-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
