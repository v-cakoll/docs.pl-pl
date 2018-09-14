---
title: Hostowanie w aplikacji usługi systemu Windows
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: 2b3935babec0c7cdc3ffca5dd11d693fdfee7a89
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45587444"
---
# <a name="hosting-in-a-windows-service-application"></a>Hostowanie w aplikacji usługi systemu Windows
Usługi Windows (znana wcześniej jako usługi Windows NT) zapewniają proces modelu szczególnie odpowiednie dla aplikacji, które muszą znajdować się w pliku wykonywalnym długotrwałych i nie są wyświetlane w dowolnej postaci interfejsu użytkownika. Okres istnienia procesu systemu Windows, aplikacji usługi jest zarządzany przez Menedżera sterowania usługami (SCM), dzięki czemu można uruchomić, zatrzymać i oraz ich wstrzymywania aplikacji usług Windows. Możesz skonfigurować proces usługi Windows do automatycznego uruchamiania podczas uruchamiania komputera, dzięki czemu odpowiednie środowisko hostingu dla aplikacji "zawsze włączone". Aby uzyskać więcej informacji na temat aplikacji usług Windows zobacz [aplikacji usług Windows](https://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikacje obsługujące usługi Windows Communication Foundation (WCF) długotrwałych mają wiele właściwości, za pomocą usługi Windows. W szczególności usług WCF są pliki wykonywalne serwera długotrwałych, które nie wchodzą w interakcje bezpośrednio z użytkownikiem i w związku z tym nie należy implementować dowolnej formie interfejsu użytkownika. W efekcie hostowanie usługi WCF wewnątrz aplikacji usługi Windows jest jedną z opcji tworzenia niezawodnych, długo działających aplikacji WCF.  
  
 Często deweloperów usług WCF należy zdecydować, czy do hostowania aplikacji WCF wewnątrz aplikacji usługi Windows lub w środowisku hostingu usług Internet Information Services (IIS) lub Windows Process Activation Service (WAS). Należy rozważyć użycie aplikacji usług Windows w następujących warunkach:  
  
-   Aplikacja wymaga jawnego aktywacji. Na przykład należy używać usług Windows, gdy aplikacja musi Uruchom automatycznie, gdy serwer jest uruchamiany zamiast dynamicznie uruchamiany w odpowiedzi na pierwsze wiadomości przychodzącej.  
  
-   Proces, który jest hostem aplikacji może zostać wyłączony po uruchomieniu. Po rozpoczęciu procesu usługi Windows jest uruchomiona, chyba że jawnie zamykanie systemu przez administratora serwera przy użyciu Menedżera kontroli usług. Aplikacje hostowane w usługach IIS i WAS może można uruchamiać i zatrzymywać dynamicznie, aby optymalnie wykorzystać zasoby systemowe. Aplikacje, które wymagają jawną kontrolę nad okresem istnienia procesu hostingu należy używać usług Windows, a nie przez usługi IIS i WAS.  
  
-   Usługi WCF, należy uruchomić w systemie Windows Server 2003 i użyj transportu innego niż HTTP. W systemie Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] Środowisko hostingu jest ograniczony do protokołu HTTP do komunikacji tylko. Aplikacje usług Windows nie podlegają to ograniczenie i można użyć dowolnego transport obsługuje WCF, m.in. net.tcp, net.pipe i net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Hostowanie usługi WCF wewnątrz aplikacji usługi Windows  
  
1.  Tworzenie aplikacji usługi Windows. Możesz tworzyć aplikacje usługi Windows w kodzie zarządzanym przy użyciu klas w <xref:System.ServiceProcess> przestrzeni nazw. Ta aplikacja musi zawierać jedną klasę, która dziedziczy <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Okres istnienia usługi WCF można połączyć cyklu życia aplikacji usługa Windows. Zazwyczaj chcesz usług WCF hostowanych w aplikacji usługi Windows stają się aktywne po uruchomieniu usługi hostingu, przestawaj słuchać komunikaty po zatrzymaniu usługi hostingowej i zamknąć procesu hostingu, gdy usługa WCF napotka błąd. Można to zrobić w następujący sposób:  
  
    -   Zastąp <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> do otwarcia jednego lub większej liczby wystąpień <xref:System.ServiceModel.ServiceHost>. Jedną aplikację usługi Windows może obsługiwać wiele usług WCF, które uruchamiają i zatrzymują jako grupa.  
  
    -   Zastąp <xref:System.ServiceProcess.ServiceBase.OnStop%2A> do wywołania <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> wszelkie uruchomionej usługi WCF, uruchomionych w ramach <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Subskrybuj <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> zdarzenia <xref:System.ServiceModel.ServiceHost> i użyj <xref:System.ServiceProcess.ServiceController> klasy do zamykania aplikacji usługi Windows w przypadku błędu.  
  
     Aplikacje usług Windows, które prowadzą hosting usług WCF są wdrożone i zarządzane w taki sam sposób, zgodnie z aplikacjami usług Windows, które nie korzystanie z usługi WCF.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceProcess>  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](https://go.microsoft.com/fwlink/?LinkId=94875)  
 [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host usług systemu Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Architektura programowania aplikacji usług](https://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
