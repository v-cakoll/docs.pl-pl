---
ms.openlocfilehash: c996dafcf65b1fd428be908be346de603ead6e0b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615683"
---
### <a name="certificate-eku-oid-validation"></a><span data-ttu-id="29bf8-101">Walidacja identyfikatora OID certyfikatu EKU</span><span class="sxs-lookup"><span data-stu-id="29bf8-101">Certificate EKU OID validation</span></span>

#### <a name="details"></a><span data-ttu-id="29bf8-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="29bf8-102">Details</span></span>

<span data-ttu-id="29bf8-103">Począwszy od .NET Framework 4,6, <xref:System.Net.Security.SslStream> klasy lub <xref:System.Net.ServicePointManager> służą do wykonywania walidacji identyfikatora obiektu (EKU) ulepszonego użycia klucza.</span><span class="sxs-lookup"><span data-stu-id="29bf8-103">Starting with .NET Framework 4.6, the <xref:System.Net.Security.SslStream> or <xref:System.Net.ServicePointManager> classes perform enhanced key use (EKU) object identifier (OID) validation.</span></span> <span data-ttu-id="29bf8-104">Rozszerzenie ulepszonego użycia klucza (EKU) to zbiór identyfikatorów obiektów (OID) wskazujący aplikacje, które używają klucza.</span><span class="sxs-lookup"><span data-stu-id="29bf8-104">An enhanced key usage (EKU) extension is a collection of object identifiers (OIDs) that indicate the applications that use the key.</span></span> <span data-ttu-id="29bf8-105">Walidacja identyfikatora OID rozszerzenia EKU używa zdalnego wywołania zwrotnego certyfikatu w celu upewnienia się, że certyfikat zdalny ma poprawne identyfikatory OID dla zamierzonego celu.</span><span class="sxs-lookup"><span data-stu-id="29bf8-105">EKU OID validation uses remote certificate callbacks to ensure that the remote certificate has the correct OIDs for the intended purpose.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="29bf8-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="29bf8-106">Suggestion</span></span>

<span data-ttu-id="29bf8-107">Jeśli ta zmiana jest niepożądana, można wyłączyć weryfikację identyfikatorów OID certyfikatu, dodając następujący przełącznik do [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) pliku konfiguracji aplikacji:</span><span class="sxs-lookup"><span data-stu-id="29bf8-107">If this change is undesirable, you can disable certificate EKU OID validation by adding the following switch to the [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) in the [\`](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md) of your app configuration file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Net.DontCheckCertificateEKUs=true" />
</runtime>
```

> [!IMPORTANT]
> <span data-ttu-id="29bf8-108">To ustawienie jest dostępne wyłącznie w celu zapewnienia zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="29bf8-108">This setting is provided for backward compatibility only.</span></span> <span data-ttu-id="29bf8-109">Jego użycie nie jest zalecane.</span><span class="sxs-lookup"><span data-stu-id="29bf8-109">Its use is otherwise not recommended.</span></span>

| <span data-ttu-id="29bf8-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="29bf8-110">Name</span></span>    | <span data-ttu-id="29bf8-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="29bf8-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="29bf8-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="29bf8-112">Scope</span></span>   | <span data-ttu-id="29bf8-113">Mały</span><span class="sxs-lookup"><span data-stu-id="29bf8-113">Minor</span></span>       |
| <span data-ttu-id="29bf8-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="29bf8-114">Version</span></span> | <span data-ttu-id="29bf8-115">4.6</span><span class="sxs-lookup"><span data-stu-id="29bf8-115">4.6</span></span>         |
| <span data-ttu-id="29bf8-116">Typ</span><span class="sxs-lookup"><span data-stu-id="29bf8-116">Type</span></span>    | <span data-ttu-id="29bf8-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="29bf8-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="29bf8-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="29bf8-118">Affected APIs</span></span>

- <xref:System.Net.Security.SslStream?displayProperty=nameWithType>
- <xref:System.Net.ServicePointManager?displayProperty=nameWithType>
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>
- <xref:System.Net.FtpWebRequest?displayProperty=nameWithType>
