---
ms.openlocfilehash: c646372104457e8bc5d418744847f3ee771c8d8b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614805"
---
### <a name="wcf-message-security-now-is-able-to-use-tls11-and-tls12"></a><span data-ttu-id="3810e-101">Zabezpieczenia komunikatów WCF mogą teraz korzystać z protokołów TLS 1.1 i TLS 1.2</span><span class="sxs-lookup"><span data-stu-id="3810e-101">WCF message security now is able to use TLS1.1 and TLS1.2</span></span>

#### <a name="details"></a><span data-ttu-id="3810e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3810e-102">Details</span></span>

<span data-ttu-id="3810e-103">Począwszy od .NET Framework 4,7, klienci mogą skonfigurować protokół TLS 1.1 lub TLS 1.2 w zabezpieczeniach komunikatów WCF oprócz protokołów SSL 3.0 i TLS 1.0 za pośrednictwem ustawień konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3810e-103">Starting in the .NET Framework 4.7, customers can configure either TLS1.1 or TLS1.2 in WCF message security in addition to SSL3.0 and TLS1.0 through application configuration settings.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3810e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3810e-104">Suggestion</span></span>

<span data-ttu-id="3810e-105">W .NET Framework 4,7 Obsługa protokołu TLS 1.1 i TLS 1.2 w zabezpieczeniach komunikatów WCF jest domyślnie wyłączona.</span><span class="sxs-lookup"><span data-stu-id="3810e-105">In the .NET Framework 4.7, support for TLS1.1 and TLS1.2 in WCF message security is disabled by default.</span></span> <span data-ttu-id="3810e-106">Można ją włączyć, dodając następujący wiersz do `<runtime>` sekcji app.config lub web.config pliku:</span><span class="sxs-lookup"><span data-stu-id="3810e-106">You can enable it by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
<AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

| <span data-ttu-id="3810e-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3810e-107">Name</span></span>    | <span data-ttu-id="3810e-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="3810e-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3810e-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="3810e-109">Scope</span></span>   | <span data-ttu-id="3810e-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="3810e-110">Edge</span></span>        |
| <span data-ttu-id="3810e-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="3810e-111">Version</span></span> | <span data-ttu-id="3810e-112">4,7</span><span class="sxs-lookup"><span data-stu-id="3810e-112">4.7</span></span>         |
| <span data-ttu-id="3810e-113">Typ</span><span class="sxs-lookup"><span data-stu-id="3810e-113">Type</span></span>    | <span data-ttu-id="3810e-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="3810e-114">Retargeting</span></span> |
