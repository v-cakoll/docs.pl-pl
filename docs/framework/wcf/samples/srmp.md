---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 5c2079f1aa90821448c88de53d311d064bb6e65b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="srmp"></a>SRMP
W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.  
  
 W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła wiadomości do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.  
  
 Usługa MSMQ umożliwia korzystanie z protokołu HTTP (łącznie z użyciem protokołu HTTPS) do wysyłania wiadomości do kolejki. W tym przykładzie mamy pokazują, że za pomocą usługi Windows Communication Foundation (WCF) w kolejce komunikacji i jak należy wysyłać komunikaty za pośrednictwem protokołu HTTP. Usługa MSMQ używa protokołu o nazwie SRMP, czyli opartego na protokole SOAP protokołu komunikacji za pośrednictwem protokołu HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Przed uruchomieniem próbki w **Dodaj/Usuń składniki systemu Windows**, upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP. Instalowanie obsługi protokołu HTTP automatycznie instaluje usługi Internet Information Services (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.  
  
5.  Jeśli chcesz mieć pewność, że używany do komunikacji HTTP, można włączyć usługi MSMQ do pracy w trybie zaostrzonym. Dzięki temu, że żadnych komunikatów do kolejkach obsługiwanych na maszynie można dostarczone przy użyciu dowolnego innego niż HTTP transportu.  
  
6.  Po wybraniu usługi MSMQ do pracy w trybie zaostrzonym komputer wymaga ponownego rozruchu na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Uruchom usługę.  
  
8.  Uruchom klienta. Upewnij się, musisz zmienić adres punktu końcowego, aby wskazywała nazwę komputera lub adresu IP, a localhost. Klient wysyła komunikat i kończy działanie.  
  
## <a name="requirements"></a>Wymagania  
 Aby uruchomić ten przykład, usługi IIS musi być zainstalowany na usługi i komputerów klienckich, oprócz usługi MSMQ.  
  
## <a name="demonstrates"></a>Demonstracje  
 W przykładzie pokazano, wysyłanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] za pośrednictwem protokołu HTTP przy użyciu usługi MSMQ wiadomości w kolejce. Jest to tak zwane SRMP wiadomości. Kiedy wiadomość w kolejce jest wysyłane, usługi MSMQ na wysyłanie przeniesień maszyny komunikaty odbierającego menedżera kolejek przy użyciu transportu TCP lub HTTP. Wybierając SRMP użytkownik wskazuje wybór HTTP jako transportu do przeniesienia kolejki. Zabezpieczanie SRMP umożliwia korzystanie z protokołu HTTPS.  
  
## <a name="example"></a>Przykład  
 Przykładowy kod jest oparta na przykład transakcyjne. Jak wysłać wiadomości do kolejki i odbierania wiadomości z kolejki przy użyciu SRMP jest taka sama jak wysyłanie i odbieranie komunikatów za pomocą natywnego protokołu.  
  
 Aby wskazać wybór protokół transferu kolejki jest zmieniła się konfiguracja klienta. Protokół transferu kolejki może być jedną z macierzystego, SRMP lub SrmpSecure. Domyślnie protokół transferu ma wartość Native. Klient i usługa określ w konfiguracji, aby użyć SRMP w tym przykładzie.  
  
 Istnieją pewne ograniczenia SRMP w odniesieniu do zabezpieczeń transportu. Domyślne zabezpieczenia transportu usługi MSMQ wymaga usługi Active Directory wymaga, aby wysyłania menedżera kolejek i odbierającego menedżera kolejek znajdują się w tej samej domenie systemu Windows. Nie jest możliwe podczas wysyłania wiadomości za pośrednictwem protokołu HTTP granic. W efekcie domyślne zabezpieczenia transportu nie działa. Zabezpieczenia transportu musi mieć ustawioną certyfikatu, jeśli wymagane jest zabezpieczeń transportu. Zabezpieczenia komunikatów mogą służyć do zabezpieczenia wiadomości. W tym przykładzie zabezpieczenia transportowe i wiadomość jest wyłączone w celu zilustrowania SRMP wiadomości.  
  
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
          <security mode="None"></security>  
        </binding>  
      </netMsmqBinding>  
    </bindings>  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Uruchamianie przykładowej daje następujące dane wyjściowe.  
  
```  
Processing Purchase Order: 556b70be-31ee-4a3b-8df4-ed5e538015a4   
Customer: somecustomer.com   
OrderDetails   
    Order LineItem: 54 of Blue Widget @unit price: $29.99   
    Order LineItem: 890 of Red Widget @unit price: $45.89   
    Total cost of this order: $42461.56   
    Order status: Pending  
```  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
  
## <a name="see-also"></a>Zobacz też
