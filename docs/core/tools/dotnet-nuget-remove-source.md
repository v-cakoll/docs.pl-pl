---
title: dotnet nuget usunąć polecenie źródła
description: Polecenie dotnet nuget remove source usuwa istniejące źródło z plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b259873e1885644b272136fa31414410bdfd9f27
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463492"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remove source

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget remove source`- Usuń źródło NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget remove source` usuwa istniejące źródło z plików konfiguracyjnych NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Nazwa źródła.

## <a name="options"></a>Opcje

- **`--configfile`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Przykłady

- Usuwanie źródła o `mySource`nazwie :

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
