---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 8130eee93ab5c14043283c28f522da53f9047e85
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64646890"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="11154-102">Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany</span><span class="sxs-lookup"><span data-stu-id="11154-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="11154-103">Aplikacja nie można uzyskać zasobu systemu operacyjnego wymagane.</span><span class="sxs-lookup"><span data-stu-id="11154-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="11154-104">Możliwe przyczyny tego problemu, należą:</span><span class="sxs-lookup"><span data-stu-id="11154-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="11154-105">Aplikacja nie ma uprawnień do utworzenia nazwane obiekty systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="11154-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="11154-106">Środowisko uruchomieniowe języka wspólnego nie ma uprawnień, aby utworzyć pliki mapowane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="11154-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="11154-107">Aplikacja potrzebuje dostępu do obiektu systemu operacyjnego, ale jest używany przez inny proces.</span><span class="sxs-lookup"><span data-stu-id="11154-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="11154-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="11154-108">To correct this error</span></span>  
  
1. <span data-ttu-id="11154-109">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów usługi o nazwie system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="11154-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="11154-110">Sprawdź, czy środowisko uruchomieniowe języka wspólnego, ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="11154-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="11154-111">Uruchom ponownie komputer, aby wyczyścić każdy proces, który może używać zasobów wymaganych do połączenia do oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="11154-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="11154-112">Należy pamiętać, okoliczności, w których wystąpił błąd i wywołać pomoc techniczna firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="11154-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11154-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="11154-113">See also</span></span>

- [<span data-ttu-id="11154-114">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11154-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="11154-115">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="11154-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="11154-116">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="11154-116">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
