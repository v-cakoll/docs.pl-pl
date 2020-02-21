---
title: 'Samouczek: Instalowanie i używanie lokalnych narzędzi platformy .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i korzystać z niego jako narzędzia lokalnego.
ms.date: 02/12/2020
ms.openlocfilehash: 6de620772cec1e9d1b1f57380b72c0163d68337c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543867"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="8c35a-103">Samouczek: Instalowanie lokalnego narzędzia .NET Core i używanie go przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8c35a-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="8c35a-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="8c35a-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="8c35a-105">W tym samouczku przedstawiono sposób instalowania i używania narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="8c35a-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="8c35a-106">Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8c35a-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8c35a-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8c35a-107">Prerequisites</span></span>

* <span data-ttu-id="8c35a-108">Wykonaj [pierwszy samouczek tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="8c35a-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="8c35a-109">Zainstaluj środowisko uruchomieniowe programu .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8c35a-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="8c35a-110">W tym samouczku zainstalujesz narzędzie, które jest przeznaczone dla platformy .NET Core 2,1, i użyjesz go, więc musisz mieć zainstalowane na maszynie środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="8c35a-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="8c35a-111">Aby zainstalować środowisko uruchomieniowe 2,1, przejdź do [strony pobierania programu .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1) i Znajdź link instalacja środowiska uruchomieniowego w kolumnie **Uruchamianie aplikacji — środowisko uruchomieniowe** .</span><span class="sxs-lookup"><span data-stu-id="8c35a-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="8c35a-112">Utwórz plik manifestu</span><span class="sxs-lookup"><span data-stu-id="8c35a-112">Create a manifest file</span></span>

<span data-ttu-id="8c35a-113">Aby zainstalować narzędzie tylko do dostępu lokalnego (dla bieżącego katalogu i podkatalogów), należy dodać je do pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span> 

<span data-ttu-id="8c35a-114">W folderze *botsay\<name >* przejdź do folderu *repozytorium* w górę o jeden poziom:</span><span class="sxs-lookup"><span data-stu-id="8c35a-114">From the *botsay-\<name>* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="8c35a-115">Utwórz plik manifestu, uruchamiając polecenie [dotnet New](dotnet-new.md) :</span><span class="sxs-lookup"><span data-stu-id="8c35a-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="8c35a-116">Dane wyjściowe wskazują pomyślne utworzenie pliku.</span><span class="sxs-lookup"><span data-stu-id="8c35a-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="8c35a-117">Plik *config/dotnet-Tools. JSON* nie zawiera jeszcze żadnych narzędzi:</span><span class="sxs-lookup"><span data-stu-id="8c35a-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="8c35a-118">Narzędzia wymienione w pliku manifestu są dostępne dla bieżącego katalogu i podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="8c35a-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="8c35a-119">Bieżącym katalogiem jest ten, który zawiera katalog *. config* z plikiem manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="8c35a-120">W przypadku korzystania z polecenia CLI odwołującego się do narzędzia lokalnego zestaw SDK wyszukuje plik manifestu w bieżącym katalogu i katalogach nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8c35a-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="8c35a-121">Jeśli odnajdzie plik manifestu, ale plik nie zawiera narzędzia, którego dotyczy odwołanie, kontynuuje wyszukiwanie za pomocą katalogów nadrzędnych.</span><span class="sxs-lookup"><span data-stu-id="8c35a-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="8c35a-122">Wyszukiwanie zostanie zakończone po znalezieniu narzędzia, którego dotyczy odwołanie, lub znalezienie pliku manifestu z `isRoot`m ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="8c35a-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="8c35a-123">Instalowanie botsay jako narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="8c35a-123">Install botsay as a local tool</span></span>

<span data-ttu-id="8c35a-124">Zainstaluj narzędzie z pakietu utworzonego w pierwszym samouczku:</span><span class="sxs-lookup"><span data-stu-id="8c35a-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./botsay-<name>/nupkg botsay-<name>
```

<span data-ttu-id="8c35a-125">To polecenie dodaje narzędzie do pliku manifestu, który został utworzony w poprzednim kroku.</span><span class="sxs-lookup"><span data-stu-id="8c35a-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="8c35a-126">Dane wyjściowe polecenia pokazują plik manifestu, w którym znajduje się nowo zainstalowane narzędzie:</span><span class="sxs-lookup"><span data-stu-id="8c35a-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="8c35a-127">Plik *config/dotnet-Tools. JSON* ma teraz jedno narzędzie:</span><span class="sxs-lookup"><span data-stu-id="8c35a-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "botsay-<name>": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="8c35a-128">Korzystanie z narzędzia</span><span class="sxs-lookup"><span data-stu-id="8c35a-128">Use the tool</span></span>

<span data-ttu-id="8c35a-129">Wywołaj narzędzie, uruchamiając polecenie `dotnet tool run` z folderu *repozytorium* :</span><span class="sxs-lookup"><span data-stu-id="8c35a-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="8c35a-130">Przywracanie lokalnego narzędzia zainstalowanego przez inne osoby</span><span class="sxs-lookup"><span data-stu-id="8c35a-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="8c35a-131">Zazwyczaj instalowane jest narzędzie lokalne w katalogu głównym repozytorium.</span><span class="sxs-lookup"><span data-stu-id="8c35a-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="8c35a-132">Po zaewidencjonowaniu pliku manifestu do repozytorium inni deweloperzy mogą uzyskać najnowszy plik manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="8c35a-133">Aby zainstalować wszystkie narzędzia wymienione w pliku manifestu, można uruchomić jedno `dotnet tool restore` polecenie.</span><span class="sxs-lookup"><span data-stu-id="8c35a-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="8c35a-134">Otwórz plik *config/dotnet-Tools. JSON* i Zastąp jego zawartość następującym kodem JSON:</span><span class="sxs-lookup"><span data-stu-id="8c35a-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "botsay-<name>": {
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

1. <span data-ttu-id="8c35a-135">Zastąp `<name>` nazwą użytą podczas tworzenia projektu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="8c35a-136">Zapisz zmiany.</span><span class="sxs-lookup"><span data-stu-id="8c35a-136">Save your changes.</span></span>

   <span data-ttu-id="8c35a-137">Wprowadzenie tej zmiany jest takie samo jak w przypadku pobierania najnowszej wersji z repozytorium, gdy ktoś inny zainstalował pakiet `dotnetsay` dla katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span> 

1. <span data-ttu-id="8c35a-138">Uruchom polecenie `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="8c35a-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="8c35a-139">Polecenie generuje dane wyjściowe podobne do następującego przykładu:</span><span class="sxs-lookup"><span data-stu-id="8c35a-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'botsay-<name>' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="8c35a-140">Sprawdź, czy narzędzia są dostępne:</span><span class="sxs-lookup"><span data-stu-id="8c35a-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="8c35a-141">Dane wyjściowe to lista pakietów i poleceń, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8c35a-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   -------------------------------------------------------------------------------------------
   botsay-<name>   1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay       2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="8c35a-142">Przetestuj narzędzia:</span><span class="sxs-lookup"><span data-stu-id="8c35a-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="8c35a-143">Aktualizowanie narzędzia lokalnego</span><span class="sxs-lookup"><span data-stu-id="8c35a-143">Update a local tool</span></span>

<span data-ttu-id="8c35a-144">Zainstalowana wersja `dotnetsay` lokalnego narzędzia to 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="8c35a-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="8c35a-145">Najnowsza wersja to 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="8c35a-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="8c35a-146">Aby zaktualizować narzędzie do najnowszej wersji, użyj polecenia [aktualizacji narzędzia dotnet](dotnet-tool-update.md) .</span><span class="sxs-lookup"><span data-stu-id="8c35a-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="8c35a-147">Dane wyjściowe wskazują nowy numer wersji:</span><span class="sxs-lookup"><span data-stu-id="8c35a-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="8c35a-148">Polecenie Update wyszukuje pierwszy plik manifestu zawierający identyfikator pakietu i aktualizuje go.</span><span class="sxs-lookup"><span data-stu-id="8c35a-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="8c35a-149">Jeśli nie ma takiego identyfikatora pakietu w żadnym pliku manifestu, który znajduje się w zakresie wyszukiwania, zestaw SDK dodaje nowy wpis do najbliższego pliku manifestu.</span><span class="sxs-lookup"><span data-stu-id="8c35a-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="8c35a-150">Zakres wyszukiwania znajduje się w katalogu nadrzędnym, dopóki nie zostanie znaleziony plik manifestu z `isRoot = true`.</span><span class="sxs-lookup"><span data-stu-id="8c35a-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="8c35a-151">Usuń narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="8c35a-151">Remove local tools</span></span>

<span data-ttu-id="8c35a-152">Aby usunąć zainstalowane narzędzia, należy uruchomić polecenie [Narzędzia dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="8c35a-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall botsay-<name>
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="8c35a-153">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="8c35a-153">Troubleshoot</span></span>

<span data-ttu-id="8c35a-154">Jeśli podczas wykonywania samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="8c35a-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8c35a-155">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8c35a-155">See also</span></span>

<span data-ttu-id="8c35a-156">Aby uzyskać więcej informacji, zobacz [Narzędzia platformy .NET Core](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="8c35a-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
