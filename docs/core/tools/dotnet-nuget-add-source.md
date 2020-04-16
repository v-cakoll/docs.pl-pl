---
title: dotnet nuget dodaj polecenie źródło
description: Polecenie dotnet nuget add source dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 319501e026f1c3102006b0be5357f127b8e366a7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463602"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget add source

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget add source`- Dodaj źródło NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget add source` dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.

## <a name="arguments"></a>Argumenty

- **`PACKAGE_SOURCE_PATH`**

  Ścieżka do źródła pakietu.

## <a name="options"></a>Opcje

- **`--configfile <FILE>`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name <SOURCE_NAME>`**

  Nazwa źródła.

- **`-p|--password <PASSWORD>`**

  Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.

- **`--store-password-in-clear-text`**

  Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.

- **`-u|--username <USER>`**

  Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.

- **`--valid-authentication-types <TYPES>`**

  Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła. Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server. Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.

## <a name="examples"></a>Przykłady

- Dodaj `nuget.org` jako źródło:

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- Dodaj `c:\packages` jako źródło lokalne:

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- Dodaj źródło, które wymaga uwierzytelniania:

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- Dodaj źródło, które wymaga uwierzytelniania (a następnie przejdź do dostawcy poświadczeń instalacji):

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a>Zobacz też

- [Sekcje źródła pakietów w plikach NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [sources, polecenie (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
