---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041662"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>Tożsamość: interfejs użytkownika używa funkcji statyczne zasoby sieci Web

W ASP.NET Core 3,0 wprowadzono statyczną funkcję zasobów sieci Web i została ona przyjęta przez interfejs użytkownika tożsamości.

#### <a name="change-description"></a>Zmień opis

W związku z tym interfejs użytkownika tożsamości przyjmuje funkcję statyczne elementy zawartości sieci Web:

- Wybór struktury jest realizowany przy użyciu właściwości `IdentityUIFrameworkVersion` w pliku projektu.
- Bootstrap 4 jest domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości. Program ładowania początkowego 3 osiągnął koniec okresu istnienia i należy rozważyć migrację do obsługiwanej wersji.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości był **Bootstrap 3**. Strukturę interfejsu użytkownika można skonfigurować przy użyciu parametru do wywołania metody `AddDefaultUI` w `Startup.ConfigureServices`.

#### <a name="new-behavior"></a>Nowe zachowanie

Domyślną strukturą interfejsu użytkownika dla interfejsu użytkownika tożsamości jest **Bootstrap 4**. Struktura interfejsu użytkownika musi być skonfigurowana w pliku projektu, a nie w wywołaniu metody `AddDefaultUI`.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zastosowanie statycznej funkcji zasobów sieci Web wymaga, aby konfiguracja struktury interfejsu użytkownika była przenoszona do programu MSBuild. Podjęcie decyzji dotyczącej struktury osadzania to decyzja w czasie kompilacji, a nie decyzja dotycząca środowiska uruchomieniowego.

#### <a name="recommended-action"></a>Zalecana akcja

Przejrzyj interfejs użytkownika witryny, aby upewnić się, że nowe składniki ładowania początkowego 4 są zgodne. W razie potrzeby użyj właściwości programu MSBuild `IdentityUIFrameworkVersion`, aby powrócić do programu Bootstrap 3. Dodaj właściwość do elementu `<PropertyGroup>` w pliku projektu:

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
