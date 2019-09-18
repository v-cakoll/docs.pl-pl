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
ms.openlocfilehash: 860f2ae22eb6510dc1f1a454ae3e51ccb366078b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053627"
---
# <a name="how-to-debug-windows-service-applications"></a>Instrukcje: Debugowanie aplikacji usług systemu Windows
Usługa musi być uruchomiona w kontekście menedżera kontroli usług, a nie z poziomu programu Visual Studio. Z tego powodu debugowanie usługi nie jest tak proste jak debugowanie innych typów aplikacji programu Visual Studio. Aby debugować usługę, należy ją uruchomić, a następnie dołączyć debuger do procesu, w którym jest uruchomiony. Następnie można debugować aplikację przy użyciu wszystkich standardowych funkcji debugowania programu Visual Studio.  
  
> [!CAUTION]
> Nie należy dołączać do procesu, chyba że wiesz, co to jest proces, i zrozumieć konsekwencje dołączenia do tego procesu i prawdopodobnie go zabijania. Na przykład jeśli dołączysz do procesu WinLogon, a następnie zatrzymasz debugowanie, system zostanie zatrzymany, ponieważ nie może działać bez usługi WinLogon.  
  
 Debuger można dołączyć tylko do działającej usługi. Proces załącznika przerywa bieżące działanie usługi; w rzeczywistości nie zatrzymuje ani nie wstrzymuje przetwarzania usługi. Oznacza to, że jeśli usługa jest uruchomiona po rozpoczęciu debugowania, nadal jest technicznie w stanie uruchomienia podczas debugowania, ale jego przetwarzanie zostało wstrzymane.  
  
 Po dołączeniu do procesu można ustawić punkty przerwania i użyć ich do debugowania kodu. Po opuszczeniu okna dialogowego, którego używasz do dołączania do procesu, Pracujesz w trybie debugowania. Można użyć Menedżera sterowania usługami, aby uruchomić, zatrzymać, wstrzymać i kontynuować usługę, a tym samym ustawić punkty przerwania, które ustawisz. Możesz później usunąć tę fikcyjną usługę po pomyślnym zakończeniu debugowania.  
  
 W tym artykule opisano debugowanie usługi, która jest uruchomiona na komputerze lokalnym, ale można również debugować usługi systemu Windows, które są uruchomione na komputerze zdalnym. Zobacz [debugowanie zdalne](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
> <xref:System.ServiceProcess.ServiceBase.OnStart%2A> Debugowanie metody może być trudne, ponieważ Menedżer kontroli usług nakłada limit 30 sekund na wszystkie próby uruchomienia usługi. Aby uzyskać więcej informacji, [zobacz Rozwiązywanie problemów: Debugowanie usług](troubleshooting-debugging-windows-services.md)systemu Windows.  
  
> [!WARNING]
> Aby uzyskać istotne informacje na potrzeby debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla debugowanych plików binarnych. W przypadku debugowania usługi skompilowanej w programie Visual Studio pliki symboli (pliki. pdb) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka, a debuger ładuje je automatycznie. W przypadku debugowania nieskompilowanej usługi należy najpierw znaleźć symbole usługi i upewnić się, że są one dostępne przez debuger. Zobacz [Określanie symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger). Jeśli debugujesz proces systemowy lub chcesz mieć symbole dla wywołań systemowych w usługach, należy dodać serwery symboli Microsoft. Zobacz [debugowanie symboli](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Aby debugować usługę  
  
1. Kompiluj swoją usługę w konfiguracji debugowania.  
  
2. Zainstaluj usługę. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie](how-to-install-and-uninstall-services.md)usług.  
  
3. Uruchom usługę z **Menedżera sterowania usługami**, **Eksplorator serwera**lub z kodu. Aby uzyskać więcej informacji, zobacz [jak: Uruchom usługi](how-to-start-services.md).  
  
4. Uruchom program Visual Studio z poświadczeniami administracyjnymi, aby umożliwić dołączenie do procesów systemowych.  
  
5. Obowiązkowe Na pasku menu programu Visual Studio wybierz **Narzędzia**, **Opcje**. W oknie dialogowym **Opcje** wybierz pozycję **debugowanie**, **symbole**, zaznacz pole wyboru **serwery symboli firmy Microsoft** , a następnie wybierz przycisk **OK** .  
  
6. Na pasku menu wybierz polecenie **Dołącz do procesu** z menu **debugowanie** lub **Narzędzia** . Klawiatury Ctrl+Alt+P)  
  
     Zostanie wyświetlone okno dialogowe **procesy** .  
  
7. Zaznacz pole wyboru **Pokaż procesy wszystkich użytkowników** .  
  
8. W sekcji **dostępne procesy** wybierz proces dla usługi, a następnie wybierz pozycję **Dołącz**.  
  
    > [!TIP]
    > Ten proces będzie mieć taką samą nazwę jak plik wykonywalny dla usługi.  
  
     **Dołączyć do procesu** pojawi się okno dialogowe.  
  
9. Wybierz odpowiednie opcje, a następnie kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
    > [!NOTE]
    > Jesteś teraz w trybie debugowania.  
  
10. Ustaw wszystkie punkty przerwania, które mają być używane w kodzie.  
  
11. Dostęp do Menedżera sterowania usługami i manipulowanie usługą, wysyłanie poleceń Zatrzymaj, Wstrzymaj i Kontynuuj, aby trafiać z punktów przerwania. Aby uzyskać więcej informacji na temat uruchamiania Menedżera sterowania usługami, [zobacz How to: Uruchom usługi](how-to-start-services.md). Zobacz [również Rozwiązywanie problemów: Debugowanie usług](troubleshooting-debugging-windows-services.md)systemu Windows.  
  
## <a name="debugging-tips-for-windows-services"></a>Wskazówki dotyczące debugowania dla usług systemu Windows  
 Dołączenie do procesu usługi pozwala debugować większość, ale nie wszystkie, kod dla tej usługi. Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metodzie usługi lub kodzie `Main` w metodzie, która jest używana do załadowania usługi w ten sposób. Jednym ze sposobów obejścia tego ograniczenia jest utworzenie tymczasowej drugiej usługi w aplikacji usługi, która istnieje tylko w celu ułatwienia debugowania. Można zainstalować obie usługi, a następnie uruchomić tę fikcyjną usługę w celu załadowania procesu usługi. Po rozpoczęciu procesu przez usługę tymczasową możesz użyć menu **Debuguj** w programie Visual Studio w celu dołączenia do procesu usługi.  
  
 Spróbuj dodać wywołania metody, <xref:System.Threading.Thread.Sleep%2A> aby opóźnić akcję do momentu dołączenia do procesu.  
  
 Spróbuj zmienić program na zwykłą aplikację konsolową. W tym celu należy napisać ponownie `Main` metodę w następujący sposób, aby można było ją uruchomić zarówno jako usługę systemu Windows, jak i jako aplikację konsolową, w zależności od sposobu jej uruchomienia.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Instrukcje: Uruchamianie usługi systemu Windows jako aplikacji konsolowej  
  
1. Dodaj metodę do usługi, która uruchamia <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i: <xref:System.ServiceProcess.ServiceBase.OnStop%2A>  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2. Napisz ponownie `Main` metodę w następujący sposób:  
  
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
  
3. Na karcie **aplikacja** we właściwościach projektu Ustaw **Typ danych wyjściowych** na **Aplikacja konsolowa**.  
  
4. Wybierz **Rozpocznij debugowanie** (F5).  
  
5. Aby ponownie uruchomić program jako usługę systemu Windows, zainstaluj go i uruchom jak zwykle w przypadku usługi systemu Windows. Nie trzeba odwrócić tych zmian.  
  
 W niektórych przypadkach, na przykład gdy chcesz debugować problem, który występuje tylko podczas uruchamiania systemu, musisz użyć debugera systemu Windows. [Pobierz zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/download-the-wdk) i zobacz, [jak debugować usługi systemu Windows](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do aplikacji usług systemu Windows](introduction-to-windows-service-applications.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md)
- [Instrukcje: Uruchom usługi](how-to-start-services.md)
- [Debugowanie usługi](/windows/desktop/Services/debugging-a-service)
