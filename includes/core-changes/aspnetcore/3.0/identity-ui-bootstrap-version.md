---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394104"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a>Tożsamość: Domyślna wersja Bootstrap interfejsu użytkownika zmieniona

Począwszy od ASP.NET Core 3.0, interfejsu tożsamości domyślnie przy użyciu wersji 4 Bootstrap.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Wywołanie `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody było takie samo jak`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`

#### <a name="new-behavior"></a>Nowe zachowanie

Wywołanie `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` metody jest takie samo jak wywołanie metody`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`

#### <a name="reason-for-change"></a>Przyczyna zmiany

Bootstrap 4 został wydany podczas ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana ma wpływ, jeśli używasz domyślnego interfejsu tożsamości i `Startup.ConfigureServices` dodano go w sposób pokazany w poniższym przykładzie:

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

Wykonaj jedno z następujących działań:

- Migruj aplikację, aby używać aplikacji Bootstrap 4, korzystając z [przewodnika migracji.](https://getbootstrap.com/docs/4.0/migration)
- Aktualizacja, `Startup.ConfigureServices` aby wymusić użycie Bootstrap 3. Przykład:

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
