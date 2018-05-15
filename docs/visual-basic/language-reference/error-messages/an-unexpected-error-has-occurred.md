---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 313128d5511ddd0f3b75c58e2c10a74eb967d130
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="b4aec-102">Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany</span><span class="sxs-lookup"><span data-stu-id="b4aec-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="b4aec-103">Aplikacji nie można uzyskać zasobu niezbędne systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4aec-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="b4aec-104">Niektóre możliwe przyczyny tego problemu są:</span><span class="sxs-lookup"><span data-stu-id="b4aec-104">Some of the possible causes for this problem are:</span></span>  
  
-   <span data-ttu-id="b4aec-105">Aplikacja nie ma uprawnień do tworzenia nazwanych obiektów systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4aec-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
-   <span data-ttu-id="b4aec-106">Środowisko uruchomieniowe języka wspólnego nie ma uprawnień do tworzenia plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="b4aec-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
-   <span data-ttu-id="b4aec-107">Aplikacja potrzebuje dostępu do obiektu systemu operacyjnego, ale używa on innego procesu.</span><span class="sxs-lookup"><span data-stu-id="b4aec-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b4aec-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="b4aec-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="b4aec-109">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia nazwanych obiektów systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="b4aec-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2.  <span data-ttu-id="b4aec-110">Sprawdź, czy środowisko uruchomieniowe języka wspólnego ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="b4aec-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3.  <span data-ttu-id="b4aec-111">Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobów wymaganych do połączenia do oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b4aec-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4.  <span data-ttu-id="b4aec-112">Zanotuj okoliczności, w których wystąpił błąd, a następnie wywołać pomocy technicznej firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="b4aec-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4aec-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4aec-113">See Also</span></span>  
 [<span data-ttu-id="b4aec-114">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4aec-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [<span data-ttu-id="b4aec-115">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="b4aec-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="b4aec-116">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="b4aec-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
