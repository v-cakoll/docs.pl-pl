---
title: Instalowanie programu .NET Core w systemie openSUSE 15 — Menedżer pakietów — .NET Core
description: Zainstaluj zestaw .NET Core SDK i środowisko uruchomieniowe na openSUSE 15 przy użyciu Menedżera pakietów.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740669"
---
# <a name="opensuse-15-package-manager---install-net-core"></a>openSUSE 15 Package Manager — Instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano, jak za pomocą Menedżera pakietów zainstalować platformę .NET Core w systemie openSUSE 15. Jeśli instalujesz środowisko uruchomieniowe, zalecamy zainstalowanie [ASP.NET Core środowiska uruchomieniowego](#install-the-aspnet-core-runtime), ponieważ zawiera on zarówno środowisko uruchomieniowe programu .NET Core, jak i ASP.NET Core.

## <a name="register-microsoft-key-and-feed"></a>Rejestrowanie klucza firmy Microsoft i źródła danych

Przed zainstalowaniem programu .NET należy:

- Zarejestruj klucz Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz Terminal i uruchom następujące polecenia.

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a>Błąd zależności z platformą .NET Core 3,1

Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** . Użyj poniższego polecenia, aby zainstalować odpowiednie zależności przed zainstalowaniem programu .NET Core 3,1 lub ASP.NET Core 3,1.

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a>Zainstaluj zestaw .NET Core SDK

Zaktualizuj produkty dostępne do zainstalowania, a następnie Zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenie.

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** . Użyj poniższego polecenia, aby zainstalować odpowiednie zależności, a następnie Zainstaluj zestaw SDK platformy .NET Core 3,1.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a>Zainstaluj środowisko uruchomieniowe ASP.NET Core

Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe ASP.NET. W terminalu uruchom następujące polecenie.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** . Użyj poniższego polecenia, aby zainstalować poprawne zależności, a następnie zainstaluj środowisko uruchomieniowe ASP.NET Core 3,1.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a>Instalowanie środowiska uruchomieniowego platformy .NET Core

Zaktualizuj produkty dostępne do zainstalowania, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> Kanał informacyjny pakietu programu .NET Core 3,1 dla openSUSE ma problem z zależnością **krb5** . Użyj poniższego polecenia, aby zainstalować poprawne zależności, a następnie zainstaluj środowisko uruchomieniowe programu .NET Core 3,1.
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
