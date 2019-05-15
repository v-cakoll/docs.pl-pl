---
title: Usługi dwukierunkowe
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: a8197dfc877842be824a5b10c742ef4fb7792858
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592749"
---
# <a name="duplex-services"></a>Usługi dwukierunkowe

Kontrakt usługi dwustronnej jest wymiany komunikatów, w którym obu punktów końcowych może wysyłać komunikaty do innych niezależnie. Usługi duplex, dlatego wiadomości można wysyłać do punktu końcowego klienta, zapewniając zachowanie podobne zdarzenia. Komunikację dupleksową występuje, gdy klient łączy się z usługą i udostępnia usługi za pomocą kanału, na którym usługa może wysłać wiadomości zwrotnie do klienta. Należy pamiętać, że zachowanie podobne zdarzenia usługi dwukierunkowe działa tylko w ramach sesji.

Aby utworzyć kontrakt dupleksowy należy utworzyć dwa interfejsy. Pierwsza to interfejsu kontraktu usługi, który opisuje operacje, które mogą być wywoływane przez klienta. Należy określić ten kontrakt usługi *kontrakt wywołania zwrotnego* w <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości. Kontrakt wywołania zwrotnego jest interfejsem, który definiuje operacje, które usługa może wywołać w punkcie końcowym klienta. Kontraktu dwukierunkowego nie wymaga sesję, mimo że dwukierunkowego powiązania dostarczane przez system, należy korzystać z nich.

Oto przykład kontraktu dwukierunkowego.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

`CalculatorService` Klasa implementuje podstawowy `ICalculatorDuplex` interfejsu. Używa usługi <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia do obsługi wyników dla każdej sesji. Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejs wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

Klient musi podać klasę, która implementuje interfejs wywołania zwrotnego kontraktu dwukierunkowego, do odbierania wiadomości z usługi. Poniższy przykładowy kod przedstawia `CallbackHandler` klasę, która implementuje `ICalculatorDuplexCallback` interfejsu.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

Klient WCF, który jest generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> klasy, należy podać podczas konstruowania. To <xref:System.ServiceModel.InstanceContext> klasa jest używana jako witryna dla obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje wiadomości wysyłanych na odpowiedź od usługi. <xref:System.ServiceModel.InstanceContext> Klasy składa się z wystąpieniem `CallbackHandler` klasy. Ten obiekt obsługi komunikatów wysyłanych z usługi na kliencie, na interfejs wywołania zwrotnego.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

Konfiguracji usługi należy skonfigurować umożliwia powiązanie, które obsługuje zarówno sesji komunikacji, jak i komunikację dupleksową. `wsDualHttpBinding` Element obsługuje komunikację sesji i umożliwia komunikację dupleksową, zapewniając dwa połączenia HTTP, jedno dla każdego kierunku.

Na komputerze klienckim należy skonfigurować adres serwera służy do połączenia z klientem, jak pokazano w poniższym Przykładowa konfiguracja.

> [!NOTE]
> Throw klientów non-duplex, którzy nie próbę uwierzytelnienia przy użyciu bezpiecznej konwersacji zazwyczaj <xref:System.ServiceModel.Security.MessageSecurityException>. Jednak jeśli dwukierunkowego klienta, który używa bezpiecznej konwersacji uwierzytelnianie zakończy się niepowodzeniem, klient odbierze <xref:System.TimeoutException> zamiast tego.

Jeśli utworzysz klienta/usługi przy użyciu `WSHttpBinding` elementu i nie mają punkt końcowy wywołania zwrotnego klienta, zostanie wyświetlony następujący błąd.

```
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

Następujący przykładowy kod przedstawia sposób określania klienta adres punktu końcowego programowo.

```csharp
WSDualHttpBinding binding = new WSDualHttpBinding();
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");
```

```vb
Dim binding As New WSDualHttpBinding()
Dim endptadr As New EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server")
binding.ClientBaseAddress = New Uri("http://localhost:8000/DuplexTestUsingCode/Client/")
```

Poniższy przykład kodu pokazuje, jak określić klienta adres punktu końcowego w konfiguracji.

```xml
<client>
    <endpoint name ="ServerEndpoint"
          address="http://localhost:12000/DuplexTestUsingConfig/Server"
          bindingConfiguration="WSDualHttpBinding_IDuplexTest"
            binding="wsDualHttpBinding"
           contract="IDuplexTest" />
</client>
<bindings>
    <wsDualHttpBinding>
        <binding name="WSDualHttpBinding_IDuplexTest"
          clientBaseAddress="http://localhost:8000/myClient/" >
            <security mode="None"/>
         </binding>
    </wsDualHttpBinding>
</bindings>
```

> [!WARNING]
> Automatycznie dwukierunkowego modelu nie wykrywa usługi lub klienta powoduje zamknięcie kanału. Dlatego jeśli klient zakończy się nieoczekiwanie, domyślnie Usługa nie będzie powiadamiany lub gdy następuje nieoczekiwane zakończenie usługi, klient nie będzie powiadamiany. Klienci i usługi mogą implementować własne protokół do siebie powiadomienie, jeśli dokonają takiego wyboru. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [obsługę błędów programu WCF](../wcf-error-handling.md)

## <a name="see-also"></a>Zobacz także

- [Dupleks](../samples/duplex.md)
- [Określanie zachowania klienta w czasie wykonywania](../specifying-client-run-time-behavior.md)
- [Instrukcje: Tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
