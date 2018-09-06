---
title: Wprowadzenie do Tutorial1
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: e5a07e5264c715f568121403721a3c844b903d99
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886321"
---
# <a name="getting-started-tutorial"></a>Wprowadzenie — samouczek
Tematy zawarte w tej sekcji są przeznaczone do umożliwiają szybkie narażenia na Windows Communication Foundation (WCF) środowisko programowania. Mają zostać wykonane zgodnie z kolejnością na liście w dolnej części tego tematu. Ten samouczek umożliwia poznanie wprowadzające kroków wymaganych do tworzenia aplikacji usługi i klienta WCF. Usługa udostępnia jeden lub więcej punktów końcowych, z których każdy ujawnia co najmniej jednej operacji usługi. *Punktu końcowego* usługi Określa adres, gdzie można znaleźć usługi, powiązania, który zawiera informacje opisujące, jak klientowi komunikowanie się z usługą i kontrakt definiujący funkcje udostępniane przez usługę do swoich klientów.  
  
 Po zakończeniu pracy z sekwencją tematów w tym samouczku będą mieć uruchomioną usługę i klienta, który wywołuje usługę. W pierwszych trzech tematach opisano, jak definiowanie kontraktu usługi, jak zaimplementować kontrakt usługi i sposobu obsługi usługi. Usługa, która jest tworzona jest samodzielnie hostowany w aplikacji konsoli. Usługi może też być hostowana w ramach usługi Internet Information Services (IIS). Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [instrukcje: hostowanie usługi WCF w programie IIS](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md). Usługa jest skonfigurowana w kodzie Jednak usługi mogą być skonfigurowane w pliku konfiguracji. Aby uzyskać więcej informacji na temat przy użyciu pliku konfiguracji zobacz [Konfigurowanie usług za pomocą plików konfiguracji](../../../docs/framework/wcf/configuring-services-using-configuration-files.md).  
  
 W trzech kolejnych tematach opisano, jak utworzyć serwer proxy klienta, skonfigurować aplikację klienta i serwer proxy klienta jest używany do wywoływania operacji usług udostępnianych przez usługę. Usługi publikowania metadanych, który definiuje informacje, które aplikacja kliencka musi komunikować się z usługą. [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] automatyzuje proces uzyskiwania dostępu do metadanych i używa ich do tworzenia i konfigurowania aplikacji klienckiej dla usługi. Jeśli nie używasz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], możesz użyć [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to utworzyć i skonfigurować aplikację klienta dla usługi.  
  
 Wszystkie tematy w tej sekcji przyjęto założenie, że używasz programu Visual Studio 2011 jako środowiska deweloperskiego. Jeśli używasz innego środowiska deweloperskiego Ignoruj określone instrukcje podane programu Visual Studio.  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[wv](../../../includes/wv-md.md)] lub nowszymi wersjami systemu operacyjnego Windows, należy uruchomić program Visual Studio, przechodząc do Start menu i programu Visual Studio 2011 kliknięcie prawym przyciskiem myszy i wybierając **Uruchom jako Administrator**. Można zawsze uruchomić programu Visual Studio 2011 jako administrator możesz można utworzyć skrótów skrótów kliknij prawym przyciskiem myszy, wybierz właściwości, wybierz **zgodności** kartę i sprawdź **uruchamiaj ten program jako administrator** pole wyboru. Po uruchomieniu programu Visual Studio 2011 z ten skrót zawsze będzie Uruchom jako administrator.  
  
 Aby uzyskać przykładowe aplikacje, które może być pobierany na dysku twardym i uruchamiania, zobacz Tematy w [Windows Communication Foundation — przykłady](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91). W tym temacie, zobacz temat w szczególności [wprowadzenie](../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
 Aby uzyskać bardziej szczegółowe informacje o sposobie tworzenia usług i klientów, zobacz [programowanie WCF Basic](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: definiowanie kontraktu usługi](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)  
 W tym artykule opisano sposób tworzenia kontraktu usługi WCF, za pomocą interfejsu użytkownika. Kontrakt definiuje funkcji udostępnianych przez usługę.  
  
 [Instrukcje: implementowanie kontraktu usługi](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)  
 Opisuje sposób implementacji kontraktu usługi. Po definiowanie kontraktu musi być implementowane za pomocą klasy usługi.  
  
 [Instrukcje: hostowanie i uruchamianie podstawowej usługi](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)  
 W tym artykule opisano sposób konfigurowania punktu końcowego dla usługi w kodzie oraz do obsługi usługi w aplikacji konsoli. Stanie się aktywna, usługi należy skonfigurować i hostowane w środowisku uruchomieniowym. Środowisko to tworzy usługę i kontroluje jego kontekstu i okresu istnienia.  
  
 [Instrukcje: tworzenie klienta](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)  
 Opisuje sposób pobierania metadanych użyte do utworzenia serwera proxy klienta WCF z usługą WCF. Ten proces korzysta z funkcji Dodaj odwołanie do usługi w ramach programu Visual Studio 2011.  
  
 [Instrukcje: konfigurowanie klienta](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)  
 W tym artykule opisano sposób konfigurowania usługi WCF klienta Konfigurowanie klienta wymaga określenia pliku punktu końcowego, który klient używa w celu uzyskania dostępu do usługi.  
  
 [Instrukcje: używanie klienta](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)  
 Opisuje sposób używania serwera proxy klienta WCF do wywoływania operacji usługi.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Windows Communication Foundation — przykłady](https://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)  
  
 [Podstawowy cykl życia programowania](../../../docs/framework/wcf/basic-programming-lifecycle.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Omówienie pojęć](../../../docs/framework/wcf/conceptual-overview.md)  
 [Przewodnik po dokumentacji](../../../docs/framework/wcf/guide-to-the-documentation.md)  
 [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Szczegóły funkcji WCF](../../../docs/framework/wcf/feature-details/index.md)
