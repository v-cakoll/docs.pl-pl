---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: b1b61c18c801059e95cd0b13a3135132a583882f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183337"
---
# <a name="srmp"></a>SRMP
W tym przykładzie pokazano, jak wykonywać komunikację w kolejce za pomocą usługi kolejkowania wiadomości (MSMQ) za pośrednictwem protokołu HTTP.  
  
 W komunikacji w kolejce klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła wiadomości do kolejki. Usługa odbiera wiadomości z kolejki. W związku z tym usługi i klienta, nie muszą być uruchomione w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Usługa MSMQ umożliwia używanie protokołu HTTP (w tym korzystania z protokołu HTTPS) do wysyłania wiadomości do kolejki. W tym przykładzie zademonstrujemy przy użyciu komunikacji w kolejce programu Windows Communication Foundation (WCF) i jak wysyłać wiadomości za pośrednictwem protokołu HTTP. Usługa MSMQ używa protokołu o nazwie SRMP, który jest protokołem opartym na mydle do komunikacji za pośrednictwem protokołu HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić próbkę w konfiguracji z jednym lub krzyżowym komputerem, postępuj zgodnie z instrukcjami w [programie Uruchamianie przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Przed uruchomieniem próbki w **add/remove Windows Components**należy upewnić się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP. Zainstalowanie obsługi protokołu HTTP automatycznie instaluje internetowe usługi informacyjne (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.  
  
5. Jeśli chcesz mieć pewność, że protokół HTTP jest używany do komunikacji, możesz włączyć obsługę usługi MSMQ w trybie wzmocnionym. Dzięki temu żadne wiadomości do dowolnej kolejki hostowane na komputerze można dotrzeć przy użyciu dowolnego transportu innego niż HTTP.  
  
6. Po wybraniu usługi MSMQ do uruchomienia w trybie wzmocnionym komputer wymaga ponownego rozruchu w systemie Windows Server 2003.  
  
7. Uruchom usługę.  
  
8. Uruchom klienta. Upewnij się, że zmienisz adres punktu końcowego, aby wskazać nazwę komputera lub adres IP zamiast localhost. Klient wysyła wiadomość i kończy pracę.  
  
## <a name="requirements"></a>Wymagania  
 Aby uruchomić ten przykład, usługi IIS muszą być zainstalowane zarówno na usłudze, jak i na komputerach klienckich oprócz usługi MSMQ.  
  
## <a name="demonstrates"></a>Demonstracje  
 W przykładzie pokazano wysyłanie wiadomości w kolejce WCF przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP. Jest to również nazywane wiadomościami SRMP. Po wysłaniu wiadomości w kolejce usługa MSMQ na komputerze wysyłającym przenosi wiadomości do menedżera kolejek odbierających za pośrednictwem transportu TCP lub HTTP. Wybierając protokół SRMP, użytkownik wskazuje wybór protokołu HTTP jako transportu do transferu kolejek. SRMP Secure umożliwia korzystanie z protokołu HTTPS.  
  
## <a name="example"></a>Przykład  
 Przykładowy kod jest oparty na próbce transakcji. Sposób wysyłania wiadomości do kolejki i odbierania wiadomości z kolejki przy użyciu protokołu SRMP jest taki sam jak wysyłanie i odbieranie wiadomości przy użyciu protokołu macierzystego.  
  
 Konfiguracja klienta zostanie zmieniona, aby wskazać wybór protokołu transferu kolejki. Protokół transferu kolejki może być jednym z Native, SRMP lub SrmpSecure. Domyślnie protokół transferu jest macierzysty. Klient i usługa określić w konfiguracji, aby użyć SRMP w tym przykładzie.  
  
 Istnieją ograniczenia dotyczące SRMP w odniesieniu do bezpieczeństwa transportu. Domyślne zabezpieczenia transportu usługi MSMQ wymagają usługi Active Directory, która wymaga, aby menedżer kolejek wysyłających i menedżer kolejek odbierających rezydują w tej samej domenie systemu Windows. Nie jest to możliwe podczas wysyłania wiadomości za pośrednictwem granicy HTTP. W związku z tym domyślne zabezpieczenia transportu nie działa. Zabezpieczenia transportu musi być ustawiona na Certyfikat, jeśli jest to pożądane zabezpieczeń transportu. Zabezpieczenia wiadomości mogą być również używane do zabezpieczania wiadomości. W tym przykładzie zabezpieczeń transportu i wiadomości jest wyłączony, aby zilustrować wiadomości SRMP.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  
  <system.serviceModel>  
  
    <client>  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint name="OrderProcessorEndpoint"  
           address=  
          "net.msmq://localhost/private/ServiceModelSamplesSrmp"
           bindingConfiguration="srmpBinding"
           binding="netMsmqBinding"
           contract="IOrderProcessor" />  
    </client>  
    <bindings>  
      <netMsmqBinding>  
        <binding name="srmpBinding"  
                 queueTransferProtocol="Srmp">  
          <security mode="None" />  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Uruchamianie próbki daje następujące dane wyjściowe.  
  
```console  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4
Customer: somecustomer.com
OrderDetails
    Order LineItem: 54 of Blue Widget @unit price: $29.99
    Order LineItem: 890 of Red Widget @unit price: $45.89
    Total cost of this order: $42461.56
    Order status: Pending  
```  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
