---
title: Hostowanie w aplikacji usługi systemu Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: e440961055ccd40bf56b4b88ea73d167f1903245
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492235"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostowanie w aplikacji usługi systemu Windows
Usługi systemu Windows (wcześniej znane jako usługi systemu Windows NT) zapewniają proces modelu szczególnie nadaje się do aplikacji, musi istnieć w pliku wykonywalnym długotrwałe, które nie są wyświetlane wszystkie formularza interfejsu użytkownika. Okres istnienia procesu systemu Windows, usługi aplikacja jest zarządzana przez Menedżera sterowania usługami (SCM), dzięki czemu można uruchomić, zatrzymać i wstrzymywanie aplikacji usług systemu Windows. Można skonfigurować do automatycznego uruchamiania podczas uruchamiania komputera, dzięki czemu odpowiednie środowisko macierzyste dla aplikacji "zawsze włączone" proces usługi systemu Windows. Aby uzyskać więcej informacji o aplikacji usług systemu Windows, zobacz [aplikacji usług systemu Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikacje obsługujące długotrwałe usług Windows Communication Foundation (WCF) mają wiele właściwości, usługami wdrażania systemu Windows. W szczególności usług WCF jest długotrwałe plików wykonywalnych serwera, które nie wchodzą w interakcje bezpośrednio z użytkownikiem i w związku z tym nie należy implementować dowolnej formy interfejsu użytkownika. Hosting usług WCF wewnątrz aplikacji usługi systemu Windows tak, jest jedną z opcji tworzenia aplikacji WCF niezawodne, długotrwałą.  
  
 Często deweloperów usług WCF należy zdecydować, czy do hostowania aplikacji WCF wewnątrz aplikacji usługi systemu Windows lub w środowisku macierzystym Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS). Należy rozważyć użycie aplikacji usług systemu Windows w następujących warunkach:  
  
-   Aplikacja wymaga jawnego aktywacji. Na przykład podczas aplikacji musi zaczynać się automatycznie podczas uruchamiania serwera zamiast dynamicznie uruchamiany w odpowiedzi na pierwszy komunikat przychodzący należy używać usług systemu Windows.  
  
-   Proces, który jest hostem aplikacji może zostać wyłączony, po uruchomieniu. Po rozpoczęciu procesu usługi systemu Windows jest uruchomiona, chyba że jawnie zamykanie przez administratora serwera przy użyciu Menedżera kontroli usług. Aplikacje hostowane w usługach IIS lub WAS może być uruchamiania i zatrzymywania dynamicznie optymalne wykorzystanie zasobów systemowych. Aplikacje, które wymagają jawne kontroli w okresie istnienia procesu hostingu powinien używać usług systemu Windows zamiast usług IIS lub WAS.  
  
-   Usługi WCF, należy uruchomić w systemie Windows Server 2003 i używają transportu innego niż HTTP. W systemie Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] środowisko macierzyste jest ograniczone do komunikacji HTTP tylko. Aplikacje usług systemu Windows nie są to ograniczenie i można użyć dowolnego transport obsługuje WCF, w tym net.tcp, net.pipe i net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Na hoście WCF wewnątrz aplikacji usługi systemu Windows  
  
1.  Utwórz aplikację usługi systemu Windows. Aplikacje usług systemu Windows może zapisać w kodzie zarządzanym przy użyciu klas w <xref:System.ServiceProcess> przestrzeni nazw. Ta aplikacja musi zawierać jedną klasę, która dziedziczy <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Łącze okres istnienia usługi WCF do użytkowania aplikacji usług systemu Windows. Zwykle ma usług WCF hostowanych w aplikacji usługi systemu Windows, aby stają się aktywne po uruchomieniu usługi hostingu, Zatrzymaj nasłuchuje wiadomości po zatrzymaniu usługi hostingu i zamknąć procesu hostingu, gdy usługa WCF napotka błąd. Można to zrobić w następujący sposób:  
  
    -   Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> do otwarcia jednego lub więcej wystąpień <xref:System.ServiceModel.ServiceHost>. Pojedynczy aplikację usługi systemu Windows może obsługiwać wiele usług WCF, których uruchamianie i zatrzymywanie jako grupa.  
  
    -   Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStop%2A> do wywołania <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> uruchomionych usług WCF, które zostały uruchomione podczas <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Subskrybuj <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> zdarzenie <xref:System.ServiceModel.ServiceHost> i użyj <xref:System.ServiceProcess.ServiceController> klasę, aby zamknąć aplikację usługi systemu Windows w przypadku błędu.  
  
     Aplikacji usług systemu Windows, które prowadzą hosting usług WCF są wdrażane i zarządzane w taki sam sposób jak aplikacje usług systemu Windows, które nie używa usługi WCF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceProcess>  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host usług systemu Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Architektura programowania aplikacji usług](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
