---
ms.openlocfilehash: fb78e1439a680a8dbb9fc0eb8afdeee3efef7ead
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768403"
---

[Skrypty dotnet-Install](../../tools/dotnet-install-script.md) są używane na potrzeby automatyzacji i nieadministracyjnych instalacji **zestawu SDK** i **środowiska uruchomieniowego**. Skrypt można pobrać z programu <https://dot.net/v1/dotnet-install.sh> .

Skrypt domyślnie instaluje najnowszą wersję programu [obsługi długoterminowej (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) zestawu SDK, która jest .net Core 3,1. Aby zainstalować bieżącą wersję, która nie może być wersją (LTS), użyj `-c Current` parametru.

```bash
./dotnet-install.sh -c Current
```

Aby zainstalować środowisko uruchomieniowe platformy .NET Core zamiast zestawu SDK, użyj `--runtime` parametru.

```bash
./dotnet-install.sh -c Current --runtime aspnetcore
```

Określoną wersję można zainstalować, zmieniając `-c` parametr w celu wskazania określonej wersji. Następujące polecenie instaluje zestaw .NET Core SDK 3,1.

```bash
./dotnet-install.sh -c 3.1
```

Aby uzyskać więcej informacji, zobacz temat informacje o [skryptach dotnet-Install](../../tools/dotnet-install-script.md).
