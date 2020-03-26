---
title: polecenie źródła aktualizacji dotnet nuget
description: Polecenie źródła aktualizacji dotnet nuget aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 38335e07f91850756c7671413e1193c2578e7e7e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148548"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="5ce84-103">źródło aktualizacji dotnet nuget</span><span class="sxs-lookup"><span data-stu-id="5ce84-103">dotnet nuget update source</span></span>

<span data-ttu-id="5ce84-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="5ce84-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5ce84-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5ce84-105">Name</span></span>

<span data-ttu-id="5ce84-106">`dotnet nuget update source`- Aktualizacja źródła NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ce84-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ce84-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="5ce84-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget update source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5ce84-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5ce84-108">Description</span></span>

<span data-ttu-id="5ce84-109">Polecenie `dotnet nuget update source` aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ce84-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="5ce84-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="5ce84-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="5ce84-111">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="5ce84-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="5ce84-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="5ce84-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="5ce84-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ce84-113">The NuGet configuration file.</span></span> <span data-ttu-id="5ce84-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="5ce84-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="5ce84-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5ce84-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="5ce84-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5ce84-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password`**

  <span data-ttu-id="5ce84-117">Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="5ce84-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source`**

  <span data-ttu-id="5ce84-118">Ścieżka do źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="5ce84-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="5ce84-119">Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.</span><span class="sxs-lookup"><span data-stu-id="5ce84-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="5ce84-120">Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="5ce84-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="5ce84-121">Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła.</span><span class="sxs-lookup"><span data-stu-id="5ce84-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="5ce84-122">Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="5ce84-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="5ce84-123">Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.</span><span class="sxs-lookup"><span data-stu-id="5ce84-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="5ce84-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5ce84-124">Examples</span></span>

- <span data-ttu-id="5ce84-125">Aktualizowanie źródła o `mySource`nazwie :</span><span class="sxs-lookup"><span data-stu-id="5ce84-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="5ce84-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ce84-126">See also</span></span>

- [<span data-ttu-id="5ce84-127">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="5ce84-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="5ce84-128">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="5ce84-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
