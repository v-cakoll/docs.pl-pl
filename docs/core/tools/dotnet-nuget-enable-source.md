---
title: dotnet nuget enable source, polecenie
description: Polecenie dotnet nuget enable source umożliwia istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463559"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget enable source

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget enable source`- Włącz źródło NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget enable source` włącza istniejące źródło w plikach konfiguracyjnych NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Nazwa źródła.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Przykłady

- Włącz źródło o `mySource`nazwie :

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
