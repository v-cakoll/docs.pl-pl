---
title: polecenie usunięcia NuGet narzędzia dotnet
description: Polecenie dotnet-NuGet-DELETE Usuwa pakiet z serwera lub go wystawia.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 79634baa9d6d7ff1f388f6a794ffd816687be105
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117639"
---
# <a name="dotnet-nuget-delete"></a>dotnet nuget delete

**Ten temat dotyczy: ✓** .NET Core 1. x SDK i nowszych wersji

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nazwa

`dotnet nuget delete`-Usuwa pakiet z serwera lub go wystawia.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
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

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* Usuwa wersję 1,0 pakietu `Microsoft.AspNetCore.Mvc`, bez monitowania użytkownika o poświadczenia lub inne dane wejściowe:

  ```dotnetcli
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```
