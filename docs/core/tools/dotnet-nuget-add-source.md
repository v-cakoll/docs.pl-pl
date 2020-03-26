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
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="d013c-103">dotnet nuget dodać źródło</span><span class="sxs-lookup"><span data-stu-id="d013c-103">dotnet nuget add source</span></span>

<span data-ttu-id="d013c-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="d013c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d013c-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d013c-105">Name</span></span>

<span data-ttu-id="d013c-106">`dotnet nuget add source`- Dodaj źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="d013c-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d013c-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="d013c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name] [--username]
    [--password] [--store-password-in-clear-text] [--valid-authentication-types]
    [--configfile]
dotnet nuget add source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="d013c-108">Opis</span><span class="sxs-lookup"><span data-stu-id="d013c-108">Description</span></span>

<span data-ttu-id="d013c-109">Polecenie `dotnet nuget add source` dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="d013c-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="d013c-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d013c-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="d013c-111">Ścieżka do źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="d013c-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="d013c-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="d013c-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="d013c-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="d013c-113">The NuGet configuration file.</span></span> <span data-ttu-id="d013c-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="d013c-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="d013c-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d013c-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="d013c-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="d013c-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name`**

  <span data-ttu-id="d013c-117">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="d013c-117">Name of the source.</span></span>

- **`-p|--password`**

  <span data-ttu-id="d013c-118">Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="d013c-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="d013c-119">Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.</span><span class="sxs-lookup"><span data-stu-id="d013c-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username`**

  <span data-ttu-id="d013c-120">Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="d013c-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types`**

  <span data-ttu-id="d013c-121">Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła.</span><span class="sxs-lookup"><span data-stu-id="d013c-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="d013c-122">Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="d013c-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="d013c-123">Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.</span><span class="sxs-lookup"><span data-stu-id="d013c-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="d013c-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="d013c-124">Examples</span></span>

- <span data-ttu-id="d013c-125">Dodaj `nuget.org` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="d013c-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="d013c-126">Dodaj `c:\packages` jako źródło lokalne:</span><span class="sxs-lookup"><span data-stu-id="d013c-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="d013c-127">Dodaj źródło, które wymaga uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="d013c-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="d013c-128">Dodaj źródło, które wymaga uwierzytelniania (a następnie przejdź do dostawcy poświadczeń instalacji):</span><span class="sxs-lookup"><span data-stu-id="d013c-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="d013c-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d013c-129">See also</span></span>

- [<span data-ttu-id="d013c-130">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="d013c-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="d013c-131">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="d013c-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
