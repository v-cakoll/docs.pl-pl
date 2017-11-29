---
title: "Wskazówki: Hosting zegara WPF w Win32"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55e5aa633e3d788ac8acaa09684c92b8608e7cfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="4aa1e-102">Wskazówki: Hosting zegara WPF w Win32</span><span class="sxs-lookup"><span data-stu-id="4aa1e-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="4aa1e-103">Aby umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, użyj <xref:System.Windows.Interop.HwndSource>, zapewniające HWND, który zawiera Twoje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="4aa1e-104">Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, nadanie mu podobna do właściwości CreateWindow parametrów.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="4aa1e-105">Następnie można sprawdzić <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości, która ma w nim.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="4aa1e-106">Ponadto możesz uzyskać HWND z <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="4aa1e-107">W tym przewodniku ilustruje sposób tworzenia mieszane [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji, która reimplements systemu operacyjnego **właściwości daty i godziny** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4aa1e-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="4aa1e-108">Prerequisites</span></span>  
 <span data-ttu-id="4aa1e-109">Zobacz [WPF i współdziałanie Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="4aa1e-109">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="4aa1e-110">Jak używać tego samouczka</span><span class="sxs-lookup"><span data-stu-id="4aa1e-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="4aa1e-111">Ten samouczek koncentruje się na ważnych czynności produkcji współdziałanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="4aa1e-112">Samouczek nie jest obsługiwana przez próbki [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051), ale ten przykład jest odbicia produktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="4aa1e-113">W tym samouczku dokumentów kroki tak, jakby były uruchamianie z istniejącym [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu własny, być może istniejącego projektu, a dodawania hostowany [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="4aa1e-114">Możesz porównać produktu zakończenia z [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="4aa1e-114">You can compare your end product with [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="4aa1e-115">Przewodnik Windows Presentation Framework wewnątrz Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="4aa1e-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="4aa1e-116">Na poniższym rysunku przedstawiono danego produktu zakończenia tego samouczka:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="4aa1e-117">![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="4aa1e-117">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="4aa1e-118">Utwórz ponownie tego okna dialogowego przez utworzenie C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]i przy użyciu edytora okien dialogowych, aby utworzyć następujące:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="4aa1e-119">![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="4aa1e-119">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="4aa1e-120">(Nie trzeba używać [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] do używania <xref:System.Windows.Interop.HwndSource>, i nie trzeba użyć C++, aby zapisać [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy, ale jest dość typowy sposób przeprowadzenia i pozwala również na stopniowym wyjaśnienie samouczka).</span><span class="sxs-lookup"><span data-stu-id="4aa1e-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="4aa1e-121">Należy wykonać pięć podetapów konkretnego celu umieść [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara w oknie dialogowym:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="4aa1e-122">Włącz Twojej [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu do wywoływania z kodu zarządzanego (**/CLR**), zmieniając ustawienia projektu w [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4aa1e-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="4aa1e-123">Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> w oddzielnych bibliotekach DLL.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="4aa1e-124">Powiązanie tej [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wewnątrz <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="4aa1e-125">Pobierz HWND tego <xref:System.Windows.Controls.Page> przy użyciu <xref:System.Windows.Interop.HwndSource.Handle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="4aa1e-126">Użyj [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] decyzji o tym, gdzie umieścić HWND w większy [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikacji</span><span class="sxs-lookup"><span data-stu-id="4aa1e-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="4aa1e-127">/ CLR</span><span class="sxs-lookup"><span data-stu-id="4aa1e-127">/clr</span></span>  
 <span data-ttu-id="4aa1e-128">Pierwszym krokiem jest włączenie tej niezarządzanych [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt na taki, który można wywołać kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="4aa1e-129">Użyj opcji kompilatora/CLR, która połączy niezbędne chcesz używać i Dostosuj metody Main do użycia z bibliotek DLL [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4aa1e-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="4aa1e-130">Aby włączyć korzystanie z kodu zarządzanego wewnątrz projektu C++: kliknij prawym przyciskiem myszy na win32clock projektu i wybierz **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="4aa1e-131">Na **ogólne** strony właściwości (ustawienie domyślne), zmienić obsługi plików wykonywalnych języka aby `/clr`.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="4aa1e-132">Następnie dodaj odwołania do bibliotek DLL niezbędne do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: plików PresentationCore.dll, PresentationFramework.dll System.dll, WindowsBase.dll, UIAutomationProvider.dll i UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="4aa1e-133">(Instrukcjami przyjęto założenie, że system operacyjny jest instalowany na dysku C:.)</span><span class="sxs-lookup"><span data-stu-id="4aa1e-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="4aa1e-134">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** i w tym oknie dialogowym:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="4aa1e-135">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** .</span><span class="sxs-lookup"><span data-stu-id="4aa1e-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="4aa1e-136">Kliknij przycisk **Dodaj nowe odwołanie**, kliknij kartę przeglądania, wprowadź C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, a następnie kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="4aa1e-137">Powtórz tę procedurę dla PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="4aa1e-138">Powtórz tę procedurę dla WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="4aa1e-139">Powtórz tę procedurę dla UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="4aa1e-140">Powtórz tę procedurę dla UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="4aa1e-141">Kliknij przycisk **Dodaj nowe odwołanie**, wybierz System.dll i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="4aa1e-142">Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="4aa1e-143">Na koniec należy dodać `STAThreadAttribute` do `_tWinMain` metoda do użycia z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="4aa1e-144">Ten atrybut informuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] który podczas inicjuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], należy użyć modelu komórek wielowątkowych pojedynczego (STA), który jest konieczny do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="4aa1e-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="4aa1e-145">Utwórz stronę Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="4aa1e-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="4aa1e-146">Następnie Utwórz bibliotekę DLL, która definiuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="4aa1e-147">Często jest najłatwiejsza do utworzenia [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako aplikacja autonomiczna i zapisu i debugowania [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] części w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="4aa1e-148">Po zakończeniu tego projektu mogą być uwzględniane biblioteki DLL przez kliknięcie prawym przyciskiem myszy projekt, klikając **właściwości**, przechodząc do aplikacji i zmiana typu danych wyjściowych biblioteki klas systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="4aa1e-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Projektu biblioteki dll można połączyć z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (rozwiązania, które zawiera dwa projekty) — kliknij prawym przyciskiem myszy rozwiązanie, wybierz opcję **projektu Add\Existing**.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="4aa1e-150">Można użyć tego [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] biblioteki dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt, musisz dodać odwołanie:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="4aa1e-151">Kliknij prawym przyciskiem myszy projekt win32clock i wybierz **odwołania...** .</span><span class="sxs-lookup"><span data-stu-id="4aa1e-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="4aa1e-152">Kliknij przycisk **Dodaj nowe odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="4aa1e-153">Kliknij przycisk **projekty** kartę.  Wybierz WPFClock, kliknij przycisk OK.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="4aa1e-154">Kliknij przycisk **OK** aby zakończyć dodawanie odwołań do strony właściwości win32clock.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="4aa1e-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="4aa1e-155">HwndSource</span></span>  
 <span data-ttu-id="4aa1e-156">Następnie użyj <xref:System.Windows.Interop.HwndSource> aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> wyglądać HWND.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="4aa1e-157">Możesz dodać ten blok kodu do pliku C++:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-157">You add this block of code to a C++ file:</span></span>  
  
```  
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
  
 <span data-ttu-id="4aa1e-158">Jest to długo fragment kodu używanego wyjaśnień.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="4aa1e-159">Pierwsza część jest różnych klauzule, dzięki czemu nie trzeba do pełnej kwalifikacji wszystkie wywołania:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="4aa1e-160">Definiuje funkcję, która tworzy [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości naraża <xref:System.Windows.Interop.HwndSource> wokół i zwraca HWND:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="4aa1e-161">Najpierw należy utworzyć <xref:System.Windows.Interop.HwndSource>, którego parametry są podobne do właściwości CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 <span data-ttu-id="4aa1e-162">Następnie możesz utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawartości przez wywołanie jego konstruktora klasy:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="4aa1e-163">Następnie połącz stronę, aby <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="4aa1e-164">I w ostatnim wierszu zwracać HWND dla <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="4aa1e-165">Pozycjonowanie Hwnd</span><span class="sxs-lookup"><span data-stu-id="4aa1e-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="4aa1e-166">Teraz, gdy masz HWND, który zawiera [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, musisz umieścić tego HWND wewnątrz [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="4aa1e-167">Jeśli wiedział właśnie, gdzie umieścić HWND możesz po prostu przejdzie tego rozmiar i położenie do `GetHwnd` funkcji zdefiniowanej w wcześniej.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="4aa1e-168">Ale użyć pliku zasobu do definiowania okna dialogowego, tak, aby dokładnie się, gdzie umieszczane są żadnego z parametrów hWnd.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="4aa1e-169">Można użyć [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] Edytor okien dialogowych, aby umieścić [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC kontrolować miejscu zegara, aby przejść ("Insert zegara tutaj") i użyj jej położenie [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="4aa1e-170">W przypadku, gdy obsługa WM_INITDIALOG, użyj `GetDlgItem` można pobrać HWND symbolu zastępczego STATYCZNĄ:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="4aa1e-171">Można obliczyć, rozmiar i położenie tego symbolu statyczna, więc można umieścić [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara w tym miejscu:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="4aa1e-172">Prostokąt RECT;</span><span class="sxs-lookup"><span data-stu-id="4aa1e-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="4aa1e-173">Następnie można ukryć symbol zastępczy STATYCZNĄ:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="4aa1e-174">I Utwórz [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara HWND w tej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="4aa1e-175">Aby interesujące samouczka i do tworzenia rzeczywistych [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara, musisz utworzyć [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegara formantu w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="4aa1e-176">To przede wszystkim w znaczniku, należy się z kilku obsługi zdarzeń w CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="4aa1e-177">Ponieważ w tym samouczku jest dotyczące współdziałanie i nie projektu kontroli, uzupełnianie kodu dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zegar jest dostarczany jako blok kodu bez odrębny instrukcje dotyczące jego budowania lub oznacza każdej części.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="4aa1e-178">Możesz eksperymentować ten kod, aby zmienić wygląd i działanie lub funkcji formantu.</span><span class="sxs-lookup"><span data-stu-id="4aa1e-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="4aa1e-179">Oto kod znaczników:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="4aa1e-180">A Oto towarzyszący kodem:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="4aa1e-181">Wynik końcowy wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="4aa1e-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="4aa1e-182">![Okno dialogowe Właściwości daty i godziny](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="4aa1e-182">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="4aa1e-183">Aby porównać wyników zakończenia kod wytworzonego tego zrzutu ekranu, zobacz [przykład współdziałanie zegara Win32](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="4aa1e-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4aa1e-184">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4aa1e-184">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="4aa1e-185">WPF i współdziałanie Win32</span><span class="sxs-lookup"><span data-stu-id="4aa1e-185">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [<span data-ttu-id="4aa1e-186">Przykład współdziałanie zegara Win32</span><span class="sxs-lookup"><span data-stu-id="4aa1e-186">Win32 Clock Interoperation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160051)
