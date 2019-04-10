---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236224"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="42877-101">Wartość domyślna WCF MsmqSecureHashAlgorithm jest teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="42877-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="42877-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="42877-102">Details</span></span>|<span data-ttu-id="42877-103">Począwszy od programu .NET Framework 4.7.1 komunikat domyślny algorytm programu WCF dla wiadomości usługi Msmq podpisywania jest algorytm SHA256.</span><span class="sxs-lookup"><span data-stu-id="42877-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="42877-104">W .NET Framework 4.7 i wcześniejszych wersjach komunikat domyślny algorytm podpisywania jest algorytm SHA1.</span><span class="sxs-lookup"><span data-stu-id="42877-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="42877-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="42877-105">Suggestion</span></span>|<span data-ttu-id="42877-106">Jeśli napotkasz problemy ze zgodnością za pomocą tej zmiany w środowisku .NET Framework 4.7.1 lub nowszej, użytkownik może zrezygnować zmiany, dodając następujący wiersz do <code>&lt;runtime&gt;</code>sekcji w pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="42877-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="42877-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="42877-107">Scope</span></span>|<span data-ttu-id="42877-108">Mały</span><span class="sxs-lookup"><span data-stu-id="42877-108">Minor</span></span>|
|<span data-ttu-id="42877-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="42877-109">Version</span></span>|<span data-ttu-id="42877-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="42877-110">4.7.1</span></span>|
|<span data-ttu-id="42877-111">Typ</span><span class="sxs-lookup"><span data-stu-id="42877-111">Type</span></span>|<span data-ttu-id="42877-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="42877-112">Runtime</span></span>|
