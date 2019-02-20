---
title: 'Instrukcje: Debugowanie aplikacji usług Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 15b790f4a4d3348e2bef3e7e929d72c09da8690c
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441882"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="826d8-102">Instrukcje: Debugowanie aplikacji usług Windows</span><span class="sxs-lookup"><span data-stu-id="826d8-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="826d8-103">Usługa musi być uruchamiane w kontekście Menedżera sterowania usługami, a nie z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="826d8-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="826d8-104">Z tego powodu debugowanie usługi jest tak proste jak debugowanie innych typów aplikacji Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="826d8-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="826d8-105">Aby debugować usługę, należy uruchomić usługę i następnie dołączyć debuger do procesu, w którym jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="826d8-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="826d8-106">Następnie można debugować aplikację za pomocą wszystkich standardowych funkcji debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="826d8-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="826d8-107">Nie należy dołączać do procesu, chyba że wiesz, co ten proces i rozumiesz, jakie skutki dołączenia i ewentualne skutki zniszczenia tego procesu.</span><span class="sxs-lookup"><span data-stu-id="826d8-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="826d8-108">Na przykład jeśli dołączyć do procesu WinLogon, a następnie zatrzymasz debugowanie, system zatrzyma się, ponieważ nie może działać bez usługi WinLogon.</span><span class="sxs-lookup"><span data-stu-id="826d8-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="826d8-109">Można dołączyć debuger, tylko do czynnej usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="826d8-110">Proces załącznika przerywa bieżące działanie usługi; faktycznie nie zatrzymać lub wstrzymać przetwarzania usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="826d8-111">Oznacza to jeśli usługa jest uruchomiona, po rozpoczęciu debugowania, jest technicznie nadal w stanie uruchomiona podczas jej debugowania, ale jej przetwarzanie jest wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="826d8-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="826d8-112">Po dołączeniu do procesu, możesz ustawić punkty przerwania i ich użyć do debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="826d8-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="826d8-113">Po zamknięciu okna dialogowego, które służy do dołączania do procesu, jesteś w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="826d8-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="826d8-114">Aby uruchomić, zatrzymać, wstrzymać lub kontynuować usługę, w tym samym osiągając ustawione punkty przerwania, można użyć Menedżera sterowania usługami.</span><span class="sxs-lookup"><span data-stu-id="826d8-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="826d8-115">Po pomyślnym debugowaniu, można później usunąć tę fikcyjną usługę.</span><span class="sxs-lookup"><span data-stu-id="826d8-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="826d8-116">W tym artykule opisano profilowanie to usługa, która jest uruchomiona na komputerze lokalnym, ale można również debugować usług Windows, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="826d8-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="826d8-117">Zobacz [zdalne debugowanie](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="826d8-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="826d8-118">Debugowanie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda może być trudne, ponieważ Menedżera sterowania usługami nakłada limit 30-sekundowy na wszystkie próby uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="826d8-119">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów: Debugowanie usług Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="826d8-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="826d8-120">Aby uzyskać istotne informacje dotyczące debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla plików binarnych, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="826d8-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="826d8-121">Jeśli debugujesz to usługa, która jest wbudowana w programie Visual Studio, plików symboli (pliki .pdb) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka i debuger ładuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="826d8-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="826d8-122">Jeśli debugujesz usługa, która nie została skompilowana, należy najpierw Znajdź symbole dla usługi i upewnij się, że są one przez debuger.</span><span class="sxs-lookup"><span data-stu-id="826d8-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="826d8-123">Zobacz [Określ symboli (.pdb) i pliki w debugerze programu Visual Studio źródłowe](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="826d8-123">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="826d8-124">Jeśli debugowanie procesów systemowych lub mają symbole dla wywołania systemowe w usługach, należy dodać serwery symboli firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="826d8-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="826d8-125">Zobacz [symboli debugowania](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="826d8-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="826d8-126">Aby debugować usługę</span><span class="sxs-lookup"><span data-stu-id="826d8-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="826d8-127">Tworzenie usługi w konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="826d8-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="826d8-128">Zainstaluj swoje usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-128">Install your service.</span></span> <span data-ttu-id="826d8-129">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="826d8-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="826d8-130">Uruchom usługę z **Menedżera sterowania usługami**, **Eksploratora serwera**, lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="826d8-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="826d8-131">Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="826d8-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="826d8-132">Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, dzięki czemu możesz dołączyć do procesów systemowych.</span><span class="sxs-lookup"><span data-stu-id="826d8-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="826d8-133">(Opcjonalnie) Na pasku menu programu Visual Studio, wybierz **narzędzia**, **opcje**.</span><span class="sxs-lookup"><span data-stu-id="826d8-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="826d8-134">W **opcje** okna dialogowego wybierz **debugowanie**, **symbole**, wybierz opcję **serwery symboli firmy Microsoft** pole wyboru, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="826d8-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="826d8-135">Na pasku menu wybierz **dołączyć do procesu** z **debugowania** lub **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="826d8-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="826d8-136">(Klawiatura: Ctrl+Alt+P)</span><span class="sxs-lookup"><span data-stu-id="826d8-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="826d8-137">**Procesy** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="826d8-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="826d8-138">Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="826d8-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="826d8-139">W **dostępne procesy** sekcji, wybierz proces danej usługi, a następnie wybierz **Dołącz**.</span><span class="sxs-lookup"><span data-stu-id="826d8-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="826d8-140">Proces będzie mieć taką samą nazwę jak plik wykonywalny dla usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="826d8-141">**Dołączyć do procesu** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="826d8-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="826d8-142">Wybierz odpowiednie opcje, a następnie wybierz **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="826d8-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="826d8-143">Jesteś teraz w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="826d8-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="826d8-144">Ustaw wszelkie punkty przerwania, którego chcesz użyć w kodzie.</span><span class="sxs-lookup"><span data-stu-id="826d8-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="826d8-145">Dostęp do Menedżera sterowania usługami i manipulowania Twojej usługi, wysyłając polecenia Zatrzymaj, Wstrzymaj i Kontynuuj do punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="826d8-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="826d8-146">Aby uzyskać więcej informacji na temat uruchamiania Menedżera sterowania usługami, zobacz [jak: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="826d8-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="826d8-147">Zobacz też [Rozwiązywanie problemów: Debugowanie usług Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="826d8-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="826d8-148">Wskazówki dotyczące debugowania dla usług Windows</span><span class="sxs-lookup"><span data-stu-id="826d8-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="826d8-149">Dołączanie do procesu usługi pozwala debugować większość, ale nie wszystkie kod dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="826d8-150">Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w usłudze <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody lub kod w `Main` metodę, która jest używana do ładowania usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="826d8-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="826d8-151">Jednym ze sposobów obejścia tego ograniczenia jest utworzyć tymczasowej drugiej usługi w aplikacji usługi, która istnieje tylko do pomocy w debugowaniu.</span><span class="sxs-lookup"><span data-stu-id="826d8-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="826d8-152">Można zainstalować obie usługi, a następnie uruchom tę fikcyjną usługę, aby załadować procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="826d8-153">Po rozpoczęciu procesu tymczasowej usługi można użyć **debugowania** menu w programie Visual Studio, aby dołączyć do procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="826d8-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="826d8-154">Spróbuj dodać wywołania <xref:System.Threading.Thread.Sleep%2A> metody akcji opóźniania, dopóki nie można dołączyć do procesu.</span><span class="sxs-lookup"><span data-stu-id="826d8-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="826d8-155">Spróbuj zmienić program w aplikacji konsolowej regularne.</span><span class="sxs-lookup"><span data-stu-id="826d8-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="826d8-156">Aby to zrobić, napisz ponownie `Main` metody w następujący sposób, dzięki czemu może działać jako usługa Windows i jako aplikację konsolową w języku, w zależności od sposobu uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="826d8-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="826d8-157">Instrukcje: Uruchom usługę Windows jako aplikację konsolową w języku</span><span class="sxs-lookup"><span data-stu-id="826d8-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="826d8-158">Dodaj metodę z uruchomioną usługą <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:</span><span class="sxs-lookup"><span data-stu-id="826d8-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="826d8-159">Ponowne zapisywanie adresów `Main` metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="826d8-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        if (Environment.UserInteractive)  
        {  
            MyNewService service1 = new MyNewService(args);  
            service1.TestStartupAndStop(args);  
        }  
        else  
        {  
            // Put the body of your old Main method here.  
        }  
    }
    ```  
  
3.  <span data-ttu-id="826d8-160">W **aplikacji** na karcie właściwości projektu, ustaw **typ danych wyjściowych** do **aplikację Konsolową**.</span><span class="sxs-lookup"><span data-stu-id="826d8-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="826d8-161">Wybierz **Rozpocznij debugowanie** (F5).</span><span class="sxs-lookup"><span data-stu-id="826d8-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="826d8-162">Aby ponownie uruchomić program jako usługę Windows, należy go zainstalować i uruchomić go w zwykły sposób usługi Windows.</span><span class="sxs-lookup"><span data-stu-id="826d8-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="826d8-163">Nie jest konieczne zmiany można cofnąć.</span><span class="sxs-lookup"><span data-stu-id="826d8-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="826d8-164">W niektórych przypadkach, np. Jeśli chcesz debugować problem, który występuje tylko podczas uruchamiania systemu należy użyć debugera Windows.</span><span class="sxs-lookup"><span data-stu-id="826d8-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="826d8-165">[Pobierz zestaw Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) zobaczyć [sposób debugowania usług Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="826d8-165">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826d8-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="826d8-166">See also</span></span>
- [<span data-ttu-id="826d8-167">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="826d8-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="826d8-168">Instrukcje: Instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="826d8-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="826d8-169">Instrukcje: Uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="826d8-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="826d8-170">Debugowanie usługi</span><span class="sxs-lookup"><span data-stu-id="826d8-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
