---
title: Trasa według treści
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: fe201161ebed66b8444c23229a6907be329d3641
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58835131"
---
# <a name="route-by-body"></a>Trasa według treści
Ten przykład demonstruje sposób implementacji to usługa, która akceptuje obiekty wiadomości z dowolnego akcją SOAP. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md) implementującej usługi kalkulatora. Usługa implementuje jedną `Calculate` operacji, który akceptuje <xref:System.ServiceModel.Channels.Message> żądań parametrów i zwraca <xref:System.ServiceModel.Channels.Message> odpowiedzi.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana w usługach IIS.  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W przykładzie pokazano wysyłania komunikatów na podstawie zawartości treści. Wbudowany komunikat modelu usługi Windows Communication Foundation (WCF): wysyłania mechanizm opiera się na komunikat akcji. Istnieją jednak wiele istniejących usług sieci Web, które definiują wszystkie operacje przy użyciu akcji = "". Nie jest możliwe tworzenie usługi języka WSDL, który przechowuje wysyła komunikaty żądań informacji o akcji. Niniejszy przykład pokazuje kontraktu usługi, który jest oparty na języku WSDL (WSDL jest zawarty w Service.wsdl, który jest dołączony do przykładu). Umowa serwisowa jest Kalkulator, podobnie jak komentarzowi użytemu w [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Jednak `[OperationContract]` Określa `Action=""` dla wszystkich operacji.  
  
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
  
 Biorąc pod uwagę kontrakt, usługa wymaga zachowania wysyłania niestandardowych `DispatchByBodyBehavior` wiadomości wysyłanych między operacjami. To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowego za pomocą tabeli nazw operacji opartych na kluczach QName otoki odpowiednich elementów. `DispatchByBodyElementOperationSelector` analizuje tagu początkowego pierwszego elementu podrzędnego treści i wybiera tej operacji z użyciem w tabeli powyżej.  
  
 Klient korzysta z serwera proxy, wygenerowany automatycznie z danych WSDL wyeksportowane za pomocą usługi [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Fakt, że akcje wszystkie operacje są puste nie ma wpływu na kod klienta, z wyjątkiem parametry akcji na serwerze proxy generowany automatycznie.  
  
 Kod klienta wykonuje kilka obliczeń. Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
