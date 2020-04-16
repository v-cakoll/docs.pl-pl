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
# <a name="dotnet-nuget-add-source"></a><span data-ttu-id="8b7d8-103">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="8b7d8-103">dotnet nuget add source</span></span>

<span data-ttu-id="8b7d8-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="8b7d8-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="8b7d8-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="8b7d8-105">Name</span></span>

<span data-ttu-id="8b7d8-106">`dotnet nuget add source`- Dodaj źródło NuGet.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-106">`dotnet nuget add source` - Add a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="8b7d8-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="8b7d8-107">Synopsis</span></span>

```dotnetcli
dotnet nuget add source <PACKAGE_SOURCE_PATH> [--name <SOURCE_NAME>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget add source -h|--help
```

## <a name="description"></a><span data-ttu-id="8b7d8-108">Opis</span><span class="sxs-lookup"><span data-stu-id="8b7d8-108">Description</span></span>

<span data-ttu-id="8b7d8-109">Polecenie `dotnet nuget add source` dodaje nowe źródło pakietu do plików konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-109">The `dotnet nuget add source` command adds a new package source to your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="8b7d8-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="8b7d8-110">Arguments</span></span>

- **`PACKAGE_SOURCE_PATH`**

  <span data-ttu-id="8b7d8-111">Ścieżka do źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-111">Path to the package source.</span></span>

## <a name="options"></a><span data-ttu-id="8b7d8-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="8b7d8-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="8b7d8-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-113">The NuGet configuration file.</span></span> <span data-ttu-id="8b7d8-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="8b7d8-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="8b7d8-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="8b7d8-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-n|--name <SOURCE_NAME>`**

  <span data-ttu-id="8b7d8-117">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-117">Name of the source.</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="8b7d8-118">Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-118">Password to be used when connecting to an authenticated source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="8b7d8-119">Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="8b7d8-120">Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="8b7d8-121">Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="8b7d8-122">Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="8b7d8-123">Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="8b7d8-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="8b7d8-124">Examples</span></span>

- <span data-ttu-id="8b7d8-125">Dodaj `nuget.org` jako źródło:</span><span class="sxs-lookup"><span data-stu-id="8b7d8-125">Add `nuget.org` as a source:</span></span>

  ```dotnetcli
  dotnet nuget add source https://api.nuget.org/v3/index.json -n nuget.org
  ```

- <span data-ttu-id="8b7d8-126">Dodaj `c:\packages` jako źródło lokalne:</span><span class="sxs-lookup"><span data-stu-id="8b7d8-126">Add `c:\packages` as a local source:</span></span>

  ```dotnetcli
  dotnet nuget add source c:\packages
  ```

- <span data-ttu-id="8b7d8-127">Dodaj źródło, które wymaga uwierzytelniania:</span><span class="sxs-lookup"><span data-stu-id="8b7d8-127">Add a source that needs authentication:</span></span>

  ```dotnetcli
  dotnet nuget add source https://someServer/myTeam -n myTeam -u myUsername -p myPassword --store-password-in-clear-text
  ```

- <span data-ttu-id="8b7d8-128">Dodaj źródło, które wymaga uwierzytelniania (a następnie przejdź do dostawcy poświadczeń instalacji):</span><span class="sxs-lookup"><span data-stu-id="8b7d8-128">Add a source that needs authentication (then go install credential provider):</span></span>

  ```dotnetcli
  dotnet nuget add source https://azureartifacts.microsoft.com/myTeam -n myTeam
  ```

## <a name="see-also"></a><span data-ttu-id="8b7d8-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8b7d8-129">See also</span></span>

- [<span data-ttu-id="8b7d8-130">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="8b7d8-130">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="8b7d8-131">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="8b7d8-131">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
