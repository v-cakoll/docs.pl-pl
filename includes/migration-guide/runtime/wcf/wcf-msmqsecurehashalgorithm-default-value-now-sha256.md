---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857270"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="2b4d5-101">WCF MsmqSecureHashAlgorithm wartość domyślna jest teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="2b4d5-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

|   |   |
|---|---|
|<span data-ttu-id="2b4d5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2b4d5-102">Details</span></span>|<span data-ttu-id="2b4d5-103">Począwszy od .NET Framework 4.7.1, domyślny algorytm podpisywania wiadomości w WCF dla komunikatów Msmq jest SHA256.</span><span class="sxs-lookup"><span data-stu-id="2b4d5-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="2b4d5-104">W .NET Framework 4.7 i wcześniejszych wersjach domyślny algorytm podpisywania wiadomości jest SHA1.</span><span class="sxs-lookup"><span data-stu-id="2b4d5-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>|
|<span data-ttu-id="2b4d5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="2b4d5-105">Suggestion</span></span>|<span data-ttu-id="2b4d5-106">Jeśli napotkasz problemy ze zgodnością z tą zmianą w programie .NET Framework 4.7.1 lub <code>&lt;runtime&gt;</code>nowszym, możesz zrezygnować ze zmiany, dodając następujący wiersz do sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="2b4d5-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="2b4d5-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="2b4d5-107">Scope</span></span>|<span data-ttu-id="2b4d5-108">Mały</span><span class="sxs-lookup"><span data-stu-id="2b4d5-108">Minor</span></span>|
|<span data-ttu-id="2b4d5-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="2b4d5-109">Version</span></span>|<span data-ttu-id="2b4d5-110">4.7.1</span><span class="sxs-lookup"><span data-stu-id="2b4d5-110">4.7.1</span></span>|
|<span data-ttu-id="2b4d5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="2b4d5-111">Type</span></span>|<span data-ttu-id="2b4d5-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2b4d5-112">Runtime</span></span>|
