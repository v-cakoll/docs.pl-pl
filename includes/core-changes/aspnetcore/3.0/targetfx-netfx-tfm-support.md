---
ms.openlocfilehash: ec6724ab378dd614c55a024ede18d997d27be3a3
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2020
ms.locfileid: "79549586"
---
### <a name="target-framework-net-framework-support-dropped"></a>Struktura docelowa: porzucona obsługa .NET Framework

Począwszy od ASP.NET Core 3.0, .NET Framework jest nieobsługiconą platformą docelową.

#### <a name="change-description"></a>Zmień opis

.NET Framework 4.8 jest ostatnią główną wersją programu .NET Framework. Nowe aplikacje ASP.NET Core powinny być oparte na programie .NET Core. Począwszy od wersji .NET Core 3.0, możesz myśleć o ASP.NET Core 3.0 jako o części .NET Core.

Klienci korzystający z ASP.NET Core z programem .NET Framework mogą kontynuować w pełni obsługiwany sposób, korzystając z [wersji 2.1 LTS.](https://dotnet.microsoft.com/download/dotnet-core/2.1) Obsługa i obsługa 2.1 trwa co najmniej do 21 sierpnia 2021 r. Ta data jest trzy lata po deklaracji wydania LTS na [.NET Support Policy](https://dotnet.microsoft.com/platform/support-policy). Obsługa pakietów core 2.1 ASP.NET **w programie .NET Framework** będzie rozszerzana na czas nieokreślony, podobnie jak zasady obsługi innych platform ASP.NET [opartych na pakiecie.](https://dotnet.microsoft.com/platform/support/policy/aspnet)

Aby uzyskać więcej informacji na temat przenoszenia z programu .NET Framework na program .NET Core, zobacz [Przenoszenie do platformy .NET Core](~/docs/core/porting/index.md).

`Microsoft.Extensions`pakiety (takie jak rejestrowanie, iniekcji zależności i konfiguracji) i Entity Framework Core nie ma wpływu. Będą nadal obsługiwać standard .NET.

Aby uzyskać więcej informacji na temat motywacji tej zmiany, zobacz [oryginalny wpis w blogu](https://devblogs.microsoft.com/aspnet/a-first-look-at-changes-coming-in-asp-net-core-3-0/).

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="old-behavior"></a>Stare zachowanie

ASP.NET aplikacje Core mogą być uruchamiane w programie .NET Core lub .NET Framework.

#### <a name="new-behavior"></a>Nowe zachowanie

ASP.NET aplikacje Core można uruchamiać tylko w programie .NET Core.

#### <a name="recommended-action"></a>Zalecana akcja

Wykonaj jedno z następujących działań:

- Utrzymuj aplikację na ASP.NET Core 2.1.
- Migrowanie aplikacji i zależności do platformy .NET Core.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
