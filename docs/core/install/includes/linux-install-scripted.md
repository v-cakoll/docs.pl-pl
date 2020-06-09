---
ms.openlocfilehash: 0d29407896145bc3b2ed8284c839ae8f2f0521b2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602951"
---

[Skrypty programu dotnet-Install](../../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i instalacji nienależących do administratora **zestawu SDK**. Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh> .

Skrypt domyślnie instaluje najnowszą [LTS](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) wersję, która jest platformą .net Core 3,1. Aby zainstalować bieżącą wersję, która nie może być wersją (LTS), użyj `-c Current` parametru.

```bash
./dotnet-install.sh -c Current
```

Aby zainstalować środowisko uruchomieniowe platformy .NET Core zamiast zestawu SDK, użyj `--runtime` parametru.

```bash
./dotnet-install.sh -c Current --runtime
```

Określoną wersję można zainstalować, zmieniając `-c` parametr w celu wskazania określonej wersji. Następujące polecenie instaluje zestaw .NET Core SDK 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Aby uzyskać więcej informacji, zobacz temat informacje o [skryptach dotnet-Install](../../tools/dotnet-install-script.md).
