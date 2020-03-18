---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449410"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="beb2b-101">UnauthorizedAccessException zgłoszony przez FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="beb2b-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="beb2b-102">W .NET Core <xref:System.UnauthorizedAccessException> jest generowany, gdy obiekt wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="beb2b-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="beb2b-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="beb2b-103">Change description</span></span>

<span data-ttu-id="beb2b-104">W platformie .NET Framework jest <xref:System.ArgumentException> generowany, gdy obiekt <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnień do zapisu.</span><span class="sxs-lookup"><span data-stu-id="beb2b-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="beb2b-105">W .NET Core <xref:System.UnauthorizedAccessException> zamiast tego jest generowany.</span><span class="sxs-lookup"><span data-stu-id="beb2b-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="beb2b-106">(W .NET Core <xref:System.ArgumentException> jest nadal generowany, jeśli obiekt wywołujący próbuje ustawić nieprawidłowy atrybut pliku).</span><span class="sxs-lookup"><span data-stu-id="beb2b-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="beb2b-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="beb2b-107">Version introduced</span></span>

<span data-ttu-id="beb2b-108">1.0</span><span class="sxs-lookup"><span data-stu-id="beb2b-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="beb2b-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="beb2b-109">Recommended action</span></span>

<span data-ttu-id="beb2b-110">Zmodyfikuj `catch` <xref:System.UnauthorizedAccessException> wszystkie instrukcje, aby przechwycić <xref:System.ArgumentException>zamiast lub oprócz , w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="beb2b-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="beb2b-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="beb2b-111">Category</span></span>

<span data-ttu-id="beb2b-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="beb2b-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="beb2b-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="beb2b-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
