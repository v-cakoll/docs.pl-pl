---
title: "Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: df5e05b1896ee272e286102a6c9433fad51b3c98
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="3c110-102">Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="3c110-103">Windows 8 wprowadzono nowy typ aplikacji o nazwie aplikacje ze Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="3c110-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="3c110-104">Te aplikacje są została zaprojektowana interfejsu ekran dotykowy.</span><span class="sxs-lookup"><span data-stu-id="3c110-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="3c110-105">.NET framework 4.5 umożliwia aplikacji ze Sklepu Windows do wywoływania usług WCF.</span><span class="sxs-lookup"><span data-stu-id="3c110-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="3c110-106">Obsługa usługi WCF w aplikacjach Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="3c110-107">Podzbiór funkcji WCF są dostępne za pośrednictwem aplikacji Sklepu Windows, zobacz następujące sekcje, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="3c110-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c110-108">Użyj zespolonego WinRT interfejsów API, zamiast te udostępniane przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3c110-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="3c110-109">Aby uzyskać więcej informacji, zobacz [API zespolonego WinRT](http://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="3c110-109">For more information see, [WinRT Syndication API](http://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3c110-110">Dodawanie odwołania do usługi sieci web do składnika środowiska wykonawczego systemu Windows przy użyciu Dodaj odwołanie do usługi nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="3c110-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="3c110-111">Obsługiwane powiązania</span><span class="sxs-lookup"><span data-stu-id="3c110-111">Supported Bindings</span></span>  
 <span data-ttu-id="3c110-112">W aplikacji ze Sklepu Windows są obsługiwane następujące powiązania WCF:</span><span class="sxs-lookup"><span data-stu-id="3c110-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="3c110-113">Obsługiwane są następujące elementy powiązania w aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="3c110-114">Obsługiwane są kodowania binarnego i tekstu.</span><span class="sxs-lookup"><span data-stu-id="3c110-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="3c110-115">Obsługiwane są wszystkie tryby transferu WCF.</span><span class="sxs-lookup"><span data-stu-id="3c110-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="3c110-116">Aby uzyskać więcej informacji, zobacz [przesyłania strumieniowego transferu wiadomości](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="3c110-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="3c110-117">Dodaj odwołanie do usługi</span><span class="sxs-lookup"><span data-stu-id="3c110-117">Add Service Reference</span></span>  
 <span data-ttu-id="3c110-118">Wywoływanie usługi WCF z aplikacją ze Sklepu Windows, użyj funkcji Dodaj odwołanie do usługi Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3c110-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="3c110-119">Można zauważyć drobne zmiany w funkcji Dodaj odwołanie do usługi po zakończeniu aplikacji Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="3c110-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="3c110-120">Najpierw plik konfiguracji nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="3c110-120">First no configuration file is generated.</span></span> <span data-ttu-id="3c110-121">Aplikacje ze Sklepu Windows nie należy używać pliki konfiguracji, dlatego musi być skonfigurowany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3c110-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="3c110-122">Ten kod konfiguracji można znaleźć w pliku References.cs generowane przez Dodaj odwołanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="3c110-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="3c110-123">Aby wyświetlić ten plik, upewnij się, że w Eksploratorze rozwiązań wybierz opcję "Pokaż wszystkie pliki".</span><span class="sxs-lookup"><span data-stu-id="3c110-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="3c110-124">Plik zostanie umieszczony w odwołania do usług, a następnie Reference.svcmap węzłów w projekcie.</span><span class="sxs-lookup"><span data-stu-id="3c110-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="3c110-125">Wszystkie operacje wygenerowany dla usług WCF w ramach aplikacji Sklepu Windows będzie za pomocą wzorca asynchronicznego opartego na zadaniach asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="3c110-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="3c110-126">Aby uzyskać więcej informacji, zobacz [wzorca asynchronicznego opartego na zadaniach](http://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="3c110-126">For more information, see [Task-based Asynchronous Pattern](http://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="3c110-127">Ponieważ konfiguracji jest teraz generowany w kodzie, wszystkie zmiany wprowadzone w pliku Reference.cs byłyby zastępowane każdej aktualizacji odwołania do usługi.</span><span class="sxs-lookup"><span data-stu-id="3c110-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="3c110-128">Aby rozwiązać ten problem kodu konfiguracji zostanie wygenerowany wewnątrz metody częściowej, które można zaimplementować klasy serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="3c110-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="3c110-129">Metoda częściowa jest zadeklarowany w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3c110-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="3c110-130">Następnie można zaimplementować tę metodę częściowe i Zmień powiązanie lub punkt końcowy w klasie klienta serwera proxy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3c110-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="3c110-131">Serializacja</span><span class="sxs-lookup"><span data-stu-id="3c110-131">Serialization</span></span>  
 <span data-ttu-id="3c110-132">Następujące serializatorów są obsługiwane w aplikacjach Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="3c110-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="3c110-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="3c110-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="3c110-134">Klasa DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="3c110-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="3c110-135">Element XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="3c110-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3c110-136">XmlDictionaryWriter.Write(DateTime) teraz zapisuje obiekt DateTime jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="3c110-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="3c110-137">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="3c110-137">Security</span></span>  
 <span data-ttu-id="3c110-138">Następujące tryby zabezpieczeń są obsługiwane w aplikacjach Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-138">The following security modes are supported in Windows Store applications</span></span>  
  
1.  <xref:System.ServiceModel.SecurityMode.None>  
  
2.  <xref:System.ServiceModel.SecurityMode.Transport>  
  
3.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredentials> --> `System.ServiceModel.SecurityMode.TransportWithMessageCredentials`
  
4.  <!--zz <xref:System.ServiceModel.SecurityMode.TransportCredentialOnly>  --> `System.ServiceModel.SecurityMode.TransportCredentialOnly`
  
 <span data-ttu-id="3c110-139">Następujących typów poświadczeń klienta są obsługiwane w aplikacjach Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-139">The following client credential types are supported in Windows Store applications</span></span>  
  
1.  <span data-ttu-id="3c110-140">Brak</span><span class="sxs-lookup"><span data-stu-id="3c110-140">None</span></span>  
  
2.  <span data-ttu-id="3c110-141">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="3c110-141">Basic</span></span>  
  
3.  <span data-ttu-id="3c110-142">Skrót</span><span class="sxs-lookup"><span data-stu-id="3c110-142">Digest</span></span>  
  
4.  <span data-ttu-id="3c110-143">Negocjowania</span><span class="sxs-lookup"><span data-stu-id="3c110-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="3c110-144">UWIERZYTELNIANIE NTLM</span><span class="sxs-lookup"><span data-stu-id="3c110-144">NTLM</span></span>  
  
6.  <span data-ttu-id="3c110-145">Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-145">Windows</span></span>  
  
7.  <span data-ttu-id="3c110-146">Nazwa użytkownika (zabezpieczenia komunikatów)</span><span class="sxs-lookup"><span data-stu-id="3c110-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="3c110-147">Systemu Windows (TLS)</span><span class="sxs-lookup"><span data-stu-id="3c110-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="3c110-148">Aby aplikacje ze Sklepu Windows do uzyskania dostępu i wysyłać domyślne poświadczenia systemu Windows należy włączyć tę funkcję w pliku Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="3c110-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="3c110-149">Otwórz ten plik i wybierz kartę możliwości i wybierz opcję "Domyślne poświadczenia systemu Windows".</span><span class="sxs-lookup"><span data-stu-id="3c110-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="3c110-150">Umożliwia to aplikacji nawiązać połączenie zasobów intranetowych, które wymagają podania poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="3c110-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3c110-151">Aby aplikacje ze Sklepu Windows do połączeń między maszyny należy włączyć kolejna możliwość o nazwie "Sieć główną/pracy".</span><span class="sxs-lookup"><span data-stu-id="3c110-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="3c110-152">To ustawienie jest również plik Package.appmanifest na karcie możliwości. Zaznacz pole wyboru sieć główną/pracy.</span><span class="sxs-lookup"><span data-stu-id="3c110-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="3c110-153">Dzięki temu aplikacja, którą przychodzący i wychodzący dostęp do sieci użytkownika, jego zaufanych miejsc, takich jak domu lub pracy.</span><span class="sxs-lookup"><span data-stu-id="3c110-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="3c110-154">Krytyczne portów przychodzących są zawsze blokowany.</span><span class="sxs-lookup"><span data-stu-id="3c110-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="3c110-155">Uzyskiwanie dostępu do usług w Internecie, należy również włączyć możliwości Internet (klient).</span><span class="sxs-lookup"><span data-stu-id="3c110-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="3c110-156">Różne</span><span class="sxs-lookup"><span data-stu-id="3c110-156">Misc</span></span>  
 <span data-ttu-id="3c110-157">Korzystanie z następujących klas nie jest obsługiwane dla aplikacji ze Sklepu Windows:</span><span class="sxs-lookup"><span data-stu-id="3c110-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <!--zz <xref:System.ServiceModel.DuplexChannelFactory> --> `System.ServiceModel.DuplexChannelFactory`
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="3c110-158">Definiowanie kontraktów usługi</span><span class="sxs-lookup"><span data-stu-id="3c110-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="3c110-159">Zaleca się definiowania tylko operacje asynchroniczne usługi za pomocą wzorca asynchronicznego opartego na zadaniach.</span><span class="sxs-lookup"><span data-stu-id="3c110-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="3c110-160">Dzięki temu aplikacje ze Sklepu Windows pozostają odpowiadać podczas wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="3c110-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3c110-161">Gdy nie zostanie wygenerowany wyjątek w przypadku definiowania Operacja synchroniczna, zdecydowanie zaleca się definiować tylko operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="3c110-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="3c110-162">Wywoływanie usług WCF z aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="3c110-163">Jak wspomniano wcześniej cała konfiguracja musi odbywać się w kod w metodzie GetBindingForEndpoint w klasie wygenerowany serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="3c110-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="3c110-164">Wywoływanie operacji usługi odbywa się taka sama jak pokazane na poniższy fragment kodu podczas wywoływania metody asynchronicznej żadnych zadań.</span><span class="sxs-lookup"><span data-stu-id="3c110-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="3c110-165">Zwróć uwagę na async — słowo kluczowe na metodę wprowadzania wywołanie asynchroniczne i słowo kluczowe await podczas wywoływania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="3c110-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c110-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3c110-166">See Also</span></span>  
 [<span data-ttu-id="3c110-167">Usługi WCF w blogu aplikacje Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-167">WCF in Windows Store Apps Blog</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)  
 [<span data-ttu-id="3c110-168">Klienci WCF Sklepu Windows i zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="3c110-168">WCF Windows Store Clients and Security</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)  
 [<span data-ttu-id="3c110-169">Aplikacje ze Sklepu Windows i połączeń między maszyny</span><span class="sxs-lookup"><span data-stu-id="3c110-169">Windows Store Apps and Cross Machine Calls</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="3c110-170">Wywołanie usługi WCF wdrożona na platformie Azure z aplikacji ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="3c110-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](http://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)  
 [<span data-ttu-id="3c110-171">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="3c110-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)  
 [<span data-ttu-id="3c110-172">Powiązania</span><span class="sxs-lookup"><span data-stu-id="3c110-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
