---
ms.openlocfilehash: db89539982c1afe0df374027d54826f3265f0fee
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84603014"
---

### <a name="install-the-sdk"></a>Instalacja zestawu SDK

Zestaw .NET Core SDK pozwala na tworzenie aplikacji przy użyciu platformy .NET Core. Aby zainstalować zestaw .NET Core SDK, uruchom następujące polecenia.

```bash
sudo zypper install dotnet-sdk-3.1
```

### <a name="install-the-runtime"></a>Instalowanie środowiska uruchomieniowego

Środowisko uruchomieniowe programu .NET Core umożliwia uruchamianie aplikacji, które zostały wykonane przy użyciu platformy .NET Core, które nie zawierały środowiska uruchomieniowego. Poniższe polecenia instalują środowisko uruchomieniowe ASP.NET Core, które jest najbardziej zgodnym środowiskiem uruchomieniowym dla platformy .NET Core. W terminalu uruchom następujące polecenia.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

Jako alternatywę dla środowiska uruchomieniowego ASP.NET Core można zainstalować środowisko uruchomieniowe programu .NET Core, które nie obejmuje ASP.NET Core Support: Zastąp `aspnetcore-runtime-2.1` w powyższym poleceniu poleceniem `dotnet-runtime-3.1` .

```bash
sudo zypper install dotnet-runtime-3.1
```
