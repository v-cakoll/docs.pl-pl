---
title: Opis usługi
ms.date: 03/30/2017
ms.assetid: 7034b5d6-d608-45f3-b57d-ec135f83ff24
ms.openlocfilehash: d77797ed2871f2211ff142e2f45c160a92632138
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144090"
---
# <a name="service-description"></a>Opis usługi
Przykład opisu usługi pokazuje, jak usługa może pobrać informacje o opisie usługi w czasie wykonywania. Próbka jest oparta na [wprowadzenie,](../../../../docs/framework/wcf/samples/getting-started-sample.md)z dodatkową operacją usługi zdefiniowane do zwracania opisowych informacji o usłudze. Informacje, które są zwracane, zawiera listę adresów podstawowych i punktów końcowych dla usługi. Usługa udostępnia te informacje <xref:System.ServiceModel.OperationContext> <xref:System.ServiceModel.ServiceHost>za <xref:System.ServiceModel.Description.ServiceDescription> pomocą , i klas.  
  
 W tym przykładzie klient jest aplikacją konsoli (.exe), a usługa jest obsługiwana przez internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Ten przykład ma zmodyfikowaną wersję kontraktu `IServiceDescriptionCalculator`kalkulatora o nazwie . Umowa definiuje dodatkową operację usługi `GetServiceDescriptionInfo` o nazwie, która zwraca ciąg wielowierszowy do klienta, który opisuje adres podstawowy lub adresy i punkt końcowy usługi lub punkty końcowe dla usługi.  
  
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
  
 Kod implementacji `GetServiceDescriptionInfo` używa <xref:System.ServiceModel.Description.ServiceDescription> do listy punktów końcowych usługi. Ponieważ punkty końcowe usługi mogą mieć względne adresy, najpierw wyświetla adresy podstawowe usługi. Aby uzyskać wszystkie te informacje, kod uzyskuje <xref:System.ServiceModel.OperationContext.Current%2A>jego kontekst operacji przy użyciu . I <xref:System.ServiceModel.ServiceHost> jego <xref:System.ServiceModel.Description.ServiceDescription> obiekt są pobierane z kontekstu operacji. Aby wyświetlić listę podstawowych punktów końcowych dla usługi, kod iteruje za pośrednictwem kolekcji hosta <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A> usługi. Aby wyświetlić listę punktów końcowych usługi dla usługi, kod iteruje za pośrednictwem kolekcji punktów końcowych opisu usługi.  
  
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
  
 Po uruchomieniu próbki, zostanie wyświetlony operacji kalkulatora, a następnie `GetServiceDescriptionInfo` informacje o usłudze zwrócone przez operację. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ServiceDescription`  
