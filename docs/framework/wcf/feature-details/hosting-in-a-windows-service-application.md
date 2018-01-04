---
title: "Hostowanie w aplikacji usługi systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1a39162097c21f20c0dd04f3911442602871436
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="hosting-in-a-windows-service-application"></a>Hostowanie w aplikacji usługi systemu Windows
Usługi systemu Windows (wcześniej znane jako usługi systemu Windows NT) zapewniają proces modelu szczególnie nadaje się do aplikacji, musi istnieć w pliku wykonywalnym długotrwałe, które nie są wyświetlane wszystkie formularza interfejsu użytkownika. Okres istnienia procesu systemu Windows, usługi aplikacja jest zarządzana przez Menedżera sterowania usługami (SCM), dzięki czemu można uruchomić, zatrzymać i wstrzymywanie aplikacji usług systemu Windows. Można skonfigurować do automatycznego uruchamiania podczas uruchamiania komputera, dzięki czemu odpowiednie środowisko macierzyste dla aplikacji "zawsze włączone" proces usługi systemu Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Aplikacje usług systemu Windows, temacie [aplikacji usług systemu Windows](http://go.microsoft.com/fwlink/?LinkId=89450).  
  
 Aplikacje obsługujące długotrwałe [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług mają wiele właściwości usługami wdrażania systemu Windows. W szczególności [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi są długotrwałe plików wykonywalnych serwera, które nie wchodzą w interakcje bezpośrednio z użytkownikiem i w związku z tym nie należy implementować dowolnej formy interfejsu użytkownika. W efekcie hosting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług wewnątrz aplikacji usługi systemu Windows jest jedną z opcji tworzenia niezawodne, długotrwałą, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji.  
  
 Często [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] deweloperzy należy zdecydować, czy do obsługi ich [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji wewnątrz aplikacji usługi systemu Windows lub w środowisku macierzystym Internet Information Services (IIS) lub usługi aktywacji procesów systemu Windows (WAS). Należy rozważyć użycie aplikacji usług systemu Windows w następujących warunkach:  
  
-   Aplikacja wymaga jawnego aktywacji. Na przykład podczas aplikacji musi zaczynać się automatycznie podczas uruchamiania serwera zamiast dynamicznie uruchamiany w odpowiedzi na pierwszy komunikat przychodzący należy używać usług systemu Windows.  
  
-   Proces, który jest hostem aplikacji może zostać wyłączony, po uruchomieniu. Po rozpoczęciu procesu usługi systemu Windows jest uruchomiona, chyba że jawnie zamykanie przez administratora serwera przy użyciu Menedżera kontroli usług. Aplikacje hostowane w usługach IIS lub WAS może być uruchamiania i zatrzymywania dynamicznie optymalne wykorzystanie zasobów systemowych. Aplikacje, które wymagają jawne kontroli w okresie istnienia procesu hostingu powinien używać usług systemu Windows zamiast usług IIS lub WAS.  
  
-   Twoje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi należy uruchomić w systemie Windows Server 2003 i korzystać z transportu innego niż HTTP. W systemie Windows Server 2003 [!INCLUDE[iis601](../../../../includes/iis601-md.md)] środowisko macierzyste jest ograniczone do komunikacji HTTP tylko. Aplikacje usług systemu Windows nie są to ograniczenie i można użyć dowolnego transportu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje, w tym net.tcp, net.pipe i net.msmq.  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Na hoście WCF wewnątrz aplikacji usługi systemu Windows  
  
1.  Utwórz aplikację usługi systemu Windows. Aplikacje usług systemu Windows może zapisać w kodzie zarządzanym przy użyciu klas w <xref:System.ServiceProcess> przestrzeni nazw. Ta aplikacja musi zawierać jedną klasę, która dziedziczy <xref:System.ServiceProcess.ServiceBase>.  
  
2.  Okres istnienia Link [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług systemu Windows przez czas ich istnienia aplikacji usługi. Zwykle ma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi hostowanej w aplikacji usługi systemu Windows staje się aktywny po uruchomieniu usługi hostingu, Zatrzymano nasłuchiwanie wiadomości po zatrzymaniu usługi hostingu i zamykania hostingu podczas przetwarzania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługa napotka błąd. Można to zrobić w następujący sposób:  
  
    -   Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> do otwarcia jednego lub więcej wystąpień <xref:System.ServiceModel.ServiceHost>. Pojedynczy aplikację usługi systemu Windows można zarządzać wieloma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, których uruchamianie i zatrzymywanie jako grupa.  
  
    -   Zastąpienie <xref:System.ServiceProcess.ServiceBase.OnStop%2A> do wywołania <xref:System.ServiceModel.Channels.CommunicationObject.Closed> na <xref:System.ServiceModel.ServiceHost> wszelkie uruchomione [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług, które zostały uruchomione podczas <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>.  
  
    -   Subskrybuj <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> zdarzenie <xref:System.ServiceModel.ServiceHost> i użyj <xref:System.ServiceProcess.ServiceController> klasę, aby zamknąć aplikację usługi systemu Windows w przypadku błędu.  
  
     Aplikacje usług systemu Windows, że host [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi są wdrażane i zarządzane w taki sam sposób jak użycie aplikacji usług systemu Windows, które nie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceProcess>  
 [Przewodnik: tworzenie aplikacji usługowej systemu Windows w Projektancie składników](http://go.microsoft.com/fwlink/?LinkId=94875)  
 [Instrukcje: hostowanie usługi WCF w usłudze zarządzanej systemu Windows](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)  
 [Host usług systemu Windows](../../../../docs/framework/wcf/samples/windows-service-host.md)  
 [Architektura programowania aplikacji usług](http://go.microsoft.com/fwlink/?LinkId=94876)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
