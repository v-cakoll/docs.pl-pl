---
ms.openlocfilehash: ccdf232d743c9e270b6ed21f698998eb95a97399
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621217"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a><span data-ttu-id="a9a35-101">Wartość domyślna MsmqSecureHashAlgorithm WCF jest teraz SHA256</span><span class="sxs-lookup"><span data-stu-id="a9a35-101">WCF MsmqSecureHashAlgorithm default value is now SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="a9a35-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a9a35-102">Details</span></span>

<span data-ttu-id="a9a35-103">Począwszy od .NET Framework 4.7.1, domyślny algorytm podpisywania komunikatów w programie WCF dla komunikatów usługi MSMQ to SHA256.</span><span class="sxs-lookup"><span data-stu-id="a9a35-103">Starting with the .NET Framework 4.7.1, the default message signing algorithm in WCF for Msmq messages is SHA256.</span></span> <span data-ttu-id="a9a35-104">W .NET Framework 4,7 i wcześniejszych wersjach domyślny algorytm podpisywania wiadomości to SHA1.</span><span class="sxs-lookup"><span data-stu-id="a9a35-104">In the .NET Framework 4.7 and earlier versions, the default message signing algorithm is SHA1.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a9a35-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a9a35-105">Suggestion</span></span>

<span data-ttu-id="a9a35-106">W przypadku wystąpienia problemów ze zgodnością z tą zmianą w .NET Framework 4.7.1 lub nowszym można zrezygnować z zmiany, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="a9a35-106">If you run into compatibility issues with this change on the .NET Framework 4.7.1 or later, you can opt-out the change by adding the following line to the <code>&lt;runtime&gt;</code>section of your app.config file:</span></span><pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="a9a35-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a9a35-107">Name</span></span>    | <span data-ttu-id="a9a35-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="a9a35-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a9a35-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="a9a35-109">Scope</span></span>   |<span data-ttu-id="a9a35-110">Mały</span><span class="sxs-lookup"><span data-stu-id="a9a35-110">Minor</span></span>|
|<span data-ttu-id="a9a35-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="a9a35-111">Version</span></span>|<span data-ttu-id="a9a35-112">4.7.1</span><span class="sxs-lookup"><span data-stu-id="a9a35-112">4.7.1</span></span>|
|<span data-ttu-id="a9a35-113">Typ</span><span class="sxs-lookup"><span data-stu-id="a9a35-113">Type</span></span>|<span data-ttu-id="a9a35-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a9a35-114">Runtime</span></span>|
