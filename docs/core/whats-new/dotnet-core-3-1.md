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
# <a name="whats-new-in-net-core-31"></a>Co nowego w programie .NET Core 3.1

W tym artykule opisano nowości w .NET Core 3.1. Ta wersja zawiera drobne ulepszenia .NET Core 3.0, koncentrując się na małych, ale ważne poprawki. Najważniejszą cechą programu .NET Core 3.1 jest to, że jest to [wersja długoterminowej pomocy technicznej (LTS).](#long-term-support)

Jeśli używasz programu Visual Studio 2019, musisz zaktualizować program [Visual Studio 2019 w wersji 16.4,](https://visualstudio.microsoft.com/downloads/) aby pracować z projektami .NET Core 3.1. Aby uzyskać więcej informacji na temat nowości w programie Visual Studio, zobacz [Co nowego w programie Visual Studio 2019 w wersji 16.4](/visualstudio/releases/2019/release-notes#whats-new-in-visual-studio-2019-version-164).

Program Visual Studio dla komputerów Mac obsługuje również program .NET Core 3.1 w programie Visual Studio dla komputerów Mac 8.4.

Aby uzyskać więcej informacji na temat wydania, zobacz [anons .NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Pobierz i zacznij korzystać z .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) w systemach Windows, macOS lub Linux.

## <a name="long-term-support"></a>Długoterminowe wsparcie

.NET Core 3.1 to wersja LTS z pomocą firmy Microsoft przez następne trzy lata. Zdecydowanie zaleca się przeniesienie aplikacji do .NET Core 3.1. Bieżący cykl życia innych głównych wersji jest następujący:

| Release | Uwaga |
| ------- | ---- |
| .NET Core 3.0 | Koniec życia 3 marca 2020 roku.     |
| .NET Core 2.2 | Koniec życia 23 grudnia 2019 r. |
| .NET Core 2.1 | Koniec życia 21 sierpnia 2021 roku.    |

Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>aplikacja macOSHost i notarialnie

*Tylko system macOS*

Począwszy od notarialnie .NET Core SDK 3.1 dla systemu macOS, ustawienie appHost jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [notarialnie Catalina w systemie macOS oraz wpływ na pobieranie i projekty programu .NET Core](../install/macos-notarization-issues.md).

Gdy ustawienie appHost jest włączone, program .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania. Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiany z kodu źródłowego za pomocą polecenia lub przez bezpośrednie uruchomienie pliku wykonywalnego Mach-O.

Bez appHost, jedynym sposobem użytkownik może uruchomić aplikację zależną od `dotnet <filename.dll>` środowiska [uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest z poleceniem. AppHost jest zawsze tworzony podczas publikowania aplikacji [niezależne .](../deploying/index.md#publish-self-contained)

Możesz skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:

- Plik projektu

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- Parametr wiersza polecenia

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

Aby uzyskać więcej `UseAppHost` informacji o tym ustawieniu, zobacz [WŁAŚCIWOŚCI MSBuild dla programu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Tylko Windows*

> [!WARNING]
> Istnieją przełomowe zmiany w formularzach systemu Windows.

Starsze formanty zostały uwzględnione w formularzach systemu Windows, które były niedostępne w przyborniku projektanta programu Visual Studio przez pewien czas. Zostały one zastąpione nowymi formantami z powrotem w .NET Framework 2.0. Zostały one usunięte z pulpitowego pakietu SDK dla .NET Core 3.1.

| Usunięto kontrolę | Zalecana wymiana | Skojarzone interfejsy API usunięte |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | Datagridcell<br/>Datagridrow<br/>Zbieranie danych datagridtable<br/>Datagridcolumncollection<br/>Datagridtablestyle<br/>Datagridcolumnstyle<br/>Styl DataGridLine<br/>Etykieta DataGridParentRowsLabel<br/>Styl LabelGridParentRows<br/>Datagridboolcolumn<br/>Datagridtextbox<br/>Gridcolumnstylescollection<br/>Gridtablestylescollection<br/>Typ hitu |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Wygląd paska narzędzi |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | Narzędzie ToolBarButtonClickEventArgs<br/>Program obsługi zdarzeń toolbarbuttonclick<br/>Styl paska narzędzi<br/>Wyrównywanie tekstu paska narzędzi |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | Menuitemcollection |
| Mainmenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Firma Microsoft zaleca zaktualizowanie aplikacji do .NET Core 3.1 i przejście do formantów zastępowania. Zastąpienie formantów jest prostym procesem, zasadniczo "znajdź i zamień" na typie.

## <a name="ccli"></a>C++/CLI

*Tylko Windows*

Dodano obsługę tworzenia projektów C++/CLI (znanych również jako "zarządzane C++"). Pliki binarne produkowane z tych projektów są zgodne z .NET Core 3.0 i nowszymi wersjami.

Aby dodać obsługę języka C++/CLI w programie Visual Studio 2019 w wersji 16.4, zainstaluj [programowanie pulpitu z obciążeniem języka C++.](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads) To obciążenie dodaje dwa szablony do programu Visual Studio:

- Biblioteka klas CLR (.NET Core)
- Pusty projekt CLR (.NET Core)

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj zmiany dotyczące podziału między programami .NET Core 3.0 i 3.1.](../compatibility/3.0-3.1.md)
- [Przejrzyj zmiany dotyczące łamania zasad w aplikacji .NET Core 3.1 dla formularzy systemu Windows.](../compatibility/winforms.md#net-core-31)
