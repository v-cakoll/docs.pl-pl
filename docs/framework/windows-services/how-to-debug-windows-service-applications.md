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
ms.openlocfilehash: 02ea82bf224349e6ea7a5afbfb3c38ba50df46f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720369"
---
# <a name="how-to-debug-windows-service-applications"></a>Instrukcje: Debugowanie aplikacji usług Windows
Usługa musi być uruchamiane w kontekście Menedżera sterowania usługami, a nie z poziomu programu Visual Studio. Z tego powodu debugowanie usługi jest tak proste jak debugowanie innych typów aplikacji Visual Studio. Aby debugować usługę, należy uruchomić usługę i następnie dołączyć debuger do procesu, w którym jest uruchomiony. Następnie można debugować aplikację za pomocą wszystkich standardowych funkcji debugowania programu Visual Studio.  
  
> [!CAUTION]
>  Nie należy dołączać do procesu, chyba że wiesz, co ten proces i rozumiesz, jakie skutki dołączenia i ewentualne skutki zniszczenia tego procesu. Na przykład jeśli dołączyć do procesu WinLogon, a następnie zatrzymasz debugowanie, system zatrzyma się, ponieważ nie może działać bez usługi WinLogon.  
  
 Można dołączyć debuger, tylko do czynnej usługi. Proces załącznika przerywa bieżące działanie usługi; faktycznie nie zatrzymać lub wstrzymać przetwarzania usługi. Oznacza to jeśli usługa jest uruchomiona, po rozpoczęciu debugowania, jest technicznie nadal w stanie uruchomiona podczas jej debugowania, ale jej przetwarzanie jest wstrzymane.  
  
 Po dołączeniu do procesu, możesz ustawić punkty przerwania i ich użyć do debugowania kodu. Po zamknięciu okna dialogowego, które służy do dołączania do procesu, jesteś w trybie debugowania. Aby uruchomić, zatrzymać, wstrzymać lub kontynuować usługę, w tym samym osiągając ustawione punkty przerwania, można użyć Menedżera sterowania usługami. Po pomyślnym debugowaniu, można później usunąć tę fikcyjną usługę.  
  
 W tym artykule opisano profilowanie to usługa, która jest uruchomiona na komputerze lokalnym, ale można również debugować usług Windows, które są uruchomione na komputerze zdalnym. Zobacz [zdalne debugowanie](/visualstudio/debugger/debug-installed-app-package).  
  
> [!NOTE]
>  Debugowanie <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metoda może być trudne, ponieważ Menedżera sterowania usługami nakłada limit 30-sekundowy na wszystkie próby uruchomienia usługi. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów: Debugowanie usług Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
> [!WARNING]
>  Aby uzyskać istotne informacje dotyczące debugowania, debuger programu Visual Studio musi znaleźć pliki symboli dla plików binarnych, które są debugowane. Jeśli debugujesz to usługa, która jest wbudowana w programie Visual Studio, plików symboli (pliki .pdb) znajdują się w tym samym folderze co plik wykonywalny lub biblioteka i debuger ładuje je automatycznie. Jeśli debugujesz usługa, która nie została skompilowana, należy najpierw Znajdź symbole dla usługi i upewnij się, że są one przez debuger. Zobacz [Określ symboli (.pdb) i pliki źródłowe](https://msdn.microsoft.com/library/1105e169-5272-4e7c-b3e7-cda1b7798a6b). Jeśli debugowanie procesów systemowych lub mają symbole dla wywołania systemowe w usługach, należy dodać serwery symboli firmy Microsoft. Zobacz [symboli debugowania](/windows/desktop/DxTechArts/debugging-with-symbols).  
  
### <a name="to-debug-a-service"></a>Aby debugować usługę  
  
1.  Tworzenie usługi w konfiguracji debugowania.  
  
2.  Zainstaluj swoje usługi. Aby uzyskać więcej informacji, zobacz [jak: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md).  
  
3.  Uruchom usługę z **Menedżera sterowania usługami**, **Eksploratora serwera**, lub z kodu. Aby uzyskać więcej informacji, zobacz [jak: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md).  
  
4.  Uruchom program Visual Studio przy użyciu poświadczeń administracyjnych, dzięki czemu możesz dołączyć do procesów systemowych.  
  
5.  (Opcjonalnie) Na pasku menu programu Visual Studio, wybierz **narzędzia**, **opcje**. W **opcje** okna dialogowego wybierz **debugowanie**, **symbole**, wybierz opcję **serwery symboli firmy Microsoft** pole wyboru, a następnie wybierz pozycję **OK** przycisku.  
  
6.  Na pasku menu wybierz **dołączyć do procesu** z **debugowania** lub **narzędzia** menu. (Klawiatura: Ctrl+Alt+P)  
  
     **Procesy** pojawi się okno dialogowe.  
  
7.  Wybierz **Pokaż procesy wszystkich użytkowników** pole wyboru.  
  
8.  W **dostępne procesy** sekcji, wybierz proces danej usługi, a następnie wybierz **Dołącz**.  
  
    > [!TIP]
    >  Proces będzie mieć taką samą nazwę jak plik wykonywalny dla usługi.  
  
     **Dołączyć do procesu** pojawi się okno dialogowe.  
  
9. Wybierz odpowiednie opcje, a następnie wybierz **OK** aby zamknąć okno dialogowe.  
  
    > [!NOTE]
    >  Jesteś teraz w trybie debugowania.  
  
10. Ustaw wszelkie punkty przerwania, którego chcesz użyć w kodzie.  
  
11. Dostęp do Menedżera sterowania usługami i manipulowania Twojej usługi, wysyłając polecenia Zatrzymaj, Wstrzymaj i Kontynuuj do punktów przerwania. Aby uzyskać więcej informacji na temat uruchamiania Menedżera sterowania usługami, zobacz [jak: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md). Zobacz też [Rozwiązywanie problemów: Debugowanie usług Windows](../../../docs/framework/windows-services/troubleshooting-debugging-windows-services.md).  
  
## <a name="debugging-tips-for-windows-services"></a>Wskazówki dotyczące debugowania dla usług Windows  
 Dołączanie do procesu usługi pozwala debugować większość, ale nie wszystkie kod dla tej usługi. Na przykład, ponieważ usługa została już uruchomiona, nie można debugować kodu w usłudze <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody lub kod w `Main` metodę, która jest używana do ładowania usługi w ten sposób. Jednym ze sposobów obejścia tego ograniczenia jest utworzyć tymczasowej drugiej usługi w aplikacji usługi, która istnieje tylko do pomocy w debugowaniu. Można zainstalować obie usługi, a następnie uruchom tę fikcyjną usługę, aby załadować procesu usługi. Po rozpoczęciu procesu tymczasowej usługi można użyć **debugowania** menu w programie Visual Studio, aby dołączyć do procesu usługi.  
  
 Spróbuj dodać wywołania <xref:System.Threading.Thread.Sleep%2A> metody akcji opóźniania, dopóki nie można dołączyć do procesu.  
  
 Spróbuj zmienić program w aplikacji konsolowej regularne. Aby to zrobić, napisz ponownie `Main` metody w następujący sposób, dzięki czemu może działać jako usługa Windows i jako aplikację konsolową w języku, w zależności od sposobu uruchamiania.  
  
#### <a name="how-to-run-a-windows-service-as-a-console-application"></a>Instrukcje: Uruchom usługę Windows jako aplikację konsolową w języku  
  
1.  Dodaj metodę z uruchomioną usługą <xref:System.ServiceProcess.ServiceBase.OnStart%2A> i <xref:System.ServiceProcess.ServiceBase.OnStop%2A> metody:  
  
    ```csharp  
    internal void TestStartupAndStop(string[] args)  
    {  
        this.OnStart(args);  
        Console.ReadLine();  
        this.OnStop();  
    }  
    ```  
  
2.  Ponowne zapisywanie adresów `Main` metody w następujący sposób:  
  
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
  
3.  W **aplikacji** na karcie właściwości projektu, ustaw **typ danych wyjściowych** do **aplikację Konsolową**.  
  
4.  Wybierz **Rozpocznij debugowanie** (F5).  
  
5.  Aby ponownie uruchomić program jako usługę Windows, należy go zainstalować i uruchomić go w zwykły sposób usługi Windows. Nie jest konieczne zmiany można cofnąć.  
  
 W niektórych przypadkach, np. Jeśli chcesz debugować problem, który występuje tylko podczas uruchamiania systemu należy użyć debugera Windows. Zainstaluj [Debugging Tools for Windows](https://msdn.microsoft.com/windows/hardware/hh852365) zobaczyć [sposób debugowania usług Windows](https://support.microsoft.com/kb/824344).  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do aplikacji usług systemu Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Instrukcje: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)
- [Debugowanie usługi](/windows/desktop/Services/debugging-a-service)
