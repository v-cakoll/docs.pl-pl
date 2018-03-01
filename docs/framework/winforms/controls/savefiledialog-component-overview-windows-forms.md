---
title: "SaveFileDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1505e2bc31afb4f44f0d635b06624528cb16ba15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="89343-102">SaveFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="89343-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="89343-103">Formularze systemu Windows <xref:System.Windows.Forms.SaveFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="89343-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="89343-104">Jest to standardowy **Zapisz plik** okno dialogowe używane przez system Windows.</span><span class="sxs-lookup"><span data-stu-id="89343-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="89343-105">Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="89343-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="89343-106">Praca ze składnikiem SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="89343-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="89343-107">Używać go jako proste rozwiązanie umożliwiający użytkownikom zapisywanie plików zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="89343-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="89343-108">Polegając na standardowe okno dialogowe systemu Windows, podstawowe funkcje tworzenia aplikacji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="89343-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="89343-109">Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnika, należy napisać logiki zapisywania plików.</span><span class="sxs-lookup"><span data-stu-id="89343-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="89343-110">Można użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="89343-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="89343-111">Plik można otworzyć w trybie odczytu/zapisu z użyciem <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="89343-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="89343-112">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="89343-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89343-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="89343-113">See Also</span></span>  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [<span data-ttu-id="89343-114">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="89343-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
