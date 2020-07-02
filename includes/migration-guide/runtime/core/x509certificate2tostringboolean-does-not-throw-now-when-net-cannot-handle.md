---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621322"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a><span data-ttu-id="3d108-101">X509Certificate2. ToString (wartość logiczna) nie jest teraz zgłaszana, gdy platforma .NET nie może obsłużyć certyfikatu</span><span class="sxs-lookup"><span data-stu-id="3d108-101">X509Certificate2.ToString(Boolean) does not throw now when .NET cannot handle the certificate</span></span>

#### <a name="details"></a><span data-ttu-id="3d108-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="3d108-102">Details</span></span>

<span data-ttu-id="3d108-103">W .NET Framework 4.5.2 i starszych wersjach ta metoda zostałaby <code>true</code> zgłoszona, jeśli została przeniesiona do parametru verbose i zainstalowano certyfikaty, które nie były obsługiwane przez .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3d108-103">In .NET Framework 4.5.2 and earlier versions, this method would throw if <code>true</code> was passed for the verbose parameter and there were certificates installed that weren't supported by the .NET Framework.</span></span> <span data-ttu-id="3d108-104">Teraz Metoda zakończy się pomyślnie i zwróci prawidłowy ciąg, który pomija niedostępne fragmenty certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="3d108-104">Now, the method will succeed and return a valid string that omits the inaccessible portions of the certificate.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="3d108-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="3d108-105">Suggestion</span></span>

<span data-ttu-id="3d108-106">Każdy kod w zależności od tego <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> należy zaktualizować, aby oczekiwać, że zwrócony ciąg może wykluczyć niektóre dane certyfikatu (takie jak klucz publiczny, klucz prywatny i rozszerzenia) w niektórych przypadkach, w których interfejs API zostałby wcześniej wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="3d108-106">Any code depending on <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> should be updated to expect that the returned string may exclude some certificate data (such as public key, private key, and extensions) in some cases in which the API would have previously thrown.</span></span>

| <span data-ttu-id="3d108-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3d108-107">Name</span></span>    | <span data-ttu-id="3d108-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="3d108-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="3d108-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="3d108-109">Scope</span></span>   |<span data-ttu-id="3d108-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="3d108-110">Edge</span></span>|
|<span data-ttu-id="3d108-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="3d108-111">Version</span></span>|<span data-ttu-id="3d108-112">4.6</span><span class="sxs-lookup"><span data-stu-id="3d108-112">4.6</span></span>|
|<span data-ttu-id="3d108-113">Typ</span><span class="sxs-lookup"><span data-stu-id="3d108-113">Type</span></span>|<span data-ttu-id="3d108-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="3d108-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3d108-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="3d108-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
