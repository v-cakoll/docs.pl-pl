---
ms.openlocfilehash: a007022bf32ffe76861f6f9016a7edace17b0f61
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620357"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a><span data-ttu-id="6b3d8-101">Dane zapisywane do PrintSystemJobInfo. strumienia zadań muszą być w formacie XPS</span><span class="sxs-lookup"><span data-stu-id="6b3d8-101">Data written to PrintSystemJobInfo.JobStream must be in XPS format</span></span>

#### <a name="details"></a><span data-ttu-id="6b3d8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6b3d8-102">Details</span></span>

<span data-ttu-id="6b3d8-103"><xref:System.Printing.PrintSystemJobInfo.JobStream>Właściwość uwidacznia strumień zadania drukowania.</span><span class="sxs-lookup"><span data-stu-id="6b3d8-103">The <xref:System.Printing.PrintSystemJobInfo.JobStream> property exposes the stream of a print job.</span></span> <span data-ttu-id="6b3d8-104">Użytkownik może wysyłać pierwotne dane do podstawowych składników drukowania systemu operacyjnego przez zapis do tego strumienia. Począwszy od .NET Framework 4,5 w systemie Windows 8 i nowszych wersjach systemu operacyjnego Windows, dane zapisywane w tym strumieniu muszą być w formacie XPS jako strumień pakietu.</span><span class="sxs-lookup"><span data-stu-id="6b3d8-104">The user can send raw data to the underlying operating system printing components by writing to this stream.Starting with the .NET Framework 4.5 on Windows 8 and later versions of the Windows operating system, data written to this stream must be in XPS format as a package stream.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6b3d8-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6b3d8-105">Suggestion</span></span>

<span data-ttu-id="6b3d8-106">Aby wydrukować zawartość wyjściową, można wykonać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="6b3d8-106">To output print content, you can do either of the following:</span></span><ul><li><span data-ttu-id="6b3d8-107">Użyj <xref:System.Windows.Xps.XpsDocumentWriter> klasy do wyjściowej zawartości wydruku.</span><span class="sxs-lookup"><span data-stu-id="6b3d8-107">Use the <xref:System.Windows.Xps.XpsDocumentWriter> class to output print content.</span></span> <span data-ttu-id="6b3d8-108">Jest to zalecana alternatywa.</span><span class="sxs-lookup"><span data-stu-id="6b3d8-108">This is the recommended alternative.</span></span></li><li><span data-ttu-id="6b3d8-109">Upewnij się, że dane wysyłane do strumienia zwróconego przez <xref:System.Printing.PrintSystemJobInfo.JobStream> Właściwość są w formacie XPS jako strumień pakietu.</span><span class="sxs-lookup"><span data-stu-id="6b3d8-109">Ensure that the data sent to the stream returned by the <xref:System.Printing.PrintSystemJobInfo.JobStream> property is in XPS format as a package stream.</span></span></li></ul>

| <span data-ttu-id="6b3d8-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6b3d8-110">Name</span></span>    | <span data-ttu-id="6b3d8-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b3d8-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6b3d8-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="6b3d8-112">Scope</span></span>   |<span data-ttu-id="6b3d8-113">Mały</span><span class="sxs-lookup"><span data-stu-id="6b3d8-113">Minor</span></span>|
|<span data-ttu-id="6b3d8-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="6b3d8-114">Version</span></span>|<span data-ttu-id="6b3d8-115">4.5</span><span class="sxs-lookup"><span data-stu-id="6b3d8-115">4.5</span></span>|
|<span data-ttu-id="6b3d8-116">Typ</span><span class="sxs-lookup"><span data-stu-id="6b3d8-116">Type</span></span>|<span data-ttu-id="6b3d8-117">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="6b3d8-117">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b3d8-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="6b3d8-118">Affected APIs</span></span>

-<xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
