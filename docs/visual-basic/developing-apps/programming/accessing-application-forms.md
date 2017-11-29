---
title: "Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1b029ce984f9cef540087181a83070b0c8aa8132
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="d76d5-102">Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d76d5-102">Accessing Application Forms (Visual Basic)</span></span>
<span data-ttu-id="d76d5-103">`My.Forms` Obiekt zapewnia prosty sposób uzyskać dostęp do wystąpienia każdego formularza systemu Windows zadeklarowany w projekcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d76d5-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="d76d5-104">Można również użyć właściwości `My.Application` obiekt dostępu do ekranu powitalnego i formularz główny aplikacji i pobranie listy otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d76d5-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d76d5-105">Zadania</span><span class="sxs-lookup"><span data-stu-id="d76d5-105">Tasks</span></span>  
 <span data-ttu-id="d76d5-106">W poniższej tabeli przedstawiono przykłady przedstawiająca sposób uzyskać dostępu do formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d76d5-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="d76d5-107">Do</span><span class="sxs-lookup"><span data-stu-id="d76d5-107">To</span></span>|<span data-ttu-id="d76d5-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="d76d5-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="d76d5-109">Dostęp do jednego formularza z innej formy w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d76d5-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="d76d5-110">My.Forms — obiekt</span><span class="sxs-lookup"><span data-stu-id="d76d5-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="d76d5-111">Wyświetla tytuły wszystkich aplikacji otwartych formularzy.</span><span class="sxs-lookup"><span data-stu-id="d76d5-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="d76d5-112">Ekran powitalny należy zaktualizować informacje o stanie po uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d76d5-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d76d5-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d76d5-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>  
 [<span data-ttu-id="d76d5-114">My.Forms — obiekt</span><span class="sxs-lookup"><span data-stu-id="d76d5-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
