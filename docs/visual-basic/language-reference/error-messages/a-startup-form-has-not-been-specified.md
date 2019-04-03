---
title: Formularz początkowy nie został określony
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 9af95b397bef4a19654510619cf0864c8ab7b76f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58833571"
---
# <a name="a-startup-form-has-not-been-specified"></a><span data-ttu-id="9e99a-102">Formularz początkowy nie został określony</span><span class="sxs-lookup"><span data-stu-id="9e99a-102">A startup form has not been specified</span></span>
<span data-ttu-id="9e99a-103">Aplikacja używa <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> klasy, ale nie określa formularz początkowy.</span><span class="sxs-lookup"><span data-stu-id="9e99a-103">The application uses the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase> class but does not specify the startup form.</span></span>  
  
 <span data-ttu-id="9e99a-104">Taka sytuacja może wystąpić, jeśli **struktury aplikacji Włącz** zaznaczono pole wyboru w Projektancie projektu, ale **formularz początkowy** nie zostanie określony.</span><span class="sxs-lookup"><span data-stu-id="9e99a-104">This can occur if the **Enable application framework** check box is selected in the project designer but the **Startup form** is not specified.</span></span> <span data-ttu-id="9e99a-105">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9e99a-105">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9e99a-106">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="9e99a-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="9e99a-107">Określ obiekt początkowy dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e99a-107">Specify a startup object for the application.</span></span>  
  
     <span data-ttu-id="9e99a-108">Aby uzyskać więcej informacji, zobacz [strona aplikacji, Projektant projektu (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9e99a-108">For more information, see [Application Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).</span></span>  
  
2.  <span data-ttu-id="9e99a-109">Zastąp <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> metodę, aby ustawić <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> właściwość formularz początkowy.</span><span class="sxs-lookup"><span data-stu-id="9e99a-109">Override the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A> method to set the <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A> property to the startup form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e99a-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e99a-110">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [<span data-ttu-id="9e99a-111">Omówienie modelu aplikacji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e99a-111">Overview of the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
