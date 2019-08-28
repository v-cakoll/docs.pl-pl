---
title: Pobieranie metadanych
ms.date: 03/30/2017
ms.assetid: e8a6ef8c-a195-495a-a15e-7d92bdf0b28c
ms.openlocfilehash: 83db86ff46d4d1e5d8382c2bd11bce85360d2ff1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038959"
---
# <a name="retrieve-metadata"></a>Pobieranie metadanych
Ten przykład pokazuje, jak wdrożyć klienta, który dynamicznie pobiera metadane z usługi, aby wybrać punkt końcowy, z którym należy się komunikować. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa została zmodyfikowana w celu uwidocznienia dwóch punktów końcowych — punktu końcowego na adresie `basicHttpBinding` podstawowym przy użyciu powiązania oraz bezpiecznego punktu końcowego w lokalizacji {*BaseAddress* `wsHttpBinding` }/Secure przy użyciu powiązania. Zamiast konfigurować klienta z adresami punktów końcowych i powiązaniami, klient dynamicznie pobiera metadane dla usługi przy użyciu <xref:System.ServiceModel.Description.MetadataExchangeClient> klasy, a następnie Importuje metadane <xref:System.ServiceModel.Description.ServiceEndpointCollection> jako za pomocą <xref:System.ServiceModel.Description.WsdlImporter> klasy.  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Aplikacja kliencka używa zaimportowanego <xref:System.ServiceModel.Description.ServiceEndpointCollection> programu do tworzenia klientów do komunikowania się z usługą. Aplikacja kliencka wykonuje iterację przez każdy pobrany punkt końcowy i komunikuje się z każdym punktem `ICalculator` końcowym, który implementuje kontrakt. Odpowiednie adresy i powiązania są dostarczane ze pobranym punktem końcowym, aby klient został skonfigurowany do komunikacji z każdym punktem końcowym, jak pokazano w poniższym przykładowym kodzie.  
  
```csharp   
// Create a MetadataExchangeClient for retrieving metadata.  
EndpointAddress mexAddress = new EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexAddress);  
  
// Retrieve the metadata for all endpoints using metadata exchange protocol (mex).  
MetadataSet metadataSet = mexClient.GetMetadata();  
  
//Convert the metadata into endpoints.  
WsdlImporter importer = new WsdlImporter(metadataSet);  
ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
  
CalculatorClient client = null;  
ContractDescription contract = ContractDescription.GetContract(typeof(ICalculator));  
// Communicate with each endpoint that supports the ICalculator contract.  
foreach (ServiceEndpoint ep in endpoints)  
{  
    if (ep.Contract.Namespace.Equals(contract.Namespace) && ep.Contract.Name.Equals(contract.Name))  
    {  
        // Create a client using the endpoint address and binding.  
        client = new CalculatorClient(ep.Binding, new EndpointAddress(ep.Address.Uri));  
        Console.WriteLine("Communicate with endpoint: ");  
        Console.WriteLine("   AddressPath={0}", ep.Address.Uri.PathAndQuery);  
        Console.WriteLine("   Binding={0}", ep.Binding.Name);  
        // Call operations.  
        DoCalculations(client);  
  
        //Closing the client gracefully closes the connection and cleans up resources.  
        client.Close();  
    }  
}  
```  
  
 W oknie konsoli klienta zostaną wyświetlone operacje wysyłane do każdego z punktów końcowych, w których wyświetlana jest ścieżka adresu i nazwa powiązania.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# C++lub Visual Basic wersję .NET rozwiązania, należy postępować zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\RetrieveMetadata`  
