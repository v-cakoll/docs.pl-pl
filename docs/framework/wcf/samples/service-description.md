---
title: Opis usługi
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: 430079cab91c61fe28db3f0a9d6c0797c7b0278a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038853"
---
# <a name="service-description"></a>Opis usługi
Przykład opisu usługi pokazuje, jak usługa może pobrać informacje o opisie usługi w czasie wykonywania. Przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md)z dodatkową operacją usługi zdefiniowaną w celu zwrócenia opisowych informacji o usłudze. Zwracane informacje wyświetlają adresy podstawowe i punkty końcowe usługi. Ta usługa udostępnia te informacje przy użyciu <xref:System.ServiceModel.OperationContext>klas <xref:System.ServiceModel.ServiceHost>, i <xref:System.ServiceModel.Description.ServiceDescription> .  
  
 W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład ma zmodyfikowaną wersję kontraktu kalkulatora o nazwie `IServiceDescriptionCalculator`. Kontrakt definiuje dodatkową operację usługi o nazwie `GetServiceDescriptionInfo` , która zwraca ciąg wielowierszowy do klienta, który opisuje adres podstawowy lub adresy oraz punkt końcowy usługi lub punkty końcowe usługi.  
  
```csharp
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
  
 Kod implementacji dla `GetServiceDescriptionInfo` programu <xref:System.ServiceModel.Description.ServiceDescription> używa do wyświetlania listy punktów końcowych usługi. Ponieważ punkty końcowe usługi mogą mieć adresy względne, najpierw wyświetlają adresy podstawowe dla usługi. Aby uzyskać wszystkie te informacje, kod uzyskuje kontekst operacji przy użyciu <xref:System.ServiceModel.OperationContext.Current%2A>. <xref:System.ServiceModel.ServiceHost> I jego<xref:System.ServiceModel.Description.ServiceDescription> obiekt jest pobierany z kontekstu operacji. Aby wyświetlić listę podstawowych punktów końcowych dla usługi, kod wykonuje iterację w <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> kolekcji hosta usługi. Aby wyświetlić listę punktów końcowych usługi dla usługi, kod wykonuje iterację w kolekcji punktów końcowych opisu usługi.  
  
```csharp
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
  
 Po uruchomieniu przykładu, zobaczysz operacje kalkulatora, a następnie informacje o usłudze zwrócone przez `GetServiceDescriptionInfo` operację. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
```console  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
