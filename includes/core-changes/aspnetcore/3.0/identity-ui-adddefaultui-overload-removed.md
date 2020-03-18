---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522666"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="46a7d-101">Tożsamość: usunięto przeciążenie metody AddDefaultUI</span><span class="sxs-lookup"><span data-stu-id="46a7d-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="46a7d-102">Począwszy od ASP.NET Core <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> 3.0, przeciążenie metody już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="46a7d-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="46a7d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="46a7d-103">Version introduced</span></span>

<span data-ttu-id="46a7d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="46a7d-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="46a7d-105">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="46a7d-105">Reason for change</span></span>

<span data-ttu-id="46a7d-106">Ta zmiana była wynikiem przyjęcia funkcji statycznych zasobów sieci web.</span><span class="sxs-lookup"><span data-stu-id="46a7d-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="46a7d-107">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="46a7d-107">Recommended action</span></span>

<span data-ttu-id="46a7d-108">Wywołanie <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> zamiast przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="46a7d-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="46a7d-109">Jeśli używasz programu Bootstrap 3, dodaj również `<PropertyGroup>` następujący wiersz do elementu w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="46a7d-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="46a7d-110">Kategoria</span><span class="sxs-lookup"><span data-stu-id="46a7d-110">Category</span></span>

<span data-ttu-id="46a7d-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="46a7d-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="46a7d-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="46a7d-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
