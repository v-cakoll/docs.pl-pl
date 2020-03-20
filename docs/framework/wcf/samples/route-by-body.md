---
title: Trasa według treści
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144191"
---
# <a name="route-by-body"></a>Trasa według treści
W tym przykładzie pokazano, jak zaimplementować usługę, która akceptuje obiekty wiadomości z dowolną akcją PROTOKOŁU SOAP. Ten przykład jest oparty na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md) który implementuje usługę kalkulatora. Usługa implementuje pojedynczą `Calculate` operację, <xref:System.ServiceModel.Channels.Message> która akceptuje parametr <xref:System.ServiceModel.Channels.Message> żądania i zwraca odpowiedź.  
  
 W tym przykładzie klient jest aplikacją konsoli (exe), a usługa jest hostowana w usługach IIS.  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Przykład pokazuje wysyłkę wiadomości na podstawie zawartości treści. Wbudowany mechanizm wysyłania komunikatów usługi Windows Communication Foundation (WCF) jest oparty na akcjach komunikatów. Istnieje jednak wiele istniejących usług sieci Web, które definiują wszystkie ich operacje za pomocą Action="". Nie można utworzyć usługi opartej na WSDL, która przechowuje komunikaty żądania wysyłki na podstawie informacji akcji. W tym przykładzie pokazano umowy serwisowej, która jest oparta na WSDL (WSDL znajduje się w Service.wsdl, który jest dołączony do próbki). Umowa serwisowa to Kalkulator, podobny do tego używanego w [wprowadzenie.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Jednak `[OperationContract]` określa `Action=""` dla wszystkich operacji.  
  
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
  
 Biorąc pod uwagę kontrakt, usługa `DispatchByBodyBehavior` wymaga niestandardowego zachowania wysyłki, aby umożliwić wysyłanie wiadomości między operacjami. To zachowanie wysyłki inicjuje `DispatchByBodyElementOperationSelector` selektor operacji niestandardowej z tabelą nazw operacji wpisanych przez QName odpowiednich elementów otoki. `DispatchByBodyElementOperationSelector`patrzy na znacznik początkowy pierwszego niaka i wybiera operację przy użyciu tabeli wcześniej wspomniano.  
  
 Klient korzysta z serwera proxy generowanego automatycznie z biblioteki WSDL eksportowanego przez usługę przy użyciu [narzędzia ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Fakt, że akcje wszystkich operacji są puste, nie ma wpływu na kod klienta, z wyjątkiem parametrów akcji w automatycznie generowanym serwerze proxy.  
  
 Kod klienta wykonuje kilka obliczeń. Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć rozwiązanie, postępuj zgodnie z instrukcjami w [tworzeniu przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
