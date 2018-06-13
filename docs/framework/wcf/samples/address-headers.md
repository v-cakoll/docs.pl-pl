---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 276649c17a04822eb27eb4e3ed9cbe711b384edc
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803793"
---
# <a name="address-headers"></a>Nagłówki adresów
Przykładowy adres nagłówki pokazano, jak klientów można przekazywać parametrów odwołania do usługi przy użyciu usługi Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Specyfikacja WS-Addressing definiuje pojęcie odwołanie do punktu końcowego sposobów rozwiązania danego punktu końcowego usługi sieci Web. W programie WCF, odwołania do punktu końcowego są modelowane przy użyciu `EndpointAddress` klasy - `EndpointAddress` jest typem pola adresu `ServiceEndpoint` klasy.  
  
 Część model referencyjny punktu końcowego jest, że każde odwołanie może przenosić niektórych parametrów odwołania, które dodać informacje identyfikacyjne bardzo. W programie WCF, te parametry odwołania są modelowane jako wystąpienia `AddressHeader` klasy.  
  
 W tym przykładzie klient dodaje parametr odwołania do `EndpointAddress` punktu końcowego klienta. Usługa szuka tego parametru odwołania i używa jej wartość w logice jego operacji usługi "Hello".  
  
## <a name="client"></a>Klient  
 Dla klienta w celu wysyłania parametru odwołania, należy dodać `AddressHeader` do `EndpointAddress` z `ServiceEndpoint`. Ponieważ `EndpointAddress` klasy nie można modyfikować, należy przeprowadzić modyfikacji adresu punktu końcowego za pomocą `EndpointAddressBuilder` klasy. Poniższy kod inicjuje klientowi wysłanie parametru odwołania jako część komunikatu.  
  
```csharp   
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 Kod tworzy `EndpointAddressBuilder` za pomocą `EndpointAddress` jako wartości początkowej. Następnie dodaje nagłówek nowo utworzonego adresu; wywołanie `CreateAddressHeadercreates` nagłówka o określonej nazwie, przestrzeni nazw i wartości. W tym miejscu wartość to "Jan". Po dodaniu do konstruktora, nagłówek `ToEndpointAddress()` metoda konwertuje (modyfikowalne) konstruktora do adresu punktu końcowego (niezmienne), który jest przypisany do pola adresu punktu końcowego klienta.  
  
 Teraz, kiedy klient wywołuje `Console.WriteLine(client.Hello());`, usługa jest w stanie uzyskać wartość tego parametru adresu w dane wyjściowe klienta.  
  
 `Hello, John`  
  
## <a name="server"></a>Serwer  
 Wykonanie operacji usługi `Hello()` używa bieżącej `OperationContext` sprawdzić wartości nagłówków w komunikacie przychodzącym.  
  
```csharp   
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 Ten kod przechodzi przez wszystkie nagłówki w komunikacie przychodzącym wyszukiwania dla nagłówków, które są parametry odwołanie o określonej nazwie i. Po znalezieniu parametr wartość parametru odczytuje i zapisuje je w zmiennej "id".  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Zobacz też
