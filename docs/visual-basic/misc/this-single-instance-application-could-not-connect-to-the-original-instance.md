---
title: To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 9bc1f33231cc4f29fabd100a695843beb334aeaa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="ec970-102">To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ec970-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="ec970-103">To pojedyncze wystąpienie aplikacji nie może połączyć się z wystąpieniem oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="ec970-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="ec970-104">Niektóre możliwe przyczyny tego problemu są następujące:</span><span class="sxs-lookup"><span data-stu-id="ec970-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="ec970-105">Oryginalne wystąpienie przestał odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="ec970-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="ec970-106">Aplikacja nie ma uprawnień do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="ec970-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="ec970-107">Aby uzyskać więcej informacji o obiektach jądra, zobacz [muteksy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="ec970-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="ec970-108">Nazwę podstawową dla obiekt jądra pochodzi z łączenia GUID zestawu, numer wersji głównej i podrzędny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="ec970-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="ec970-109">Na przykład można podstawowej nazwy `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="ec970-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="ec970-110">Aby rozwiązać ten problem, podczas opracowywania aplikacji</span><span class="sxs-lookup"><span data-stu-id="ec970-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="ec970-111">Sprawdź, czy aplikacja nie przechodzi w stan, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="ec970-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="ec970-112">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="ec970-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="ec970-113">Ponowne uruchomienie oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec970-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="ec970-114">Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobu, który jest wymagany do połączenia do oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ec970-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="ec970-115">Zanotuj okoliczności, w których wystąpił błąd, a telefonu pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ec970-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec970-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec970-116">See Also</span></span>  
 [<span data-ttu-id="ec970-117">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="ec970-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  

