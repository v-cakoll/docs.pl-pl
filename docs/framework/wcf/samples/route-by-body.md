---
title: "Trasa według treści"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09e274bcbc1995dcd6b2c21e0114aa4a865f4129
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="route-by-body"></a>Trasa według treści
W tym przykładzie pokazano, jak wdrożyć usługi, która akceptuje obiekty komunikatów z dowolną akcję SOAP. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi Kalkulator. Usługa implementuje pojedynczy `Calculate` operacja, która akceptuje <xref:System.ServiceModel.Channels.Message> żądań parametrów i zwraca <xref:System.ServiceModel.Channels.Message> odpowiedzi.  
  
 W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana w usługach IIS.  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano wysyłania wiadomości na podstawie zawartości treści. Wbudowane [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanizmu wysyłania wiadomości modelu usługi jest oparta na komunikat akcji. Istnieją jednak wielu istniejących usług sieci Web, definiujące wszystkich ich operacji z wartością Action = "". Nie jest możliwe kompilacji usługi oparte na WSDL, który przechowuje wysyła komunikaty żądań informacje o akcji. W przykładzie pokazano umowy serwisowej, która jest oparta na WSDL (WSDL znajduje się w Service.wsdl dołączonego przykładu). Kontrakt usługi jest Kalkulator, podobnie jak używaną w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Jednak `[OperationContract]` Określa `Action=""` dla wszystkich operacji.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Biorąc pod uwagę kontrakt, usługa wymaga zachowania wysyłania niestandardowych `DispatchByBodyBehavior` wiadomości wysyłanych między operacjami. To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowych z tabelą nazw operacji, wyznaczaną przez QName otoki odpowiednich elementów. `DispatchByBodyElementOperationSelector`przegląda tagu początkowego pierwszego elementu podrzędnego treści i wybiera operację, używając w tabeli powyżej.  
  
 Klient korzysta z serwera proxy automatycznie generowanej z WSDL wyeksportowane za pomocą usługi [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Fakt, że akcje wszystkie operacje są puste nie ma wpływu na kod klienta, z wyjątkiem parametry akcji w obiekcie pośredniczącym wygenerowany automatycznie.  
  
 Kod klienta wykonuje kilka obliczeń. Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>Zobacz też
