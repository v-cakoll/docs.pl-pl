---
title: 'Instrukcje: Debugowanie aplikacji usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
ms.openlocfilehash: 71b2b1d32c06afca4abd89df4f6449dacb32046c
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988528"
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="d8b4a-102">Instrukcje: Debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d8b4a-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="d8b4a-103">Usługa musi być uruchomiona w kontekście menedżera kontroli usług, a nie z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="d8b4a-104">Z tego powodu debugowanie usługi nie jest tak proste jak debugowanie innych typów aplikacji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="d8b4a-105">Aby debugować usługę, należy ją uruchomić, a następnie dołączyć debuger do procesu, w którym jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="d8b4a-106">Następnie można debugować aplikację przy użyciu wszystkich standardowych funkcji debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="d8b4a-107">Nie należy dołączać do procesu, chyba że wiesz, co to jest proces, i zrozumieć konsekwencje dołączenia do tego procesu i prawdopodobnie go zabijania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="d8b4a-108">Na przykład jeśli dołączysz do procesu WinLogon, a następnie zatrzymasz debugowanie, system zostanie zatrzymany, ponieważ nie może działać bez usługi WinLogon.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="d8b4a-109">Debuger można dołączyć tylko do działającej usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="d8b4a-110">Proces załącznika przerywa bieżące działanie usługi; w rzeczywistości nie zatrzymuje ani nie wstrzymuje przetwarzania usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="d8b4a-111">Oznacza to, że jeśli usługa jest uruchomiona po rozpoczęciu debugowania, nadal jest technicznie w stanie uruchomienia podczas debugowania, ale jego przetwarzanie zostało wstrzymane.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="d8b4a-112">Po dołączeniu do procesu można ustawić punkty przerwania i użyć ich do debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="d8b4a-113">Po opuszczeniu okna dialogowego, którego używasz do dołączania do procesu, Pracujesz w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="d8b4a-114">Można użyć Menedżera sterowania usługami, aby uruchomić, zatrzymać, wstrzymać i kontynuować usługę, a tym samym ustawić punkty przerwania, które ustawisz.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="d8b4a-115">Możesz później usunąć tę fikcyjną usługę po pomyślnym zakończeniu debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="d8b4a-116">W tym artykule opisano debugowanie usługi, która jest uruchomiona na komputerze lokalnym, ale można również debugować usługi systemu Windows, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="d8b4a-117">Zobacz [debugowanie zdalne](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8b4a-118"><xref:System.ServiceProcess.ServiceBase.OnStart%2A> Debugowanie metody może być trudne, ponieważ Menedżer kontroli usług nakłada limit 30 sekund na wszystkie próby uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="d8b4a-119">Aby uzyskać więcej informacji, [zobacz Rozwiązywanie problemów: Debugowanie usług](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d8b4a-120">Aby uzyskać istotne informacje na potrzeby debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla debugowanych plików binarnych.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="d8b4a-121">W przypadku debugowania usługi skompilowanej w programie Visual Studio pliki symboli (pliki. pdb) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka, a debuger ładuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="d8b4a-122">W przypadku debugowania nieskompilowanej usługi należy najpierw znaleźć symbole usługi i upewnić się, że są one dostępne przez debuger.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="d8b4a-123">Zobacz [Określanie symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-123">See [Specify Symbol (.pdb) and Source Files in the Visual Studio Debugger](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span> <span data-ttu-id="d8b4a-124">Jeśli debugujesz proces systemowy lub chcesz mieć symbole dla wywołań systemowych w usługach, należy dodać serwery symboli Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="d8b4a-125">Zobacz [debugowanie symboli](/windows/desktop/DxTechArts/debugging-with-symbols).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-125">See [Debugging Symbols](/windows/desktop/DxTechArts/debugging-with-symbols).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="d8b4a-126">Aby debugować usługę</span><span class="sxs-lookup"><span data-stu-id="d8b4a-126">To debug a service</span></span>  
  
1. <span data-ttu-id="d8b4a-127">Kompiluj swoją usługę w konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-127">Build your service in the Debug configuration.</span></span>  
  
2. <span data-ttu-id="d8b4a-128">Zainstaluj usługę.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-128">Install your service.</span></span> <span data-ttu-id="d8b4a-129">Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)usług.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3. <span data-ttu-id="d8b4a-130">Uruchom usługę z **Menedżera sterowania usługami**, **Eksplorator serwera**lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="d8b4a-131">Aby uzyskać więcej informacji, zobacz [jak: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4. <span data-ttu-id="d8b4a-132">Uruchom program Visual Studio z poświadczeniami administracyjnymi, aby umożliwić dołączenie do procesów systemowych.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5. <span data-ttu-id="d8b4a-133">Obowiązkowe Na pasku menu programu Visual Studio wybierz **Narzędzia**, **Opcje**.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="d8b4a-134">W oknie dialogowym **Opcje** wybierz pozycję **debugowanie**, **symbole**, zaznacz pole wyboru **serwery symboli firmy Microsoft** , a następnie wybierz przycisk **OK** .</span><span class="sxs-lookup"><span data-stu-id="d8b4a-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6. <span data-ttu-id="d8b4a-135">Na pasku menu wybierz polecenie **Dołącz do procesu** z menu **debugowanie** lub **Narzędzia** .</span><span class="sxs-lookup"><span data-stu-id="d8b4a-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="d8b4a-136">Klawiatury Ctrl+Alt+P)</span><span class="sxs-lookup"><span data-stu-id="d8b4a-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="d8b4a-137">Zostanie wyświetlone okno dialogowe **procesy** .</span><span class="sxs-lookup"><span data-stu-id="d8b4a-137">The **Processes** dialog box appears.</span></span>  
  
7. <span data-ttu-id="d8b4a-138">Zaznacz pole wyboru **Pokaż procesy wszystkich użytkowników** .</span><span class="sxs-lookup"><span data-stu-id="d8b4a-138">Select the **Show processes from all users** check box.</span></span>  
  
8. <span data-ttu-id="d8b4a-139">W sekcji **dostępne procesy** wybierz proces dla usługi, a następnie wybierz pozycję **Dołącz**.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="d8b4a-140">Ten proces będzie mieć taką samą nazwę jak plik wykonywalny dla usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="d8b4a-141">**Dołączyć do procesu** pojawi się okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="d8b4a-142">Wybierz odpowiednie opcje, a następnie kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="d8b4a-143">Jesteś teraz w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="d8b4a-144">Ustaw wszystkie punkty przerwania, które mają być używane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="d8b4a-145">Dostęp do Menedżera sterowania usługami i manipulowanie usługą, wysyłanie poleceń Zatrzymaj, Wstrzymaj i Kontynuuj, aby trafiać z punktów przerwania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="d8b4a-146">Aby uzyskać więcej informacji na temat uruchamiania Menedżera sterowania usługami, [zobacz How to: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="d8b4a-147">Zobacz [również Rozwiązywanie problemów: Debugowanie usług](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md)systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="d8b4a-148">Wskazówki dotyczące debugowania dla usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d8b4a-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="d8b4a-149">Dołączenie do procesu usługi pozwala debugować większość, ale nie wszystkie, kod dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="d8b4a-150">Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie usługi lub kodzie `Main` w metodzie, która jest używana do załadowania usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="d8b4a-151">Jednym ze sposobów obejścia tego ograniczenia jest utworzenie tymczasowej drugiej usługi w aplikacji usługi, która istnieje tylko w celu ułatwienia debugowania.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="d8b4a-152">Można zainstalować obie usługi, a następnie uruchomić tę fikcyjną usługę w celu załadowania procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="d8b4a-153">Po rozpoczęciu procesu przez usługę tymczasową możesz użyć menu **Debuguj** w programie Visual Studio w celu dołączenia do procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="d8b4a-154">Spróbuj dodać wywołania metody, <xref:System.Threading.Thread.Sleep%2A> aby opóźnić akcję do momentu dołączenia do procesu.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="d8b4a-155">Spróbuj zmienić program na zwykłą aplikację konsolową.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="d8b4a-156">W tym celu należy napisać ponownie `Main` metodę w następujący sposób, aby można było ją uruchomić zarówno jako usługę systemu Windows, jak i jako aplikację konsolową, w zależności od sposobu jej uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="d8b4a-157">Instrukcje: Uruchamianie usługi systemu Windows jako aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="d8b4a-157">How to: Run a Windows Service as a console application</span></span>  
  
1. <span data-ttu-id="d8b4a-158">Dodaj metodę do usługi, która uruchamia <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i: <xref:System.ServiceProcess.ServiceBase.OnStop%2A></span><span class="sxs-lookup"><span data-stu-id="d8b4a-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. <span data-ttu-id="d8b4a-159">Napisz ponownie `Main` metodę w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d8b4a-159">Rewrite the `Main` method as follows:</span></span>  
  
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
  
3. <span data-ttu-id="d8b4a-160">Na karcie **aplikacja** we właściwościach projektu Ustaw **Typ danych wyjściowych** na **Aplikacja konsolowa**.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4. <span data-ttu-id="d8b4a-161">Wybierz **Rozpocznij debugowanie** (F5).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-161">Choose **Start Debugging** (F5).</span></span>  
  
5. <span data-ttu-id="d8b4a-162">Aby ponownie uruchomić program jako usługę systemu Windows, zainstaluj go i uruchom jak zwykle w przypadku usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="d8b4a-163">Nie trzeba odwrócić tych zmian.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="d8b4a-164">W niektórych przypadkach, na przykład gdy chcesz debugować problem, który występuje tylko podczas uruchamiania systemu, musisz użyć debugera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d8b4a-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="d8b4a-165">[Pobierz zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/download-the-wdk) i zobacz, [jak debugować usługi systemu Windows](https://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="d8b4a-165">[Download the Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk) and see [How to debug Windows Services](https://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b4a-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8b4a-166">See also</span></span>

- [<span data-ttu-id="d8b4a-167">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d8b4a-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [<span data-ttu-id="d8b4a-168">Instrukcje: Instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="d8b4a-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [<span data-ttu-id="d8b4a-169">Instrukcje: Uruchom usługi</span><span class="sxs-lookup"><span data-stu-id="d8b4a-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)
- [<span data-ttu-id="d8b4a-170">Debugowanie usługi</span><span class="sxs-lookup"><span data-stu-id="d8b4a-170">Debugging a Service</span></span>](/windows/desktop/Services/debugging-a-service)
