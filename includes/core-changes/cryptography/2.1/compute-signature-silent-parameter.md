---
ms.openlocfilehash: 9583d868ee01117d7bd6e465e7d89a734489d1a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449229"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="4515a-101">Przestrzegany jest parametr logiczny podpisu SignedCms.ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="4515a-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="4515a-102">W .NET Core jest `silent` przestrzegana <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametr logiczny metody.</span><span class="sxs-lookup"><span data-stu-id="4515a-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="4515a-103">Monit o numer PIN nie `true`jest wyświetlany, jeśli ten parametr jest ustawiony na .</span><span class="sxs-lookup"><span data-stu-id="4515a-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="4515a-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="4515a-104">Change description</span></span>

<span data-ttu-id="4515a-105">W platformie .NET `silent` Framework <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> parametr metody jest ignorowany, a monit o numer PIN jest zawsze wyświetlany, jeśli jest wymagany przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="4515a-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="4515a-106">W .NET Core `silent` parametr jest przestrzegany, `true`a jeśli jest ustawiona na , wiersz pin nigdy nie jest wyświetlany, nawet jeśli jest to wymagane przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="4515a-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="4515a-107">Obsługa komunikatów #7 CMS/PKCS została wprowadzona do programu .NET Core w wersji 2.1.</span><span class="sxs-lookup"><span data-stu-id="4515a-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="4515a-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="4515a-108">Version introduced</span></span>

<span data-ttu-id="4515a-109">2.1</span><span class="sxs-lookup"><span data-stu-id="4515a-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="4515a-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="4515a-110">Recommended action</span></span>

<span data-ttu-id="4515a-111">Aby upewnić się, że w razie potrzeby <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> pojawi się monit o numer PIN, aplikacje klasyczne powinny wywołać i ustawić parametr Logiczny na `false`.</span><span class="sxs-lookup"><span data-stu-id="4515a-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="4515a-112">Wynikowe zachowanie jest taka sama jak w .NET Framework niezależnie od tego, czy kontekst cichy jest tam wyłączony.</span><span class="sxs-lookup"><span data-stu-id="4515a-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

### <a name="category"></a><span data-ttu-id="4515a-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="4515a-113">Category</span></span>

<span data-ttu-id="4515a-114">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="4515a-114">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="4515a-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="4515a-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
