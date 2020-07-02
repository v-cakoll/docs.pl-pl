---
title: Jak dodać ekran powitalny
description: Dowiedz się, jak dodać okno uruchamiania lub ekran powitalny do aplikacji Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617963"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="a0b74-103">Jak dodać ekran powitalny do aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="a0b74-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="a0b74-104">W tym temacie pokazano, jak dodać okno uruchamiania lub *ekran powitalny*do aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="a0b74-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="a0b74-105">Aby dodać istniejący obraz jako ekran powitalny</span><span class="sxs-lookup"><span data-stu-id="a0b74-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="a0b74-106">Utwórz lub Znajdź obraz, który ma być używany na potrzeby ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="a0b74-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="a0b74-107">Można użyć dowolnego formatu obrazu, który jest obsługiwany przez składnik Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="a0b74-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="a0b74-108">Można na przykład użyć formatu BMP, GIF, JPEG, PNG lub TIFF.</span><span class="sxs-lookup"><span data-stu-id="a0b74-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="a0b74-109">Dodaj plik obrazu do projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="a0b74-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="a0b74-110">W **Eksplorator rozwiązań**wybierz obraz.</span><span class="sxs-lookup"><span data-stu-id="a0b74-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="a0b74-111">W okno Właściwości kliknij strzałkę listy rozwijanej dla właściwości **Akcja kompilacji** .</span><span class="sxs-lookup"><span data-stu-id="a0b74-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="a0b74-112">Wybierz pozycję **SplashScreen** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="a0b74-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="a0b74-113">Naciśnij klawisz **F5** , aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="a0b74-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="a0b74-114">Obraz ekranu powitalnego pojawia się na środku ekranu, a następnie znika po wyświetleniu okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a0b74-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="a0b74-115">Aby wykluczyć ekran powitalny z kompilacji</span><span class="sxs-lookup"><span data-stu-id="a0b74-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="a0b74-116">W **Eksplorator rozwiązań**wybierz obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="a0b74-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="a0b74-117">W oknie **Właściwości** Ustaw **akcję kompilacja** na **Brak**.</span><span class="sxs-lookup"><span data-stu-id="a0b74-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="a0b74-118">Aby usunąć ekran powitalny z aplikacji</span><span class="sxs-lookup"><span data-stu-id="a0b74-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="a0b74-119">W **Eksplorator rozwiązań**Usuń obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="a0b74-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0b74-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0b74-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="a0b74-121">[Instrukcje: Dodawanie istniejących elementów do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a0b74-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
