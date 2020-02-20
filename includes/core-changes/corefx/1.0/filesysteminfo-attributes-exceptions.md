---
ms.openlocfilehash: 4091bdcf7d9ed8872aed5faa6e6d3ed143903787
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449410"
---
### <a name="unauthorizedaccessexception-thrown-by-filesysteminfoattributes"></a><span data-ttu-id="0cfaf-101">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="0cfaf-101">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>

<span data-ttu-id="0cfaf-102">W programie .NET Core jest generowany <xref:System.UnauthorizedAccessException>, gdy wywołujący próbuje ustawić wartość atrybutu pliku, ale nie ma uprawnienia do zapisu.</span><span class="sxs-lookup"><span data-stu-id="0cfaf-102">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown when the caller attempts to set a file attribute value but doesn't have write permission.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0cfaf-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="0cfaf-103">Change description</span></span>

<span data-ttu-id="0cfaf-104">W .NET Framework jest generowany <xref:System.ArgumentException>, gdy wywołujący próbuje ustawić wartość atrybutu pliku w <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>, ale nie ma uprawnienia do zapisu.</span><span class="sxs-lookup"><span data-stu-id="0cfaf-104">In .NET Framework, an <xref:System.ArgumentException> is thrown when the caller attempts to set a file attribute value in <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType> but doesn't have write permission.</span></span> <span data-ttu-id="0cfaf-105">W przypadku platformy .NET Core w zamian zostanie zgłoszony <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="0cfaf-105">In .NET Core, an <xref:System.UnauthorizedAccessException> is thrown instead.</span></span> <span data-ttu-id="0cfaf-106">(W środowisku .NET Core jest nadal zgłaszane <xref:System.ArgumentException>, jeśli obiekt wywołujący podejmie próbę ustawienia nieprawidłowego atrybutu pliku).</span><span class="sxs-lookup"><span data-stu-id="0cfaf-106">(In .NET Core, an <xref:System.ArgumentException> is still thrown if the caller attempts to set an invalid file attribute.)</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0cfaf-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="0cfaf-107">Version introduced</span></span>

<span data-ttu-id="0cfaf-108">1.0</span><span class="sxs-lookup"><span data-stu-id="0cfaf-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0cfaf-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="0cfaf-109">Recommended action</span></span>

<span data-ttu-id="0cfaf-110">Zmodyfikuj wszystkie instrukcje `catch`, aby przechwycić <xref:System.UnauthorizedAccessException> zamiast lub oprócz <xref:System.ArgumentException>, w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="0cfaf-110">Modify any `catch` statements to catch an <xref:System.UnauthorizedAccessException> instead of, or in addition to, an <xref:System.ArgumentException>, as necessary.</span></span>

#### <a name="category"></a><span data-ttu-id="0cfaf-111">Kategoria</span><span class="sxs-lookup"><span data-stu-id="0cfaf-111">Category</span></span>

<span data-ttu-id="0cfaf-112">CoreFx</span><span class="sxs-lookup"><span data-stu-id="0cfaf-112">CoreFx</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0cfaf-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0cfaf-113">Affected APIs</span></span>

- <xref:System.IO.FileSystemInfo.Attributes?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.IO.FileSystemInfo.Attributes`

-->
