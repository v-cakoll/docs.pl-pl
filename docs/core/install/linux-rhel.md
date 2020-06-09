---
title: Instalowanie programu .NET Core w systemie RHEL — .NET Core
description: Ilustruje różne sposoby instalowania zestaw .NET Core SDK i środowiska uruchomieniowego .NET Core w systemie RHEL.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 7ae55f881cd0c877cf1db24be7a4ee23320e21a8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603042"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a>Zainstaluj zestaw .NET Core SDK lub środowisko uruchomieniowe platformy .NET Core w systemie RHEL

Platforma .NET Core jest obsługiwana w systemie RHEL. W tym artykule opisano sposób instalowania programu .NET Core w systemie RHEL.

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Zarejestruj swoją subskrypcję Red Hat

Aby zainstalować platformę .NET Core z Red Hat na RHEL, należy najpierw zarejestrować się przy użyciu Menedżera subskrypcji Red Hat. Jeśli nie zostało to zrobione w systemie lub jeśli nie masz pewności, zapoznaj się z [dokumentacją produktu Red Hat dla platformy .NET Core](https://access.redhat.com/documentation/net_core/).

## <a name="supported-distributions"></a>Obsługiwane dystrybucje

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach RHEL 7 i RHEL 8. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu RHEL nie jest już obsługiwana.

- ✔️ wskazuje, że wersja programu RHEL lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja RHEL lub .NET Core nie jest obsługiwana w tej wersji RHEL.
- Gdy wersja RHEL i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [7](#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Następujące wersje programu .NET Core nie są już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

## <a name="how-to-install-other-versions"></a>Jak zainstalować inne wersje

Zapoznaj się z [dokumentacją firmy Red Hat dla platformy .NET Core w przypadku](https://access.redhat.com/documentation/net_core/) czynności wymaganych do zainstalowania innych wersji platformy .NET Core.

## <a name="rhel-8-"></a>RHEL 8 ✔️

Platforma .NET Core jest dołączona do repozytoriów AppStream dla RHEL 8.

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a>RHEL ✔️ 7

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

Następujące polecenie instaluje `scl-utils` pakiet:

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a>Instalacja zestawu SDK

Zestaw .NET Core SDK umożliwia tworzenie aplikacji przy użyciu platformy .NET Core. W przypadku zainstalowania zestaw .NET Core SDK nie trzeba instalować odpowiedniego środowiska uruchomieniowego. Aby zainstalować zestaw .NET Core SDK, uruchom następujące polecenia:

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

Red Hat nie zaleca trwałego włączania `rh-dotnet31` , ponieważ może to mieć wpływ na inne programy. Program zawiera na przykład `rh-dotnet31` wersję `libcurl` , która różni się od bazowej wersji RHEL. Może to prowadzić do problemów z programami, które nie oczekują innej wersji programu `libcurl` . Jeśli chcesz `rh-dotnet` trwale włączyć, Dodaj następujący wiersz do pliku _~/.bashrc._ .

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a>Instalowanie środowiska uruchomieniowego

Środowisko uruchomieniowe programu .NET Core umożliwia uruchamianie aplikacji, które zostały wykonane przy użyciu platformy .NET Core, które nie zawierały środowiska uruchomieniowego. Poniższe polecenia instalują środowisko uruchomieniowe ASP.NET Core, które jest najbardziej zgodnym środowiskiem uruchomieniowym dla platformy .NET Core. W terminalu uruchom następujące polecenia.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

Red Hat nie zaleca trwałego włączania `rh-dotnet31-aspnetcore-runtime-3.1` , ponieważ może to mieć wpływ na inne programy. Program zawiera na przykład `rh-dotnet31-aspnetcore-runtime-3.1` wersję `libcurl` , która różni się od bazowej wersji RHEL. Może to prowadzić do problemów z programami, które nie oczekują innej wersji programu `libcurl` . Jeśli chcesz `rh-dotnet31-aspnetcore-runtime-3.1` trwale włączyć, Dodaj następujący wiersz do pliku _~/.bashrc._ .

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

Jako alternatywę dla środowiska uruchomieniowego ASP.NET Core można zainstalować środowisko uruchomieniowe programu .NET Core, które nie obejmuje ASP.NET Core Support: Zastąp `rh-dotnet31-aspnetcore-runtime-3.1` w poleceniach powyżej `rh-dotnet31-dotnet-runtime-3.1` .

## <a name="snap"></a>Przystawki

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a>Zależności

[!INCLUDE [linux-install-dependencies](includes/linux-install-dependencies.md)]

## <a name="scripted-install"></a>Instalacja z skryptami

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a>Instalacja ręczna

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a>Następne kroki

- [Samouczek: Tworzenie aplikacji konsolowej z zestaw .NET Core SDK przy użyciu Visual Studio Code](../tutorials/with-visual-studio-code.md)
