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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349244"
---
# <a name="accessing-application-forms-visual-basic"></a><span data-ttu-id="d8d79-102">Uzyskiwanie dostępu do formularzy aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8d79-102">Accessing Application Forms (Visual Basic)</span></span>

<span data-ttu-id="d8d79-103">Obiekt `My.Forms` zapewnia łatwy sposób uzyskiwania dostępu do wystąpienia każdego formularza systemu Windows zadeklarowanego w projekcie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-103">The `My.Forms` object provides an easy way to access an instance of each Windows Form declared in the application's project.</span></span> <span data-ttu-id="d8d79-104">Możesz również użyć właściwości obiektu `My.Application`, aby uzyskać dostęp do ekranu powitalnego i formularza głównego aplikacji oraz uzyskać listę otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-104">You can also use properties of the `My.Application` object to access the application's splash screen and main form, and get a list of the application's open forms.</span></span>  
  
## <a name="tasks"></a><span data-ttu-id="d8d79-105">Zadania</span><span class="sxs-lookup"><span data-stu-id="d8d79-105">Tasks</span></span>  

 <span data-ttu-id="d8d79-106">W poniższej tabeli przedstawiono przykłady pokazujące, jak uzyskać dostęp do formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-106">The following table lists examples showing how to access an application's forms.</span></span>  
  
|<span data-ttu-id="d8d79-107">Do</span><span class="sxs-lookup"><span data-stu-id="d8d79-107">To</span></span>|<span data-ttu-id="d8d79-108">Zobacz</span><span class="sxs-lookup"><span data-stu-id="d8d79-108">See</span></span>|  
|---|---|  
|<span data-ttu-id="d8d79-109">Dostęp do jednego formularza z innego formularza w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-109">Access one form from another form in an application.</span></span>|[<span data-ttu-id="d8d79-110">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="d8d79-110">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)|  
|<span data-ttu-id="d8d79-111">Wyświetla tytuły wszystkich otwartych formularzy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-111">Display the titles of all the application's open forms.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>|  
|<span data-ttu-id="d8d79-112">Zaktualizuj ekran powitalny informacjami o stanie podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d8d79-112">Update the splash screen with status information as the application starts.</span></span>|<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>|  
  
## <a name="see-also"></a><span data-ttu-id="d8d79-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8d79-113">See also</span></span>

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.SplashScreen%2A>
- [<span data-ttu-id="d8d79-114">My.Forms, obiekt</span><span class="sxs-lookup"><span data-stu-id="d8d79-114">My.Forms Object</span></span>](../../../visual-basic/language-reference/objects/my-forms-object.md)
