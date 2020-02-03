---
title: SaveFileDialog — Informacje o składniku
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: 7609c29b7e932ecee7dc8a289617094bd8d480e2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743100"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="8b684-102">SaveFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="8b684-102">SaveFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="8b684-103">Składnik <xref:System.Windows.Forms.SaveFileDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym.</span><span class="sxs-lookup"><span data-stu-id="8b684-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="8b684-104">Jest to takie samo, jak okno dialogowe **plik zapisywania** standardowego używany przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="8b684-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="8b684-105">Dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="8b684-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="8b684-106">Praca ze składnikiem SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="8b684-106">Working with the SaveFileDialog Component</span></span>

<span data-ttu-id="8b684-107">Użyj jej jako prostego rozwiązania umożliwiającego użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="8b684-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="8b684-108">Opierając się na standardowych oknach dialogowych systemu Windows, podstawowe funkcje aplikacji tworzonych przez Ciebie są od razu znane użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="8b684-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="8b684-109">Należy jednak pamiętać, że w przypadku korzystania ze składnika <xref:System.Windows.Forms.SaveFileDialog> należy napisać własną logikę zapisywania plików.</span><span class="sxs-lookup"><span data-stu-id="8b684-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>

<span data-ttu-id="8b684-110">Możesz użyć metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8b684-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="8b684-111">Plik można otworzyć w trybie odczytu/zapisu przy użyciu metody <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>.</span><span class="sxs-lookup"><span data-stu-id="8b684-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>

<span data-ttu-id="8b684-112">Po dodaniu do formularza składnik <xref:System.Windows.Forms.SaveFileDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b684-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b684-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b684-113">See also</span></span>

- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="8b684-114">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="8b684-114">SaveFileDialog Component</span></span>](savefiledialog-component-windows-forms.md)
