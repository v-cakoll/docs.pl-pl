---
title: "Wzorce projektowe: Oparte na liście publikowania / subskrypcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4257abc-12df-4736-a03b-0731becf0fd4
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b54982439f621ea504c91c264dde002751ec9185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="f63ed-102">Wzorce projektowe: Oparte na liście publikowania / subskrypcji</span><span class="sxs-lookup"><span data-stu-id="f63ed-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="f63ed-103">W tym przykładzie przedstawiono wzorzec oparty na liście publikowania / subskrypcji, zaimplementowane jako [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span><span class="sxs-lookup"><span data-stu-id="f63ed-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] program.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f63ed-104">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="f63ed-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f63ed-105">Wzorzec projektowy oparty na liście publikowania / subskrypcji jest opisane w publikacji Microsoft Patterns & rozwiązań [wzorce integracji](http://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="f63ed-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](http://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="f63ed-106">Wzorzec publikowania / subskrypcji przekazuje informacje do kolekcji adresatów, do których masz subskrypcję tematu informacji.</span><span class="sxs-lookup"><span data-stu-id="f63ed-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="f63ed-107">Na podstawie listy publikowania / subskrypcji przechowuje listę subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="f63ed-108">W przypadku informacji do udziału kopii są wysyłane do każdego subskrybenta na liście.</span><span class="sxs-lookup"><span data-stu-id="f63ed-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="f63ed-109">W tym przykładzie pokazano dynamicznym oparte na liście publikowania / subskrypcji wzorzec, których klientów można subskrypcji lub anulować subskrypcję tak często, zgodnie z wymaganiami.</span><span class="sxs-lookup"><span data-stu-id="f63ed-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="f63ed-110">Próbka oparte na liście publikowania / subskrypcji składa się z klientem, usługi i program źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f63ed-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="f63ed-111">Może istnieć więcej niż jednego klienta i więcej niż jeden program źródła danych, systemem.</span><span class="sxs-lookup"><span data-stu-id="f63ed-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="f63ed-112">Klienci subskrybowania usługi, otrzymywać powiadomienia i anulować subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="f63ed-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="f63ed-113">Programy źródłowe dane wysyłania informacji do usługi, które mają być współużytkowane przez wszystkich subskrybentów bieżącego.</span><span class="sxs-lookup"><span data-stu-id="f63ed-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="f63ed-114">W tym źródle próbki, klienta i dane są programy konsoli (pliki .exe), a Usługa biblioteki (.dll) hostowanych w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="f63ed-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="f63ed-115">Działanie źródłowego klienta i dane są widoczne na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="f63ed-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="f63ed-116">Usługa korzysta z komunikacji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="f63ed-116">The service uses duplex communication.</span></span> <span data-ttu-id="f63ed-117">`ISampleContract` Kontraktu usługi jest łączyć z `ISampleClientCallback` kontrakt wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f63ed-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="f63ed-118">Usługa implementuje Subskrybuj i Anuluj subskrypcję operacji usługi, których klienci używają do dołączenia lub opuszczenia listy subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="f63ed-119">Usługa implementuje również `PublishPriceChange` operacji usługi, która wywołuje program źródła danych do świadczenia usług przy użyciu nowych informacji.</span><span class="sxs-lookup"><span data-stu-id="f63ed-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="f63ed-120">Implementuje program kliencki `PriceChange` operacji usługi, która wywołuje usługę powiadomiono wszystkich subskrybentów zmiany ceny.</span><span class="sxs-lookup"><span data-stu-id="f63ed-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="f63ed-121">Usługa używa zdarzeń .NET Framework jako mechanizm do informowania o nowe informacje o wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="f63ed-122">Gdy klient dołącza usługi przez wywołanie Subskrybuj, udostępnia program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f63ed-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="f63ed-123">Pozostawia klienta, cofnięć subskrypcji jej procedura obsługi zdarzenia ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f63ed-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="f63ed-124">Gdy źródło danych wywołuje usługę, aby zgłosić zmiany ceny, usługa wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="f63ed-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="f63ed-125">Każde wystąpienie usługi, po jednej dla każdego klienta, który zostały zasubskrybowane i powoduje, że ich obsługi zdarzeń wykonać to wywołanie.</span><span class="sxs-lookup"><span data-stu-id="f63ed-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="f63ed-126">Każdy program obsługi zdarzeń przekazuje informacje do klienta za pośrednictwem funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f63ed-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
        //The previous price change event handler is deregistered.  
  
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
  
 <span data-ttu-id="f63ed-127">Po uruchomieniu próbki, należy uruchomić kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="f63ed-128">Klienci subskrybowania usługi.</span><span class="sxs-lookup"><span data-stu-id="f63ed-128">The clients subscribe to the service.</span></span> <span data-ttu-id="f63ed-129">Następnie uruchom program źródła danych, który wysyła informacje do usługi.</span><span class="sxs-lookup"><span data-stu-id="f63ed-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="f63ed-130">Usługa przekazuje informacje do wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="f63ed-131">Mogą zobaczyć aktywność na każdy klient konsoli potwierdzenie otrzymano informacje.</span><span class="sxs-lookup"><span data-stu-id="f63ed-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="f63ed-132">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="f63ed-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="f63ed-133">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="f63ed-133">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="f63ed-134">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f63ed-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="f63ed-135">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f63ed-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="f63ed-136">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="f63ed-136">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="f63ed-137">Test, czy można uzyskać dostępu do usługi przy użyciu przeglądarki wprowadź następujący adres: http://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="f63ed-137">Test that you can access the service using a browser by entering the following address: http://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="f63ed-138">Powinna być wyświetlana strona potwierdzenia w odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f63ed-138">A confirmation page should be displayed in response.</span></span>  
  
2.  <span data-ttu-id="f63ed-139">Uruchom Client.exe z \client\bin\\, z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="f63ed-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="f63ed-140">Aktywność klienta jest wyświetlany w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="f63ed-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="f63ed-141">Uruchamianie wielu klientów.</span><span class="sxs-lookup"><span data-stu-id="f63ed-141">Launch several clients.</span></span>  
  
3.  <span data-ttu-id="f63ed-142">Uruchom Datasource.exe z \datasource\bin\\, z folderu specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="f63ed-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="f63ed-143">Działania źródła danych jest wyświetlany w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="f63ed-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="f63ed-144">Gdy źródło danych wysyła informacje do usługi, powinny zostać przekazane do każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="f63ed-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4.  <span data-ttu-id="f63ed-145">Jeśli klient, źródła danych i programy usługi nie są mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="f63ed-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="f63ed-146">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="f63ed-146">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="f63ed-147">Skonfiguruj komputer usługi:</span><span class="sxs-lookup"><span data-stu-id="f63ed-147">Set up the service machine:</span></span>  
  
    1.  <span data-ttu-id="f63ed-148">Na komputerze usługi należy utworzyć katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="f63ed-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="f63ed-149">Setupvroot.bat z pliku wsadowego [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu na dysku i katalog wirtualny.</span><span class="sxs-lookup"><span data-stu-id="f63ed-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2.  <span data-ttu-id="f63ed-150">Skopiuj pliki programu usługi z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="f63ed-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="f63ed-151">Pamiętaj uwzględnić pliki w katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="f63ed-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3.  <span data-ttu-id="f63ed-152">Aby uzyskać dostęp do usługi z komputera klienta przy użyciu przeglądarki testu.</span><span class="sxs-lookup"><span data-stu-id="f63ed-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2.  <span data-ttu-id="f63ed-153">Konfigurowanie komputerów klienckich:</span><span class="sxs-lookup"><span data-stu-id="f63ed-153">Set up the client machines:</span></span>  
  
    1.  <span data-ttu-id="f63ed-154">Skopiuj pliki programu klienta z folderu \client\bin\ w folderze danego języka na komputerach klienckich.</span><span class="sxs-lookup"><span data-stu-id="f63ed-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2.  <span data-ttu-id="f63ed-155">W każdym pliku konfiguracji klienta Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="f63ed-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="f63ed-156">Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="f63ed-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3.  <span data-ttu-id="f63ed-157">Skonfiguruj maszynę źródła danych:</span><span class="sxs-lookup"><span data-stu-id="f63ed-157">Set up the data source machine:</span></span>  
  
    1.  <span data-ttu-id="f63ed-158">Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze danego języka maszyną źródła danych.</span><span class="sxs-lookup"><span data-stu-id="f63ed-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2.  <span data-ttu-id="f63ed-159">W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego do dopasowania nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="f63ed-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="f63ed-160">Zamień wszystkie odwołania do "localhost" pełni kwalifikowanej nazwy domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="f63ed-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4.  <span data-ttu-id="f63ed-161">Na komputerach klienckich należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f63ed-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="f63ed-162">Na komputerze źródłowym, danych uruchom Datasource.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f63ed-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f63ed-163">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="f63ed-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f63ed-164">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="f63ed-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f63ed-165">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="f63ed-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f63ed-166">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="f63ed-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
  
## <a name="see-also"></a><span data-ttu-id="f63ed-167">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f63ed-167">See Also</span></span>
