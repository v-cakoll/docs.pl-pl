---
title: 'Wzorce projektowe: Oparte na liście publikowania / subskrypcji'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: ee05be76607975bd771c0e6f83c242ad944251df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Wzorce projektowe: Oparte na liście publikowania / subskrypcji
W tym przykładzie przedstawiono wzorzec oparty na liście publikowania / subskrypcji, zaimplementowane jako programu Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Wzorzec projektowy oparty na liście publikowania / subskrypcji jest opisane w publikacji Microsoft Patterns & rozwiązań [wzorce integracji](http://go.microsoft.com/fwlink/?LinkId=95894). Wzorzec publikowania / subskrypcji przekazuje informacje do kolekcji adresatów, do których masz subskrypcję tematu informacji. Na podstawie listy publikowania / subskrypcji przechowuje listę subskrybentów. W przypadku informacji do udziału kopii są wysyłane do każdego subskrybenta na liście. W tym przykładzie pokazano dynamicznym oparte na liście publikowania / subskrypcji wzorzec, których klientów można subskrypcji lub anulować subskrypcję tak często, zgodnie z wymaganiami.  
  
 Próbka oparte na liście publikowania / subskrypcji składa się z klientem, usługi i program źródła danych. Może istnieć więcej niż jednego klienta i więcej niż jeden program źródła danych, systemem. Klienci subskrybowania usługi, otrzymywać powiadomienia i anulować subskrypcję. Programy źródłowe dane wysyłania informacji do usługi, które mają być współużytkowane przez wszystkich subskrybentów bieżącego.  
  
 W tym źródle próbki, klienta i dane są programy konsoli (pliki .exe), a Usługa biblioteki (.dll) hostowanych w Internet Information Services (IIS). Działanie źródłowego klienta i dane są widoczne na pulpicie.  
  
 Usługa korzysta z komunikacji dupleksowej. `ISampleContract` Kontraktu usługi jest łączyć z `ISampleClientCallback` kontrakt wywołania zwrotnego. Usługa implementuje Subskrybuj i Anuluj subskrypcję operacji usługi, których klienci używają do dołączenia lub opuszczenia listy subskrybentów. Usługa implementuje również `PublishPriceChange` operacji usługi, która wywołuje program źródła danych do świadczenia usług przy użyciu nowych informacji. Implementuje program kliencki `PriceChange` operacji usługi, która wywołuje usługę powiadomiono wszystkich subskrybentów zmiany ceny.  
  
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
  
 Usługa używa zdarzeń .NET Framework jako mechanizm do informowania o nowe informacje o wszystkich subskrybentów. Gdy klient dołącza usługi przez wywołanie Subskrybuj, udostępnia program obsługi zdarzeń. Pozostawia klienta, cofnięć subskrypcji jej procedura obsługi zdarzenia ze zdarzenia. Gdy źródło danych wywołuje usługę, aby zgłosić zmiany ceny, usługa wywołuje zdarzenie. Każde wystąpienie usługi, po jednej dla każdego klienta, który zostały zasubskrybowane i powoduje, że ich obsługi zdarzeń wykonać to wywołanie. Każdy program obsługi zdarzeń przekazuje informacje do klienta za pośrednictwem funkcji wywołania zwrotnego.  
  
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
  
 Po uruchomieniu próbki, należy uruchomić kilku klientów. Klienci subskrybowania usługi. Następnie uruchom program źródła danych, który wysyła informacje do usługi. Usługa przekazuje informacje do wszystkich subskrybentów. Mogą zobaczyć aktywność na każdy klient konsoli potwierdzenie otrzymano informacje. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i tworzyć przykładowy kod  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1.  Test, czy można uzyskać dostępu do usługi przy użyciu przeglądarki wprowadź następujący adres: http://localhost/servicemodelsamples/service.svc. Powinna być wyświetlana strona potwierdzenia w odpowiedzi.  
  
2.  Uruchom Client.exe z \client\bin\\, z folderu specyficzny dla języka. Aktywność klienta jest wyświetlany w oknie konsoli klienta. Uruchamianie wielu klientów.  
  
3.  Uruchom Datasource.exe z \datasource\bin\\, z folderu specyficzny dla języka. Działania źródła danych jest wyświetlany w oknie konsoli. Gdy źródło danych wysyła informacje do usługi, powinny zostać przekazane do każdego klienta.  
  
4.  Jeśli klient, źródła danych i programy usługi nie są mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na komputerach  
  
1.  Skonfiguruj komputer usługi:  
  
    1.  Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples. Setupvroot.bat z pliku wsadowego [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalog wirtualny.  
  
    2.  Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi. Pamiętaj uwzględnić pliki w katalogu \bin.  
  
    3.  Aby uzyskać dostęp do usługi z komputera klienta przy użyciu przeglądarki testu.  
  
2.  Konfigurowanie komputerów klienckich:  
  
    1.  Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerach klienckich.  
  
    2.  W każdym pliku konfiguracji klienta Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
3.  Skonfiguruj maszynę źródła danych:  
  
    1.  Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze danego języka maszyną źródła danych.  
  
    2.  W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą. Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.  
  
4.  Na komputerach klienckich należy uruchomić Client.exe z wiersza polecenia.  
  
5.  Na komputerze źródłowym, danych uruchom Datasource.exe z wiersza polecenia.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a>Zobacz też
