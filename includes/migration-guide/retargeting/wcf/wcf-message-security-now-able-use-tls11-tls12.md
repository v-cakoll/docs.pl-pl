---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859074"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="15be4-101">Zabezpieczenia wiadomości WCF mogą teraz używać TLS1.1 i TLS1.2</span><span class="sxs-lookup"><span data-stu-id="15be4-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="15be4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="15be4-102">Details</span></span>|<span data-ttu-id="15be4-103">Począwszy od programu .NET Framework 4.7, klienci mogą konfigurować tls1.1 lub TLS1.2 w zabezpieczeniach wiadomości WCF oprócz SSL3.0 i TLS1.0 za pomocą ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="15be4-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="15be4-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="15be4-104">Suggestion</span></span>|<span data-ttu-id="15be4-105">W .NET Framework 4.7 obsługa TLS1.1 i TLS1.2 w zabezpieczeniach komunikatów WCF jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="15be4-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="15be4-106">Można go włączyć, dodając następujący <code>&lt;runtime&gt;</code> wiersz do sekcji pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="15be4-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="15be4-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="15be4-107">Scope</span></span>|<span data-ttu-id="15be4-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="15be4-108">Edge</span></span>|
|<span data-ttu-id="15be4-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="15be4-109">Version</span></span>|<span data-ttu-id="15be4-110">4.7</span><span class="sxs-lookup"><span data-stu-id="15be4-110">4.7</span></span>|
|<span data-ttu-id="15be4-111">Typ</span><span class="sxs-lookup"><span data-stu-id="15be4-111">Type</span></span>|<span data-ttu-id="15be4-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="15be4-112">Retargeting</span></span>|
