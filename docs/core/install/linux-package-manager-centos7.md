---
title: Zainstaluj .NET Core na CentOS 7 - menedżer pakietów - .NET Core
description: Użyj menedżera pakietów, aby zainstalować zestaw SDK .NET Core i program runtime w centos 7.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 66e78aadf933d3e10b99e3d2c7258733e96164f6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920853"
---
# <a name="centos-7-package-manager---install-net-core"></a>CentOS 7 Menedżer pakietów — instalowanie programu .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

W tym artykule opisano sposób instalowania programu .NET Core za pomocą menedżera pakietów w systemach CentOS 7. Jeśli instalujesz program runtime, zalecamy zainstalowanie [ASP.NET core runtime](#install-the-aspnet-core-runtime), ponieważ zawiera zarówno .NET Core, jak i ASP.NET core.

## <a name="register-microsoft-key-and-feed"></a>Rejestrowanie klucza firmy Microsoft i źródła danych

Przed zainstalowaniem programu .NET należy:

- Zarejestruj klucz firmy Microsoft.
- Zarejestruj repozytorium produktów.
- Zainstaluj wymagane zależności.

Te operacje należy wykonać tylko jeden raz na każdej maszynie.

Otwórz terminal i uruchom następujące polecenie.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>Zainstalowany zestaw .NET Core SDK

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj zestaw .NET Core SDK. W terminalu uruchom następujące polecenie.

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>Instalowanie ASP.NET core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj ASP.NET czasie wykonywania. W terminalu uruchom następujące polecenie.

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>Instalowanie programu .NET Core

Zaktualizuj produkty dostępne do instalacji, a następnie zainstaluj program .NET Core. W terminalu uruchom następujące polecenie.

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Rozwiązywanie problemów z menedżerem pakietów

Ta sekcja zawiera informacje o typowych błędach, które mogą pojawić się podczas instalowania programu .NET Core za pomocą Menedżera pakietów.

### <a name="failed-to-fetch"></a>Nie można pobrać

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
