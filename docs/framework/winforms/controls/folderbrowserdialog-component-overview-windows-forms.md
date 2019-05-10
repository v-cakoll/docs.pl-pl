---
title: FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210398"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)

Formularze Windows <xref:System.Windows.Forms.FolderBrowserDialog> składnik to modalne okno dialogowe służy do przeglądania i wybranie folderów. Można również tworzyć nowe foldery z poziomu <xref:System.Windows.Forms.FolderBrowserDialog> składnika.

> [!NOTE]
> Aby wybrać pliki, a nie foldery, użyj [OpenFileDialog](openfiledialog-component-windows-forms.md) składnika.

<xref:System.Windows.Forms.FolderBrowserDialog> Składników są wyświetlane w czasie wykonywania za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwości w celu określenia folderu najbardziej na wierzchu i wszelkich podfolderów, które będą wyświetlane w widoku drzewa okna dialogowego. Gdy okno dialogowe wykazało, możesz użyć <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwość, aby pobrać ścieżkę do folderu, który został wybrany.

Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.FolderBrowserDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Instrukcje: Wybierz foldery, za pomocą składnika FolderBrowserDialog formularzy Windows](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog, składnik](folderbrowserdialog-component-windows-forms.md)
