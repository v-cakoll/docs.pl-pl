---
title: polecenie źródło listy dotnet nuget
description: Polecenie źródło listy nuget dotnet zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463543"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget list source

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget list source`- Wyświetla listę wszystkich skonfigurowanych źródeł NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget list source` zawiera listę wszystkich istniejących źródeł z plików konfiguracyjnych NuGet.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`--format [Detailed|Short]`**

  Format wyjścia polecenia listy: `Detailed` (domyślny) `Short`i .

## <a name="examples"></a>Przykłady

- Lista skonfigurowanych źródeł z bieżącego katalogu:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
