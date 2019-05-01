---
ms.openlocfilehash: 318609c15d2e0b9a7ee59b38463735b33ef87974
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61764043"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="639e1-101">Usługi WCF PipeConnection.GetHashAlgorithm używa teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="639e1-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="639e1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="639e1-102">Details</span></span>|<span data-ttu-id="639e1-103">Począwszy od programu .NET Framework 4.7.1 Windows Communication Foundation używa skrót SHA256 do wygenerowania losowych nazw dla nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="639e1-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="639e1-104">W .NET Framework 4.7 i wcześniejszych wersjach on Skrót SHA1.</span><span class="sxs-lookup"><span data-stu-id="639e1-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="639e1-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="639e1-105">Suggestion</span></span>|<span data-ttu-id="639e1-106">Jeśli napotkasz problem ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub później, użytkownik może zrezygnować go, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="639e1-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="639e1-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="639e1-107">Scope</span></span>|<span data-ttu-id="639e1-108">Mały</span><span class="sxs-lookup"><span data-stu-id="639e1-108">Minor</span></span>|
|<span data-ttu-id="639e1-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="639e1-109">Version</span></span>|<span data-ttu-id="639e1-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="639e1-110">4.7.1</span></span>|
|<span data-ttu-id="639e1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="639e1-111">Type</span></span>|<span data-ttu-id="639e1-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="639e1-112">Runtime</span></span>|
