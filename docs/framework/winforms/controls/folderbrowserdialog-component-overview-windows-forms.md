---
title: FolderBrowserDialog, składnik — Omówienie
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: 8b017ba08ae4205e930ac00177c89a89fde17d3b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745726"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)

Składnik <xref:System.Windows.Forms.FolderBrowserDialog> Windows Forms to modalne okno dialogowe, które służy do przeglądania i wybierania folderów. Nowe foldery można także tworzyć z poziomu składnika <xref:System.Windows.Forms.FolderBrowserDialog>.

> [!NOTE]
> Aby wybrać pliki zamiast folderów, użyj składnika [OpenFileDialog](openfiledialog-component-windows-forms.md) .

Składnik <xref:System.Windows.Forms.FolderBrowserDialog> jest wyświetlany w czasie wykonywania przy użyciu metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>. Ustaw właściwość <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, aby określić górny folder i wszystkie podfoldery, które będą wyświetlane w widoku drzewa okna dialogowego. Po wyświetleniu okna dialogowego można użyć właściwości <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>, aby uzyskać ścieżkę wybranego folderu.

Po dodaniu do formularza składnik <xref:System.Windows.Forms.FolderBrowserDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Instrukcje: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy Windows Forms](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog, składnik](folderbrowserdialog-component-windows-forms.md)
