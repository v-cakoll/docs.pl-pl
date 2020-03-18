---
title: polecenie dotnet nuget delete
description: Polecenie dotnet-nuget-delete usuwa lub usuwa pakiet z serwera.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76733123"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Ten artykuł dotyczy:** ✔️ .NET Core 1.x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget delete`- Usuwa lub usuwa pakiet z serwera.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget delete` usuwa lub usuwa listę pakietu z serwera. W [przypadku nuget.org](https://www.nuget.org/)akcja polega na wykreślania pakietu z listy.

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

  Umożliwia blokowanie polecenia i wymaga ręcznego działania dla operacji, takich jak uwierzytelnianie. Opcja dostępna od sdk .NET Core 2.2.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera.

* **`--no-service-endpoint`**

  Nie dołącza "api/v2/package" do źródłowego adresu URL. Opcja dostępna od sdk .NET Core 2.1.

* **`--non-interactive`**

  Nie monituje o wprowadzenie danych przez użytkownika ani potwierdzenia.

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Obsługiwane adresy URL dla `https://www.nuget.org` `https://www.nuget.org/api/v3`nuget.org `https://www.nuget.org/api/v2/package`obejmują , i . W przypadku prywatnych źródeł danych należy zastąpić `%hostname%/api/v3`nazwę hosta (na przykład).

## <a name="examples"></a>Przykłady

* Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Usuwa wersję 1.0 `Microsoft.AspNetCore.Mvc`pakietu, nie monitując użytkownika o poświadczenia lub inne dane wejściowe:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
