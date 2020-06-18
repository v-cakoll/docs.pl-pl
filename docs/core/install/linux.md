---
title: Instalowanie dystrybucji .NET Core i Linux
description: Dowiedz się więcej o tym, jakie dystrybucje systemu Linux obsługują instalowanie programu .NET Core w systemie Linux.
author: thraka
ms.author: adegeo
ms.date: 06/01/2020
ms.openlocfilehash: e668ad733481c2d9b73994b6344b38768f5851fe
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903379"
---
# <a name="install-net-core-on-linux"></a>Instalowanie programu .NET Core w systemie Linux

Program .NET Core jest dostępny dla różnych dystrybucji systemu Linux. Większość platform i dystrybucji systemu Linux jest w każdym roku ważna wersja i większość udostępnia Menedżer pakietów, który jest używany do instalowania platformy .NET Core. W tym artykule opisano, co jest obecnie obsługiwane i który jest używany przez Menedżera pakietów.

Pozostała część tego artykułu stanowi podział każdej głównej dystrybucji systemu Linux obsługiwanej przez platformę .NET Core. Wszystkie wersje programu .NET Core pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub dystrybucja systemu Linux osiągnie koniec cyklu życia.

Aby uzyskać najlepszą zgodność, wybierz wersję długoterminową (LTS).

## <a name="unsupported-releases"></a>Nieobsługiwane wersje

Następujące wersje programu .NET Core nie są ❌ już obsługiwane. Pliki do pobrania dla tych nadal są publikowane:

- 3.0
- 2.2
- 2.0

Te nieobsługiwane wersje nie są szczegółowo opisane w poniższych sekcjach, a przebieg może się różnić w przypadku próby ich zainstalowania.

## <a name="alpine"></a>Alp

Brak instalatorów dla Alpine. Musisz użyć [skryptu instalacji](linux-alpine.md#scripted-install) lub instrukcji [instalacji ręcznej](linux-alpine.md#manual-install) .

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core i wersje Alpine, w których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Alp osiągnie koniec cyklu życia](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).

- ✔️ wskazuje, że wersja Alpine lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Alpine lub .NET Core nie jest obsługiwana w tej wersji Alpine.
- Gdy wersja Alpine i wersja platformy .NET Core ma ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Alp                      | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) |
|-----------------------------|---------------|---------------|----------------|
| ✔️ [3,12](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [3,11](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [3,10](linux-alpine.md)  | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [3,9](linux-alpine.md)   | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌[3,8](linux-alpine.md)   | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w witrynie Alpine](linux-alpine.md).

## <a name="centos"></a>CentOS

CentOS 7 używa yum jako Menedżera pakietów i CentOS 8 używa DNF.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach CentOS 7 i CentOS 8. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu CentOS nie jest już obsługiwana.

| CentOS                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-centos.md#centos-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [7](linux-centos.md#centos-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie CentOS](linux-centos.md).

## <a name="debian"></a>Debian

Debian używa narzędzia APT (zaawansowanego pakietu) jako Menedżera pakietów.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core oraz wersji Debian, na których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Debian osiągnie koniec cyklu życia](https://wiki.debian.org/DebianReleases).

- ✔️ wskazuje, że wersja programu debian lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Debian lub .NET Core nie jest obsługiwana w tej wersji Debian.
- Gdy wersja Debian i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Debian                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [10](linux-debian.md#debian-10-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [9](linux-debian.md#debian-9-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌ [8](linux-debian.md#debian-8-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie Debian](linux-debian.md).

## <a name="fedora"></a>Fedora

Fedora używa DNF jako Menedżera pakietów.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core oraz wersji Fedora, na których są obsługiwane. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec okresu obsłudze](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja [Fedora osiągnie koniec cyklu życia](https://fedoraproject.org/wiki/End_of_life).

- ✔️ wskazuje, że wersja programu Fedora lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Fedora lub .NET Core nie jest obsługiwana w tej wersji Fedora.
- Gdy wersja Fedora i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Fedora                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [32](linux-fedora.md#fedora-32-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [31](linux-fedora.md#fedora-31-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌ [30](linux-fedora.md#fedora-30-) | ✔️ 2,1        | ✔️ 3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[29](linux-fedora.md#fedora-29-) | ✔️ 2,1        | ✔️ 3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[28](linux-fedora.md#fedora-28-) | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[27](linux-fedora.md#fedora-27-) | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie Fedora](linux-fedora.md).

## <a name="opensuse"></a>openSUSE

openSUSE używa użyciu narzędzia zypper jako Menedżera pakietów.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemie openSUSE 15. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu openSUSE nie jest już obsługiwana.

- ✔️ wskazuje, że wersja programu openSUSE lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja openSUSE lub .NET Core nie jest obsługiwana w tej wersji openSUSE.
- Gdy wersja openSUSE i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| openSUSE                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|----------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-opensuse.md#opensuse-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie openSUSE](linux-opensuse.md).

## <a name="red-hat"></a>Red Hat

Red Hat Enterprise Linux (RHEL) używa yum (RHEL 7) i DNF (RHEL 8) jako Menedżera pakietów.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach RHEL 7 i RHEL 8. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu RHEL nie jest już obsługiwana.

- ✔️ wskazuje, że wersja programu RHEL lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja RHEL lub .NET Core nie jest obsługiwana w tej wersji RHEL.
- Gdy wersja RHEL i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| RHEL                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [8](linux-rhel.md#rhel-8-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [7](linux-rhel.md#rhel-7-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie RHEL](linux-rhel.md).

## <a name="sles"></a>SLES

SLES używa użyciu narzędzia zypper jako Menedżera pakietów.

Poniższa tabela zawiera listę obecnie obsługiwanych wersji programu .NET Core w systemach SLES 12 SP2 i SLES 15. Te wersje pozostają obsługiwane, dopóki wersja [platformy .NET Core osiągnie koniec obsługi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) lub wersja programu SLES nie jest już obsługiwana.

- ✔️ wskazuje, że wersja programu SLES lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja SLES lub .NET Core nie jest obsługiwana w tej wersji SLES.
- Gdy wersja SLES i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| SLES                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|------------------------|---------------|---------------|----------------|
| ✔️ [15](linux-sles.md#sles-15-)     | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [12 z dodatkiem SP2](linux-sles.md#sles-12-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie SLES](linux-sles.md).

## <a name="ubuntu"></a>Ubuntu

Ubuntu używa narzędzia APT (zaawansowanego pakietu) jako Menedżera pakietów.

Poniższa tabela przedstawia stan pomocy technicznej Ubuntu i .NET Core.

- ✔️ wskazuje, że wersja programu Ubuntu lub .NET Core jest nadal obsługiwana.
- ❌Wskazuje, że wersja Ubuntu lub .NET Core nie jest obsługiwana w tej wersji Ubuntu.
- Gdy wersja Ubuntu i wersja platformy .NET Core mają ✔️, obsługiwane są kombinacje systemów operacyjnych i .NET.

| Ubuntu                   | .NET Core 2.1 | .NET Core 3,1 | .NET 5 (wersja zapoznawcza) (tylko instalacja ręczna) |
|--------------------------|---------------|---------------|----------------|
| ✔️ [20,04 (LTS)](linux-ubuntu.md#2004-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ✔️ [19,10](linux-ubuntu.md#1910-)       | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌[19,04](linux-ubuntu.md#1904-)       | ✔️ 2,1        | ✔️ 3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[18,10](linux-ubuntu.md#1810-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ✔️ [18,04 (LTS)](linux-ubuntu.md#1804-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |
| ❌[17,10](linux-ubuntu.md#1710-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[17,04](linux-ubuntu.md#1704-)       | ✔️ 2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ❌[16,10](linux-ubuntu.md#1610-)       | ❌2,1        | ❌3,1        | ❌wersja zapoznawcza 5,0 |
| ✔️ [16,04 (LTS)](linux-ubuntu.md#1604-) | ✔️ 2,1        | ✔️ 3,1        | ✔️ 5,0 — wersja zapoznawcza |

Aby uzyskać więcej informacji, zobacz [Instalowanie programu .NET Core w systemie Ubuntu](linux-ubuntu.md).
