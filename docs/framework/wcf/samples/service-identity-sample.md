---
title: Tożsamość usług — przykład
ms.date: 03/30/2017
ms.assetid: 79fa8c1c-85bb-4b67-bc67-bfaf721303f8
ms.openlocfilehash: 868bd6e0ac7429224462c973c1c48132ec3860ba
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76919363"
---
# <a name="service-identity-sample"></a><span data-ttu-id="5b342-102">Tożsamość usług — przykład</span><span class="sxs-lookup"><span data-stu-id="5b342-102">Service Identity Sample</span></span>
<span data-ttu-id="5b342-103">Ta przykładowa tożsamość usługi pokazuje, jak ustawić tożsamość dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-103">This service identity sample demonstrates how to set the identity for a service.</span></span> <span data-ttu-id="5b342-104">W czasie projektowania klient może pobrać tożsamość przy użyciu metadanych usługi, a następnie w czasie wykonywania klient może uwierzytelnić tożsamość usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-104">At design time, a client can retrieve the identity using the service's metadata and then at runtime the client can authenticate the service's identity.</span></span> <span data-ttu-id="5b342-105">Pojęcie tożsamości usługi polega na umożliwieniu klientowi uwierzytelnienia usługi przed wywołaniem jakiejkolwiek z jej operacji, co chroni klienta przed nieuwierzytelnionymi wywołaniami.</span><span class="sxs-lookup"><span data-stu-id="5b342-105">The concept of service identity is to allow a client to authenticate a service before calling any of its operations, thereby protecting the client from unauthenticated calls.</span></span> <span data-ttu-id="5b342-106">W przypadku bezpiecznego połączenia usługa uwierzytelnia także poświadczenia klienta przed zezwoleniem na dostęp do niego, ale nie jest to fokus tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="5b342-106">On a secure connection the service also authenticates a client's credentials before allowing it access, but this is not the focus of this sample.</span></span> <span data-ttu-id="5b342-107">Zapoznaj się z przykładami w [kliencie](../../../../docs/framework/wcf/samples/client.md) , który pokazuje uwierzytelnianie serwera.</span><span class="sxs-lookup"><span data-stu-id="5b342-107">See the samples in [Client](../../../../docs/framework/wcf/samples/client.md) that show server authentication.</span></span>

> [!NOTE]
> <span data-ttu-id="5b342-108">Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="5b342-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="5b342-109">Ten przykład ilustruje następujące funkcje:</span><span class="sxs-lookup"><span data-stu-id="5b342-109">This sample illustrates the following features:</span></span>

- <span data-ttu-id="5b342-110">Jak ustawić różne typy tożsamości w różnych punktach końcowych dla usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-110">How to set the different types of identity on different endpoints for a service.</span></span> <span data-ttu-id="5b342-111">Każdy typ tożsamości ma różne możliwości.</span><span class="sxs-lookup"><span data-stu-id="5b342-111">Each type of identity has different capabilities.</span></span> <span data-ttu-id="5b342-112">Typ tożsamości do użycia zależy od typu poświadczeń zabezpieczeń używanych w powiązaniu punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="5b342-112">The type of identity to use is dependent on the type of security credentials used on the endpoint's binding.</span></span>

- <span data-ttu-id="5b342-113">Tożsamość można skonfigurować w sposób deklaratywny w konfiguracji lub za pomocą kodu.</span><span class="sxs-lookup"><span data-stu-id="5b342-113">Identity can either be set declaratively in configuration or imperatively in code.</span></span> <span data-ttu-id="5b342-114">Zwykle dla klienta i usługi należy użyć konfiguracji, aby ustawić tożsamość.</span><span class="sxs-lookup"><span data-stu-id="5b342-114">Typically for both the client and the service you should use configuration to set the identity.</span></span>

- <span data-ttu-id="5b342-115">Jak ustawić niestandardową tożsamość na kliencie.</span><span class="sxs-lookup"><span data-stu-id="5b342-115">How to set a custom identity on the client.</span></span> <span data-ttu-id="5b342-116">Niestandardowa tożsamość jest zwykle dostosowywana do istniejącego typu tożsamości, która umożliwia klientowi badanie innych informacji o zadaniu w poświadczeniach usługi w celu podejmowania decyzji dotyczących autoryzacji przed wywołaniem usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-116">A custom identity is typically a customization of an existing type of identity that enables the client to examine other claim information provided in the service's credentials to make authorization decisions before calling the service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5b342-117">Ten przykład umożliwia sprawdzenie tożsamości określonego certyfikatu o nazwie identity.com i klucza RSA zawartego w tym certyfikacie.</span><span class="sxs-lookup"><span data-stu-id="5b342-117">This sample checks the identity of a specific certificate called identity.com and the RSA key contained within this certificate.</span></span> <span data-ttu-id="5b342-118">W przypadku korzystania z certyfikatów i typów tożsamości RSA w konfiguracji na kliencie, prostym sposobem na uzyskanie tych wartości jest sprawdzenie WSDL dla usługi, w której te wartości są serializowane.</span><span class="sxs-lookup"><span data-stu-id="5b342-118">When using the Certificate and RSA identity types in configuration on the client, an easy way to get these values is to inspect the WSDL for the service where these values are serialized.</span></span>

 <span data-ttu-id="5b342-119">Poniższy przykładowy kod pokazuje, jak skonfigurować tożsamość punktu końcowego usługi za pomocą serwera nazw domen (DNS) certyfikatu przy użyciu WSHttpBinding.</span><span class="sxs-lookup"><span data-stu-id="5b342-119">The following sample code shows how to configure the identity of a service endpoint with the Domain Name Server (DNS) of a certificate using a WSHttpBinding.</span></span>

```csharp
//Create a service endpoint and set its identity to the certificate's DNS
WSHttpBinding wsAnonbinding = new WSHttpBinding (SecurityMode.Message);
// Client are Anonymous to the service
wsAnonbinding.Security.Message.ClientCredentialType = MessageCredentialType.None;
WServiceEndpoint ep = serviceHost.AddServiceEndpoint(typeof(ICalculator),wsAnonbinding, String.Empty);
EndpointAddress epa = new EndpointAddress(dnsrelativeAddress,EndpointIdentity.CreateDnsIdentity("identity.com"));
ep.Address = epa;
```

 <span data-ttu-id="5b342-120">Tożsamość można także określić w konfiguracji w pliku App. config.</span><span class="sxs-lookup"><span data-stu-id="5b342-120">The identity can also be specified in configuration in the App.config file.</span></span> <span data-ttu-id="5b342-121">Poniższy przykład pokazuje, jak ustawić tożsamość UPN (główna nazwa użytkownika) dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-121">The following example shows how to set the UPN (User Principal Name) identity for a service endpoint.</span></span>

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

 <span data-ttu-id="5b342-122">Tożsamość niestandardową można ustawić na kliencie, pobierając z <xref:System.ServiceModel.EndpointIdentity> i <xref:System.ServiceModel.Security.IdentityVerifier> klas.</span><span class="sxs-lookup"><span data-stu-id="5b342-122">A custom identity can be set on the client by deriving from the <xref:System.ServiceModel.EndpointIdentity> and the <xref:System.ServiceModel.Security.IdentityVerifier> classes.</span></span> <span data-ttu-id="5b342-123">Koncepcyjnie Klasa <xref:System.ServiceModel.Security.IdentityVerifier> może być traktowana jako odpowiednik klienta klasy `AuthorizationManager` usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-123">Conceptually the <xref:System.ServiceModel.Security.IdentityVerifier> class can be considered to be the client equivalent of the service's `AuthorizationManager` class.</span></span> <span data-ttu-id="5b342-124">Poniższy przykład kodu przedstawia implementację `OrgEndpointIdentity`, która przechowuje nazwę organizacji do dopasowania w nazwie podmiotu certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="5b342-124">The following code example shows an implementation of `OrgEndpointIdentity`, which stores an organization name to match in the subject name of the server's certificate.</span></span> <span data-ttu-id="5b342-125">Sprawdzanie autoryzacji nazwy organizacji odbywa się w metodzie `CheckAccess` klasy `CustomIdentityVerifier`.</span><span class="sxs-lookup"><span data-stu-id="5b342-125">The authorization check for the organization name occurs in the `CheckAccess` method on the `CustomIdentityVerifier` class.</span></span>

```csharp
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

 <span data-ttu-id="5b342-126">Ten przykład używa certyfikatu o nazwie identity.com, który znajduje się w folderze rozwiązania tożsamości specyficznej dla języka.</span><span class="sxs-lookup"><span data-stu-id="5b342-126">This sample uses a certificate called identity.com which is in the language-specific Identity solution folder.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b342-127">Aby skonfigurować, skompilować i uruchomić przykład</span><span class="sxs-lookup"><span data-stu-id="5b342-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5b342-128">Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b342-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="5b342-129">Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b342-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="5b342-130">Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b342-130">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="5b342-131">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="5b342-131">To run the sample on the same computer</span></span>

1. <span data-ttu-id="5b342-132">W systemie Windows XP lub Windows Vista Zaimportuj plik certyfikatu Identity. pfx w folderze rozwiązania tożsamości do magazynu certyfikatów LocalMachine/my (Personal) za pomocą narzędzia przystawek programu MMC.</span><span class="sxs-lookup"><span data-stu-id="5b342-132">On Windows XP or Windows Vista, import the Identity.pfx certificate file in the Identity solution folder into the LocalMachine/My (Personal) certificate store using the MMC snap-in tool.</span></span> <span data-ttu-id="5b342-133">Ten plik jest chroniony hasłem.</span><span class="sxs-lookup"><span data-stu-id="5b342-133">This file is password protected.</span></span> <span data-ttu-id="5b342-134">Podczas importowania zostanie wyświetlony monit o podanie hasła.</span><span class="sxs-lookup"><span data-stu-id="5b342-134">During the import you are asked for a password.</span></span> <span data-ttu-id="5b342-135">Wpisz `xyz` w polu hasło.</span><span class="sxs-lookup"><span data-stu-id="5b342-135">Type `xyz` into the password box.</span></span> <span data-ttu-id="5b342-136">Aby uzyskać więcej informacji, zobacz temat [How to: View Certificates with MMC przystawka](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) .</span><span class="sxs-lookup"><span data-stu-id="5b342-136">For more information, see the [How to: View Certificates with the MMC Snap-in](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md) topic.</span></span> <span data-ttu-id="5b342-137">Po wykonaniu tej czynności uruchom setup. bat w wiersz polecenia dla deweloperów dla programu Visual Studio z uprawnieniami administratora, które kopiuje ten certyfikat do magazynu CurrentUser/zaufane osoby do użytku na kliencie.</span><span class="sxs-lookup"><span data-stu-id="5b342-137">Once this is done, run Setup.bat in a Developer Command Prompt for Visual Studio with administrator privileges, which copies this certificate to the CurrentUser/Trusted People store for use on the client.</span></span>

2. <span data-ttu-id="5b342-138">W systemie Windows Server 2003 uruchom setup. bat z przykładowego folderu instalacyjnego w wierszu polecenia programu Visual Studio 2012 z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5b342-138">On Windows Server 2003, run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt with administrator privileges.</span></span> <span data-ttu-id="5b342-139">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="5b342-139">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5b342-140">Plik wsadowy Setup. bat został zaprojektowany do uruchamiania z wiersza polecenia programu Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="5b342-140">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="5b342-141">Zmienna środowiskowa PATH ustawiona w wierszu polecenia programu Visual Studio 2012 wskazuje katalog zawierający pliki wykonywalne wymagane przez skrypt Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="5b342-141">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span> <span data-ttu-id="5b342-142">Upewnij się, że certyfikaty są usuwane przez uruchomienie Oczyść. bat po zakończeniu z przykładem.</span><span class="sxs-lookup"><span data-stu-id="5b342-142">Ensure that you remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="5b342-143">Inne przykłady zabezpieczeń używają tych samych certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="5b342-143">Other security samples use the same certificates.</span></span>  
  
3. <span data-ttu-id="5b342-144">Uruchom plik Service. exe z katalogu \service\bin.</span><span class="sxs-lookup"><span data-stu-id="5b342-144">Launch Service.exe from the \service\bin directory.</span></span> <span data-ttu-id="5b342-145">Upewnij się, że usługa wskazuje, że jest gotowa i wyświetla monit o naciśnięcie klawisza \<wprowadzenie > w celu zakończenia usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-145">Ensure that the service indicates that it is ready and displays a prompt to Press \<Enter> to terminate the service.</span></span>  
  
4. <span data-ttu-id="5b342-146">Uruchom program Client. exe z katalogu \client\bin lub naciskając klawisz F5 w programie Visual Studio, aby skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="5b342-146">Launch Client.exe from \client\bin directory or by pressing F5 in Visual Studio to build and run.</span></span> <span data-ttu-id="5b342-147">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="5b342-147">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="5b342-148">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5b342-148">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="5b342-149">Aby uruchomić przykład na wielu komputerach</span><span class="sxs-lookup"><span data-stu-id="5b342-149">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="5b342-150">Przed utworzeniem części klienta przykładu należy zmienić wartość adresu punktu końcowego usługi w pliku Client.cs w metodzie `CallServiceCustomClientIdentity`.</span><span class="sxs-lookup"><span data-stu-id="5b342-150">Before building the client part of the sample, be sure to change the value for the service's endpoint address in the Client.cs file in the `CallServiceCustomClientIdentity` method.</span></span> <span data-ttu-id="5b342-151">Następnie Skompiluj przykład.</span><span class="sxs-lookup"><span data-stu-id="5b342-151">Then build the sample.</span></span>  
  
2. <span data-ttu-id="5b342-152">Utwórz katalog na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-152">Create a directory on the service computer.</span></span>  
  
3. <span data-ttu-id="5b342-153">Skopiuj pliki programu Service z usługi service\bin do katalogu na komputerze usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-153">Copy the service program files from service\bin to the directory on the service computer.</span></span> <span data-ttu-id="5b342-154">Skopiuj także pliki Setup. bat i Oczyść. bat do komputera usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-154">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
4. <span data-ttu-id="5b342-155">Utwórz katalog na komputerze klienckim dla plików binarnych klienta.</span><span class="sxs-lookup"><span data-stu-id="5b342-155">Create a directory on the client computer for the client binaries.</span></span>  
  
5. <span data-ttu-id="5b342-156">Skopiuj pliki programu klienckiego do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5b342-156">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="5b342-157">Skopiuj również do klienta pliki Setup. bat, Oczyść. bat i ImportServiceCert. bat.</span><span class="sxs-lookup"><span data-stu-id="5b342-157">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
6. <span data-ttu-id="5b342-158">W usłudze Uruchom `setup.bat service` w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5b342-158">On the service, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="5b342-159">Uruchomienie `setup.bat` z argumentem `service` tworzy certyfikat usługi z w pełni kwalifikowaną nazwą domeny komputera i eksportuje certyfikat usługi do pliku o nazwie Service. cer.</span><span class="sxs-lookup"><span data-stu-id="5b342-159">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
7. <span data-ttu-id="5b342-160">Skopiuj plik. cer usługi z katalogu usługi do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="5b342-160">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="5b342-161">W pliku Client. exe. config na komputerze klienckim Zmień wartość adresu punktu końcowego, aby odpowiadała nowemu adresowi usługi.</span><span class="sxs-lookup"><span data-stu-id="5b342-161">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="5b342-162">Istnieje wiele wystąpień, które należy zmienić.</span><span class="sxs-lookup"><span data-stu-id="5b342-162">There are multiple instances that must be changed.</span></span>  
  
9. <span data-ttu-id="5b342-163">Na kliencie Uruchom program ImportServiceCert. bat w wiersz polecenia dla deweloperów dla programu Visual Studio otwartego z uprawnieniami administratora.</span><span class="sxs-lookup"><span data-stu-id="5b342-163">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="5b342-164">Spowoduje to zaimportowanie certyfikatu usługi z pliku CER usługi do magazynu CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5b342-164">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="5b342-165">Na komputerze usługi Uruchom program Service. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b342-165">On the service computer, launch the Service.exe from the command prompt.</span></span>  
  
11. <span data-ttu-id="5b342-166">Na komputerze klienckim uruchom program Client. exe z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="5b342-166">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="5b342-167">Jeśli klient i usługa nie mogą się komunikować, zobacz Wskazówki dotyczące [rozwiązywania problemów z przykładami programu WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="5b342-167">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="5b342-168">Aby wyczyścić po przykładzie</span><span class="sxs-lookup"><span data-stu-id="5b342-168">To clean up after the sample</span></span>  
  
- <span data-ttu-id="5b342-169">Uruchom Oczyść. bat w folderze Samples po zakończeniu uruchamiania przykładu.</span><span class="sxs-lookup"><span data-stu-id="5b342-169">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5b342-170">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania tego przykładu między komputerami.</span><span class="sxs-lookup"><span data-stu-id="5b342-170">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="5b342-171">W przypadku uruchamiania przykładów programu Windows Communication Foundation (WCF), które używają certyfikatów między komputerami, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w magazynie CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="5b342-171">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="5b342-172">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="5b342-172">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
