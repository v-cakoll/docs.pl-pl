---
title: Instalowanie programu .NET Core w systemie SLES — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie SLES.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 8f64efcc8206b47855871104e5b6914570c06da0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619419"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-sles"></a>Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie SLES

Platforma .NET Core jest obsługiwana w systemie SLES. W tym artykule opisano sposób instalowania programu .NET Core w systemie SLES.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="supported-distributions"></a>Obsługiwane dystrybucje

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach SLES 12 SP2 i SLES 15. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu SLES nie jest już obsługiwana.

- ✔️ wskazuje, że wersja programu SLES lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja SLES lub .NET Core nie jest obsługiwana w tej wersji SLES.
- Gdy wersja SLES i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| SLES                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [12 z dodatkiem SP2](#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Następujące wersje programu .NET Core nie są już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="sles-15-"></a>SLES 15 ✔️

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

Obecnie pakiet instalacyjny usługi Microsoft Repository SLES 15 zainstaluje plik *Microsoft-prod.* Repository w niewłaściwym katalogu, uniemożliwiając użyciu narzędzia zypper znalezienie pakietów .NET Core. Aby rozwiązać ten problem, Utwórz link symboliczny w poprawnym katalogu.

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="sles-12-"></a>SLES 12 ✔️

Program .NET Core wymaga programu SP2 jako minimum dla rodziny SLES 12.

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

[!INCLUDE [linux-zyp-install-31](includes/linux-install-31-zyp.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje o typowych błędach, które mogą wystąpić podczas korzystania z Menedżera pakietów w celu zainstalowania platformy .NET Core.

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]

## <a name="dependencies"></a>Zależności

Po zainstalowaniu programu przy użyciu Menedżera pakietów te biblioteki są instalowane dla Ciebie. Jeśli jednak ręcznie zainstalujesz platformę .NET Core lub opublikujesz aplikację, musisz upewnić się, że te biblioteki są zainstalowane:

- krb5
- libicu
- libopenssl1_1

Jeśli docelowa wersja OpenSSL środowiska uruchomieniowego to 1,1 lub nowsza, należy zainstalować polecenie **COMPAT-openssl10**.

Aby uzyskać więcej informacji o zależnościach, zobacz [samodzielne aplikacje systemu Linux](https://github.com/dotnet/core/blob/master/Documentation/self-contained-linux-apps.md).

W przypadku aplikacji .NET Core, które używają zestawu *System. Drawing. Common* , konieczne będzie również użycie następujących zależności:

- [libgdiplus (wersja 6.0.1 lub nowsza)](https://www.mono-project.com/docs/gui/libgdiplus/)

  > [!WARNING]
  > Aby zainstalować najnowszą wersję programu *libgdiplus* , można dodać do systemu repozytorium mono. Aby uzyskać więcej informacji, zobacz <https://www.mono-project.com/download/stable/>.

## <a name="scripted-install"></a>Instalacja z skryptami

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalacja ręczna

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Następne kroki

- [Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md)
