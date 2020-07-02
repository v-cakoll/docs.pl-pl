---
ms.openlocfilehash: 23e278d38d6904d8afe927e6b54c388d443e41f5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616095"
---
### <a name="signedxmlgetpublickey-returns-rsacng-on-net462-or-lightup-without-retargeting-change"></a><span data-ttu-id="f341a-101">SignedXml. GetPublicKey zwraca RSACng na net462 (lub lightup) bez przekierowania zmiany</span><span class="sxs-lookup"><span data-stu-id="f341a-101">SignedXml.GetPublicKey returns RSACng on net462 (or lightup) without retargeting change</span></span>

#### <a name="details"></a><span data-ttu-id="f341a-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="f341a-102">Details</span></span>

<span data-ttu-id="f341a-103">Rozpoczynając od .NET Framework 4.6.2, konkretny typ obiektu zwróconego przez <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> metodę został zmieniony (bez Quirk) z implementacji CryptoServiceProvider do implementacji CNG.</span><span class="sxs-lookup"><span data-stu-id="f341a-103">Starting with the .NET Framework 4.6.2, the concrete type of the object returned by the <xref:System.Security.Cryptography.Xml.SignedXml.GetPublicKey%2A?displayProperty=nameWithType> method changed (without a quirk) from a CryptoServiceProvider implementation to a Cng implementation.</span></span> <span data-ttu-id="f341a-104">Wynika to z faktu, że implementacja zmieniła się z użycia `certificate.PublicKey.Key` na do użycia wewnętrznego, `certificate.GetAnyPublicKey` do którego przekazuje <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f341a-104">This is because the implementation changed from using `certificate.PublicKey.Key` to using the internal `certificate.GetAnyPublicKey` which forwards to <xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey%2A?displayProperty=nameWithType>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="f341a-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="f341a-105">Suggestion</span></span>

<span data-ttu-id="f341a-106">Począwszy od aplikacji uruchomionych na .NET Framework 4.7.1 można użyć implementacji CryptoServiceProvider używanej domyślnie w .NET Framework 4.6.1 i starszych wersjach, dodając następujący przełącznik konfiguracji do sekcji [środowiska uruchomieniowego](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) w pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="f341a-106">Starting with apps running on the .NET Framework 4.7.1, you can use the CryptoServiceProvider implementation used by default in the .NET Framework 4.6.1 and earlier versions by adding the following configuration switch to the [runtime](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app config file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.Security.Cryptography.Xml.SignedXmlUseLegacyCertificatePrivateKey=true" />
```

| <span data-ttu-id="f341a-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f341a-107">Name</span></span>    | <span data-ttu-id="f341a-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="f341a-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="f341a-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="f341a-109">Scope</span></span>   | <span data-ttu-id="f341a-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="f341a-110">Edge</span></span>        |
| <span data-ttu-id="f341a-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="f341a-111">Version</span></span> | <span data-ttu-id="f341a-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="f341a-112">4.6.2</span></span>       |
| <span data-ttu-id="f341a-113">Typ</span><span class="sxs-lookup"><span data-stu-id="f341a-113">Type</span></span>    | <span data-ttu-id="f341a-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="f341a-114">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="f341a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="f341a-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Xml.SignedXml.CheckSignatureReturningKey(System.Security.Cryptography.AsymmetricAlgorithm@)?displayProperty=nameWithType>
