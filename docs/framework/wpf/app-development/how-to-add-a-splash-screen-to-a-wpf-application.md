---
title: "Jak dodać ekran powitalny do aplikacji WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 121cbc1c07ea8f6458df81d861aea3f8e1f91086
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="f2401-102">Jak dodać ekran powitalny do aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="f2401-102">How to: Add a Splash Screen to a WPF Application</span></span>
<span data-ttu-id="f2401-103">W tym temacie przedstawiono sposób dodawania okno uruchamiania lub *ekranu powitalnego*, do aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="f2401-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="f2401-104">Aby dodać obraz istniejącego jako ekran powitalny</span><span class="sxs-lookup"><span data-stu-id="f2401-104">To add an existing image as a splash screen</span></span>  
  
1.  <span data-ttu-id="f2401-105">Utwórz lub znaleźć obrazu, który ma być używany dla ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="f2401-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="f2401-106">Można użyć dowolnego format obrazu, który jest obsługiwany przez Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="f2401-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="f2401-107">Na przykład można użyć formatu BMP, GIF, JPEG, PNG lub TIFF.</span><span class="sxs-lookup"><span data-stu-id="f2401-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>  
  
2.  <span data-ttu-id="f2401-108">Dodaj plik obrazu do projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="f2401-108">Add the image file to the WPF Application project.</span></span> <span data-ttu-id="f2401-109">Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="f2401-109">For more information, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
3.  <span data-ttu-id="f2401-110">W Eksploratorze rozwiązań wybierz obraz.</span><span class="sxs-lookup"><span data-stu-id="f2401-110">In Solution Explorer, select the image.</span></span>  
  
4.  <span data-ttu-id="f2401-111">W oknie właściwości, kliknij strzałkę listy rozwijanej dla **Akcja kompilacji** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f2401-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>  
  
5.  <span data-ttu-id="f2401-112">Wybierz **ekranu powitalnego** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="f2401-112">Select **SplashScreen** from the drop-down list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2401-113">Jeśli nie widzisz **ekranu powitalnego** opcji, należy sprawdzić, czy używasz [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] z dodatkiem SP1 lub nowszym.</span><span class="sxs-lookup"><span data-stu-id="f2401-113">If you do not see the **SplashScreen** option, be sure to check that you are using [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 or later.</span></span>  
  
6.  <span data-ttu-id="f2401-114">Naciśnij klawisz F5, aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="f2401-114">Press F5 to build and run the application.</span></span>  
  
     <span data-ttu-id="f2401-115">Obraz ekranu powitalnego zostanie wyświetlony w Centrum ekranu, a następnie stopniowo po wyświetleniu okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f2401-115">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="f2401-116">Aby usunąć ekranu powitalnego aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2401-116">To remove the splash screen from an application</span></span>  
  
1.  <span data-ttu-id="f2401-117">W Eksploratorze rozwiązań wybierz obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="f2401-117">In Solution Explorer, select the splash screen image.</span></span>  
  
2.  <span data-ttu-id="f2401-118">W oknie właściwości ustaw **Akcja kompilacji** do **Brak**.</span><span class="sxs-lookup"><span data-stu-id="f2401-118">In the Properties window, set the **Build Action** to **None**.</span></span>  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="f2401-119">Aby usunąć ekranu powitalnego aplikacji</span><span class="sxs-lookup"><span data-stu-id="f2401-119">To remove the splash screen from an application</span></span>  
  
-   <span data-ttu-id="f2401-120">W Eksploratorze rozwiązań Usuń obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="f2401-120">In Solution Explorer, delete the splash screen image.</span></span>  
  
-   <span data-ttu-id="f2401-121">Obraz ekranu powitalnego Wyklucz z projektu.</span><span class="sxs-lookup"><span data-stu-id="f2401-121">Exclude the splash screen image from the project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2401-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2401-122">See Also</span></span>  
 <xref:System.Windows.SplashScreen>  
 [<span data-ttu-id="f2401-123">NIB: porady: Dodawanie istniejących elementów do projektu</span><span class="sxs-lookup"><span data-stu-id="f2401-123">NIB:How to: Add Existing Items to a Project</span></span>](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
