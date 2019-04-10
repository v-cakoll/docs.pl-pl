---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 4921b2746b9df362a0bb3e6048602d41f3f2faaf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59346161"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="ed798-102">Zaufana usługa fasady</span><span class="sxs-lookup"><span data-stu-id="ed798-102">Trusted Facade Service</span></span>
<span data-ttu-id="ed798-103">Ten przykładowy scenariusz pokazuje, jak przepływ informacji o tożsamości wywołującego z jednej usługi do innego za pomocą usługi Windows Communication Foundation (WCF) infrastruktura zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ed798-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="ed798-104">Jest wspólny wzorzec projektowania, aby udostępnić funkcje udostępniane przez usługi w sieci publicznej przy użyciu usługi fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="ed798-105">Usługa fasady zazwyczaj znajduje się w sieci obwodowej (znany także jako DMZ, strefa zdemilitaryzowana i podsieć ekranowana) i komunikuje się za pomocą usługi zaplecza, która implementuje logikę biznesową i ma dostęp do danych wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="ed798-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="ed798-106">Kanał komunikacyjny między usługą fasady i usługą zaplecza przechodzi przez zaporę i jest zwykle ograniczony tylko do jednego celu.</span><span class="sxs-lookup"><span data-stu-id="ed798-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="ed798-107">W tym przykładzie składa się z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="ed798-107">This sample consists of the following components:</span></span>  
  
-   <span data-ttu-id="ed798-108">Kalkulator klienta</span><span class="sxs-lookup"><span data-stu-id="ed798-108">Calculator client</span></span>  
  
-   <span data-ttu-id="ed798-109">Usługa fasady Kalkulator</span><span class="sxs-lookup"><span data-stu-id="ed798-109">Calculator façade service</span></span>  
  
-   <span data-ttu-id="ed798-110">Kalkulator usługi zaplecza</span><span class="sxs-lookup"><span data-stu-id="ed798-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="ed798-111">Usługa fasady jest odpowiedzialna za weryfikowanie żądania i uwierzytelniania obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ed798-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="ed798-112">Po pomyślnym uwierzytelnieniu i sprawdzania poprawności przesyła żądanie do usługi zaplecza przy użyciu kanału komunikacyjnego kontrolowany w sieci obwodowej z siecią wewnętrzną.</span><span class="sxs-lookup"><span data-stu-id="ed798-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="ed798-113">Jako część żądania przekazywane usługa fasady zawiera informacje o tożsamości elementu wywołującego, tak aby usługi wewnętrznej bazy danych można użyć tych informacji w zakresie przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="ed798-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="ed798-114">Tożsamość obiektu wywołującego jest przesyłane przy użyciu `Username` tokenu zabezpieczającego w komunikacie `Security` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="ed798-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="ed798-115">W przykładzie użyto infrastruktura zabezpieczeń programu WCF do przesyłania i wyodrębnić te informacje z `Security` nagłówka.</span><span class="sxs-lookup"><span data-stu-id="ed798-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed798-116">Usługi wewnętrznej bazy danych i relacje zaufania usługi fasady do uwierzytelniania obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ed798-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="ed798-117">W związku z tym usługa zaplecza nie uwierzytelnia obiektu wywołującego ponownie; informacje o tożsamości, usługa fasady w żądaniu przekazywane go używa.</span><span class="sxs-lookup"><span data-stu-id="ed798-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="ed798-118">Ze względu na tę relację zaufania usługi wewnętrznej bazy danych muszą zostać uwierzytelnione Usługa fasady, aby upewnić się, że przekazany dalej komunikat pochodzi z zaufanego źródła — w tym przypadku usługa fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="ed798-119">Implementacja</span><span class="sxs-lookup"><span data-stu-id="ed798-119">Implementation</span></span>  
 <span data-ttu-id="ed798-120">W tym przykładzie istnieją dwie ścieżki komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ed798-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="ed798-121">Najpierw jest między klientem a usługa fasady drugą jest wartość między usługą fasady i usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="ed798-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="ed798-122">Ścieżka komunikacji między klientem a usługą fasady</span><span class="sxs-lookup"><span data-stu-id="ed798-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="ed798-123">Korzysta z klienta do ścieżki komunikacji usługi fasady `wsHttpBinding` z `UserName` typu poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="ed798-124">Oznacza to, że klient używa nazwy użytkownika i hasło do uwierzytelniania usługa fasady i usługa fasady używa certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="ed798-125">Konfiguracja powiązania wygląda podobnie jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ed798-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="ed798-126">Usługa fasady uwierzytelnia wywołującemu, korzystając z niestandardowego `UserNamePasswordValidator` implementacji.</span><span class="sxs-lookup"><span data-stu-id="ed798-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="ed798-127">Dla celów demonstracyjnych uwierzytelniania tylko zapewnia zgodność nazwy użytkownika wywołującego prezentowane hasła.</span><span class="sxs-lookup"><span data-stu-id="ed798-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="ed798-128">W rzeczywistych sytuacji prawdopodobnie uwierzytelnieniu użytkownika przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ed798-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="ed798-129">Implementacja modułu sprawdzania poprawności, który znajduje się w `FacadeService.cs` pliku.</span><span class="sxs-lookup"><span data-stu-id="ed798-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
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
  
 <span data-ttu-id="ed798-130">Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowanie w pliku konfiguracji usługi fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="ed798-131">To zachowanie umożliwia również konfigurowanie certyfikacie X.509.</span><span class="sxs-lookup"><span data-stu-id="ed798-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="ed798-132">Ścieżka komunikacji między usługą fasady i usługi zaplecza</span><span class="sxs-lookup"><span data-stu-id="ed798-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="ed798-133">Usługa fasady do ścieżki komunikacji usługi wewnętrznej bazy danych używa `customBinding` składający się z kilku elementów powiązania.</span><span class="sxs-lookup"><span data-stu-id="ed798-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="ed798-134">Dwie rzeczy w ramach tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="ed798-134">This binding accomplishes two things.</span></span> <span data-ttu-id="ed798-135">Usługa ta uwierzytelnia usługa fasady i usługi zaplecza, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="ed798-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="ed798-136">Ponadto również przesyła tożsamości elementu wywołującego początkowej wewnątrz `Username` tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ed798-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="ed798-137">W tym przypadku tylko nazwy użytkownika wywołującego początkowej są przesyłane do usługi zaplecza, hasło nie znajduje się w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="ed798-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="ed798-138">Jest to spowodowane usługi wewnętrznej bazy danych i relacje zaufania usługi fasady do uwierzytelniania obiektu wywołującego przed przekazaniem żądania do niego.</span><span class="sxs-lookup"><span data-stu-id="ed798-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="ed798-139">Ponieważ usługa fasady uwierzytelnia do usługi zaplecza, usługi zaplecza mogą ufać informacji zawartych w żądaniu przesyłanych dalej.</span><span class="sxs-lookup"><span data-stu-id="ed798-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="ed798-140">Poniżej znajduje się Konfiguracja powiązania dla tej ścieżki komunikacji.</span><span class="sxs-lookup"><span data-stu-id="ed798-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="ed798-141">[ \<Zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element powiązania dba o przesyłania nazwy użytkownika i wyodrębniania początkowego obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="ed798-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="ed798-142">[ \<WindowsStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) obsługi uwierzytelniania usługi frontonu i wewnętrznej bazy danych i ochrona wiadomości.</span><span class="sxs-lookup"><span data-stu-id="ed798-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="ed798-143">Do przesyłania żądania, fasady implementacji usługi należy podać username początkowego wywołującego, tak że infrastruktura zabezpieczeń programu WCF można umieścić ten przekazany dalej komunikat.</span><span class="sxs-lookup"><span data-stu-id="ed798-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="ed798-144">Username początkowego wywołującego znajduje się w implementacji usługi fasady ustawiając w `ClientCredentials` właściwość w wystąpieniu serwera proxy klienta usługi fasady używa do komunikowania się z usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="ed798-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="ed798-145">Poniższy kod przedstawia sposób `GetCallerIdentity` metoda jest implementowana w usłudze fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="ed798-146">Inne metody używają tego samego wzorca.</span><span class="sxs-lookup"><span data-stu-id="ed798-146">Other methods use the same pattern.</span></span>  
  
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
  
 <span data-ttu-id="ed798-147">Jak pokazano w poprzednim kodzie, hasło nie jest ustawiona na `ClientCredentials` , tylko nazwy użytkownika ustawiono właściwość.</span><span class="sxs-lookup"><span data-stu-id="ed798-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="ed798-148">Infrastruktura zabezpieczeń WCF tworzy token zabezpieczający nazwy użytkownika bez hasła w tym przypadku, co jest dokładnie co jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="ed798-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="ed798-149">W usłudze zaplecza informacji zawartych w tokenie zabezpieczającym nazwa użytkownika musi zostać uwierzytelnione.</span><span class="sxs-lookup"><span data-stu-id="ed798-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="ed798-150">Domyślnie zabezpieczeń WCF próbuje mapowanie użytkownika do konta Windows przy użyciu podanego hasła.</span><span class="sxs-lookup"><span data-stu-id="ed798-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="ed798-151">W tym przypadku jest nie podano hasła i usługi wewnętrznej bazy danych nie jest wymagane do uwierzytelniania nazwy użytkownika, ponieważ uwierzytelnianie zostało już wykonane przez usługa fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="ed798-152">Aby zaimplementować tę funkcję w programie WCF, niestandardowe `UserNamePasswordValidator` zostanie podana, tylko wymusza, że nazwa użytkownika jest określona w tokenie i niewykonywanie żadnego dodatkowego uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="ed798-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
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
  
 <span data-ttu-id="ed798-153">Niestandardowy moduł sprawdzania poprawności jest skonfigurowana do używania wewnątrz `serviceCredentials` zachowanie w pliku konfiguracji usługi fasady.</span><span class="sxs-lookup"><span data-stu-id="ed798-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="ed798-154">Aby wyodrębnić informacje nazwy użytkownika i informacje o koncie usługi zaufanej fasady, korzysta z implementacji usługi zaplecza `ServiceSecurityContext` klasy.</span><span class="sxs-lookup"><span data-stu-id="ed798-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="ed798-155">Poniższy kod przedstawia sposób, w jaki `GetCallerIdentity` metoda jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="ed798-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
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
  
 <span data-ttu-id="ed798-156">Informacje o koncie usługi fasady jest wyodrębniany przy użyciu `ServiceSecurityContext.Current.WindowsIdentity` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed798-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="ed798-157">Aby uzyskać dostęp do informacji o obiekcie wywołującym początkowej, używa usługi wewnętrznej bazy danych `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed798-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="ed798-158">Szuka `Identity` oświadczenie z typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="ed798-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="ed798-159">To oświadczenie jest generowany automatycznie przez infrastrukturę zabezpieczeń programu WCF z informacji zawartych w `Username` tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="ed798-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="ed798-160">Działa aplikacja przykładowa</span><span class="sxs-lookup"><span data-stu-id="ed798-160">Running the sample</span></span>  
 <span data-ttu-id="ed798-161">Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="ed798-162">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="ed798-163">Można naciśnij klawisz ENTER w oknach konsoli usługi frontonu i zaplecza, aby zamknąć usługi.</span><span class="sxs-lookup"><span data-stu-id="ed798-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
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
  
 <span data-ttu-id="ed798-164">Plik wsadowy Setup.bat jest dołączone do zaufanych fasady przykładowy scenariusz umożliwia skonfigurowanie serwera przy użyciu certyfikatu odpowiedniego do uruchamiania usługi fasady wymagającego opartego na certyfikatach zabezpieczeń, aby uwierzytelniać się klient.</span><span class="sxs-lookup"><span data-stu-id="ed798-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="ed798-165">Zapoznaj się z procedurą konfiguracji na końcu tego tematu, aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="ed798-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="ed798-166">Poniżej zawiera krótkie omówienie różnych sekcji w plikach wsadowych.</span><span class="sxs-lookup"><span data-stu-id="ed798-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
-   <span data-ttu-id="ed798-167">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="ed798-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="ed798-168">Następujące wiersze z pliku wsadowego Setup.bat jest utworzenie certyfikatu serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="ed798-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="ed798-169">`%SERVER_NAME%` Zmienna Określa nazwę serwera — wartość domyślna to hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="ed798-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="ed798-170">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="ed798-170">The certificate is stored in the LocalMachine store.</span></span>  
  
-   <span data-ttu-id="ed798-171">Instalowanie usługi fasady certyfikat do magazynu zaufanych certyfikatów klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="ed798-172">Następujący wiersz kopiuje usługa fasady certyfikat w magazynie zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="ed798-173">Ten krok jest wymagany, ponieważ generowaną przez Makecert.exe certyfikaty nie są niejawnie zaufany przez system klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="ed798-174">Jeśli masz już certyfikat, który jest ścieżką w klienta zaufanego certyfikatu głównego — na przykład certyfikat wystawiony przez Microsoft — w tym kroku zapełnianie magazynu certyfikatów klienta z certyfikatu serwera nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="ed798-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ed798-175">Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej</span><span class="sxs-lookup"><span data-stu-id="ed798-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="ed798-176">Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ed798-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="ed798-177">Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="ed798-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="ed798-178">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="ed798-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="ed798-179">Upewnij się, że ścieżka zawiera folder, w którym znajduje się Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="ed798-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="ed798-180">Uruchom Setup.bat jest z poziomu folderu instalacji przykładowej.</span><span class="sxs-lookup"><span data-stu-id="ed798-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="ed798-181">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="ed798-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="ed798-182">Uruchom BackendService.exe \BackendService\bin katalog w oknie konsoli oddzielne</span><span class="sxs-lookup"><span data-stu-id="ed798-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="ed798-183">Uruchom FacadeService.exe \FacadeService\bin katalog w oknie konsoli oddzielne</span><span class="sxs-lookup"><span data-stu-id="ed798-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="ed798-184">Uruchom Client.exe z \client\bin.</span><span class="sxs-lookup"><span data-stu-id="ed798-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="ed798-185">Aktywność klienta jest wyświetlany w aplikacji konsolowej klienta.</span><span class="sxs-lookup"><span data-stu-id="ed798-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="ed798-186">Jeśli klient i usługa nie mogła nawiązać połączenia, zobacz [Rozwiązywanie problemów z porady dotyczące przykłady WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="ed798-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="ed798-187">Aby wyczyścić zasoby po próbki</span><span class="sxs-lookup"><span data-stu-id="ed798-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="ed798-188">Uruchom Cleanup.bat w folderze samples, po zakończeniu działa aplikacja przykładowa.</span><span class="sxs-lookup"><span data-stu-id="ed798-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ed798-189">Przykłady może już być zainstalowany na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ed798-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ed798-190">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="ed798-190">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ed798-191">Jeśli ten katalog nie istnieje, przejdź do strony [Windows Communication Foundation (WCF) i przykłady Windows Workflow Foundation (WF) dla platformy .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) do pobierania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykładów.</span><span class="sxs-lookup"><span data-stu-id="ed798-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ed798-192">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ed798-192">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
