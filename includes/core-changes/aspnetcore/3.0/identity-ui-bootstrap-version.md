---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394104"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="81db0-101">Tożsamość: Domyślna wersja Bootstrap interfejsu użytkownika zmieniona</span><span class="sxs-lookup"><span data-stu-id="81db0-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="81db0-102">Począwszy od ASP.NET Core 3.0, interfejsu tożsamości domyślnie przy użyciu wersji 4 Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="81db0-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81db0-103">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="81db0-103">Version introduced</span></span>

<span data-ttu-id="81db0-104">3.0</span><span class="sxs-lookup"><span data-stu-id="81db0-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="81db0-105">Stare zachowanie</span><span class="sxs-lookup"><span data-stu-id="81db0-105">Old behavior</span></span>

<span data-ttu-id="81db0-106">Wywołanie `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody było takie samo jak`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="81db0-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="81db0-107">Nowe zachowanie</span><span class="sxs-lookup"><span data-stu-id="81db0-107">New behavior</span></span>

<span data-ttu-id="81db0-108">Wywołanie `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody jest takie samo jak wywołanie metody`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="81db0-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="81db0-109">Przyczyna zmiany</span><span class="sxs-lookup"><span data-stu-id="81db0-109">Reason for change</span></span>

<span data-ttu-id="81db0-110">Bootstrap 4 został wydany podczas ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="81db0-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="81db0-111">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="81db0-111">Recommended action</span></span>

<span data-ttu-id="81db0-112">Ta zmiana ma wpływ, jeśli używasz domyślnego interfejsu tożsamości i `Startup.ConfigureServices` dodano go w sposób pokazany w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="81db0-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="81db0-113">Wykonaj jedno z następujących działań:</span><span class="sxs-lookup"><span data-stu-id="81db0-113">Take one of the following actions:</span></span>

- <span data-ttu-id="81db0-114">Migruj aplikację, aby używać aplikacji Bootstrap 4, korzystając z [przewodnika migracji.](https://getbootstrap.com/docs/4.0/migration)</span><span class="sxs-lookup"><span data-stu-id="81db0-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="81db0-115">Aktualizacja, `Startup.ConfigureServices` aby wymusić użycie Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="81db0-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="81db0-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="81db0-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="81db0-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="81db0-117">Category</span></span>

<span data-ttu-id="81db0-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="81db0-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="81db0-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="81db0-119">Affected APIs</span></span>

<span data-ttu-id="81db0-120">Brak</span><span class="sxs-lookup"><span data-stu-id="81db0-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
