---
title: polecenie źródła aktualizacji dotnet nuget
description: Polecenie źródła aktualizacji dotnet nuget aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 42b1aec95cdd57e53f966400f6692a3d0150c16c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463480"
---
# <a name="dotnet-nuget-update-source"></a><span data-ttu-id="03003-103">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="03003-103">dotnet nuget update source</span></span>

<span data-ttu-id="03003-104">**Ten artykuł dotyczy:** ✔️.NET Core 3.1.200 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="03003-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="03003-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="03003-105">Name</span></span>

<span data-ttu-id="03003-106">`dotnet nuget update source`- Aktualizacja źródła NuGet.</span><span class="sxs-lookup"><span data-stu-id="03003-106">`dotnet nuget update source` - Update a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="03003-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="03003-107">Synopsis</span></span>

```dotnetcli
dotnet nuget update source <NAME> [--source <SOURCE>] [--username <USER>]
    [--password <PASSWORD>] [--store-password-in-clear-text]
    [--valid-authentication-types <TYPES>] [--configfile <FILE>]

dotnet nuget update source -h|--help
```

## <a name="description"></a><span data-ttu-id="03003-108">Opis</span><span class="sxs-lookup"><span data-stu-id="03003-108">Description</span></span>

<span data-ttu-id="03003-109">Polecenie `dotnet nuget update source` aktualizuje istniejące źródło w plikach konfiguracyjnych NuGet.</span><span class="sxs-lookup"><span data-stu-id="03003-109">The `dotnet nuget update source` command updates an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="03003-110">Argumenty</span><span class="sxs-lookup"><span data-stu-id="03003-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="03003-111">Nazwa źródła.</span><span class="sxs-lookup"><span data-stu-id="03003-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="03003-112">Opcje</span><span class="sxs-lookup"><span data-stu-id="03003-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="03003-113">Plik konfiguracyjny NuGet.</span><span class="sxs-lookup"><span data-stu-id="03003-113">The NuGet configuration file.</span></span> <span data-ttu-id="03003-114">Jeśli zostanie określony, będą używane tylko ustawienia z tego pliku.</span><span class="sxs-lookup"><span data-stu-id="03003-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="03003-115">Jeśli nie zostanie określona, zostanie użyta hierarchia plików konfiguracyjnych z bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="03003-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="03003-116">Aby uzyskać więcej informacji, zobacz [typowe konfiguracje NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="03003-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`-p|--password <PASSWORD>`**

  <span data-ttu-id="03003-117">Hasło, które ma być używane podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="03003-117">Password to be used when connecting to an authenticated source.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="03003-118">Ścieżka do źródła pakietu.</span><span class="sxs-lookup"><span data-stu-id="03003-118">Path to the package source.</span></span>

- **`--store-password-in-clear-text`**

  <span data-ttu-id="03003-119">Umożliwia przechowywanie poświadczeń źródła pakietu przenośnego przez wyłączenie szyfrowania haseł.</span><span class="sxs-lookup"><span data-stu-id="03003-119">Enables storing portable package source credentials by disabling password encryption.</span></span>

- **`-u|--username <USER>`**

  <span data-ttu-id="03003-120">Nazwa użytkownika, która ma być używana podczas łączenia się z uwierzytelnionym źródłem.</span><span class="sxs-lookup"><span data-stu-id="03003-120">Username to be used when connecting to an authenticated source.</span></span>

- **`--valid-authentication-types <TYPES>`**

  <span data-ttu-id="03003-121">Oddzielona przecinkami lista prawidłowych typów uwierzytelniania dla tego źródła.</span><span class="sxs-lookup"><span data-stu-id="03003-121">Comma-separated list of valid authentication types for this source.</span></span> <span data-ttu-id="03003-122">Ustaw to, `basic` jeśli serwer anonsuje NTLM lub Negocjuj, a poświadczenia muszą być wysyłane przy użyciu mechanizmu Basic, na przykład podczas korzystania z pat z lokalnym serwerem Azure DevOps Server.</span><span class="sxs-lookup"><span data-stu-id="03003-122">Set this to `basic` if the server advertises NTLM or Negotiate and your credentials must be sent using the Basic mechanism, for instance when using a PAT with on-premises Azure DevOps Server.</span></span> <span data-ttu-id="03003-123">Inne prawidłowe `negotiate` `kerberos`wartości `ntlm`to `digest`, , i , ale te wartości są mało prawdopodobne, aby być przydatne.</span><span class="sxs-lookup"><span data-stu-id="03003-123">Other valid values include `negotiate`, `kerberos`, `ntlm`, and `digest`, but these values are unlikely to be useful.</span></span>

## <a name="examples"></a><span data-ttu-id="03003-124">Przykłady</span><span class="sxs-lookup"><span data-stu-id="03003-124">Examples</span></span>

- <span data-ttu-id="03003-125">Aktualizowanie źródła o `mySource`nazwie :</span><span class="sxs-lookup"><span data-stu-id="03003-125">Update a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget update source mySource --source c:\packages
  ```

## <a name="see-also"></a><span data-ttu-id="03003-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03003-126">See also</span></span>

- [<span data-ttu-id="03003-127">Sekcje źródła pakietów w plikach NuGet.config</span><span class="sxs-lookup"><span data-stu-id="03003-127">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="03003-128">sources, polecenie (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="03003-128">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
