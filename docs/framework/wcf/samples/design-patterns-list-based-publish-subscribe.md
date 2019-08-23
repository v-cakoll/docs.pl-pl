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
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="2fc2e-102">Wzorce projektowania: Publikowanie/subskrybowanie oparte na liście</span><span class="sxs-lookup"><span data-stu-id="2fc2e-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="2fc2e-103">Ten przykład ilustruje wzorzec publikowania/subskrybowania opartego na liście wdrożony jako program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2fc2e-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="2fc2e-105">Wzorzec projektowy publikowania/subskrybowania opartego na liście jest opisany w artykule wzorce firmy Microsoft dotyczące publikacji & praktyk, [wzorców integracji](https://go.microsoft.com/fwlink/?LinkId=95894).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://go.microsoft.com/fwlink/?LinkId=95894).</span></span> <span data-ttu-id="2fc2e-106">Wzorzec publikowania/subskrybowania przekazuje informacje do kolekcji adresatów, którzy subskrybują temat informacji.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="2fc2e-107">Publikowanie/subskrybowanie oparte na liście zachowuje listę subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="2fc2e-108">Gdy są informacje do udostępnienia, kopia jest wysyłana do każdego subskrybenta na liście.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="2fc2e-109">Ten przykład ilustruje dynamiczny wzorzec publikowania/subskrybowania opartego na listach, w którym klienci mogą subskrybować lub anulować subskrypcję, tak często, jak jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="2fc2e-110">Przykład publikowania/subskrybowania opartego na liście składa się z klienta, usługi i programu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="2fc2e-111">Może istnieć więcej niż jeden klient i więcej niż jeden uruchomiony program źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="2fc2e-112">Klienci subskrybują usługę, odbierają powiadomienia i anulują subskrypcję.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="2fc2e-113">Programy ze źródeł danych wysyłają do usługi informacje, które mają być współużytkowane z bieżącymi subskrybentami.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="2fc2e-114">W tym przykładzie klient i źródło danych to programy konsolowe (pliki. exe), a usługa to biblioteka (. dll) hostowana w Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="2fc2e-115">Na pulpicie są widoczne działania klienta i źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="2fc2e-116">Usługa używa komunikacji dwukierunkowej.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-116">The service uses duplex communication.</span></span> <span data-ttu-id="2fc2e-117">Kontrakt usługi jest sparowany `ISampleClientCallback` z kontraktem wywołania zwrotnego. `ISampleContract`</span><span class="sxs-lookup"><span data-stu-id="2fc2e-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="2fc2e-118">Usługa implementuje operacje subskrybowania i anulowania subskrypcji, których klienci używają do przyłączania lub opuszczania listy subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="2fc2e-119">Usługa implementuje `PublishPriceChange` również operację usługi, która jest wywoływana przez program źródła danych w celu zapewnienia usłudze nowych informacji.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="2fc2e-120">Program kliencki implementuje `PriceChange` operację usługi, która jest wywoływana przez usługę w celu powiadomienia wszystkich subskrybentów o zmianie cen.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="2fc2e-121">Usługa używa zdarzenia .NET Framework jako mechanizmu do informowania wszystkich subskrybentów o nowych informacjach.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="2fc2e-122">Gdy klient przyłącza się do usługi przez wywołanie funkcji Subskrybuj, zapewnia obsługę zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="2fc2e-123">Po opuszczeniu klient anulował subskrypcję jego programu obsługi zdarzeń ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="2fc2e-124">Gdy źródło danych wywoła usługę w celu zgłoszenia zmiany ceny, usługa zgłasza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="2fc2e-125">To wywołuje każde wystąpienie usługi, jeden dla każdego klienta, który ma subskrypcję, i powoduje wykonanie przez nich programów obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="2fc2e-126">Każdy program obsługi zdarzeń przekazuje informacje do klienta za pomocą funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="2fc2e-127">Po uruchomieniu przykładu należy uruchomić kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="2fc2e-128">Klienci subskrybują usługę.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-128">The clients subscribe to the service.</span></span> <span data-ttu-id="2fc2e-129">Następnie uruchom program źródła danych, który wysyła informacje do usługi.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="2fc2e-130">Usługa przekazuje informacje do wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="2fc2e-131">Na każdej konsoli klienta można sprawdzić, czy informacje zostały odebrane.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="2fc2e-132">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta programu.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="2fc2e-133">Aby skonfigurować i skompilować przykład</span><span class="sxs-lookup"><span data-stu-id="2fc2e-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="2fc2e-134">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="2fc2e-135">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="2fc2e-136">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="2fc2e-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="2fc2e-137">Sprawdź, czy możesz uzyskać dostęp do usługi przy użyciu przeglądarki, wprowadzając następujący adres: `http://localhost/servicemodelsamples/service.svc`.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="2fc2e-138">W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="2fc2e-139">Uruchom program Client. exe z\\\client\bin, z poziomu folderu specyficznego dla języka.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="2fc2e-140">Aktywność klienta jest wyświetlana w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="2fc2e-141">Uruchom kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="2fc2e-142">Uruchom polecenie DataSource. exe z\\\datasource\bin, z poziomu folderu specyficznego dla języka.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="2fc2e-143">Działanie źródła danych jest wyświetlane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="2fc2e-144">Gdy źródło danych wyśle informacje do usługi, powinna zostać przeniesiona do każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="2fc2e-145">Jeśli klient, źródło danych i programy usług nie będą mogły się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="2fc2e-146">Aby uruchomić przykład na wielu maszynach</span><span class="sxs-lookup"><span data-stu-id="2fc2e-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="2fc2e-147">Skonfiguruj maszynę usługi:</span><span class="sxs-lookup"><span data-stu-id="2fc2e-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="2fc2e-148">Na maszynie usługi Utwórz katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="2fc2e-149">Plik wsadowy Setupvroot. bat z [procedury konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) można użyć do utworzenia katalogu dysku i katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="2fc2e-150">Skopiuj pliki programu usługi z%SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na maszynie usługi.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="2fc2e-151">Pamiętaj o uwzględnieniu plików w katalogu \Bin.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="2fc2e-152">Sprawdź, czy możesz uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="2fc2e-153">Skonfiguruj komputery klienckie:</span><span class="sxs-lookup"><span data-stu-id="2fc2e-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="2fc2e-154">Skopiuj pliki programu klienckiego z folderu \client\bin\, w obszarze folder specyficzny dla języka, do komputerów klienckich.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="2fc2e-155">W każdym pliku konfiguracyjnym klienta Zmień wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="2fc2e-156">Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="2fc2e-157">Skonfiguruj maszynę źródła danych:</span><span class="sxs-lookup"><span data-stu-id="2fc2e-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="2fc2e-158">Skopiuj pliki programu źródła danych z folderu \datasource\bin\, w obszarze folder specyficzny dla języka, do maszyny źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="2fc2e-159">W pliku konfiguracji źródła danych Zmień wartość adresu definicji punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="2fc2e-160">Zastąp wszystkie odwołania do "localhost" z w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="2fc2e-161">Na komputerach klienckich Uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="2fc2e-162">Na maszynie źródła danych Uruchom plik DataSource. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2fc2e-163">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2fc2e-164">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="2fc2e-164">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2fc2e-165">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) , aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2fc2e-166">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2fc2e-166">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
