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
# <a name="folderbrowserdialog-component-overview-windows-forms"></a><span data-ttu-id="9356b-102">FolderBrowserDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="9356b-102">FolderBrowserDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="9356b-103">Składnik <xref:System.Windows.Forms.FolderBrowserDialog> Windows Forms to modalne okno dialogowe, które służy do przeglądania i wybierania folderów.</span><span class="sxs-lookup"><span data-stu-id="9356b-103">The Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> component is a modal dialog box that is used for browsing and selecting folders.</span></span> <span data-ttu-id="9356b-104">Nowe foldery można także tworzyć z poziomu składnika <xref:System.Windows.Forms.FolderBrowserDialog>.</span><span class="sxs-lookup"><span data-stu-id="9356b-104">New folders can also be created from within the <xref:System.Windows.Forms.FolderBrowserDialog> component.</span></span>

> [!NOTE]
> <span data-ttu-id="9356b-105">Aby wybrać pliki zamiast folderów, użyj składnika [OpenFileDialog](openfiledialog-component-windows-forms.md) .</span><span class="sxs-lookup"><span data-stu-id="9356b-105">To select files, instead of folders, use the [OpenFileDialog](openfiledialog-component-windows-forms.md) component.</span></span>

<span data-ttu-id="9356b-106">Składnik <xref:System.Windows.Forms.FolderBrowserDialog> jest wyświetlany w czasie wykonywania przy użyciu metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="9356b-106">The <xref:System.Windows.Forms.FolderBrowserDialog> component is displayed at run time using the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method.</span></span> <span data-ttu-id="9356b-107">Ustaw właściwość <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A>, aby określić górny folder i wszystkie podfoldery, które będą wyświetlane w widoku drzewa okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="9356b-107">Set the <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> property to determine the top-most folder and any subfolders that will appear within the tree view of the dialog box.</span></span> <span data-ttu-id="9356b-108">Po wyświetleniu okna dialogowego można użyć właściwości <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A>, aby uzyskać ścieżkę wybranego folderu.</span><span class="sxs-lookup"><span data-stu-id="9356b-108">Once the dialog box has been shown, you can use the <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> property to get the path of the folder that was selected.</span></span>

<span data-ttu-id="9356b-109">Po dodaniu do formularza składnik <xref:System.Windows.Forms.FolderBrowserDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9356b-109">When it is added to a form, the <xref:System.Windows.Forms.FolderBrowserDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="9356b-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9356b-110">See also</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [<span data-ttu-id="9356b-111">Instrukcje: wybieranie folderów za pomocą składnika FolderBrowserDialog formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9356b-111">How to: Choose Folders with the Windows Forms FolderBrowserDialog Component</span></span>](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [<span data-ttu-id="9356b-112">FolderBrowserDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="9356b-112">FolderBrowserDialog Component</span></span>](folderbrowserdialog-component-windows-forms.md)
