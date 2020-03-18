---
title: 'Samouczek: Instalowanie i używanie narzędzi lokalnych .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i używać go jako narzędzia lokalnego.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156702"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="8c1da-103">Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c1da-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="8c1da-104">**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="8c1da-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="8c1da-105">W tym samouczku nauczycię, jak zainstalować i używać lokalnego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="8c1da-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="8c1da-106">Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8c1da-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c1da-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c1da-107">Prerequisites</span></span>

* <span data-ttu-id="8c1da-108">Ukończ [pierwszy samouczek z tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8c1da-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="8c1da-109">Zainstaluj program .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="8c1da-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="8c1da-110">W tym samouczku należy zainstalować i użyć narzędzia przeznaczonego dla programu .NET Core 2.1, więc musisz zainstalować ten czas uruchomieniowy na komputerze.</span><span class="sxs-lookup"><span data-stu-id="8c1da-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="8c1da-111">Aby zainstalować czas uruchomieniowy 2.1, przejdź do [strony pobierania .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) i znajdź łącze instalacji programu Run w kolumnie **Uruchom aplikacje — Czas wykonywania.**</span><span class="sxs-lookup"><span data-stu-id="8c1da-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="8c1da-112">Tworzenie pliku manifestu</span><span class="sxs-lookup"><span data-stu-id="8c1da-112">Create a manifest file</span></span>

<span data-ttu-id="8c1da-113">Aby zainstalować narzędzie tylko dla dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy je dodać do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="8c1da-114">Z folderu *microsoft.botsay* przejdź do jednego poziomu do folderu *repozytorium:*</span><span class="sxs-lookup"><span data-stu-id="8c1da-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="8c1da-115">Utwórz plik manifestu, uruchamiając [polecenie dotnet nowe:](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="8c1da-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="8c1da-116">Dane wyjściowe wskazują na pomyślne utworzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="8c1da-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="8c1da-117">Plik *.config/dotnet-tools.json* nie zawiera jeszcze żadnych narzędzi:</span><span class="sxs-lookup"><span data-stu-id="8c1da-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="8c1da-118">Narzędzia wymienione w pliku manifestu są dostępne dla bieżącego katalogu i podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="8c1da-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="8c1da-119">Bieżący katalog to katalog zawierający katalog *konfiguracyjny* z plikiem manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="8c1da-120">Korzystając z polecenia wiersza polecenia, które odwołuje się do narzędzia lokalnego, zestaw SDK wyszukuje plik manifestu w bieżącym katalogu i katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8c1da-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="8c1da-121">Jeśli znajdzie plik manifestu, ale plik nie zawiera narzędzia, do którego do której dowołuje się, kontynuuje wyszukiwanie w górę za pośrednictwem katalogów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8c1da-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="8c1da-122">Wyszukiwanie kończy się, gdy znajdzie narzędzie, do którego `isRoot` istnieje `true`odwołanie, lub znajdzie plik manifestu z ustawieniem .</span><span class="sxs-lookup"><span data-stu-id="8c1da-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="8c1da-123">Zainstaluj botsay jako narzędzie lokalne</span><span class="sxs-lookup"><span data-stu-id="8c1da-123">Install botsay as a local tool</span></span>

<span data-ttu-id="8c1da-124">Zainstaluj narzędzie z pakietu utworzonego w pierwszym samouczku:</span><span class="sxs-lookup"><span data-stu-id="8c1da-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="8c1da-125">To polecenie dodaje narzędzie do pliku manifestu utworzonego w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="8c1da-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="8c1da-126">Dane wyjściowe polecenia pokazuje, w którym pliku manifestu znajduje się nowo zainstalowane narzędzie:</span><span class="sxs-lookup"><span data-stu-id="8c1da-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="8c1da-127">Plik *.config/dotnet-tools.json* ma teraz jedno narzędzie:</span><span class="sxs-lookup"><span data-stu-id="8c1da-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="8c1da-128">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="8c1da-128">Use the tool</span></span>

<span data-ttu-id="8c1da-129">Wywołaj narzędzie, uruchamiając `dotnet tool run` polecenie z folderu *repozytorium:*</span><span class="sxs-lookup"><span data-stu-id="8c1da-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="8c1da-130">Przywracanie lokalnego narzędzia zainstalowanego przez inne osoby</span><span class="sxs-lookup"><span data-stu-id="8c1da-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="8c1da-131">Zazwyczaj instalujesz narzędzie lokalne w katalogu głównym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="8c1da-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="8c1da-132">Po zaewidencjonowanie pliku manifestu do repozytorium, inni deweloperzy mogą uzyskać najnowszy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="8c1da-133">Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, `dotnet tool restore` można uruchomić jedno polecenie.</span><span class="sxs-lookup"><span data-stu-id="8c1da-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="8c1da-134">Otwórz plik *.config/dotnet-tools.json* i zastąp zawartość następującym plikiem JSON:</span><span class="sxs-lookup"><span data-stu-id="8c1da-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="8c1da-135">Zastąp `<name>` nazwę użytą do utworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="8c1da-136">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="8c1da-136">Save your changes.</span></span>

   <span data-ttu-id="8c1da-137">Wprowadzenie tej zmiany jest taka sama jak uzyskanie najnowszej wersji z repozytorium po zainstalowaniu pakietu `dotnetsay` dla katalogu projektu przez inną osobę.</span><span class="sxs-lookup"><span data-stu-id="8c1da-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="8c1da-138">Uruchom polecenie `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="8c1da-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="8c1da-139">Polecenie generuje dane wyjściowe, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8c1da-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="8c1da-140">Sprawdź, czy narzędzia są dostępne:</span><span class="sxs-lookup"><span data-stu-id="8c1da-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="8c1da-141">Dane wyjściowe to lista pakietów i poleceń, podobna do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="8c1da-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="8c1da-142">Przetestuj narzędzia:</span><span class="sxs-lookup"><span data-stu-id="8c1da-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="8c1da-143">Aktualizowanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="8c1da-143">Update a local tool</span></span>

<span data-ttu-id="8c1da-144">Zainstalowana wersja narzędzia `dotnetsay` lokalnego to 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="8c1da-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="8c1da-145">Najnowsza wersja to 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="8c1da-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="8c1da-146">Użyj polecenia [dotnet tool update,](dotnet-tool-update.md) aby zaktualizować narzędzie do najnowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="8c1da-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="8c1da-147">Dane wyjściowe wskazują nowy numer wersji:</span><span class="sxs-lookup"><span data-stu-id="8c1da-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="8c1da-148">Polecenie update znajdzie pierwszy plik manifestu, który zawiera identyfikator pakietu i aktualizuje go.</span><span class="sxs-lookup"><span data-stu-id="8c1da-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="8c1da-149">Jeśli nie ma takiego identyfikatora pakietu w żadnym pliku manifestu, który znajduje się w zakresie wyszukiwania, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="8c1da-150">Zakres wyszukiwania jest za pośrednictwem katalogów `isRoot = true` nadrzędnych, dopóki nie zostanie znaleziony plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c1da-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="8c1da-151">Usuwanie narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="8c1da-151">Remove local tools</span></span>

<span data-ttu-id="8c1da-152">Usuń zainstalowane narzędzia, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="8c1da-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="8c1da-153">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8c1da-153">Troubleshoot</span></span>

<span data-ttu-id="8c1da-154">Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8c1da-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c1da-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c1da-155">See also</span></span>

<span data-ttu-id="8c1da-156">Aby uzyskać więcej informacji, zobacz [narzędzia .NET Core](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8c1da-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
