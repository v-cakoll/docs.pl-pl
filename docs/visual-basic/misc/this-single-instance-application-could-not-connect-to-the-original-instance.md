---
title: Ta aplikacja o pojedynczym wystąpieniu nie można połączyć z oryginalnego wystąpienia
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 7ffa9b185e16cfdf8223ce84e77d1a0e1fa67f65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942615"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="e318a-102">Ta aplikacja o pojedynczym wystąpieniu nie można połączyć z oryginalnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="e318a-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="e318a-103">Ta aplikacja o pojedynczym wystąpieniu nie może połączyć do oryginalnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e318a-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="e318a-104">Niektóre z możliwych przyczyn tego problemu są następujące:</span><span class="sxs-lookup"><span data-stu-id="e318a-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="e318a-105">Oryginalne wystąpienie przestał odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="e318a-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="e318a-106">Aplikacja nie ma uprawnień do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="e318a-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="e318a-107">Aby uzyskać więcej informacji na temat jądra obiektów, zobacz [muteksy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="e318a-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="e318a-108">Nazwa podstawowa dla obiektów jądra pochodzi z łączenia identyfikator GUID, główny numer wersji i pomocniczy numer wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="e318a-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="e318a-109">Na przykład może być nazwa podstawowa `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="e318a-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="e318a-110">Aby naprawić ten błąd, podczas opracowywania aplikacji</span><span class="sxs-lookup"><span data-stu-id="e318a-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="e318a-111">Upewnij się, że aplikacja nie przechodzi do stanu nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="e318a-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="e318a-112">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="e318a-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="e318a-113">Uruchom ponownie oryginalne wystąpienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e318a-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="e318a-114">Uruchom ponownie komputer, aby wyczyścić każdy proces, który może używać zasób, który jest wymagane do połączenia z oryginalnej aplikacji wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e318a-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="e318a-115">Należy pamiętać, okoliczności, w których wystąpił błąd i telefoniczna pomoc techniczna firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e318a-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e318a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e318a-116">See also</span></span>

- [<span data-ttu-id="e318a-117">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="e318a-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
