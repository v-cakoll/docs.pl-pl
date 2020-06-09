---
title: Trasa według treści
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 146baf806f4922f5e3ddd92a762772786e61d443
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594598"
---
# <a name="route-by-body"></a>Trasa według treści
Ten przykład pokazuje, jak wdrożyć usługę akceptującą obiekty komunikatów z dowolną akcją SOAP. Ten przykład jest oparty na [wprowadzenie](getting-started-sample.md) , który implementuje usługę kalkulatora. Usługa implementuje pojedynczą `Calculate` operację, która akceptuje <xref:System.ServiceModel.Channels.Message> parametr żądania i zwraca <xref:System.ServiceModel.Channels.Message> odpowiedź.  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana w usługach IIS.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład ilustruje wysyłanie komunikatów na podstawie zawartości treści. Wbudowany mechanizm wysyłania komunikatów modelu usługi Windows Communication Foundation (WCF) jest oparty na akcjach komunikatów. Istnieje jednak wiele istniejących usług sieci Web, które definiują wszystkie operacje z akcją = "". Nie można utworzyć usługi opartej na języku WSDL, która ciągle wysyła komunikaty żądania na podstawie informacji o akcjach. Ten przykład pokazuje kontrakt usługi oparty na języku WSDL (WSDL jest zawarty w plik Service. WSDL, który jest dołączony do przykładu). Kontrakt usługi jest kalkulatorem podobnym do użytego w [wprowadzenie](getting-started-sample.md). Jest to jednak wartość `[OperationContract]` określana `Action=""` dla wszystkich operacji.  
  
```csharp  
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
  
 W przypadku kontraktu usługa wymaga niestandardowego zachowania wysyłania `DispatchByBodyBehavior` , aby umożliwić wysyłanie komunikatów między operacjami. To zachowanie wysyłania inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowych z tabelą nazw operacji, które są poprzedzone przez QName odpowiednich elementów otoki. `DispatchByBodyElementOperationSelector`sprawdza tag początkowy pierwszego elementu podrzędnego treści i wybiera operację przy użyciu wcześniej wymienionej tabeli.  
  
 Klient korzysta z wygenerowanego automatycznie serwera proxy z poziomu WSDL wyeksportowanego przez usługę za pomocą [narzędzia Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Fakt, że akcje wszystkich operacji są puste nie ma wpływu na kod klienta, z wyjątkiem parametrów akcji w automatycznie generowanym serwerze proxy.  
  
 Kod klienta wykonuje kilka obliczeń. Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
