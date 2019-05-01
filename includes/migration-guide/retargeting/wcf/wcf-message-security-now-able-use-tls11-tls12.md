---
ms.openlocfilehash: 0a3dc43ebdc58d54675f2264a8ee56d9f4358cd8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61759512"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="91ea1-101">Zabezpieczenie wiadomości WCF teraz jest w stanie używać TLS1.1 i TLS1.2</span><span class="sxs-lookup"><span data-stu-id="91ea1-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="91ea1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="91ea1-102">Details</span></span>|<span data-ttu-id="91ea1-103">Począwszy od programu .NET Framework 4.7, klienci mogą skonfigurować TLS1.1 lub TLS1.2 w ramach zabezpieczeń komunikatów WCF oprócz SSL3.0 i TLS1.0 przy użyciu ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91ea1-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="91ea1-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="91ea1-104">Suggestion</span></span>|<span data-ttu-id="91ea1-105">W programie .NET Framework 4.7 Obsługa TLS1.1 i TLS1.2 w ramach zabezpieczeń komunikatów WCF jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="91ea1-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="91ea1-106">Możesz je włączyć, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="91ea1-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="91ea1-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="91ea1-107">Scope</span></span>|<span data-ttu-id="91ea1-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="91ea1-108">Edge</span></span>|
|<span data-ttu-id="91ea1-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="91ea1-109">Version</span></span>|<span data-ttu-id="91ea1-110">4.7</span><span class="sxs-lookup"><span data-stu-id="91ea1-110">4.7</span></span>|
|<span data-ttu-id="91ea1-111">Typ</span><span class="sxs-lookup"><span data-stu-id="91ea1-111">Type</span></span>|<span data-ttu-id="91ea1-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="91ea1-112">Retargeting</span></span>|
