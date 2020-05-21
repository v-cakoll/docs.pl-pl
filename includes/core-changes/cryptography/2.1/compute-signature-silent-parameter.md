---
ms.openlocfilehash: b861dbaa02c97a03c015fdf4e63d25c40c90ea0a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721202"
---
### <a name="boolean-parameter-of-signedcmscomputesignature-is-respected"></a><span data-ttu-id="a81b2-101">Parametr logiczny elementu SignedCms. ComputeSignature jest przestrzegany</span><span class="sxs-lookup"><span data-stu-id="a81b2-101">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>

<span data-ttu-id="a81b2-102">W programie .NET Core `silent` <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> jest przestrzegany parametr Boolean metody.</span><span class="sxs-lookup"><span data-stu-id="a81b2-102">In .NET Core, the Boolean `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is respected.</span></span> <span data-ttu-id="a81b2-103">Monit o podanie numeru PIN nie jest wyświetlany, jeśli ten parametr jest ustawiony na `true` .</span><span class="sxs-lookup"><span data-stu-id="a81b2-103">A PIN prompt is not shown if this parameter is set to `true`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a81b2-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a81b2-104">Change description</span></span>

<span data-ttu-id="a81b2-105">W .NET Framework `silent` parametr <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> metody jest ignorowany, a monit o podanie numeru PIN jest zawsze wyświetlany, jeśli jest to wymagane przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="a81b2-105">In .NET Framework, the `silent` parameter of the <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> method is ignored, and a PIN prompt is always shown if required by the provider.</span></span> <span data-ttu-id="a81b2-106">W przypadku platformy .NET Core `silent` parametr jest przestrzegany, a w przypadku ustawienia opcji monit o podanie `true` numeru PIN nigdy nie jest wyświetlany, nawet jeśli jest wymagany przez dostawcę.</span><span class="sxs-lookup"><span data-stu-id="a81b2-106">In .NET Core, the `silent` parameter is respected, and if set to `true`, a PIN prompt is never shown, even if it's required by the provider.</span></span>

<span data-ttu-id="a81b2-107">Obsługa komunikatów CMS/PKCS #7 została wprowadzona do programu .NET Core w wersji 2,1.</span><span class="sxs-lookup"><span data-stu-id="a81b2-107">Support for CMS/PKCS #7 messages was introduced into .NET Core in version 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a81b2-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="a81b2-108">Version introduced</span></span>

<span data-ttu-id="a81b2-109">2.1</span><span class="sxs-lookup"><span data-stu-id="a81b2-109">2.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a81b2-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a81b2-110">Recommended action</span></span>

<span data-ttu-id="a81b2-111">Aby zapewnić, że w razie potrzeby będzie wyświetlany monit o podanie numeru PIN, aplikacje klasyczne powinny wywołać <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> i ustawić parametr logiczny `false` .</span><span class="sxs-lookup"><span data-stu-id="a81b2-111">To ensure a PIN prompt appears if required, desktop applications should call <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> and set the Boolean parameter to `false`.</span></span> <span data-ttu-id="a81b2-112">Zachowanie rezultatowe jest takie samo jak w przypadku .NET Framework niezależnie od tego, czy kontekst dyskretny jest wyłączony.</span><span class="sxs-lookup"><span data-stu-id="a81b2-112">The resulting behavior is the same as on .NET Framework regardless of whether the silent context is disabled there.</span></span>

#### <a name="category"></a><span data-ttu-id="a81b2-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a81b2-113">Category</span></span>

<span data-ttu-id="a81b2-114">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="a81b2-114">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a81b2-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a81b2-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)`

-->
