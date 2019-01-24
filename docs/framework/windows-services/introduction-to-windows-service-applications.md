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
ms.openlocfilehash: b26186ccf4a773297db89026797e89f194db2aa4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614422"
---
# <a name="introduction-to-windows-service-applications"></a>Wprowadzenie do aplikacji usług systemu Windows
Usługi Microsoft Windows, znana wcześniej jako usługi NT, umożliwiają tworzenie długotrwałych wykonywalny aplikacji, które działają w ich własnych sesjach Windows. Te usługi mogą być uruchamiane automatycznie podczas rozruchu komputera, mogą być wstrzymywane i ponownie uruchomiony i nie wyświetlają żadnego interfejsu użytkownika. Te funkcje idealnym rozwiązaniem usługi do użycia na serwerze lub w przypadku, gdy potrzebujesz długo działających funkcji, które nie kolidują z innymi użytkownikami pracującymi na tym samym komputerze. Można również uruchomić usługi w kontekście zabezpieczeń konta określonego użytkownika, który jest inny niż zalogowany użytkownik lub domyślne konto komputera. Aby uzyskać więcej informacji o usługach i sesjach Windows zobacz dokumentację zestawu Windows SDK.  
  
 Możesz łatwo tworzyć usługi, tworząc aplikację, która jest instalowana jako usługa. Na przykład załóżmy, że chcesz monitorować dane licznika wydajności i reagowanie na wartości progowe. Można napisać aplikację Windows Service, która nasłuchuje dane licznika wydajności, Wdróż aplikację i rozpocząć zbieranie i analizowanie danych.  
  
 Utwórz usługę jako projekt programu Microsoft Visual Studio, definiując znajdujący się w nim kod, który określa, jakie polecenia mogą być wysyłane do usługi i jakie działania powinny zostać podjęte, po otrzymaniu tych poleceń. Polecenia, które mogą być wysyłane do usługi obejmują uruchamianie, wstrzymywanie, wznawianie i zatrzymywanie usługi; można również wykonać polecenia niestandardowe.  
  
 Po utworzeniu i skompilowaniu aplikacji, należy ją zainstalować, uruchamiając narzędzie wiersza polecenia InstallUtil.exe i przekazanie ścieżki do pliku wykonywalnego usługi. Następnie można użyć **Menedżera sterowania usługami** na uruchamianie, zatrzymywanie, wstrzymywanie, wznawianie i skonfigurować usługę. Można również wykonać wiele tych samych zadań z **usług** w węźle **Eksploratora serwera** lub za pomocą <xref:System.ServiceProcess.ServiceController> klasy.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikacje usług vs. Inne aplikacje programu Visual Studio  
 Funkcja aplikacji usług różni się od wielu innych typów projektów, na kilka sposobów:  
  
-   Skompilowany plik wykonywalny, który tworzy projekt aplikacji usługi musi być zainstalowany na serwerze zanim projekt mógł działać w znaczący sposób. Nie można debugować lub uruchomić aplikacji usługi, naciskając klawisz F5 lub F11; Nie można natychmiast uruchomić usługi lub wejść w jej kod. Zamiast tego należy zainstalować i uruchom usługę i następnie dołączyć debuger do procesu usługi. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie aplikacji usług Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   W odróżnieniu od niektórych typów projektów należy utworzyć składniki instalacyjne dla aplikacji usług. Składniki instalacji Zainstaluj i rejestrują usługę na serwerze i tworzą wpis dla usługi przy użyciu Windows **Menedżera sterowania usługami**. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Metoda dla aplikacji usługi musi wydać polecenie Uruchom dla usług projektu zawiera. `Run` Metoda ładuje usługi do **Menedżera sterowania usługami** na odpowiednim serwerze. Jeśli używasz **usług Windows** szablon projektu, ta metoda jest napisana dla Ciebie automatycznie. Należy pamiętać, że ładowanie usługi nie jest tym samym co uruchamianie usługi. Zobacz "Okres istnienia usługi" poniżej Aby uzyskać więcej informacji.  
  
-   Usługa Windows aplikacje uruchamiane w innej stacji okna niż interaktywna stacja zalogowanego użytkownika. Stacja jest zabezpieczonym obiektem, który zawiera Schowek, zestaw globalnych atomów i grupę obiektów pulpitu. Ponieważ stacja usługi Windows nie jest stacją interaktywną, okna dialogowe wywoływane w w Windows aplikacja usługi nie będą widoczne i mogą spowodować, że program przestanie odpowiadać. Podobnie komunikaty o błędach powinny być rejestrowane w dzienniku zdarzeń Windows zamiast zgłoszone w interfejsie użytkownika.  
  
     Klasy usług Windows, które są obsługiwane przez program .NET Framework nie obsługują interakcji ze stacjami interaktywnymi, czyli zalogowanego użytkownika. .NET Framework nie zawiera również klasy reprezentującej stacje i komputery stacjonarne. Jeśli usługa Windows musi współdziałać z innymi stacjami, konieczne będzie dostęp do niezarządzanego interfejsu API Windows. Aby uzyskać więcej informacji zobacz dokumentację zestawu Windows SDK.  
  
     Interakcja Windows service z użytkownikiem lub innymi stacjami należy starannie zaprojektować, uwzględniając takie scenariusze jak istnienie niezalogowanego lub użytkownika mającego nieoczekiwany zestaw obiektów pulpitu. W niektórych przypadkach może być bardziej odpowiednie napisanie aplikacji Windows, która działa pod kontrolą użytkownika.  
  
-   Aplikacje usługi Windows działają w kontekstu zabezpieczeń i są uruchamiane przed zalogowaniem użytkownika do systemu Windows, na którym są zainstalowane. Należy zaplanować dokładnie, jakiego konta użytkownika, aby uruchomić usługę; Usługa uruchomiona przy użyciu konta systemowego ma więcej uprawnień i przywilejów niż konto użytkownika.  
  
## <a name="service-lifetime"></a>Okres istnienia usługi  
 Usługa przechodzi przez kilka stanów wewnętrznych w okresie swojego istnienia. Najpierw usługa jest zainstalowana w systemie, na którym będzie uruchamiany. Ten proces wykonuje instalatorów dla projektu usługi i ładuje usługę do **Menedżera sterowania usługami** dla tego komputera. **Menedżera sterowania usługami** to centralne narzędzie oferowane przez Windows do administrowania usługami.  
  
 Po załadowaniu usługi, musi zostać uruchomiona. Uruchomienie usługi pozwala jej na rozpoczęcie działania. Można uruchomić usługi z **Menedżera sterowania usługami**, z **Eksploratora serwera**, lub z kodu, wywołując <xref:System.ServiceProcess.ServiceController.Start%2A> metody. <xref:System.ServiceProcess.ServiceController.Start%2A> Metoda przekazuje przetwarzanie do aplikacji <xref:System.ServiceProcess.ServiceBase.OnStart%2A> metody i przetwarza każdy kod zdefiniowany w niej.  
  
 Uruchomiona usługa mogą istnieć w tym stanie, dopóki nie jest ona zatrzymana lub wstrzymana, lub do momentu wyłączenia komputera. Usługa może istnieć w jednym z trzech podstawowych stanów: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, lub <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Usługa może również zgłosić stan polecenia oczekującego: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, lub <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Te stany wskazują, że polecenie zostało wydane, np. polecenie, aby wstrzymać uruchomioną usługę, ale nie przeprowadzono jeszcze. Można tworzyć zapytania <xref:System.ServiceProcess.ServiceController.Status%2A> do określenia, który stan usługi jest lub użyj <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> do wykonania akcji, gdy którykolwiek z tych stanów występuje.  
  
 Wstrzymaj, Zatrzymaj lub wznowić działanie usługi z **Menedżera sterowania usługami**, z **Eksploratora serwera**, lub przez wywołanie metody w kodzie. Każda z tych akcji może wywołać powiązaną procedurę w usłudze (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, lub <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), w którym można zdefiniować dodatkowe przetwarzanie do wykonania, gdy usługa zmienia stan.  
  
## <a name="types-of-services"></a>Typy usług  
 Istnieją dwa rodzaje usług tworzonych w programie Visual Studio przy użyciu programu .NET Framework. Usługi, które są jedynymi usługami w procesie, przypisywany jest typ <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Usługi, które współużytkują proces z inną usługą, przypisywany jest typ <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Możesz przywrócić typ usługi, badając <xref:System.ServiceProcess.ServiceController.ServiceType%2A> właściwości.  
  
 Czasu można zobaczyć inne typy usług, jeśli zapytania o istniejące usługi, które nie zostały utworzone w programie Visual Studio. Aby uzyskać więcej informacji na ten temat, zobacz <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Usługi i składnik ServiceController  
 <xref:System.ServiceProcess.ServiceController> Składnik jest używane do nawiązywania z zainstalowaną usługą i operowania jej stanem; za pomocą <xref:System.ServiceProcess.ServiceController> składnik, można uruchomić i zatrzymać usługę, wstrzymywać i kontynuować jej działanie i wysyłania poleceń niestandardowych do usługi. Jednakże, nie trzeba używać <xref:System.ServiceProcess.ServiceController> składnika podczas tworzenia aplikacji usługi. W rzeczywistości w większości przypadków swoje <xref:System.ServiceProcess.ServiceController> składnika powinny istnieć w innej aplikacji z poziomu aplikacji usługi Windows, która definiuje usługę.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Wymagania  
  
-   Usługi muszą być tworzone w **usługi Windows** projekt aplikacji lub innym projekcie rozpoznającym program .NET Framework, tworzy plik .exe, podczas kompilacji, która dziedziczy po elemencie <xref:System.ServiceProcess.ServiceBase> klasy.  
  
-   Projekty zawierające usług Windows muszą mieć składniki instalacyjne dla projektu i jego usług. Można to łatwo zrobić z **właściwości** okna. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Zobacz także
- [Aplikacje usług systemu Windows](../../../docs/framework/windows-services/index.md)
- [Architektura programowania aplikacji usług](../../../docs/framework/windows-services/service-application-programming-architecture.md)
- [Instrukcje: Tworzenie usług Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
- [Instrukcje: Instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)
- [Instrukcje: Uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)
- [Instrukcje: Debugowanie aplikacji usług Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)
- [Przewodnik: Tworzenie aplikacji usługi Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)
- [Instrukcje: Dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
