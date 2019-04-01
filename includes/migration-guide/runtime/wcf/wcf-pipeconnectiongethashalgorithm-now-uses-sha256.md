---
ms.openlocfilehash: 71f61f23a8b17459610d253766a99e594f09428e
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760454"
---
### <a name="wcf-pipeconnectiongethashalgorithm-now-uses-sha256"></a><span data-ttu-id="0815a-101">Usługi WCF PipeConnection.GetHashAlgorithm używa teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="0815a-101">WCF PipeConnection.GetHashAlgorithm now uses SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="0815a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0815a-102">Details</span></span>|<span data-ttu-id="0815a-103">Począwszy od programu .NET Framework 4.7.1 Windows Communication Foundation używa skrót SHA256 do wygenerowania losowych nazw dla nazwanych potoków.</span><span class="sxs-lookup"><span data-stu-id="0815a-103">Starting with the .NET Framework 4.7.1, Windows Communication Foundation uses a SHA256 hash to generate random names for named pipes.</span></span> <span data-ttu-id="0815a-104">W .NET Framework 4.7 i wcześniejszych wersjach on Skrót SHA1.</span><span class="sxs-lookup"><span data-stu-id="0815a-104">In the .NET Framework 4.7 and earlier versions, it used a SHA1 hash.</span></span>|
|<span data-ttu-id="0815a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0815a-105">Suggestion</span></span>|<span data-ttu-id="0815a-106">Jeśli napotkasz problem ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub później, użytkownik może zrezygnować go, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="0815a-106">If you run into compatibility issue with this change on the .NET Framework 4.7.1 or later, you can opt-out it by adding the following line to the <code>&lt;runtime&gt;</code> section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InPipeConnectionGetHashAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="0815a-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="0815a-107">Scope</span></span>|<span data-ttu-id="0815a-108">Mały</span><span class="sxs-lookup"><span data-stu-id="0815a-108">Minor</span></span>|
|<span data-ttu-id="0815a-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="0815a-109">Version</span></span>|<span data-ttu-id="0815a-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="0815a-110">4.7.1</span></span>|
|<span data-ttu-id="0815a-111">Typ</span><span class="sxs-lookup"><span data-stu-id="0815a-111">Type</span></span>|<span data-ttu-id="0815a-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0815a-112">Runtime</span></span>|

