---
title: "Wprowadzenie do aplikacji usług systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ServiceController
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
caps.latest.revision: "17"
author: ghogen
ms.author: ghogen
manager: douge
ms.workload: dotnet
ms.openlocfilehash: 613107a13820ad71b854dcba93f21c41f2a5fa5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="introduction-to-windows-service-applications"></a>Wprowadzenie do aplikacji usług systemu Windows
Program Microsoft Windows services, wcześniej znana jako usługi NT umożliwiają tworzenie aplikacji wykonywalnych długotrwałe działających w ich własnej sesji systemu Windows. Tych usług można automatycznie uruchamiana podczas rozruchu komputera, może być wstrzymane i ponownie uruchomione i nie wyświetlaj interfejsu użytkownika. Te funkcje należy usług idealne do użycia na serwerze lub jeśli potrzebne jest długotrwałe funkcje, które nie koliduje z innym użytkownikom pracującym na tym samym komputerze. Można również uruchomić usług w kontekście zabezpieczeń konta określonego użytkownika, który różni się od zalogowanego użytkownika lub domyślnego konta komputera. Aby uzyskać więcej informacji o usługach i sesji systemu Windows zobacz dokumentację zestawu Windows SDK.  
  
 Można łatwo tworzyć usługi przez utworzenie aplikacji, która jest zainstalowany jako usługa. Na przykład załóżmy, że chcesz monitorować dane licznika wydajności i reagowania na wartości progowe. Można napisać aplikację usługi systemu Windows nasłuchujący dane licznika wydajności, Wdróż aplikację i rozpocząć zbieranie i analizowanie danych.  
  
 Tworzenie usługi jako projekt programu Microsoft Visual Studio, definiowanie w niej kodu, która kontroluje, jakie polecenia mogą być wysyłane do usługi i działania, jakie należy podjąć po otrzymaniu tych poleceń. Polecenia, które mogą być wysyłane do usługi obejmują uruchamianie, wstrzymywanie, wznawianie i zatrzymywanie usługi; można również wykonywać polecenia niestandardowych.  
  
 Po utworzeniu i skompilować aplikację można zainstalować go przez uruchomienie narzędzia wiersza polecenia InstallUtil.exe i przekazywanie ścieżka do pliku wykonywalnego usługi. Następnie można użyć **Menedżera sterowania usługami** na uruchamianie, zatrzymywanie, wstrzymywanie, wznawianie i skonfigurować usługi. Można również wykonywać wiele tych samych zadań w **usług** w węźle **Eksploratora serwera** lub za pomocą <xref:System.ServiceProcess.ServiceController> klasy.  
  
## <a name="service-applications-vs-other-visual-studio-applications"></a>Aplikacje usług vs. Inne aplikacje programu Visual Studio  
 Funkcja aplikacji usługa zależy od wielu innych typów projektu na kilka sposobów:  
  
-   Skompilowany plik wykonywalny, który tworzy projekt aplikacji usługi przed należy skonfigurować na serwerze projektu mogą działać w sposób łatwy do rozpoznania. Nie można debugować ani uruchamiać aplikacji usługi, naciskając klawisz F5 lub F11; Nie można natychmiast uruchomić usługi lub krok do jej kodu. Zamiast tego należy zainstalować i uruchomić usługę, a następnie dołącz debugera do procesu usługi. Aby uzyskać więcej informacji, zobacz [porady: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md).  
  
-   W przeciwieństwie do niektórych typów projektów należy utworzyć składniki instalacji dla aplikacji usługi. Składniki instalacji Zainstaluj i zarejestruj usługę na serwerze oraz utworzyć wpis dla usługi z systemu Windows **Menedżera sterowania usługami**. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
-   `Main` Metoda aplikacji usługi należy wydać polecenie uruchomienia usług projektu zawiera. `Run` Metody ładuje usług do **Menedżera sterowania usługami** na odpowiednim serwerze. Jeśli używasz **usług systemu Windows** szablon projektu, ta metoda jest przeznaczony dla zostanie automatycznie. Należy pamiętać, że ładowanie usługi nie jest odpowiednikiem uruchamiania usługi. Zobacz "Okres istnienia usługi" poniżej Aby uzyskać więcej informacji.  
  
-   Aplikacje usług systemu Windows uruchom w stacji innego niż stacji zalogowanego użytkownika interaktywnego. Stacja jest bezpieczny obiekt, który zawiera Schowek, zestaw globalnych atomami i grup obiektów pulpitu. Ponieważ stacji usługi systemu Windows nie jest interaktywny stacji, okna dialogowe zgłoszony z w Windows usługi aplikacji nie będą widoczne i może spowodować, że program może przestać odpowiadać. Podobnie komunikaty o błędach powinny być rejestrowane w dzienniku zdarzeń systemu Windows zamiast wywoływane w interfejsie użytkownika.  
  
     Klasy usługi systemu Windows, które są obsługiwane przez program .NET Framework nie obsługuje interakcji z interaktywnego stacji, oznacza to, że zalogowany użytkownik. .NET Framework nie obejmuje również klasy reprezentujące stacji i pulpitów. Jeśli usługi systemu Windows musi pracować interaktywnie z innych stacjach, należy uzyskać dostęp z niezarządzanego API systemu Windows. Aby uzyskać więcej informacji zobacz dokumentację zestawu Windows SDK.  
  
     Interakcja usługi z użytkownika lub innych stacjach muszą być dokładnie zaprojektowane obejmują scenariusze, takie jak brak nie zalogowanego użytkownika lub użytkowników o nieoczekiwany zestaw obiektów pulpitu systemu Windows. W niektórych przypadkach może być bardziej odpowiednie do tworzenia aplikacji systemu Windows działającą w formancie użytkownika.  
  
-   Aplikacje usług systemu Windows uruchom w kontekstu zabezpieczeń i są uruchamiane przed zalogowaniem użytkownika do komputera z systemem Windows, na którym są zainstalowane. Należy zaplanować dokładnie jakiego konta użytkownika do uruchamiania usługi w ramach; w usłudze działającej na koncie systemu ma więcej uprawnień i uprawnień niż konto użytkownika.  
  
## <a name="service-lifetime"></a>Okres istnienia usługi  
 Usługa przechodzi przez kilka stanów wewnętrznego w okresie użytkowania. Po pierwsze usługa jest instalowana na system, na którym będzie uruchomiona. Ten proces wykonuje instalatorów do projektu usługi i ładuje usługi do **Menedżera sterowania usługami** dla tego komputera. **Menedżera sterowania usługami** to centralne narzędzie dostarczonymi przez system Windows do administrowania usługami.  
  
 Po załadowaniu usługi musi być uruchomiona. Uruchamianie usługi umożliwia rozpoczęcie działania. Można uruchomić usługi z **Menedżera sterowania usługami**, z **Eksploratora serwera**, lub z kodu przez wywołanie metody <xref:System.ServiceProcess.ServiceController.Start%2A> metody. <xref:System.ServiceProcess.ServiceController.Start%2A> Metoda przekazuje przetwarzania do aplikacji <xref:System.ServiceProcess.ServiceBase.OnStart%2A> — metoda i przetwarza każdy kod zdefiniowano.  
  
 Uruchomionej usługi może istnieć w tym stanie przez czas nieokreślony, aż do jej jest zatrzymana lub wstrzymana lub wyłączania komputera. Usługa może występować w jednym z trzech stanów podstawowe: <xref:System.ServiceProcess.ServiceControllerStatus.Running>, <xref:System.ServiceProcess.ServiceControllerStatus.Paused>, lub <xref:System.ServiceProcess.ServiceControllerStatus.Stopped>. Usługa także zgłosić stan oczekującego polecenia: <xref:System.ServiceProcess.ServiceControllerStatus.ContinuePending>, <xref:System.ServiceProcess.ServiceControllerStatus.PausePending>, <xref:System.ServiceProcess.ServiceControllerStatus.StartPending>, lub <xref:System.ServiceProcess.ServiceControllerStatus.StopPending>. Te stany wskazują, że polecenie został wystawiony, takich jak polecenia wstrzymanie uruchomionej usługi, ale nie przeprowadzono jeszcze. Można zbadać <xref:System.ServiceProcess.ServiceController.Status%2A> w celu określenia, który stan usługi jest w lub użyj <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A> do wykonania akcji, gdy dowolne z tych stanów występuje.  
  
 Można wstrzymać, zatrzymać lub wznowić działanie usługi z **Menedżera sterowania usługami**, z **Eksploratora serwera**, lub przez wywołanie metody w kodzie. Każdy z tych działań można wywołać procedury w usłudze (<xref:System.ServiceProcess.ServiceBase.OnStop%2A>, <xref:System.ServiceProcess.ServiceBase.OnPause%2A>, lub <xref:System.ServiceProcess.ServiceBase.OnContinue%2A>), w którym można zdefiniować dodatkowe przetwarzanie do wykonania, gdy usługa zmieni stan.  
  
## <a name="types-of-services"></a>Typy usług  
 Istnieją dwa typy usług, które można utworzyć w programie Visual Studio przy użyciu programu .NET Framework. Usługi, które są tylko usługi w ramach procesu są przypisane typ <xref:System.ServiceProcess.ServiceType.Win32OwnProcess>. Usługi, które umożliwia udostępnianie procesu z innej usługi, są przypisane typ <xref:System.ServiceProcess.ServiceType.Win32ShareProcess>. Typ usługi można pobrać badając <xref:System.ServiceProcess.ServiceController.ServiceType%2A> właściwości.  
  
 Czasami może być wyświetlanych innych typów usług, po wykonaniu zapytania istniejących usług, które nie zostały utworzone w programie Visual Studio. Aby uzyskać więcej informacji o tych zobacz <xref:System.ServiceProcess.ServiceType>.  
  
## <a name="services-and-the-servicecontroller-component"></a>Usługi i składnika ServiceController  
 <xref:System.ServiceProcess.ServiceController> Składnik jest używane do łączenia się z usługą zainstalowanych i manipulowania stanu; przy użyciu <xref:System.ServiceProcess.ServiceController> składnika, można uruchomić i zatrzymać usługę, wstrzymywać i kontynuować jego działania i wysyłać polecenia niestandardowych do usługi. Jednak nie trzeba używać <xref:System.ServiceProcess.ServiceController> składnika podczas tworzenia aplikacji usługi. W rzeczywistości w większości przypadków Twojej <xref:System.ServiceProcess.ServiceController> składnika powinna istnieć w innej aplikacji z aplikacji usługi systemu Windows, który definiuje usługi.  
  
 Aby uzyskać więcej informacji, zobacz <xref:System.ServiceProcess.ServiceController>.  
  
## <a name="requirements"></a>Wymagania  
  
-   Usługi muszą zostać utworzone w **usługi systemu Windows** projekt aplikacji lub inny projekt .NET Framework — włączone tworzy plik .exe podczas tworzenia, który dziedziczy z <xref:System.ServiceProcess.ServiceBase> klasy.  
  
-   Projekty zawierające usług systemu Windows musi mieć instalacja składników dla projektu i jego usług. Można to łatwo zrobić z **właściwości** okna. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie instalatorów do Twojej aplikacji usługi](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje usług systemu Windows](../../../docs/framework/windows-services/index.md)  
 [Architektura programowania aplikacji usług](../../../docs/framework/windows-services/service-application-programming-architecture.md)  
 [Instrukcje: tworzenie usług systemu Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)  
 [Instrukcje: instalowanie i odinstalowywanie usług](../../../docs/framework/windows-services/how-to-install-and-uninstall-services.md)  
 [Instrukcje: uruchamianie usług](../../../docs/framework/windows-services/how-to-start-services.md)  
 [Instrukcje: debugowanie aplikacji usług systemu Windows](../../../docs/framework/windows-services/how-to-debug-windows-service-applications.md)  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](../../../docs/framework/windows-services/walkthrough-creating-a-windows-service-application-in-the-component-designer.md)  
 [Instrukcje: dodawanie instalatorów od aplikacji usług](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)
