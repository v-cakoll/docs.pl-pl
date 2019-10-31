---
title: Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
ms.openlocfilehash: 9643d14b3e94e814c492b362b9db3e37cff4ce9f
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197372"
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a><span data-ttu-id="d5947-102">Wystąpił nieoczekiwany błąd, ponieważ zasób systemu operacyjnego zażądany dla uruchomienia pojedynczego wystąpienia nie może zostać pobrany</span><span class="sxs-lookup"><span data-stu-id="d5947-102">An unexpected error has occurred because an operating system resource required for single instance startup cannot be acquired</span></span>
<span data-ttu-id="d5947-103">Aplikacja nie może uzyskać wymaganego zasobu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d5947-103">The application could not acquire a necessary operating system resource.</span></span> <span data-ttu-id="d5947-104">Oto niektóre z możliwych przyczyn tego problemu:</span><span class="sxs-lookup"><span data-stu-id="d5947-104">Some of the possible causes for this problem are:</span></span>  
  
- <span data-ttu-id="d5947-105">Aplikacja nie ma uprawnień do tworzenia nazwanych obiektów systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d5947-105">The application does not have permissions to create named operating-system objects.</span></span>  
  
- <span data-ttu-id="d5947-106">Środowisko uruchomieniowe języka wspólnego nie ma uprawnień do tworzenia plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="d5947-106">The common language runtime does not have permissions to create memory-mapped files.</span></span>  
  
- <span data-ttu-id="d5947-107">Aplikacja musi uzyskać dostęp do obiektu systemu operacyjnego, ale jest on używany przez inny proces.</span><span class="sxs-lookup"><span data-stu-id="d5947-107">The application needs to access an operating-system object, but another process is using it.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d5947-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d5947-108">To correct this error</span></span>  
  
1. <span data-ttu-id="d5947-109">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia nazwanych obiektów systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d5947-109">Check that the application has sufficient permissions to create named operating-system objects.</span></span>  
  
2. <span data-ttu-id="d5947-110">Sprawdź, czy środowisko uruchomieniowe języka wspólnego ma wystarczające uprawnienia do tworzenia plików mapowanych na pamięć.</span><span class="sxs-lookup"><span data-stu-id="d5947-110">Check that the common language runtime has sufficient permissions to create memory-mapped files.</span></span>  
  
3. <span data-ttu-id="d5947-111">Uruchom ponownie komputer, aby wyczyścić każdy proces, który może korzystać z zasobu potrzebnego do nawiązania połączenia z aplikacją oryginalnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d5947-111">Restart the computer to clear any process that may be using the resource needed to connect to the original instance application.</span></span>  
  
4. <span data-ttu-id="d5947-112">Zanotuj sytuacje, w których wystąpił błąd i Wywołaj usługi pomocy technicznej firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="d5947-112">Note the circumstances under which the error occurred, and call Microsoft Product Support Services</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5947-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5947-113">See also</span></span>

- [<span data-ttu-id="d5947-114">Strona aplikacji, Projektant projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5947-114">Application Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [<span data-ttu-id="d5947-115">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="d5947-115">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
- [<span data-ttu-id="d5947-116">Porozmawiaj z nami</span><span class="sxs-lookup"><span data-stu-id="d5947-116">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
