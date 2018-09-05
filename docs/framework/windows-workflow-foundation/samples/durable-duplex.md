---
title: Niezawodna komunikacja dwukierunkowa
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 107c617fa4a8ee0279dcaa07e495587c617b866e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513356"
---
# <a name="durable-duplex"></a><span data-ttu-id="fa257-102">Niezawodna komunikacja dwukierunkowa</span><span class="sxs-lookup"><span data-stu-id="fa257-102">Durable Duplex</span></span>
<span data-ttu-id="fa257-103">W tym przykładzie przedstawiono sposób instalowania i konfigurowania trwałe dwukierunkowego wiadomości programu exchange, przy użyciu działań dotyczących komunikatów w Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="fa257-103">This sample demonstrates how to set up and configure durable duplex message exchange using the messaging activities in Windows Workflow Foundation (WF).</span></span> <span data-ttu-id="fa257-104">Exchange trwałych wiadomości dwukierunkowego jest dwukierunkowej wiadomości programu exchange, która ma miejsce w długim okresie czasu.</span><span class="sxs-lookup"><span data-stu-id="fa257-104">A durable duplex message exchange is a two-way message exchange that takes place over a long period of time.</span></span> <span data-ttu-id="fa257-105">Okres istnienia wymiany komunikatów może być dłuższy niż okres istnienia kanał komunikacyjny i okresu istnienia wystąpienia usługi w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fa257-105">The lifetime of the message exchange may be longer than the lifetime of the communication channel and the in-memory lifetime of the service instances.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="fa257-106">Przykład szczegółów</span><span class="sxs-lookup"><span data-stu-id="fa257-106">Sample Details</span></span>  
 <span data-ttu-id="fa257-107">W tym przykładzie dwie usługi Windows Communication Foundation (WCF) implementowane przy użyciu programu Windows Workflow Foundation są skonfigurowane do program exchange trwałych wiadomości dwukierunkowego.</span><span class="sxs-lookup"><span data-stu-id="fa257-107">In this sample, two Windows Communication Foundation (WCF) services implemented using Windows Workflow Foundation are configured to have a durable duplex message exchange.</span></span> <span data-ttu-id="fa257-108">Wymiany trwałych wiadomości dwukierunkowego składa się z dwóch jednokierunkowe komunikaty wysyłane za pośrednictwem usługi MSMQ i korelować je przy użyciu [wymiana kontekstu .NET](https://go.microsoft.com/fwlink/?LinkID=166059).</span><span class="sxs-lookup"><span data-stu-id="fa257-108">The durable duplex message exchange is composed from two one-way messages sent over MSMQ and correlated using [.NET Context Exchange](https://go.microsoft.com/fwlink/?LinkID=166059).</span></span> <span data-ttu-id="fa257-109">Komunikaty są wysyłane przy użyciu <xref:System.ServiceModel.Activities.Send> i <xref:System.ServiceModel.Activities.Receive> działań dotyczących komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa257-109">The messages are sent using the <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.Receive> messaging activities.</span></span> <span data-ttu-id="fa257-110">Wymiana kontekstu .NET jest używany do określenia adresu zwrotnego na wysłanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa257-110">.NET Context Exchange is use to specify the callback address on the sent messages.</span></span> <span data-ttu-id="fa257-111">Obie te usługi są hostowane przy użyciu usługi aktywacji procesów Windows (WAS) i są skonfigurowane, aby włączyć opcję trwałości wystąpień usługi.</span><span class="sxs-lookup"><span data-stu-id="fa257-111">Both services are hosted using Windows Process Activation Services (WAS) and are configured to enable persistence of the services instances.</span></span>  
  
 <span data-ttu-id="fa257-112">Pierwsza usługa (Service1.xamlx) wysyła żądanie do wysyłania usługi (Service2.xamlx) wykonania dodatkowych czynności.</span><span class="sxs-lookup"><span data-stu-id="fa257-112">The first service (Service1.xamlx) sends a request to the send service (Service2.xamlx) to do some work.</span></span> <span data-ttu-id="fa257-113">Po ukończeniu pracy Service2.xamlx wysyła powiadomienie do Service1.xamlx, aby wskazać, że praca została ukończona.</span><span class="sxs-lookup"><span data-stu-id="fa257-113">Once the work is completed, Service2.xamlx sends a notification back to Service1.xamlx to indicate that the work has been completed.</span></span> <span data-ttu-id="fa257-114">Aplikacja konsoli przepływu pracy konfiguruje kolejki, które usługi nasłuchują i wysyła początkowy komunikat uruchomienia można aktywować Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="fa257-114">A workflow console application sets up the queues that the services are listening on and sends the initial Start message to activate Service1.xamlx.</span></span> <span data-ttu-id="fa257-115">Po Service1.xamlx odbiera powiadomienia z Service2.xamlx czy żądanej pracy wykonanej, Service1.xamlx zapisuje wynik w pliku XML.</span><span class="sxs-lookup"><span data-stu-id="fa257-115">Once Service1.xamlx receives the notification from Service2.xamlx that the requested work has been completed, Service1.xamlx saves the result to an XML file.</span></span> <span data-ttu-id="fa257-116">Podczas oczekiwania na komunikat wywołania zwrotnego, Service1.xamlx będzie się powtarzał jego stan wystąpienia przy użyciu domyślnego <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span><span class="sxs-lookup"><span data-stu-id="fa257-116">While waiting for the callback message, Service1.xamlx persists its instance state using the default <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>.</span></span> <span data-ttu-id="fa257-117">Jego stan wystąpienia jako część ukończenia pracy nad żądaniem Service1.xamlx Service2.xamlx, będzie się powtarzać.</span><span class="sxs-lookup"><span data-stu-id="fa257-117">Service2.xamlx persists its instance state as part of completing the work requested by Service1.xamlx.</span></span>  
  
 <span data-ttu-id="fa257-118">Aby skonfigurować usługi do użycia wymiana kontekstu platformy .NET za pośrednictwem usługi MSMQ, obie usługi są skonfigurowane do używania niestandardowego powiązania, który składa się z <xref:System.ServiceModel.Channels.ContextBindingElement> i <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="fa257-118">To configure the services to use .NET Context Exchange over MSMQ, both services are configured to use a custom binding that consists of the <xref:System.ServiceModel.Channels.ContextBindingElement> and the <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>.</span></span> <span data-ttu-id="fa257-119">Adres wywołania zwrotnego jest określony za pomocą <xref:System.ServiceModel.Channels.ContextBindingElement> i znajduje się w nagłówku Kontekst wywołania zwrotnego z wszystkie komunikaty wysyłane za pomocą niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa257-119">A callback address is specified with the <xref:System.ServiceModel.Channels.ContextBindingElement> and is included in a callback context header with all messages sent using a custom binding.</span></span> <span data-ttu-id="fa257-120">Poniższy kod definiuje niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa257-120">The following code example defines the custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="fa257-121">Wiązanie używane przez ten przykład nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="fa257-121">The binding used by this sample is not secure.</span></span> <span data-ttu-id="fa257-122">W przypadku wdrażania aplikacji należy skonfigurować Twoje powiązanie, w oparciu o wymagania dotyczące zabezpieczeń aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fa257-122">When deploying your application you should configure your binding based on the security requirements of your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa257-123">Kolejki, używane w tym przykładzie nie są transakcyjne.</span><span class="sxs-lookup"><span data-stu-id="fa257-123">The queues used in this sample are not transactional.</span></span> <span data-ttu-id="fa257-124">Dla przykładu, który pokazuje, jak skonfigurować wymianę komunikatów WCF przy użyciu funkcji kolejek transakcji, zobacz [Aktywacja usługi MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="fa257-124">For a sample that shows how to set up WCF message exchanges using transaction queues, see the [MSMQ Activation](../../../../docs/framework/wcf/samples/msmq-activation.md) sample.</span></span>  
  
 <span data-ttu-id="fa257-125">Komunikat wysyłany przez Service1.xamlx do Service2.xamlx są wysyłane przy użyciu klienta punktu końcowego, konfiguruje się adres Service2.xamlx i niestandardowego powiązania zdefiniowane wcześniej.</span><span class="sxs-lookup"><span data-stu-id="fa257-125">The message sent by Service1.xamlx to Service2.xamlx is sent using a client endpoint configured with the address of Service2.xamlx and the custom binding defined previously.</span></span> <span data-ttu-id="fa257-126">Wywołania zwrotnego z Service2.xamlx Service1.xamlx są wysyłane przy użyciu punktu końcowego klienta przy użyciu nie jawnie skonfigurowanego adresu, ponieważ adres jest pobierana z kontekstu wywołanie zwrotne wysyłane przez Service1.xamlx.</span><span class="sxs-lookup"><span data-stu-id="fa257-126">The callback from Service2.xamlx to Service1.xamlx is sent using a client endpoint with no explicitly configured address because the address is taken from the callback context sent by Service1.xamlx.</span></span> <span data-ttu-id="fa257-127">Poniższy kod definiuje punktów końcowych klienta.</span><span class="sxs-lookup"><span data-stu-id="fa257-127">The following code example defines the client endpoints.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fa257-128">Poniższy przykład kodu przedstawia punktów końcowych przy użyciu tego niestandardowego powiązania, zmieniając domyślnego mapowania protokołu dla net.msmq adres podstawowy do użycia tego niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="fa257-128">The following code example exposes endpoints using this custom binding by changing the default protocol mapping for net.msmq base addresses to use this custom binding.</span></span>  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="fa257-129">Poniższy przykład kodu umożliwia stanów trwałych dla obu usług, dodając <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> zachowanie do usług i określanie parametrów połączenia dla bazy danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="fa257-129">The following code example enables persistence for both services by adding the <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> behavior to both services and specifying the connection string for the persistence database.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a><span data-ttu-id="fa257-130">Wymagania systemowe</span><span class="sxs-lookup"><span data-stu-id="fa257-130">System Requirements</span></span>  
 <span data-ttu-id="fa257-131">Ten przykładowy skrypt wymaga następujących składników.</span><span class="sxs-lookup"><span data-stu-id="fa257-131">This sample requires the following components.</span></span>  
  
1.  <span data-ttu-id="fa257-132">Internetowe usługi informacyjne.</span><span class="sxs-lookup"><span data-stu-id="fa257-132">Internet Information Services.</span></span>  
  
2.  <span data-ttu-id="fa257-133">Internetowe usługi informacyjne -> zgodność z narzędziami zarządzania usług IIS 6.0 -> zgodności konfiguracji metabazy usług IIS i usług IIS 6.0.</span><span class="sxs-lookup"><span data-stu-id="fa257-133">Internet Information Services -> IIS 6.0 Management Compatibility -> IIS Metabase and IIS 6.0 configuration compatibility.</span></span>  
  
3.  <span data-ttu-id="fa257-134">Usługi World Wide Web -> Tworzenie aplikacji funkcji -> ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="fa257-134">World Wide Web Services -> Application Development Features -> ASP.NET.</span></span>  
  
4.  <span data-ttu-id="fa257-135">Microsoft Message kolejki (MSMQ) serwer.</span><span class="sxs-lookup"><span data-stu-id="fa257-135">Microsoft Message Queues (MSMQ) Server.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fa257-136">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="fa257-136">To use this sample</span></span>  
  
1.  <span data-ttu-id="fa257-137">Konfigurowanie bazy danych trwałości i katalog wyników.</span><span class="sxs-lookup"><span data-stu-id="fa257-137">Set up the persistence database and the results directory.</span></span>  
  
    1.  <span data-ttu-id="fa257-138">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-138">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="fa257-139">Przejdź do folderu, w tym przykładzie, a następnie uruchom plik Setup.cmd.</span><span class="sxs-lookup"><span data-stu-id="fa257-139">Navigate to the folder for this sample and run Setup.cmd.</span></span>  
  
2.  <span data-ttu-id="fa257-140">Konfigurowanie aplikacji wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="fa257-140">Set up the virtual application.</span></span>  
  
    1.  <span data-ttu-id="fa257-141">Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersz polecenia, Zarejestruj aplikację ASP.NET przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-141">From a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt, register ASP.NET by running the following command.</span></span>  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  <span data-ttu-id="fa257-142">Uruchom [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] z uprawnieniami administratora, klikając prawym przyciskiem myszy [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierając polecenie **Uruchom jako administrator**.</span><span class="sxs-lookup"><span data-stu-id="fa257-142">Run [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] with administrator permissions by right-clicking [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] and selecting **Run as administrator**.</span></span>  
  
    3.  <span data-ttu-id="fa257-143">Za pomocą [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otwórz plik DurableDuplex.sln.</span><span class="sxs-lookup"><span data-stu-id="fa257-143">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the DurableDuplex.sln file.</span></span>  
  
3.  <span data-ttu-id="fa257-144">Konfigurowanie usługi kolejki.</span><span class="sxs-lookup"><span data-stu-id="fa257-144">Set up the service queues.</span></span>  
  
    1.  <span data-ttu-id="fa257-145">Aby uruchomić klienta DurableDuplex, naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="fa257-145">To run the DurableDuplex client, press F5.</span></span>  
  
    2.  <span data-ttu-id="fa257-146">Otwórz **Zarządzanie komputerem** konsoli, uruchamiając `Compmgmt.msc` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-146">Open the **Computer Management** console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    3.  <span data-ttu-id="fa257-147">Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**.</span><span class="sxs-lookup"><span data-stu-id="fa257-147">Expand **Service and Applications**, **Message Queuing**.</span></span> <span data-ttu-id="fa257-148">**Kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="fa257-148">**Private Queues**.</span></span>  
  
    4.  <span data-ttu-id="fa257-149">Kliknij prawym przyciskiem myszy durableduplex/service1.xamlx i durableduplex/service2.xamlx kolejek, a następnie wybierz pozycję **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="fa257-149">Right-click the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues and select **Properties**.</span></span>  
  
    5.  <span data-ttu-id="fa257-150">Wybierz **zabezpieczeń** kartę i umożliwiają **wszyscy odbieranie wiadomości**, **wglądu do wiadomości** i **wysyłania komunikatu** uprawnienia dla obu kolejek.</span><span class="sxs-lookup"><span data-stu-id="fa257-150">Select the **Security** tab and allow **Everyone Receive Message**, **Peek Message** and **Send Message** permissions for both queues.</span></span>  
  
    6.  <span data-ttu-id="fa257-151">Otwórz Menedżera internetowych usług informacyjnych (IIS).</span><span class="sxs-lookup"><span data-stu-id="fa257-151">Open Internet Information Services (IIS) Manager.</span></span>  
  
    7.  <span data-ttu-id="fa257-152">Przejdź do **serwera**, **witryn**, **domyślnej witryny sieci Web**, **prywatnej**, **trwałe dwukierunkowego** i wybierz pozycję **Zaawansowane opcje**.</span><span class="sxs-lookup"><span data-stu-id="fa257-152">Browse to **Server**, **Sites**, **Default Web site**, **private**, **Durable Duplex** and select **Advanced Options**.</span></span>  
  
    8.  <span data-ttu-id="fa257-153">Zmiana **włączone protokoły** do **http,net.msmq**.</span><span class="sxs-lookup"><span data-stu-id="fa257-153">Change the **Enabled Protocols** to **http,net.msmq**.</span></span>  
  
4.  <span data-ttu-id="fa257-154">Uruchamianie aplikacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="fa257-154">Run the sample.</span></span>  
  
    1.  <span data-ttu-id="fa257-155">Przejdź do http://localhost/private/durableduplex/service1.xamlx i http://localhost/private/durableduplex/service2.xamlx aby upewnić się, że obie te usługi są uruchomione.</span><span class="sxs-lookup"><span data-stu-id="fa257-155">Browse to http://localhost/private/durableduplex/service1.xamlx and http://localhost/private/durableduplex/service2.xamlx to ensure that both services are running.</span></span>  
  
    2.  <span data-ttu-id="fa257-156">Naciśnij klawisz F5, aby uruchomić DurableDuplexClient.</span><span class="sxs-lookup"><span data-stu-id="fa257-156">Press F5 to run DurableDuplexClient.</span></span>  
  
         <span data-ttu-id="fa257-157">Po zakończeniu wymiany trwałych wiadomości dwukierunkowego result.xml pliku zostanie zapisana w folderze C:\Inbox i zawiera wynik wymianę komunikatów.</span><span class="sxs-lookup"><span data-stu-id="fa257-157">When the durable duplex message exchange completes a result.xml file is saved to the C:\Inbox folder and contains the result of the message exchange.</span></span>  
  
#### <a name="to-cleanup-optional"></a><span data-ttu-id="fa257-158">Aby oczyścić (opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="fa257-158">To cleanup (Optional)</span></span>  
  
1.  <span data-ttu-id="fa257-159">Uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="fa257-159">Run Cleanup.cmd.</span></span>  
  
    1.  <span data-ttu-id="fa257-160">Otwórz [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-160">Open a [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] command prompt.</span></span>  
  
    2.  <span data-ttu-id="fa257-161">Przejdź do folderu, w tym przykładzie, a następnie uruchom Cleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="fa257-161">Navigate to the folder for this sample and run Cleanup.cmd.</span></span>  
  
2.  <span data-ttu-id="fa257-162">Usuń aplikację wirtualną dla usług.</span><span class="sxs-lookup"><span data-stu-id="fa257-162">Remove the virtual application for the services.</span></span>  
  
    1.  <span data-ttu-id="fa257-163">Otwórz Menedżera usług Internet Information Services (IIS), uruchamiając `Inetmgr.exe` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-163">Open the Internet Information Services (IIS) Manager by running `Inetmgr.exe` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="fa257-164">Przejdź do domyślnej witryny sieci Web, a następnie usuń **prywatnej** katalogu wirtualnego.</span><span class="sxs-lookup"><span data-stu-id="fa257-164">Browse to the default Web site and remove the **private** virtual directory.</span></span>  
  
3.  <span data-ttu-id="fa257-165">Usunięcie kolejki, skonfiguruj dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="fa257-165">Remove the queues set up for this sample.</span></span>  
  
    1.  <span data-ttu-id="fa257-166">Otwórz konsolę Zarządzanie komputerem, uruchamiając `Compmgmt.msc` z poziomu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="fa257-166">Open the Computer Management console by running `Compmgmt.msc` from a command prompt.</span></span>  
  
    2.  <span data-ttu-id="fa257-167">Rozwiń **usługi i aplikacje**, **usługi kolejkowania komunikatów**, **kolejki prywatne**.</span><span class="sxs-lookup"><span data-stu-id="fa257-167">Expand **Service and Applications**, **Message Queuing**, **Private Queues**.</span></span>  
  
    3.  <span data-ttu-id="fa257-168">Usuwanie kolejek durableduplex/service1.xamlx i durableduplex/service2.xamlx.</span><span class="sxs-lookup"><span data-stu-id="fa257-168">Delete the durableduplex/service1.xamlx and durableduplex/service2.xamlx queues.</span></span>  
  
4.  <span data-ttu-id="fa257-169">Usuń katalog C:\Inbox.</span><span class="sxs-lookup"><span data-stu-id="fa257-169">Remove the C:\Inbox directory.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa257-170">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="fa257-170">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fa257-171">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="fa257-171">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa257-172">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="fa257-172">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa257-173">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fa257-173">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`