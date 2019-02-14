---
title: Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows
ms.date: 03/30/2017
ms.assetid: e2002ef4-5dee-4a54-9d87-03b33d35fc52
ms.openlocfilehash: 484fad33614ca2b9507ed88aadfc1a41bb216c28
ms.sourcegitcommit: af0a22a4eb11bbcd33baec49150d551955b50a16
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2019
ms.locfileid: "56261118"
---
# <a name="accessing-wcf-services-with-a-windows-store-client-app"></a><span data-ttu-id="65b81-102">Dostęp do usług WCF za pomocą aplikacji klienckiej ze Sklepu Windows</span><span class="sxs-lookup"><span data-stu-id="65b81-102">Accessing WCF Services with a Windows Store Client App</span></span>
<span data-ttu-id="65b81-103">Windows 8 wprowadzono nowy typ aplikacji o nazwie aplikacje Windows Store.</span><span class="sxs-lookup"><span data-stu-id="65b81-103">Windows 8 introduces a new type of application called Windows Store applications.</span></span> <span data-ttu-id="65b81-104">Te aplikacje są projektowane na podstawie interfejsem ekranie dotykowym.</span><span class="sxs-lookup"><span data-stu-id="65b81-104">These applications are designed around a touch screen interface.</span></span> <span data-ttu-id="65b81-105">.NET framework 4.5 umożliwia aplikacji Windows Store do wywołania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="65b81-105">.NET Framework 4.5 enables Windows Store applications to call WCF services.</span></span>  
  
## <a name="wcf-support-in-windows-store-applications"></a><span data-ttu-id="65b81-106">Obsługa usług WCF w aplikacjach Windows Store</span><span class="sxs-lookup"><span data-stu-id="65b81-106">WCF Support in Windows Store Applications</span></span>  
 <span data-ttu-id="65b81-107">Podzbiór funkcji WCF jest dostępne z poziomu aplikacji Windows Store, zobacz poniższe sekcje, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="65b81-107">A subset of WCF functionality is available from within a Windows Store application, see the following sections for more details.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65b81-108">Użyj syndykacji WinRT API zamiast te udostępniane przez usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="65b81-108">Use the WinRT syndication APIs instead of those exposed by WCF.</span></span> <span data-ttu-id="65b81-109">Aby uzyskać więcej informacji, zobacz [API syndykacji WinRT](https://go.microsoft.com/fwlink/?LinkId=236265)</span><span class="sxs-lookup"><span data-stu-id="65b81-109">For more information see, [WinRT Syndication API](https://go.microsoft.com/fwlink/?LinkId=236265)</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="65b81-110">Aby dodać odwołanie do składnika środowiska wykonawczego Windows usługi sieci web przy użyciu Dodaj odwołanie do usługi nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="65b81-110">Using Add Service Reference to add a web service reference to a Windows Runtime Component isn’t supported.</span></span>  
  
### <a name="supported-bindings"></a><span data-ttu-id="65b81-111">Obsługiwane powiązania</span><span class="sxs-lookup"><span data-stu-id="65b81-111">Supported Bindings</span></span>  
 <span data-ttu-id="65b81-112">Następujące powiązaniami WCF są obsługiwane w Windows Store aplikacji:</span><span class="sxs-lookup"><span data-stu-id="65b81-112">The following WCF bindings are supported in Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.BasicHttpBinding>  
  
2.  <xref:System.ServiceModel.NetTcpBinding>  
  
3.  <xref:System.ServiceModel.NetHttpBinding>  
  
4.  <xref:System.ServiceModel.Channels.CustomBinding>
  
 <span data-ttu-id="65b81-113">Następujące elementy powiązania są obsługiwane w programie Windows Store aplikacji</span><span class="sxs-lookup"><span data-stu-id="65b81-113">The following binding elements are supported in Windows Store Applications</span></span>  
  
1.  <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
2.  <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
3.  <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
4.  <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
5.  <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
6.  <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
7.  <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
8.  <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
9. <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="65b81-114">Obsługiwane są zarówno tekstowych i binarnych kodowania.</span><span class="sxs-lookup"><span data-stu-id="65b81-114">Both Text and Binary encodings are supported.</span></span> <span data-ttu-id="65b81-115">Obsługiwane są wszystkie tryby transferu WCF.</span><span class="sxs-lookup"><span data-stu-id="65b81-115">All WCF transfer modes are supported.</span></span> <span data-ttu-id="65b81-116">Aby uzyskać więcej informacji, zobacz [przesyłanie strumieniowe przesyłanie komunikatów](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span><span class="sxs-lookup"><span data-stu-id="65b81-116">For more information see, [Streaming Message Transfer](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md).</span></span>  
  
### <a name="add-service-reference"></a><span data-ttu-id="65b81-117">Dodaj odwołanie do usługi</span><span class="sxs-lookup"><span data-stu-id="65b81-117">Add Service Reference</span></span>  
 <span data-ttu-id="65b81-118">Aby wywołać usługi WCF z aplikacji Windows Store, użyj funkcji Dodaj odwołanie do usługi Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="65b81-118">To call a WCF service from a Windows Store application, use the Add Service Reference feature of Visual Studio 2012.</span></span> <span data-ttu-id="65b81-119">Zauważysz kilka zmian w funkcji Dodaj odwołanie do usługi po zakończeniu w aplikacji Windows Store.</span><span class="sxs-lookup"><span data-stu-id="65b81-119">You will notice a few changes in the functionality of Add Service Reference when done within a Windows Store application.</span></span> <span data-ttu-id="65b81-120">Najpierw plik konfiguracji nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="65b81-120">First no configuration file is generated.</span></span> <span data-ttu-id="65b81-121">Aplikacje Windows Store nie należy używać plików konfiguracji, więc musi być skonfigurowany w kodzie.</span><span class="sxs-lookup"><span data-stu-id="65b81-121">Windows Store applications do not use configuration files, so they must be configured in code.</span></span> <span data-ttu-id="65b81-122">Ten kod konfiguracji można znaleźć w pliku References.cs generowane przez Dodaj odwołanie do usługi.</span><span class="sxs-lookup"><span data-stu-id="65b81-122">This configuration code can be found in the References.cs file generated by Add Service Reference.</span></span> <span data-ttu-id="65b81-123">Aby wyświetlić ten plik, koniecznie wybierz pozycję "Pokaż wszystkie pliki" w Eksploratorze rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="65b81-123">To see this file, make sure to select "Show All Files" in the solution explorer.</span></span> <span data-ttu-id="65b81-124">Plik zostanie umieszczony w odwołania do usług, a następnie Reference.svcmap węzły w projekcie.</span><span class="sxs-lookup"><span data-stu-id="65b81-124">The file will be located under the Service References and then Reference.svcmap nodes within the project.</span></span> <span data-ttu-id="65b81-125">Wszystkie operacje wygenerowane dla usług WCF w aplikacji Windows Store jest asynchroniczne, za pomocą wzorca asynchronicznego opartego na zadaniach.</span><span class="sxs-lookup"><span data-stu-id="65b81-125">All operations generated for WCF services within a Windows Store application will be asynchronous using the Task-based asynchronous pattern.</span></span> <span data-ttu-id="65b81-126">Aby uzyskać więcej informacji, zobacz [zadań asynchronicznych - uprościć programowanie asynchroniczne przy użyciu zadania](https://msdn.microsoft.com/magazine/ff959203.aspx).</span><span class="sxs-lookup"><span data-stu-id="65b81-126">For more information, see [Async Tasks - Simplify Asynchronous Programming with Tasks](https://msdn.microsoft.com/magazine/ff959203.aspx).</span></span>  
  
 <span data-ttu-id="65b81-127">Ponieważ konfiguracji jest teraz generowany w kodzie, wszelkie zmiany wprowadzone w pliku Reference.cs zostaną zastąpione za każdym razem, gdy odwołanie do usługi jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="65b81-127">Because configuration is now generated in code, any changes made in the Reference.cs file would be overwritten every time the service reference is updated.</span></span> <span data-ttu-id="65b81-128">Aby rozwiązać ten problem kodu konfiguracji zostanie wygenerowany wewnątrz metody częściowej, można zaimplementować w klasie serwera proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="65b81-128">To remedy this situation the configuration code is generated within a partial method, which you can implement in your client proxy class.</span></span> <span data-ttu-id="65b81-129">Metoda częściowa jest zadeklarowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="65b81-129">The partial method is declared as follows:</span></span>  
  
```csharp  
static partial void Configure(System.ServiceModel.Description.ServiceEndpoint serviceEndpoint,  
            System.ServiceModel.Description.ClientCredentials clientCredentials);  
```  
  
 <span data-ttu-id="65b81-130">Następnie można zaimplementować tę metodę częściową i Zmień powiązanie lub punkt końcowy w klasie klienta serwera proxy w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="65b81-130">You can then implement this partial method and change the binding or endpoint in your client proxy class as follows:</span></span>  
  
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
  
### <a name="serialization"></a><span data-ttu-id="65b81-131">Serializacja</span><span class="sxs-lookup"><span data-stu-id="65b81-131">Serialization</span></span>  
 <span data-ttu-id="65b81-132">Następujące serializatory są obsługiwane w aplikacjach Windows Store:</span><span class="sxs-lookup"><span data-stu-id="65b81-132">The following serializers are supported in Windows Store applications:</span></span>  
  
1.  <span data-ttu-id="65b81-133">DataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="65b81-133">DataContractSerializer</span></span>  
  
2.  <span data-ttu-id="65b81-134">DataContractJsonSerializer</span><span class="sxs-lookup"><span data-stu-id="65b81-134">DataContractJsonSerializer</span></span>  
  
3.  <span data-ttu-id="65b81-135">XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="65b81-135">XmlSerializer</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="65b81-136">XmlDictionaryWriter.Write(DateTime) teraz zapisuje obiekt daty/godziny jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="65b81-136">XmlDictionaryWriter.Write(DateTime) now writes the DateTime object as a string.</span></span>  
  
### <a name="security"></a><span data-ttu-id="65b81-137">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="65b81-137">Security</span></span>  

<span data-ttu-id="65b81-138">Następujące tryby zabezpieczeń są obsługiwane w aplikacjach Windows Store:</span><span class="sxs-lookup"><span data-stu-id="65b81-138">The following security modes are supported in Windows Store applications:</span></span>
  
1. <xref:System.ServiceModel.SecurityMode.None>  
  
2. <xref:System.ServiceModel.SecurityMode.Transport>  
  
3. <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>
  
4. <xref:System.ServiceModel.SecurityMode.Message>
  
<span data-ttu-id="65b81-139">Następujące typy poświadczeń klienta są obsługiwane w aplikacjach Windows Store:</span><span class="sxs-lookup"><span data-stu-id="65b81-139">The following client credential types are supported in Windows Store applications:</span></span>
  
1.  <span data-ttu-id="65b81-140">Brak</span><span class="sxs-lookup"><span data-stu-id="65b81-140">None</span></span>  
  
2.  <span data-ttu-id="65b81-141">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="65b81-141">Basic</span></span>  
  
3.  <span data-ttu-id="65b81-142">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="65b81-142">Digest</span></span>  
  
4.  <span data-ttu-id="65b81-143">Negotiate</span><span class="sxs-lookup"><span data-stu-id="65b81-143">Negotiate</span></span>  
  
5.  <span data-ttu-id="65b81-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="65b81-144">NTLM</span></span>  
  
6.  <span data-ttu-id="65b81-145">Windows</span><span class="sxs-lookup"><span data-stu-id="65b81-145">Windows</span></span>  
  
7.  <span data-ttu-id="65b81-146">Nazwa użytkownika (zabezpieczenia komunikatów)</span><span class="sxs-lookup"><span data-stu-id="65b81-146">Username (Message Security)</span></span>  
  
8.  <span data-ttu-id="65b81-147">Windows (zabezpieczenia transportu)</span><span class="sxs-lookup"><span data-stu-id="65b81-147">Windows (Transport Security)</span></span>  
  
 <span data-ttu-id="65b81-148">Do uzyskania dostępu i wysyłać domyślne poświadczenia Windows przy użyciu aplikacji Windows Store, należy włączyć tę funkcję w pliku Package.appmanifest.</span><span class="sxs-lookup"><span data-stu-id="65b81-148">In order for Windows Store applications to access and send default Windows credentials, you must enable this functionality within the Package.appmanifest file.</span></span> <span data-ttu-id="65b81-149">Otwórz ten plik i wybierz kartę funkcji wybierz pozycję "Domyślne poświadczenia Windows".</span><span class="sxs-lookup"><span data-stu-id="65b81-149">Open this file and select the Capabilities tab and select "Default Windows Credentials".</span></span> <span data-ttu-id="65b81-150">Umożliwia aplikacji łączenie się z zasobami w sieci intranet, które wymagają podania poświadczeń domeny.</span><span class="sxs-lookup"><span data-stu-id="65b81-150">This allows the application to connect to intranet resources that require domain credentials.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="65b81-151">Aby aplikacje Windows Store, do nawiązywania połączeń między maszyny należy włączyć dostępna inna funkcja o nazwie "Strona główna/pracy sieci".</span><span class="sxs-lookup"><span data-stu-id="65b81-151">In order for Windows Store applications to make cross machine calls you must enable another capability called "Home/Work Networking".</span></span> <span data-ttu-id="65b81-152">To ustawienie jest również w pliku Package.appmanifest na karcie możliwości. Zaznacz pole wyboru głównej/pracy sieci.</span><span class="sxs-lookup"><span data-stu-id="65b81-152">This setting is also in the Package.appmanifest file under the Capabilities tab. Select the Home/Work Networking checkbox.</span></span> <span data-ttu-id="65b81-153">Dzięki temu aplikację, którą przychodzący i wychodzący dostęp do sieci użytkownika przez zaufanych miejsc, takich jak macierzystego i działają.</span><span class="sxs-lookup"><span data-stu-id="65b81-153">This gives your application inbound and outbound access to the networks of the user’s trusted places like home and work.</span></span> <span data-ttu-id="65b81-154">Porty przychodzące krytyczne zawsze są blokowane.</span><span class="sxs-lookup"><span data-stu-id="65b81-154">Inbound critical ports are always blocked.</span></span> <span data-ttu-id="65b81-155">Aby uzyskać dostęp do usług w Internecie, należy również włączyć możliwości Internet (klient).</span><span class="sxs-lookup"><span data-stu-id="65b81-155">For accessing services on the internet you must also enable Internet (Client) capability.</span></span>  
  
### <a name="misc"></a><span data-ttu-id="65b81-156">Różne</span><span class="sxs-lookup"><span data-stu-id="65b81-156">Misc</span></span>  
 <span data-ttu-id="65b81-157">Użyj następujących klas jest obsługiwana dla Windows Store aplikacji:</span><span class="sxs-lookup"><span data-stu-id="65b81-157">The use of the following classes is supported for Windows Store Applications:</span></span>  
  
1.  <xref:System.ServiceModel.ChannelFactory>  
  
2.  <xref:System.ServiceModel.DuplexChannelFactory%601>
  
3.  <xref:System.ServiceModel.CallbackBehaviorAttribute>  
  
### <a name="defining-service-contracts"></a><span data-ttu-id="65b81-158">Definiowanie kontraktów usług</span><span class="sxs-lookup"><span data-stu-id="65b81-158">Defining Service Contracts</span></span>  
 <span data-ttu-id="65b81-159">Firma Microsoft zaleca tylko Definiowanie operacji asynchronicznej usługi za pomocą wzorca asynchronicznego opartego na zadaniach.</span><span class="sxs-lookup"><span data-stu-id="65b81-159">We recommend only defining asynchronous service operations using the task-based async pattern.</span></span> <span data-ttu-id="65b81-160">Dzięki temu aplikacje Windows Store nadal odpowiadać podczas wywoływania operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="65b81-160">This ensures Windows Store applications remain responsive while calling a service operation.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="65b81-161">Gdy żaden wyjątek zostanie zgłoszony, jeśli zdefiniujesz Operacja synchroniczna, zdecydowanie zaleca się definiować tylko operacji asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="65b81-161">While no exception will be thrown if you define a synchronous operation, it is strongly recommended to only define asynchronous operations.</span></span>  
  
### <a name="calling-wcf-services-from-windows-store-applications"></a><span data-ttu-id="65b81-162">Wywoływanie usługi WCF z aplikacji Windows Store</span><span class="sxs-lookup"><span data-stu-id="65b81-162">Calling WCF Services from Windows Store Applications</span></span>  
 <span data-ttu-id="65b81-163">Jak wspomniano wcześniej cała konfiguracja musi odbywać się w kodzie w metodzie GetBindingForEndpoint w klasie, wygenerowany serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="65b81-163">As mentioned before all configuration must be done in code in the GetBindingForEndpoint method in the generated proxy class.</span></span> <span data-ttu-id="65b81-164">Wywoływanie operacji usługi odbywa się taka sama jak wywołanie metody asynchronicznej wszelkie zadania, jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="65b81-164">Calling a service operation is done the same as calling any task-based asynchronous method as shown in the following code snippet.</span></span>  
  
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
  
 <span data-ttu-id="65b81-165">Zwróć uwagę na async — słowo kluczowe dla metody, dzięki czemu wywołania asynchronicznego i słowo kluczowe await podczas wywoływania metody asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="65b81-165">Notice the use of the async keyword on the method making the asynchronous call and the await keyword when calling the asynchronous method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b81-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65b81-166">See also</span></span>
- [<span data-ttu-id="65b81-167">Usługi WCF w blogu aplikacje Windows Store</span><span class="sxs-lookup"><span data-stu-id="65b81-167">WCF in Windows Store Apps Blog</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/09/22/wcf-in-win8-metro-styled-apps-absolutely-supported.aspx)
- [<span data-ttu-id="65b81-168">Klienci WCF Windows Store i zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="65b81-168">WCF Windows Store Clients and Security</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/11/calling-a-wcf-service-from-a-metro-application-adding-security.aspx)
- [<span data-ttu-id="65b81-169">Aplikacje Windows Store i wywołań między maszyny</span><span class="sxs-lookup"><span data-stu-id="65b81-169">Windows Store Apps and Cross Machine Calls</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="65b81-170">Wywołanie usługi WCF wdrożonych na platformie Azure z aplikacji Windows Store</span><span class="sxs-lookup"><span data-stu-id="65b81-170">Calling a WCF Service Deployed in Azure from a Windows Store App</span></span>](https://blogs.msdn.com/b/piyushjo/archive/2011/10/22/calling-a-wcf-service-from-a-metro-application-cross-machine-scenario.aspx)
- [<span data-ttu-id="65b81-171">Programowanie zabezpieczeń WCF</span><span class="sxs-lookup"><span data-stu-id="65b81-171">Programming WCF Security</span></span>](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [<span data-ttu-id="65b81-172">Powiązania</span><span class="sxs-lookup"><span data-stu-id="65b81-172">Bindings</span></span>](../../../../docs/framework/wcf/bindings.md)
