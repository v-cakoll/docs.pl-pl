---
title: Wyłącz rozpoznawanie DPI w programie Visual Studio
description: W tym artykule omówiono ograniczenia Windows Forms Designer na monitorach HDPI oraz sposobu uruchamiania programu Visual Studio jako proces świadomości DPI.
ms.date: 03/19/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 73f2371c40facf8902958cce020a6f02047615ba
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58633871"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a><span data-ttu-id="86d56-103">Wyłącz rozpoznawanie DPI w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86d56-103">Disable DPI-awareness in Visual Studio</span></span>

<span data-ttu-id="86d56-104">Program Visual Studio jest kropki na aplikację świadomą CAL (DPI), co oznacza automatycznie skaluje ekran.</span><span class="sxs-lookup"><span data-stu-id="86d56-104">Visual Studio is a dots per inch (DPI) aware application, which means the display scales automatically.</span></span> <span data-ttu-id="86d56-105">Jeśli aplikacja stwierdzający, że nie jest obsługującą ustawienia DPI, systemu operacyjnego można skalować aplikację jako mapę bitową.</span><span class="sxs-lookup"><span data-stu-id="86d56-105">If an application states that it's not DPI-aware, the operating system scales the application as a bitmap.</span></span> <span data-ttu-id="86d56-106">To zachowanie jest również nazywany wirtualizacji DPI.</span><span class="sxs-lookup"><span data-stu-id="86d56-106">This behavior is also called DPI virtualization.</span></span> <span data-ttu-id="86d56-107">Aplikacji nadal sądzą, że działa on w 100%, skalowanie lub rozdzielczości 96 dpi.</span><span class="sxs-lookup"><span data-stu-id="86d56-107">The application still thinks that it's running at 100% scaling, or 96 dpi.</span></span>

## <a name="windows-forms-designer-on-hdpi-monitors"></a><span data-ttu-id="86d56-108">Windows Forms Designer na monitorach HDPI</span><span class="sxs-lookup"><span data-stu-id="86d56-108">Windows Forms Designer on HDPI monitors</span></span>

<span data-ttu-id="86d56-109">**Windows Forms Designer** w programie Visual Studio nie ma skalowanie pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="86d56-109">The **Windows Forms Designer** in Visual Studio doesn't have scaling support.</span></span> <span data-ttu-id="86d56-110">Powoduje to, że problemy z wyświetlaniem otwieraniu niektórych formularzy w **Windows Forms Designer** na dużej liczbie punktów na cal (HDPI) monitorów.</span><span class="sxs-lookup"><span data-stu-id="86d56-110">This causes display issues when you open some forms in the **Windows Forms Designer** on high dots per inch (HDPI) monitors.</span></span> <span data-ttu-id="86d56-111">Aby uzyskać przykłady formanty może okazać się nakładają się, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="86d56-111">For examples, controls can appear to overlap as shown in the following image:</span></span>

![Windows Forms Designer w monitorze HDPI](./media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

<span data-ttu-id="86d56-113">Po otwarciu formularza w **Windows Forms Designer** w programie Visual Studio na monitorze HDPI programu Visual Studio Wyświetla żółty informacyjny paska w górnej części projektanta:</span><span class="sxs-lookup"><span data-stu-id="86d56-113">When you open a form in the **Windows Forms Designer** in Visual Studio on an HDPI monitor, Visual Studio displays a yellow informational bar at the top of the designer:</span></span>

![Pasek informacyjny w programie Visual Studio, aby ponownie uruchomić w trybie świadomości DPI](./media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

<span data-ttu-id="86d56-115">Odczytuje komunikat **skalowanie na ekranie głównym jest ustawiona na 200% (192 dpi). Może to spowodować problemy z renderowaniem w oknie projektanta.**</span><span class="sxs-lookup"><span data-stu-id="86d56-115">The message reads **Scaling on your main display is set to 200% (192 dpi). This might cause rendering problems in the designer window.**</span></span>

> [!NOTE]
> <span data-ttu-id="86d56-116">Ten pasek informacyjny została wprowadzona w Visual Studio 2017 w wersji 15.8.</span><span class="sxs-lookup"><span data-stu-id="86d56-116">This informational bar was introduced in Visual Studio 2017 version 15.8.</span></span>

<span data-ttu-id="86d56-117">Jeśli nie działają w projektancie, a nie trzeba dostosować układ formularza, można zignorować pasek informacyjny i kontynuować pracę w edytorze kodu lub w innych typach projektantów.</span><span class="sxs-lookup"><span data-stu-id="86d56-117">If you aren't working in the designer and don't need to adjust the layout of your form, you can ignore the informational bar and continue working in the code editor or in other types of designers.</span></span> <span data-ttu-id="86d56-118">(Możesz również [wyłączyć powiadomienia](#disable-notifications) tak, aby pasek informacyjny nie w dalszym ciągu są wyświetlane.) Tylko **Windows Forms Designer** dotyczy problem.</span><span class="sxs-lookup"><span data-stu-id="86d56-118">(You can also [disable notifications](#disable-notifications) so that the informational bar doesn't continue to appear.) Only the **Windows Forms Designer** is affected.</span></span> <span data-ttu-id="86d56-119">Jeśli musisz pracować w **Windows Forms Designer**, następna sekcja pomoże Ci [stwierdzenie](#to-resolve-the-problem).</span><span class="sxs-lookup"><span data-stu-id="86d56-119">If you do need to work in the **Windows Forms Designer**, the next section helps you [resolve the problem](#to-resolve-the-problem).</span></span>

## <a name="to-resolve-the-problem"></a><span data-ttu-id="86d56-120">Aby rozwiązać ten problem</span><span class="sxs-lookup"><span data-stu-id="86d56-120">To resolve the problem</span></span>

<span data-ttu-id="86d56-121">Istnieją trzy opcje, aby rozwiązać problem z wyświetlaniem.</span><span class="sxs-lookup"><span data-stu-id="86d56-121">There are three options to resolve the display problem.</span></span>

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a><span data-ttu-id="86d56-122">Uruchom program Visual Studio jako proces świadomości DPI</span><span class="sxs-lookup"><span data-stu-id="86d56-122">Restart Visual Studio as a DPI-unaware process</span></span>

<span data-ttu-id="86d56-123">Możesz ponownie uruchomić program Visual Studio jako proces świadomości DPI, wybierając opcję na żółty pasek informacyjny.</span><span class="sxs-lookup"><span data-stu-id="86d56-123">You can restart Visual Studio as a DPI-unaware process by selecting the option on the yellow informational bar.</span></span> <span data-ttu-id="86d56-124">Jest to preferowany sposób rozwiązanie problemu.</span><span class="sxs-lookup"><span data-stu-id="86d56-124">This is the preferred way of resolving the problem.</span></span>

<span data-ttu-id="86d56-125">Po uruchomieniu programu Visual Studio jako proces świadomości DPI są rozwiązywane problemy układu projektanta, ale czcionki mogą pojawić się rozmyty.</span><span class="sxs-lookup"><span data-stu-id="86d56-125">When Visual Studio runs as a DPI-unaware process, the designer layout issues are resolved, but fonts may appear blurry.</span></span> <span data-ttu-id="86d56-126">Programu Visual Studio wyświetla inny komunikat informacyjny żółty, gdy jest uruchamiany jako proces świadomości DPI, informujący, że **Visual Studio jest uruchomiony jako proces świadomości DPI. Projektanci WPF i XAML mogą być wyświetlane nieprawidłowo.**</span><span class="sxs-lookup"><span data-stu-id="86d56-126">Visual Studio displays a different yellow informational message when it runs as a DPI-unaware process that says **Visual Studio is running as a DPI-unaware process. WPF and XAML designers might not display correctly.**</span></span> <span data-ttu-id="86d56-127">Pasek informacyjny zawiera także opcję **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces**.</span><span class="sxs-lookup"><span data-stu-id="86d56-127">The informational bar also provides an option to **Restart Visual Studio as a DPI-aware process**.</span></span>

> [!NOTE]
> - <span data-ttu-id="86d56-128">Jeśli było oddokowane okien narzędzi w programie Visual Studio, w przypadku wybrania opcji, aby ponownie uruchomić jako proces świadomości DPI, położenie tych okien narzędzi, mogą ulec zmianie.</span><span class="sxs-lookup"><span data-stu-id="86d56-128">If you had undocked tool windows in Visual Studio when you selected the option to restart as a DPI-unaware process, the position of those tool windows may change.</span></span>
> - <span data-ttu-id="86d56-129">Jeśli używasz profilu domyślnego języka Visual Basic lub jeśli masz **Zapisz nowe projekty po utworzeniu** opcja jest wyłączona w **narzędzia** > **opcje**  >  **Projekty i rozwiązania**, Visual Studio nie można ponownie otworzyć projekt, po jej ponownym uruchomieniu jako proces świadomości DPI.</span><span class="sxs-lookup"><span data-stu-id="86d56-129">If you use the default Visual Basic profile, or if you have the **Save new projects when created** option deselected in **Tools** > **Options** > **Projects and Solutions**, Visual Studio cannot reopen your project when it restarts as a DPI-unaware process.</span></span> <span data-ttu-id="86d56-130">Jednak można otworzyć projektu, wybierając je w obszarze **pliku** > **niedawne projekty i rozwiązania**.</span><span class="sxs-lookup"><span data-stu-id="86d56-130">However, you can open the project by selecting it under **File** > **Recent Projects and Solutions**.</span></span>

<span data-ttu-id="86d56-131">Ważne jest, aby ponownie program Visual Studio jako obsługującą ustawienia DPI proces po zakończeniu pracy w **Windows Forms Designer**.</span><span class="sxs-lookup"><span data-stu-id="86d56-131">It's important to restart Visual Studio as a DPI-aware process when you're finished working in the **Windows Forms Designer**.</span></span> <span data-ttu-id="86d56-132">Gdy jest uruchomiona jako proces świadomości DPI, czcionki mogą wyglądać rozmyte i może zostać wyświetlony problemów w innych projektantów, takich jak **projektanta XAML**.</span><span class="sxs-lookup"><span data-stu-id="86d56-132">When it's running as a DPI-unaware process, fonts can look blurry and you may see issues in other designers such as the **XAML Designer**.</span></span> <span data-ttu-id="86d56-133">Po zamknięciu i ponownym otwarciu Visual Studio, gdy jest uruchomiona w trybie świadomości DPI, zostanie on obsługującą ustawienia DPI ponownie.</span><span class="sxs-lookup"><span data-stu-id="86d56-133">If you close and reopen Visual Studio when it's running in DPI-unaware mode, it becomes DPI-aware again.</span></span> <span data-ttu-id="86d56-134">Możesz również kliknąć **ponowne uruchomienie programu Visual Studio jako obsługującą ustawienia DPI proces** opcja na pasku informacyjnym.</span><span class="sxs-lookup"><span data-stu-id="86d56-134">You can also click the **Restart Visual Studio as a DPI-aware process** option in the informational bar.</span></span>

### <a name="add-a-registry-entry"></a><span data-ttu-id="86d56-135">Należy dodać wpis rejestru</span><span class="sxs-lookup"><span data-stu-id="86d56-135">Add a registry entry</span></span>

<span data-ttu-id="86d56-136">Visual Studio można oznaczyć jako świadomości DPI przez modyfikację rejestru.</span><span class="sxs-lookup"><span data-stu-id="86d56-136">You can mark Visual Studio as DPI-unaware by modifying the registry.</span></span> <span data-ttu-id="86d56-137">Otwórz **Edytora rejestru** i Dodaj wpis do **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** podklucz:</span><span class="sxs-lookup"><span data-stu-id="86d56-137">Open **Registry Editor** and add an entry to the **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** subkey:</span></span>

<span data-ttu-id="86d56-138">**Wpis**: W zależności od tego, czy używasz programu Visual Studio 2017 lub 2019 r należy użyć jednej z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="86d56-138">**Entry**: Depending on whether you're using Visual Studio 2017 or 2019, use one of these values:</span></span>

- <span data-ttu-id="86d56-139">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="86d56-139">C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe</span></span>
- <span data-ttu-id="86d56-140">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span><span class="sxs-lookup"><span data-stu-id="86d56-140">C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe</span></span>

> [!NOTE]
> <span data-ttu-id="86d56-141">Jeśli używasz wersji Professional lub Enterprise programu Visual Studio, należy zastąpić **społeczności** z **Professional** lub **Enterprise** we wpisie.</span><span class="sxs-lookup"><span data-stu-id="86d56-141">If you're using the Professional or Enterprise edition of Visual Studio, replace **Community** with **Professional** or **Enterprise** in the entry.</span></span> <span data-ttu-id="86d56-142">Również zastąpić literę dysku, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="86d56-142">Also replace the drive letter as necessary.</span></span>

<span data-ttu-id="86d56-143">**Typ**: REG_SZ</span><span class="sxs-lookup"><span data-stu-id="86d56-143">**Type**: REG_SZ</span></span>

<span data-ttu-id="86d56-144">**Wartość**: DPIUNAWARE</span><span class="sxs-lookup"><span data-stu-id="86d56-144">**Value**: DPIUNAWARE</span></span>

> [!NOTE]
> <span data-ttu-id="86d56-145">Program Visual Studio pozostaje w trybie świadomości DPI, dopóki nie usuniesz wpisu rejestru.</span><span class="sxs-lookup"><span data-stu-id="86d56-145">Visual Studio remains in DPI-unaware mode until you remove the registry entry.</span></span>

### <a name="set-your-display-scaling-setting-to-100"></a><span data-ttu-id="86d56-146">Ustaw skalowanie ustawienie do 100%</span><span class="sxs-lookup"><span data-stu-id="86d56-146">Set your display scaling setting to 100%</span></span>

<span data-ttu-id="86d56-147">Aby ustawić ekranu skalowanie ustawienie do 100% w systemie Windows 10, wpisz **ustawienia wyświetlania** na pasku wyszukiwania, a następnie zaznacz zadań **Zmienianie ustawień wyświetlania**.</span><span class="sxs-lookup"><span data-stu-id="86d56-147">To set your display scaling setting to 100% in Windows 10, type **display settings** in the task bar search box, and then select **Change display settings**.</span></span> <span data-ttu-id="86d56-148">W **ustawienia** oknie **Zmień rozmiar tekstu, aplikacji i innych elementów** do **100%**.</span><span class="sxs-lookup"><span data-stu-id="86d56-148">In the **Settings** window, set **Change the size of text, apps, and other items** to **100%**.</span></span>

<span data-ttu-id="86d56-149">Ustawianie ekranu skalowanie do 100% może być niepożądane, może sprawić, że interfejs użytkownika zbyt mały, może być używany.</span><span class="sxs-lookup"><span data-stu-id="86d56-149">Setting your display scaling to 100% may be undesirable, because it can make the user interface too small to be usable.</span></span>

## <a name="disable-notifications"></a><span data-ttu-id="86d56-150">Wyłącz powiadomienia</span><span class="sxs-lookup"><span data-stu-id="86d56-150">Disable notifications</span></span>

<span data-ttu-id="86d56-151">Możesz nie otrzymywać powiadomienia o rozdzielczości DPI skalowanie problemy w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="86d56-151">You can choose not to be notified of DPI scaling issues in Visual Studio.</span></span> <span data-ttu-id="86d56-152">Możesz chcieć wyłączyć powiadomienia, jeśli nie działają w projektancie, na przykład.</span><span class="sxs-lookup"><span data-stu-id="86d56-152">You might want to disable notifications if you aren't working in the designer, for example.</span></span>

<span data-ttu-id="86d56-153">Aby wyłączyć powiadomienia, wybierz **narzędzia** > **opcje** otworzyć **opcje** okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="86d56-153">To disable notifications, choose **Tools** > **Options** to open the **Options** dialog.</span></span> <span data-ttu-id="86d56-154">Następnie wybierz **Windows Forms Designer** > **ogólne**i ustaw **powiadomienia skalowania DPI** do **False**.</span><span class="sxs-lookup"><span data-stu-id="86d56-154">Then, choose **Windows Forms Designer** > **General**, and set **DPI Scaling Notifications** to **False**.</span></span>

![Wartość DPI skalowanie opcji powiadomień w programie Visual Studio](./media/disable-dpi-awareness-visual-studio/notifications-option.png)

<span data-ttu-id="86d56-156">Jeśli chcesz później ponownie włączyć powiadomienia skalowania, ustaw właściwość na **True**.</span><span class="sxs-lookup"><span data-stu-id="86d56-156">If you want to later reenable scaling notifications, set the property to **True**.</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="86d56-157">Rozwiązywanie problemów</span><span class="sxs-lookup"><span data-stu-id="86d56-157">Troubleshoot</span></span>

<span data-ttu-id="86d56-158">Jeśli przejście rozpoznawanie DPI nie działa zgodnie z oczekiwaniami w programie Visual Studio, sprawdź, czy masz `dpiAwareness` wartość w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image pliku wykonywania Options\devenv.exe**  podkluczy w Edytorze rejestru.</span><span class="sxs-lookup"><span data-stu-id="86d56-158">If the DPI-awareness transition isn't working as expected in Visual Studio, check to see if you have the `dpiAwareness` value in the **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** subkey in Registry Editor.</span></span> <span data-ttu-id="86d56-159">Jeśli jest obecny, usuń wartość.</span><span class="sxs-lookup"><span data-stu-id="86d56-159">Delete the value if it's present.</span></span>

## <a name="see-also"></a><span data-ttu-id="86d56-160">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86d56-160">See also</span></span>

- [<span data-ttu-id="86d56-161">Automatyczne skalowanie w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="86d56-161">Automatic scaling in Windows Forms</span></span>](automatic-scaling-in-windows-forms.md)
