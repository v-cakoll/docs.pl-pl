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
ms.openlocfilehash: eb40606f55785b4b6ec9271b55c8159a26822011
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581856"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="364a0-102">Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="364a0-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="364a0-103">`My.Forms` Obiekt zapewnia prosty sposób uzyskać dostęp do wystąpienia każdego formularza systemu Windows zadeklarowany w projekcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="364a0-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="364a0-104">Można również użyć właściwości `My.Application` obiekt dostępu do ekranu powitalnego i formularz główny aplikacji i pobranie listy otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="364a0-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="364a0-105">Zadania</span><span class="sxs-lookup"><span data-stu-id="364a0-105">Tasks</span></span>  
 <span data-ttu-id="364a0-106">W poniższej tabeli przedstawiono przykłady przedstawiająca sposób uzyskać dostępu do formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="364a0-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="364a0-107">Do</span><span class="sxs-lookup"><span data-stu-id="364a0-107">To</span></span>|<span data-ttu-id="364a0-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="364a0-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="364a0-109">Dostęp do jednego formularza z innej formy w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="364a0-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="364a0-110">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="364a0-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="364a0-111">Wyświetla tytuły wszystkich aplikacji otwartych formularzy.</span><span class="sxs-lookup"><span data-stu-id="364a0-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="364a0-112">Ekran powitalny należy zaktualizować informacje o stanie po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="364a0-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="364a0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="364a0-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>  
 [<span data-ttu-id="364a0-114">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="364a0-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
