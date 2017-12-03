---
title: "Usługi dwukierunkowe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 396b875a-d203-4ebe-a3a1-6a330d962e95
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a5c7cb9d963e56c6a6e06421afdb14427440643c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="duplex-services"></a>Usługi dwukierunkowe
Kontrakt usługi dwustronnej jest wymiany komunikatów w których oba punkty końcowe można wysyłać wiadomości do innych niezależnie. Usługi duplex, w związku z tym wiadomości można wysyłać do punktu końcowego klienta, zapewniając zdarzenia podobne zachowania. Komunikację dupleksową występuje, gdy klient nawiąże połączenie z usługą i zapewnia usługę, z kanałem, na którym usługa można wysłać wiadomości zwrotnie do klienta. Należy pamiętać, że zachowanie podobnych zdarzeń usługi dwukierunkowe działa tylko w ramach sesji.  
  
 Aby utworzyć kontrakt dupleksowy, należy utworzyć dwa interfejsy. Pierwszy jest interfejsem kontraktu usługi, który zawiera opis czynności, które klient może wywołać. Ten kontrakt usługi musi określać *kontrakt wywołania zwrotnego* w <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A?displayProperty=nameWithType> właściwości. Kontrakt wywołania zwrotnego to interfejs, który definiuje operacje, które usługa może wywoływać klienta w punkcie końcowym. Kontrakt dupleksowy nie wymaga sesji, mimo że dwukierunkowego powiązania dostarczane przez system, należy korzystać z nich.  
  
 Oto przykład kontraktu dwukierunkowego.  
  
 [!code-csharp[c_DuplexServices#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#0)]
 [!code-vb[c_DuplexServices#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#0)]  
  
 `CalculatorService` Klasa implementuje podstawową `ICalculatorDuplex` interfejsu. Używane przez usługę <xref:System.ServiceModel.InstanceContextMode.PerSession> tryb wystąpienia przechowywać wynik dla każdej sesji. Właściwość prywatna o nazwie `Callback` uzyskuje dostęp do kanału wywołania zwrotnego do klienta. Usługa używa wywołania zwrotnego do wysyłania wiadomości do klienta za pośrednictwem interfejsu wywołania zwrotnego, jak pokazano w poniższym kodzie próbki.  
  
 [!code-csharp[c_DuplexServices#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/service.cs#1)]
 [!code-vb[c_DuplexServices#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/service.vb#1)]  
  
 Klient musi dostarczyć klasy, która implementuje interfejs wywołania zwrotnego kontrakt dupleksu do odbierania wiadomości z usługi. Poniższy przykładowy kod przedstawia `CallbackHandler` klasa implementująca `ICalculatorDuplexCallback` interfejsu.  
  
 [!code-csharp[c_DuplexServices#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#2)]
 [!code-vb[c_DuplexServices#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#2)]  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Klienta, który jest generowany dla kontraktu dwukierunkowego wymaga <xref:System.ServiceModel.InstanceContext> klasę, aby podać po konstrukcji. To <xref:System.ServiceModel.InstanceContext> klasa jest używana jako witryna dla obiekt, który implementuje interfejs wywołania zwrotnego i obsługi wiadomości, które są wysyłane z usługi. <xref:System.ServiceModel.InstanceContext> Klasy jest tworzony przy użyciu wystąpienia `CallbackHandler` klasy. Ten obiekt obsługi komunikatów wysyłanych z usługi do klienta w interfejsie wywołania zwrotnego.  
  
 [!code-csharp[c_DuplexServices#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_duplexservices/cs/client.cs#3)]
 [!code-vb[c_DuplexServices#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_duplexservices/vb/client.vb#3)]  
  
 Konfiguracji usługi musi skonfigurować ma zostać udostępnione wiązanie, która obsługuje zarówno sesji komunikacji i komunikację dupleksową. `wsDualHttpBinding` Elementu obsługuje komunikację sesji i umożliwia komunikację dupleksową zapewniając dwa połączenia HTTP, po jednej dla każdego kierunku.  
  
 Na komputerze klienckim należy skonfigurować adres serwera można użyć do nawiązania połączenia klienta, jak pokazano w poniższych Przykładowa konfiguracja.  
  
  
  
> [!NOTE]
>  Throw non-duplex klientów, którzy nie mogą się uwierzytelnić, zwykle za pomocą bezpiecznej konwersacji <xref:System.ServiceModel.Security.MessageSecurityException>. Jednak jeśli dupleksu klienta, który używa bezpiecznej konwersacji uwierzytelnianie zakończy się niepowodzeniem, klient odbierze <xref:System.TimeoutException> zamiast tego.  
  
 W przypadku utworzenia przy użyciu klienta/usługa `WSHttpBinding` elemencie i użytkownik nie ma punktu końcowego wywołania zwrotnego klienta, zostanie wyświetlony następujący błąd.  
  
```  
HTTP could not register URL  
htp://+:80/Temporary_Listen_Addresses/<guid> because TCP port 80 is being used by another application.  
```  
  
 Następujący przykładowy kod przedstawia sposób określić klienta adres punktu końcowego w kodzie.  
  
```  
WSDualHttpBinding binding = new WSDualHttpBinding();  
EndpointAddress endptadr = new EndpointAddress("http://localhost:12000/DuplexTestUsingCode/Server");  
binding.ClientBaseAddress = new Uri("http://localhost:8000/DuplexTestUsingCode/Client/");  
```  
  
 Następujący przykładowy kod przedstawia sposób określić klienta adres punktu końcowego w konfiguracji.  
  
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
>  Automatycznie dupleksu modelu nie wykrywa usługi lub klienta powoduje zamknięcie kanału. Dlatego jeśli klienta zakończy się nieoczekiwanie, domyślnie Usługa nie zostanie poinformowany lub jeśli klienta zakończy się nieoczekiwanie, usługa nie będzie powiadamiany. Klienci i usługi można zaimplementować własnych protokołu do siebie powiadomienia, gdy wybiera on.  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikacja dwukierunkowa](../../../../docs/framework/wcf/samples/duplex.md)  
 [Określanie zachowania klienta w czasie wykonywania](../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)  
 [Porady: tworzenie fabryki kanałów i używać go do tworzenia kanałów oraz zarządzania nimi](../../../../docs/framework/wcf/feature-details/how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels.md)
