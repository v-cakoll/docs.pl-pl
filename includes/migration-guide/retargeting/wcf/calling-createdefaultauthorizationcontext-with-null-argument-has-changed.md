---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615711"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="66dce-101">Wywołanie CreateDefaultAuthorizationContext z pustym argumentem zostało zmienione</span><span class="sxs-lookup"><span data-stu-id="66dce-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="66dce-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="66dce-102">Details</span></span>

<span data-ttu-id="66dce-103">Implementacja <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> zwracanego przez wywołanie <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> z argumentem authorizationPolicies o wartości null zmieniła swoją implementację w .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="66dce-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="66dce-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="66dce-104">Suggestion</span></span>

<span data-ttu-id="66dce-105">W rzadkich przypadkach aplikacje WCF korzystające z uwierzytelniania niestandardowego mogą zobaczyć różnice w zachowaniu.</span><span class="sxs-lookup"><span data-stu-id="66dce-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="66dce-106">W takich przypadkach poprzednie zachowanie można przywrócić na jeden z dwóch sposobów:</span><span class="sxs-lookup"><span data-stu-id="66dce-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="66dce-107">Skompiluj ponownie aplikację pod kątem wcześniejszej wersji .NET Framework niż 4,6.</span><span class="sxs-lookup"><span data-stu-id="66dce-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="66dce-108">W przypadku usług hostowanych przez usługi IIS Użyj `<httpRuntime targetFramework="x.x">` elementu jako docelowego dla wcześniejszej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="66dce-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="66dce-109">Dodaj następujący wiersz do `<appSettings>` sekcji pliku app.config:</span><span class="sxs-lookup"><span data-stu-id="66dce-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="66dce-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="66dce-110">Name</span></span>    | <span data-ttu-id="66dce-111">Wartość</span><span class="sxs-lookup"><span data-stu-id="66dce-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="66dce-112">Zakres</span><span class="sxs-lookup"><span data-stu-id="66dce-112">Scope</span></span>   | <span data-ttu-id="66dce-113">Mały</span><span class="sxs-lookup"><span data-stu-id="66dce-113">Minor</span></span>       |
| <span data-ttu-id="66dce-114">Wersja</span><span class="sxs-lookup"><span data-stu-id="66dce-114">Version</span></span> | <span data-ttu-id="66dce-115">4.6</span><span class="sxs-lookup"><span data-stu-id="66dce-115">4.6</span></span>         |
| <span data-ttu-id="66dce-116">Typ</span><span class="sxs-lookup"><span data-stu-id="66dce-116">Type</span></span>    | <span data-ttu-id="66dce-117">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="66dce-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="66dce-118">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="66dce-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
