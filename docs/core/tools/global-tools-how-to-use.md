---
title: 'Samouczek: Instalowanie i używanie narzędzia globalnego .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i używać go jako narzędzia globalnego.
ms.date: 02/12/2020
ms.openlocfilehash: 9f8378e50fd2544eedbbaaeffb89d67800ec6880
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156741"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="31665-103">Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="31665-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="31665-104">**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji</span><span class="sxs-lookup"><span data-stu-id="31665-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="31665-105">W tym samouczku nauczycię, jak zainstalować i używać globalnego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="31665-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="31665-106">Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="31665-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="31665-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="31665-107">Prerequisites</span></span>

* <span data-ttu-id="31665-108">Ukończ [pierwszy samouczek z tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="31665-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="31665-109">Używanie narzędzia jako narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="31665-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="31665-110">Zainstaluj narzędzie z pakietu, uruchamiając polecenie [instalacji narzędzia dotnet](dotnet-tool-install.md) w folderze projektu *microsoft.botsay:*</span><span class="sxs-lookup"><span data-stu-id="31665-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *microsoft.botsay* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="31665-111">Parametr `--global` informuje polecenie .NET Core CLI o zainstalowaniu plików binarnych narzędzi w lokalizacji domyślnej, która jest automatycznie dodawana do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="31665-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="31665-112">Parametr `--add-source` informuje kontrolera CLI .NET Core o tymczasowym użyciu katalogu *./nupkg* jako dodatkowego źródła źródła dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="31665-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="31665-113">Nadasz pakietunikalną nazwę, aby upewnić się, że będzie ona dostępna tylko w katalogu *./nupkg,* a nie w Nuget.org witryny.</span><span class="sxs-lookup"><span data-stu-id="31665-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span>

   <span data-ttu-id="31665-114">Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowana wersja:</span><span class="sxs-lookup"><span data-stu-id="31665-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="31665-115">Wywołaj narzędzie:</span><span class="sxs-lookup"><span data-stu-id="31665-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="31665-116">Jeśli to polecenie nie powiedzie się, może być konieczne otwarcie nowego terminalu w celu odświeżenia ŚCIEŻKI.</span><span class="sxs-lookup"><span data-stu-id="31665-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="31665-117">Usuń narzędzie, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="31665-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g microsoft.botsay
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="31665-118">Używanie narzędzia jako narzędzia globalnego zainstalowanego w lokalizacji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="31665-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="31665-119">Zainstaluj narzędzie z opakowania.</span><span class="sxs-lookup"><span data-stu-id="31665-119">Install the tool from the package.</span></span>

   <span data-ttu-id="31665-120">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="31665-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="31665-121">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="31665-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg microsoft.botsay
   ```

   <span data-ttu-id="31665-122">Parametr `--tool-path` informuje cli .NET Core o zainstalowaniu plików binarnych narzędzi w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="31665-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="31665-123">Jeśli katalog nie istnieje, jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="31665-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="31665-124">Ten katalog nie jest automatycznie dodawany do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="31665-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="31665-125">Dane wyjściowe pokazuje polecenie używane do wywołania narzędzia i zainstalowana wersja:</span><span class="sxs-lookup"><span data-stu-id="31665-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="31665-126">Wywołaj narzędzie:</span><span class="sxs-lookup"><span data-stu-id="31665-126">Invoke the tool:</span></span>

   <span data-ttu-id="31665-127">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="31665-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="31665-128">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="31665-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="31665-129">Usuń narzędzie, uruchamiając polecenie [odinstalowywania narzędzia dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="31665-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="31665-130">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="31665-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools microsoft.botsay
   ```

   <span data-ttu-id="31665-131">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="31665-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin microsoft.botsay
   ```

## <a name="troubleshoot"></a><span data-ttu-id="31665-132">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="31665-132">Troubleshoot</span></span>

<span data-ttu-id="31665-133">Jeśli podczas korzystania z samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z używaniem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="31665-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="31665-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="31665-134">Next steps</span></span>

<span data-ttu-id="31665-135">W tym samouczku zainstalowano i użyto narzędzia jako narzędzia globalnego.</span><span class="sxs-lookup"><span data-stu-id="31665-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="31665-136">Aby zainstalować i używać tego samego narzędzia co narzędzie lokalne, przejdź do następnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="31665-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="31665-137">Instalowanie i używanie narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="31665-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
