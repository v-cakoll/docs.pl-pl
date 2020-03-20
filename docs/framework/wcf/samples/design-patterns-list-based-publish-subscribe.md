---
title: 'Wzorce projektowe: publikowanie/subskrybowanie oparte na liście'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 7342b3702338d5cd1fcc27d80e4e70cee019cc22
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144763"
---
# <a name="design-patterns-list-based-publish-subscribe"></a>Wzorce projektowe: publikowanie/subskrybowanie oparte na liście
W tym przykładzie przedstawiono wzorzec publikowania i subskrybowania oparty na liście zaimplementowany jako program Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Wzorzec projektu publikowania i subskrybowania oparty na liście jest opisany w publikacji Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)). Wzorzec publikowania i subskrybowania przekazuje informacje do kolekcji adresatów, którzy zasubskrybowali temat informacyjny. Lista na podstawie publikowania subskrypcji utrzymuje listę subskrybentów. Gdy istnieją informacje do udostępnienia, kopia jest wysyłana do każdego subskrybenta na liście. W tym przykładzie pokazano dynamiczny wzorzec publikowania i subskrybowania oparty na liście, w którym klienci mogą subskrybować lub anulować subskrypcję tak często, jak jest to wymagane.  
  
 Przykład publikowania i subskrybowania oparty na liście składa się z klienta, usługi i programu źródła danych. Może być więcej niż jeden klient i uruchomiony więcej niż jeden program źródła danych. Klienci subskrybują usługę, otrzymują powiadomienia i ub.r. Programy źródła danych wysyłają informacje do usługi, które mają być współużytkowane wszystkim bieżącym subskrybentom.  
  
 W tym przykładzie klient i źródło danych są programami konsoli (pliki exe), a usługa jest biblioteką (dll) hostowana w internetowych usługach informacyjnych (IIS). Aktywność klienta i źródła danych są widoczne na pulpicie.  
  
 Usługa korzysta z komunikacji dupleksowej. Umowa `ISampleContract` serwisowa jest powiązana `ISampleClientCallback` z umową wywołania zwrotnego. Usługa implementuje subskrybować i anulować subskrypcję operacji usługi, których klienci używają do dołączenia lub opuszczenia listy subskrybentów. Usługa implementuje również `PublishPriceChange` operację usługi, którą program źródła danych wywołuje w celu dostarczenia usługi z nowymi informacjami. Program kliencki `PriceChange` implementuje operację usługi, którą usługa wywołuje, aby powiadomić wszystkich abonentów o zmianie ceny.  
  
```csharp  
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
  
 Usługa używa zdarzenia .NET Framework jako mechanizmu informowania wszystkich subskrybentów o nowych informacjach. Gdy klient dołącza do usługi, wywołując Subscribe, zapewnia program obsługi zdarzeń. Gdy klient opuszcza, ubskrybuje jego obsługi zdarzeń ze zdarzenia. Gdy źródło danych wywołuje usługę, aby zgłosić zmianę ceny, usługa podnosi zdarzenie. To wywołuje każde wystąpienie usługi, po jednym dla każdego klienta, który subskrybował i powoduje, że ich programy obsługi zdarzeń do wykonania. Każdy program obsługi zdarzeń przekazuje informacje do swojego klienta za pośrednictwem funkcji wywołania zwrotnego.  
  
```csharp
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
  
 Po uruchomieniu próbki uruchom kilku klientów. Klienci subskrybują usługę. Następnie uruchom program źródła danych, który wysyła informacje do usługi. Usługa przekazuje informacje do wszystkich subskrybentów. Możesz zobaczyć działanie na każdej konsoli klienta potwierdzające, że informacje zostały odebrane. Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.  
  
### <a name="to-set-up-and-build-the-sample"></a>Aby skonfigurować i utworzyć próbkę  
  
1. Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Aby uruchomić próbkę na tym samym komputerze  
  
1. Sprawdź, czy możesz uzyskać dostęp do usługi za `http://localhost/servicemodelsamples/service.svc`pomocą przeglądarki, wprowadzając następujący adres: . W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.  
  
2. Uruchom plik Client.exe z\\\client\bin , spod folderu specyficznego dla języka. Aktywność klienta jest wyświetlana w oknie konsoli klienta. Uruchom kilku klientów.  
  
3. Uruchom plik Datasource.exe z\\\datasource\bin , spod folderu specyficznego dla języka. Aktywność źródła danych jest wyświetlana w oknie konsoli. Gdy źródło danych wysyła informacje do usługi, powinny być przekazywane do każdego klienta.  
  
4. Jeśli klient, źródło danych i programy usługowe nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów z próbkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-machines"></a>Aby uruchomić próbkę na różnych komputerach  
  
1. Skonfiguruj urządzenie serwisowe:  
  
    1. Na komputerze serwisowym utwórz katalog wirtualny o nazwie ServiceModelSamples. Plik wsadowy Setupvroot.bat z [procedury jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu dysku i katalogu wirtualnego.  
  
    2. Skopiuj pliki programu serwisowego z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze serwisowym. Pamiętaj, aby dołączyć pliki do katalogu \bin.  
  
    3. Sprawdź, czy można uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.  
  
2. Skonfiguruj maszyny klienckie:  
  
    1. Skopiuj pliki programu klienckiego z folderu \client\bin\ w folderze specyficznym dla języka na maszyny klienckie.  
  
    2. W każdym pliku konfiguracji klienta zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi. Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.  
  
3. Konfigurowanie komputera źródła danych:  
  
    1. Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze specyficznym dla języka do komputera źródła danych.  
  
    2. W pliku konfiguracji źródła danych zmień wartość adresu definicji punktu końcowego, aby dopasować go do nowego adresu usługi. Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.  
  
4. Na komputerach klienckich uruchom program Client.exe z wiersza polecenia.  
  
5. Na komputerze ze źródłem danych uruchom program Datasource.exe z wiersza polecenia.  
  
> [!IMPORTANT]
> Próbki mogą być już zainstalowane na komputerze. Przed kontynuowaniem sprawdź następujący (domyślny) katalog.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady. Ten przykład znajduje się w następującym katalogu.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
