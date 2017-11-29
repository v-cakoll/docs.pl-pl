---
title: Wprowadzenie Tutorial1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
caps.latest.revision: "47"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5f34ac7ec2761efda640e3c4838a5f44f2e244e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="getting-started-tutorial"></a>Wprowadzenie — samouczek
Tematy zawarte w tej sekcji mają na celu umożliwiają szybkie narażenia na [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] środowisko programowania. Są one przeznaczone do wypełnienia kolejności na liście w dolnej części tego tematu. Ten samouczek umożliwia poznanie wprowadzające kroków wymaganych do utworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi i aplikacje klienckie. Usługa udostępnia jeden lub więcej punktów końcowych, z których każdy ujawnia co najmniej jedną operację usługi. *Punktu końcowego* usługi Określa adres, gdzie można znaleźć usługi, powiązania, który zawiera informacje opisujące, jak klient musi komunikować się z usługą i kontrakt definiujący funkcje udostępniony przez usługę klientom.  
  
 Po zakończeniu pracy z sekwencją tematów w tym samouczku, będzie mieć uruchomioną usługę i klienta, który wywołuje usługę. Pierwsze trzy tematach opisano, jak definiowanie kontraktu usługi, jak Implementowanie kontraktu usługi oraz sposobu obsługi usługi. Usługa, która jest tworzona jest samodzielnie hostowana w aplikacji konsoli. Usługi również może być hostowana w obszarze usługi Internet Information Services (IIS). [!INCLUDE[crabout](../../../includes/crabout-md.md)]jak to zrobić, zobacz [porady: hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Usługa jest skonfigurowana w kodzie; Jednak usługi, można również skonfigurować w pliku konfiguracji. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Zobacz użycie pliku konfiguracji [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 W trzech kolejnych tematach opisano sposób tworzenia serwera proxy klienta, konfigurowania aplikacji klienckiej i użyć serwera proxy klienta do wywołania operacji usługi udostępniane przez usługę. Usługi Publikowanie metadanych, który definiuje informacje potrzebne do komunikowania się z usługi aplikacji klienckiej. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)]automatyzuje proces uzyskiwania dostępu do metadanych i używa go do tworzenia i konfigurowania aplikacji klienckiej dla usługi. Jeśli nie używasz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], można użyć [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) utworzyć i skonfigurować aplikację klienta dla usługi.  
  
 We wszystkich tematach w tej sekcji założono, że używasz programu Visual Studio 2011 jako Środowisko deweloperskie. Jeśli korzystasz z innego środowiska projektowania, Pomiń [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] szczegółowych instrukcji.  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[wv](../../../includes/wv-md.md)] lub nowszymi wersjami systemu operacyjnego Windows, należy uruchomić [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] , przechodząc do Start menu i programu Visual Studio 2011 kliknięcie prawym przyciskiem myszy i wybierając **Uruchom jako Administrator**. Można zawsze uruchomić programu Visual Studio 2011 jako administrator możesz można tworzenia skrótów, kliknij prawym przyciskiem myszy skrótów, wybierz polecenie Właściwości, wybierz **zgodności** i sprawdź **uruchomić ten program jako administrator** wyboru. Po uruchomieniu programu Visual Studio 2011 z ten skrót będzie zawsze Uruchom jako administrator.  
  
 Dla aplikacji przykładowej, które może być pobierany na dysku twardym i uruchom można znaleźć w tematach w [przykładów Windows Communication Foundation](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). W tym temacie można znaleźć, w szczególności [wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Aby uzyskać więcej szczegółowych informacji o tworzeniu usług i klientów, zobacz [podstawowe programowania WCF](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Porady: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 Opisuje sposób tworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kontraktu przy użyciu interfejsu użytkownika. Kontrakt definiuje funkcji udostępnianych przez usługę.  
  
 [Porady: Implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Opisuje sposób Implementowanie kontraktu usługi. Gdy kontrakt jest zdefiniowanie, musi być implementowana z klasą usługi.  
  
 [Porady: hostowanie i uruchamianie podstawowej usługi](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 Zawiera opis sposobu konfigurowania punktu końcowego usługi w kodzie i obsługiwać usługę w aplikacji konsoli. Staje się aktywny, usługi należy skonfigurować i hostowany w środowisku czasu wykonywania. To środowisko tworzy usługi i formanty jego kontekstu i okresem istnienia.  
  
 [Porady: Tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Zawiera opis sposobu pobierania metadanych używany do tworzenia [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy klienta z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi. Ten proces korzysta z funkcji Dodaj odwołanie do usługi w programie Visual Studio 2011.  
  
 [Porady: Konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 Opisuje sposób konfigurowania WCF klienta Konfigurowanie klienta wymaga określenia punktu końcowego, który klient używa do uzyskania dostępu do usługi.  
  
 [Porady: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Informacje dotyczące używania [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] proxy klienta do wywołania operacji usługi.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Windows Communication Foundation — przykłady](http://msdn.microsoft.com/en-us/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Podstawowy cykl życia programowania](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pojęć](../../../docs/framework/wcf/conceptual-overview.md)  
 [Przewodnik po dokumentacji](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Co to jest Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md)
