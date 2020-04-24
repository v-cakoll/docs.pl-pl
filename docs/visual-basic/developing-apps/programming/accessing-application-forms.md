---
title: Uzyskiwanie dostępu do formularzy aplikacji
ms.date: 07/20/2015
helpviewer_keywords:
- forms [Visual Basic], communicating between
- application forms [Visual Basic], accessing
- forms [Visual Basic], accessing one from another
- My.Forms object
- forms [Visual Basic], accessing all open
ms.assetid: 9aaf5aaf-2012-4f97-89c7-6e62b9d17863
ms.openlocfilehash: 332b6a7563160528b6c17210170af0db6e9bc0e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74349244"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="773d7-102">Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="773d7-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="773d7-103">`My.Forms` Obiekt zapewnia łatwy sposób uzyskiwania dostępu do wystąpienia każdego formularza systemu Windows zadeklarowanego w projekcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="773d7-104">Możesz również użyć właściwości `My.Application` obiektu, aby uzyskać dostęp do ekranu powitalnego i formularza głównego aplikacji oraz uzyskać listę otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="773d7-105">Zadania</span><span class="sxs-lookup"><span data-stu-id="773d7-105">Tasks</span></span>  

 <span data-ttu-id="773d7-106">W poniższej tabeli przedstawiono przykłady pokazujące, jak uzyskać dostęp do formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="773d7-107">Do</span><span class="sxs-lookup"><span data-stu-id="773d7-107">To</span></span>|<span data-ttu-id="773d7-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="773d7-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="773d7-109">Dostęp do jednego formularza z innego formularza w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="773d7-110">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="773d7-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="773d7-111">Wyświetla tytuły wszystkich otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="773d7-112">Zaktualizuj ekran powitalny informacjami o stanie podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="773d7-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="773d7-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="773d7-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="773d7-114">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="773d7-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
