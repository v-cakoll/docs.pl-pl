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
ms.openlocfilehash: aae18167b29c71ad692cc6ba447457cd079374b4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074134"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)
Formularze Windows <xref:System.Windows.Forms.FolderBrowserDialog> składnik to modalne okno dialogowe służy do przeglądania i wybranie folderów. Można również tworzyć nowe foldery z poziomu <xref:System.Windows.Forms.FolderBrowserDialog> składnika.  
  
> [!NOTE]
>  Aby wybrać pliki, a nie foldery, użyj [OpenFileDialog](openfiledialog-component-windows-forms.md) składnika.  
  
 <xref:System.Windows.Forms.FolderBrowserDialog> Składników są wyświetlane w czasie wykonywania za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody. Ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwości w celu określenia folderu najbardziej na wierzchu i wszelkich podfolderów, które będą wyświetlane w widoku drzewa okna dialogowego. Gdy okno dialogowe wykazało, możesz użyć <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwość, aby pobrać ścieżkę do folderu, który został wybrany.  
  
 Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.FolderBrowserDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Instrukcje: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy systemu Windows](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [FolderBrowserDialog, składnik](folderbrowserdialog-component-windows-forms.md)
