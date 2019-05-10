---
title: 'Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście'
ms.date: 03/30/2017
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
ms.openlocfilehash: 1b99908c1b83bb0d75e295b7a12e8c5933fe86a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650126"
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="e90c2-102">Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście</span><span class="sxs-lookup"><span data-stu-id="e90c2-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="e90c2-103">W tym przykładzie pokazano wzorzec listy publikowanie/subskrybowanie oparte na zaimplementowane jako program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e90c2-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e90c2-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="e90c2-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e90c2-105">Wzorzec projektowy listy publikowanie/subskrybowanie oparte na opisanej w publikacji Microsoft Patterns i praktyk, [wzorce integracji](https://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="e90c2-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="e90c2-106">Wzorzec publikowania/subskrybowania przekazuje informacje do kolekcji adresatów, do których masz subskrypcję tematu informacji.</span><span class="sxs-lookup"><span data-stu-id="e90c2-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="e90c2-107">Oparte na liście publikowania/subskrybowania utrzymuje listę subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="e90c2-108">W przypadku informacji, aby udostępnić kopię są wysyłane do każdego subskrybenta na liście.</span><span class="sxs-lookup"><span data-stu-id="e90c2-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="e90c2-109">W tym przykładzie przedstawiono dynamiczny oparte na liście publikowania/subskrybowania wzorzec, gdzie klienci mogą subskrybowanie lub anulować subskrypcję tak często, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="e90c2-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="e90c2-110">Listy publikowanie/subskrybowanie oparte na przykład składa się z klientem, usługi i program źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e90c2-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="e90c2-111">Może to być więcej niż jednego klienta i uruchomiony więcej niż jeden program źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e90c2-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="e90c2-112">Klienci subskrybowania usługi, otrzymywać powiadomienia i anulowanie subskrypcji.</span><span class="sxs-lookup"><span data-stu-id="e90c2-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="e90c2-113">Programy źródłowe dane wysłać informacje do usługi, które mają być współużytkowane przez wszystkich bieżących subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="e90c2-114">W tym źródle próbki, klienta i dane są programy konsoli (pliki .exe), a Usługa biblioteki (.dll) hostowanych w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="e90c2-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="e90c2-115">Działanie źródłowego klienta i dane są wyświetlane na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="e90c2-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="e90c2-116">Usługa używa komunikację dupleksową.</span><span class="sxs-lookup"><span data-stu-id="e90c2-116">The service uses duplex communication.</span></span> <span data-ttu-id="e90c2-117">`ISampleContract` Kontraktu usługi jest łączyć z `ISampleClientCallback` kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e90c2-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="e90c2-118">Usługa implementuje operacje usługi subskrypcji i Anuluj subskrypcję, na których klienci używają chcesz dołączyć lub opuścić listy subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="e90c2-119">Implementuje również usługę `PublishPriceChange` operacji usługi, która wywołuje program źródła danych, do świadczenia usług o nowe informacje.</span><span class="sxs-lookup"><span data-stu-id="e90c2-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="e90c2-120">Implementuje program kliencki `PriceChange` operacji usługi, która wywołuje usługę w celu powiadomienia wszyscy subskrybenci zmiany ceny.</span><span class="sxs-lookup"><span data-stu-id="e90c2-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="e90c2-121">Usługa używa zdarzenia .NET Framework jako mechanizm poinformowanie wszyscy subskrybenci o nowe informacje.</span><span class="sxs-lookup"><span data-stu-id="e90c2-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="e90c2-122">Gdy klient dołącza usługi przez wywołującego Subskrybuj, zawiera program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e90c2-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="e90c2-123">Gdy klient opuszcza, anulowań subskrypcji swojego programu obsługi zdarzeń ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e90c2-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="e90c2-124">Gdy źródło danych wywołuje usługę do zgłaszania zmian cen, usługa wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="e90c2-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="e90c2-125">Każde wystąpienie usługi, jeden dla każdego klienta, który przyłącza i powoduje, że ich procedury obsługi zdarzeń wykonać to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="e90c2-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="e90c2-126">Każdy program obsługi zdarzeń przekazuje informacje do klienta za pośrednictwem jego funkcję wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="e90c2-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="e90c2-127">Po uruchomieniu przykładu, należy uruchomić kilka klientów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="e90c2-128">Klienci subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-128">The clients subscribe to the service.</span></span> <span data-ttu-id="e90c2-129">Następnie uruchom program źródła danych, który wysyła informacje do usługi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="e90c2-130">Usługa przekazuje informacje do wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="e90c2-131">Mogą zobaczyć aktywność na każdy klient konsoli potwierdzenie Odebrano informacje.</span><span class="sxs-lookup"><span data-stu-id="e90c2-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="e90c2-132">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="e90c2-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="e90c2-133">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="e90c2-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="e90c2-134">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e90c2-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e90c2-135">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e90c2-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="e90c2-136">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="e90c2-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="e90c2-137">Test, czy można uzyskać dostęp do usługi, za pomocą przeglądarki, wpisując następujący adres: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="e90c2-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="e90c2-138">Strona potwierdzenia powinna być wyświetlana w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="e90c2-139">Uruchom Client.exe z \client\bin\\, jest dostępna z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="e90c2-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="e90c2-140">Aktywność klienta jest wyświetlany w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="e90c2-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="e90c2-141">Uruchom kilka klientów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="e90c2-142">Uruchom Datasource.exe z \datasource\bin\\, jest dostępna z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="e90c2-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="e90c2-143">W oknie konsoli wyświetlane jest działanie źródła danych.</span><span class="sxs-lookup"><span data-stu-id="e90c2-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="e90c2-144">Gdy źródło danych wysyła informacje do usługi, powinien zostać przekazany do każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="e90c2-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="e90c2-145">W przypadku klienta, źródła danych i usługi, programy nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e90c2-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="e90c2-146">Do uruchomienia przykładu na komputerach</span><span class="sxs-lookup"><span data-stu-id="e90c2-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="e90c2-147">Skonfiguruj komputer usługi:</span><span class="sxs-lookup"><span data-stu-id="e90c2-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="e90c2-148">Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="e90c2-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="e90c2-149">Zadanie wsadowe pliku Setupvroot.bat z [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="e90c2-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="e90c2-150">Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples ServiceModelSamples katalogu wirtualnego na maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="e90c2-151">Pamiętaj uwzględnić pliki w katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="e90c2-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="e90c2-152">Test, aby uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="e90c2-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="e90c2-153">Konfigurowanie komputerów klienckich:</span><span class="sxs-lookup"><span data-stu-id="e90c2-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="e90c2-154">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze specyficzny dla języka na komputerach klienckich.</span><span class="sxs-lookup"><span data-stu-id="e90c2-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="e90c2-155">W każdym pliku konfiguracji klienta należy zmienić wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="e90c2-156">Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="e90c2-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="e90c2-157">Skonfiguruj maszyny źródła danych:</span><span class="sxs-lookup"><span data-stu-id="e90c2-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="e90c2-158">Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze specyficzny dla języka na maszynie źródłowej danych.</span><span class="sxs-lookup"><span data-stu-id="e90c2-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="e90c2-159">W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="e90c2-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="e90c2-160">Zastąp wszystkie odwołania do "localhost" w pełni kwalifikowaną nazwę domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="e90c2-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="e90c2-161">Na komputerach klienckich należy uruchomić Client.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e90c2-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="e90c2-162">Na maszynie źródłowej danych uruchom Datasource.exe z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="e90c2-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e90c2-163">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="e90c2-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e90c2-164">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="e90c2-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e90c2-165">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="e90c2-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e90c2-166">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="e90c2-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
