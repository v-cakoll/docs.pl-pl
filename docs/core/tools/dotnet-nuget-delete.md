---
title: polecenie usunięcia NuGet narzędzia dotnet
description: Polecenie dotnet-NuGet-DELETE Usuwa pakiet z serwera lub go wystawia.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 70316a0baa2cf9923738a53af561b5c77014c3ff
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202571"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget delete`-Usuwa pakiet z serwera lub go wystawia.

## <a name="synopsis"></a>Streszczenie

```console
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

## <a name="description"></a>Opis

`dotnet nuget delete` Polecenie usuwa pakiet z serwera lub go wystawia. W przypadku [NuGet.org](https://www.nuget.org/)akcja ma na celu odlistowanie pakietu.

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

  Określa adres URL serwera. Obsługiwane adresy URL dla NuGet.org `https://www.nuget.org`obejmują `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`. W przypadku prywatnych kanałów informacyjnych Zastąp nazwę hosta (na `%hostname%/api/v3`przykład).

## <a name="examples"></a>Przykłady

* Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`, bez monitowania użytkownika o poświadczenia lub inne dane wejściowe:

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
