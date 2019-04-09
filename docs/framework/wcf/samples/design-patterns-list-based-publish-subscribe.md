---
title: 'Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 2d8041bf3efefa085e94636624e92abb573c1820
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196921"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście
W tym przykładzie pokazano wzorzec listy publikowanie/subskrybowanie oparte na zaimplementowane jako program Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Wzorzec projektowy listy publikowanie/subskrybowanie oparte na opisanej w publikacji Microsoft Patterns i praktyk, [wzorce integracji](https://go.microsoft.com/fwlink/?LinkId=95894). Wzorzec publikowania/subskrybowania przekazuje informacje do kolekcji adresatów, do których masz subskrypcję tematu informacji. Oparte na liście publikowania/subskrybowania utrzymuje listę subskrybentów. W przypadku informacji, aby udostępnić kopię są wysyłane do każdego subskrybenta na liście. W tym przykładzie przedstawiono dynamiczny oparte na liście publikowania/subskrybowania wzorzec, gdzie klienci mogą subskrybowanie lub anulować subskrypcję tak często, zgodnie z potrzebami.  
  
 Listy publikowanie/subskrybowanie oparte na przykład składa się z klientem, usługi i program źródła danych. Może to być więcej niż jednego klienta i uruchomiony więcej niż jeden program źródła danych. Klienci subskrybowania usługi, otrzymywać powiadomienia i anulowanie subskrypcji. Programy źródłowe dane wysłać informacje do usługi, które mają być współużytkowane przez wszystkich bieżących subskrybentów.  
  
 W tym źródle próbki, klienta i dane są programy konsoli (pliki .exe), a Usługa biblioteki (.dll) hostowanych w Internet Information Services (IIS). Działanie źródłowego klienta i dane są wyświetlane na pulpicie.  
  
 Usługa używa komunikację dupleksową. `ISampleContract` Kontraktu usługi jest łączyć z `ISampleClientCallback` kontrakt wywołania zwrotnego. Usługa implementuje operacje usługi subskrypcji i Anuluj subskrypcję, na których klienci używają chcesz dołączyć lub opuścić listy subskrybentów. Implementuje również usługę `PublishPriceChange` operacji usługi, która wywołuje program źródła danych, do świadczenia usług o nowe informacje. Implementuje program kliencki `PriceChange` operacji usługi, która wywołuje usługę w celu powiadomienia wszyscy subskrybenci zmiany ceny.  
  
```  
// Create a service contract and define the service operations.  
// NOTE: The service operations must be declared explicitly.  
[ServiceContract(SessionMode=SessionMode.Required,  
      CallbackContract=typeof(ISampleClientContract))]  
public interface ISampleContract  
{  
    [OperationContract(IsOneWay = false, IsInitiating=true)]  
    void Subscribe();  
    [OperationContract(IsOneWay = false, IsTerminating=true)]  
    void Unsubscribe();  
    [OperationContract(IsOneWay = true)]  
    void PublishPriceChange(string item, double price,   
                                     double change);  
}  
  
public interface ISampleClientContract  
{  
    [OperationContract(IsOneWay = true)]  
    void PriceChange(string item, double price, double change);  
}  
```  
  
 Usługa używa zdarzenia .NET Framework jako mechanizm poinformowanie wszyscy subskrybenci o nowe informacje. Gdy klient dołącza usługi przez wywołującego Subskrybuj, zawiera program obsługi zdarzeń. Gdy klient opuszcza, anulowań subskrypcji swojego programu obsługi zdarzeń ze zdarzenia. Gdy źródło danych wywołuje usługę do zgłaszania zmian cen, usługa wywołuje zdarzenie. Każde wystąpienie usługi, jeden dla każdego klienta, który przyłącza i powoduje, że ich procedury obsługi zdarzeń wykonać to wywołanie. Każdy program obsługi zdarzeń przekazuje informacje do klienta za pośrednictwem jego funkcję wywołania zwrotnego.  
  
```  
public class PriceChangeEventArgs : EventArgs  
    {  
        public string Item;  
        public double Price;  
        public double Change;  
    }  
  
    // The Service implementation implements your service contract.  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    public class SampleService : ISampleContract  
    {  
        public static event PriceChangeEventHandler PriceChangeEvent;  
        public delegate void PriceChangeEventHandler(object sender, PriceChangeEventArgs e);  
  
        ISampleClientContract callback = null;  
  
        PriceChangeEventHandler priceChangeHandler = null;  
  
        //Clients call this service operation to subscribe.  
        //A price change event handler is registered for this client instance.  
  
        public void Subscribe()  
        {  
            callback = OperationContext.Current.GetCallbackChannel<ISampleClientContract>();  
            priceChangeHandler = new PriceChangeEventHandler(PriceChangeHandler);  
            PriceChangeEvent += priceChangeHandler;  
        }  
  
        //Clients call this service operation to unsubscribe.  
        //The previous price change event handler is unregistered.  
  
        public void Unsubscribe()  
        {  
            PriceChangeEvent -= priceChangeHandler;  
        }  
  
        //Information source clients call this service operation to report a price change.  
        //A price change event is raised. The price change event handlers for each subscriber will execute.  
  
        public void PublishPriceChange(string item, double price, double change)  
        {  
            PriceChangeEventArgs e = new PriceChangeEventArgs();  
            e.Item = item;  
            e.Price = price;  
            e.Change = change;  
            PriceChangeEvent(this, e);  
        }  
  
        //This event handler runs when a PriceChange event is raised.  
        //The client's PriceChange service operation is invoked to provide notification about the price change.  
  
        public void PriceChangeHandler(object sender, PriceChangeEventArgs e)  
        {  
            callback.PriceChange(e.Item, e.Price, e.Change);  
        }  
  
    }  
```  
  
 Po uruchomieniu przykładu, należy uruchomić kilka klientów. Klienci subskrybowania usługi. Następnie uruchom program źródła danych, który wysyła informacje do usługi. Usługa przekazuje informacje do wszystkich subskrybentów. Mogą zobaczyć aktywność na każdy klient konsoli potwierdzenie Odebrano informacje. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Test, czy można uzyskać dostęp do usługi, za pomocą przeglądarki, wpisując następujący adres: `http://localhost/servicemodelsamples/service.svc`. Strona potwierdzenia powinna być wyświetlana w odpowiedzi.  
  
2.  Uruchom Client.exe z \client\bin\\, jest dostępna z folderu specyficzny dla języka. Aktywność klienta jest wyświetlany w oknie konsoli klienta. Uruchom kilka klientów.  
  
3.  Uruchom Datasource.exe z \datasource\bin\\, jest dostępna z folderu specyficzny dla języka. W oknie konsoli wyświetlane jest działanie źródła danych. Gdy źródło danych wysyła informacje do usługi, powinien zostać przekazany do każdego klienta.  
  
4.  W przypadku klienta, źródła danych i usługi, programy nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Do uruchomienia przykładu na komputerach  
  
1.  Skonfiguruj komputer usługi:  
  
    1.  Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Zadanie wsadowe pliku Setupvroot.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalogu wirtualnego.  
  
    2.  Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ServiceModelSamples katalogu wirtualnego na maszynie usługi. Pamiętaj uwzględnić pliki w katalogu \bin.  
  
    3.  Test, aby uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
2.  Konfigurowanie komputerów klienckich:  
  
    1.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerach klienckich.  
  
    2.  W każdym pliku konfiguracji klienta należy zmienić wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
3.  Skonfiguruj maszyny źródła danych:  
  
    1.  Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze specyficzny dla języka na maszynie źródłowej danych.  
  
    2.  W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.  
  
4.  Na komputerach klienckich należy uruchomić Client.exe z poziomu wiersza polecenia.  
  
5.  Na maszynie źródłowej danych uruchom Datasource.exe z poziomu wiersza polecenia.  
  
> [!IMPORTANT]
>  Przykłady może już być zainstalowany na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
