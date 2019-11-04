---
title: SRMP
ms.date: 03/30/2017
ms.assetid: cf37078c-dcb4-45e0-acaf-2f196521b226
ms.openlocfilehash: 51b0e0513ba20bf7aeae461dee6ac864f1d55897
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417096"
---
# <a name="srmp"></a>SRMP
Ten przykład pokazuje, jak przeprowadzić komunikację z kolejką w kolejce przy użyciu usługi kolejkowania komunikatów (MSMQ) za pośrednictwem protokołu HTTP.  
  
 W kolejce komunikacja klient komunikuje się z usługą przy użyciu kolejki. Dokładniej, klient wysyła komunikaty do kolejki. Usługa odbiera komunikaty z kolejki. W związku z tym usługa i klient nie muszą być uruchomione w tym samym czasie w celu komunikowania się przy użyciu kolejki.  
  
 Usługa MSMQ umożliwia wysyłanie komunikatów do kolejki przy użyciu protokołu HTTP (łącznie z użyciem protokołu HTTPS). W tym przykładzie pokazano, jak używać funkcji komunikacji z kolejką Windows Communication Foundation (WCF) oraz jak wysyłać komunikaty za pośrednictwem protokołu HTTP. Usługa MSMQ korzysta z protokołu o nazwie SRMP, czyli protokołu opartego na protokole SOAP do komunikacji za pośrednictwem protokołu HTTP.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
4. Przed uruchomieniem przykładu w obszarze **Dodawanie/usuwanie składników systemu Windows**upewnij się, że usługa MSMQ jest zainstalowana z obsługą protokołu HTTP. Zainstalowanie obsługi protokołu HTTP powoduje automatyczne zainstalowanie Internet Information Services (IIS) i dodanie obsługi protokołu w usługach IIS dla usługi MSMQ.  
  
5. Jeśli chcesz mieć pewność, że protokół HTTP jest używany do komunikacji, możesz włączyć usługę MSMQ do działania w trybie zaostrzonym. Pozwala to zagwarantować, że żadne komunikaty do żadnej kolejki hostowanej na komputerze nie mogą zostać dostarczone przy użyciu żadnego transportu innego niż HTTP.  
  
6. Po wybraniu usługi MSMQ do uruchomienia w trybie zaostrzonym maszyna wymaga ponownego uruchomienia w [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
7. Uruchom usługę.  
  
8. Uruchom klienta programu. Upewnij się, że adres punktu końcowego został zmieniony tak, aby wskazywał nazwę lub adres IP maszyny zamiast hosta lokalnego. Klient wysyła komunikat i kończy pracę.  
  
## <a name="requirements"></a>Wymagania  
 Aby można było uruchomić ten przykład, usługi IIS muszą być zainstalowane na komputerach klienckich i klientach oprócz usługi MSMQ.  
  
## <a name="demonstrates"></a>Demonstracje  
 Przykład ilustruje wysyłanie komunikatów w kolejce WCF przy użyciu usługi MSMQ za pośrednictwem protokołu HTTP. Jest to również nazywane wiadomościami SRMP. Po wysłaniu komunikatu w kolejce usługa MSMQ na komputerze wysyłającym przesyła komunikaty do Menedżera kolejki odbioru przez TCP lub HTTP. Po wybraniu opcji SRMP użytkownik wskazuje wybór protokołu HTTP jako transportu do przeniesienia kolejki. Funkcja SRMP Secure umożliwia korzystanie z protokołu HTTPS.  
  
## <a name="example"></a>Przykład  
 Przykładowy kod jest oparty na przykładach transakcyjnych. Jak wysłać komunikat do kolejki i odebrać komunikat z kolejki przy użyciu protokołu SRMP jest taka sama jak wysyłanie i odbieranie komunikatów przy użyciu natywnych protokołów.  
  
 Konfiguracja klienta zostanie zmieniona, aby wskazać wybór protokołu transferu kolejki. Protokół transferu kolejki może być jednym z natywnych, SRMP lub SrmpSecure. Domyślnie protokół transferu jest natywny. Klient i usługa Określ w konfiguracji, aby użyć SRMP w tym przykładzie.  
  
 W odniesieniu do zabezpieczeń transportu istnieją ograniczenia dotyczące protokołu SRMP. Domyślne zabezpieczenia transportu usługi MSMQ wymagają Active Directory, które wymagają, aby Menedżer kolejki wysyłania i Menedżer kolejki odbiorczej znajdowały się w tej samej domenie systemu Windows. Nie jest to możliwe w przypadku wysyłania komunikatów za pośrednictwem granicy protokołu HTTP. W związku z tym domyślne zabezpieczenia transportu nie działają. Zabezpieczenia transportu muszą być ustawione na wartość certyfikat, jeśli są wymagane zabezpieczenia transportu. Zabezpieczenia komunikatów mogą również służyć do zabezpieczania wiadomości. W tym przykładzie zabezpieczenia transportu i komunikatów są wyłączone w celu zilustrowania wiadomości SRMP.  
  
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
  
 Uruchomienie przykładu daje następujące dane wyjściowe.  
  
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
> Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)]. Ten przykład znajduje się w następującym katalogu.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\SRMP`  
