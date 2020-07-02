---
ms.openlocfilehash: 0e949cbdeda99dd7b94e919b903a21171a57f527
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614730"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a><span data-ttu-id="053c0-101">Powiązanie WCF z trybem zabezpieczeń TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="053c0-101">WCF binding with the TransportWithMessageCredential security mode</span></span>

#### <a name="details"></a><span data-ttu-id="053c0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="053c0-102">Details</span></span>

<span data-ttu-id="053c0-103">Począwszy od .NET Framework 4.6.1, powiązanie WCF korzystające z trybu zabezpieczeń TransportWithMessageCredential można skonfigurować do odbierania komunikatów z niepodpisanymi &quot; do &quot; nagłówków kluczy zabezpieczeń asymetrycznych. Domyślnie niepodpisane &quot; do &quot; nagłówków nadal będą odrzucane w .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="053c0-103">Beginning in the .NET Framework 4.6.1, WCF binding that uses the TransportWithMessageCredential security mode can be set up to receive messages with unsigned &quot;to&quot; headers for asymmetric security keys.By default, unsigned &quot;to&quot; headers will continue to be rejected in .NET Framework 4.6.1.</span></span> <span data-ttu-id="053c0-104">Zostaną one zaakceptowane tylko wtedy, gdy aplikacja zdecyduje się na ten nowy tryb operacji za pomocą Switch.System. Element ServiceModel. AllowUnsignedToHeader Configuration Switch.</span><span class="sxs-lookup"><span data-stu-id="053c0-104">They will only be accepted if an application opts into this new mode of operation using the Switch.System.ServiceModel.AllowUnsignedToHeader configuration switch.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="053c0-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="053c0-105">Suggestion</span></span>

<span data-ttu-id="053c0-106">Ponieważ jest to funkcja opcjonalna, nie powinna mieć wpływu na zachowanie istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="053c0-106">Because this is an opt-in feature, it should not affect the behavior of existing apps.</span></span><br/><span data-ttu-id="053c0-107">Aby kontrolować, czy nowe zachowanie jest używane, użyj następującego ustawienia konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="053c0-107">To control whether the new behavior is used or not, use the following configuration setting:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.AllowUnsignedToHeader=true" />
</runtime>
```

| <span data-ttu-id="053c0-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="053c0-108">Name</span></span>    | <span data-ttu-id="053c0-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="053c0-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="053c0-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="053c0-110">Scope</span></span>   | <span data-ttu-id="053c0-111">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="053c0-111">Transparent</span></span> |
| <span data-ttu-id="053c0-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="053c0-112">Version</span></span> | <span data-ttu-id="053c0-113">4.6.1</span><span class="sxs-lookup"><span data-stu-id="053c0-113">4.6.1</span></span>       |
| <span data-ttu-id="053c0-114">Typ</span><span class="sxs-lookup"><span data-stu-id="053c0-114">Type</span></span>    | <span data-ttu-id="053c0-115">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="053c0-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="053c0-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="053c0-116">Affected APIs</span></span>

- <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType>
