---
title: 'Przewodnik: hostowanie zegara WPF w Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 98e48060bbb82764e1e541797c666ca33f247c39
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400474"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="d47c2-102">Przewodnik: hostowanie zegara WPF w Win32</span><span class="sxs-lookup"><span data-stu-id="d47c2-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>

<span data-ttu-id="d47c2-103">Aby umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, należy <xref:System.Windows.Interop.HwndSource>użyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , która zapewnia Właściwość HWND, która zawiera zawartość.</span><span class="sxs-lookup"><span data-stu-id="d47c2-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="d47c2-104">Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, podając parametry IT podobne do okna.</span><span class="sxs-lookup"><span data-stu-id="d47c2-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="d47c2-105">Następnie poinformuj <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o zawartości, którą chcesz umieścić w niej.</span><span class="sxs-lookup"><span data-stu-id="d47c2-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="d47c2-106">Na koniec można uzyskać wartość HWND z <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="d47c2-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="d47c2-107">W tym instruktażu przedstawiono sposób tworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mieszanej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] wewnątrz aplikacji, która ponownie implementuje okno dialogowe **Właściwości daty i godziny** systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="d47c2-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d47c2-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d47c2-108">Prerequisites</span></span>

<span data-ttu-id="d47c2-109">Zobacz [WPF i Win32](wpf-and-win32-interoperation.md)— współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="d47c2-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="d47c2-110">Jak korzystać z tego samouczka</span><span class="sxs-lookup"><span data-stu-id="d47c2-110">How to Use This Tutorial</span></span>

<span data-ttu-id="d47c2-111">Ten samouczek koncentruje się na ważnych krokach tworzenia aplikacji międzyoperacyjnej.</span><span class="sxs-lookup"><span data-stu-id="d47c2-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="d47c2-112">Ten samouczek jest obsługiwany przez przykładową próbkę Międzyoperacyjną z [zegarem Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale ten przykład stanowi odbicie produktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="d47c2-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="d47c2-113">W tym samouczku przedstawiono kroki, tak jak w przypadku rozpoczęcia pracy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z istniejącym projektem, prawdopodobnie istniejącym projektem i dodaniem hostowanych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d47c2-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="d47c2-114">Możesz porównać produkt końcowy z próbką [międzyoperacyjną zegara Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="d47c2-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="d47c2-115">Przewodnik dotyczący struktury prezentacji systemu Windows w systemie Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="d47c2-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="d47c2-116">Na poniższej ilustracji przedstawiono zamierzony produkt końcowy tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="d47c2-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Zrzut ekranu przedstawiający okno dialogowe Właściwości daty i godziny.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="d47c2-118">To okno dialogowe można utworzyć ponownie, tworząc projekt C++ Win32 w programie Visual Studio i używając edytora okien dialogowych, aby utworzyć następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="d47c2-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Okno dialogowe Właściwości daty i godziny ponownego utworzenia](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="d47c2-120">( [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] Nie musisz <xref:System.Windows.Interop.HwndSource>używać programu, aby korzystać z programu, a nie musisz używać C++ do pisania [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programów, ale jest to dość typowy sposób na to, i dowiesz się, jak najlepiej wykonać krokowe wyjaśnienie samouczka).</span><span class="sxs-lookup"><span data-stu-id="d47c2-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="d47c2-121">Aby włączyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar do okna dialogowego, należy wykonać pięć konkretnych podkroków:</span><span class="sxs-lookup"><span data-stu-id="d47c2-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="d47c2-122">Zezwól, aby [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] projektmógłwywołaćkodzarządzany(/CLR)przezzmianęustawieńprojektu[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w.</span><span class="sxs-lookup"><span data-stu-id="d47c2-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>

2. <span data-ttu-id="d47c2-123">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Utwórzwoddzielnym<xref:System.Windows.Controls.Page> pliku dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="d47c2-124">Umieść ten [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> element<xref:System.Windows.Interop.HwndSource>wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="d47c2-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="d47c2-125">Pobierz <xref:System.Windows.Interop.HwndSource.Handle%2A> Właściwość HWND dla tego <xref:System.Windows.Controls.Page> elementu przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="d47c2-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="d47c2-126">Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] , aby zdecydować, gdzie umieścić Właściwość HWND w większej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji</span><span class="sxs-lookup"><span data-stu-id="d47c2-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>

## <a name="clr"></a><span data-ttu-id="d47c2-127">/CLR</span><span class="sxs-lookup"><span data-stu-id="d47c2-127">/clr</span></span>

<span data-ttu-id="d47c2-128">Pierwszym krokiem jest przekształcenie tego niezarządzanego [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu w taki, który może wywołać kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="d47c2-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span> <span data-ttu-id="d47c2-129">Używasz opcji kompilatora/CLR, która będzie łączyć się z niezbędnymi bibliotekami DLL, których chcesz użyć, i Dostosuj metodę Main do użycia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]z.</span><span class="sxs-lookup"><span data-stu-id="d47c2-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="d47c2-130">Aby umożliwić korzystanie z kodu zarządzanego w C++ projekcie: Kliknij prawym przyciskiem myszy projekt win32clock i wybierz polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d47c2-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="d47c2-131">Na stronie właściwości **Ogólne** (domyślnie) Zmień obsługę środowiska uruchomieniowego języka wspólnego na `/clr`.</span><span class="sxs-lookup"><span data-stu-id="d47c2-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="d47c2-132">Następnie Dodaj odwołania do bibliotek DLL niezbędnych dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: 'Presentationcore. dll, platformie docelowej. dll, system. dll, 'Windowsbase. dll, UIAutomationProvider. dll i UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="d47c2-133">(W poniższych instrukcjach przyjęto założenie, że system operacyjny jest zainstalowany na dysku C: dysk).</span><span class="sxs-lookup"><span data-stu-id="d47c2-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="d47c2-134">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** i wewnątrz tego okna dialogowego:</span><span class="sxs-lookup"><span data-stu-id="d47c2-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="d47c2-135">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .</span><span class="sxs-lookup"><span data-stu-id="d47c2-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="d47c2-136">Kliknij przycisk **Dodaj nowe odwołanie**, kliknij przycisk Przeglądaj kartę, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="d47c2-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="d47c2-137">Powtórz dla platformie docelowej. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="d47c2-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="d47c2-139">Powtórz dla UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="d47c2-140">Powtórz dla UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="d47c2-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="d47c2-141">Kliknij pozycję **Dodaj nowe odwołanie**, wybierz pozycję System. dll, a następnie kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="d47c2-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="d47c2-142">Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="d47c2-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="d47c2-143">`STAThreadAttribute` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]Na koniec Dodaj do `_tWinMain` metody do użycia z:</span><span class="sxs-lookup"><span data-stu-id="d47c2-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="d47c2-144">Ten atrybut zawiera informacje o środowisku uruchomieniowym języka wspólnego (CLR), [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)]który podczas jego inicjowania powinien używać jednowątkowego modelu Apartment (STA), który jest niezbędny [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i).</span><span class="sxs-lookup"><span data-stu-id="d47c2-144">This attribute tells the common language runtime (CLR) that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="d47c2-145">Tworzenie strony struktury prezentacji systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d47c2-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="d47c2-146">Następnie utworzysz bibliotekę DLL, która definiuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Page></span><span class="sxs-lookup"><span data-stu-id="d47c2-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="d47c2-147">Często najłatwiej jest utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> aplikację jako autonomiczną i napisać i debugować tę [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] część.</span><span class="sxs-lookup"><span data-stu-id="d47c2-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="d47c2-148">Po wykonaniu tych czynności projekt można przekształcić w bibliotekę DLL, klikając prawym przyciskiem myszy projekt, klikając polecenie **Właściwości**, przechodząc do aplikacji i zmieniając typ danych wyjściowych na bibliotekę klas systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d47c2-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="d47c2-149">Projekt DLL można następnie połączyć [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z projektem (jedno rozwiązanie, które zawiera dwa projekty) — kliknij prawym przyciskiem myszy rozwiązanie, a następnie wybierz pozycję **projekt Add\Existing**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d47c2-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="d47c2-150">Aby użyć tej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biblioteki DLL [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] z projektu, należy dodać odwołanie:</span><span class="sxs-lookup"><span data-stu-id="d47c2-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>

1. <span data-ttu-id="d47c2-151">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz pozycję **odwołania...** .</span><span class="sxs-lookup"><span data-stu-id="d47c2-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="d47c2-152">Kliknij przycisk **Dodaj nowe odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d47c2-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="d47c2-153">Kliknij kartę **projekty** . Wybierz pozycję WPFClock, a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="d47c2-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="d47c2-154">Kliknij przycisk **OK** , aby zamknąć strony właściwości win32clock na potrzeby dodawania odwołań.</span><span class="sxs-lookup"><span data-stu-id="d47c2-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="d47c2-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="d47c2-155">HwndSource</span></span>

<span data-ttu-id="d47c2-156">Następnie użyj <xref:System.Windows.Interop.HwndSource> , aby <xref:System.Windows.Controls.Page> wyglądać podobnie do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementu HWND.</span><span class="sxs-lookup"><span data-stu-id="d47c2-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="d47c2-157">Ten blok kodu zostanie dodany do C++ pliku:</span><span class="sxs-lookup"><span data-stu-id="d47c2-157">You add this block of code to a C++ file:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 <span data-ttu-id="d47c2-158">Jest to długi fragment kodu, który może korzystać z pewnych wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="d47c2-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="d47c2-159">Pierwsza część to różne klauzule, dzięki czemu nie trzeba w pełni kwalifikować wszystkich wywołań:</span><span class="sxs-lookup"><span data-stu-id="d47c2-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="d47c2-160">Następnie zdefiniujesz funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartość, <xref:System.Windows.Interop.HwndSource> umieści ją wokół niej i zwraca wartość HWND:</span><span class="sxs-lookup"><span data-stu-id="d47c2-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="d47c2-161">Najpierw należy utworzyć obiekt <xref:System.Windows.Interop.HwndSource>, którego parametry są podobne do okna:</span><span class="sxs-lookup"><span data-stu-id="d47c2-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

<span data-ttu-id="d47c2-162">Następnie utworzysz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klasę zawartości, wywołując jej Konstruktor:</span><span class="sxs-lookup"><span data-stu-id="d47c2-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="d47c2-163">Następnie nawiążesz połączenie ze stroną <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="d47c2-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="d47c2-164">I w ostatnim wierszu Zwróć wartość HWND dla <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="d47c2-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="d47c2-165">Pozycjonowanie parametru HWND</span><span class="sxs-lookup"><span data-stu-id="d47c2-165">Positioning the Hwnd</span></span>

<span data-ttu-id="d47c2-166">Teraz, gdy masz już Właściwość HWND, która [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera zegar, musisz umieścić ten HWND [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="d47c2-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span> <span data-ttu-id="d47c2-167">Jeśli wiesz tylko, gdzie umieścić Właściwość HWND, wystarczy przekazać ten rozmiar i lokalizację do `GetHwnd` zdefiniowanej wcześniej funkcji.</span><span class="sxs-lookup"><span data-stu-id="d47c2-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="d47c2-168">Jednak w celu zdefiniowania okna dialogowego użyto pliku zasobów, dlatego nie należy dokładnie sprawdzić, gdzie są umieszczone dowolne z tych elementów.</span><span class="sxs-lookup"><span data-stu-id="d47c2-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="d47c2-169">Możesz użyć [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] edytora okien dialogowych, aby [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] umieścić formant statyczny w miejscu, w którym ma się znajdować zegar ("Wstaw zegar tutaj") i [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] użyć, aby ustawić zegar.</span><span class="sxs-lookup"><span data-stu-id="d47c2-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="d47c2-170">Gdy obsłużysz WM_INITDIALOG, możesz `GetDlgItem` pobrać właściwość HWND dla symbolu zastępczego static:</span><span class="sxs-lookup"><span data-stu-id="d47c2-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="d47c2-171">Następnie można obliczyć rozmiar i położenie tego symbolu zastępczego statycznie, aby można było umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="d47c2-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="d47c2-172">Prostokąt;</span><span class="sxs-lookup"><span data-stu-id="d47c2-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="d47c2-173">Następnie Ukryj symbol zastępczy STATIC:</span><span class="sxs-lookup"><span data-stu-id="d47c2-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="d47c2-174">I Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] w tej lokalizacji Właściwość HWND zegara:</span><span class="sxs-lookup"><span data-stu-id="d47c2-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="d47c2-175">Aby zapewnić ciekawy samouczek i utworzyć rzeczywisty [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar, należy w tym momencie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utworzyć kontrolkę zegar.</span><span class="sxs-lookup"><span data-stu-id="d47c2-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="d47c2-176">Można to zrobić głównie w znaczniku, z zaledwie kilkoma programami obsługi zdarzeń w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d47c2-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="d47c2-177">Ponieważ ten samouczek dotyczy operacji międzyoperacyjnych, a nie informacje o projekcie kontroli, pełny [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kod zegara jest dostarczany w tym miejscu jako blok kodu, bez odrębnych instrukcji dotyczących tworzenia go lub co oznacza każda część.</span><span class="sxs-lookup"><span data-stu-id="d47c2-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="d47c2-178">Możesz poeksperymentować z tym kodem, aby zmienić wygląd i działanie lub funkcjonalność formantu.</span><span class="sxs-lookup"><span data-stu-id="d47c2-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="d47c2-179">Oto znacznik:</span><span class="sxs-lookup"><span data-stu-id="d47c2-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="d47c2-180">A oto towarzyszący kod w tle:</span><span class="sxs-lookup"><span data-stu-id="d47c2-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="d47c2-181">Końcowy wynik wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="d47c2-181">The final result looks like:</span></span>

![Okno dialogowe Właściwości daty i godziny końcowego wyniku](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="d47c2-183">Aby porównać wynik końcowy z kodem, który wygenerował ten zrzut ekranu, zobacz przykład międzyoperacyjna w systemie [Win32](https://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="d47c2-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://go.microsoft.com/fwlink/?LinkID=160051).</span></span>

## <a name="see-also"></a><span data-ttu-id="d47c2-184">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d47c2-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="d47c2-185">WPF i Win32 — współdziałanie</span><span class="sxs-lookup"><span data-stu-id="d47c2-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="d47c2-186">Przykład międzyoperacyjności zegara Win32</span><span class="sxs-lookup"><span data-stu-id="d47c2-186">Win32 Clock Interoperation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160051)
