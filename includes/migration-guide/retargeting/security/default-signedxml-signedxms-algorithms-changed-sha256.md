---
ms.openlocfilehash: e2ae329d027d605e6331afe422e550990fab1042
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614810"
---
### <a name="default-signedxml-and-signedxms-algorithms-changed-to-sha256"></a><span data-ttu-id="4c400-101">Domyślne algorytmy SignedXML i SignedXMS zostały zmienione na SHA256</span><span class="sxs-lookup"><span data-stu-id="4c400-101">Default SignedXML and SignedXMS algorithms changed to SHA256</span></span>

#### <a name="details"></a><span data-ttu-id="4c400-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4c400-102">Details</span></span>

<span data-ttu-id="4c400-103">W .NET Framework 4,7 i starszych SignedXML i SignedCMS domyślnie SHA1 dla niektórych operacji. Począwszy od .NET Framework 4.7.1, SHA256 jest domyślnie włączone dla tych operacji.</span><span class="sxs-lookup"><span data-stu-id="4c400-103">In the .NET Framework 4.7 and earlier, SignedXML and SignedCMS default to SHA1 for some operations.Starting with the .NET Framework 4.7.1, SHA256 is enabled by default for these operations.</span></span> <span data-ttu-id="4c400-104">Ta zmiana jest konieczna, ponieważ algorytm SHA1 nie jest już uznawany za bezpieczny.</span><span class="sxs-lookup"><span data-stu-id="4c400-104">This change is necessary because SHA1 is no longer considered to be secure.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4c400-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4c400-105">Suggestion</span></span>

<span data-ttu-id="4c400-106">Istnieją dwie nowe wartości przełącznika kontekstu, które umożliwiają kontrolowanie, czy algorytm SHA1 (niezabezpieczony) lub SHA256 jest używany domyślnie:</span><span class="sxs-lookup"><span data-stu-id="4c400-106">There are two new context switch values to control whether SHA1 (insecure) or SHA256 is used by default:</span></span>

- <span data-ttu-id="4c400-107">Switch.System.Security.Cryptography.Xml. UseInsecureHashAlgorithms</span><span class="sxs-lookup"><span data-stu-id="4c400-107">Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms</span></span>
- <span data-ttu-id="4c400-108">Switch.System Security. Cryptography. PKCS. UseInsecureHashAlgorithms dla aplikacji, które są przeznaczone dla .NET Framework 4.7.1 i nowszych wersji, jeśli użycie SHA256 jest niepożądane, można przywrócić wartość domyślną SHA1, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4c400-108">Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms For applications that target the .NET Framework 4.7.1 and later versions, if the use of SHA256 is undesirable, you can restore the default to SHA1 by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=true;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=true" />
```

<span data-ttu-id="4c400-109">W przypadku aplikacji przeznaczonych dla .NET Framework 4,7 i starszych wersji można przystąpić do tej zmiany, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="4c400-109">For applications that target the .NET Framework 4.7 and earlier versions, you can opt into this change by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.UseInsecureHashAlgorithms=false;Switch.System.Security.Cryptography.Pkcs.UseInsecureHashAlgorithms=false" />
```

| <span data-ttu-id="4c400-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4c400-110">Name</span></span>    | <span data-ttu-id="4c400-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="4c400-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4c400-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="4c400-112">Scope</span></span>   | <span data-ttu-id="4c400-113">Mały</span><span class="sxs-lookup"><span data-stu-id="4c400-113">Minor</span></span>       |
| <span data-ttu-id="4c400-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="4c400-114">Version</span></span> | <span data-ttu-id="4c400-115">4.7.1</span><span class="sxs-lookup"><span data-stu-id="4c400-115">4.7.1</span></span>       |
| <span data-ttu-id="4c400-116">Typ</span><span class="sxs-lookup"><span data-stu-id="4c400-116">Type</span></span>    | <span data-ttu-id="4c400-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="4c400-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="4c400-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4c400-118">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.CmsSigner?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=nameWithType>
- <xref:System.Security.Cryptography.Xml.Reference?displayProperty=nameWithType>
