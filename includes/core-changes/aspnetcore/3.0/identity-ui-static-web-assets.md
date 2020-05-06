---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041662"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="fe4ac-101">Tożsamość: interfejs użytkownika używa funkcji statyczne zasoby sieci Web</span><span class="sxs-lookup"><span data-stu-id="fe4ac-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="fe4ac-102">W ASP.NET Core 3,0 wprowadzono statyczną funkcję zasobów sieci Web i została ona przyjęta przez interfejs użytkownika tożsamości.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fe4ac-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="fe4ac-103">Change description</span></span>

<span data-ttu-id="fe4ac-104">W związku z tym interfejs użytkownika tożsamości przyjmuje funkcję statyczne elementy zawartości sieci Web:</span><span class="sxs-lookup"><span data-stu-id="fe4ac-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="fe4ac-105">Wybór struktury jest realizowany przy użyciu `IdentityUIFrameworkVersion` właściwości w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="fe4ac-106">Bootstrap 4 jest domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="fe4ac-107">Program ładowania początkowego 3 osiągnął koniec okresu istnienia i należy rozważyć migrację do obsługiwanej wersji.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fe4ac-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="fe4ac-108">Version introduced</span></span>

<span data-ttu-id="fe4ac-109">3.0</span><span class="sxs-lookup"><span data-stu-id="fe4ac-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fe4ac-110">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="fe4ac-110">Old behavior</span></span>

<span data-ttu-id="fe4ac-111">Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości był **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="fe4ac-112">Strukturę interfejsu użytkownika można skonfigurować przy użyciu parametru do wywołania `AddDefaultUI` metody w. `Startup.ConfigureServices`</span><span class="sxs-lookup"><span data-stu-id="fe4ac-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fe4ac-113">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="fe4ac-113">New behavior</span></span>

<span data-ttu-id="fe4ac-114">Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości jest **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="fe4ac-115">Struktura interfejsu użytkownika musi być skonfigurowana w pliku projektu, a nie w wywołaniu `AddDefaultUI` metody.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fe4ac-116">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="fe4ac-116">Reason for change</span></span>

<span data-ttu-id="fe4ac-117">Zastosowanie statycznej funkcji zasobów sieci Web wymaga, aby konfiguracja struktury interfejsu użytkownika była przenoszona do programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="fe4ac-118">Podjęcie decyzji dotyczącej struktury osadzania to decyzja w czasie kompilacji, a nie decyzja dotycząca środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fe4ac-119">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="fe4ac-119">Recommended action</span></span>

<span data-ttu-id="fe4ac-120">Przejrzyj interfejs użytkownika witryny, aby upewnić się, że nowe składniki ładowania początkowego 4 są zgodne.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="fe4ac-121">W razie potrzeby użyj właściwości `IdentityUIFrameworkVersion` programu MSBuild, aby przywrócić wartość Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="fe4ac-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="fe4ac-122">Dodaj właściwość do `<PropertyGroup>` elementu w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="fe4ac-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="fe4ac-123">Kategoria</span><span class="sxs-lookup"><span data-stu-id="fe4ac-123">Category</span></span>

<span data-ttu-id="fe4ac-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fe4ac-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fe4ac-125">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="fe4ac-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
