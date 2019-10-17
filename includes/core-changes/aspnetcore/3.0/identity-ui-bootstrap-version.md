---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394104"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="214b6-101">Tożsamość: domyślna wersja użytkownika Bootstrap została zmieniona</span><span class="sxs-lookup"><span data-stu-id="214b6-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="214b6-102">Począwszy od ASP.NET Core 3,0, interfejs użytkownika tożsamości jest domyślnie używany w wersji 4 programu Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="214b6-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="214b6-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="214b6-103">Version introduced</span></span>

<span data-ttu-id="214b6-104">3.0</span><span class="sxs-lookup"><span data-stu-id="214b6-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="214b6-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="214b6-105">Old behavior</span></span>

<span data-ttu-id="214b6-106">Wywołanie metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` jest takie samo jak `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="214b6-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="214b6-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="214b6-107">New behavior</span></span>

<span data-ttu-id="214b6-108">Wywołanie metody `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` jest takie samo jak `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="214b6-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="214b6-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="214b6-109">Reason for change</span></span>

<span data-ttu-id="214b6-110">Uruchomienie Bootstrap 4 zostało wydane w okresie ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="214b6-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="214b6-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="214b6-111">Recommended action</span></span>

<span data-ttu-id="214b6-112">Ta zmiana ma wpływ na tę zmianę, jeśli używany jest domyślny interfejs użytkownika tożsamości i dodano go w `Startup.ConfigureServices`, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="214b6-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="214b6-113">Wykonaj jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="214b6-113">Take one of the following actions:</span></span>

- <span data-ttu-id="214b6-114">Przeprowadź migrację aplikacji, aby użyć ładowania początkowego 4 przy użyciu ich [przewodnika migracji](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="214b6-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="214b6-115">Aktualizacja `Startup.ConfigureServices` w celu wymuszenia użycia narzędzia Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="214b6-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="214b6-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="214b6-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="214b6-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="214b6-117">Category</span></span>

<span data-ttu-id="214b6-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="214b6-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="214b6-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="214b6-119">Affected APIs</span></span>

<span data-ttu-id="214b6-120">Brak</span><span class="sxs-lookup"><span data-stu-id="214b6-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
