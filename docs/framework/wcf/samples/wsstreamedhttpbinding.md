---
title: WSStreamedHttpBinding
ms.date: 03/30/2017
ms.assetid: 97ce4d3d-ca6f-45fa-b33b-2429bb84e65b
ms.openlocfilehash: 36b4db5270205aec55ad52db40500c8d434a1560
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714549"
---
# <a name="wsstreamedhttpbinding"></a><span data-ttu-id="27909-102">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="27909-102">WSStreamedHttpBinding</span></span>

<span data-ttu-id="27909-103">W przykładzie pokazano, jak utworzyć powiązanie, które jest przeznaczone do obsługi scenariuszy przesyłania strumieniowego, gdy używany jest transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="27909-103">The sample demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>

> [!NOTE]
> <span data-ttu-id="27909-104">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="27909-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27909-105">Przykłady mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="27909-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27909-106">Przed kontynuowaniem Wyszukaj następujący katalog (domyślny).</span><span class="sxs-lookup"><span data-stu-id="27909-106">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="27909-107">Jeśli ten katalog nie istnieje, przejdź do [przykładów Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) dla .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) , aby pobrać wszystkie próbki Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="27909-107">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27909-108">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="27909-108">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Binding\WSStreamedHttpBinding`

 <span data-ttu-id="27909-109">Poniżej przedstawiono procedurę tworzenia i konfigurowania nowego powiązania standardowego.</span><span class="sxs-lookup"><span data-stu-id="27909-109">The steps to create and configure a new standard binding are as follows.</span></span>

1. <span data-ttu-id="27909-110">Tworzenie nowego powiązania standardowego</span><span class="sxs-lookup"><span data-stu-id="27909-110">Create a new standard binding</span></span>

    <span data-ttu-id="27909-111">Standardowe powiązania w Windows Communication Foundation (WCF), takie jak basicHttpBinding i netTcpBinding, konfigurują podstawowe transporty i stos kanałów dla określonych wymagań.</span><span class="sxs-lookup"><span data-stu-id="27909-111">The standard bindings in Windows Communication Foundation (WCF) such as basicHttpBinding, and netTcpBinding configure the underlying transports and channel stack for specific requirements.</span></span> <span data-ttu-id="27909-112">W tym przykładzie `WSStreamedHttpBinding` konfiguruje stos kanałów do obsługi przesyłania strumieniowego.</span><span class="sxs-lookup"><span data-stu-id="27909-112">In this sample, `WSStreamedHttpBinding` configures the channel stack to support streaming.</span></span> <span data-ttu-id="27909-113">Domyślnie usługa WS-Security i niezawodna obsługa komunikatów nie są dodawane do stosu kanałów, ponieważ obie funkcje nie są obsługiwane przez przesyłanie strumieniowe.</span><span class="sxs-lookup"><span data-stu-id="27909-113">By default, WS-Security and reliable messaging are not added to the channel stack because both features are not supported by streaming.</span></span> <span data-ttu-id="27909-114">Nowe powiązanie jest zaimplementowane w klasie `WSStreamedHttpBinding`, która pochodzi od <xref:System.ServiceModel.Channels.Binding>.</span><span class="sxs-lookup"><span data-stu-id="27909-114">The new binding is implemented in the class `WSStreamedHttpBinding` that derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="27909-115">`WSStreamedHttpBinding` zawiera następujące elementy powiązania: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>i <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="27909-115">The `WSStreamedHttpBinding` contains the following binding elements: <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>, <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, and <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span> <span data-ttu-id="27909-116">Klasa udostępnia metodę `CreateBindingElements()`, aby skonfigurować wynikowy stos powiązań, jak pokazano w poniższym przykładowym kodzie.</span><span class="sxs-lookup"><span data-stu-id="27909-116">The class provides a `CreateBindingElements()` method to configure the resulting binding stack, as shown in the following sample code.</span></span>

    ```csharp
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

2. <span data-ttu-id="27909-117">Dodawanie obsługi konfiguracji</span><span class="sxs-lookup"><span data-stu-id="27909-117">Add configuration support</span></span>

    <span data-ttu-id="27909-118">Aby uwidocznić transport poprzez konfigurację, przykład implementuje dwie więcej klas —`WSStreamedHttpBindingConfigurationElement` i `WSStreamedHttpBindingSection`.</span><span class="sxs-lookup"><span data-stu-id="27909-118">To expose the transport through configuration the sample implements two more classes—`WSStreamedHttpBindingConfigurationElement` and `WSStreamedHttpBindingSection`.</span></span> <span data-ttu-id="27909-119">Klasa `WSStreamedHttpBindingSection` jest <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602>, który uwidacznia `WSStreamedHttpBinding` do systemu konfiguracji WCF.</span><span class="sxs-lookup"><span data-stu-id="27909-119">The class `WSStreamedHttpBindingSection` is a <xref:System.ServiceModel.Configuration.StandardBindingCollectionElement%602> that exposes `WSStreamedHttpBinding` to the WCF configuration system.</span></span> <span data-ttu-id="27909-120">Zbiorcza implementacja jest delegowana do `WSStreamedHttpBindingConfigurationElement`, który pochodzi z <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="27909-120">The bulk of the implementation is delegated to `WSStreamedHttpBindingConfigurationElement`, which derives from <xref:System.ServiceModel.Configuration.StandardBindingElement>.</span></span> <span data-ttu-id="27909-121">Klasa `WSStreamedHttpBindingConfigurationElement` ma właściwości, które odpowiadają właściwościom `WSStreamedHttpBinding`i funkcje do mapowania każdego elementu konfiguracji do powiązania.</span><span class="sxs-lookup"><span data-stu-id="27909-121">The class `WSStreamedHttpBindingConfigurationElement` has properties that correspond to the properties of `WSStreamedHttpBinding`, and functions to map each configuration element to a binding.</span></span>

    <span data-ttu-id="27909-122">Zarejestruj program obsługi przy użyciu systemu konfiguracji, dodając następującą sekcję do pliku konfiguracji usługi.</span><span class="sxs-lookup"><span data-stu-id="27909-122">Register the handler with the configuration system, by adding the following section to the service's configuration file.</span></span>

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

    <span data-ttu-id="27909-123">Do programu obsługi można odwoływać się z sekcji konfiguracji serviceModel.</span><span class="sxs-lookup"><span data-stu-id="27909-123">The handler can then be referenced from the serviceModel configuration section.</span></span>

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

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="27909-124">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="27909-124">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="27909-125">Zainstaluj ASP.NET 4,0 przy użyciu następującego polecenia.</span><span class="sxs-lookup"><span data-stu-id="27909-125">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="27909-126">Upewnij się, że wykonano kroki opisane w [temacie Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27909-126">Ensure that you have performed the steps listed in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="27909-127">Upewnij się, że wykonano [instrukcje instalacji certyfikatu serwera Internet Information Services (IIS)](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span><span class="sxs-lookup"><span data-stu-id="27909-127">Ensure that you have performed the [Internet Information Services (IIS) Server Certificate Installation Instructions](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md).</span></span>

4. <span data-ttu-id="27909-128">Aby skompilować rozwiązanie, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27909-128">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="27909-129">Aby uruchomić przykład w konfiguracji między maszynami, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="27909-129">To run the sample in a cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

6. <span data-ttu-id="27909-130">Po wyświetleniu okna klienta wpisz "Sample. txt".</span><span class="sxs-lookup"><span data-stu-id="27909-130">When the client window displays, type "Sample.txt".</span></span> <span data-ttu-id="27909-131">W katalogu powinna znajdować się "kopia przykładowa. txt".</span><span class="sxs-lookup"><span data-stu-id="27909-131">You should find a "Copy of Sample.txt" in your directory.</span></span>

## <a name="the-wsstreamedhttpbinding-sample-service"></a><span data-ttu-id="27909-132">Przykładowa usługa WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="27909-132">The WSStreamedHttpBinding Sample Service</span></span>

<span data-ttu-id="27909-133">Przykładowa usługa, która używa `WSStreamedHttpBinding`, znajduje się w podkatalogu usługi.</span><span class="sxs-lookup"><span data-stu-id="27909-133">The sample service that uses `WSStreamedHttpBinding` is located in the service subdirectory.</span></span> <span data-ttu-id="27909-134">Implementacja `OperationContract` używa `MemoryStream`, aby najpierw pobrać wszystkie dane ze strumienia przychodzącego przed zwróceniem `MemoryStream`.</span><span class="sxs-lookup"><span data-stu-id="27909-134">The implementation of `OperationContract` uses a `MemoryStream` to first retrieve all data from the incoming stream before returning the `MemoryStream`.</span></span> <span data-ttu-id="27909-135">Przykładowa usługa jest hostowana przez Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="27909-135">The sample service is hosted by Internet Information Services (IIS).</span></span>

```csharp
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

## <a name="the-wsstreamedhttpbinding-sample-client"></a><span data-ttu-id="27909-136">Przykładowy klient WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="27909-136">The WSStreamedHttpBinding Sample Client</span></span>

<span data-ttu-id="27909-137">Klient, który jest używany do współdziałania z usługą za pomocą `WSStreamedHttpBinding`, znajduje się w podkatalogu klienta.</span><span class="sxs-lookup"><span data-stu-id="27909-137">The client that is used to interact with the service using `WSStreamedHttpBinding` is located in the client subdirectory.</span></span> <span data-ttu-id="27909-138">Ponieważ certyfikat używany w tym przykładzie jest certyfikatem testowym utworzonym przy użyciu programu Makecert. exe, podczas próby uzyskania dostępu do adresu HTTPS w przeglądarce, takiego jak https://localhost/servicemodelsamples/service.svc, zostanie wyświetlony alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="27909-138">Because the certificate used in this sample is a test certificate created with Makecert.exe, a security alert displays when you attempt to access an HTTPS address in your browser such as https://localhost/servicemodelsamples/service.svc.</span></span> <span data-ttu-id="27909-139">Aby umożliwić klientowi WCF współpracuję z certyfikatem testowym, do klienta został dodany dodatkowy kod, aby pominąć alert zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="27909-139">To allow the WCF client to work with a test certificate in place, some additional code has been added to the client to suppress the security alert.</span></span> <span data-ttu-id="27909-140">Kod i towarzysząca Klasa nie są wymagane w przypadku korzystania z certyfikatów produkcyjnych.</span><span class="sxs-lookup"><span data-stu-id="27909-140">The code and the accompanying class are not required when using production certificates.</span></span>

```csharp
// WARNING: This code is only required for test certificates such as those created by makecert. It is
// not recommended for production code.
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");
```
