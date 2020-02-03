---
title: Jak dodać ekran powitalny
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 39f53e21c40f036c65894b4f275cd5fb414999be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740452"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="516fc-102">Jak dodać ekran powitalny do aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="516fc-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="516fc-103">W tym temacie pokazano, jak dodać okno uruchamiania lub *ekran powitalny*do aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="516fc-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="516fc-104">Aby dodać istniejący obraz jako ekran powitalny</span><span class="sxs-lookup"><span data-stu-id="516fc-104">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="516fc-105">Utwórz lub Znajdź obraz, który ma być używany na potrzeby ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="516fc-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="516fc-106">Można użyć dowolnego formatu obrazu, który jest obsługiwany przez składnik Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="516fc-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="516fc-107">Można na przykład użyć formatu BMP, GIF, JPEG, PNG lub TIFF.</span><span class="sxs-lookup"><span data-stu-id="516fc-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="516fc-108">Dodaj plik obrazu do projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="516fc-108">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="516fc-109">W **Eksplorator rozwiązań**wybierz obraz.</span><span class="sxs-lookup"><span data-stu-id="516fc-109">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="516fc-110">W okno Właściwości kliknij strzałkę listy rozwijanej dla właściwości **Akcja kompilacji** .</span><span class="sxs-lookup"><span data-stu-id="516fc-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="516fc-111">Wybierz pozycję **SplashScreen** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="516fc-111">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="516fc-112">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="516fc-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="516fc-113">Obraz ekranu powitalnego pojawia się na środku ekranu, a następnie znika po wyświetleniu okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="516fc-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="516fc-114">Aby wykluczyć ekran powitalny z kompilacji</span><span class="sxs-lookup"><span data-stu-id="516fc-114">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="516fc-115">W **Eksplorator rozwiązań**wybierz obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="516fc-115">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="516fc-116">W oknie **Właściwości** Ustaw **akcję kompilacja** na **Brak**.</span><span class="sxs-lookup"><span data-stu-id="516fc-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="516fc-117">Aby usunąć ekran powitalny z aplikacji</span><span class="sxs-lookup"><span data-stu-id="516fc-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="516fc-118">W **Eksplorator rozwiązań**Usuń obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="516fc-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="516fc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="516fc-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="516fc-120">[Instrukcje: Dodawanie istniejących elementów do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="516fc-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
