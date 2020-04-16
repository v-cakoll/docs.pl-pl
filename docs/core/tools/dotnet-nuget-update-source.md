---
title: polecenie źródła aktualizacji dotnet nuget
description: Polecenie źródła aktualizacji dotnet nuget aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463480"
---
# <a name="dotnet-nuget-update-source"></a>dotnet nuget update source

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget update source`- Aktualizacja źródła NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget update source` aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.

## <a name="arguments"></a>Argumenty

- **`NAME`**

  Nazwa źródła.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-p|--password <PASSWORD>`**

  Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.

- **`-s|--source <SOURCE>`**

  Ścieżka do źródła pakietu.

- **`--store-password-in-clear-text`**

  Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.

- **`-u|--username <USER>`**

  Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.

- **`--valid-authentication-types <TYPES>`**

  Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła. Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server. Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.

## <a name="examples"></a>Przykłady

- Aktualizowanie źródła o `mySource`nazwie :

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
