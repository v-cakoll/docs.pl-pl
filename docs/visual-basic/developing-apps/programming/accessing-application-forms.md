---
title: Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 85de915f4dc9a79e0161411951062afbeb764513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014469"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="c7212-102">Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7212-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="c7212-103">`My.Forms` Obiekt zapewnia łatwy sposób uzyskać dostęp do wystąpienia każdego formularza Windows zadeklarowane w projekcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7212-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="c7212-104">Można również użyć właściwości `My.Application` obiektu dostęp do ekranu powitalnego i formularza głównego aplikacji i Uzyskaj listę formularzy otwartych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7212-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="c7212-105">Zadania</span><span class="sxs-lookup"><span data-stu-id="c7212-105">Tasks</span></span>  
 <span data-ttu-id="c7212-106">W poniższej tabeli wymieniono przykłady pokazujące sposób dostępu do formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7212-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="c7212-107">Zadanie</span><span class="sxs-lookup"><span data-stu-id="c7212-107">To</span></span>|<span data-ttu-id="c7212-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="c7212-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="c7212-109">Dostęp do jednego formularza z innej formy w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7212-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="c7212-110">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="c7212-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="c7212-111">Wyświetla tytuły wszystkich aplikacji, otwartych formularzy.</span><span class="sxs-lookup"><span data-stu-id="c7212-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="c7212-112">Zaktualizuj ekran powitalny informacje o stanie uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c7212-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="c7212-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c7212-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="c7212-114">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="c7212-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
