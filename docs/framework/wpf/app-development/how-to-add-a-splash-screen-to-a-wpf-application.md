---
title: 'Instrukcje: Dodawanie ekranu powitalnego do aplikacji WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59307505"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="5eff8-102">Instrukcje: Dodawanie ekranu powitalnego do aplikacji WPF</span><span class="sxs-lookup"><span data-stu-id="5eff8-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="5eff8-103">W tym temacie przedstawiono sposób dodawania oknem uruchamiania lub *ekran powitalny*, do aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5eff8-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="5eff8-104">Aby dodać istniejący obraz jako ekran powitalny</span><span class="sxs-lookup"><span data-stu-id="5eff8-104">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="5eff8-105">Utwórz lub Znajdź obraz, który chcesz użyć dla ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="5eff8-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="5eff8-106">Możesz użyć dowolnego format obrazu, który jest obsługiwany przez Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="5eff8-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="5eff8-107">Na przykład można użyć formatu BMP, GIF, JPEG, PNG lub TIFF.</span><span class="sxs-lookup"><span data-stu-id="5eff8-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="5eff8-108">Dodaj plik obrazu do projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="5eff8-108">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="5eff8-109">W **Eksploratora rozwiązań**, wybierz obraz.</span><span class="sxs-lookup"><span data-stu-id="5eff8-109">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="5eff8-110">W oknie dialogowym właściwości kliknij strzałkę listy rozwijanej dla **Build Action** właściwości.</span><span class="sxs-lookup"><span data-stu-id="5eff8-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="5eff8-111">Wybierz **ekranu powitalnego** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="5eff8-111">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="5eff8-112">Naciśnij klawisz **F5** Aby skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="5eff8-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="5eff8-113">Obraz ekranu powitalnego pojawia się w środku ekranu, a następnie stopniowo zmienia się po wyświetleniu okna głównego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5eff8-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="5eff8-114">Aby wykluczyć ekran powitalny z kompilacji</span><span class="sxs-lookup"><span data-stu-id="5eff8-114">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="5eff8-115">W **Eksploratora rozwiązań**, wybierz obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="5eff8-115">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="5eff8-116">W **właściwości** oknie **Build Action** do **Brak**.</span><span class="sxs-lookup"><span data-stu-id="5eff8-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="5eff8-117">Aby usunąć ekran powitalny aplikacji</span><span class="sxs-lookup"><span data-stu-id="5eff8-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="5eff8-118">W **Eksploratora rozwiązań**, Usuń obraz ekranu powitalnego.</span><span class="sxs-lookup"><span data-stu-id="5eff8-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="5eff8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5eff8-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="5eff8-120">[Instrukcje: Dodaj istniejące elementy do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5eff8-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
