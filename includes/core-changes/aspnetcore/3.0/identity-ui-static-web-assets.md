---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041662"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Tożsamość: interfejs użytkownika używa funkcji statyczne zasoby sieci Web

W ASP.NET Core 3,0 wprowadzono statyczną funkcję zasobów sieci Web i została ona przyjęta przez interfejs użytkownika tożsamości.

#### <a name="change-description"></a>Zmień opis

W związku z tym interfejs użytkownika tożsamości przyjmuje funkcję statyczne elementy zawartości sieci Web:

- Wybór struktury jest realizowany przy użyciu `IdentityUIFrameworkVersion` właściwości w pliku projektu.
- Bootstrap 4 jest domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości. Program ładowania początkowego 3 osiągnął koniec okresu istnienia i należy rozważyć migrację do obsługiwanej wersji.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości był **Bootstrap 3**. Strukturę interfejsu użytkownika można skonfigurować przy użyciu parametru do wywołania `AddDefaultUI` metody w. `Startup.ConfigureServices`

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości jest **Bootstrap 4**. Struktura interfejsu użytkownika musi być skonfigurowana w pliku projektu, a nie w wywołaniu `AddDefaultUI` metody.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zastosowanie statycznej funkcji zasobów sieci Web wymaga, aby konfiguracja struktury interfejsu użytkownika była przenoszona do programu MSBuild. Podjęcie decyzji dotyczącej struktury osadzania to decyzja w czasie kompilacji, a nie decyzja dotycząca środowiska uruchomieniowego.

#### <a name="recommended-action"></a>Zalecana akcja

Przejrzyj interfejs użytkownika witryny, aby upewnić się, że nowe składniki ładowania początkowego 4 są zgodne. W razie potrzeby użyj właściwości `IdentityUIFrameworkVersion` programu MSBuild, aby przywrócić wartość Bootstrap 3. Dodaj właściwość do `<PropertyGroup>` elementu w pliku projektu:

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
