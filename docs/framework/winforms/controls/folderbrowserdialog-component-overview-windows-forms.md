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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074134"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="e4939-102">FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="e4939-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="e4939-103">Formularze Windows <xref:System.Windows.Forms.FolderBrowserDialog> składnik to modalne okno dialogowe służy do przeglądania i wybranie folderów.</span><span class="sxs-lookup"><span data-stu-id="e4939-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="e4939-104">Można również tworzyć nowe foldery z poziomu <xref:System.Windows.Forms.FolderBrowserDialog> składnika.</span><span class="sxs-lookup"><span data-stu-id="e4939-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e4939-105">Aby wybrać pliki, a nie foldery, użyj [OpenFileDialog](openfiledialog-component-windows-forms.md) składnika.</span><span class="sxs-lookup"><span data-stu-id="e4939-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>  
  
 <span data-ttu-id="e4939-106"><xref:System.Windows.Forms.FolderBrowserDialog> Składników są wyświetlane w czasie wykonywania za pomocą <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e4939-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="e4939-107">Ustaw <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> właściwości w celu określenia folderu najbardziej na wierzchu i wszelkich podfolderów, które będą wyświetlane w widoku drzewa okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="e4939-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="e4939-108">Gdy okno dialogowe wykazało, możesz użyć <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> właściwość, aby pobrać ścieżkę do folderu, który został wybrany.</span><span class="sxs-lookup"><span data-stu-id="e4939-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>  
  
 <span data-ttu-id="e4939-109">Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.FolderBrowserDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e4939-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4939-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4939-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="e4939-111">Instrukcje: Wybierz foldery, za pomocą składnika FolderBrowserDialog formularzy Windows</span><span class="sxs-lookup"><span data-stu-id="e4939-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="e4939-112">FolderBrowserDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="e4939-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
