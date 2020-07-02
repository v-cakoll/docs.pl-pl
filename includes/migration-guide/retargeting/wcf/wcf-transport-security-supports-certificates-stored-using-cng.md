---
ms.openlocfilehash: 5c09bee92f679cd7e7a95cd23d5ce0ca9b57170c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614742"
---
### <a name="wcf-transport-security-supports-certificates-stored-using-cng"></a><span data-ttu-id="192e4-101">Zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu CNG</span><span class="sxs-lookup"><span data-stu-id="192e4-101">WCF transport security supports certificates stored using CNG</span></span>

#### <a name="details"></a><span data-ttu-id="192e4-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="192e4-102">Details</span></span>

<span data-ttu-id="192e4-103">Począwszy od aplikacji przeznaczonych dla .NET Framework 4.6.2, zabezpieczenia transportu WCF obsługują certyfikaty przechowywane przy użyciu biblioteki kryptografii systemu Windows (CNG).</span><span class="sxs-lookup"><span data-stu-id="192e4-103">Starting with apps that target the .NET Framework 4.6.2, WCF transport security supports certificates stored using the Windows Cryptography Library (CNG).</span></span> <span data-ttu-id="192e4-104">Ta obsługa jest ograniczona do certyfikatów z kluczem publicznym o wykładniku nie większym niż 32 bitów.</span><span class="sxs-lookup"><span data-stu-id="192e4-104">This support is limited to certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="192e4-105">Gdy aplikacja jest przeznaczona dla .NET Framework 4.6.2, ta funkcja jest domyślnie włączona. We wcześniejszych wersjach .NET Framework próba użycia certyfikatów x509 z dostawcą magazynu kluczy CSG zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="192e4-105">When an application targets the .NET Framework 4.6.2, this feature is on by default.In earlier versions of the .NET Framework, the attempt to use X509 certificates with a CSG key storage provider throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="192e4-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="192e4-106">Suggestion</span></span>

<span data-ttu-id="192e4-107">Aplikacje, które są przeznaczone dla .NET Framework 4.6.1 i wcześniejszych, ale działają na .NET Framework 4.6.2 mogą włączyć obsługę certyfikatów CNG, dodając następujący wiersz do `<runtime>` sekcji pliku app.config lub web.config:</span><span class="sxs-lookup"><span data-stu-id="192e4-107">Apps that target the .NET Framework 4.6.1 and earlier but are running on the .NET Framework 4.6.2 can enable support for CNG certificates by adding the following line to the `<runtime>` section of the app.config or web.config file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableCngCertificates=false" />
</runtime>
```

<span data-ttu-id="192e4-108">Można to również zrobić programowo przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="192e4-108">This can also be done programmatically with the following code:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificate";

AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="192e4-109">Należy zauważyć, że ze względu na tę zmianę wszelki kod obsługi wyjątków, który zależy od próby zainicjowania bezpiecznej komunikacji z certyfikatem CNG do niepowodzenia, nie będzie już wykonywany.</span><span class="sxs-lookup"><span data-stu-id="192e4-109">Note that, because of this change, any exception handling code that depends on the attempt to initiate secure communication with a CNG certificate to fail will no longer execute.</span></span>

| <span data-ttu-id="192e4-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="192e4-110">Name</span></span>    | <span data-ttu-id="192e4-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="192e4-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="192e4-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="192e4-112">Scope</span></span>   | <span data-ttu-id="192e4-113">Mały</span><span class="sxs-lookup"><span data-stu-id="192e4-113">Minor</span></span>       |
| <span data-ttu-id="192e4-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="192e4-114">Version</span></span> | <span data-ttu-id="192e4-115">4.6.2</span><span class="sxs-lookup"><span data-stu-id="192e4-115">4.6.2</span></span>       |
| <span data-ttu-id="192e4-116">Typ</span><span class="sxs-lookup"><span data-stu-id="192e4-116">Type</span></span>    | <span data-ttu-id="192e4-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="192e4-117">Retargeting</span></span> |
