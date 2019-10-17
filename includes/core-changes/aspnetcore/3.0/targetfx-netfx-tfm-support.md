---
ms.openlocfilehash: 4c676a185ff4a7a825acb059bf0a5842ca3922fc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394021"
---
### <a name="target-framework-net-framework-support-dropped"></a>Platforma docelowa: porzucona obsługa .NET Framework

Począwszy od ASP.NET Core 3,0, .NET Framework jest nieobsługiwaną strukturą docelową.

#### <a name="change-description"></a>Zmień opis

.NET Framework 4,8 to Ostatnia wersja główna .NET Framework. Nowe aplikacje ASP.NET Core powinny być oparte na platformie .NET Core. Począwszy od wersji programu .NET Core 3,0, można traktować ASP.NET Core 3,0 jako część platformy .NET Core.

Klienci korzystający z ASP.NET Core z .NET Framework mogą kontynuować w pełni obsługiwaną pracę przy użyciu [wersji 2,1 LTS](https://www.microsoft.com/net/download/dotnet-core/2.1). Obsługa i obsługa 2,1 są kontynuowane do dnia 21 sierpnia 2021. Ta data jest trzy lata po deklaracji wydania LTS zgodnie z [zasadami pomocy technicznej dla platformy .NET](https://www.microsoft.com/net/platform/support-policy). Obsługa pakietów ASP.NET Core 2,1 **w .NET Framework** zostanie rozbudowana w nieskończoność, podobnie jak w [przypadku innych platform ASP.NET opartych na pakietach](https://dotnet.microsoft.com/platform/support/policy/aspnet).

Aby uzyskać więcej informacji na temat przenoszenia z .NET Framework do programu .NET Core, zobacz [przenoszenie do platformy .NET Core](~/docs/core/porting/index.md).

nie ma to wpływu na pakiety `Microsoft.Extensions` (takie jak rejestrowanie, iniekcja zależności i konfiguracja Entity Framework Core). Będą oni nadal obsługiwać .NET Standard.

Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://blogs.msdn.microsoft.com/webdev/2018/10/29/a-first-look-at-changes-coming-in-asp-net-core-3-0).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="old-behavior"></a>Stare zachowanie

Aplikacje ASP.NET Core mogą działać na platformie .NET Core lub .NET Framework.

#### <a name="new-behavior"></a>Nowe zachowanie

Aplikacje ASP.NET Core można uruchamiać tylko na platformie .NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Wykonaj jedną z następujących czynności:

- Zachowaj swoją aplikację na ASP.NET Core 2,1.
- Migruj swoją aplikację i zależności do programu .NET Core.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
