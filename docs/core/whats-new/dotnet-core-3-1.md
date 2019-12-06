---
title: Co nowego w programie .NET Core 3,1
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,1.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 08ae824b79ba6a1ff5a92a0b4306eabe5ccadfd2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838324"
---
# <a name="whats-new-in-net-core-31"></a>Co nowego w programie .NET Core 3,1

W tym artykule opisano nowości w programie .NET Core 3,1. Ta wersja zawiera drobne ulepszenia programu .NET Core 3,0, skupiając się na małych, ale ważnych poprawkach. Najważniejszym elementem na platformie .NET Core 3,1 jest to, że jest to wersja [długoterminowa (LTS)](#long-term-support) .

Jeśli używasz programu Visual Studio 2019, musisz zaktualizować [program do programu Visual studio 2019 16,4](https://visualstudio.microsoft.com/downloads/) , aby współpracował z projektami .net Core 3,1. Aby uzyskać więcej informacji na temat Nowości w programie Visual Studio, zobacz [Blog programu Visual Studio](https://devblogs.microsoft.com/visualstudio/tis-the-season-visual-studio-2019/).

Visual Studio dla komputerów Mac obsługuje również program .NET Core 3,1 i zawiera go w kanale Visual Studio dla komputerów Mac 8,4 w wersji zapoznawczej. Aby korzystać z platformy .NET Core 3,1, należy wybrać kanał w wersji zapoznawczej.

Aby uzyskać więcej informacji o wersji, zobacz [anons programu .NET Core 3,1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).

- [Pobierz i Rozpocznij pracę z platformą .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1) w systemie Windows, MacOS lub Linux.

## <a name="long-term-support"></a>Długoterminowa pomoc techniczna

.NET Core 3,1 to wersja LTS z pomocą techniczną firmy Microsoft przez kolejne trzy lata. Zdecydowanie zalecamy, aby przenieść aplikacje do programu .NET Core 3,1. Bieżący cykl życia innych głównych wydań jest następujący:

| Wydanie | Uwaga |
| ------- | ---- |
| .NET Core 3.0 | Koniec okresu życia w dniu 3 marca 2020.     |
| .NET Core 2.2 | Koniec okresu istnienia 23 grudnia 2019. |
| .NET Core 2.1 | Koniec okresu istnienia 21 sierpnia 2021.    |

Aby uzyskać więcej informacji, zobacz [zasady obsługi .NET Core](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

## <a name="windows-forms"></a>Windows Forms

*Tylko Windows*

> [!WARNING]
> Istnieją istotne zmiany w Windows Forms.

Starsze formanty zostały uwzględnione w Windows Forms, które były niedostępne w przyborniku projektanta Visual Studio przez jakiś czas. Zostały one zastąpione nowymi kontrolkami z powrotem w .NET Framework 2,0. Zostały one usunięte z zestawu Desktop SDK dla platformy .NET Core 3,1.

| Usunięto kontrolkę | Zalecane zastąpienie | Usunięto skojarzone interfejsy API |
| --------------- | ----------------------- | ----------------------- |
| DataGrid        | <xref:System.Windows.Forms.DataGridView>      | DataGridCell<br/>DataGridRow<br/>DataGridTableCollection<br/>DataGridColumnCollection<br/>Element DataGridTableStyle<br/>DataGridColumnStyle<br/>Datasiatki<br/>DataGridParentRowsLabel<br/>DataGridParentRowsLabelStyle<br/>DataGridBoolColumn<br/>DataGridTextBox<br/>GridColumnStylesCollection<br/>GridTableStylesCollection<br/>HitTestType |
| ToolBar         | <xref:System.Windows.Forms.ToolStrip>         | ToolBarAppearance |
| ToolBarButton   | <xref:System.Windows.Forms.ToolStripButton>   | ToolBarButtonClickEventArgs<br/>ToolBarButtonClickEventHandler<br/>ToolBarButton<br/>ToolBarTextAlign |
| ContextMenu     | <xref:System.Windows.Forms.ContextMenuStrip>  |  |
| :::no-loc text="Menu"::: | <xref:System.Windows.Forms.ToolStripDropDown><br/><xref:System.Windows.Forms.ToolStripDropDownMenu> | MenuItemCollection |
| MainMenu        | <xref:System.Windows.Forms.MenuStrip>         |  |
| MenuItem        | <xref:System.Windows.Forms.ToolStripMenuItem> |  |

Zalecamy zaktualizowanie aplikacji do programu .NET Core 3,1 i przejście do kontrolek zastępczych. Zastępowanie formantów jest prostym procesem, zasadniczo "Znajdź i Zamień" w typie.

## <a name="ccli"></a>C++/CLI

*Tylko Windows*

Dodano obsługę tworzenia C++projektów/CLI (znanych również jako "zarządzane C++"). Pliki binarne wytworzone z tych projektów są zgodne z platformą .NET Core 3,0 i nowszymi wersjami.

Aby dodać obsługę C++/CLI w programie Visual Studio 2019 16,4, zainstaluj [Programowanie aplikacji klasycznych C++ za pomocą obciążenia](https://docs.microsoft.com/cpp/build/vscpp-step-0-installation?view=vs-2019#step-4---choose-workloads). To obciążenie dodaje dwa szablony do programu Visual Studio:

- Biblioteka klas CLR (.NET Core)
- Pusty projekt CLR (.NET Core)

## <a name="next-steps"></a>Następne kroki

- [Zapoznaj się z istotnymi zmianami między programem .NET Core 3,0 i 3,1.](../compatibility/3.0-3.1.md)
- [Zapoznaj się z istotnymi zmianami między .NET Framework i .NET Core 3,0 dla aplikacji Windows Forms.](../porting/winforms-breaking-changes.md)
