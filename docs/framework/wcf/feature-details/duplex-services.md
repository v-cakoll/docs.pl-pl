---
title: Usługi dwukierunkowe
ms.date: 05/09/2018
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
ms.openlocfilehash: 4fd8b679dcd4ac9efce5fa915118736b15206068
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834768"
---
# <a name="duplex-services"></a>Usługi dwukierunkowe

Kontrakt usługi dupleksowej jest wzorcem wymiany komunikatów, w którym oba punkty końcowe mogą wysyłać wiadomości osobno do siebie. Usługa dupleksowa, dlatego może wysyłać komunikaty z powrotem do punktu końcowego klienta, zapewniając zachowanie podobne do zdarzeń. Komunikacja dupleksowa występuje, gdy klient nawiązuje połączenie z usługą i udostępnia usługę za pomocą kanału, w którym usługa może wysyłać komunikaty z powrotem do klienta. Należy zauważyć, że zachowanie usługi dupleksowej działa wyłącznie w ramach sesji.

Aby utworzyć umowę dupleksową, utworzysz parę interfejsów. Pierwszy to interfejs kontraktu usługi, który opisuje operacje, które mogą być wywoływane przez klienta. Ten kontrakt usługi musi określać *kontrakt wywołania zwrotnego* we właściwości <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType>. Kontrakt wywołania zwrotnego jest interfejsem, który definiuje operacje, które usługa może wywołać w punkcie końcowym klienta. Kontrakt dupleksowy nie wymaga sesji, mimo że powiązania dupleksowe dostępne w systemie korzystają z nich.

Poniżej znajduje się przykład kontraktu dupleksowego.

[!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
[!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]

Klasa `CalculatorService` implementuje interfejs podstawowy `ICalculatorDuplex`. Usługa używa trybu wystąpienia <xref:System.ServiceModel.InstanceContextMode.PerSession>, aby zachować wynik dla każdej sesji. Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania komunikatów z powrotem do klienta za pośrednictwem interfejsu wywołania zwrotnego, jak pokazano w poniższym przykładowym kodzie.

[!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
[!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]

Klient musi dostarczyć klasę, która implementuje interfejs wywołania zwrotnego kontraktu dupleksowego na potrzeby otrzymywania komunikatów z usługi. Poniższy przykładowy kod przedstawia klasę `CallbackHandler` implementującą interfejs `ICalculatorDuplexCallback`.

[!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
[!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]

Klient WCF wygenerowany dla kontraktu dupleksowego wymaga podania klasy <xref:System.ServiceModel.InstanceContext> w czasie konstruowania. Ta klasa <xref:System.ServiceModel.InstanceContext> jest używana jako witryna obiektu, który implementuje interfejs wywołania zwrotnego i obsługuje komunikaty wysyłane z powrotem z usługi. Klasa <xref:System.ServiceModel.InstanceContext> jest zbudowana z wystąpieniem klasy `CallbackHandler`. Ten obiekt obsługuje komunikaty wysyłane z usługi do klienta w interfejsie wywołania zwrotnego.

[!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
[!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]

Konfiguracja usługi musi być skonfigurowana w taki sposób, aby zapewnić powiązanie obsługujące komunikację między sesjami i dupleks. Element `wsDualHttpBinding` obsługuje komunikację z sesją i umożliwia komunikację dwukierunkową przez dostarczanie podwójnych połączeń HTTP, po jednym dla każdego kierunku.

Na kliencie należy skonfigurować adres używany przez serwer do łączenia się z klientem, jak pokazano w poniższej konfiguracji przykładowej.

> [!NOTE]
> Klienci niebędący w trybie dupleksu, którzy nie mogą uwierzytelnić się przy użyciu bezpiecznej konwersacji, zazwyczaj generują <xref:System.ServiceModel.Security.MessageSecurityException>. Jednak w przypadku niepowodzenia uwierzytelniania klienta dwustronnego korzystającego z bezpiecznej konwersacji klient otrzymuje <xref:System.TimeoutException>.

Jeśli utworzysz klienta/usługę przy użyciu elementu `WSHttpBinding`, a punkt końcowy wywołania zwrotnego klienta nie zostanie uwzględniony, zostanie wyświetlony następujący błąd.

```console
HTTP could not register URL
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.
```

Poniższy przykładowy kod przedstawia sposób programowego określania adresu punktu końcowego klienta.

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

Poniższy przykładowy kod pokazuje, jak określić adres punktu końcowego klienta w konfiguracji.

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
> Model dupleksu nie wykrywa automatycznie, gdy usługa lub klient zamknie kanał. Jeśli więc klient nieoczekiwanie zakończy działanie, domyślnie usługa nie zostanie powiadomiona lub jeśli usługa nieoczekiwanie zakończy działanie, klient nie zostanie powiadomiony. W przypadku korzystania z usługi, która jest odłączona, zostanie zgłoszony wyjątek <xref:System.ServiceModel.CommunicationException>. Klienci i usługi mogą wdrożyć własny protokół, aby powiadomić siebie nawzajem o takim wyborze. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz [Obsługa błędów WCF](../wcf-error-handling.md).

## <a name="see-also"></a>Zobacz także

- [Dupleks](../samples/duplex.md)
- [Określanie zachowania klienta w czasie wykonywania](../specifying-client-run-time-behavior.md)
- [Instrukcje: tworzenie fabryki kanałów i używanie jej do tworzenia kanałów oraz zarządzania nimi](how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
