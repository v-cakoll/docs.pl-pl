---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041662"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Tożsamość: interfejs użytkowników interfejsu używa funkcji statycznych zasobów sieci Web

ASP.NET Core 3.0 wprowadziła funkcję statycznych zasobów sieci web, a interfejs tożsamości ją przyjął.

#### <a name="change-description"></a>Zmień opis

W wyniku interfejsu tożsamości przyjęcia funkcji statycznych zasobów sieci web:

- Wybór struktury odbywa się `IdentityUIFrameworkVersion` przy użyciu właściwości w pliku projektu.
- Bootstrap 4 jest domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości. Bootstrap 3 osiągnął koniec życia i należy rozważyć migrację do obsługiwanej wersji.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości był **Bootstrap 3**. Platformę interfejsu użytkownika można skonfigurować przy `AddDefaultUI` użyciu parametru do wywołania metody w . `Startup.ConfigureServices`

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu tożsamości jest **Bootstrap 4**. Struktura interfejsu użytkownika musi być skonfigurowana w pliku `AddDefaultUI` projektu, a nie w wywołaniu metody.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Przyjęcie funkcji statycznych zasobów sieci web wymagane, że konfiguracja struktury interfejsu użytkownika przenieść do MSBuild. Decyzja, które ramy do osadzenie jest decyzja w czasie kompilacji, a nie decyzji runtime.

#### <a name="recommended-action"></a>Zalecana akcja

Przejrzyj swój ui witryny, aby upewnić się, że nowe składniki Bootstrap 4 są kompatybilne. W razie potrzeby `IdentityUIFrameworkVersion` użyj MSBuild właściwości, aby powrócić do Bootstrap 3. Dodaj właściwość do `<PropertyGroup>` elementu w pliku projektu:

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
