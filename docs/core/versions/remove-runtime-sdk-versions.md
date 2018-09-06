---
title: Jak usunąć środowisko uruchomieniowe platformy .NET i zestawu SDK
description: Instrukcje dotyczące usuwania składników środowiska uruchomieniowego programu .NET Core i zestawu SDK w Windows, Mac i Linux
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43787184"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Jak usunąć środowisko uruchomieniowe programu .NET Core i zestawu SDK

Wraz z upływem czasu jak zainstalować zaktualizowane wersje środowiska uruchomieniowego .NET Core i zestawu SDK, warto Usuń nieaktualne wersje programu .NET Core z poziomu Twojej maszyny. Trwa usuwanie starszych wersji środowiska uruchomieniowego mogą ulec zmianie środowiska uruchomieniowego, wybierany do uruchamiania aplikacji udostępnionej platformy, zgodnie z opisem w artykule na [wybór wersji platformy .NET Core](selection.md).

Począwszy od platformy .NET Core 2.1 interfejsu wiersza polecenia platformy .NET zawiera opcje, których można użyć, aby wyświetlić listę wersji zestawu SDK i środowiska uruchomieniowego, które są zainstalowane na komputerze.  Użyj [ `dotnet --list-sdks` ](../tools/dotnet.md#options) Aby wyświetlić listę zestawów SDK zainstalowany na tym komputerze. Użyj [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) Aby wyświetlić listę środowiska uruchomieniowe zainstalowane na tym komputerze. Następujący tekst przedstawiono typowe dane wyjściowe, Windows, macOS i Linux:

# <a name="windowstabwindows"></a>[Windows](#tab/Windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[Linux](#tab/Linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[macOS](#tab/macOS)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

***

## <a name="uninstalling-net-core"></a>Odinstalowywanie platformy .NET Core

# <a name="windowstabwindows"></a>[Windows](#tab/Windows)

Windows korzysta z platformy .NET core **Dodaj/Usuń programy** okno dialogowe, aby usunąć wersje środowiska uruchomieniowego .NET Core i zestawu SDK. Poniższy rysunek przedstawia **Dodaj/Usuń programy** okna dialogowego z różnymi wersjami środowiska uruchomieniowego .NET i zainstalowany zestaw SDK.

![Dodaj / Usuń programy, aby usunąć .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Wybierz wszystkie wersje, które chcesz usunąć z komputera, a następnie kliknij przycisk **Odinstaluj**.

# <a name="linuxtablinux"></a>[Linux](#tab/Linux)

Istnieje więcej opcji, aby odinstalować platformy .NET Core (zestaw SDK lub środowisko uruchomieniowe) w systemie Linux. Najlepszym sposobem odinstalować platformy .NET Core jest duplikatów akcję, która umożliwia instalowanie programu .NET Core. Szczegółowe informacje na temat, zależy od wybranej dystrybucji i metody instalacji.

> [!IMPORTANT]
> W przypadku instalacji Red Hat, zapoznaj się z [Red Hat — wprowadzenie](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) instrukcje dotyczące instalowania i odinstalowywania platformy .NET Core.

Począwszy od platformy .NET Core 2.1 nie ma potrzeby odinstalowania zestawu .NET Core SDK, podczas uaktualniania go przy użyciu Menedżera pakietów. Menedżer pakietów `update` lub `refresh` polecenia spowoduje automatyczne usunięcie starszej wersji po pomyślnej instalacji w nowszej wersji.

Po zainstalowaniu platformy .NET Core przy użyciu Menedżera pakietów, użyjesz tej samej Menedżera pakietów odinstalować zestaw SDK platformy .NET lub środowisko uruchomieniowe. Instalacje .NET core obsługuje najbardziej popularne Menedżery pakietów. Zapoznaj się z dokumentacją dla Twojej dystrybucji Menedżer pakietów dla dokładne składni w swoim środowisku:

- [apt-GET(8)](https://linux.die.net/man/8/apt-get) jest używany przez Debian systemów, w tym Ubuntu.
- [YUM(8)](https://linux.die.net/man/8/yum) jest używana na Fedora i CentOS, Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) jest używana w systemach openSUSE i SUSE Linux Enterprise systemu (SLES).
- [dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) na Fedora ma być używana.

W większości przypadków, to polecenie, aby usunąć pakiet `remove`.

Nazwa pakietu dla większości menedżerów pakietów instalacji zestawu .NET Core SDK jest `dotnet-sdk`, a następnie za pomocą numeru wersji. Począwszy od wersji 2.1.300 zestawu .NET Core SDK, a wersja `2.1` środowiska uruchomieniowego, wymagane są tylko numery wersji głównych i pomocniczych: na przykład, .NET Core SDK w wersji 2.1.300 mogą być przywoływane w taki sposób, jak pakiet `dotnet-sdk-2.1`. Wcześniejsze wersje wymagają całą wersję ciągu: na przykład `dotnet-sdk-2.1.200` jest wymagana dla wersji 2.1.200 .NET Core SDK.

Dla maszyn, na których zainstalowano tylko środowiska uruchomieniowego, a nie zestaw SDK, pakiet nazywa `dotnet-runtime-<version>` dla środowiska uruchomieniowego .NET Core, i `aspnetcore-runtime-<version>` dla stosu całego środowiska uruchomieniowego.

Instalacje .NET core 2.0 — przed odinstalowaniem aplikacji hosta odinstalowanie zestawu SDK przy użyciu Menedżera pakietów. Za pomocą `apt-get`, polecenie to:

```bash
apt-get remove dotnet-host
```

Należy zauważyć, że wersja nie jest dołączony do `dotnet-host`.

Jeśli został zainstalowany przy użyciu pliku tar, należy usunąć .NET Core przy użyciu metody ręcznej.

Możesz usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, przez usunięcie katalogu, który zawiera tę wersję. Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.

# <a name="macostabmacos"></a>[macOS](#tab/macOS)

Na komputerze Mac należy usunąć zestawy SDK i środowiska uruchomieniowe oddzielnie, usuwając katalogu, który zawiera tę wersję. Na przykład, aby usunąć 1.0.1 SDK i środowisko uruchomieniowe, należy użyć następujących poleceń powłoki bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Katalogi nadrzędne dla zestawu SDK i środowiska uruchomieniowego są wymienione w danych wyjściowych `dotnet --list-sdks` i `dotnet --list-runtimes` polecenia, jak pokazano w tabeli wcześniej.

Począwszy od platformy .NET Core 2.1 nie ma potrzeby odinstalowania zestawu .NET Core SDK, podczas uaktualniania go przy użyciu Menedżera pakietów. Menedżer pakietów `update` lub `refresh` polecenia spowoduje automatyczne usunięcie starszej wersji po pomyślnej instalacji w nowszej wersji.

---
