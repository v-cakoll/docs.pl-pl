---
title: polecenie dotnet nuget delete
description: Polecenie dotnet-nuget-delete usuwa lub usuwa listę pakiet z serwera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 4fa4f24adba251d7872986de4a8b1a63203c36c3
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463584"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Ten artykuł dotyczy:** ✔️.NET Core 1.x SDK i nowszych wersjach

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget delete`- Usuwa lub usuwa listę pakiet z serwera.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output]
    [--interactive] [-k|--api-key <API_KEY>] [--no-service-endpoint]
    [--non-interactive] [-s|--source <SOURCE>]

dotnet nuget delete -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget delete` usuwa lub usuwa listę pakiet z serwera. W [przypadku nuget.org](https://www.nuget.org/)akcja polega na odsuń pakiet do wykreślenia.

## <a name="arguments"></a>Argumenty

* **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu do usunięcia.

* **`PACKAGE_VERSION`**

  Wersja pakietu do usunięcia.

## <a name="options"></a>Opcje

* **`--force-english-output`**

  Wymusza uruchamianie aplikacji przy użyciu niezmiennej kultury opartej na języku angielskim.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie. Opcja dostępna od pliku .NET Core 2.2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API serwera.

* **`--no-service-endpoint`**

  Nie dołącza "api/v2/package" do źródłowego adresu URL. Opcja dostępna od pliku .NET Core 2.1 SDK.

* **`--non-interactive`**

  Nie monituje o wprowadzenie danych przez użytkownika lub potwierdzenia.

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Obsługiwane adresy URL dla nuget.org `https://www.nuget.org` `https://www.nuget.org/api/v3`obejmują `https://www.nuget.org/api/v2/package`, i . W przypadku prywatnych kanałów informacyjnych `%hostname%/api/v3`zastąp nazwę hosta (na przykład ).

## <a name="examples"></a>Przykłady

* Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu, nie monitując użytkownika o poświadczenia lub inne dane wejściowe:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
