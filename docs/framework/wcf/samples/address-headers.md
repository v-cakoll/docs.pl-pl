---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 4ccb309178251b32068d6cdbb81874322f991bb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002953"
---
# <a name="address-headers"></a>Nagłówki adresów

W przykładzie nagłówki adresów pokazano, jak klienci parametry można przekazać odwołanie do usługi przy użyciu usługi Windows Communication Foundation (WCF).

> [!NOTE]
> Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.

Specyfikacja WS-Addressing definiuje pojęcie odwołania do punktu końcowego jako sposób adresu określonego punktu końcowego usługi sieci Web. W programie WCF, odwołania do punktu końcowego są modelowane przy użyciu `EndpointAddress` , klasa — `EndpointAddress` jest typem pola adres `ServiceEndpoint` klasy.

Część model referencyjny punkt końcowy jest, że każde odwołanie może wykonywać niektóre parametry odwołań, dodających informacje identyfikacyjne dodatkowych. W programie WCF, parametry te odwołania są modelowane jako wystąpień obiektu `AddressHeader` klasy.

W tym przykładzie klient dodaje parametr przekazany przez odwołanie do `EndpointAddress` punktu końcowego klienta. Usługa szuka tego parametru odwołania i używa jej wartości w logice jego działania usługi "Hello".

## <a name="client"></a>Klient

Dla klienta, aby wysyłać parametr przekazany przez odwołanie, należy dodać `AddressHeader` do `EndpointAddress` z `ServiceEndpoint`. Ponieważ `EndpointAddress` klasy jest niezmienny, musi odbywać się modyfikacja adresu punktu końcowego przy użyciu `EndpointAddressBuilder` klasy. Poniższy kod inicjuje to klientowi wysłanie parametr przekazany przez odwołanie jako część komunikatu.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

Ten kod tworzy `EndpointAddressBuilder` przy użyciu oryginalnego `EndpointAddress` jako początkowej wartości. Następnie dodaje adres nowoutworzonego nagłówka. wywołanie `CreateAddressHeader` tworzy nagłówek o określonej nazwie, przestrzeni nazw i wartości. W tym miejscu wartość "John". Po dodaniu do konstruktora, nagłówek `ToEndpointAddress()` metoda konwertuje konstruktora (mutable) do adresu punktu końcowego (niezmiennego), która jest przypisana do pola Adres punktu końcowego klienta.

Teraz, kiedy klient wywołuje `Console.WriteLine(client.Hello());`, usługa jest w stanie uzyskać wartość tego parametru adresu jak widać na dane wyjściowe z klienta.

`Hello, John`

## <a name="server"></a>Serwer

Wykonanie operacji usługi `Hello()` używa bieżącej `OperationContext` sprawdzić wartości nagłówków w wiadomości przychodzącej.

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

Kod wykonuje iterację na wszystkie nagłówki dla wiadomości przychodzących, szukasz nagłówki, które są parametrami odwołanie o określonej nazwie i. W przypadku odnalezienia parametru odczytuje wartość parametru i zapisuje ją w zmiennej "id".

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej

1. Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
