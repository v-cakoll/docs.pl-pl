---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522666"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="29e9d-101">Tożsamość: Usunięto Przeciążenie metody AddDefaultUI</span><span class="sxs-lookup"><span data-stu-id="29e9d-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="29e9d-102">Począwszy od ASP.NET Core 3,0, Przeciążenie metody <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="29e9d-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29e9d-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="29e9d-103">Version introduced</span></span>

<span data-ttu-id="29e9d-104">3.0</span><span class="sxs-lookup"><span data-stu-id="29e9d-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="29e9d-105">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="29e9d-105">Reason for change</span></span>

<span data-ttu-id="29e9d-106">Ta zmiana była wynikiem przyjęcia funkcji statyczne elementy zawartości sieci Web.</span><span class="sxs-lookup"><span data-stu-id="29e9d-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29e9d-107">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="29e9d-107">Recommended action</span></span>

<span data-ttu-id="29e9d-108">Wywołaj <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> zamiast przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="29e9d-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="29e9d-109">Jeśli używasz narzędzia Bootstrap 3, Dodaj również następujący wiersz do `<PropertyGroup>` elementu w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="29e9d-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="29e9d-110">Kategoria</span><span class="sxs-lookup"><span data-stu-id="29e9d-110">Category</span></span>

<span data-ttu-id="29e9d-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29e9d-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29e9d-112">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="29e9d-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
