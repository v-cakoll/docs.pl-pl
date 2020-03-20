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
# <a name="design-patterns-list-based-publish-subscribe"></a><span data-ttu-id="4be74-102">Wzorce projektowe: publikowanie/subskrybowanie oparte na liście</span><span class="sxs-lookup"><span data-stu-id="4be74-102">Design Patterns: List-Based Publish-Subscribe</span></span>
<span data-ttu-id="4be74-103">W tym przykładzie przedstawiono wzorzec publikowania i subskrybowania oparty na liście zaimplementowany jako program Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4be74-103">This sample illustrates the List-based Publish-Subscribe pattern implemented as a Windows Communication Foundation (WCF) program.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4be74-104">Procedura konfiguracji i instrukcje kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="4be74-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4be74-105">Wzorzec projektu publikowania i subskrybowania oparty na liście jest opisany w publikacji Microsoft Patterns & Practices, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="4be74-105">The List-based Publish-Subscribe design pattern is described in the Microsoft Patterns & Practices publication, [Integration Patterns](https://docs.microsoft.com/previous-versions/msp-n-p/ff647309(v=pandp.10)).</span></span> <span data-ttu-id="4be74-106">Wzorzec publikowania i subskrybowania przekazuje informacje do kolekcji adresatów, którzy zasubskrybowali temat informacyjny.</span><span class="sxs-lookup"><span data-stu-id="4be74-106">The Publish-Subscribe pattern passes information to a collection of recipients who have subscribed to an information topic.</span></span> <span data-ttu-id="4be74-107">Lista na podstawie publikowania subskrypcji utrzymuje listę subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="4be74-107">List-based publish-subscribe maintains a list of subscribers.</span></span> <span data-ttu-id="4be74-108">Gdy istnieją informacje do udostępnienia, kopia jest wysyłana do każdego subskrybenta na liście.</span><span class="sxs-lookup"><span data-stu-id="4be74-108">When there is information to share, a copy is sent to each subscriber on the list.</span></span> <span data-ttu-id="4be74-109">W tym przykładzie pokazano dynamiczny wzorzec publikowania i subskrybowania oparty na liście, w którym klienci mogą subskrybować lub anulować subskrypcję tak często, jak jest to wymagane.</span><span class="sxs-lookup"><span data-stu-id="4be74-109">This sample demonstrates a dynamic list-based publish-subscribe pattern, where clients can subscribe or unsubscribe as often as required.</span></span>  
  
 <span data-ttu-id="4be74-110">Przykład publikowania i subskrybowania oparty na liście składa się z klienta, usługi i programu źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4be74-110">The List-based Publish-Subscribe sample consists of a client, a service, and a data source program.</span></span> <span data-ttu-id="4be74-111">Może być więcej niż jeden klient i uruchomiony więcej niż jeden program źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4be74-111">There can be more than one client and more than one data source program running.</span></span> <span data-ttu-id="4be74-112">Klienci subskrybują usługę, otrzymują powiadomienia i ub.r.</span><span class="sxs-lookup"><span data-stu-id="4be74-112">Clients subscribe to the service, receive notifications, and unsubscribe.</span></span> <span data-ttu-id="4be74-113">Programy źródła danych wysyłają informacje do usługi, które mają być współużytkowane wszystkim bieżącym subskrybentom.</span><span class="sxs-lookup"><span data-stu-id="4be74-113">Data source programs send information to the service to be shared with all current subscribers.</span></span>  
  
 <span data-ttu-id="4be74-114">W tym przykładzie klient i źródło danych są programami konsoli (pliki exe), a usługa jest biblioteką (dll) hostowana w internetowych usługach informacyjnych (IIS).</span><span class="sxs-lookup"><span data-stu-id="4be74-114">In this sample, the client and data source are console programs (.exe files) and the service is a library (.dll) hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="4be74-115">Aktywność klienta i źródła danych są widoczne na pulpicie.</span><span class="sxs-lookup"><span data-stu-id="4be74-115">Client and data source activity are visible on the desktop.</span></span>  
  
 <span data-ttu-id="4be74-116">Usługa korzysta z komunikacji dupleksowej.</span><span class="sxs-lookup"><span data-stu-id="4be74-116">The service uses duplex communication.</span></span> <span data-ttu-id="4be74-117">Umowa `ISampleContract` serwisowa jest powiązana `ISampleClientCallback` z umową wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4be74-117">The `ISampleContract` service contract is paired up with an `ISampleClientCallback` callback contract.</span></span> <span data-ttu-id="4be74-118">Usługa implementuje subskrybować i anulować subskrypcję operacji usługi, których klienci używają do dołączenia lub opuszczenia listy subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="4be74-118">The service implements Subscribe and Unsubscribe service operations, which clients use to join or leave the list of subscribers.</span></span> <span data-ttu-id="4be74-119">Usługa implementuje również `PublishPriceChange` operację usługi, którą program źródła danych wywołuje w celu dostarczenia usługi z nowymi informacjami.</span><span class="sxs-lookup"><span data-stu-id="4be74-119">The service also implements the `PublishPriceChange` service operation, which the data source program calls to provide the service with new information.</span></span> <span data-ttu-id="4be74-120">Program kliencki `PriceChange` implementuje operację usługi, którą usługa wywołuje, aby powiadomić wszystkich abonentów o zmianie ceny.</span><span class="sxs-lookup"><span data-stu-id="4be74-120">The client program implements the `PriceChange` service operation, which the service calls to notify all subscribers of a price change.</span></span>  
  
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
  
 <span data-ttu-id="4be74-121">Usługa używa zdarzenia .NET Framework jako mechanizmu informowania wszystkich subskrybentów o nowych informacjach.</span><span class="sxs-lookup"><span data-stu-id="4be74-121">The service uses a .NET Framework event as the mechanism to inform all subscribers about new information.</span></span> <span data-ttu-id="4be74-122">Gdy klient dołącza do usługi, wywołując Subscribe, zapewnia program obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="4be74-122">When a client joins the service by calling Subscribe, it provides an event handler.</span></span> <span data-ttu-id="4be74-123">Gdy klient opuszcza, ubskrybuje jego obsługi zdarzeń ze zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="4be74-123">When a client leaves, it unsubscribes its event handler from the event.</span></span> <span data-ttu-id="4be74-124">Gdy źródło danych wywołuje usługę, aby zgłosić zmianę ceny, usługa podnosi zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4be74-124">When a data source calls the service to report a price change, the service raises the event.</span></span> <span data-ttu-id="4be74-125">To wywołuje każde wystąpienie usługi, po jednym dla każdego klienta, który subskrybował i powoduje, że ich programy obsługi zdarzeń do wykonania.</span><span class="sxs-lookup"><span data-stu-id="4be74-125">This calls each instance of the service, one for each client that has subscribed, and causes their event handlers to execute.</span></span> <span data-ttu-id="4be74-126">Każdy program obsługi zdarzeń przekazuje informacje do swojego klienta za pośrednictwem funkcji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4be74-126">Each event handler passes the information to its client through its callback function.</span></span>  
  
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
  
 <span data-ttu-id="4be74-127">Po uruchomieniu próbki uruchom kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="4be74-127">When you run the sample, launch several clients.</span></span> <span data-ttu-id="4be74-128">Klienci subskrybują usługę.</span><span class="sxs-lookup"><span data-stu-id="4be74-128">The clients subscribe to the service.</span></span> <span data-ttu-id="4be74-129">Następnie uruchom program źródła danych, który wysyła informacje do usługi.</span><span class="sxs-lookup"><span data-stu-id="4be74-129">Then run the data source program, which sends information to the service.</span></span> <span data-ttu-id="4be74-130">Usługa przekazuje informacje do wszystkich subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="4be74-130">The service passes on the information to all subscribers.</span></span> <span data-ttu-id="4be74-131">Możesz zobaczyć działanie na każdej konsoli klienta potwierdzające, że informacje zostały odebrane.</span><span class="sxs-lookup"><span data-stu-id="4be74-131">You can see activity on each client console confirming that the information has been received.</span></span> <span data-ttu-id="4be74-132">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="4be74-132">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4be74-133">Aby skonfigurować i utworzyć próbkę</span><span class="sxs-lookup"><span data-stu-id="4be74-133">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="4be74-134">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4be74-134">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4be74-135">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4be74-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4be74-136">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="4be74-136">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="4be74-137">Sprawdź, czy możesz uzyskać dostęp do usługi za `http://localhost/servicemodelsamples/service.svc`pomocą przeglądarki, wprowadzając następujący adres: .</span><span class="sxs-lookup"><span data-stu-id="4be74-137">Test that you can access the service using a browser by entering the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="4be74-138">W odpowiedzi powinna zostać wyświetlona strona potwierdzenia.</span><span class="sxs-lookup"><span data-stu-id="4be74-138">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="4be74-139">Uruchom plik Client.exe z\\\client\bin , spod folderu specyficznego dla języka.</span><span class="sxs-lookup"><span data-stu-id="4be74-139">Run Client.exe from \client\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="4be74-140">Aktywność klienta jest wyświetlana w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="4be74-140">Client activity is displayed on the client console window.</span></span> <span data-ttu-id="4be74-141">Uruchom kilku klientów.</span><span class="sxs-lookup"><span data-stu-id="4be74-141">Launch several clients.</span></span>  
  
3. <span data-ttu-id="4be74-142">Uruchom plik Datasource.exe z\\\datasource\bin , spod folderu specyficznego dla języka.</span><span class="sxs-lookup"><span data-stu-id="4be74-142">Run Datasource.exe from \datasource\bin\\, from under the language-specific folder.</span></span> <span data-ttu-id="4be74-143">Aktywność źródła danych jest wyświetlana w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4be74-143">Data source activity is displayed on the console window.</span></span> <span data-ttu-id="4be74-144">Gdy źródło danych wysyła informacje do usługi, powinny być przekazywane do każdego klienta.</span><span class="sxs-lookup"><span data-stu-id="4be74-144">Once the data source sends information to the service, it should be passed on to each client.</span></span>  
  
4. <span data-ttu-id="4be74-145">Jeśli klient, źródło danych i programy usługowe nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów z próbkami WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4be74-145">If the client, data source, and service programs are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4be74-146">Aby uruchomić próbkę na różnych komputerach</span><span class="sxs-lookup"><span data-stu-id="4be74-146">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="4be74-147">Skonfiguruj urządzenie serwisowe:</span><span class="sxs-lookup"><span data-stu-id="4be74-147">Set up the service machine:</span></span>  
  
    1. <span data-ttu-id="4be74-148">Na komputerze serwisowym utwórz katalog wirtualny o nazwie ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="4be74-148">On the service machine, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="4be74-149">Plik wsadowy Setupvroot.bat z [procedury jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) może służyć do tworzenia katalogu dysku i katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="4be74-149">The batch file Setupvroot.bat from the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md) can be used to create the disk directory and virtual directory.</span></span>  
  
    2. <span data-ttu-id="4be74-150">Skopiuj pliki programu serwisowego z %SystemDrive%\Inetpub\wwwroot\servicemodelsamples do katalogu wirtualnego ServiceModelSamples na komputerze serwisowym.</span><span class="sxs-lookup"><span data-stu-id="4be74-150">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service machine.</span></span> <span data-ttu-id="4be74-151">Pamiętaj, aby dołączyć pliki do katalogu \bin.</span><span class="sxs-lookup"><span data-stu-id="4be74-151">Be sure to include the files in the \bin directory.</span></span>  
  
    3. <span data-ttu-id="4be74-152">Sprawdź, czy można uzyskać dostęp do usługi z komputera klienckiego za pomocą przeglądarki.</span><span class="sxs-lookup"><span data-stu-id="4be74-152">Test that you can access the service from the client machine using a browser.</span></span>  
  
2. <span data-ttu-id="4be74-153">Skonfiguruj maszyny klienckie:</span><span class="sxs-lookup"><span data-stu-id="4be74-153">Set up the client machines:</span></span>  
  
    1. <span data-ttu-id="4be74-154">Skopiuj pliki programu klienckiego z folderu \client\bin\ w folderze specyficznym dla języka na maszyny klienckie.</span><span class="sxs-lookup"><span data-stu-id="4be74-154">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machines.</span></span>  
  
    2. <span data-ttu-id="4be74-155">W każdym pliku konfiguracji klienta zmień wartość adresu definicji punktu końcowego, aby dopasować nowy adres usługi.</span><span class="sxs-lookup"><span data-stu-id="4be74-155">In each client configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="4be74-156">Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="4be74-156">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
3. <span data-ttu-id="4be74-157">Konfigurowanie komputera źródła danych:</span><span class="sxs-lookup"><span data-stu-id="4be74-157">Set up the data source machine:</span></span>  
  
    1. <span data-ttu-id="4be74-158">Skopiuj pliki programu źródła danych z folderu \datasource\bin\ w folderze specyficznym dla języka do komputera źródła danych.</span><span class="sxs-lookup"><span data-stu-id="4be74-158">Copy the data source program files from the \datasource\bin\ folder, under the language-specific folder, to the data source machine.</span></span>  
  
    2. <span data-ttu-id="4be74-159">W pliku konfiguracji źródła danych zmień wartość adresu definicji punktu końcowego, aby dopasować go do nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="4be74-159">In the data source configuration file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="4be74-160">Zastąp wszelkie odwołania do "localhost" w pełni kwalifikowaną nazwą domeny w adresie.</span><span class="sxs-lookup"><span data-stu-id="4be74-160">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
4. <span data-ttu-id="4be74-161">Na komputerach klienckich uruchom program Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4be74-161">On the client machines, launch Client.exe from a command prompt.</span></span>  
  
5. <span data-ttu-id="4be74-162">Na komputerze ze źródłem danych uruchom program Datasource.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4be74-162">On the data source machine, launch Datasource.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4be74-163">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4be74-163">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4be74-164">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="4be74-164">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4be74-165">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="4be74-165">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4be74-166">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="4be74-166">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DesignPatterns/ListBasedPublishSubscribe`  
