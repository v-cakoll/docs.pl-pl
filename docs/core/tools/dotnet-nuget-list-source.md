---
title: polecenie źródło listy dotnet nuget
description: Polecenie źródło listy nuget dotnet zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148576"
---
# <a name="dotnet-nuget-list-source"></a>źródło listy dotnet nuget

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget list source`- Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget list source` zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.

## <a name="options"></a>Opcje

- **`--configfile`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`--format`**

  Format wyjścia polecenia listy: `Detailed` (domyślny) `Short`i .

## <a name="examples"></a>Przykłady

- Lista skonfigurowanych źródeł z bieżącego katalogu:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
