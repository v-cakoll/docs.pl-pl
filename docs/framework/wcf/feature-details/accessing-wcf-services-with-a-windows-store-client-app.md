---
title: Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: b4b91c103aa91e3b2c9e811c642a8347c7db1a88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185481"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="2bde7-102">Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="2bde7-103">System Windows 8 wprowadza nowy typ aplikacji o nazwie Aplikacje ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bde7-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="2bde7-104">Aplikacje te są zaprojektowane wokół interfejsu ekranu dotykowego.</span><span class="sxs-lookup"><span data-stu-id="2bde7-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="2bde7-105">Program .NET Framework 4.5 umożliwia aplikacjom ze Sklepu Windows wywoływanie usług WCF.</span><span class="sxs-lookup"><span data-stu-id="2bde7-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="2bde7-106">Obsługa WCF w aplikacjach ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="2bde7-107">Podzbiór funkcji WCF jest dostępny z poziomu aplikacji ze Sklepu Windows, zobacz poniższe sekcje, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2bde7-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bde7-108">Użyj interfejsów API syndykacji WinRT zamiast interfejsów zainteresowanych przez WCF.</span><span class="sxs-lookup"><span data-stu-id="2bde7-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="2bde7-109">Aby uzyskać więcej informacji, zobacz [WinRT Syndication API](xref:Windows.Web.Syndication)</span><span class="sxs-lookup"><span data-stu-id="2bde7-109">For more information see, [WinRT Syndication API](xref:Windows.Web.Syndication)</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2bde7-110">Dodawanie odwołania do usługi w celu dodania odwołania do usługi sieci Web do składnika środowiska wykonawczego systemu Windows nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2bde7-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="2bde7-111">Obsługiwane powiązania</span><span class="sxs-lookup"><span data-stu-id="2bde7-111">Supported Bindings</span></span>  
 <span data-ttu-id="2bde7-112">Następujące powiązania WCF są obsługiwane w aplikacjach ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="2bde7-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.BasicHttpBinding>  
  
2. <xref:System.ServiceModel.NetTcpBinding>  
  
3. <xref:System.ServiceModel.NetHttpBinding>  
  
4. <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="2bde7-113">Następujące elementy wiązania są obsługiwane w aplikacjach ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2. <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3. <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4. <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5. <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6. <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7. <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="2bde7-114">Obsługiwane są kodowania tekstowe i binarne.</span><span class="sxs-lookup"><span data-stu-id="2bde7-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="2bde7-115">Obsługiwane są wszystkie tryby transferu WCF.</span><span class="sxs-lookup"><span data-stu-id="2bde7-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="2bde7-116">Aby uzyskać więcej informacji, zobacz [Przesyłanie strumieniowe wiadomości](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="2bde7-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="2bde7-117">Dodaj dokumentację usługi</span><span class="sxs-lookup"><span data-stu-id="2bde7-117">Add Service Reference</span></span>  
 <span data-ttu-id="2bde7-118">Aby wywołać usługę WCF z aplikacji ze Sklepu Windows, należy użyć funkcji Dodaj odwołanie do usługi programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="2bde7-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="2bde7-119">Można zauważyć kilka zmian w funkcjonalności Dodaj odwołanie do usługi, gdy odbywa się w aplikacji ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="2bde7-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="2bde7-120">Najpierw nie jest generowany żaden plik konfiguracyjny.</span><span class="sxs-lookup"><span data-stu-id="2bde7-120">First no configuration file is generated.</span></span> <span data-ttu-id="2bde7-121">Aplikacje ze Sklepu Windows nie używają plików konfiguracyjnych, więc muszą być skonfigurowane w kodzie.</span><span class="sxs-lookup"><span data-stu-id="2bde7-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="2bde7-122">Ten kod konfiguracji można znaleźć w pliku References.cs wygenerowanym przez dodaj odwołanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="2bde7-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="2bde7-123">Aby wyświetlić ten plik, upewnij się, że w Eksploratorze rozwiązań wybierz opcję "Pokaż wszystkie pliki".</span><span class="sxs-lookup"><span data-stu-id="2bde7-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="2bde7-124">Plik będzie znajdować się w obszarze Odwołania do usługi, a następnie węzły Reference.svcmap w ramach projektu.</span><span class="sxs-lookup"><span data-stu-id="2bde7-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="2bde7-125">Wszystkie operacje generowane dla usług WCF w aplikacji Ze Sklepu Windows będą asynchroniczne przy użyciu wzorca asynchronicznego opartego na zadaniach.</span><span class="sxs-lookup"><span data-stu-id="2bde7-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="2bde7-126">Aby uzyskać więcej informacji, zobacz [Zadania asynchroniczne — upraszczanie programowania asynchroniczne z zadaniami](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span><span class="sxs-lookup"><span data-stu-id="2bde7-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://docs.microsoft.com/archive/msdn-magazine/2010/september/async-tasks-simplify-asynchronous-programming-with-tasks).</span></span>  
  
 <span data-ttu-id="2bde7-127">Ponieważ konfiguracja jest teraz generowana w kodzie, wszelkie zmiany wprowadzone w pliku Reference.cs zostaną zastąpione za każdym razem, gdy odwołanie do usługi jest aktualizowane.</span><span class="sxs-lookup"><span data-stu-id="2bde7-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="2bde7-128">Aby zaradzić tej sytuacji kod konfiguracji jest generowany w ramach metody częściowej, które można zaimplementować w klasie serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="2bde7-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="2bde7-129">Metoda częściowa jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2bde7-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="2bde7-130">Następnie można zaimplementować tę metodę częściową i zmienić powiązanie lub punkt końcowy w klasie serwera proxy klienta w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2bde7-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
```csharp  
public partial class Service1Client : System.ServiceModel.ClientBase<MetroWcfClient.ServiceRefMultiEndpt.IService1>, MetroWcfClient.ServiceRefMultiEndpt.IService1  
    {
        static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,
            System.ServiceModel.Description.ClientCredentials clientCredentials)  
        {  
            if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.BasicHttpBinding_IService11.ToString())  
            {  
                serviceEndpoint.Binding.SendTimeout = new System.TimeSpan(0, 1, 0);  
                clientCredentials.UserName.UserName = "username1";  
                clientCredentials.UserName.Password = "password";  
            }  
            else if (serviceEndpoint.Name ==
                    ServiceRefMultiEndpt.Service1Client.EndpointConfiguration.NetTcpBinding_IService1.ToString())  
            {  
                serviceEndpoint.Binding.Name = "MyTcpBinding";  
                serviceEndpoint.Address = new System.ServiceModel.EndpointAddress("net.tcp://localhost/tcp");  
            }  
        }  
    }  
```  
  
### <a name="serialization"></a><span data-ttu-id="2bde7-131">Serializacja</span><span class="sxs-lookup"><span data-stu-id="2bde7-131">Serialization</span></span>  
 <span data-ttu-id="2bde7-132">W aplikacjach ze Sklepu Windows obsługiwane są następujące serializatory:</span><span class="sxs-lookup"><span data-stu-id="2bde7-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1. <span data-ttu-id="2bde7-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="2bde7-133">DataContractSerializer</span></span>  
  
2. <span data-ttu-id="2bde7-134">Datacontractjsonserializer</span><span class="sxs-lookup"><span data-stu-id="2bde7-134">DataContractJsonSerializer</span></span>  
  
3. <span data-ttu-id="2bde7-135">Xmlserializer</span><span class="sxs-lookup"><span data-stu-id="2bde7-135">XmlSerializer</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2bde7-136">XmlDictionaryWriter.Write(DateTime) teraz zapisuje DateTime obiektu jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="2bde7-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="2bde7-137">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="2bde7-137">Security</span></span>  

<span data-ttu-id="2bde7-138">W aplikacjach ze Sklepu Windows są obsługiwane następujące tryby zabezpieczeń:</span><span class="sxs-lookup"><span data-stu-id="2bde7-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="2bde7-139">Następujące typy poświadczeń klienta są obsługiwane w aplikacjach ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="2bde7-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1. <span data-ttu-id="2bde7-140">Brak</span><span class="sxs-lookup"><span data-stu-id="2bde7-140">None</span></span>  
  
2. <span data-ttu-id="2bde7-141">Podstawowa (Basic)</span><span class="sxs-lookup"><span data-stu-id="2bde7-141">Basic</span></span>  
  
3. <span data-ttu-id="2bde7-142">Szyfrowane</span><span class="sxs-lookup"><span data-stu-id="2bde7-142">Digest</span></span>  
  
4. <span data-ttu-id="2bde7-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="2bde7-143">Negotiate</span></span>  
  
5. <span data-ttu-id="2bde7-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="2bde7-144">NTLM</span></span>  
  
6. <span data-ttu-id="2bde7-145">Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-145">Windows</span></span>  
  
7. <span data-ttu-id="2bde7-146">Nazwa użytkownika (zabezpieczenia wiadomości)</span><span class="sxs-lookup"><span data-stu-id="2bde7-146">Username (Message Security)</span></span>  
  
8. <span data-ttu-id="2bde7-147">Windows (zabezpieczenia transportu)</span><span class="sxs-lookup"><span data-stu-id="2bde7-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="2bde7-148">Aby aplikacje ze Sklepu Windows uzyskiwano dostęp do domyślnych poświadczeń systemu Windows i wysyłać je, należy włączyć tę funkcję w pliku Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="2bde7-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="2bde7-149">Otwórz ten plik i wybierz kartę Możliwości i wybierz "Domyślne poświadczenia systemu Windows".</span><span class="sxs-lookup"><span data-stu-id="2bde7-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="2bde7-150">Dzięki temu aplikacja może łączyć się z zasobami intranetowymi, które wymagają poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="2bde7-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2bde7-151">Aby aplikacje ze Sklepu Windows do wykonywania połączeń między komputerami należy włączyć inną funkcję o nazwie "Home/Work Networking".</span><span class="sxs-lookup"><span data-stu-id="2bde7-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="2bde7-152">To ustawienie znajduje się również w pliku Package.appmanifest na karcie Możliwości.</span><span class="sxs-lookup"><span data-stu-id="2bde7-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="2bde7-153">Dzięki temu aplikacja przychodzące i wychodzące dostęp do sieci zaufanych miejsc użytkownika, takich jak dom i praca.</span><span class="sxs-lookup"><span data-stu-id="2bde7-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="2bde7-154">Przychodzące porty krytyczne są zawsze blokowane.</span><span class="sxs-lookup"><span data-stu-id="2bde7-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="2bde7-155">Aby uzyskać dostęp do usług w Internecie, należy również włączyć możliwość korzystania z Internetu (klienta).</span><span class="sxs-lookup"><span data-stu-id="2bde7-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="2bde7-156">Różne</span><span class="sxs-lookup"><span data-stu-id="2bde7-156">Misc</span></span>  
 <span data-ttu-id="2bde7-157">Korzystanie z następujących klas jest obsługiwane dla aplikacji ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="2bde7-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1. <xref:System.ServiceModel.ChannelFactory>  
  
2. <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3. <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="2bde7-158">Definiowanie umów serwisowych</span><span class="sxs-lookup"><span data-stu-id="2bde7-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="2bde7-159">Zaleca się definiowanie tylko operacji asynchronicznych usługi przy użyciu wzorca asynchroniczne oparte na zadaniach.</span><span class="sxs-lookup"><span data-stu-id="2bde7-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="2bde7-160">Dzięki temu aplikacje ze Sklepu Windows pozostają responsywne podczas wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="2bde7-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="2bde7-161">Chociaż nie wyjątek zostanie zgłoszony, jeśli zdefiniujesz operację synchroniową, zdecydowanie zaleca się definiowanie tylko operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="2bde7-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="2bde7-162">Wywoływanie usług WCF z aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="2bde7-163">Jak wspomniano wcześniej wszystkie konfiguracje muszą być wykonane w kodzie w GetBindingForEndpoint metody w klasie wygenerowanego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2bde7-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="2bde7-164">Wywołanie operacji usługi odbywa się tak samo jak wywołanie dowolnej metody asynchronicznego opartej na zadaniach, jak pokazano w poniższym urywek kodu.</span><span class="sxs-lookup"><span data-stu-id="2bde7-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
```csharp  
void async SomeMethod()  
{  
    ServiceClient proxy = new ServiceClient();  
    Task<T> results = await proxy.CallAsync(param1, param2);  
    T result = results.Result;  
    if (result.Success)  
    {  
       // Do something with result  
    }  
}  
```  
  
 <span data-ttu-id="2bde7-165">Zwróć uwagę na użycie asynchroniczne słowo kluczowe na metodę podejmowania wywołania asynchroniczne i await słowa kluczowego podczas wywoływania metody asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="2bde7-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bde7-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bde7-166">See also</span></span>

- [<span data-ttu-id="2bde7-167">WCF w blogu aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-167">WCF in Windows Store Apps Blog</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/wcf-in-windows-8-metro-styled-apps-absolutely-supported)
- [<span data-ttu-id="2bde7-168">Klienci i zabezpieczenia sklepu Windows WCF</span><span class="sxs-lookup"><span data-stu-id="2bde7-168">WCF Windows Store Clients and Security</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-adding-security)
- [<span data-ttu-id="2bde7-169">Aplikacje ze Sklepu Windows i połączenia między komputerami</span><span class="sxs-lookup"><span data-stu-id="2bde7-169">Windows Store Apps and Cross Machine Calls</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="2bde7-170">Wywoływanie usługi WCF wdrożonej na platformie Azure z aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="2bde7-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://docs.microsoft.com/archive/blogs/piyushjo/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario)
- [<span data-ttu-id="2bde7-171">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="2bde7-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="2bde7-172">Powiązania</span><span class="sxs-lookup"><span data-stu-id="2bde7-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
