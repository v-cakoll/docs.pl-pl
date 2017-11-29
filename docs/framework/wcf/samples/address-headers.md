---
title: "Nagłówki adresów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 19a7291ce13221e85b49c6ef97c6b375b8b71014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="address-headers"></a>Nagłówki adresów
W przykładzie nagłówki adresów pokazano, jak klienci można przekazywać parametrów odwołania do usługi za pomocą [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Specyfikacja WS-Addressing definiuje pojęcie odwołanie do punktu końcowego sposobów rozwiązania danego punktu końcowego usługi sieci Web. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], odwołania do punktu końcowego są modelowane przy użyciu `EndpointAddress` klasy - `EndpointAddress` jest typem pola adresu `ServiceEndpoint` klasy.  
  
 Część model referencyjny punktu końcowego jest, że każde odwołanie może przenosić niektórych parametrów odwołania, które dodać informacje identyfikacyjne bardzo. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], te parametry odwołania są modelowane jako wystąpienia `AddressHeader` klasy.  
  
 W tym przykładzie klient dodaje parametr odwołania do `EndpointAddress` punktu końcowego klienta. Usługa szuka tego parametru odwołania i używa jej wartość w logice jego operacji usługi "Hello".  
  
## <a name="client"></a>Klient  
 Dla klienta w celu wysyłania parametru odwołania, należy dodać `AddressHeader` do `EndpointAddress` z `ServiceEndpoint`. Ponieważ `EndpointAddress` klasy nie można modyfikować, należy przeprowadzić modyfikacji adresu punktu końcowego za pomocą `EndpointAddressBuilder` klasy. Poniższy kod inicjuje klientowi wysłanie parametru odwołania jako część komunikatu.  
  
```  
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
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
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
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a>Zobacz też
