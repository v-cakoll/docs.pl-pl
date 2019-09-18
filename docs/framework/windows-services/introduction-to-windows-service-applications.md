---
title: Wprowadzenie do aplikacji usług systemu Windows
ms.date: 03/30/2017
f1_keywords:
- ServiceController
helpviewer_keywords:
- Windows Service applications, deploying
- OnStop method
- OnPause method
- services, about services
- Service class, Windows Service applications
- framework services, creating services
- ServiceController components, about Windows services
- Win32OwnProcess service type
- services, lifetime
- OnContinue method
- Windows Service applications, about Windows Service applications
- services, states
- service states
- WaitForStatus method
- Win32ShareProcess service type
- Windows Service applications, lifetime
ms.assetid: 1b1b5e67-3ff3-40c0-8154-322cfd6ef0ae
author: ghogen
ms.openlocfilehash: 8ff1adaa025dc11417c3dcfdaf42ea203828be57
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053524"
---
# <a name="introduction-to-windows-service-applications"></a>Wprowadzenie do aplikacji usług systemu Windows
Usługi systemu Microsoft Windows, znane wcześniej jako usługi NT, umożliwiają tworzenie długotrwałych aplikacji wykonywalnych, które są uruchamiane w ich własnych sesjach systemu Windows. Te usługi mogą być uruchamiane automatycznie podczas uruchamiania komputera, mogą zostać wstrzymane i ponownie uruchomione i nie są wyświetlane żadne interfejsy użytkownika. Te funkcje sprawiają, że usługi są idealnym rozwiązaniem do użycia na serwerze, lub zawsze, gdy potrzebne są długotrwałe funkcje, które nie zakłócają innych użytkowników pracujących na tym samym komputerze. Można również uruchamiać usługi w kontekście zabezpieczeń określonego konta użytkownika, które różnią się od zalogowanego użytkownika lub domyślnego konta komputera. Więcej informacji o usługach i sesjach systemu Windows można znaleźć w dokumentacji Windows SDK.  
  
 Możesz łatwo tworzyć usługi, tworząc aplikację, która jest zainstalowana jako usługa. Załóżmy na przykład, że chcesz monitorować dane licznika wydajności i reagować na wartości progowe. Można napisać aplikację usługi systemu Windows, która nasłuchuje danych licznika wydajności, wdrożyć aplikację i rozpocząć zbieranie i analizowanie danych.  
  
 Tworzysz usługę jako projekt Microsoft Visual Studio, definiując w niej kod, który określa, jakie polecenia mogą być wysyłane do usługi i jakie akcje należy wykonać, gdy te polecenia są odbierane. Polecenia, które mogą być wysyłane do usługi, obejmują uruchamianie, wstrzymywanie, wznawianie i zatrzymywanie usługi; Możesz również wykonywać polecenia niestandardowe.  
  
 Po utworzeniu i skompilowaniu aplikacji można ją zainstalować przez uruchomienie narzędzia wiersza polecenia InstallUtil. exe i przekazanie ścieżki do pliku wykonywalnego usługi. Następnie można użyć **Menedżera sterowania usługami** , aby uruchomić, zatrzymać, wstrzymać, wznowić i skonfigurować usługę. Wiele z tych samych zadań można również wykonać w węźle **usługi** w **Eksplorator serwera** lub przy użyciu <xref:System.ServiceProcess.ServiceController> klasy.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikacje usług a Inne aplikacje Visual Studio  
 Aplikacje usługi działają inaczej niż wiele innych typów projektów na kilka sposobów:  
  
- Skompilowany plik wykonywalny tworzony przez projekt aplikacji usługi musi być zainstalowany na serwerze, aby projekt mógł działać w zrozumiały sposób. Nie można debugować lub uruchomić aplikacji usługi przez naciśnięcie klawisza F5 lub F11; nie można natychmiast uruchomić usługi lub przejść do jej kodu. Zamiast tego należy zainstalować i uruchomić usługę, a następnie dołączyć debuger do procesu usługi. Aby uzyskać więcej informacji, zobacz [jak: Debuguj aplikacje](how-to-debug-windows-service-applications.md)usług systemu Windows.  
  
- W odróżnieniu od niektórych typów projektów należy utworzyć składniki instalacyjne dla aplikacji usługi. Składniki instalacji instalują i rejestrują usługę na serwerze i tworzą wpis dla usługi za pomocą **Menedżera kontroli usług**systemu Windows. Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](how-to-add-installers-to-your-service-application.md)usługi.  
  
- `Main` Metoda aplikacji usługi musi wydać polecenie uruchomienia dla usług, które zawiera projekt. Metoda ładuje usługi do **Menedżera kontroli usług** na odpowiednim serwerze. `Run` Jeśli używasz szablonu projektu **usług systemu Windows** , ta metoda jest automatycznie zapisywana. Należy zauważyć, że ładowanie usługi nie jest takie samo jak uruchamianie usługi. Aby uzyskać więcej informacji, zobacz "okres istnienia usługi" poniżej.  
  
- Aplikacje usług systemu Windows działają w innej stacji okna niż interaktywna stacja zalogowanego użytkownika. Stacja okien jest zabezpieczonym obiektem, który zawiera Schowek, zestaw globalnych atomów i grupę obiektów pulpitu. Ponieważ stacja usługi systemu Windows nie jest stacją interaktywną, okna dialogowe wywoływane z poziomu aplikacji usługi systemu Windows nie będą widoczne i mogą spowodować, że program przestanie odpowiadać. Podobnie komunikaty o błędach powinny być rejestrowane w dzienniku zdarzeń systemu Windows, a nie zgłaszane w interfejsie użytkownika.  
  
     Klasy usług systemu Windows obsługiwane przez .NET Framework nie obsługują interakcji z stacjami interaktywnymi, czyli zalogowanym użytkownikiem. .NET Framework również nie obejmuje klas, które reprezentują stacje i komputery stacjonarne. Jeśli usługa systemu Windows musi współistnieć z innymi stacjami, trzeba będzie uzyskać dostęp do niezarządzanego interfejsu API systemu Windows. Aby uzyskać więcej informacji, zobacz dokumentację Windows SDK.  
  
     Interakcja usługi systemu Windows z użytkownikiem lub innymi stacjami musi być starannie zaprojektowana w taki sposób, aby obejmowała takie scenariusze, jak nie ma zalogowanego użytkownika lub użytkownik ma nieoczekiwany zestaw obiektów pulpitu. W niektórych przypadkach może być bardziej odpowiednie do napisania aplikacji systemu Windows, która działa pod kontrolą użytkownika.  
  
- Aplikacje usług systemu Windows działają w ich własnym kontekście zabezpieczeń i są uruchamiane przed zalogowaniem się użytkownika do komputera z systemem Windows, na którym są zainstalowane. Należy zaplanować dokładne konto użytkownika, w ramach którego ma zostać uruchomiona usługa; Usługa uruchomiona na koncie systemowym ma więcej uprawnień i uprawnień niż konto użytkownika.  
  
## <a name="service-lifetime"></a>Okres istnienia usługi  
 Usługa przechodzi przez kilka stanów wewnętrznych w swoim okresie istnienia. Najpierw usługa jest instalowana w systemie, w którym zostanie uruchomiona. Ten proces wykonuje Instalatory dla projektu usługi i ładuje usługę do **Menedżera kontroli usług** dla tego komputera. **Menedżer sterowania usługami** jest centralnym narzędziem udostępnianym przez system Windows do administrowania usługami.  
  
 Po załadowaniu usługi należy ją uruchomić. Uruchomienie usługi pozwala na rozpoczęcie działania. Usługę można uruchomić z poziomu **Menedżera kontroli usług**, z **Eksplorator serwera**lub z kodu, wywołując <xref:System.ServiceProcess.ServiceController.Start%2A> metodę. Metoda przekazuje przetwarzanie do <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody aplikacji i przetwarza kod, który został tam zdefiniowany. <xref:System.ServiceProcess.ServiceController.Start%2A>  
  
 Uruchomiona usługa może istnieć w tym stanie w nieskończoność, dopóki nie zostanie zatrzymana lub wstrzymana lub dopóki komputer nie zostanie zamknięty. Usługa może istnieć w jednym z trzech stanów podstawowych: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, lub <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Usługa może również zgłosić <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>stan oczekującego polecenia:, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>lub <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Te Stany wskazują, że polecenie zostało wystawione, na przykład polecenie wstrzymania uruchomionej usługi, ale nie zostało jeszcze wykonane. Można wykonać zapytanie w <xref:System.ServiceProcess.ServiceController.Status%2A> celu określenia stanu usługi lub <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> użyć, aby wykonać akcję w przypadku wystąpienia któregokolwiek z tych stanów.  
  
 Usługę można wstrzymywać, zatrzymywać i wznawiać z poziomu **Menedżera kontroli usług**, z poziomu **Eksplorator serwera**lub wywołując metody w kodzie. Każda z tych akcji może wywołać skojarzoną procedurę w usłudze (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>lub <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), w której można zdefiniować dodatkowe przetwarzanie, które ma zostać wykonane po zmianie stanu usługi.  
  
## <a name="types-of-services"></a>Typy usług  
 Istnieją dwa typy usług, które można utworzyć w programie Visual Studio przy użyciu .NET Framework. Do usług, które są jedyną usługą w procesie, przypisywany jest <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>typ. Do usług, które współużytkują proces z inną usługą, <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>przypisywany jest typ. Typ usługi można pobrać, wykonując zapytania dotyczące <xref:System.ServiceProcess.ServiceController.ServiceType%2A> właściwości.  
  
 W przypadku wykonywania zapytań dotyczących istniejących usług, które nie zostały utworzone w programie Visual Studio, mogą czasami być widoczne inne typy usług. Aby uzyskać więcej informacji na ten temat, <xref:System.ServiceProcess.ServiceType>Zobacz.  
  
## <a name="services-and-the-servicecontroller-component"></a>Usługi i składnik ServiceController  
 Składnik jest używany do nawiązywania połączenia z zainstalowaną usługą i manipulowania jej stanem. <xref:System.ServiceProcess.ServiceController> za pomocą składnika można uruchamiać i zatrzymywać usługę, wstrzymywać i kontynuować działanie oraz wysyłać polecenia niestandardowe do usługi. <xref:System.ServiceProcess.ServiceController> Nie trzeba jednak używać <xref:System.ServiceProcess.ServiceController> składnika podczas tworzenia aplikacji usługi. W rzeczywistości w większości przypadków <xref:System.ServiceProcess.ServiceController> składnik powinien znajdować się w osobnej aplikacji z poziomu aplikacji usługi systemu Windows, która definiuje swoją usługę.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Wymagania  
  
- Usługi muszą zostać utworzone w projekcie aplikacji **usługi systemu Windows** lub w innym projekcie z obsługą .NET Framework, który tworzy plik. exe po skompilowaniu i <xref:System.ServiceProcess.ServiceBase> dziedziczeniu z klasy.  
  
- Projekty zawierające usługi systemu Windows muszą mieć składniki instalacyjne dla projektu i jego usług. Można to łatwo zrobić w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [jak: Dodaj Instalatory do aplikacji](how-to-add-installers-to-your-service-application.md)usługi.  
  
## <a name="see-also"></a>Zobacz także

- [Aplikacje usług systemu Windows](index.md)
- [Architektura programowania aplikacji usług](service-application-programming-architecture.md)
- [Instrukcje: Tworzenie usług systemu Windows](how-to-create-windows-services.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](how-to-install-and-uninstall-services.md)
- [Instrukcje: Uruchom usługi](how-to-start-services.md)
- [Instrukcje: Debuguj aplikacje usług systemu Windows](how-to-debug-windows-service-applications.md)
- [Przewodnik: Tworzenie aplikacji usługi systemu Windows w projektancie składników](walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Instrukcje: Dodawanie instalatorów do aplikacji usługi](how-to-add-installers-to-your-service-application.md)
