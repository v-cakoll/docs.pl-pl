---
ms.openlocfilehash: 3b7b50700541649a785fa9bbe3ecc56c2697fbfc
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760272"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="91988-101">Zabezpieczenie wiadomości WCF teraz jest w stanie używać TLS1.1 i TLS1.2</span><span class="sxs-lookup"><span data-stu-id="91988-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

|   |   |
|---|---|
|<span data-ttu-id="91988-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="91988-102">Details</span></span>|<span data-ttu-id="91988-103">Począwszy od programu .NET Framework 4.7, klienci mogą skonfigurować TLS1.1 lub TLS1.2 w ramach zabezpieczeń komunikatów WCF oprócz SSL3.0 i TLS1.0 przy użyciu ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="91988-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>|
|<span data-ttu-id="91988-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="91988-104">Suggestion</span></span>|<span data-ttu-id="91988-105">W programie .NET Framework 4.7 Obsługa TLS1.1 i TLS1.2 w ramach zabezpieczeń komunikatów WCF jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="91988-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="91988-106">Możesz je włączyć, dodając następujący wiersz do <code>&lt;runtime&gt;</code> sekcji w pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="91988-106">You can enable it by adding the following line to the <code>&lt;runtime&gt;</code> section of the app.config or web.config file:</span></span><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|<span data-ttu-id="91988-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="91988-107">Scope</span></span>|<span data-ttu-id="91988-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="91988-108">Edge</span></span>|
|<span data-ttu-id="91988-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="91988-109">Version</span></span>|<span data-ttu-id="91988-110">4.7</span><span class="sxs-lookup"><span data-stu-id="91988-110">4.7</span></span>|
|<span data-ttu-id="91988-111">Typ</span><span class="sxs-lookup"><span data-stu-id="91988-111">Type</span></span>|<span data-ttu-id="91988-112">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="91988-112">Retargeting</span></span>|

