---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: f771886192e85cc7e34f0ace4fd95ca04bdb89c9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881485"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="2204c-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="2204c-102">WSStreamedHttpBinding</span></span>
<span data-ttu-id="2204c-103">W przykładzie pokazano sposób tworzenia powiązania, który jest przeznaczony do obsługi transmisji strumieniowej scenariuszy stosowania transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2204c-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2204c-104">Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="2204c-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2204c-105">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="2204c-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="2204c-106">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="2204c-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="2204c-107">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="2204c-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2204c-108">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2204c-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`  
  
 <span data-ttu-id="2204c-109">Dostępne są następujące kroki, aby utworzyć i skonfigurować nowe powiązanie standardowe.</span><span class="sxs-lookup"><span data-stu-id="2204c-109">The steps to create and configure a new standard binding are as follows.</span></span>  
  
1. <span data-ttu-id="2204c-110">Utwórz nowe powiązanie standardowe</span><span class="sxs-lookup"><span data-stu-id="2204c-110">Create a new standard binding</span></span>  
  
     <span data-ttu-id="2204c-111">Powiązania w standardowych w Windows Communication Foundation (WCF), takie jak basicHttpBinding i netTcpBinding Konfigurowanie transportów podstawowych i stosu kanału do określonych wymagań.</span><span class="sxs-lookup"><span data-stu-id="2204c-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="2204c-112">W tym przykładzie `WSStreamedHttpBinding` konfiguruje stosu kanału do obsługi przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2204c-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="2204c-113">Domyślnie WS-Security i niezawodną obsługę komunikatów nie są dodawane do stosu kanału, ponieważ obie funkcje nie są obsługiwane przez przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="2204c-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="2204c-114">Nowe powiązanie jest zaimplementowana w klasie `WSStreamedHttpBinding` który pochodzi od klasy <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="2204c-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="2204c-115">`WSStreamedHttpBinding` Zawiera następujące elementy powiązania: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2204c-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="2204c-116">Klasa oferuje `CreateBindingElements()` metodę, aby skonfigurować wynikowy stosu powiązania, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="2204c-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>  
  
    ```  
    public override BindingElementCollection CreateBindingElements()  
    {  
         // return collection of BindingElements  
         BindingElementCollection bindingElements = new BindingElementCollection();  
  
        // the order of binding elements within the collection is important: layered channels are applied in the order included, followed by  
        // the message encoder, and finally the transport at the end  
        if (flowTransactions)  
        {  
            bindingElements.Add(transactionFlow);  
        }  
        bindingElements.Add(textEncoding);  
  
        // add transport (http or https)  
        bindingElements.Add(transport);  
        return bindingElements.Clone();  
    }  
    ```  
  
2. <span data-ttu-id="2204c-117">Dodanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2204c-117">Add configuration support</span></span>  
  
     <span data-ttu-id="2204c-118">Aby uwidocznić transportu za pomocą konfiguracji próbki implementuje dwóch klas więcej —`WSStreamedHttpBindingConfigurationElement` i `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="2204c-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="2204c-119">Klasa `WSStreamedHttpBindingSection` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> który uwidacznia `WSStreamedHttpBinding` systemu konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="2204c-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="2204c-120">Duża część wykonania jest delegowane do `WSStreamedHttpBindingConfigurationElement`, która jest pochodną <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="2204c-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="2204c-121">Klasa `WSStreamedHttpBindingConfigurationElement` ma właściwości, które odnoszą się do właściwości `WSStreamedHttpBinding`i funkcje, aby mapować każdy element konfiguracji do powiązania.</span><span class="sxs-lookup"><span data-stu-id="2204c-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>  
  
     <span data-ttu-id="2204c-122">Zarejestruj program obsługi przy użyciu systemu konfiguracji, dodając następującą sekcję do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="2204c-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <extensions>  
          <bindingExtensions>  
            <add name="wsStreamedHttpBinding" type="Microsoft.ServiceModel.Samples.WSStreamedHttpBindingCollectionElement, WSStreamedHttpBinding, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
          </bindingExtensions>  
        </extensions>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="2204c-123">Program obsługi mogą następnie odwoływać się w sekcji Konfiguracja modelu serviceModel.</span><span class="sxs-lookup"><span data-stu-id="2204c-123">The handler can then be referenced from the serviceModel configuration section.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint  
                    address="https://localhost/servicemodelsamples/service.svc"  
                    bindingConfiguration="Binding"  
                    binding="wsStreamedHttpBinding"  
                    contract="Microsoft.ServiceModel.Samples.IStreamedEchoService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2204c-124">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="2204c-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="2204c-125">Instalowanie programu ASP.NET 4.0, używając następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="2204c-125">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="2204c-126">Upewnij się, że wykonano czynności opisane w [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2204c-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="2204c-127">Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="2204c-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>  
  
4. <span data-ttu-id="2204c-128">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2204c-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5. <span data-ttu-id="2204c-129">Do uruchomienia przykładu w konfiguracji między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2204c-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
6. <span data-ttu-id="2204c-130">Kiedy wyświetli się okno klienta, wpisz "Przykład.txt".</span><span class="sxs-lookup"><span data-stu-id="2204c-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="2204c-131">"Kopiuj z przykład.txt" powinien znajdować się w katalogu.</span><span class="sxs-lookup"><span data-stu-id="2204c-131">You should find a "Copy of Sample.txt" in your directory.</span></span>  
  
## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="2204c-132">Usługa WSStreamedHttpBinding próbki</span><span class="sxs-lookup"><span data-stu-id="2204c-132">The WSStreamedHttpBinding Sample Service</span></span>  
 <span data-ttu-id="2204c-133">Usługa próbki, która używa `WSStreamedHttpBinding` znajduje się w podkatalogu usługi.</span><span class="sxs-lookup"><span data-stu-id="2204c-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="2204c-134">Implementacja `OperationContract` używa `MemoryStream` można najpierw pobrać wszystkie dane w przychodzącym strumieniu przed zwróceniem `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="2204c-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="2204c-135">Próbka jest hostowana usługa Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="2204c-135">The sample service is hosted by Internet Information Services (IIS).</span></span>  
  
```  
[ServiceContract]  
public interface IStreamedEchoService  
{  
    [OperationContract]  
    Stream Echo(Stream data);  
}  
  
public class StreamedEchoService : IStreamedEchoService  
{  
    public Stream Echo(Stream data)  
    {  
        MemoryStream dataStorage = new MemoryStream();  
        byte[] byteArray = new byte[8192];  
        int bytesRead = data.Read(byteArray, 0, 8192);  
        while (bytesRead > 0)  
        {  
            dataStorage.Write(byteArray, 0, bytesRead);  
            bytesRead = data.Read(byteArray, 0, 8192);  
        }  
        data.Close();  
        dataStorage.Seek(0, SeekOrigin.Begin);  
  
        return dataStorage;  
    }  
}  
```  
  
## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="2204c-136">Klient WSStreamedHttpBinding próbki</span><span class="sxs-lookup"><span data-stu-id="2204c-136">The WSStreamedHttpBinding Sample Client</span></span>  
 <span data-ttu-id="2204c-137">Klient, który służy do interakcji z usługą przy użyciu `WSStreamedHttpBinding` znajduje się w podkatalogu klienta.</span><span class="sxs-lookup"><span data-stu-id="2204c-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="2204c-138">Ponieważ certyfikat używany w tym przykładzie jest utworzone za pomocą Makecert.exe certyfikat testowy, alert zabezpieczeń zawiera przy próbie uzyskania dostępu do adresu HTTPS w przeglądarce, takich jak https://localhost/servicemodelsamples/service.svc.</span><span class="sxs-lookup"><span data-stu-id="2204c-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="2204c-139">Aby zezwolić na klienta platformy WCF do pracy z certyfikatem testowym w miejscu, dodano dodatkowy kod klienta dla pomijania alertu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="2204c-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="2204c-140">Kod i towarzyszące klasy nie są wymagane, podczas korzystania z certyfikatów w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2204c-140">The code and the accompanying class are not required when using production certificates.</span></span>  
  
```  
// WARNING: This code is only required for test certificates such as those created by makecert. It is   
// not recommended for production code.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```  
