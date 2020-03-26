---
title: dotnet nuget dodaj polecenie źródło
description: Polecenie dotnet nuget add source dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: c1e398699c7482a69b750cde718e6f9178b5c4bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148569"
---
# <a name="dotnet-nuget-add-source"></a>dotnet nuget dodać źródło

**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet nuget add source`- Dodaj źródło NuGet.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget add source` dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.

## <a name="arguments"></a>Argumenty

- **`PACKAGE_SOURCE_PATH`**

  Ścieżka do źródła pakietu.

## <a name="options"></a>Opcje

- **`--configfile`**

  Plik konfiguracyjny NuGet. Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku. Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu. Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`-n|--name`**

  Nazwa źródła.

- **`-p|--password`**

  Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.

- **`--store-password-in-clear-text`**

  Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.

- **`-u|--username`**

  Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.

- **`--valid-authentication-types`**

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
