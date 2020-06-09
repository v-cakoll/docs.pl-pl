---
title: Nagłówki adresów
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 133826bbbea62b660bdcdd884ce657528ad30873
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576008"
---
# <a name="address-headers"></a>Nagłówki adresów

W przykładach nagłówków adresów pokazano, jak klienci mogą przekazywać parametry odwołania do usługi przy użyciu Windows Communication Foundation (WCF).

> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.

Specyfikacja WS-Addressing definiuje pojęcie odwołania do punktu końcowego jako sposób adresowania określonego punktu końcowego usługi sieci Web. W programie WCF odwołania do punktów końcowych są modelowane przy użyciu `EndpointAddress` klasy- `EndpointAddress` jest typem pola Address `ServiceEndpoint` klasy.

Część modelu referencyjnego punktu końcowego polega na tym, że każde odwołanie może zawierać kilka parametrów referencyjnych, które dodają dodatkowe informacje identyfikacyjne. W programie WCF te parametry odwołania są modelowane jako wystąpienia `AddressHeader` klasy.

W tym przykładzie klient dodaje parametr Reference do `EndpointAddress` punktu końcowego klienta. Usługa szuka tego parametru odwołania i używa jego wartości w logice operacji usługi "Hello".

## <a name="client"></a>Klient

Aby klient mógł wysłać parametr referencyjny, musi dodać `AddressHeader` do `EndpointAddress` elementu `ServiceEndpoint` . Ponieważ `EndpointAddress` Klasa jest niezmienna, modyfikowanie adresu punktu końcowego musi być wykonywane przy użyciu `EndpointAddressBuilder` klasy. Poniższy kod inicjuje klienta do wysłania parametru odwołania w ramach jego komunikatu.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

Kod tworzy `EndpointAddressBuilder` oryginalny `EndpointAddress` jako wartość początkową. Następnie dodaje nowo utworzony nagłówek adresu; wywołanie `CreateAddressHeader` tworzenia nagłówka z określoną nazwą, przestrzenią nazw i wartością. Oto wartość "Jan". Po dodaniu nagłówka do konstruktora `ToEndpointAddress()` Metoda konwertuje Konstruktor (mutable) z powrotem na adres punktu końcowego (niezmienny), który jest przypisywany z powrotem do pola adresu punktu końcowego klienta.

Teraz, gdy klient wywołuje `Console.WriteLine(client.Hello());` usługę, może uzyskać wartość tego parametru adresu, jak pokazano w wynikowym wyjściu klienta.

`Hello, John`

## <a name="server"></a>Serwer

Implementacja operacji usługi `Hello()` używa bieżącego `OperationContext` do sprawdzenia wartości nagłówków w komunikacie przychodzącym.

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

Kod wykonuje iterację wszystkich nagłówków komunikatu przychodzącego, szukając nagłówków, które są parametrami odwołań o określonej nazwie i. Po znalezieniu parametru odczytuje wartość parametru i zapisuje je w zmiennej "ID".

#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład

1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Aby skompilować wersję rozwiązania w języku C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](building-the-samples.md).

3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](running-the-samples.md).

> [!IMPORTANT]
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
