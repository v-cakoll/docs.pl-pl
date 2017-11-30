---
title: "To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="aef10-102">To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="aef10-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="aef10-103">To pojedyncze wystąpienie aplikacji nie może połączyć się z wystąpieniem oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="aef10-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="aef10-104">Niektóre możliwe przyczyny tego problemu są następujące:</span><span class="sxs-lookup"><span data-stu-id="aef10-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="aef10-105">Oryginalne wystąpienie przestał odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="aef10-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="aef10-106">Aplikacja nie ma uprawnień do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="aef10-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="aef10-107">Aby uzyskać więcej informacji o obiektach jądra, zobacz [muteksy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="aef10-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="aef10-108">Nazwę podstawową dla obiekt jądra pochodzi z łączenia GUID zestawu, numer wersji głównej i podrzędny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="aef10-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="aef10-109">Na przykład można podstawowej nazwy `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="aef10-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="aef10-110">Aby rozwiązać ten problem, podczas opracowywania aplikacji</span><span class="sxs-lookup"><span data-stu-id="aef10-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="aef10-111">Sprawdź, czy aplikacja nie przechodzi w stan, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="aef10-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="aef10-112">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="aef10-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="aef10-113">Ponowne uruchomienie oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aef10-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="aef10-114">Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobu, który jest wymagany do połączenia do oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="aef10-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="aef10-115">Zanotuj okoliczności, w których wystąpił błąd, a telefonu pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="aef10-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef10-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aef10-116">See Also</span></span>  
 [<span data-ttu-id="aef10-117">NIB: Porady: Określanie wystąpień zachowanie aplikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aef10-117">NIB: How to: Specify Instancing Behavior for an Application (Visual Basic)</span></span>](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [<span data-ttu-id="aef10-118">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="aef10-118">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  
 [<span data-ttu-id="aef10-119">Pomoc techniczna PAVEOVER i ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="aef10-119">PAVEOVER Product Support and Accessibility</span></span>](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
