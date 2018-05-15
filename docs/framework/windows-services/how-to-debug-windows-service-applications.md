---
title: 'Porady: debugowanie aplikacji usług systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
author: ghogen
manager: douge
ms.openlocfilehash: 2c73ccd75bdbd1298371921bababa87ba4520495
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-debug-windows-service-applications"></a><span data-ttu-id="1e566-102">Porady: debugowanie aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1e566-102">How to: Debug Windows Service Applications</span></span>
<span data-ttu-id="1e566-103">Usługa musi być uruchamiane w kontekście Menedżera sterowania usługami, a nie z poziomu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e566-103">A service must be run from within the context of the Services Control Manager rather than from within Visual Studio.</span></span> <span data-ttu-id="1e566-104">Z tego powodu debugowania usługi nie jest równie proste jak debugowanie różnych typów aplikacji Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e566-104">For this reason, debugging a service is not as straightforward as debugging other Visual Studio application types.</span></span> <span data-ttu-id="1e566-105">Aby debugować usługi, należy uruchomić usługę i następnie dołączyć do procesu, w którym jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="1e566-105">To debug a service, you must start the service and then attach a debugger to the process in which it is running.</span></span> <span data-ttu-id="1e566-106">Można następnie Debuguj aplikację przy użyciu wszystkich standardowych funkcji debugowania programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1e566-106">You can then debug your application by using all of the standard debugging functionality of Visual Studio.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1e566-107">Należy nie dołączyć procesu, jeśli nie masz pewności, co proces jest i konsekwencje związane z a prawdopodobnie skasowanie tego procesu.</span><span class="sxs-lookup"><span data-stu-id="1e566-107">You should not attach to a process unless you know what the process is and understand the consequences of attaching to and possibly killing that process.</span></span> <span data-ttu-id="1e566-108">Na przykład jeśli dołączyć do procesu logowania do systemu Windows, a następnie zatrzymać debugowanie, system zostanie zatrzymany, ponieważ nie może działać bez usługi WinLogon.</span><span class="sxs-lookup"><span data-stu-id="1e566-108">For example, if you attach to the WinLogon process and then stop debugging, the system will halt because it can’t operate without WinLogon.</span></span>  
  
 <span data-ttu-id="1e566-109">Tylko do uruchomionej usługi można dołączyć debugera.</span><span class="sxs-lookup"><span data-stu-id="1e566-109">You can attach the debugger only to a running service.</span></span> <span data-ttu-id="1e566-110">Przerywa proces załącznika bieżącego działania usługi; faktycznie nie zatrzymać lub wstrzymać przetwarzania usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-110">The attachment process interrupts the current functioning of your service; it doesn’t actually stop or pause the service's processing.</span></span> <span data-ttu-id="1e566-111">Oznacza to jeśli usługa jest uruchomiona, po rozpoczęciu debugowania, jest nadal technicznie w stanie uruchomiono jego debugowania, ale jego przetwarzanie zostało zawieszone.</span><span class="sxs-lookup"><span data-stu-id="1e566-111">That is, if your service is running when you begin debugging, it is still technically in the Started state as you debug it, but its processing has been suspended.</span></span>  
  
 <span data-ttu-id="1e566-112">Po dołączeniu do procesu, można ustawić punktów przerwania i ich używać do debugowania kodu.</span><span class="sxs-lookup"><span data-stu-id="1e566-112">After attaching to the process, you can set breakpoints and use these to debug your code.</span></span> <span data-ttu-id="1e566-113">Po zamknięciu okna dialogowego, który służy do dołączania do procesu jesteś skutecznie w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="1e566-113">Once you exit the dialog box you use to attach to the process, you are effectively in debug mode.</span></span> <span data-ttu-id="1e566-114">W Menedżerze sterowania usługami umożliwia uruchamianie, zatrzymywanie, wstrzymywanie i kontynuować usługi, w związku z tym naciśnięcie punktów przerwania ustawionych.</span><span class="sxs-lookup"><span data-stu-id="1e566-114">You can use the Services Control Manager to start, stop, pause and continue your service, thus hitting the breakpoints you've set.</span></span> <span data-ttu-id="1e566-115">Później można usunąć tej usługi fikcyjny po debugowania zakończy się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1e566-115">You can later remove this dummy service after debugging is successful.</span></span>  
  
 <span data-ttu-id="1e566-116">W tym artykule omówiono debugowania to usługa, która jest uruchomiona na komputerze lokalnym, ale również można debugować usług systemu Windows, które są uruchomione na komputerze zdalnym.</span><span class="sxs-lookup"><span data-stu-id="1e566-116">This article covers debugging a service that's running on the local computer, but you can also debug Windows Services that are running on a remote computer.</span></span> <span data-ttu-id="1e566-117">Zobacz [zdalnego debugowania](/visualstudio/debugger/debug-installed-app-package).</span><span class="sxs-lookup"><span data-stu-id="1e566-117">See [Remote Debugging](/visualstudio/debugger/debug-installed-app-package).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e566-118">Debugowanie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda może być trudne, ponieważ Menedżera sterowania usługami związany z ograniczeniem 30 sekund na wszystkie próby uruchomienia usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-118">Debugging the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method can be difficult because the Services Control Manager imposes a 30-second limit on all attempts to start a service.</span></span> <span data-ttu-id="1e566-119">Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów: debugowanie usług systemu Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e566-119">For more information, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="1e566-120">Aby uzyskać przydatne informacje dotyczące debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla danych binarnych, które są debugowane.</span><span class="sxs-lookup"><span data-stu-id="1e566-120">To get meaningful information for debugging, the Visual Studio debugger needs to find symbol files for the binaries that are being debugged.</span></span> <span data-ttu-id="1e566-121">Jeśli debugujesz usługi, które zostały utworzone w programie Visual Studio, plików symboli (.pdb, pliki) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka i debuger ładuje je automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1e566-121">If you are debugging a service that you built in Visual Studio, the symbol files (.pdb files) are in the same folder as the executable or library, and the debugger loads them automatically.</span></span> <span data-ttu-id="1e566-122">Jeśli usługa, która nie kompilacji debugowania, należy najpierw odnaleźć symboli dla usługi i upewnij się, że są one przez debuger.</span><span class="sxs-lookup"><span data-stu-id="1e566-122">If you are debugging a service that you didn't build, you should first find symbols for the service and make sure they can be found by the debugger.</span></span> <span data-ttu-id="1e566-123">Zobacz [Określ symboli (.pdb) i pliki źródłowe](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span><span class="sxs-lookup"><span data-stu-id="1e566-123">See [Specify Symbol (.pdb) and Source Files](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b).</span></span> <span data-ttu-id="1e566-124">Jeśli debugowanie procesów systemowych lub mają symboli dla wywołań systemowych w usługach, należy dodać serwerów symboli firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1e566-124">If you're debugging a system process or want to have symbols for system calls in your services, you should add the Microsoft Symbol Servers.</span></span> <span data-ttu-id="1e566-125">Zobacz [symbole debugowania](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span><span class="sxs-lookup"><span data-stu-id="1e566-125">See [Debugging Symbols](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).</span></span>  
  
### <a name="to-debug-a-service"></a><span data-ttu-id="1e566-126">Aby debugować usługi</span><span class="sxs-lookup"><span data-stu-id="1e566-126">To debug a service</span></span>  
  
1.  <span data-ttu-id="1e566-127">Tworzenie usługi w konfiguracji debugowania.</span><span class="sxs-lookup"><span data-stu-id="1e566-127">Build your service in the Debug configuration.</span></span>  
  
2.  <span data-ttu-id="1e566-128">Zainstaluj usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-128">Install your service.</span></span> <span data-ttu-id="1e566-129">Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e566-129">For more information, see [How to: Install and Uninstall Services](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).</span></span>  
  
3.  <span data-ttu-id="1e566-130">Uruchomić usługę, albo z **Menedżera sterowania usługami**, **Eksploratora serwera**, lub z kodu.</span><span class="sxs-lookup"><span data-stu-id="1e566-130">Start your service, either from **Services Control Manager**, **Server Explorer**, or from code.</span></span> <span data-ttu-id="1e566-131">Aby uzyskać więcej informacji, zobacz [porady: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e566-131">For more information, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span>  
  
4.  <span data-ttu-id="1e566-132">Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, więc można dołączyć do procesów systemowych.</span><span class="sxs-lookup"><span data-stu-id="1e566-132">Start Visual Studio with administrative credentials so you can attach to system processes.</span></span>  
  
5.  <span data-ttu-id="1e566-133">(Opcjonalnie) Na pasku menu programu Visual Studio wybierz **narzędzia**, **opcje**.</span><span class="sxs-lookup"><span data-stu-id="1e566-133">(Optional) On the Visual Studio menu bar, choose **Tools**, **Options**.</span></span> <span data-ttu-id="1e566-134">W **opcje** oknie dialogowym wybierz **debugowanie**, **symbole**, wybierz pozycję **serwerów symboli firmy Microsoft** pole wyboru, a następnie wybierz pozycję **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="1e566-134">In the **Options** dialog box, choose **Debugging**, **Symbols**, select the **Microsoft Symbol Servers** check box, and then choose the **OK** button.</span></span>  
  
6.  <span data-ttu-id="1e566-135">Na pasku menu wybierz **dołączyć do procesu** z **debugowania** lub **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="1e566-135">On the menu bar, choose **Attach to Process** from the **Debug** or **Tools** menu.</span></span> <span data-ttu-id="1e566-136">(Klawiatury: Ctrl + Alt + P)</span><span class="sxs-lookup"><span data-stu-id="1e566-136">(Keyboard: Ctrl+Alt+P)</span></span>  
  
     <span data-ttu-id="1e566-137">**Procesów** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1e566-137">The **Processes** dialog box appears.</span></span>  
  
7.  <span data-ttu-id="1e566-138">Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.</span><span class="sxs-lookup"><span data-stu-id="1e566-138">Select the **Show processes from all users** check box.</span></span>  
  
8.  <span data-ttu-id="1e566-139">W **dostępne procesy** sekcji, wybierz proces usługi, a następnie wybierz pozycję **Attach**.</span><span class="sxs-lookup"><span data-stu-id="1e566-139">In the **Available Processes** section, choose the process for your service, and then choose **Attach**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="1e566-140">Proces ma taką samą nazwę jak plik wykonywalny dla usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-140">The process will have the same name as the executable file for your service.</span></span>  
  
     <span data-ttu-id="1e566-141">**Dołączyć do procesu** zostanie wyświetlone okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1e566-141">The **Attach to Process** dialog box appears.</span></span>  
  
9. <span data-ttu-id="1e566-142">Wybierz odpowiednie opcje, a następnie wybierz **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1e566-142">Choose the appropriate options, and then choose **OK** to close the dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1e566-143">Jesteś teraz w trybie debugowania.</span><span class="sxs-lookup"><span data-stu-id="1e566-143">You are now in debug mode.</span></span>  
  
10. <span data-ttu-id="1e566-144">Ustaw wszystkie punkty przerwania, który ma być używany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1e566-144">Set any breakpoints you want to use in your code.</span></span>  
  
11. <span data-ttu-id="1e566-145">Dostęp do Menedżera sterowania usługami manipulowania Twojej usługi, wysyłania Zatrzymaj, Wstrzymaj i Kontynuuj polecenia trafienie punkty przerwań.</span><span class="sxs-lookup"><span data-stu-id="1e566-145">Access the Services Control Manager and manipulate your service, sending stop, pause, and continue commands to hit your breakpoints.</span></span> <span data-ttu-id="1e566-146">Aby uzyskać więcej informacji dotyczących uruchamiania Menedżera kontroli usług, zobacz [porady: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e566-146">For more information about running the Services Control Manager, see [How to: Start Services](../../../docs/framework/windows-services/how-to-start-services.md).</span></span> <span data-ttu-id="1e566-147">Zobacz też [Rozwiązywanie problemów: debugowanie usług systemu Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span><span class="sxs-lookup"><span data-stu-id="1e566-147">Also, see [Troubleshooting: Debugging Windows Services](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).</span></span>  
  
## <a name="debugging-tips-for-windows-services"></a><span data-ttu-id="1e566-148">Debugowanie porady dla usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1e566-148">Debugging Tips for Windows Services</span></span>  
 <span data-ttu-id="1e566-149">Dołączanie do procesu usługi umożliwia debugowanie najbardziej, ale nie wszystkie kod dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-149">Attaching to the service's process allows you to debug most, but not all, the code for that service.</span></span> <span data-ttu-id="1e566-150">Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w tej usłudze <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody lub kod w `Main` metodę, która jest używana do załadowania usługi w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="1e566-150">For example, because the service has already been started, you cannot debug the code in the service's <xref:System.ServiceProcess.ServiceBase.OnStart%2A> method or the code in the `Main` method that is used to load the service this way.</span></span> <span data-ttu-id="1e566-151">Jest jednym ze sposobów obejścia tego ograniczenia można utworzyć tymczasowej usługi drugi w aplikacji usługi, który istnieje tylko w celu ułatwienia debugowania.</span><span class="sxs-lookup"><span data-stu-id="1e566-151">One way to work around this limitation is to create a temporary second service in your service application that exists only to aid in debugging.</span></span> <span data-ttu-id="1e566-152">Można zainstalować obie usługi, a następnie uruchom tę usługę fikcyjny załadować procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-152">You can install both services, and then start this dummy service to load the service process.</span></span> <span data-ttu-id="1e566-153">Po rozpoczęciu procesu tymczasowej usługi można użyć **debugowania** menu programu Visual Studio, aby dołączyć do procesu usługi.</span><span class="sxs-lookup"><span data-stu-id="1e566-153">Once the temporary service has started the process, you can use the **Debug** menu in Visual Studio to attach to the service process.</span></span>  
  
 <span data-ttu-id="1e566-154">Spróbuj dodać wywołania <xref:System.Threading.Thread.Sleep%2A> metodę opóźnienie akcji, dopóki nie możesz dołączyć do procesu.</span><span class="sxs-lookup"><span data-stu-id="1e566-154">Try adding calls to the <xref:System.Threading.Thread.Sleep%2A> method to delay action until you’re able to attach to the process.</span></span>  
  
 <span data-ttu-id="1e566-155">Spróbuj zmienić program w aplikacji konsoli regularne.</span><span class="sxs-lookup"><span data-stu-id="1e566-155">Try changing the program to a regular console application.</span></span> <span data-ttu-id="1e566-156">Aby to zrobić, należy zmodyfikować `Main` w następujący sposób, dlatego można je uruchomić usługi systemu Windows oraz w aplikacji konsoli, w zależności od tego, jak została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="1e566-156">To do this, rewrite the `Main` method as follows so it can run both as a Windows Service and as a console application, depending on how it's started.</span></span>  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a><span data-ttu-id="1e566-157">Porady: uruchamianie usługi systemu Windows jako aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="1e566-157">How to: Run a Windows Service as a console application</span></span>  
  
1.  <span data-ttu-id="1e566-158">Dodaj metodę z uruchomioną usługą <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metod:</span><span class="sxs-lookup"><span data-stu-id="1e566-158">Add a method to your service that runs the <xref:System.ServiceProcess.ServiceBase.OnStart%2A> and <xref:System.ServiceProcess.ServiceBase.OnStop%2A> methods:</span></span>  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  <span data-ttu-id="1e566-159">Ponowne zapisywanie adresów `Main` metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1e566-159">Rewrite the `Main` method as follows:</span></span>  
  
    ```  
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
    ```  
  
3.  <span data-ttu-id="1e566-160">W **aplikacji** we właściwościach projektu ustaw **Output typu** do **aplikacji konsoli**.</span><span class="sxs-lookup"><span data-stu-id="1e566-160">In the **Application** tab of the project's properties, set the **Output type** to **Console Application**.</span></span>  
  
4.  <span data-ttu-id="1e566-161">Wybierz **Rozpocznij debugowanie** (F5).</span><span class="sxs-lookup"><span data-stu-id="1e566-161">Choose **Start Debugging** (F5).</span></span>  
  
5.  <span data-ttu-id="1e566-162">Aby ponownie uruchomić program jako usługa systemu Windows, należy go zainstalować i uruchomić go w zwykły sposób usługi systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1e566-162">To run the program as a Windows Service again, install it and start it as usual for a Windows Service.</span></span> <span data-ttu-id="1e566-163">Nie jest konieczne, aby odwrócić tych zmian.</span><span class="sxs-lookup"><span data-stu-id="1e566-163">It's not necessary to reverse these changes.</span></span>  
  
 <span data-ttu-id="1e566-164">W niektórych przypadkach, takich jak kiedy chcesz debugować problem, który występuje tylko podczas uruchamiania systemu należy użyć debugera systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1e566-164">In some cases, such as when you want to debug an issue that occurs only on system startup, you have to use the Windows debugger.</span></span> <span data-ttu-id="1e566-165">Zainstaluj [narzędzia do debugowania dla systemu Windows](http://msdn.microsoft.com/windows/hardware/hh852365) i zobacz [debugowanie usług systemu Windows](http://support.microsoft.com/kb/824344).</span><span class="sxs-lookup"><span data-stu-id="1e566-165">Install [Debugging Tools for Windows](http://msdn.microsoft.com/windows/hardware/hh852365) and see [How to debug Windows Services](http://support.microsoft.com/kb/824344).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e566-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1e566-166">See Also</span></span>  
 [<span data-ttu-id="1e566-167">Wprowadzenie do aplikacji usług systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1e566-167">Introduction to Windows Service Applications</span></span>](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [<span data-ttu-id="1e566-168">Instrukcje: instalowanie i odinstalowywanie usług</span><span class="sxs-lookup"><span data-stu-id="1e566-168">How to: Install and Uninstall Services</span></span>](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [<span data-ttu-id="1e566-169">Instrukcje: uruchamianie usług</span><span class="sxs-lookup"><span data-stu-id="1e566-169">How to: Start Services</span></span>](../../../docs/framework/windows-services/how-to-start-services.md)  
 [<span data-ttu-id="1e566-170">Debugowanie usługi</span><span class="sxs-lookup"><span data-stu-id="1e566-170">Debugging a Service</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
