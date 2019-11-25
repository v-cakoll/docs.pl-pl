---
title: Formularz początkowy nie został określony
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 301f249e6222c929d2c513964ecbb21df5fbc47f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976190"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="6601d-102">Formularz początkowy nie został określony</span><span class="sxs-lookup"><span data-stu-id="6601d-102">A startup form has not been specified</span></span>

<span data-ttu-id="6601d-103">Aplikacja używa klasy <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>, ale nie określa formularza startowego.</span><span class="sxs-lookup"><span data-stu-id="6601d-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="6601d-104">Taka sytuacja może wystąpić, jeśli pole wyboru **Włącz platformę aplikacji** jest zaznaczone w projektancie projektu, ale **formularz uruchamiania** nie został określony.</span><span class="sxs-lookup"><span data-stu-id="6601d-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="6601d-105">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6601d-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6601d-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6601d-106">To correct this error</span></span>  
  
1. <span data-ttu-id="6601d-107">Określ obiekt uruchamiania dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6601d-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="6601d-108">Aby uzyskać więcej informacji, zobacz [Strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="6601d-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2. <span data-ttu-id="6601d-109">Zastąp metodę <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>, aby ustawić właściwość <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> na formularz startowy.</span><span class="sxs-lookup"><span data-stu-id="6601d-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6601d-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6601d-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="6601d-111">Omówienie modelu aplikacji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6601d-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
