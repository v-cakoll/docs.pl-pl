---
title: Wyłącz rozpoznawanie DPI w programie Visual Studio
description: W tym artykule omówiono ograniczenia Windows Forms Designer na monitorach HDPI oraz sposobu uruchamiania programu Visual Studio jako proces świadomości DPI.
ms.date: 04/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.custom: seoapril2019
ms.openlocfilehash: e52debea382033417afe0bd47f899af1666192bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181386"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="9ccfc-103">Wyłącz rozpoznawanie DPI w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9ccfc-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="9ccfc-104">Program Visual Studio jest kropki na aplikację świadomą CAL (DPI), co oznacza automatycznie skaluje ekran.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="9ccfc-105">Jeśli aplikacja stwierdzający, że nie jest obsługującą ustawienia DPI, systemu operacyjnego można skalować aplikację jako mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="9ccfc-106">To zachowanie jest również nazywany wirtualizacji DPI.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="9ccfc-107">Aplikacji nadal sądzą, że działa on w 100%, skalowanie lub rozdzielczości 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

<span data-ttu-id="9ccfc-108">W tym artykule omówiono ograniczenia Windows Forms Designer na monitorach HDPI oraz sposobu uruchamiania programu Visual Studio jako proces świadomości DPI.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-108">This article discusses the limitations of Windows Forms Designer on HDPI monitors and how to run Visual Studio as a DPI-unaware process.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="9ccfc-109">Windows Forms Designer na monitorach HDPI</span><span class="sxs-lookup"><span data-stu-id="9ccfc-109">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="9ccfc-110">**Windows Forms Designer** w programie Visual Studio nie ma skalowanie pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-110">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="9ccfc-111">Powoduje to, że problemy z wyświetlaniem otwieraniu niektórych formularzy w **Windows Forms Designer** na dużej liczbie punktów na cal (HDPI) monitorów.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-111">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="9ccfc-112">Aby uzyskać przykłady formanty może okazać się nakładają się, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="9ccfc-112">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Windows Forms Designer w monitorze HDPI](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="9ccfc-114">Po otwarciu formularza w **Windows Forms Designer** w programie Visual Studio na monitorze HDPI programu Visual Studio Wyświetla żółty informacyjny paska w górnej części projektanta:</span><span class="sxs-lookup"><span data-stu-id="9ccfc-114">When you open a form in the **Windows Forms Designer** in Visual Studio on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![Pasek informacyjny w programie Visual Studio, aby ponownie uruchomić w trybie świadomości DPI](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="9ccfc-116">Odczytuje komunikat **skalowanie na ekranie głównym jest ustawiona na 200% (192 dpi). Może to spowodować problemy z renderowaniem w oknie projektanta.**</span><span class="sxs-lookup"><span data-stu-id="9ccfc-116">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

> [!NOTE]
> <span data-ttu-id="9ccfc-117">Ten pasek informacyjny została wprowadzona w Visual Studio 2017 w wersji 15.8.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-117">This informational bar was introduced in Visual Studio 2017 version 15.8.</span></span>

<span data-ttu-id="9ccfc-118">Jeśli nie działają w projektancie, a nie trzeba dostosować układ formularza, można zignorować pasek informacyjny i kontynuować pracę w edytorze kodu lub w innych typach projektantów.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-118">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="9ccfc-119">(Możesz również [wyłączyć powiadomienia](#disable-notifications) tak, aby pasek informacyjny nie w dalszym ciągu są wyświetlane.) Tylko **Windows Forms Designer** dotyczy problem.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-119">(You can also [disable notifications](#disable-notifications) so that the informational bar doesn't continue to appear.) Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="9ccfc-120">Jeśli musisz pracować w **Windows Forms Designer**, następna sekcja pomoże Ci [stwierdzenie](#to-resolve-the-display-problem).</span><span class="sxs-lookup"><span data-stu-id="9ccfc-120">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-display-problem).</span></span>

## <a name="to-resolve-the-display-problem"></a><span data-ttu-id="9ccfc-121">Aby rozwiązać problem z wyświetlaniem</span><span class="sxs-lookup"><span data-stu-id="9ccfc-121">To resolve the display problem</span></span>

<span data-ttu-id="9ccfc-122">Istnieją trzy opcje, aby rozwiązać problem z wyświetlaniem:</span><span class="sxs-lookup"><span data-stu-id="9ccfc-122">There are three options to resolve the display problem:</span></span>

1. [<span data-ttu-id="9ccfc-123">Uruchom program Visual Studio jako proces świadomości DPI</span><span class="sxs-lookup"><span data-stu-id="9ccfc-123">Restart Visual Studio as a DPI-unaware process</span></span>](#restart-visual-studio-as-a-dpi-unaware-process)
2. [<span data-ttu-id="9ccfc-124">Należy dodać wpis rejestru</span><span class="sxs-lookup"><span data-stu-id="9ccfc-124">Add a registry entry</span></span>](#add-a-registry-entry)
3. [<span data-ttu-id="9ccfc-125">Ustaw skalowanie ustawienie do 100%</span><span class="sxs-lookup"><span data-stu-id="9ccfc-125">Set your display scaling setting to 100%</span></span>](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="9ccfc-126">Uruchom program Visual Studio jako proces świadomości DPI</span><span class="sxs-lookup"><span data-stu-id="9ccfc-126">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="9ccfc-127">Możesz ponownie uruchomić program Visual Studio jako proces świadomości DPI, wybierając opcję na żółty pasek informacyjny.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-127">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="9ccfc-128">Jest to preferowany sposób rozwiązanie problemu.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-128">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="9ccfc-129">Po uruchomieniu programu Visual Studio jako proces świadomości DPI są rozwiązywane problemy układu projektanta, ale czcionki mogą pojawić się rozmyty.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-129">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="9ccfc-130">Programu Visual Studio wyświetla inny komunikat informacyjny żółty, gdy jest uruchamiany jako proces świadomości DPI, informujący, że **Visual Studio jest uruchomiony jako proces świadomości DPI. Projektanci WPF i XAML mogą być wyświetlane nieprawidłowo.**</span><span class="sxs-lookup"><span data-stu-id="9ccfc-130">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="9ccfc-131">Pasek informacyjny zawiera także opcję **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-131">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="9ccfc-132">Jeśli było oddokowane okien narzędzi w programie Visual Studio, w przypadku wybrania opcji, aby ponownie uruchomić jako proces świadomości DPI, położenie tych okien narzędzi, mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-132">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="9ccfc-133">Jeśli używasz profilu domyślnego języka Visual Basic lub jeśli masz **Zapisz nowe projekty po utworzeniu** opcja jest wyłączona w **narzędzia** > **opcje**  >  **Projekty i rozwiązania**, Visual Studio nie można ponownie otworzyć projekt, po jej ponownym uruchomieniu jako proces świadomości DPI.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-133">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="9ccfc-134">Jednak można otworzyć projektu, wybierając je w obszarze **pliku** > **niedawne projekty i rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-134">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="9ccfc-135">Ważne jest, aby ponownie program Visual Studio jako obsługującą ustawienia DPI proces po zakończeniu pracy w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-135">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="9ccfc-136">Gdy jest uruchomiona jako proces świadomości DPI, czcionki mogą wyglądać rozmyte i może zostać wyświetlony problemów w innych projektantów, takich jak **projektanta XAML**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-136">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="9ccfc-137">Po zamknięciu i ponownym otwarciu Visual Studio, gdy jest uruchomiona w trybie świadomości DPI, zostanie on obsługującą ustawienia DPI ponownie.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-137">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="9ccfc-138">Możesz również kliknąć **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces** opcja na pasku informacyjnym.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-138">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="9ccfc-139">Należy dodać wpis rejestru</span><span class="sxs-lookup"><span data-stu-id="9ccfc-139">Add a registry entry</span></span>

<span data-ttu-id="9ccfc-140">Visual Studio można oznaczyć jako świadomości DPI przez modyfikację rejestru.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-140">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="9ccfc-141">Otwórz **Edytora rejestru** i Dodaj wpis do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklucz:</span><span class="sxs-lookup"><span data-stu-id="9ccfc-141">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="9ccfc-142">**Wpis**: W zależności od tego, czy używasz programu Visual Studio 2017 lub 2019 r należy użyć jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="9ccfc-142">**Entry**: Depending on whether you're using Visual Studio 2017 or 2019, use one of these values:</span></span>

- <span data-ttu-id="9ccfc-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="9ccfc-143">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>
- <span data-ttu-id="9ccfc-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="9ccfc-144">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span></span>

> [!NOTE]
> <span data-ttu-id="9ccfc-145">Jeśli używasz wersji Professional lub Enterprise programu Visual Studio, należy zastąpić **społeczności** z **Professional** lub **Enterprise** we wpisie.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-145">If you're using the Professional or Enterprise edition of Visual Studio, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="9ccfc-146">Również zastąpić literę dysku, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-146">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="9ccfc-147">**Typ**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="9ccfc-147">**Type**: REG_SZ</span></span>

<span data-ttu-id="9ccfc-148">**Wartość**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="9ccfc-148">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="9ccfc-149">Program Visual Studio pozostaje w trybie świadomości DPI, dopóki nie usuniesz wpisu rejestru.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-149">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="9ccfc-150">Ustaw skalowanie ustawienie do 100%</span><span class="sxs-lookup"><span data-stu-id="9ccfc-150">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="9ccfc-151">Aby ustawić ekranu skalowanie ustawienie do 100% w systemie Windows 10, wpisz **ustawienia wyświetlania** na pasku wyszukiwania, a następnie zaznacz zadań **Zmienianie ustawień wyświetlania**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-151">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="9ccfc-152">W **ustawienia** oknie **Zmień rozmiar tekstu, aplikacji i innych elementów** do **100%**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-152">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="9ccfc-153">Ustawianie ekranu skalowanie do 100% może być niepożądane, może sprawić, że interfejs użytkownika zbyt mały, może być używany.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-153">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="disable-notifications"></a><span data-ttu-id="9ccfc-154">Wyłącz powiadomienia</span><span class="sxs-lookup"><span data-stu-id="9ccfc-154">Disable notifications</span></span>

<span data-ttu-id="9ccfc-155">Możesz nie otrzymywać powiadomienia o rozdzielczości DPI skalowanie problemy w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-155">You can choose not to be notified of DPI scaling issues in Visual Studio.</span></span> <span data-ttu-id="9ccfc-156">Możesz chcieć wyłączyć powiadomienia, jeśli nie działają w projektancie, na przykład.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-156">You might want to disable notifications if you aren't working in the designer, for example.</span></span>

<span data-ttu-id="9ccfc-157">Aby wyłączyć powiadomienia, wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-157">To disable notifications, choose **Tools** > **Options** to open the **Options** dialog.</span></span> <span data-ttu-id="9ccfc-158">Następnie wybierz **Windows Forms Designer** > **ogólne**i ustaw **powiadomienia skalowania DPI** do **False**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-158">Then, choose **Windows Forms Designer** > **General**, and set **DPI Scaling Notifications** to **False**.</span></span>

![Wartość DPI skalowanie opcji powiadomień w programie Visual Studio](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

<span data-ttu-id="9ccfc-160">Jeśli chcesz później ponownie włączyć powiadomienia skalowania, ustaw właściwość na **True**.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-160">If you want to later reenable scaling notifications, set the property to **True**.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="9ccfc-161">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="9ccfc-161">Troubleshoot</span></span>

<span data-ttu-id="9ccfc-162">Jeśli przejście rozpoznawanie DPI nie działa zgodnie z oczekiwaniami w programie Visual Studio, sprawdź, czy masz `dpiAwareness` wartość w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image pliku wykonywania Options\devenv.exe**  podkluczy w Edytorze rejestru.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-162">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="9ccfc-163">Jeśli jest obecny, usuń wartość.</span><span class="sxs-lookup"><span data-stu-id="9ccfc-163">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="9ccfc-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ccfc-164">See also</span></span>

- [<span data-ttu-id="9ccfc-165">Automatyczne skalowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9ccfc-165">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
