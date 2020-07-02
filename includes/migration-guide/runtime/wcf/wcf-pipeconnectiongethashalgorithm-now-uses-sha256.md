---
ms.openlocfilehash: 0f87f9e9b87860da97ce96e18104b44ec4327c91
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621229"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="90df8-101">Funkcja WCF PipeConnection. GetHashAlgorithm używa teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="90df8-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="90df8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="90df8-102">Details</span></span>

<span data-ttu-id="90df8-103">Rozpoczynając od .NET Framework 4.7.1, Windows Communication Foundation używa skrótu SHA256 do generowania losowych nazw dla nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="90df8-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="90df8-104">W .NET Framework 4,7 i starszych wersjach użyto skrótu SHA1.</span><span class="sxs-lookup"><span data-stu-id="90df8-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="90df8-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="90df8-105">Suggestion</span></span>

<span data-ttu-id="90df8-106">Jeśli wystąpi problem ze zgodnością z tą zmianą w .NET Framework 4.7.1 lub nowszym, możesz go wycofać, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="90df8-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="90df8-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="90df8-107">Name</span></span>    | <span data-ttu-id="90df8-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="90df8-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="90df8-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="90df8-109">Scope</span></span>   |<span data-ttu-id="90df8-110">Mały</span><span class="sxs-lookup"><span data-stu-id="90df8-110">Minor</span></span>|
|<span data-ttu-id="90df8-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="90df8-111">Version</span></span>|<span data-ttu-id="90df8-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="90df8-112">4.7.1</span></span>|
|<span data-ttu-id="90df8-113">Typ</span><span class="sxs-lookup"><span data-stu-id="90df8-113">Type</span></span>|<span data-ttu-id="90df8-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="90df8-114">Runtime</span></span>|
