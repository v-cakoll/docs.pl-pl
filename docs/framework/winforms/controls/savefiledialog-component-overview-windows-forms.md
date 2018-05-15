---
title: SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="b9e70-102">SaveFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="b9e70-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="b9e70-103">Formularze systemu Windows <xref:System.Windows.Forms.SaveFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="b9e70-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="b9e70-104">Jest to standardowy **Zapisz plik** okno dialogowe używane przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e70-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="b9e70-105">Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="b9e70-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="b9e70-106">Praca ze składnikiem SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="b9e70-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="b9e70-107">Używać go jako proste rozwiązanie umożliwiający użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="b9e70-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="b9e70-108">Polegając na standardowe okno dialogowe systemu Windows, podstawowe funkcje tworzenia aplikacji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="b9e70-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="b9e70-109">Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnika, należy napisać logiki zapisywania plików.</span><span class="sxs-lookup"><span data-stu-id="b9e70-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="b9e70-110">Można użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b9e70-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="b9e70-111">Plik można otworzyć w trybie odczytu/zapisu z użyciem <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b9e70-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="b9e70-112">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b9e70-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e70-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9e70-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="b9e70-114">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="b9e70-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
