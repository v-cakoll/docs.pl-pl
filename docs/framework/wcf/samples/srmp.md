---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 108293a5f4607afb8c19dce65d53efdaf9e184b1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210467"
---
# <a name="srmp"></a>SRMP
W tym przykładzie pokazano, jak wykonać transakcyjnych w kolejce komunikacji przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.  
  
 W komunikacie w kolejce klient komunikuje się z usługą przy użyciu kolejki. Mówiąc ściślej klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. Usługi i klienta w związku z tym, nie musi być uruchomiona w tym samym czasie do komunikowania się za pomocą kolejki.  
  
 Usługi MSMQ umożliwia korzystanie z protokołu HTTP (w tym użycie protokołu HTTPS), aby wysyłać komunikaty do kolejki. W tym przykładzie firma Microsoft pokazują, czy przy użyciu usługi Windows Communication Foundation (WCF) w kolejce komunikacji oraz jak wysyłać komunikaty za pośrednictwem protokołu HTTP. Usługa MSMQ używa protokołu o nazwie SRMP, czyli opartego na protokole SOAP protokół komunikacji za pośrednictwem protokołu HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub wielu maszyny, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4.  Przed uruchomieniem przykładu **Dodaj/Usuń składniki Windows**, upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP. Instalowanie obsługi HTTP automatycznie instaluje Internet Information Services (IIS) i dodaje obsługę protokołu w usługach IIS dla usługi MSMQ.  
  
5.  Jeśli chcesz mieć pewność, że HTTP jest używany do komunikacji, można włączyć usługi MSMQ do pracy w trybie zaostrzonym. Daje to gwarancję, że żadnych komunikatów do kolejkach obsługiwanych na maszynie mogą pojawić się za pomocą transportu dowolnego innego niż HTTP.  
  
6.  Po wybraniu usługi MSMQ do pracy w trybie zaostrzonym komputer wymaga ponownego rozruchu na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7.  Uruchom usługę.  
  
8.  Uruchom klienta. Upewnij się, że zmienisz adres punktu końcowego, aby wskazywał nazwę komputera lub adres IP zamiast nazwy localhost. Klient wysyła komunikat i kończy pracę.  
  
## <a name="requirements"></a>Wymagania  
 Aby uruchomić ten przykład, usługi IIS musi być zainstalowany zarówno usługi, jak i na komputerach klienckich, oprócz usługi MSMQ.  
  
## <a name="demonstrates"></a>Demonstracje  
 W przykładzie pokazano WCF wysyłanie wiadomości przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP w kolejce. Jest to tak zwane SRMP komunikatów. Gdy wiadomość w kolejce są wysyłane, usługi MSMQ na wysyłanie przeniesień maszyny komunikaty odbierający Menedżer kolejki przy użyciu transportu TCP lub HTTP. Wybierając SRMP, użytkownik wskazuje wybór HTTP jako transportu do kolejki transferu. Zabezpieczanie SRMP umożliwia korzystanie z protokołu HTTPS.  
  
## <a name="example"></a>Przykład  
 Przykładowy kod jest oparty na przykład transakcyjne. Jak wysyłać komunikat do kolejki i odebrania komunikatu z kolejki, używając SRMP jest taka sama jak wysyłanie i odbieranie wiadomości przy użyciu natywnego protokołu.  
  
 Konfiguracja klienta jest zmieniany na wskazują wybór protokół transferu kolejki. Protokół transferu kolejki może być jednym z natywnych, SRMP lub SrmpSecure. Domyślnie protokół transferu jest Native. Klient i usługa określ w konfiguracji, aby użyć SRMP w tym przykładzie.  
  
 Istnieją ograniczenia dotyczące SRMP w odniesieniu do zabezpieczeń transportu. Zabezpieczenia transportu usługi MSMQ domyślne wymaga usługi Active Directory, która wymaga, że Menedżer kolejki wysyłania i odbierania menedżera kolejek znajdują się w tej samej domenie Windows. To nie jest możliwe podczas wysyłania komunikatów za pośrednictwem protokołu HTTP granic. W efekcie domyślnych zabezpieczeń transportu nie działa. Zabezpieczenia transportu musi być równa certyfikatu, jeśli pożądane jest zabezpieczeń transportu. Zabezpieczenia komunikatów również może służyć do zabezpieczenia wiadomości. W tym przykładzie zabezpieczeń transportu i komunikatów jest wyłączona do zilustrowania SRMP komunikatów.  
  
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
  
 Działa aplikacja przykładowa daje następujące wyniki.  
  
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
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
