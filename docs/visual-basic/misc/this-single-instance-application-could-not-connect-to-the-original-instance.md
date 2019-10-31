---
title: Ta aplikacja z jednym wystąpieniem nie może nawiązać połączenia z oryginalnym wystąpieniem
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 04ceec4839d07ba959c39af8c4f582c7abfe7d6b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198130"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a><span data-ttu-id="3af6a-102">Ta aplikacja z jednym wystąpieniem nie może nawiązać połączenia z oryginalnym wystąpieniem</span><span class="sxs-lookup"><span data-stu-id="3af6a-102">This single-instance application could not connect to the original instance</span></span>
<span data-ttu-id="3af6a-103">Ta aplikacja pojedynczego wystąpienia nie może nawiązać połączenia z oryginalnym wystąpieniem.</span><span class="sxs-lookup"><span data-stu-id="3af6a-103">This single-instance application could not connect to the original instance.</span></span> <span data-ttu-id="3af6a-104">Poniżej przedstawiono niektóre możliwe przyczyny tego problemu:</span><span class="sxs-lookup"><span data-stu-id="3af6a-104">Some of the possible causes for this problem are as follows:</span></span>  
  
- <span data-ttu-id="3af6a-105">Oryginalne wystąpienie przestało odpowiadać.</span><span class="sxs-lookup"><span data-stu-id="3af6a-105">The original instance stopped responding.</span></span>  
  
- <span data-ttu-id="3af6a-106">Aplikacja nie ma uprawnień do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="3af6a-106">The application does not have permissions to create kernel objects.</span></span> <span data-ttu-id="3af6a-107">Aby uzyskać więcej informacji na temat obiektów jądra, zobacz [muteksy](../../standard/threading/mutexes.md).</span><span class="sxs-lookup"><span data-stu-id="3af6a-107">For more information about kernel objects, see [Mutexes](../../standard/threading/mutexes.md).</span></span>  
  
     <span data-ttu-id="3af6a-108">Nazwa podstawowa obiektów jądra pochodzi z łączenia identyfikatora GUID zestawu, głównego numeru wersji i pomocniczego numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="3af6a-108">The base name for the kernel objects comes from concatenating the assembly's GUID, major version number, and minor version number.</span></span> <span data-ttu-id="3af6a-109">Na przykład nazwa podstawowa może być `3639f15d-9547-43da-8145-60da347829915.1`.</span><span class="sxs-lookup"><span data-stu-id="3af6a-109">For example, the base name could be `3639f15d-9547-43da-8145-60da347829915.1`.</span></span>  
  
## <a name="to-correct-this-error-when-developing-the-application"></a><span data-ttu-id="3af6a-110">Aby poprawić ten błąd podczas tworzenia aplikacji</span><span class="sxs-lookup"><span data-stu-id="3af6a-110">To correct this error when developing the application</span></span>  
  
1. <span data-ttu-id="3af6a-111">Sprawdź, czy aplikacja nie przechodzi w stan braku odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3af6a-111">Check that the application does not go into an unresponsive state.</span></span>  
  
2. <span data-ttu-id="3af6a-112">Sprawdź, czy aplikacja ma wystarczające uprawnienia do tworzenia obiektów jądra.</span><span class="sxs-lookup"><span data-stu-id="3af6a-112">Check that the application has sufficient permissions to create kernel objects.</span></span>  
  
3. <span data-ttu-id="3af6a-113">Uruchom ponownie oryginalne wystąpienie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3af6a-113">Restart the original instance of the application.</span></span>  
  
4. <span data-ttu-id="3af6a-114">Uruchom ponownie komputer, aby wyczyścić każdy proces, który może korzystać z zasobu, który jest wymagany do nawiązania połączenia z aplikacją oryginalnego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="3af6a-114">Restart the computer to clear any process that may be using the resource that is required to connect to the original instance application.</span></span>  
  
5. <span data-ttu-id="3af6a-115">Zanotuj sytuacje, w których wystąpił błąd, i telefoniczne usługi pomocy technicznej firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3af6a-115">Note the circumstances under which the error occurred, and telephone Microsoft Product Support Services.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3af6a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3af6a-116">See also</span></span>

- [<span data-ttu-id="3af6a-117">Podstawowe informacje o debugerze</span><span class="sxs-lookup"><span data-stu-id="3af6a-117">Debugger Basics</span></span>](/visualstudio/debugger/debugger-feature-tour)
