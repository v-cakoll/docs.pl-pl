---
title: Co nowego w programie .NET Core 3.1
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core 3.1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: b52615a3fb288a6ca0622deb83f4db3c8e3587fb
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607909"
---
# <a name="whats-new-in-net-core-31"></a>Co nowego w programie .NET Core 3.1

W tym artykule opisano nowości w .NET Core 3.1. Ta wersja zawiera drobne ulepszenia programu .NET Core 3.0, koncentrujące się na małych, ale ważnych poprawkach. Najważniejszą cechą dotyczącą platformy .NET Core 3.1 jest to, że jest to [wersja z długim wsparciem (LTS).](#long-term-support)

Jeśli używasz programu Visual Studio 2019, należy zaktualizować do [programu Visual Studio 2019 w wersji 16.4 lub nowszej,](https://visualstudio.microsoft.com/downloads/) aby pracować z projektami .NET Core 3.1. Aby uzyskać informacje o nowościach w programie Visual Studio w wersji 16.4, zobacz [Co nowego w programie Visual Studio 2019 w wersji 16.4](/visualstudio/releases/2019/release-notes-v16.4#whats-new-in-visual-studio-2019-version-164).

Program Visual Studio dla komputerów Mac obsługuje również i zawiera program .NET Core 3.1 w programie Visual Studio dla komputerów Mac 8.4.

Aby uzyskać więcej informacji na temat wydania, zobacz [.NET Core 3.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Pobierz i zacznij cie z .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet-core/3.1) w systemie Windows, macOS lub Linux.

## <a name="long-term-support"></a>Wsparcie długoterminowe

.NET Core 3.1 to wersja LTS z pomocą firmy Microsoft przez następne trzy lata. Zdecydowanie zaleca się przeniesienie aplikacji do platformy .NET Core 3.1. Bieżący cykl życia innych głównych wydań jest następujący:

| Release | Uwaga |
| ------- | ---- |
| .NET Core 3.0 | Koniec życia 3 marca 2020 roku.     |
| .NET Core 2.2 | Koniec życia 23 grudnia 2019. |
| .NET Core 2.1 | Koniec życia 21 sierpnia 2021 roku.    |

Aby uzyskać więcej informacji, zobacz [zasady pomocy technicznej .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="macos-apphost-and-notarization"></a>aplikacja macOSHost i notarization

*Tylko system macOS*

Począwszy od nota pośledzonych pośowianych .NET Core SDK 3.1 dla systemu macOS, ustawienie appHost jest domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [system notarization systemu macOS Catalina i wpływ na pliki do pobrania i projekty .NET Core](../install/macos-notarization-issues.md).

Gdy ustawienie appHost jest włączone, .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania. Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiana z kodu źródłowego za pomocą polecenia lub uruchamiając plik wykonywalny Mach-O bezpośrednio.

Bez appHost, jedynym sposobem, w jaki użytkownik może uruchomić `dotnet <filename.dll>` aplikację [zależną od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest za pomocą polecenia. AplikacjaHost jest zawsze tworzony podczas publikowania aplikacji [samodzielny](../deploying/index.md#publish-self-contained).

Można skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:

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

Aby uzyskać więcej `UseAppHost` informacji na temat tego ustawienia, zobacz [Właściwości msbuild dla pliku Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).

## <a name="windows-forms"></a>Windows Forms

*Tylko Windows*

> [!WARNING]
> W formularzach systemu Windows występują przełomowe zmiany.

Starsze formanty zostały uwzględnione w formularzach systemu Windows, które były niedostępne w visual studio projektanta Toolbox przez pewien czas. Zostały one zastąpione nowymi formantami w ramach .NET Framework 2.0. Zostały one usunięte z pakietu SDK pulpitu dla platformy .NET Core 3.1.

| Usunięto kontrolę | Zalecana wymiana | Usunięte skojarzone interfejsy API |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | Datagridcell<br/>Datagridrow<br/>DataGridTableCollection (Gromadzenie danych)<br/>Datagridcolumncollection<br/>Datagridtablestyle<br/>Datagridcolumnstyle<br/>Styl DataGridLineStyle<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>Datagridboolcolumn<br/>Datagridtextbox<br/>Gridcolumnstylescollection<br/>Gridtablestylescollection<br/>Typ hitu |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | Przychylenia paska narzędzi |
| Toolbarbutton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>Uchwyt na toolbarbuttonclickeventhandler<br/>Styl paska narzędzi<br/>Narzędzie ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | Menuitemcollection |
| Mainmenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Zaleca się zaktualizowanie aplikacji do platformy .NET Core 3.1 i przejście do formantów zastępczych. Wymiana formantów jest prosty proces, zasadniczo "znajdź i zastąp" na typ.

## <a name="ccli"></a>C++/CLI

*Tylko Windows*

Dodano obsługę tworzenia projektów języka C++/CLI (znanych również jako "zarządzane c++"). Pliki binarne produkowane z tych projektów są zgodne z programem .NET Core 3.0 i nowszymi wersjami.

Aby dodać obsługę języka C++/CLI w programie Visual Studio 2019 w wersji 16.4, zainstaluj [program rozwoju pulpitu z obciążeniem C++.](/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads) To obciążenie dodaje dwa szablony do programu Visual Studio:

- Biblioteka klas CLR (core.NET)
- Pusty projekt CLR (core.NET)

## <a name="next-steps"></a>Następne kroki

- [Przejrzyj przełomowe zmiany między .NET Core 3.0 i 3.1.](../compatibility/3.0-3.1.md)
- [Przejrzyj przełomowe zmiany w aplikacjach .NET Core 3.1 dla formularzy systemu Windows.](../compatibility/winforms.md#net-core-31)
