---
title: polecenie Usuń nuget DotNet
description: Polecenia dotnet-nuget-delete Usuwa lub unlists pakietu z serwera.
author: karann-msft
ms.date: 12/04/2018
ms.openlocfilehash: a657fa273ca6b5229a1713fbcaf003217a59fd7f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648681"
---
# <a name="dotnet-nuget-delete"></a><span data-ttu-id="03624-103">Usuń nuget DotNet</span><span class="sxs-lookup"><span data-stu-id="03624-103">dotnet nuget delete</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="03624-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="03624-104">Name</span></span>

<span data-ttu-id="03624-105">`dotnet nuget delete` -Usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-105">`dotnet nuget delete` - Deletes or unlists a package from the server.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03624-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="03624-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="03624-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="03624-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [--interactive] [-k|--api-key] [--no-service-endpoint]
    [--non-interactive] [-s|--source]
dotnet nuget delete [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="03624-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="03624-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet nuget delete [<PACKAGE_NAME> <PACKAGE_VERSION>] [--force-english-output] [-k|--api-key] [--non-interactive]
    [-s|--source]
dotnet nuget delete [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="03624-109">Opis</span><span class="sxs-lookup"><span data-stu-id="03624-109">Description</span></span>

<span data-ttu-id="03624-110">`dotnet nuget delete` Polecenie usuwa lub unlists pakietu z serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-110">The `dotnet nuget delete` command deletes or unlists a package from the server.</span></span> <span data-ttu-id="03624-111">Aby uzyskać [nuget.org](https://www.nuget.org/), akcja jest wyrejestrowanie pakietu.</span><span class="sxs-lookup"><span data-stu-id="03624-111">For [nuget.org](https://www.nuget.org/), the action is to unlist the package.</span></span>

## <a name="arguments"></a><span data-ttu-id="03624-112">Argumenty</span><span class="sxs-lookup"><span data-stu-id="03624-112">Arguments</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="03624-113">Nazwa/identyfikator pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="03624-113">Name/ID of the package to delete.</span></span>

* **`PACKAGE_VERSION`**

  <span data-ttu-id="03624-114">Wersja pakietu do usunięcia.</span><span class="sxs-lookup"><span data-stu-id="03624-114">Version of the package to delete.</span></span>

## <a name="options"></a><span data-ttu-id="03624-115">Opcje</span><span class="sxs-lookup"><span data-stu-id="03624-115">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="03624-116">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="03624-116">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`--force-english-output`**

  <span data-ttu-id="03624-117">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="03624-117">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="03624-118">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="03624-118">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="03624-119">Umożliwia polecenie, aby zablokować i wymaga ręcznej akcji dla operacji, takich jak uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="03624-119">Allows the command to block and requires manual action for operations like authentication.</span></span> <span data-ttu-id="03624-120">Opcja dostępna od zestawu SDK programu .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="03624-120">Option available since .NET Core 2.2 SDK.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="03624-121">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-121">The API key for the server.</span></span>

* **`--no-service-endpoint`**

  <span data-ttu-id="03624-122">Nie dołącza "interfejsu api w wersji 2/pakiet" adres URL źródła.</span><span class="sxs-lookup"><span data-stu-id="03624-122">Doesn't append "api/v2/package" to the source URL.</span></span> <span data-ttu-id="03624-123">Opcja dostępna od zestawu SDK programu .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="03624-123">Option available since .NET Core 2.1 SDK.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="03624-124">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="03624-124">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="03624-125">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-125">Specifies the server URL.</span></span> <span data-ttu-id="03624-126">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="03624-126">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="03624-127">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="03624-127">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="03624-128">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="03624-128">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`--force-english-output`**

  <span data-ttu-id="03624-129">Wymusza na aplikacji do uruchamiania przy użyciu kultury niezmiennej, oparte na język angielski.</span><span class="sxs-lookup"><span data-stu-id="03624-129">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="03624-130">Drukuje krótki pomoc dotyczącą polecenia.</span><span class="sxs-lookup"><span data-stu-id="03624-130">Prints out a short help for the command.</span></span>

* **`-k|--api-key <API_KEY>`**

  <span data-ttu-id="03624-131">Klucz interfejsu API dla serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-131">The API key for the server.</span></span>

* **`--non-interactive`**

  <span data-ttu-id="03624-132">Nie monit o podanie danych wejściowych użytkownika lub potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="03624-132">Doesn't prompt for user input or confirmations.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="03624-133">Określa adres URL serwera.</span><span class="sxs-lookup"><span data-stu-id="03624-133">Specifies the server URL.</span></span> <span data-ttu-id="03624-134">Obsługiwane adresów URL dla dołączania nuget.org `https://www.nuget.org`, `https://www.nuget.org/api/v3`, i `https://www.nuget.org/api/v2/package`.</span><span class="sxs-lookup"><span data-stu-id="03624-134">Supported URLs for nuget.org include `https://www.nuget.org`, `https://www.nuget.org/api/v3`, and `https://www.nuget.org/api/v2/package`.</span></span> <span data-ttu-id="03624-135">Dla prywatnych źródeł danych, zastąp nazwę hosta (na przykład `%hostname%/api/v3`).</span><span class="sxs-lookup"><span data-stu-id="03624-135">For private feeds, replace the host name (for example, `%hostname%/api/v3`).</span></span>

---

## <a name="examples"></a><span data-ttu-id="03624-136">Przykłady</span><span class="sxs-lookup"><span data-stu-id="03624-136">Examples</span></span>

* <span data-ttu-id="03624-137">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`:</span><span class="sxs-lookup"><span data-stu-id="03624-137">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0
  ```

* <span data-ttu-id="03624-138">Usuwa pakiet w wersji 1.0 dla `Microsoft.AspNetCore.Mvc`, nie monitowania użytkownika o poświadczenia lub inne dane wejściowe:</span><span class="sxs-lookup"><span data-stu-id="03624-138">Deletes version 1.0 of package `Microsoft.AspNetCore.Mvc`, not prompting user for credentials or other input:</span></span>

  ```console
  dotnet nuget delete Microsoft.AspNetCore.Mvc 1.0 --non-interactive
  ```