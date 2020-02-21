---
title: 'Samouczek: Instalowanie i używanie narzędzia globalnego platformy .NET Core'
description: Dowiedz się, jak zainstalować narzędzie .NET i korzystać z niego jako narzędzia globalnego.
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543874"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a><span data-ttu-id="34a28-103">Samouczek: Instalowanie i używanie narzędzia globalnego platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="34a28-103">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>

<span data-ttu-id="34a28-104">**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach</span><span class="sxs-lookup"><span data-stu-id="34a28-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="34a28-105">W tym samouczku przedstawiono sposób instalowania i używania narzędzia globalnego.</span><span class="sxs-lookup"><span data-stu-id="34a28-105">This tutorial teaches you how to install and use a global tool.</span></span> <span data-ttu-id="34a28-106">Używasz narzędzia, które tworzysz w [pierwszym samouczku tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="34a28-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="34a28-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="34a28-107">Prerequisites</span></span>

* <span data-ttu-id="34a28-108">Wykonaj [pierwszy samouczek tej serii](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="34a28-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="use-the-tool-as-a-global-tool"></a><span data-ttu-id="34a28-109">Użyj narzędzia jako narzędzia globalnego</span><span class="sxs-lookup"><span data-stu-id="34a28-109">Use the tool as a global tool</span></span>

1. <span data-ttu-id="34a28-110">Zainstaluj narzędzie z pakietu, uruchamiając polecenie [Narzędzia dotnet](dotnet-tool-install.md) w *nazwie botsay\<>* folderze projektu:</span><span class="sxs-lookup"><span data-stu-id="34a28-110">Install the tool from the package by running the [dotnet tool install](dotnet-tool-install.md) command in the *botsay-\<name>* project folder:</span></span>

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="34a28-111">`--global` parametr informuje interfejs wiersza polecenia platformy .NET Core o konieczności zainstalowania plików binarnych narzędzia w domyślnej lokalizacji, która jest automatycznie dodawana do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="34a28-111">The `--global` parameter tells the .NET Core CLI to install the tool binaries in a default location that is automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="34a28-112">`--add-source` parametr informuje interfejs wiersza polecenia platformy .NET Core o tymczasowym użyciu katalogu *./nupkg* jako dodatkowego źródła strumieniowego dla pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="34a28-112">The `--add-source` parameter tells the .NET Core CLI to temporarily use the *./nupkg* directory as an additional source feed for NuGet packages.</span></span> <span data-ttu-id="34a28-113">Pakiet ma unikatową nazwę, aby upewnić się, że zostanie on znaleziony tylko w katalogu *./nupkg* , a nie w witrynie NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="34a28-113">You gave your package a unique name to make sure that it will only be found in the *./nupkg* directory, not on the Nuget.org site.</span></span> 

   <span data-ttu-id="34a28-114">Dane wyjściowe przedstawiają polecenie używane do wywoływania narzędzia i zainstalowanej wersji:</span><span class="sxs-lookup"><span data-stu-id="34a28-114">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="34a28-115">Wywołaj narzędzie:</span><span class="sxs-lookup"><span data-stu-id="34a28-115">Invoke the tool:</span></span>

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > <span data-ttu-id="34a28-116">Jeśli to polecenie nie powiedzie się, może być konieczne otwarcie nowego terminalu w celu odświeżenia ścieżki.</span><span class="sxs-lookup"><span data-stu-id="34a28-116">If this command fails, you may need to open a new terminal to refresh the PATH.</span></span>

1. <span data-ttu-id="34a28-117">Aby usunąć narzędzie, należy wykonać polecenie [odinstalowania narzędzia dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="34a28-117">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a><span data-ttu-id="34a28-118">Używanie narzędzia jako globalnego narzędzia zainstalowanego w lokalizacji niestandardowej</span><span class="sxs-lookup"><span data-stu-id="34a28-118">Use the tool as a global tool installed in a custom location</span></span>

1. <span data-ttu-id="34a28-119">Zainstaluj narzędzie z pakietu.</span><span class="sxs-lookup"><span data-stu-id="34a28-119">Install the tool from the package.</span></span>

   <span data-ttu-id="34a28-120">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="34a28-120">On Windows:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="34a28-121">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="34a28-121">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="34a28-122">`--tool-path` parametr informuje interfejs wiersza polecenia platformy .NET Core o konieczności zainstalowania plików binarnych narzędzia w określonej lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="34a28-122">The `--tool-path` parameter tells the .NET Core CLI to install the tool binaries in the specified location.</span></span> <span data-ttu-id="34a28-123">Jeśli katalog nie istnieje, zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="34a28-123">If the directory doesn't exist, it is created.</span></span> <span data-ttu-id="34a28-124">Ten katalog nie jest automatycznie dodawany do zmiennej środowiskowej PATH.</span><span class="sxs-lookup"><span data-stu-id="34a28-124">This directory is not automatically added to the PATH environment variable.</span></span>

   <span data-ttu-id="34a28-125">Dane wyjściowe przedstawiają polecenie używane do wywoływania narzędzia i zainstalowanej wersji:</span><span class="sxs-lookup"><span data-stu-id="34a28-125">The output shows the command used to call the tool and the version installed:</span></span>

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. <span data-ttu-id="34a28-126">Wywołaj narzędzie:</span><span class="sxs-lookup"><span data-stu-id="34a28-126">Invoke the tool:</span></span>

   <span data-ttu-id="34a28-127">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="34a28-127">On Windows:</span></span>

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   <span data-ttu-id="34a28-128">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="34a28-128">On Linux or macOS:</span></span>

   ```console
   ~/bin/botsay hello from the bot
   ```

1. <span data-ttu-id="34a28-129">Aby usunąć narzędzie, należy wykonać polecenie [odinstalowania narzędzia dotnet](dotnet-tool-uninstall.md) :</span><span class="sxs-lookup"><span data-stu-id="34a28-129">Remove the tool by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

   <span data-ttu-id="34a28-130">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="34a28-130">On Windows:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   <span data-ttu-id="34a28-131">W systemie Linux lub macOS:</span><span class="sxs-lookup"><span data-stu-id="34a28-131">On Linux or macOS:</span></span>

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a><span data-ttu-id="34a28-132">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="34a28-132">Troubleshoot</span></span>

<span data-ttu-id="34a28-133">Jeśli podczas wykonywania samouczka zostanie wyświetlony komunikat o błędzie, zobacz [Rozwiązywanie problemów z użyciem narzędzia .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="34a28-133">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="34a28-134">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="34a28-134">Next steps</span></span>

<span data-ttu-id="34a28-135">W tym samouczku narzędzie zostało zainstalowane i użyte jako narzędzie globalne.</span><span class="sxs-lookup"><span data-stu-id="34a28-135">In this tutorial, you installed and used a tool as a global tool.</span></span> <span data-ttu-id="34a28-136">Aby zainstalować narzędzie i korzystać z tego samego narzędzia co narzędzie lokalne, przejdź do następnego samouczka.</span><span class="sxs-lookup"><span data-stu-id="34a28-136">To install and use the same tool as a local tool, advance to the next tutorial.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34a28-137">Instalowanie i używanie lokalnych narzędzi</span><span class="sxs-lookup"><span data-stu-id="34a28-137">Install and use local tools</span></span>](local-tools-how-to-use.md)
