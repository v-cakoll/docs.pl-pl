---
title: "Porady: debugowanie aplikacji usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging Windows Service applications
- debugging [Visual Studio], Windows services
- Windows NT services, debugging
- Windows Service applications, debugging
- services, debugging
ms.assetid: 63ab0800-0f05-4f1e-88e6-94c73fd920a2
caps.latest.revision: "16"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 86d90e4129f089a77e51e6e58233a1087fe5d0f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-debug-windows-service-applications"></a>Porady: debugowanie aplikacji usług systemu Windows
Usługa musi być uruchamiane w kontekście Menedżera sterowania usługami, a nie z poziomu programu Visual Studio. Z tego powodu debugowania usługi nie jest równie proste jak debugowanie różnych typów aplikacji Visual Studio. Aby debugować usługi, należy uruchomić usługę i następnie dołączyć do procesu, w którym jest uruchomiony. Można następnie Debuguj aplikację przy użyciu wszystkich standardowych funkcji debugowania programu Visual Studio.  
  
> [!CAUTION]
>  Należy nie dołączyć procesu, jeśli nie masz pewności, co proces jest i konsekwencje związane z a prawdopodobnie skasowanie tego procesu. Na przykład jeśli dołączyć do procesu logowania do systemu Windows, a następnie zatrzymać debugowanie, system zostanie zatrzymany, ponieważ nie może działać bez usługi WinLogon.  
  
 Tylko do uruchomionej usługi można dołączyć debugera. Przerywa proces załącznika bieżącego działania usługi; faktycznie nie zatrzymać lub wstrzymać przetwarzania usługi. Oznacza to jeśli usługa jest uruchomiona, po rozpoczęciu debugowania, jest nadal technicznie w stanie uruchomiono jego debugowania, ale jego przetwarzanie zostało zawieszone.  
  
 Po dołączeniu do procesu, można ustawić punktów przerwania i ich używać do debugowania kodu. Po zamknięciu okna dialogowego, który służy do dołączania do procesu jesteś skutecznie w trybie debugowania. W Menedżerze sterowania usługami umożliwia uruchamianie, zatrzymywanie, wstrzymywanie i kontynuować usługi, w związku z tym naciśnięcie punktów przerwania ustawionych. Później można usunąć tej usługi fikcyjny po debugowania zakończy się pomyślnie.  
  
 W tym artykule omówiono debugowania to usługa, która jest uruchomiona na komputerze lokalnym, ale również można debugować usług systemu Windows, które są uruchomione na komputerze zdalnym. Zobacz [zdalnego debugowania](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Debugowanie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda może być trudne, ponieważ Menedżera sterowania usługami związany z ograniczeniem 30 sekund na wszystkie próby uruchomienia usługi. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów: debugowanie usług systemu Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Aby uzyskać przydatne informacje dotyczące debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla danych binarnych, które są debugowane. Jeśli debugujesz usługi, które zostały utworzone w programie Visual Studio, plików symboli (.pdb, pliki) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka i debuger ładuje je automatycznie. Jeśli usługa, która nie kompilacji debugowania, należy najpierw odnaleźć symboli dla usługi i upewnij się, że są one przez debuger. Zobacz [Określ symboli (.pdb) i pliki źródłowe](http://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Jeśli debugowanie procesów systemowych lub mają symboli dla wywołań systemowych w usługach, należy dodać serwerów symboli firmy Microsoft. Zobacz [symbole debugowania](http://msdn.microsoft.com/windows/desktop/ee416588.aspx).  
  
### <a name="to-debug-a-service"></a>Aby debugować usługi  
  
1.  Tworzenie usługi w konfiguracji debugowania.  
  
2.  Zainstaluj usługi. Aby uzyskać więcej informacji, zobacz [porady: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Uruchomić usługę, albo z **Menedżera sterowania usługami**, **Eksploratora serwera**, lub z kodu. Aby uzyskać więcej informacji, zobacz [porady: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, więc można dołączyć do procesów systemowych.  
  
5.  (Opcjonalnie) Na pasku menu programu Visual Studio wybierz **narzędzia**, **opcje**. W **opcje** oknie dialogowym wybierz **debugowanie**, **symbole**, wybierz pozycję **serwerów symboli firmy Microsoft** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Na pasku menu wybierz **dołączyć do procesu** z **debugowania** lub **narzędzia** menu. (Klawiatury: Ctrl + Alt + P)  
  
     **Procesów** zostanie wyświetlone okno dialogowe.  
  
7.  Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
8.  W **dostępne procesy** sekcji, wybierz proces usługi, a następnie wybierz pozycję **Attach**.  
  
    > [!TIP]
    >  Proces ma taką samą nazwę jak plik wykonywalny dla usługi.  
  
     **Dołączyć do procesu** zostanie wyświetlone okno dialogowe.  
  
9. Wybierz odpowiednie opcje, a następnie wybierz **OK** aby zamknąć okno dialogowe.  
  
    > [!NOTE]
    >  Jesteś teraz w trybie debugowania.  
  
10. Ustaw wszystkie punkty przerwania, który ma być używany w kodzie.  
  
11. Dostęp do Menedżera sterowania usługami manipulowania Twojej usługi, wysyłania Zatrzymaj, Wstrzymaj i Kontynuuj polecenia trafienie punkty przerwań. Aby uzyskać więcej informacji dotyczących uruchamiania Menedżera kontroli usług, zobacz [porady: Uruchom usługi](../../../docs/framework/windows-services/how-to-start-services.md). Zobacz też [Rozwiązywanie problemów: debugowanie usług systemu Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Debugowanie porady dla usług systemu Windows  
 Dołączanie do procesu usługi umożliwia debugowanie najbardziej, ale nie wszystkie kod dla tej usługi. Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w tej usłudze <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody lub kod w `Main` metodę, która jest używana do załadowania usługi w ten sposób. Jest jednym ze sposobów obejścia tego ograniczenia można utworzyć tymczasowej usługi drugi w aplikacji usługi, który istnieje tylko w celu ułatwienia debugowania. Można zainstalować obie usługi, a następnie uruchom tę usługę fikcyjny załadować procesu usługi. Po rozpoczęciu procesu tymczasowej usługi można użyć **debugowania** menu programu Visual Studio, aby dołączyć do procesu usługi.  
  
 Spróbuj dodać wywołania <xref:System.Threading.Thread.Sleep%2A> metodę opóźnienie akcji, dopóki nie możesz dołączyć do procesu.  
  
 Spróbuj zmienić program w aplikacji konsoli regularne. Aby to zrobić, należy zmodyfikować `Main` w następujący sposób, dlatego można je uruchomić usługi systemu Windows oraz w aplikacji konsoli, w zależności od tego, jak została uruchomiona.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Porady: uruchamianie usługi systemu Windows jako aplikacji konsoli  
  
1.  Dodaj metodę z uruchomioną usługą <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metod:  
  
    ```  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Ponowne zapisywanie adresów `Main` metody w następujący sposób:  
  
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
  
3.  W **aplikacji** we właściwościach projektu ustaw **Output typu** do **aplikacji konsoli**.  
  
4.  Wybierz **Rozpocznij debugowanie** (F5).  
  
5.  Aby ponownie uruchomić program jako usługa systemu Windows, należy go zainstalować i uruchomić go w zwykły sposób usługi systemu Windows. Nie jest konieczne, aby odwrócić tych zmian.  
  
 W niektórych przypadkach, takich jak kiedy chcesz debugować problem, który występuje tylko podczas uruchamiania systemu należy użyć debugera systemu Windows. Zainstaluj [narzędzia do debugowania dla systemu Windows](http://msdn.microsoft.com/windows/hardware/hh852365) i zobacz [debugowanie usług systemu Windows](http://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Instrukcje: instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Instrukcje: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Debugowanie usługi](http://msdn.microsoft.com/library/windows/desktop/ms682546.aspx)
