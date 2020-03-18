---
title: Co nowego w programie .NET Core 3.1
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 323a2390f079c17b81db01e4e3787916251943bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156559"
---
# <a name="whats-new-in-net-core-31"></a><span data-ttu-id="1f3ec-103">Co nowego w programie .NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1f3ec-103">What's new in .NET Core 3.1</span></span>

<span data-ttu-id="1f3ec-104">W tym artykule opisano nowości w .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-104">This article describes what is new in .NET Core 3.1.</span></span> <span data-ttu-id="1f3ec-105">Ta wersja zawiera drobne ulepszenia .NET Core 3.0, koncentrując się na małych, ale ważne poprawki.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-105">This release contains minor improvements to .NET Core 3.0, focusing on small, but important, fixes.</span></span> <span data-ttu-id="1f3ec-106">Najważniejszą cechą programu .NET Core 3.1 jest to, że jest to [wersja długoterminowej pomocy technicznej (LTS).](#long-term-support)</span><span class="sxs-lookup"><span data-stu-id="1f3ec-106">The most important feature about .NET Core 3.1 is that it's a [long-term support (LTS)](#long-term-support) release.</span></span>

<span data-ttu-id="1f3ec-107">Jeśli używasz programu Visual Studio 2019, musisz zaktualizować program [Visual Studio 2019 w wersji 16.4,](https://visualstudio.microsoft.com/downloads/) aby pracować z projektami .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-107">If you're using Visual Studio 2019, you must update to [Visual Studio 2019 version 16.4](https://visualstudio.microsoft.com/downloads/) to work with .NET Core 3.1 projects.</span></span> <span data-ttu-id="1f3ec-108">Aby uzyskać więcej informacji na temat nowości w programie Visual Studio, zobacz [Co nowego w programie Visual Studio 2019 w wersji 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span><span class="sxs-lookup"><span data-stu-id="1f3ec-108">For more information on what's new in Visual Studio, see [What's New in Visual Studio 2019 version 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).</span></span>

<span data-ttu-id="1f3ec-109">Program Visual Studio dla komputerów Mac obsługuje również program .NET Core 3.1 w programie Visual Studio dla komputerów Mac 8.4.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-109">Visual Studio for Mac also supports and includes .NET Core 3.1 in Visual Studio for Mac 8.4.</span></span>

<span data-ttu-id="1f3ec-110">Aby uzyskać więcej informacji na temat wydania, zobacz [anons .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span><span class="sxs-lookup"><span data-stu-id="1f3ec-110">For more information about the release, see the [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

- <span data-ttu-id="1f3ec-111">[Pobierz i zacznij korzystać z .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) w systemach Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-111">[Download and get started with .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) on Windows, macOS, or Linux.</span></span>

## <a name="long-term-support"></a><span data-ttu-id="1f3ec-112">Długoterminowe wsparcie</span><span class="sxs-lookup"><span data-stu-id="1f3ec-112">Long-term support</span></span>

<span data-ttu-id="1f3ec-113">.NET Core 3.1 to wersja LTS z pomocą firmy Microsoft przez następne trzy lata.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-113">.NET Core 3.1 is an LTS release with support from Microsoft for the next three years.</span></span> <span data-ttu-id="1f3ec-114">Zdecydowanie zaleca się przeniesienie aplikacji do .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-114">It's highly recommended that you move your apps to .NET Core 3.1.</span></span> <span data-ttu-id="1f3ec-115">Bieżący cykl życia innych głównych wersji jest następujący:</span><span class="sxs-lookup"><span data-stu-id="1f3ec-115">The current lifecycle of other major releases is as follows:</span></span>

| <span data-ttu-id="1f3ec-116">Release</span><span class="sxs-lookup"><span data-stu-id="1f3ec-116">Release</span></span> | <span data-ttu-id="1f3ec-117">Uwaga</span><span class="sxs-lookup"><span data-stu-id="1f3ec-117">Note</span></span> |
| ------- | ---- |
| <span data-ttu-id="1f3ec-118">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="1f3ec-118">.NET Core 3.0</span></span> | <span data-ttu-id="1f3ec-119">Koniec życia 3 marca 2020 roku.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-119">End of life on March 3, 2020.</span></span>     |
| <span data-ttu-id="1f3ec-120">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="1f3ec-120">.NET Core 2.2</span></span> | <span data-ttu-id="1f3ec-121">Koniec życia 23 grudnia 2019 r.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-121">End of life on December 23, 2019.</span></span> |
| <span data-ttu-id="1f3ec-122">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1f3ec-122">.NET Core 2.1</span></span> | <span data-ttu-id="1f3ec-123">Koniec życia 21 sierpnia 2021 roku.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-123">End of life on August 21, 2021.</span></span>    |

<span data-ttu-id="1f3ec-124">Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span><span class="sxs-lookup"><span data-stu-id="1f3ec-124">For more information, see the [.NET Core support policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span>

## <a name="macos-apphost-and-notarization"></a><span data-ttu-id="1f3ec-125">aplikacja macOSHost i notarialnie</span><span class="sxs-lookup"><span data-stu-id="1f3ec-125">macOS appHost and notarization</span></span>

<span data-ttu-id="1f3ec-126">*Tylko system macOS*</span><span class="sxs-lookup"><span data-stu-id="1f3ec-126">*macOS only*</span></span>

<span data-ttu-id="1f3ec-127">Począwszy od notarialnie .NET Core SDK 3.1 dla systemu macOS, ustawienie appHost jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-127">Starting with the notarized .NET Core SDK 3.1 for macOS, the appHost setting is disabled by default.</span></span> <span data-ttu-id="1f3ec-128">Aby uzyskać więcej informacji, zobacz [notarialnie Catalina w systemie macOS oraz wpływ na pobieranie i projekty programu .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="1f3ec-128">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="1f3ec-129">Gdy ustawienie appHost jest włączone, program .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-129">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="1f3ec-130">Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiany z kodu źródłowego za pomocą polecenia lub przez bezpośrednie uruchomienie pliku wykonywalnego Mach-O.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-130">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="1f3ec-131">Bez appHost, jedynym sposobem użytkownik może uruchomić aplikację zależną od `dotnet <filename.dll>` środowiska [uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-131">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="1f3ec-132">AppHost jest zawsze tworzony podczas publikowania aplikacji [niezależne .](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="1f3ec-132">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="1f3ec-133">Możesz skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:</span><span class="sxs-lookup"><span data-stu-id="1f3ec-133">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="1f3ec-134">Plik projektu</span><span class="sxs-lookup"><span data-stu-id="1f3ec-134">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="1f3ec-135">Parametr wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="1f3ec-135">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="1f3ec-136">Aby uzyskać więcej `UseAppHost` informacji o tym ustawieniu, zobacz [WŁAŚCIWOŚCI MSBuild dla programu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="1f3ec-136">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

## <a name="windows-forms"></a><span data-ttu-id="1f3ec-137">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1f3ec-137">Windows Forms</span></span>

<span data-ttu-id="1f3ec-138">*Tylko Windows*</span><span class="sxs-lookup"><span data-stu-id="1f3ec-138">*Windows only*</span></span>

> [!WARNING]
> <span data-ttu-id="1f3ec-139">Istnieją przełomowe zmiany w formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-139">There are breaking changes in Windows Forms.</span></span>

<span data-ttu-id="1f3ec-140">Starsze formanty zostały uwzględnione w formularzach systemu Windows, które były niedostępne w przyborniku projektanta programu Visual Studio przez pewien czas.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-140">Legacy controls were included in Windows Forms that have been unavailable in the Visual Studio Designer Toolbox for some time.</span></span> <span data-ttu-id="1f3ec-141">Zostały one zastąpione nowymi formantami z powrotem w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-141">These were replaced with new controls back in .NET Framework 2.0.</span></span> <span data-ttu-id="1f3ec-142">Zostały one usunięte z pulpitowego pakietu SDK dla .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-142">These have been removed from the Desktop SDK for .NET Core 3.1.</span></span>

| <span data-ttu-id="1f3ec-143">Usunięto kontrolę</span><span class="sxs-lookup"><span data-stu-id="1f3ec-143">Removed control</span></span> | <span data-ttu-id="1f3ec-144">Zalecana wymiana</span><span class="sxs-lookup"><span data-stu-id="1f3ec-144">Recommended replacement</span></span> | <span data-ttu-id="1f3ec-145">Skojarzone interfejsy API usunięte</span><span class="sxs-lookup"><span data-stu-id="1f3ec-145">Associated APIs removed</span></span> |
| --------------- | ----------------------- | ----------------------- |
| <span data-ttu-id="1f3ec-146">DataGrid</span><span class="sxs-lookup"><span data-stu-id="1f3ec-146">DataGrid</span></span>        | <xref:System.Windows.Forms.DataGridView>      | <span data-ttu-id="1f3ec-147">Datagridcell</span><span class="sxs-lookup"><span data-stu-id="1f3ec-147">DataGridCell</span></span><br/><span data-ttu-id="1f3ec-148">Datagridrow</span><span class="sxs-lookup"><span data-stu-id="1f3ec-148">DataGridRow</span></span><br/><span data-ttu-id="1f3ec-149">Zbieranie danych datagridtable</span><span class="sxs-lookup"><span data-stu-id="1f3ec-149">DataGridTableCollection</span></span><br/><span data-ttu-id="1f3ec-150">Datagridcolumncollection</span><span class="sxs-lookup"><span data-stu-id="1f3ec-150">DataGridColumnCollection</span></span><br/><span data-ttu-id="1f3ec-151">Datagridtablestyle</span><span class="sxs-lookup"><span data-stu-id="1f3ec-151">DataGridTableStyle</span></span><br/><span data-ttu-id="1f3ec-152">Datagridcolumnstyle</span><span class="sxs-lookup"><span data-stu-id="1f3ec-152">DataGridColumnStyle</span></span><br/><span data-ttu-id="1f3ec-153">Styl DataGridLine</span><span class="sxs-lookup"><span data-stu-id="1f3ec-153">DataGridLineStyle</span></span><br/><span data-ttu-id="1f3ec-154">Etykieta DataGridParentRowsLabel</span><span class="sxs-lookup"><span data-stu-id="1f3ec-154">DataGridParentRowsLabel</span></span><br/><span data-ttu-id="1f3ec-155">Styl LabelGridParentRows</span><span class="sxs-lookup"><span data-stu-id="1f3ec-155">DataGridParentRowsLabelStyle</span></span><br/><span data-ttu-id="1f3ec-156">Datagridboolcolumn</span><span class="sxs-lookup"><span data-stu-id="1f3ec-156">DataGridBoolColumn</span></span><br/><span data-ttu-id="1f3ec-157">Datagridtextbox</span><span class="sxs-lookup"><span data-stu-id="1f3ec-157">DataGridTextBox</span></span><br/><span data-ttu-id="1f3ec-158">Gridcolumnstylescollection</span><span class="sxs-lookup"><span data-stu-id="1f3ec-158">GridColumnStylesCollection</span></span><br/><span data-ttu-id="1f3ec-159">Gridtablestylescollection</span><span class="sxs-lookup"><span data-stu-id="1f3ec-159">GridTableStylesCollection</span></span><br/><span data-ttu-id="1f3ec-160">Typ hitu</span><span class="sxs-lookup"><span data-stu-id="1f3ec-160">HitTestType</span></span> |
| <span data-ttu-id="1f3ec-161">ToolBar</span><span class="sxs-lookup"><span data-stu-id="1f3ec-161">ToolBar</span></span>         | <xref:System.Windows.Forms.ToolStrip>         | <span data-ttu-id="1f3ec-162">Wygląd paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="1f3ec-162">ToolBarAppearance</span></span> |
| <span data-ttu-id="1f3ec-163">Toolbarbutton</span><span class="sxs-lookup"><span data-stu-id="1f3ec-163">ToolBarButton</span></span>   | <xref:System.Windows.Forms.ToolStripButton>   | <span data-ttu-id="1f3ec-164">Narzędzie ToolBarButtonClickEventArgs</span><span class="sxs-lookup"><span data-stu-id="1f3ec-164">ToolBarButtonClickEventArgs</span></span><br/><span data-ttu-id="1f3ec-165">Program obsługi zdarzeń toolbarbuttonclick</span><span class="sxs-lookup"><span data-stu-id="1f3ec-165">ToolBarButtonClickEventHandler</span></span><br/><span data-ttu-id="1f3ec-166">Styl paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="1f3ec-166">ToolBarButtonStyle</span></span><br/><span data-ttu-id="1f3ec-167">Wyrównywanie tekstu paska narzędzi</span><span class="sxs-lookup"><span data-stu-id="1f3ec-167">ToolBarTextAlign</span></span> |
| <span data-ttu-id="1f3ec-168">ContextMenu</span><span class="sxs-lookup"><span data-stu-id="1f3ec-168">ContextMenu</span></span>     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | <span data-ttu-id="1f3ec-169">Menuitemcollection</span><span class="sxs-lookup"><span data-stu-id="1f3ec-169">MenuItemCollection</span></span> |
| <span data-ttu-id="1f3ec-170">Mainmenu</span><span class="sxs-lookup"><span data-stu-id="1f3ec-170">MainMenu</span></span>        | <xref:System.Windows.Forms.MenuStrip>         |  |
| <span data-ttu-id="1f3ec-171">MenuItem</span><span class="sxs-lookup"><span data-stu-id="1f3ec-171">MenuItem</span></span>        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

<span data-ttu-id="1f3ec-172">Firma Microsoft zaleca zaktualizowanie aplikacji do .NET Core 3.1 i przejście do formantów zastępowania.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-172">We recommend you update your applications to .NET Core 3.1 and move to the replacement controls.</span></span> <span data-ttu-id="1f3ec-173">Zastąpienie formantów jest prostym procesem, zasadniczo "znajdź i zamień" na typie.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-173">Replacing the controls is a straightforward process, essentially "find and replace" on the type.</span></span>

## <a name="ccli"></a><span data-ttu-id="1f3ec-174">C++/CLI</span><span class="sxs-lookup"><span data-stu-id="1f3ec-174">C++/CLI</span></span>

<span data-ttu-id="1f3ec-175">*Tylko Windows*</span><span class="sxs-lookup"><span data-stu-id="1f3ec-175">*Windows only*</span></span>

<span data-ttu-id="1f3ec-176">Dodano obsługę tworzenia projektów C++/CLI (znanych również jako "zarządzane C++").</span><span class="sxs-lookup"><span data-stu-id="1f3ec-176">Support has been added for creating C++/CLI (also known as "managed C++") projects.</span></span> <span data-ttu-id="1f3ec-177">Pliki binarne produkowane z tych projektów są zgodne z .NET Core 3.0 i nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-177">Binaries produced from these projects are compatible with .NET Core 3.0 and later versions.</span></span>

<span data-ttu-id="1f3ec-178">Aby dodać obsługę języka C++/CLI w programie Visual Studio 2019 w wersji 16.4, zainstaluj [programowanie pulpitu z obciążeniem języka C++.](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads)</span><span class="sxs-lookup"><span data-stu-id="1f3ec-178">To add support for C++/CLI in Visual Studio 2019 version 16.4, install the [Desktop development with C++ workload](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads).</span></span> <span data-ttu-id="1f3ec-179">To obciążenie dodaje dwa szablony do programu Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="1f3ec-179">This workload adds two templates to Visual Studio:</span></span>

- <span data-ttu-id="1f3ec-180">Biblioteka klas CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="1f3ec-180">CLR Class Library (.NET Core)</span></span>
- <span data-ttu-id="1f3ec-181">Pusty projekt CLR (.NET Core)</span><span class="sxs-lookup"><span data-stu-id="1f3ec-181">CLR Empty Project (.NET Core)</span></span>

## <a name="next-steps"></a><span data-ttu-id="1f3ec-182">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1f3ec-182">Next steps</span></span>

- [<span data-ttu-id="1f3ec-183">Przejrzyj zmiany dotyczące podziału między programami .NET Core 3.0 i 3.1.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-183">Review the breaking changes between .NET Core 3.0 and 3.1.</span></span>](../compatibility/3.0-3.1.md)
- [<span data-ttu-id="1f3ec-184">Przejrzyj zmiany dotyczące łamania zasad w aplikacji .NET Core 3.1 dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1f3ec-184">Review the breaking changes in .NET Core 3.1 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-31)
