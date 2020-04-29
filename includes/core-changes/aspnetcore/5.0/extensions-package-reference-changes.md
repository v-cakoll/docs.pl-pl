---
ms.openlocfilehash: d7a93cb539baee6a70f75d3afe52fd7546ac2399
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507097"
---
### <a name="extensions-package-reference-changes-affecting-some-nuget-packages"></a>Rozszerzenia: zmiany odwołania do pakietów wpływające na niektóre pakiety NuGet

Po przeprowadzeniu migracji `Microsoft.Extensions.*` niektórych pakietów NuGet z repozytorium [dotnet/Extensions](https://github.com/dotnet/extensions) do programu [dotnet/Runtime](https://github.com/dotnet/runtime), zgodnie z opisem w polu [ASPNET/anonse # 411](https://github.com/aspnet/Announcements/issues/411), zmiany pakietów są stosowane do niektórych migrowanych pakietów. Aby zapoznać się z omówieniem tego problemu, zobacz [dotnet/aspnetcore # 21033](https://github.com/dotnet/aspnetcore/issues/21033).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 4

#### <a name="old-behavior"></a>Stare zachowanie

Niektóre `Microsoft.Extensions.*` pakiety zawierają odwołania do pakietów dla interfejsów API, na których opiera się Twoja aplikacja.

#### <a name="new-behavior"></a>Nowe zachowanie

Być może aplikacja będzie musiała `Microsoft.Extensions.*` dodać zależności pakietu.

#### <a name="reason-for-change"></a>Przyczyna zmiany

Zasady pakowania zostały zaktualizowane w celu lepszego dopasowania do repozytorium *dotnet/Runtime* . W ramach nowych zasad odwołania do nieużywanych pakietów są usuwane z plików *. nupkg* podczas tworzenia pakietów.

#### <a name="recommended-action"></a>Zalecana akcja

Konsumenci pakietów, których to dotyczy, powinni dodać bezpośrednią zależność do usuniętej zależności pakietu w projekcie, jeśli są używane interfejsy API z usuniętej zależności pakietu. W poniższej tabeli wymieniono odnośne pakiety i odpowiednie zmiany.

|Nazwa pakietu|Zmień opis|
|------------|------------------|
|[Microsoft. Extensions. Configuration. Binder](https://nuget.org/packages/Microsoft.Extensions.Configuration.Binder)|Usunięto odwołanie do`Microsoft.Extensions.Configuration`|
|[Microsoft. Extensions. Configuration. JSON](https://nuget.org/packages/Microsoft.Extensions.Configuration.Json)    |Usunięto odwołanie do`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. host. Abstracts](https://nuget.org/packages/Microsoft.Extensions.Hosting.Abstractions)|Usunięto odwołanie do`Microsoft.Extensions.Logging.Abstractions`|
|[Microsoft. Extensions. Logging](https://nuget.org/packages/Microsoft.Extensions.Logging)                          |Usunięto odwołanie do`Microsoft.Extensions.Configuration.Binder`|
|[Microsoft. Extensions. Logging. Console](https://nuget.org/packages/Microsoft.Extensions.Logging.Console)          |Usunięto odwołanie do`Microsoft.Extensions.Configuration.Abstractions`|
|[Microsoft. Extensions. Logging. EventLog](https://nuget.org/packages/Microsoft.Extensions.Logging.EventLog)        |Usunięto odwołanie `System.Diagnostics.EventLog` do dla monikera platformy docelowej .NET Framework 4.6.1|
|[Microsoft. Extensions. Logging. EventSource](https://nuget.org/packages/Microsoft.Extensions.Logging.EventSource)  |Usunięto odwołanie do`System.Threading.Tasks.Extensions`|
|[Microsoft. Extensions. Opcje](https://nuget.org/packages/Microsoft.Extensions.Options)                          |Usunięto odwołanie do`System.ComponentModel.Annotations`|

Na przykład odwołanie do `Microsoft.Extensions.Configuration` pakietu zostało usunięte z. `Microsoft.Extensions.Configuration.Binder` W pakiecie nie użyto interfejsu API z zależności. Użytkownicy `Microsoft.Extensions.Configuration.Binder` , którzy zależą od interfejsów `Microsoft.Extensions.Configuration` API, powinni dodać bezpośrednie odwołanie do niego w swoim projekcie.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!--

#### Affected APIs

Not detectable via API analysis

-->
