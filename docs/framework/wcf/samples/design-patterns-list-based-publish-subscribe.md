---
title: 'Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: cf6fe2da3101918e25aa9548fd18973088f348a7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961743"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście
Ten przykład ilustruje wzorzec publikowania/subskrybowania opartego na liście wdrożony jako program Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Wzorzec projektowy publikowania/subskrybowania opartego na liście jest opisany w artykule wzorce firmy Microsoft dotyczące publikacji & praktyk, [wzorców integracji](https://go.microsoft.com/fwlink/?LinkId=95894). Wzorzec publikowania/subskrybowania przekazuje informacje do kolekcji adresatów, którzy subskrybują temat informacji. Publikowanie/subskrybowanie oparte na liście zachowuje listę subskrybentów. Gdy są informacje do udostępnienia, kopia jest wysyłana do każdego subskrybenta na liście. Ten przykład ilustruje dynamiczny wzorzec publikowania/subskrybowania opartego na listach, w którym klienci mogą subskrybować lub anulować subskrypcję, tak często, jak jest to wymagane.  
  
 Przykład publikowania/subskrybowania opartego na liście składa się z klienta, usługi i programu źródła danych. Może istnieć więcej niż jeden klient i więcej niż jeden uruchomiony program źródła danych. Klienci subskrybują usługę, odbierają powiadomienia i anulują subskrypcję. Programy ze źródeł danych wysyłają do usługi informacje, które mają być współużytkowane z bieżącymi subskrybentami.  
  
 W tym przykładzie klient i źródło danych to programy konsolowe (pliki. exe), a usługa to biblioteka (. dll) hostowana w Internet Information Services (IIS). Na pulpicie są widoczne działania klienta i źródła danych.  
  
 Usługa używa komunikacji dwukierunkowej. Kontrakt usługi jest sparowany `ISampleClientCallback` z kontraktem wywołania zwrotnego. `ISampleContract` Usługa implementuje operacje subskrybowania i anulowania subskrypcji, których klienci używają do przyłączania lub opuszczania listy subskrybentów. Usługa implementuje `PublishPriceChange` również operację usługi, która jest wywoływana przez program źródła danych w celu zapewnienia usłudze nowych informacji. Program kliencki implementuje `PriceChange` operację usługi, która jest wywoływana przez usługę w celu powiadomienia wszystkich subskrybentów o zmianie cen.  
  
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
  
 Usługa używa zdarzenia .NET Framework jako mechanizmu do informowania wszystkich subskrybentów o nowych informacjach. Gdy klient przyłącza się do usługi przez wywołanie funkcji Subskrybuj, zapewnia obsługę zdarzeń. Po opuszczeniu klient anulował subskrypcję jego programu obsługi zdarzeń ze zdarzenia. Gdy źródło danych wywoła usługę w celu zgłoszenia zmiany ceny, usługa zgłasza zdarzenie. To wywołuje każde wystąpienie usługi, jeden dla każdego klienta, który ma subskrypcję, i powoduje wykonanie przez nich programów obsługi zdarzeń. Każdy program obsługi zdarzeń przekazuje informacje do klienta za pomocą funkcji wywołania zwrotnego.  
  
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
  
 Po uruchomieniu przykładu należy uruchomić kilku klientów. Klienci subskrybują usługę. Następnie uruchom program źródła danych, który wysyła informacje do usługi. Usługa przekazuje informacje do wszystkich subskrybentów. Na każdej konsoli klienta można sprawdzić, czy informacje zostały odebrane. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i skompilować przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić przykład na tym samym komputerze  
  
1. Sprawdź, czy możesz uzyskać dostęp do usługi przy użyciu przeglądarki, wprowadzając następujący adres: `http://localhost/servicemodelsamples/service.svc`. W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.  
  
2. Uruchom program Client. exe z\\\client\bin, z poziomu folderu specyficznego dla języka. Aktywność klienta jest wyświetlana w oknie konsoli klienta. Uruchom kilku klientów.  
  
3. Uruchom polecenie DataSource. exe z\\\datasource\bin, z poziomu folderu specyficznego dla języka. Działanie źródła danych jest wyświetlane w oknie konsoli. Gdy źródło danych wyśle informacje do usługi, powinna zostać przeniesiona do każdego klienta.  
  
4. Jeśli klient, źródło danych i programy usług nie będą mogły się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić przykład na wielu maszynach  
  
1. Skonfiguruj maszynę usługi:  
  
    1. Na maszynie usługi Utwórz katalog wirtualny o nazwie ServiceModelSamples. Plik wsadowy Setupvroot. bat z [procedury konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można użyć do utworzenia katalogu dysku i katalogu wirtualnego.  
  
    2. Skopiuj pliki programu usługi z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na maszynie usługi. Pamiętaj o uwzględnieniu plików w katalogu \Bin.  
  
    3. Sprawdź, czy możesz uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
2. Skonfiguruj komputery klienckie:  
  
    1. Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputerów klienckich.  
  
    2. W każdym pliku konfiguracyjnym klienta Zmień wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi. Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.  
  
3. Skonfiguruj maszynę źródła danych:  
  
    1. Skopiuj pliki programu źródła danych z folderu \datasource\bin\, w obszarze folder specyficzny dla języka, do maszyny źródła danych.  
  
    2. W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi. Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.  
  
4. Na komputerach klienckich Uruchom program Client. exe z wiersza polecenia.  
  
5. Na maszynie źródła danych Uruchom plik DataSource. exe z wiersza polecenia.  
  
> [!IMPORTANT]
>  Przykłady mogą być już zainstalowane na komputerze. Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
