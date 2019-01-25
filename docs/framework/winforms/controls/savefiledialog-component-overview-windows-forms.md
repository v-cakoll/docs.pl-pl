---
title: SaveFileDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: ab8eb5409d017c6ea73a44e4e57ccec9cece4824
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631064"
---
# <a name="savefiledialog-component-overview-windows-forms"></a><span data-ttu-id="a135f-102">SaveFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a135f-102">SaveFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a135f-103">Formularze Windows <xref:System.Windows.Forms.SaveFileDialog> składnik to wstępnie skonfigurowane okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a135f-103">The Windows Forms <xref:System.Windows.Forms.SaveFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="a135f-104">Jest taka sama jak standardowy **Zapisz plik** okno dialogowe używane przez Windows.</span><span class="sxs-lookup"><span data-stu-id="a135f-104">It is the same as the standard **Save File** dialog box used by Windows.</span></span> <span data-ttu-id="a135f-105">Dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="a135f-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="working-with-the-savefiledialog-component"></a><span data-ttu-id="a135f-106">Praca ze składnikiem SaveFileDialog</span><span class="sxs-lookup"><span data-stu-id="a135f-106">Working with the SaveFileDialog Component</span></span>  
 <span data-ttu-id="a135f-107">Używać go jako proste rozwiązanie umożliwiające użytkownikom zapisywanie plików, zamiast konfigurować własne okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="a135f-107">Use it as a simple solution for enabling users to save files instead of configuring your own dialog box.</span></span> <span data-ttu-id="a135f-108">Opierając się na standardowych okien dialogowych Windows, natychmiast dobrze znanym użytkownikom jest podstawową funkcjonalność aplikacji, które tworzysz.</span><span class="sxs-lookup"><span data-stu-id="a135f-108">By relying on standard Windows dialog boxes, the basic functionality of applications you create is immediately familiar to users.</span></span> <span data-ttu-id="a135f-109">Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.SaveFileDialog> składnik, należy napisać własną logiką zapisywania pliku.</span><span class="sxs-lookup"><span data-stu-id="a135f-109">Be aware, however, that when using the <xref:System.Windows.Forms.SaveFileDialog> component, you must write your own file-saving logic.</span></span>  
  
 <span data-ttu-id="a135f-110">Możesz użyć <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a135f-110">You can use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog box at run time.</span></span> <span data-ttu-id="a135f-111">Możesz otworzyć plik w trybie odczytu i zapisu za pomocą <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a135f-111">You can open a file in read/write mode using the <xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A> method.</span></span>  
  
 <span data-ttu-id="a135f-112">Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.SaveFileDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="a135f-112">When it is added to a form, the <xref:System.Windows.Forms.SaveFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a135f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a135f-113">See also</span></span>
- <xref:System.Windows.Forms.SaveFileDialog>
- [<span data-ttu-id="a135f-114">SaveFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="a135f-114">SaveFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
