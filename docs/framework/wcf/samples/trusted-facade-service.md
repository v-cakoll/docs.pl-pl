---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: d5a4cfe63f2fc6facbe4ce78d1c0047349e303fd
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807664"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="cb088-102">Zaufana usługa fasady</span><span class="sxs-lookup"><span data-stu-id="cb088-102">Trusted Facade Service</span></span>
<span data-ttu-id="cb088-103">W tym przykładzie scenariuszu pokazano, jak przepływ informacji o tożsamości obiektu wywołującego z jedną usługę do drugiego za pomocą usługi Windows Communication Foundation (WCF) infrastruktura zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="cb088-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="cb088-104">Jest wspólnego wzorca projektowego do udostępnienia funkcji udostępnianych przez usługę do publicznej sieci przy użyciu usługi fasad.</span><span class="sxs-lookup"><span data-stu-id="cb088-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="cb088-105">Usługa fasad zazwyczaj znajduje się w sieci obwodowej (znanej także jako strefa DMZ, strefą zdemilitaryzowaną i podsiecią ekranowaną), a także komunikuje się za pomocą usługi wewnętrznej bazy danych, która implementuje logiki biznesowej i ma dostęp do danych wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="cb088-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="cb088-106">Kanał komunikacji między usługą fasad i usługi wewnętrznej bazy danych przechodzi przez zaporę i jest zazwyczaj ograniczone do tylko jednej celu.</span><span class="sxs-lookup"><span data-stu-id="cb088-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="cb088-107">Ten przykład obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="cb088-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="cb088-108">Kalkulator klienta</span><span class="sxs-lookup"><span data-stu-id="cb088-108">Calculator client</span></span>  
  
-   <span data-ttu-id="cb088-109">Kalkulator fasad usługi</span><span class="sxs-lookup"><span data-stu-id="cb088-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="cb088-110">Kalkulator usługi wewnętrznej bazy danych</span><span class="sxs-lookup"><span data-stu-id="cb088-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="cb088-111">Usługa fasad jest odpowiedzialna za sprawdzanie poprawności żądania i uwierzytelniania obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cb088-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="cb088-112">Po pomyślnym uwierzytelnieniu i sprawdzania poprawności przesyła żądanie do usługi zaplecza przy użyciu kanału komunikacyjnego kontrolowane w sieci obwodowej z siecią wewnętrzną.</span><span class="sxs-lookup"><span data-stu-id="cb088-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="cb088-113">Jako część przekazane żądanie usługi fasad zawiera informacje o tożsamości obiektu wywołującego, dzięki czemu usługi wewnętrznej bazy danych można użyć tych informacji podczas jego przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="cb088-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="cb088-114">Tożsamość obiektu wywołującego są przesyłane przy użyciu `Username` tokenów zabezpieczających w komunikacie `Security` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="cb088-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="cb088-115">Przykład używa infrastruktury zabezpieczeń WCF do przesyłania i wyodrębnić te informacje z `Security` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="cb088-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb088-116">Do usługi zaplecza ufa usługi fasad do uwierzytelniania obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cb088-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="cb088-117">W związku z tym usługi wewnętrznej bazy danych nie uwierzytelnia wywołującego ponownie; używa informacji o tożsamości udostępnianych przez usługę fasad w przekazane żądanie.</span><span class="sxs-lookup"><span data-stu-id="cb088-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="cb088-118">Z powodu tej relacji zaufania usługi wewnętrznej bazy danych musi uwierzytelniać usługi fasad w celu zapewnienia, że przekazany dalej komunikat pochodzi z zaufanego źródła — w takim przypadku usługa fasad.</span><span class="sxs-lookup"><span data-stu-id="cb088-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="cb088-119">Implementacja</span><span class="sxs-lookup"><span data-stu-id="cb088-119">Implementation</span></span>  
 <span data-ttu-id="cb088-120">Istnieją dwie ścieżki komunikacji, w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb088-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="cb088-121">Najpierw jest między klientem a usługą fasad drugą jest wartość między usługą fasad i usługi wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cb088-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="cb088-122">Ścieżki komunikacji między klientem a usługą fasad</span><span class="sxs-lookup"><span data-stu-id="cb088-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="cb088-123">Klient do komunikacji usługi fasad ścieżki używa `wsHttpBinding` z `UserName` typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="cb088-124">Oznacza to, że klient używa nazwy użytkownika i hasła do uwierzytelnienia usługi fasad i fasad używa certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="cb088-125">Konfiguracja powiązania wygląda jak w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb088-125">The binding configuration looks like the following example.</span></span>  
  
```xml  
<bindings>  
  <wsHttpBinding>  
    <binding name="Binding1">  
      <security mode="Message">  
        <message clientCredentialType="UserName"/>  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="cb088-126">Usługa fasad uwierzytelnia wywołującemu, korzystając z niestandardowych `UserNamePasswordValidator` implementacji.</span><span class="sxs-lookup"><span data-stu-id="cb088-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="cb088-127">Dla celów demonstracyjnych uwierzytelnianie tylko zapewnia zgodność nazwy użytkownika wywołującego przedstawioną hasła.</span><span class="sxs-lookup"><span data-stu-id="cb088-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="cb088-128">W przypadku rzeczywistych prawdopodobnie uwierzytelnieniu użytkownika przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="cb088-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="cb088-129">Implementacja modułu sprawdzania poprawności znajduje się w `FacadeService.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="cb088-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // check that username matches password  
        if (null == userName || userName != password)  
        {  
            Console.WriteLine("Invalid username or password");  
            throw new SecurityTokenValidationException(  
                       "Invalid username or password");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cb088-130">Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi fasad.</span><span class="sxs-lookup"><span data-stu-id="cb088-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="cb088-131">To zachowanie umożliwia również konfigurowanie certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="cb088-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="FacadeServiceBehavior">  
      <!--The serviceCredentials behavior allows you to define -->  
      <!--a service certificate. -->  
      <!--A service certificate is used by the service to  -->  
      <!--authenticate itself to its clients and to provide  -->  
      <!--message protection. -->  
      <!--This configuration references the "localhost"  -->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate   
               findValue="localhost"   
               storeLocation="LocalMachine"   
               storeName="My"   
               x509FindType="FindBySubjectName" />  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
            customUserNamePasswordValidatorType=  
           "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,  
            FacadeService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="cb088-132">Ścieżki komunikacji między usługą fasad i usługi wewnętrznej bazy danych</span><span class="sxs-lookup"><span data-stu-id="cb088-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="cb088-133">Usługa fasadowym przeznaczonym do ścieżki komunikacji usługi wewnętrznej bazy danych używa `customBinding` składający się z kilku elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="cb088-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="cb088-134">To powiązanie wykonuje dwie czynności.</span><span class="sxs-lookup"><span data-stu-id="cb088-134">This binding accomplishes two things.</span></span> <span data-ttu-id="cb088-135">Uwierzytelnia fasad usługi i usługi wewnętrznej bazy danych, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="cb088-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="cb088-136">Ponadto również przesyła tożsamości obiektu wywołującego początkowej wewnątrz `Username` tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="cb088-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="cb088-137">W takim przypadku tylko początkowego wywołującego username są przesyłane do usługi zaplecza, hasło nie jest zawarte w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="cb088-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="cb088-138">Jest to spowodowane usługi zaplecza relacje zaufania usługi fasad do uwierzytelniania wywołującego przed przekazaniem żądania do niego.</span><span class="sxs-lookup"><span data-stu-id="cb088-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="cb088-139">Ponieważ usługa fasad uwierzytelnia się do usługi zaplecza, do usługi zaplecza można ufać informacji zawartych w przekazane żądanie.</span><span class="sxs-lookup"><span data-stu-id="cb088-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="cb088-140">Poniżej znajduje się Konfiguracja powiązania dla tej ścieżki komunikacji.</span><span class="sxs-lookup"><span data-stu-id="cb088-140">The following is the binding configuration for this communication path.</span></span>  
  
```xml  
<bindings>  
  <customBinding>  
    <binding name="ClientBinding">  
      <security authenticationMode="UserNameOverTransport"/>  
      <windowsStreamSecurity/>  
      <tcpTransport/>  
    </binding>  
  </customBinding>  
</bindings>  
```  
  
 <span data-ttu-id="cb088-141">[ \<Zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania zajmuje się przesyłania nazwy użytkownika i wyodrębniania początkowego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="cb088-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="cb088-142">[ \<Obiekt windowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) zajmie się uwierzytelniania usługi fasad i wewnętrznej bazy danych i komunikatów ochrony.</span><span class="sxs-lookup"><span data-stu-id="cb088-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="cb088-143">Aby przesłać żądanie, implementacji usługi fasad podać nazwę użytkownika początkowego wywołującego, umieść dla infrastruktury zabezpieczeń WCF do przekazany dalej komunikat.</span><span class="sxs-lookup"><span data-stu-id="cb088-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="cb088-144">Username początkowego wywołującego znajduje się w implementacji usługi fasad ustawiając w `ClientCredentials` właściwość w wystąpieniu serwera proxy klienta usługi fasad używa do komunikacji z usługą wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="cb088-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="cb088-145">Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest zaimplementowana w usłudze fasad.</span><span class="sxs-lookup"><span data-stu-id="cb088-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="cb088-146">Inne metody korzystają z tego samego wzorca.</span><span class="sxs-lookup"><span data-stu-id="cb088-146">Other methods use the same pattern.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="cb088-147">Jak pokazano w poprzednim kodzie, hasło nie jest ustawiona na `ClientCredentials` właściwość jest ustawiona tylko nazwy użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cb088-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="cb088-148">Infrastruktura zabezpieczeń WCF tworzy tokenu zabezpieczającego nazwy użytkownika bez hasła w tym przypadku, czyli dokładnie co jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="cb088-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="cb088-149">W usłudze zaplecza informacji zawartych w tokenie zabezpieczającym, nazwa użytkownika musi zostać uwierzytelniony.</span><span class="sxs-lookup"><span data-stu-id="cb088-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="cb088-150">Domyślnie WCF nieudane próby dostępu do mapowania użytkownika na konto systemu Windows przy użyciu podanego hasła.</span><span class="sxs-lookup"><span data-stu-id="cb088-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="cb088-151">W takim przypadku nie jest żadne hasło podane i usługi wewnętrznej bazy danych nie jest wymagane do uwierzytelniania nazwa użytkownika, ponieważ usługa fasad już zostało przeprowadzone uwierzytelnianie.</span><span class="sxs-lookup"><span data-stu-id="cb088-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="cb088-152">Aby zaimplementować tę funkcję w programie WCF, niestandardowego `UserNamePasswordValidator` jest pod warunkiem, że tylko wymusza czy nazwę użytkownika w tokenie określono i nie wykonuje żadnego dodatkowego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="cb088-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```  
public class MyUserNamePasswordValidator : UserNamePasswordValidator  
{  
    public override void Validate(string userName, string password)  
    {  
        // Ignore the password because it is empty,   
        // we trust the facade service to authenticate the client.  
        // Accept the username information here so that the   
        // application gets access to it.  
        if (null == userName)  
        {  
            Console.WriteLine("Invalid username");  
            throw new   
             SecurityTokenValidationException("Invalid username");  
        }  
    }  
}  
```  
  
 <span data-ttu-id="cb088-153">Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowania w pliku konfiguracji usługi fasad.</span><span class="sxs-lookup"><span data-stu-id="cb088-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="BackendServiceBehavior">  
      <serviceCredentials>  
        <userNameAuthentication userNamePasswordValidationMode="Custom"  
           customUserNamePasswordValidatorType=  
          "Microsoft.ServiceModel.Samples.MyUserNamePasswordValidator,   
           BackendService"/>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="cb088-154">Aby wyodrębnić informacje nazwy użytkownika i informacje o koncie usługi zaufanej fasad, korzysta z implementacji usługi wewnętrznej bazy danych `ServiceSecurityContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="cb088-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="cb088-155">Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="cb088-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```  
public string GetCallerIdentity()  
{  
    // Facade service is authenticated using Windows authentication.  
    //Its identity is accessible.  
    // On ServiceSecurityContext.Current.WindowsIdentity.  
    string facadeServiceIdentityName =   
          ServiceSecurityContext.Current.WindowsIdentity.Name;  
  
    // The client name is transmitted using Username authentication on   
    //the message level without the password  
    // using a supporting encrypted UserNameToken.  
    // Claims extracted from this supporting token are available in   
    // ServiceSecurityContext.Current.AuthorizationContext.ClaimSets   
    // collection.  
    string clientName = null;  
    foreach (ClaimSet claimSet in   
        ServiceSecurityContext.Current.AuthorizationContext.ClaimSets)  
    {  
        foreach (Claim claim in claimSet)  
        {  
            if (claim.ClaimType == ClaimTypes.Name &&   
                                   claim.Right == Rights.Identity)  
            {  
                clientName = (string)claim.Resource;  
                break;  
            }  
        }  
    }  
    if (clientName == null)  
    {  
        // In case there was no UserNameToken attached to the request.  
        // In the real world implementation the service should reject   
        // this request.  
        return "Anonymous caller via " + facadeServiceIdentityName;  
    }  
  
    return clientName + " via " + facadeServiceIdentityName;  
}  
```  
  
 <span data-ttu-id="cb088-156">Informacje o koncie usługi fasad jest wyodrębniany przy użyciu `ServiceSecurityContext.Current.WindowsIdentity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb088-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="cb088-157">Aby uzyskać dostęp do informacji o elemencie wywołującym początkowej używa usługi wewnętrznej bazy danych `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb088-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="cb088-158">Szuka `Identity` oświadczenie z typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="cb088-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="cb088-159">To oświadczenie jest generowana automatycznie przez infrastrukturę zabezpieczeń WCF z informacji zawartych w `Username` tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="cb088-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="cb088-160">Uruchomiona próbki</span><span class="sxs-lookup"><span data-stu-id="cb088-160">Running the sample</span></span>  
 <span data-ttu-id="cb088-161">Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="cb088-162">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="cb088-163">Naciśnij klawisz ENTER w oknach konsoli fasad i wewnętrznej bazy danych usługi, aby zamknąć usługi.</span><span class="sxs-lookup"><span data-stu-id="cb088-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```  
Username authentication required.  
Provide a valid machine or domain ac  
   Enter username:  
user  
   Enter password:  
****  
user via MyMachine\testaccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="cb088-164">Plik wsadowy pliku Setup.bat dołączonego przykładowy scenariusz zaufane fasady umożliwia skonfigurowanie serwera przy użyciu odpowiedniego certyfikatu do uruchamiania usługi fasad wymagające zabezpieczenia oparte na certyfikatach do samodzielnego uwierzytelnienia klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="cb088-165">Zapoznaj się z procedurą instalacji na końcu tego tematu, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="cb088-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="cb088-166">Poniżej znajdują się krótki przegląd różnych sekcji pliki wsadowe.</span><span class="sxs-lookup"><span data-stu-id="cb088-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="cb088-167">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="cb088-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="cb088-168">Następujące wiersze z pliku wsadowego pliku Setup.bat utworzenie certyfikatu serwera do użycia.</span><span class="sxs-lookup"><span data-stu-id="cb088-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="cb088-169">`%SERVER_NAME%` Zmiennej określa nazwę serwera — wartość domyślna to localhost.</span><span class="sxs-lookup"><span data-stu-id="cb088-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="cb088-170">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="cb088-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="cb088-171">Instalowanie usługi fasad certyfikatu do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="cb088-172">Następujący wiersz kopiuje usługi fasad certyfikatu w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="cb088-173">Ten krok jest wymagany, ponieważ certyfikaty generowane przez Makecert.exe nie są jawnie ufa systemu klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="cb088-174">Jeśli masz już znajdującym się w klienta zaufanego certyfikatu głównego certyfikatu — na przykład certyfikat wystawiony przez Microsoft — ten krok zapełnianie magazynu certyfikatów klienta przy użyciu certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="cb088-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cb088-175">Aby skonfigurować, kompilacji, a następnie uruchom próbki</span><span class="sxs-lookup"><span data-stu-id="cb088-175">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cb088-176">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb088-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cb088-177">Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="cb088-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="cb088-178">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="cb088-178">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="cb088-179">Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="cb088-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2.  <span data-ttu-id="cb088-180">Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki.</span><span class="sxs-lookup"><span data-stu-id="cb088-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="cb088-181">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="cb088-181">This installs all the certificates required for running the sample.</span></span>  
  
3.  <span data-ttu-id="cb088-182">Uruchom BackendService.exe \BackendService\bin katalog w oknie konsoli oddzielne</span><span class="sxs-lookup"><span data-stu-id="cb088-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4.  <span data-ttu-id="cb088-183">Uruchom FacadeService.exe \FacadeService\bin katalog w oknie konsoli oddzielne</span><span class="sxs-lookup"><span data-stu-id="cb088-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5.  <span data-ttu-id="cb088-184">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="cb088-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="cb088-185">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="cb088-185">Client activity is displayed on the client console application.</span></span>  
  
6.  <span data-ttu-id="cb088-186">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="cb088-186">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/library/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="cb088-187">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="cb088-187">To clean up after the sample</span></span>  
  
1.  <span data-ttu-id="cb088-188">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="cb088-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb088-189">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="cb088-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb088-190">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="cb088-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cb088-191">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="cb088-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb088-192">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="cb088-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
  
## <a name="see-also"></a><span data-ttu-id="cb088-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cb088-193">See Also</span></span>
