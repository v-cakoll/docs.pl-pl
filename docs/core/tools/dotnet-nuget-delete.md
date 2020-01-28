---
title: polecenie usunięcia NuGet narzędzia dotnet
description: Polecenie dotnet-NuGet-DELETE Usuwa pakiet z serwera lub go wystawia.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 0950f03c0986bde17ae3e2e7170d402ea8222853
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733123"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Ten artykuł ma zastosowanie do:** ✔️ .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget delete` — usuwa pakiet z serwera lub go wystawia.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Opis

Polecenie `dotnet nuget delete` usuwa pakiet z serwera lub go wystawia. W przypadku [NuGet.org](https://www.nuget.org/)akcja ma na celu odlistowanie pakietu.

## <a name="arguments"></a>Argumenty

* **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu do usunięcia.

* **`PACKAGE_VERSION`**

  Wersja pakietu do usunięcia.

## <a name="options"></a>Opcje

* **`--force-english-output`**

  Wymusza uruchomienie aplikacji przy użyciu niezmiennej, opartej na języku angielskim kultury.

* **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

* **`--interactive`**

  Umożliwia zablokowanie polecenia i wymaga ręcznej akcji dla operacji takich jak uwierzytelnianie. Opcja dostępna od wersji .NET Core 2,2 SDK.

* **`-k|--api-key <API_KEY>`**

  Klucz interfejsu API dla serwera programu.

* **`--no-service-endpoint`**

  Nie dołącza "API/v2/Package" do źródłowego adresu URL. Opcja dostępna od wersji .NET Core 2,1 SDK.

* **`--non-interactive`**

  Nie monituje o dane wejściowe lub potwierdzone przez użytkownika.

* **`-s|--source <SOURCE>`**

  Określa adres URL serwera. Obsługiwane adresy URL dla nuget.org obejmują `https://www.nuget.org`, `https://www.nuget.org/api/v3`i `https://www.nuget.org/api/v2/package`. W przypadku źródeł prywatnych Zastąp wartość Nazwa hosta (na przykład `%hostname%/api/v3`).

## <a name="examples"></a>Przykłady

* Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`, bez monitowania użytkownika o poświadczenia lub inne dane wejściowe:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
