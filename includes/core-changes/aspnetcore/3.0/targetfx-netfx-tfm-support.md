---
ms.openlocfilehash: b60f74947a537c602c7bd1a89587b76bd847c82a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75937286"
---
### <a name="target-framework-net-framework-support-dropped"></a>Struktura docelowa: obsługa platformy .NET Framework porzucona

Począwszy od ASP.NET Core 3.0, .NET Framework jest nieobsługiwaną platformą docelową.

#### <a name="change-description"></a>Zmień opis

.NET Framework 4.8 jest ostatnią wersją główną programu .NET Framework. Nowe ASP.NET aplikacje Core powinny być zbudowane na .NET Core. Począwszy od wersji .NET Core 3.0, można traktować ASP.NET Core 3.0 jako część .NET Core.

Klienci korzystający z ASP.NET Core z platformą .NET Framework mogą kontynuować w pełni obsługiwany sposób przy użyciu [wersji 2.1 LTS.](https://www.microsoft.com/net/download/dotnet-core/2.1) Wsparcie i serwis owanie dla 2.1 trwa co najmniej do 21 sierpnia 2021 r. Ta data jest trzy lata po deklaracji wydania LTS na [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy). Obsługa pakietów ASP.NET Core 2.1 **w platformie .NET Framework** będzie trwać przez czas nieokreślony, podobnie jak [zasady obsługi dla innych platform ASP.NET opartych na pakiecie.](https://dotnet.microsoft.com/platform/support/policy/aspnet)

Aby uzyskać więcej informacji na temat przenoszenia z platformy .NET Framework do platformy .NET Core, zobacz [Przenoszenie do .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions`pakiety (takie jak rejestrowanie, iniekcji zależności i konfiguracji) i entity framework core nie ma wpływu. Będą nadal obsługiwać .NET Standard.

Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

ASP.NET aplikacje Core mogą działać na platformie .NET Core lub .NET Framework.

#### <a name="new-behavior"></a>Nowe zachowanie

ASP.NET aplikacje Core można uruchamiać tylko w usłudze .NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Wykonaj jedno z następujących działań:

- Utrzymuj aplikację na ASP.NET Core 2.1.
- Migrowanie aplikacji i zależności do .NET Core.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
