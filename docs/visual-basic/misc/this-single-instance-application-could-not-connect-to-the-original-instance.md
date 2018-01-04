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
ms.openlocfilehash: 9cb8cef696ba93f922dfe0d92195a5fb5147b4cc
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="b74ab-102">To pojedyncze wystąpienie aplikacji nie można połączyć z oryginalnego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="b74ab-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="b74ab-103">To pojedyncze wystąpienie aplikacji nie może połączyć się z wystąpieniem oryginalnym.</span><span class="sxs-lookup"><span data-stu-id="b74ab-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="b74ab-104">Niektóre możliwe przyczyny tego problemu są następujące:</span><span class="sxs-lookup"><span data-stu-id="b74ab-104">Some of the possible causes for this problem are as follows:</span></span>  
  
-   <span data-ttu-id="b74ab-105">Oryginalne wystąpienie przestał odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="b74ab-105">The original instance stopped responding.</span></span>  
  
-   <span data-ttu-id="b74ab-106">Aplikacja nie ma uprawnień do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="b74ab-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="b74ab-107">Aby uzyskać więcej informacji o obiektach jądra, zobacz [muteksy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="b74ab-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="b74ab-108">Nazwę podstawową dla obiekt jądra pochodzi z łączenia GUID zestawu, numer wersji głównej i podrzędny numer wersji.</span><span class="sxs-lookup"><span data-stu-id="b74ab-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="b74ab-109">Na przykład można podstawowej nazwy `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="b74ab-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="b74ab-110">Aby rozwiązać ten problem, podczas opracowywania aplikacji</span><span class="sxs-lookup"><span data-stu-id="b74ab-110">To correct this error when developing the application</span></span>  
  
1.  <span data-ttu-id="b74ab-111">Sprawdź, czy aplikacja nie przechodzi w stan, który nie odpowiada.</span><span class="sxs-lookup"><span data-stu-id="b74ab-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2.  <span data-ttu-id="b74ab-112">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="b74ab-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3.  <span data-ttu-id="b74ab-113">Ponowne uruchomienie oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b74ab-113">Restart the original instance of the application.</span></span>  
  
4.  <span data-ttu-id="b74ab-114">Uruchom ponownie komputer, aby wyczyścić żaden proces, który używa zasobu, który jest wymagany do połączenia do oryginalnego wystąpienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b74ab-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5.  <span data-ttu-id="b74ab-115">Zanotuj okoliczności, w których wystąpił błąd, a telefonu pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b74ab-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b74ab-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b74ab-116">See Also</span></span>  
 [<span data-ttu-id="b74ab-117">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="b74ab-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)  

