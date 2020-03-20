---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857263"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="8267e-101">WCF PipeConnection.GetHashAlgorithm używa teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="8267e-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="8267e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="8267e-102">Details</span></span>|<span data-ttu-id="8267e-103">Począwszy od programu .NET Framework 4.7.1, Program Windows Communication Foundation używa skrótu SHA256 do generowania losowych nazw nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="8267e-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="8267e-104">W .NET Framework 4.7 i wcześniejszych wersjach użyto skrótu SHA1.</span><span class="sxs-lookup"><span data-stu-id="8267e-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="8267e-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="8267e-105">Suggestion</span></span>|<span data-ttu-id="8267e-106">Jeśli problem ze zgodnością z tą zmianą występuje w programie .NET Framework 4.7.1 lub nowszym, możesz ją zrezygnować, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="8267e-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="8267e-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="8267e-107">Scope</span></span>|<span data-ttu-id="8267e-108">Mały</span><span class="sxs-lookup"><span data-stu-id="8267e-108">Minor</span></span>|
|<span data-ttu-id="8267e-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="8267e-109">Version</span></span>|<span data-ttu-id="8267e-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="8267e-110">4.7.1</span></span>|
|<span data-ttu-id="8267e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="8267e-111">Type</span></span>|<span data-ttu-id="8267e-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="8267e-112">Runtime</span></span>|
