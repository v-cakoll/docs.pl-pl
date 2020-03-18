---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041662"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="d840b-101">Tożsamość: interfejs użytkowników interfejsu używa funkcji statycznych zasobów sieci Web</span><span class="sxs-lookup"><span data-stu-id="d840b-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="d840b-102">ASP.NET Core 3.0 wprowadziła funkcję statycznych zasobów sieci web, a interfejs tożsamości ją przyjął.</span><span class="sxs-lookup"><span data-stu-id="d840b-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d840b-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d840b-103">Change description</span></span>

<span data-ttu-id="d840b-104">W wyniku interfejsu tożsamości przyjęcia funkcji statycznych zasobów sieci web:</span><span class="sxs-lookup"><span data-stu-id="d840b-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="d840b-105">Wybór struktury odbywa się `IdentityUIFrameworkVersion` przy użyciu właściwości w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="d840b-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="d840b-106">Bootstrap 4 jest domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości.</span><span class="sxs-lookup"><span data-stu-id="d840b-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="d840b-107">Bootstrap 3 osiągnął koniec życia i należy rozważyć migrację do obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="d840b-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d840b-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d840b-108">Version introduced</span></span>

<span data-ttu-id="d840b-109">3.0</span><span class="sxs-lookup"><span data-stu-id="d840b-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d840b-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="d840b-110">Old behavior</span></span>

<span data-ttu-id="d840b-111">Domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości był **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="d840b-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="d840b-112">Platformę interfejsu użytkownika można skonfigurować przy `AddDefaultUI` użyciu parametru do wywołania metody w . `Startup.ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="d840b-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d840b-113">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="d840b-113">New behavior</span></span>

<span data-ttu-id="d840b-114">Domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości jest **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="d840b-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="d840b-115">Struktura interfejsu użytkownika musi być skonfigurowana w pliku `AddDefaultUI` projektu, a nie w wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="d840b-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d840b-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="d840b-116">Reason for change</span></span>

<span data-ttu-id="d840b-117">Przyjęcie funkcji statycznych zasobów sieci web wymagane, że konfiguracja struktury interfejsu użytkownika przenieść do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d840b-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="d840b-118">Decyzja, które ramy do osadzenie jest decyzja w czasie kompilacji, a nie decyzji runtime.</span><span class="sxs-lookup"><span data-stu-id="d840b-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d840b-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d840b-119">Recommended action</span></span>

<span data-ttu-id="d840b-120">Przejrzyj swój ui witryny, aby upewnić się, że nowe składniki Bootstrap 4 są kompatybilne.</span><span class="sxs-lookup"><span data-stu-id="d840b-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="d840b-121">W razie potrzeby `IdentityUIFrameworkVersion` użyj MSBuild właściwości, aby powrócić do Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="d840b-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="d840b-122">Dodaj właściwość do `<PropertyGroup>` elementu w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="d840b-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="d840b-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d840b-123">Category</span></span>

<span data-ttu-id="d840b-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d840b-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d840b-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d840b-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
