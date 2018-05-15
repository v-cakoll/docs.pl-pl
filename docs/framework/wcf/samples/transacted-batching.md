---
title: Obsługa wsadowa w ramach transakcji
ms.date: 03/30/2017
ms.assetid: ecd328ed-332e-479c-a894-489609bcddd2
ms.openlocfilehash: 7df65b8f3f149deac841010e392f3919b24506b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="transacted-batching"></a><span data-ttu-id="d08ef-102">Obsługa wsadowa w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="d08ef-102">Transacted Batching</span></span>
<span data-ttu-id="d08ef-103">W tym przykładzie pokazano, jak partii odczyty transakcyjne przy użyciu usługi kolejkowania komunikatów (MSMQ).</span><span class="sxs-lookup"><span data-stu-id="d08ef-103">This sample demonstrates how to batch transacted reads by using Message Queuing (MSMQ).</span></span> <span data-ttu-id="d08ef-104">Wsadowe transakcyjne jest funkcja optymalizacji wydajności dla odczytów transakcyjnych w kolejce komunikacji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-104">Transacted Batching is a performance optimization feature for transacted reads in queued communication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d08ef-105">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d08ef-106">W kolejce komunikacji klient komunikuje się z usługą przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-106">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="d08ef-107">Mówiąc ściślej klient wysyła wiadomości do kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-107">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="d08ef-108">Usługa odbiera komunikaty z kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-108">The service receives messages from the queue.</span></span> <span data-ttu-id="d08ef-109">Usługi i klienta w związku z tym ma być uruchomiona, w tym samym czasie do komunikowania się przy użyciu kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-109">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="d08ef-110">W tym przykładzie przedstawiono transakcyjnego przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="d08ef-110">This sample demonstrates transacted batching.</span></span> <span data-ttu-id="d08ef-111">Transakcyjnego przetwarzania wsadowego jest to zachowanie, która umożliwia korzystanie z jednej transakcji podczas odczytywania wiele wiadomości w kolejce i przetwarzanie ich.</span><span class="sxs-lookup"><span data-stu-id="d08ef-111">Transacted batching is a behavior that enables the use of a single transaction when reading many messages in the queue and processing them.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d08ef-112">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="d08ef-112">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d08ef-113">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d08ef-113">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d08ef-114">Jeśli usługa jest uruchamiana pierwszy, sprawdza, upewnij się, że kolejka jest obecny.</span><span class="sxs-lookup"><span data-stu-id="d08ef-114">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="d08ef-115">Jeśli kolejka nie jest obecny, będzie utworzyć usługę.</span><span class="sxs-lookup"><span data-stu-id="d08ef-115">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="d08ef-116">Można uruchomić usługi, aby najpierw utworzyć kolejkę, lub można go utworzyć za pomocą Menedżera kolejki usługi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="d08ef-116">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="d08ef-117">Wykonaj następujące kroki, aby utworzyć kolejkę w systemie Windows 2008.</span><span class="sxs-lookup"><span data-stu-id="d08ef-117">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="d08ef-118">Otwórz Menedżera serwera w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d08ef-118">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="d08ef-119">Rozwiń węzeł **funkcje** kartę.</span><span class="sxs-lookup"><span data-stu-id="d08ef-119">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="d08ef-120">Kliknij prawym przyciskiem myszy **kolejki wiadomości prywatne**i wybierz **nowy**, **kolejki prywatnej**.</span><span class="sxs-lookup"><span data-stu-id="d08ef-120">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="d08ef-121">Sprawdź **transakcyjna** pole.</span><span class="sxs-lookup"><span data-stu-id="d08ef-121">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="d08ef-122">Wprowadź `ServiceModelSamplesTransacted` jako nazwę nowej kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-122">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d08ef-123">W tym przykładzie klient wysyła setki wiadomości jako część partii.</span><span class="sxs-lookup"><span data-stu-id="d08ef-123">In this sample the client sends hundreds of messages as part of the batch.</span></span> <span data-ttu-id="d08ef-124">Jest zjawiskiem aplikacji usługi do trochę potrwać zostać przetworzone.</span><span class="sxs-lookup"><span data-stu-id="d08ef-124">It is normal for the service application to take some time to process these.</span></span>  
  
3.  <span data-ttu-id="d08ef-125">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d08ef-125">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="d08ef-126">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d08ef-126">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="d08ef-127">Aby uruchomić na komputerze, na przykład dołączona do grupy roboczej lub bez integracji z usługą active directory</span><span class="sxs-lookup"><span data-stu-id="d08ef-127">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="d08ef-128">Domyślnie z <xref:System.ServiceModel.NetMsmqBinding>, zabezpieczeń transportu jest włączona.</span><span class="sxs-lookup"><span data-stu-id="d08ef-128">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="d08ef-129">Istnieją dwa odpowiednie właściwości dla zabezpieczeń transportu MSMQ, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> i <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A> `.` domyślnie tryb uwierzytelniania jest ustawiony na `Windows` i poziom ochrony jest ustawiony na `Sign`.</span><span class="sxs-lookup"><span data-stu-id="d08ef-129">There are two relevant properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="d08ef-130">Dla usługi MSMQ w celu zapewnienia uwierzytelniania oraz podpisywania funkcji musi być częścią domeny, a opcja integracji usługi active directory dla usługi MSMQ musi być zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="d08ef-130">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="d08ef-131">Jeśli w tym przykładzie jest uruchomiony na komputerze, który nie spełnia te kryteria, wystąpi błąd.</span><span class="sxs-lookup"><span data-stu-id="d08ef-131">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
2.  <span data-ttu-id="d08ef-132">Jeśli komputer nie jest częścią domeny lub nie ma zainstalowanych integracji usługi active directory, należy wyłączyć zabezpieczeń transportu przez ustawienie poziomu uwierzytelniania w trybie i ochrony `None` jak pokazano w poniższych Przykładowa konfiguracja:</span><span class="sxs-lookup"><span data-stu-id="d08ef-132">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration:</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <behaviors>  
        <serviceBehaviors>  
          <behavior name="ThrottlingBehavior">  
            <serviceMetadata httpGetEnabled="true"/>  
            <serviceThrottling maxConcurrentCalls="5"/>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="BatchingBehavior">  
            <transactedBatching maxBatchSize="100"/>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>  
      <services>  
        <service   
            behaviorConfiguration="ThrottlingBehavior"   
            name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
          <host>  
            <baseAddresses>  
              <add baseAddress="http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint address="net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                    binding="netMsmqBinding"  
                    bindingConfiguration="Binding1"   
                    behaviorConfiguration="BatchingBehavior"   
                    contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="d08ef-133">Sprawdź, czy zmian konfiguracji na serwerze i kliencie, przed uruchomieniem próbki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-133">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d08ef-134">Ustawienie `security``mode` do `None` jest odpowiednikiem ustawienia <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, i `Message` zabezpieczeń do `None`.</span><span class="sxs-lookup"><span data-stu-id="d08ef-134">Setting `security``mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
4.  <span data-ttu-id="d08ef-135">Aby uruchomić bazy danych na komputerze zdalnym, Zmień parametry połączenia, aby wskazywały na komputerze, na którym znajdują się bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d08ef-135">To run the database on a remote computer, change the connection string to point to the computer on which the database resides.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d08ef-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d08ef-136">Requirements</span></span>  
 <span data-ttu-id="d08ef-137">Aby uruchomić ten przykład, muszą zostać zainstalowane usługi MSMQ i bazy danych SQL lub programu SQL Express jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="d08ef-137">To run this sample, MSMQ must be installed and SQL or SQL Express is required.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d08ef-138">Demonstracje</span><span class="sxs-lookup"><span data-stu-id="d08ef-138">Demonstrates</span></span>  
 <span data-ttu-id="d08ef-139">W przykładzie pokazano transakcyjnego łączenia we wsady zachowanie.</span><span class="sxs-lookup"><span data-stu-id="d08ef-139">The sample demonstrates transacted batching behavior.</span></span> <span data-ttu-id="d08ef-140">Transakcyjnego przetwarzania wsadowego jest funkcja optymalizacji wydajności dostarczane z usługi MSMQ w kolejce transportu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-140">Transacted batching is a performance optimization feature provided with MSMQ queued transport.</span></span>  
  
 <span data-ttu-id="d08ef-141">Jeśli transakcje są używane do wysyłania i odbierania wiadomości są faktycznie 2 oddzielne transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-141">When transactions are used to send and receive messages there are actually 2 separate transactions.</span></span> <span data-ttu-id="d08ef-142">Gdy klient wysyła komunikaty w zakresie transakcji, transakcja jest lokalne klient i klient menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="d08ef-142">When the client sends messages within the scope of a transaction, the transaction is local to the client and the client queue manager.</span></span> <span data-ttu-id="d08ef-143">Gdy usługa odbiera komunikaty w zakresie transakcji, transakcja jest lokalnego do usługi i odbierającego menedżera kolejek.</span><span class="sxs-lookup"><span data-stu-id="d08ef-143">When the service receives messages within the scope of the transaction, the transaction is local to the service and the receiving queue manager.</span></span> <span data-ttu-id="d08ef-144">Jest bardzo ważne, aby należy pamiętać, że klient i usługa nie uczestniczą w tej samej transakcji; zamiast używają różnych transakcji podczas wykonywania ich działania (takie jak wysyłanie i odbieranie) z kolejką.</span><span class="sxs-lookup"><span data-stu-id="d08ef-144">It is very important to remember that the client and the service are not participating in the same transaction; rather they are using different transactions when performing their operations (such as send and receive) with the queue.</span></span>  
  
 <span data-ttu-id="d08ef-145">W przykładzie używamy pojedynczej transakcji do wykonania wielu operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d08ef-145">In the sample we use a single transaction for the execution of multiple service operations.</span></span> <span data-ttu-id="d08ef-146">To jest używany tylko jako funkcja optymalizacji wydajności i nie ma wpływu na semantykę aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-146">This is used only as a performance optimization feature and does not impact the semantics of the application.</span></span> <span data-ttu-id="d08ef-147">Próbki jest oparta na [nietransakcyjnego powiązanie MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span><span class="sxs-lookup"><span data-stu-id="d08ef-147">The sample is based on [Transacted MSMQ Binding](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="d08ef-148">Komentarze</span><span class="sxs-lookup"><span data-stu-id="d08ef-148">Comments</span></span>  
 <span data-ttu-id="d08ef-149">W tym przykładzie klient wysyła komunikaty zbiorczo do usługi z zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-149">In this sample, the client sends a batch of messages to the service from within the scope of a transaction.</span></span> <span data-ttu-id="d08ef-150">Aby wyświetlić optymalizacji wydajności, możemy wysyłać dużej liczby wiadomości. w takim przypadku maksymalnie 2500 wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d08ef-150">To show the performance optimization, we send a large number of messages; in this case, up to 2500 messages.</span></span>  
  
 <span data-ttu-id="d08ef-151">Komunikaty wysłane do kolejki następnie są odbierane przez usługę w zakresie transakcji, określonym przez usługę.</span><span class="sxs-lookup"><span data-stu-id="d08ef-151">The messages sent to the queue are then received by the service within the transaction scope defined by the service.</span></span> <span data-ttu-id="d08ef-152">Bez partii, powoduje to 2500 transakcji dla każdego wywołania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d08ef-152">Without batching, this results in 2500 transactions for each invocation of the service operation.</span></span> <span data-ttu-id="d08ef-153">Ma to wpływ na wydajność systemu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-153">This impacts performance of the system.</span></span> <span data-ttu-id="d08ef-154">Ponieważ obejmuje dwa menedżerowie zasobów - kolejki usługi MSMQ i `Orders` bazy danych — każdego tych transakcji jest transakcji usługi DTC.</span><span class="sxs-lookup"><span data-stu-id="d08ef-154">Because two resource managers are involved -the MSMQ queue and the `Orders` database- each such transaction is a DTC transaction.</span></span> <span data-ttu-id="d08ef-155">Zoptymalizowana to przy użyciu znacznie mniejszą liczbę transakcji przez zapewnienie im to zrobić partii komunikatów i wywołania operacji usługi w ramach jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-155">We optimize this by using a much smaller number of transactions by ensuring that a batch of messages and service operation invocations happen in a single transaction.</span></span>  
  
 <span data-ttu-id="d08ef-156">Możemy użyć funkcji łączenia we wsady przez:</span><span class="sxs-lookup"><span data-stu-id="d08ef-156">We use the batching feature by:</span></span>  
  
-   <span data-ttu-id="d08ef-157">Określanie transakcyjnego łączenia we wsady zachowanie w konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-157">Specifying transacted batching behavior in configuration.</span></span>  
  
-   <span data-ttu-id="d08ef-158">Określanie rozmiar partii pod względem liczby wiadomości odczytywane przy użyciu pojedynczej transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-158">Specifying a batch size in terms of number of messages to be read using a single transaction.</span></span>  
  
-   <span data-ttu-id="d08ef-159">Określająca maksymalną liczbę równoczesnych partie do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="d08ef-159">Specifying the maximum number of concurrent batches to run.</span></span>  
  
 <span data-ttu-id="d08ef-160">W tym przykładzie zostanie przedstawiony wydajność dzięki zmniejszeniu liczby transakcji przez zapewnienie, że 100 operacje usług są wywoływane w ramach jednej transakcji przed zatwierdzeniem transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-160">In this example, we show performance gains by reducing the number of transactions by ensuring that 100 service operations are invoked in a single transaction before committing the transaction.</span></span>  
  
 <span data-ttu-id="d08ef-161">Zachowanie usługi definiuje zachowanie operacji z `TransactionScopeRequired` ustawioną `true`.</span><span class="sxs-lookup"><span data-stu-id="d08ef-161">The service behavior defines an operation behavior with `TransactionScopeRequired` set to `true`.</span></span> <span data-ttu-id="d08ef-162">Dzięki temu, że tego samego zakresu transakcji, który służy do pobierania wiadomości z kolejki jest używana przez Menedżera zasobów, wszystkie dostępne metody.</span><span class="sxs-lookup"><span data-stu-id="d08ef-162">This ensures that the same transaction scope that is used to retrieve the message from the queue is used by any resource managers accessed by the method.</span></span> <span data-ttu-id="d08ef-163">W tym przykładzie używamy podstawowej bazy danych do przechowywania informacji o zamówienia zakupu, które zostały zawarte w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d08ef-163">In this example, we use a basic database to store the purchase order information contained in the message.</span></span> <span data-ttu-id="d08ef-164">Zakresu transakcji gwarantuje również, że jeśli metoda zgłosi wyjątek, wiadomość jest zwracana do kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-164">The transaction scope also guarantees that if the method throws an exception, the message is returned to the queue.</span></span> <span data-ttu-id="d08ef-165">Bez ustawienia zachowania tej operacji, kolejkowanym kanale tworzy transakcji, aby odczytać wiadomość z kolejki i zatwierdza ją automatycznie, zanim wywoływane jest tak, aby w przypadku niepowodzenia operacji wiadomości utraconych.</span><span class="sxs-lookup"><span data-stu-id="d08ef-165">Without setting this operation behavior, a queued channel creates a transaction to read the message from the queue and commits it automatically before it is dispatched so that if the operation fails, the message is lost.</span></span> <span data-ttu-id="d08ef-166">Najbardziej typowym scenariuszem jest dla operacji usługi zarejestrować się w transakcji, który jest używany do odczytu komunikatu z kolejki, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="d08ef-166">The most common scenario is for service operations to enlist in the transaction that is used to read the message from the queue as demonstrated in the following code.</span></span>  
  
 <span data-ttu-id="d08ef-167">Należy pamiętać, że `ReleaseServiceInstanceOnTransactionComplete` ma ustawioną wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="d08ef-167">Note that `ReleaseServiceInstanceOnTransactionComplete` is set to `false`.</span></span> <span data-ttu-id="d08ef-168">Jest to ważne potrzeby przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="d08ef-168">This is an important requirement for batching.</span></span> <span data-ttu-id="d08ef-169">Właściwość `ReleaseServiceInstanceOnTransactionComplete` na `ServiceBehaviorAttribute` wskazuje, co należy zrobić po zakończeniu transakcji wystąpienia usługi.</span><span class="sxs-lookup"><span data-stu-id="d08ef-169">The property `ReleaseServiceInstanceOnTransactionComplete` on `ServiceBehaviorAttribute` indicates what to do with the service instance once the transaction is completed.</span></span> <span data-ttu-id="d08ef-170">Domyślnie wystąpienie usługi jest publikowany po zakończeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-170">By default, the service instance is released upon completing the transaction.</span></span> <span data-ttu-id="d08ef-171">Aspekt core do przetwarzania wsadowego jest wykorzystanie pojedynczej transakcji do odczytywania i wysyłania wielu wiadomości w kolejce.</span><span class="sxs-lookup"><span data-stu-id="d08ef-171">The core aspect to batching is the use of a single transaction for reading and dispatching many messages in the queue.</span></span> <span data-ttu-id="d08ef-172">W związku z tym wydanie wystąpienia usługi kończy się wykonanie transakcji przedwcześnie Negacja bardzo stosowania przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="d08ef-172">Therefore releasing the service instance ends up completing the transaction prematurely negating the very use of batching.</span></span> <span data-ttu-id="d08ef-173">Jeśli ta właściwość jest ustawiona na `true` i transakcyjnego łączenia we wsady zachowanie jest dodawany do punktu końcowego, przetwarzanie wsadowe zachowanie weryfikacji zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d08ef-173">If this property is set to `true` and transacted batching behavior is added to the endpoint, the batching validation behavior throws an exception.</span></span>  

```csharp
// Service class that implements the service contract.  
// Added code to write output to the console window.  
[ServiceBehavior(ReleaseServiceInstanceOnTransactionComplete=false,   
TransactionIsolationLevel=  
System.Transactions.IsolationLevel.Serializable, ConcurrencyMode=ConcurrencyMode.Multiple)]  
public class OrderProcessorService : IOrderProcessor  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                       TransactionAutoComplete = true)]  
    public void SubmitPurchaseOrder(PurchaseOrder po)  
    {  
        Orders.Add(po);  
        Console.WriteLine("Processing {0} ", po);  
    }  
    …  
}  
```

 <span data-ttu-id="d08ef-174">`Orders` Klasa hermetyzuje przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="d08ef-174">The `Orders` class encapsulates the processing of the order.</span></span> <span data-ttu-id="d08ef-175">W przykładzie aktualizuje bazę danych z informacji o zamówieniu zakupu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-175">In the sample, it updates the database with purchase order information.</span></span>  

```csharp
// Order Processing Logic  
public class Orders  
{  
    public static void Add(PurchaseOrder po)  
    {  
        // Insert purchase order.  
        SqlCommand insertPurchaseOrderCommand =   
        new SqlCommand(  
        "insert into PurchaseOrders(poNumber, customerId)   
                               values(@poNumber, @customerId)");  
        insertPurchaseOrderCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        insertPurchaseOrderCommand.Parameters.Add("@customerId",   
                                         SqlDbType.VarChar, 50);  
  
        // Insert product line item.  
        SqlCommand insertProductLineItemCommand =   
             new SqlCommand("insert into ProductLineItems(productId,   
                    unitCost, quantity, poNumber) values(@productId,   
                    @unitCost, @quantity, @poNumber)");  
        insertProductLineItemCommand.Parameters.Add("@productId",   
                                           SqlDbType.VarChar, 50);  
        insertProductLineItemCommand.Parameters.Add("@unitCost",   
                                                  SqlDbType.Float);  
        insertProductLineItemCommand.Parameters.Add("@quantity",   
                                                     SqlDbType.Int);  
        insertProductLineItemCommand.Parameters.Add("@poNumber",   
                                           SqlDbType.VarChar, 50);  
        int rowsAffected = 0;  
        using (TransactionScope scope =   
              new TransactionScope(TransactionScopeOption.Required))  
        {  
             using (SqlConnection conn = new   
                 SqlConnection(  
                 ConfigurationManager.AppSettings["connectionString"]))  
             {  
                 conn.Open();  
  
                // Insert into purchase order table.  
               insertPurchaseOrderCommand.Connection = conn;  
               insertPurchaseOrderCommand.Parameters["@poNumber"].Value   
                                                       = po.PONumber;  
             insertPurchaseOrderCommand.Parameters["@customerId"].Value   
                                                    =po.CustomerId;  
             insertPurchaseOrderCommand.ExecuteNonQuery();  
  
            // Insert into product line item table.  
            insertProductLineItemCommand.Connection = conn;  
            foreach (PurchaseOrderLineItem orderLineItem in   
                                        po.orderLineItems) {  
            insertProductLineItemCommand.Parameters["@poNumber"].Value   
                                                          =po.PONumber;  
            insertProductLineItemCommand.Parameters["@productId"].Value   
                                             = orderLineItem.ProductId;  
            insertProductLineItemCommand.Parameters["@unitCost"].Value   
                                             = orderLineItem.UnitCost;  
            insertProductLineItemCommand.Parameters["@quantity"].Value   
                                             = orderLineItem.Quantity;  
            rowsAffected +=   
            insertProductLineItemCommand.ExecuteNonQuery();  
            }  
            scope.Complete();  
        }  
     }  
     Console.WriteLine(  
     "Updated database with {0} product line items  for purchase order   
                                     {1} ", rowsAffected, po.PONumber);  
    }  
}  
```

 <span data-ttu-id="d08ef-176">Przetwarzanie wsadowe zachowania i jego konfiguracja są określone w konfiguracji aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="d08ef-176">The batching behavior and its configuration are specified in the service application configuration.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <appSettings>  
    <!-- Use appSetting to configure MSMQ queue name. -->  
    <add key="queueName"   
     value=".\private$\ServiceModelSamplesTransactedBatching" />  
    <add key="baseAddress"   
     value=  
     "http://localhost:8000/orderProcessor/transactedBatchingSample"/>  
    <add key="connectionString" value="Data Source=.\SQLEXPRESS;AttachDbFilename=|DataDirectory|orders.mdf;Integrated Security=True;User Instance=True;" />  
  </appSettings>  
  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ThrottlingBehavior">  
          <serviceThrottling maxConcurrentCalls="5"/>  
        </behavior>  
      </serviceBehaviors>  
  
      <endpointBehaviors>  
        <behavior name="BatchingBehavior">  
          <transactedBatching maxBatchSize="100"/>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <services>  
      <service   
          behaviorConfiguration="ThrottlingBehavior"   
          name="Microsoft.ServiceModel.Samples.OrderProcessorService">  
        <!-- Define NetMsmqEndpoint -->  
        <endpoint address=  
"net.msmq://localhost/private/ServiceModelSamplesTransactedBatching"  
                  binding="netMsmqBinding"  
                  behaviorConfiguration="BatchingBehavior"   
                  contract=  
                    "Microsoft.ServiceModel.Samples.IOrderProcessor" />  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="d08ef-177">Rozmiar partii to wskazówkę systemu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-177">The batch size is a hint to the system.</span></span> <span data-ttu-id="d08ef-178">Na przykład jeśli określisz rozmiar partii, 20, następnie 20 komunikatów będą odczytywane i wysłane przy użyciu pojedynczej transakcji i następnie transakcja została przekazana.</span><span class="sxs-lookup"><span data-stu-id="d08ef-178">For example, if you specify a batch size of 20, then 20 messages would be read and dispatched using a single transaction and then the transaction is committed.</span></span> <span data-ttu-id="d08ef-179">Istnieją przypadki, w którym może zatwierdzić transakcji partii przed osiągnięciem rozmiar partii.</span><span class="sxs-lookup"><span data-stu-id="d08ef-179">But there are cases where the transaction may commit the batch before the batch size is reached.</span></span>  
>   
>  <span data-ttu-id="d08ef-180">Skojarzone z każdej transakcji jest limit czasu, która rozpoczyna się zaznaczenie po utworzeniu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-180">Associated with every transaction is a timeout that starts ticking once the transaction is created.</span></span> <span data-ttu-id="d08ef-181">Transakcja została przerwana, po upływie tego czasu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-181">When this timeout expires the transaction is aborted.</span></span> <span data-ttu-id="d08ef-182">Istnieje możliwość tego limitu czasu wygaśnięcia nawet przed osiągnięciem rozmiaru partii.</span><span class="sxs-lookup"><span data-stu-id="d08ef-182">It is possible for this timeout to expire even before the batch size is reached.</span></span> <span data-ttu-id="d08ef-183">Aby uniknąć ponownego pracy partii z powodu przerwania, `TransactedBatchingBehavior` sprawdza, ile czasu pozostało w transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-183">To avoid re-working the batch because of the abort, the `TransactedBatchingBehavior` checks to see how much time is left on the transaction.</span></span> <span data-ttu-id="d08ef-184">Jeśli wykorzystane 80% czasu transakcji transakcja została przekazana.</span><span class="sxs-lookup"><span data-stu-id="d08ef-184">If 80% of the transaction timeout is used up, then the transaction is committed.</span></span>  
>   
>  <span data-ttu-id="d08ef-185">Jeśli nie ma żadnych więcej wiadomości w kolejce, a następnie zamiast oczekiwania na realizację rozmiar partii <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zatwierdza transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-185">If there are no more messages in the queue then instead of waiting for the fulfillment of the batch size the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> commits the transaction.</span></span>  
>   
>  <span data-ttu-id="d08ef-186">Wybór rozmiar partii jest zależny od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-186">The choice of the batch size is dependent on your application.</span></span> <span data-ttu-id="d08ef-187">Jeśli rozmiar partii jest za mały, nie może pobrać żądaną wydajność.</span><span class="sxs-lookup"><span data-stu-id="d08ef-187">If the batch size is too small, you may not get the desired performance.</span></span> <span data-ttu-id="d08ef-188">Z drugiej strony, jeśli rozmiar partii jest zbyt duży, może pogarszać wydajność.</span><span class="sxs-lookup"><span data-stu-id="d08ef-188">On the other hand if the batch size is too big, it may deteriorate performance.</span></span> <span data-ttu-id="d08ef-189">Na przykład transakcji można już na żywo i przytrzymaj blokady bazy danych lub transakcji może stać się martwych zablokowana, które mogłyby powodować partii pobrać wycofana i wykonaj ponownie pracy.</span><span class="sxs-lookup"><span data-stu-id="d08ef-189">For example, your transaction could live longer and hold locks on your database or your transaction could become dead locked, which could cause the batch to get rolled back and to redo the work.</span></span>  
  
 <span data-ttu-id="d08ef-190">Klient tworzy zakresu transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-190">The client creates a transaction scope.</span></span> <span data-ttu-id="d08ef-191">Komunikacja z kolejki odbywa się w zakresie transakcji, co powoduje traktowane jako Atomowej jednostki, w którym wszystkie komunikaty są wysyłane do kolejki lub brak komunikaty są wysyłane do kolejki.</span><span class="sxs-lookup"><span data-stu-id="d08ef-191">Communication with the queue takes place within the scope of the transaction, causing it to be treated as an atomic unit where all messages are sent to the queue or none of the messages are sent to the queue.</span></span> <span data-ttu-id="d08ef-192">Transakcja zostaje zatwierdzona przez wywołanie metody <xref:System.Transactions.TransactionScope.Complete%2A> w zakresie transakcji.</span><span class="sxs-lookup"><span data-stu-id="d08ef-192">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A> on the transaction scope.</span></span>  

```csharp
//Client implementation code.  
class Client  
{  
    static void Main()  
    {  
        Random randomGen = new Random();  
        for (int i = 0; i < 2500; i++)  
        {  
            // Create a client with given client endpoint configuration.  
            OrderProcessorClient client = new OrderProcessorClient("OrderProcessorEndpoint");  
  
            // Create the purchase order.  
            PurchaseOrder po = new PurchaseOrder();  
            po.CustomerId = "somecustomer" + i + ".com";  
            po.PONumber = Guid.NewGuid().ToString();  
  
            PurchaseOrderLineItem lineItem1 = new PurchaseOrderLineItem();  
            lineItem1.ProductId = "Blue Widget";  
            lineItem1.Quantity = randomGen.Next(1, 100);  
            lineItem1.UnitCost = (float)randomGen.NextDouble() * 10;  
  
            PurchaseOrderLineItem lineItem2 = new PurchaseOrderLineItem();  
            lineItem2.ProductId = "Red Widget";  
            lineItem2.Quantity = 890;  
            lineItem2.UnitCost = 45.89F;  
  
            po.orderLineItems = new PurchaseOrderLineItem[2];  
            po.orderLineItems[0] = lineItem1;  
            po.orderLineItems[1] = lineItem2;  
  
            //Create a transaction scope.  
            using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
            {  
                // Make a queued call to submit the purchase order.  
                client.SubmitPurchaseOrder(po);  
                // Complete the transaction.  
                scope.Complete();  
            }  
  
            client.Close();  
        }  
        Console.WriteLine();  
        Console.WriteLine("Press <ENTER> to terminate client.");  
        Console.ReadLine();  
    }  
}  
```

 <span data-ttu-id="d08ef-193">Po uruchomieniu próbki działania klienta i usługi są wyświetlane w oknach konsoli usługi i klienta.</span><span class="sxs-lookup"><span data-stu-id="d08ef-193">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="d08ef-194">Można wyświetlić wiadomości receive usługi z klienta.</span><span class="sxs-lookup"><span data-stu-id="d08ef-194">You can see the service receive messages from the client.</span></span> <span data-ttu-id="d08ef-195">Naciśnij klawisz ENTER w każdym okna konsoli można zamknąć usługę i klienta.</span><span class="sxs-lookup"><span data-stu-id="d08ef-195">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="d08ef-196">Należy zauważyć, że usługi kolejkowania wiadomości jest w użyciu, klient i usługa nie być uruchomiona w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="d08ef-196">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="d08ef-197">Możesz z klientem, zamknij go, a następnie uruchom usługi i nadal otrzymuje jej wiadomości.</span><span class="sxs-lookup"><span data-stu-id="d08ef-197">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span> <span data-ttu-id="d08ef-198">Widać stopniowego dane wyjściowe jako odczytana w partii i przetwarzania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="d08ef-198">You can see a rolling output as messages are read in a batch and processed.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Updated database with 2 product line items for purchase order 493ac832-d216-4e94-b2a5-d7f492fb5e39  
Processing Purchase Order: 8b567f5b-0661-4662-aae2-6cef1bd6d278  
        Customer: somecustomer849.com  
        OrderDetails  
               Order LineItem: 80 of Blue Widget @unit price: $9.751623  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41622.23  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 41130b95-4ea8-40a9-91c3-2e129117fcb8  
Processing Purchase Order: 5ce2699d-9a31-4cc2-a8c5-64cda614b3c7  
        Customer: somecustomer850.com  
        OrderDetails  
               Order LineItem: 89 of Blue Widget @unit price: $6.369128  
               Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $41408.95  
        Order status: Pending  
  
Updated database with 2 product line items for purchase order 8b567f5b-0661-4662-aae2-6cef1bd6d278  
Processing Purchase Order: ea94486b-7c86-4309-a42d-2f06c00656cd  
        Customer: somecustomer851.com  
        OrderDetails  
             Order LineItem: 47 of Blue Widget @unit price: $0.9391424  
             Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $40886.24  
        Order status: Pending  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="d08ef-199">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="d08ef-199">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d08ef-200">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="d08ef-200">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d08ef-201">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="d08ef-201">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d08ef-202">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="d08ef-202">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Batching`  
  
## <a name="see-also"></a><span data-ttu-id="d08ef-203">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d08ef-203">See Also</span></span>
