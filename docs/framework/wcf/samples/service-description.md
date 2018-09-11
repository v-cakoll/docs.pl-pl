---
title: Opis usługi
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 1acd82fddd378a379023c7aa46ead2ce36c5b243
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342599"
---
# <a name="service-description"></a>Opis usługi
Przykładowy opis usługi pokazuje, jak usługa można pobrać jego informacje o opisie usługi w czasie wykonywania. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md), z operacją dodatkowych usług zdefiniowane, zwracają opisowe informacje na temat usługi. Informacje, która jest zwracana Wyświetla adresy podstawowe i punktów końcowych usługi. Te informacje przy użyciu udostępnianych przez usługę <xref:System.ServiceModel.OperationContext>, <xref:System.ServiceModel.ServiceHost>, i <xref:System.ServiceModel.Description.ServiceDescription> klasy.  
  
 W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 W tym przykładzie została zmodyfikowana wersja kontraktu Kalkulator, o nazwie `IServiceDescriptionCalculator`. Kontrakt definiuje operacji dodatkowej usługi o nazwie `GetServiceDescriptionInfo` zwracającego ciąg wielowierszowy do klienta, który opisuje podstawowy adres lub adresy i punkt końcowy usługi lub punktów końcowych usługi.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IServiceDescriptionCalculator  
{  
    [OperationContract]  
    int Add(int n1, int n2);  
    [OperationContract]  
    int Subtract(int n1, int n2);  
    [OperationContract]  
    int Multiply(int n1, int n2);  
    [OperationContract]  
    int Divide(int n1, int n2);  
    [OperationContract]  
    string GetServiceDescriptionInfo();  
}  
```  
  
 Kod implementacji `GetServiceDescriptionInfo` używa <xref:System.ServiceModel.Description.ServiceDescription> Aby wyświetlić listę punktów końcowych usługi. Ponieważ punktów końcowych usługi może mieć względnych adresów, najpierw Wyświetla adres podstawowy dla usługi. Aby uzyskać wszystkie te informacje, kod uzyskuje jego operacji kontekstu za pomocą <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> i jego <xref:System.ServiceModel.Description.ServiceDescription> obiektu są pobierane z kontekstu operacji. Aby wyświetlić listę podstawowych punktów końcowych usługi, kod wykonuje iterację przez hosta usługi <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> kolekcji. Aby wyświetlić listę punktów końcowych usługi dla usługi, kodu iteruje po kolekcji punktów końcowych opisu usługi.  
  
```  
public string GetServiceDescriptionInfo()  
{  
    string info = "";  
    OperationContext operationContext = OperationContext.Current;  
    ServiceHost host = (ServiceHost)operationContext.Host;  
    ServiceDescription desc = host.Description;  
    // Enumerate the base addresses in the service host.  
    info += "Base addresses:\n";  
    foreach (Uri uri in host.BaseAddresses)  
    {  
        info += "    " + uri + "\n";  
    }  
    // Enumerate the service endpoints in the service description.  
    info += "Service endpoints:\n";  
    foreach (ServiceEndpoint endpoint in desc.Endpoints)  
    {  
        info += "    Address:  " + endpoint.Address + "\n";  
        info += "    Binding:  " + endpoint.Binding.Name + "\n";  
        info += "    Contract: " + endpoint.Contract.Name + "\n";  
    }  
     return info;  
}  
```  
  
 Po uruchomieniu przykładu, zobacz operacje obliczeniowe, a następnie informacji usługi zwracanych przez `GetServiceDescriptionInfo` operacji. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
```  
Add(15,3) = 18  
Subtract(145,76) = 69  
Multiply(9,81) = 729  
Divide(22,7) = 3  
GetServiceDescriptionInfo  
Base addresses:  
    http://<machine-name>/ServiceModelSamples/service.svc  
    https://<machine-name>/ServiceModelSamples/service.svc  
Service endpoints:  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc  
    Binding:  WSHttpBinding  
    Contract: IServiceDescriptionCalculator  
    Address:  http://<machine-name>/ServiceModelSamples/service.svc/mex  
    Binding:  MetadataExchangeHttpBinding  
    Contract: IMetadataExchange  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
  
## <a name="see-also"></a>Zobacz też
