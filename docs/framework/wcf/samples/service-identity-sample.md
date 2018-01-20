---
title: "Tożsamość usług — przykład"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a89839294f74d733ec7f607a0afda53148fbd57
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="service-identity-sample"></a><span data-ttu-id="61769-102">Tożsamość usług — przykład</span><span class="sxs-lookup"><span data-stu-id="61769-102">Service Identity Sample</span></span>
<span data-ttu-id="61769-103">Usługi tożsamości przykładzie pokazano, jak ustawić tożsamości usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="61769-104">W czasie projektowania klient może pobrać tożsamość przy użyciu metadanych usługi, a następnie w czasie wykonywania klienta można uwierzytelnić tożsamości usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="61769-105">Pojęcie tożsamości usługi jest umożliwienie klientowi uwierzytelniania usługi przed wywołaniem dowolnej jego operacje, co chroni klienta z nieuwierzytelnione wywołania.</span><span class="sxs-lookup"><span data-stu-id="61769-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="61769-106">Za pomocą bezpiecznego połączenia usługi również służy do uwierzytelniania poświadczeń klienta wcześniej, ale nie jest to fokus w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="61769-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="61769-107">Zobacz przykłady w [klienta](../../../../docs/framework/wcf/samples/client.md) który Pokaż uwierzytelniania serwera.</span><span class="sxs-lookup"><span data-stu-id="61769-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61769-108">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="61769-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="61769-109">W tym przykładzie przedstawiono następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="61769-109">This sample illustrates the following features:</span></span>  
  
-   <span data-ttu-id="61769-110">Jak ustawić różne typy tożsamości dla różnych punktów końcowych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="61769-111">Każdy typ tożsamości ma innej możliwości.</span><span class="sxs-lookup"><span data-stu-id="61769-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="61769-112">Typ tożsamości do użycia zależy od typu poświadczeń zabezpieczeń używane w powiązaniu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="61769-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>  
  
-   <span data-ttu-id="61769-113">Tożsamość albo można ustawić deklaratywnie w konfiguracji lub imperatively w kodzie.</span><span class="sxs-lookup"><span data-stu-id="61769-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="61769-114">Zazwyczaj zarówno klient, jak i usługi należy użyć konfiguracji, aby ustawić tożsamości.</span><span class="sxs-lookup"><span data-stu-id="61769-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>  
  
-   <span data-ttu-id="61769-115">Jak ustawić tożsamość niestandardowa na kliencie.</span><span class="sxs-lookup"><span data-stu-id="61769-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="61769-116">Tożsamość niestandardowa jest zwykle dostosowanie istniejącego typu tożsamości, która umożliwia klientowi Sprawdź inne informacje oświadczeń w poświadczenia do podejmowania decyzji dotyczących autoryzacji przed wywołaniem usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61769-117">W tym przykładzie sprawdza tożsamość identity.com i kluczy RSA zawartych w tym certyfikatu określonego certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="61769-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="61769-118">Podczas używania typów tożsamości certyfikatu i RSA w konfiguracji na kliencie, najłatwiejszym sposobem uzyskania tych wartości jest do zbadania WSDL usługi gdzie te wartości są serializowane.</span><span class="sxs-lookup"><span data-stu-id="61769-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>  
  
 <span data-ttu-id="61769-119">Następujący przykładowy kod przedstawia sposób konfigurowania tożsamości punktu końcowego usługi z serwera nazw domen (DNS) przy użyciu WSHttpBinding certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="61769-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>  
  
```  
//Create a service endpoint and set its identity to the certificate's DNS                 
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);  
// Client are Anonymous to the service  
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;  
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);  
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));  
ep.Address = epa;  
```  
  
 <span data-ttu-id="61769-120">Można również określić tożsamość w konfiguracji w pliku App.config.</span><span class="sxs-lookup"><span data-stu-id="61769-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="61769-121">Poniższy przykład przedstawia sposób ustawiania tożsamością UPN (główna nazwa użytkownika) dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>  
  
```xml  
<endpoint address="upnidentity"  
        behaviorConfiguration=""  
        binding="wsHttpBinding"  
        bindingConfiguration="WSHttpBinding_Windows"  
        name="WSHttpBinding_ICalculator_Windows"  
        contract="Microsoft.ServiceModel.Samples.ICalculator">  
  <!-- Set the UPN identity for this endpoint -->  
  <identity>  
      <userPrincipalName value="host\myservice.com" />  
  </identity >  
</endpoint>  
```  
  
 <span data-ttu-id="61769-122">Tożsamość niestandardowa można ustawić na kliencie przez pochodny <xref:System.ServiceModel.EndpointIdentity> i <xref:System.ServiceModel.Security.IdentityVerifier> klasy.</span><span class="sxs-lookup"><span data-stu-id="61769-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="61769-123">Koncepcyjnie <xref:System.ServiceModel.Security.IdentityVerifier> klasy mogą być uważane klienta odpowiednik usługi `AuthorizationManager` klasy.</span><span class="sxs-lookup"><span data-stu-id="61769-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="61769-124">Poniższy przykładowy kod przedstawia implementację `OrgEndpointIdentity`, która przechowuje nazwę organizacji w celu dopasowania do nazwy podmiotu certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="61769-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="61769-125">Sprawdzanie autoryzacji, nazwę organizacji jest wykonywane w `CheckAccess` metoda `CustomIdentityVerifier` klasy.</span><span class="sxs-lookup"><span data-stu-id="61769-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>  
  
```  
// This custom EndpointIdentity stores an organization name   
public class OrgEndpointIdentity : EndpointIdentity  
{  
    private string orgClaim;  
    public OrgEndpointIdentity(string orgName)  
    {  
        orgClaim = orgName;  
    }  
    public string OrganizationClaim  
    {  
        get { return orgClaim; }  
        set { orgClaim = value; }  
    }  
}  
  
//This custom IdentityVerifier uses the supplied OrgEndpointIdentity to  
//check that X.509 certificate's distinguished name claim contains  
//the organization name e.g. the string value "O=Contoso"   
class CustomIdentityVerifier : IdentityVerifier  
{  
    public override bool CheckAccess(EndpointIdentity identity, AuthorizationContext authContext)  
    {  
        bool returnvalue = false;  
        foreach (ClaimSet claimset in authContext.ClaimSets)  
        {  
            foreach (Claim claim in claimset)  
            {  
                if (claim.ClaimType == "http://schemas.microsoft.com/ws/2005/05/identity/claims/x500distinguishedname")  
                {  
                    X500DistinguishedName name = (X500DistinguishedName)claim.Resource;  
                    if (name.Name.Contains(((OrgEndpointIdentity)identity).OrganizationClaim))  
                    {  
                        Console.WriteLine("Claim Type: {0}",claim.ClaimType);  
                        Console.WriteLine("Right: {0}", claim.Right);  
                        Console.WriteLine("Resource: {0}",claim.Resource);  
                        Console.WriteLine();  
                        returnvalue = true;  
                    }  
                }  
            }  
        }  
        return returnvalue;  
    }  
}  
```  
  
 <span data-ttu-id="61769-126">W przykładzie użyto certyfikatu o nazwie identity.com, który znajduje się w folderze rozwiązania tożsamości specyficzny dla języka.</span><span class="sxs-lookup"><span data-stu-id="61769-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="61769-127">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="61769-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="61769-128">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61769-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="61769-129">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61769-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="61769-130">Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="61769-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="61769-131">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="61769-131">To run the sample on the same computer</span></span>  
  
1.  <span data-ttu-id="61769-132">Na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] lub [!INCLUDE[wv](../../../../includes/wv-md.md)], zaimportuj plik certyfikatu Identity.pfx w folderze rozwiązania tożsamości w magazynie LocalMachine/My (osobistych) certyfikatu przy użyciu narzędzia przystawki programu MMC.</span><span class="sxs-lookup"><span data-stu-id="61769-132">On [!INCLUDE[wxp](../../../../includes/wxp-md.md)] or [!INCLUDE[wv](../../../../includes/wv-md.md)], import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="61769-133">Ten plik jest chroniony hasłem.</span><span class="sxs-lookup"><span data-stu-id="61769-133">This file is password protected.</span></span> <span data-ttu-id="61769-134">Podczas importowania użytkownik zostanie poproszony o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="61769-134">During the import you are asked for a password.</span></span> <span data-ttu-id="61769-135">Typ `xyz` w polu hasła.</span><span class="sxs-lookup"><span data-stu-id="61769-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="61769-136">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie certyfikatów w przystawce MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="61769-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="61769-137">Po zakończeniu uruchom pliku Setup.bat w Visual Studio wiersz polecenia z uprawnieniami administratora, które kopiuje ten certyfikat w magazynie CurrentUser/zaufanych osób do użycia na kliencie.</span><span class="sxs-lookup"><span data-stu-id="61769-137">Once this is done, run Setup.bat in a Visual Studio command prompt with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>  
  
2.  <span data-ttu-id="61769-138">Na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], uruchom z folderu instalacyjnego próbki wewnątrz pliku Setup.bat [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersz polecenia z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="61769-138">On [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], run Setup.bat from the sample install folder inside a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt with administrator privileges.</span></span> <span data-ttu-id="61769-139">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="61769-139">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61769-140">Plik wsadowy pliku Setup.bat jest przeznaczony do uruchamiania z [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61769-140">The Setup.bat batch file is designed to be run from a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt.</span></span> <span data-ttu-id="61769-141">Wartość zmiennej środowiskowej PATH w [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] wskazuje katalog zawierający pliki wykonywalne wymagane przez pliku Setup.bat skryptu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61769-141">The PATH environment variable set within the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="61769-142">Upewnij się, Usuń certyfikaty, uruchamiając Cleanup.bat, po zakończeniu z próbką.</span><span class="sxs-lookup"><span data-stu-id="61769-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="61769-143">Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="61769-143">Other security samples use the same certificates.</span></span>  
  
3.  <span data-ttu-id="61769-144">Uruchom Service.exe z katalogu \service\bin.</span><span class="sxs-lookup"><span data-stu-id="61769-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="61769-145">Upewnij się, że usługa wskazuje, że jest gotowy i wyświetla monit o naciśnięcie klawisza \<Enter > zakończenie usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4.  <span data-ttu-id="61769-146">Uruchom Client.exe z katalogu \client\bin lub naciskając klawisz F5 w programie Visual Studio, aby skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="61769-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="61769-147">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="61769-147">Client activity is displayed on the client console application.</span></span>  
  
5.  <span data-ttu-id="61769-148">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="61769-148">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="61769-149">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="61769-149">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="61769-150">Przed zbudowaniem klienta część próbki, należy zmienić wartość adres punktu końcowego usługi w pliku Client.cs `CallServiceCustomClientIdentity` metody.</span><span class="sxs-lookup"><span data-stu-id="61769-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="61769-151">Następnie tworzyć przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="61769-151">Then build the sample.</span></span>  
  
2.  <span data-ttu-id="61769-152">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-152">Create a directory on the service computer.</span></span>  
  
3.  <span data-ttu-id="61769-153">Skopiuj pliki programu usługi z service\bin do katalogu na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="61769-154">Także skopiować pliki pliku Setup.bat i Cleanup.bat na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4.  <span data-ttu-id="61769-155">Utwórz katalog na komputerze klienckim, aby pliki binarne klienta.</span><span class="sxs-lookup"><span data-stu-id="61769-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5.  <span data-ttu-id="61769-156">Skopiuj pliki programu klienta do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="61769-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="61769-157">Także skopiować pliki pliku Setup.bat, Cleanup.bat i ImportServiceCert.bat do klienta.</span><span class="sxs-lookup"><span data-stu-id="61769-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6.  <span data-ttu-id="61769-158">W usłudze, uruchom `setup.bat service` w wierszu polecenia programu Visual Studio otwarty z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="61769-158">On the service, run `setup.bat service` in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="61769-159">Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z domeny w pełni kwalifikowaną nazwę komputera i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="61769-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7.  <span data-ttu-id="61769-160">Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="61769-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8.  <span data-ttu-id="61769-161">W pliku Client.exe.config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby dopasować nowego adresu usługi.</span><span class="sxs-lookup"><span data-stu-id="61769-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="61769-162">Istnieje wiele wystąpień, które musi zostać zmienione.</span><span class="sxs-lookup"><span data-stu-id="61769-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="61769-163">Na komputerze klienckim należy uruchomić ImportServiceCert.bat w wierszu polecenia programu Visual Studio została otwarta z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="61769-163">On the client, run ImportServiceCert.bat in a Visual Studio command prompt opened with administrator privileges.</span></span> <span data-ttu-id="61769-164">Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="61769-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="61769-165">Na komputerze, usługi uruchom Service.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61769-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="61769-166">Na komputerze klienckim należy uruchomić Client.exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="61769-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="61769-167">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="61769-167">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="61769-168">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="61769-168">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="61769-169">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="61769-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="61769-170">Ten skrypt nie powoduje usunięcia usług certyfikatów na komputerze klienckim, podczas uruchamiania na komputerach w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="61769-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="61769-171">Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="61769-171">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="61769-172">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="61769-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61769-173">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61769-173">See Also</span></span>
