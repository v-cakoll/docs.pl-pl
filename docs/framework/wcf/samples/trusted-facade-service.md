---
title: Zaufana usługa fasady
ms.date: 03/30/2017
ms.assetid: c34d1a8f-e45e-440b-a201-d143abdbac38
ms.openlocfilehash: 17901b7a68d4701287d02bc7ee3174683e777fd1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143749"
---
# <a name="trusted-facade-service"></a><span data-ttu-id="9a2dd-102">Zaufana usługa fasady</span><span class="sxs-lookup"><span data-stu-id="9a2dd-102">Trusted Facade Service</span></span>
<span data-ttu-id="9a2dd-103">W tym przykładzie scenariusza pokazano, jak przepływ informacji o tożsamości wywołującego z jednej usługi do drugiej przy użyciu infrastruktury zabezpieczeń Programu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9a2dd-103">This scenario sample demonstrates how to flow caller's identity information from one service to another using Windows Communication Foundation (WCF) security infrastructure.</span></span>  
  
 <span data-ttu-id="9a2dd-104">Jest to typowy wzorzec projektu, aby udostępnić funkcje udostępniane przez usługę do sieci publicznej za pomocą usługi fasadowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-104">It is a common design pattern to expose the functionality provided by a service to the public network using a façade service.</span></span> <span data-ttu-id="9a2dd-105">Usługa fasadowa zazwyczaj znajduje się w sieci obwodowej (znanej również jako STREFA DMZ, strefa zdemilitaryzowana i podsieć ekranowana) i komunikuje się z usługą zaplecza, która implementuje logikę biznesową i ma dostęp do danych wewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-105">The façade service typically resides in the perimeter network (also known as DMZ, demilitarized zone, and screened subnet) and communicates with a backend service that implements the business logic and has access to internal data.</span></span> <span data-ttu-id="9a2dd-106">Kanał komunikacji między usługą elewacji a usługą wewnętrznej bazy danych przechodzi przez zaporę i jest zwykle ograniczony tylko do jednego celu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-106">The communication channel between the façade service and the backend service goes through a firewall and is usually limited for a single purpose only.</span></span>  
  
 <span data-ttu-id="9a2dd-107">Ten przykład składa się z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="9a2dd-107">This sample consists of the following components:</span></span>  
  
- <span data-ttu-id="9a2dd-108">Klient kalkulatora</span><span class="sxs-lookup"><span data-stu-id="9a2dd-108">Calculator client</span></span>  
  
- <span data-ttu-id="9a2dd-109">Usługa elewacji kalkulatora</span><span class="sxs-lookup"><span data-stu-id="9a2dd-109">Calculator façade service</span></span>  
  
- <span data-ttu-id="9a2dd-110">Usługa zaplecza kalkulatora</span><span class="sxs-lookup"><span data-stu-id="9a2dd-110">Calculator backend service</span></span>  
  
 <span data-ttu-id="9a2dd-111">Usługa fasady jest odpowiedzialna za sprawdzanie poprawności żądania i uwierzytelnianie rozmówcy.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-111">The façade service is responsible for validating the request and authenticating the caller.</span></span> <span data-ttu-id="9a2dd-112">Po pomyślnym uwierzytelnieniu i weryfikacji przekazuje żądanie do usługi wewnętrznej bazy danych przy użyciu kontrolowanego kanału komunikacyjnego z sieci obwodowej do sieci wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-112">After successful authentication and validation, it forwards the request to the backend service using the controlled communication channel from the perimeter network to the internal network.</span></span> <span data-ttu-id="9a2dd-113">W ramach żądania przekazanego usługa fasadowa zawiera informacje o tożsamości wywołującego, dzięki czemu usługa zaplecza może używać tych informacji w jego przetwarzaniu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-113">As a part of the forwarded request, the façade service includes information about the caller's identity so that the backend service can use this information in its processing.</span></span> <span data-ttu-id="9a2dd-114">Tożsamość wywołującego jest przesyłany `Username` przy użyciu tokenu zabezpieczającego wewnątrz nagłówka wiadomości. `Security`</span><span class="sxs-lookup"><span data-stu-id="9a2dd-114">The caller's identity is transmitted using a `Username` security token inside the message `Security` header.</span></span> <span data-ttu-id="9a2dd-115">Przykład używa infrastruktury zabezpieczeń WCF do przesyłania i `Security` wyodrębniania tych informacji z nagłówka.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-115">The sample uses the WCF security infrastructure to transmit and extract this information from the `Security` header.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9a2dd-116">Usługa wewnętrznej bazy danych ufa usłudze fasadowej w celu uwierzytelnienia wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-116">The backend service trusts the façade service to authenticate the caller.</span></span> <span data-ttu-id="9a2dd-117">Z tego powodu usługa wewnętrznej bazy danych nie uwierzytelnia obiektu wywołującego ponownie; wykorzystuje informacje o tożsamości podane przez usługę fasadową w przesłanym żądaniu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-117">Because of this, the backend service does not authenticate the caller again; it uses the identity information provided by the façade service in the forwarded request.</span></span> <span data-ttu-id="9a2dd-118">Z powodu tej relacji zaufania usługa zaplecza musi uwierzytelnić usługę fasadową, aby upewnić się, że przekazywany komunikat pochodzi z zaufanego źródła — w tym przypadku usługi fasadowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-118">Because of this trust relationship, the backend service must authenticate the façade service to ensure that the forwarded message comes from a trusted source - in this case, the façade service.</span></span>  
  
## <a name="implementation"></a><span data-ttu-id="9a2dd-119">Wdrażanie</span><span class="sxs-lookup"><span data-stu-id="9a2dd-119">Implementation</span></span>  
 <span data-ttu-id="9a2dd-120">Istnieją dwie ścieżki komunikacji w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-120">There are two communication paths in this sample.</span></span> <span data-ttu-id="9a2dd-121">Pierwszy znajduje się między klientem a usługą elewacji, drugi znajduje się między serwisem elewacji a usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-121">First is between the client and the façade service, the second is between the façade service and the backend service.</span></span>  
  
### <a name="communication-path-between-client-and-faade-service"></a><span data-ttu-id="9a2dd-122">Ścieżka komunikacji między obsługą klienta i fasady</span><span class="sxs-lookup"><span data-stu-id="9a2dd-122">Communication Path between Client and Façade Service</span></span>  
 <span data-ttu-id="9a2dd-123">Klient do ścieżki komunikacji usługi elewacji `wsHttpBinding` `UserName` używa z typem poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-123">The client to the façade service communication path uses `wsHttpBinding` with a `UserName` client credential type.</span></span> <span data-ttu-id="9a2dd-124">Oznacza to, że klient używa nazwy użytkownika i hasła do uwierzytelniania w usłudze fasadowej, a usługa fasadowa używa certyfikatu X.509 do uwierzytelniania klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-124">This means that the client uses username and password to authenticate to the façade service and the façade service uses X.509 certificate to authenticate to the client.</span></span> <span data-ttu-id="9a2dd-125">Konfiguracja powiązania wygląda jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-125">The binding configuration looks like the following example.</span></span>  
  
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
  
 <span data-ttu-id="9a2dd-126">Usługa fasady uwierzytelnia wywołującego przy `UserNamePasswordValidator` użyciu implementacji niestandardowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-126">The façade service authenticates the caller using custom `UserNamePasswordValidator` implementation.</span></span> <span data-ttu-id="9a2dd-127">W celach demonstracyjnych uwierzytelnianie zapewnia tylko, że nazwa użytkownika wywołującego jest zgodna z prezentowanym hasłem.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-127">For demonstration purposes, the authentication only ensures that the caller's username matches the presented password.</span></span> <span data-ttu-id="9a2dd-128">W sytuacji rzeczywistych użytkownik jest prawdopodobnie uwierzytelniony przy użyciu usługi Active Directory lub niestandardowego dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-128">In the real world situation, the user is probably authenticated using Active Directory or custom ASP.NET Membership provider.</span></span> <span data-ttu-id="9a2dd-129">Implementacja walidatora `FacadeService.cs` znajduje się w pliku.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-129">The validator implementation resides in `FacadeService.cs` file.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="9a2dd-130">Niestandardowy walidator jest skonfigurowany `serviceCredentials` do użycia wewnątrz zachowania w pliku konfiguracyjnym usługi fasadowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-130">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span> <span data-ttu-id="9a2dd-131">To zachowanie jest również używane do konfigurowania certyfikatu X.509 usługi.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-131">This behavior is also used to configure the service's X.509 certificate.</span></span>  
  
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
  
### <a name="communication-path-between-faade-service-and-backend-service"></a><span data-ttu-id="9a2dd-132">Ścieżka komunikacji między usługą fasadową a usługą zaplecza</span><span class="sxs-lookup"><span data-stu-id="9a2dd-132">Communication Path between Façade Service and Backend Service</span></span>  
 <span data-ttu-id="9a2dd-133">Usługa elewacji do ścieżki komunikacji usługi wewnętrznej `customBinding` bazy danych używa, który składa się z kilku elementów wiązania.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-133">The façade service to the backend service communication path uses a `customBinding` that consists of several binding elements.</span></span> <span data-ttu-id="9a2dd-134">To powiązanie osiąga dwie rzeczy.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-134">This binding accomplishes two things.</span></span> <span data-ttu-id="9a2dd-135">Uwierzytelnia usługę elewacji i usługę zaplecza, aby upewnić się, że komunikacja jest bezpieczna i pochodzi z zaufanego źródła.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-135">It authenticates the façade service and backend service to ensure that the communication is secure and is coming from a trusted source.</span></span> <span data-ttu-id="9a2dd-136">Ponadto przesyła również tożsamość początkowego obiektu wywołującego `Username` wewnątrz tokenu zabezpieczającego.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-136">Additionally, it also transmits the initial caller's identity inside the `Username` security token.</span></span> <span data-ttu-id="9a2dd-137">W takim przypadku tylko początkowa nazwa użytkownika wywołującego jest przesyłana do usługi wewnętrznej bazy danych, hasło nie jest zawarte w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-137">In this case, only the initial caller's username is transmitted to the backend service, the password is not included in the message.</span></span> <span data-ttu-id="9a2dd-138">Dzieje się tak, ponieważ usługa wewnętrznej bazy danych ufa usłudze fasadowej w celu uwierzytelnienia wywołującego przed przekazaniem żądania do niego.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-138">This is because the backend service trusts the façade service to authenticate the caller before forwarding the request to it.</span></span> <span data-ttu-id="9a2dd-139">Ponieważ usługa fasadowa uwierzytelnia się w usłudze wewnętrznej bazy danych, usługa zaplecza może ufać informacjom zawartym w żądaniu przesyłania dalej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-139">Because the façade service authenticates itself to the backend service, the backend service can trust the information contained in the forwarded request.</span></span>  
  
 <span data-ttu-id="9a2dd-140">Poniżej przedstawiono konfigurację powiązania dla tej ścieżki komunikacji.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-140">The following is the binding configuration for this communication path.</span></span>  
  
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
  
 <span data-ttu-id="9a2dd-141">Element wiązania [ \<zabezpieczeń>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) zajmuje się przesyłaniem i wyodrębnianiem nazwy użytkownika początkowego wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-141">The [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) binding element takes care of the initial caller's username transmission and extraction.</span></span> <span data-ttu-id="9a2dd-142">[ \<WindowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) i [ \<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) dbać o usługi elewacji i wewnętrznej bazy danych oraz ochrony wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-142">The [\<windowsStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/windowsstreamsecurity.md) and [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) take care of authenticating façade and backend services and message protection.</span></span>  
  
 <span data-ttu-id="9a2dd-143">Aby przesłać dalej żądanie, implementacja usługi fasadowej musi podać nazwę użytkownika początkowego wywołującego, aby infrastruktura zabezpieczeń WCF mogła umieścić to w wiadomości przesyłanej dalej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-143">To forward the request, the façade service implementation must provide the initial caller's username so that WCF security infrastructure can place this into the forwarded message.</span></span> <span data-ttu-id="9a2dd-144">Nazwa użytkownika początkowego obiektu wywołującego jest dostępna w implementacji `ClientCredentials` usługi fasadowej, ustawiając ją we właściwości w wystąpieniu serwera proxy klienta, którego usługa fasadowa używa do komunikowania się z usługą zaplecza.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-144">The initial caller's username is provided in the façade service implementation by setting it in the `ClientCredentials` property on the client proxy instance that façade service uses to communicate with the backend service.</span></span>  
  
 <span data-ttu-id="9a2dd-145">Poniższy kod `GetCallerIdentity` pokazuje, jak metoda jest implementowana w usłudze fasadowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-145">The following code shows how `GetCallerIdentity` method is implemented on the façade service.</span></span> <span data-ttu-id="9a2dd-146">Inne metody używają tego samego wzorca.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-146">Other methods use the same pattern.</span></span>  
  
```csharp  
public string GetCallerIdentity()  
{  
    CalculatorClient client = new CalculatorClient();  
    client.ClientCredentials.UserName.UserName = ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    string result = client.GetCallerIdentity();  
    client.Close();  
    return result;  
}  
```  
  
 <span data-ttu-id="9a2dd-147">Jak pokazano w poprzednim kodzie, hasło `ClientCredentials` nie jest ustawione na właściwości, tylko nazwa użytkownika jest ustawiona.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-147">As shown in the previous code, the password is not set on the `ClientCredentials` property, only the username is set.</span></span> <span data-ttu-id="9a2dd-148">Infrastruktura zabezpieczeń WCF tworzy token zabezpieczający nazwy użytkownika bez hasła w tym przypadku, co jest dokładnie to, co jest wymagane w tym scenariuszu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-148">WCF security infrastructure creates a username security token without a password in this case, which is exactly what is required in this scenario.</span></span>  
  
 <span data-ttu-id="9a2dd-149">W usłudze wewnętrznej bazy danych informacje zawarte w tokenie zabezpieczającym nazwy użytkownika muszą być uwierzytelnione.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-149">On the backend service, the information contained in the username security token must be authenticated.</span></span> <span data-ttu-id="9a2dd-150">Domyślnie zabezpieczenia WCF próbują zamapować użytkownika na konto systemu Windows przy użyciu podanego hasła.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-150">By default, WCF security attempts to map the user to a Windows account using the provided password.</span></span> <span data-ttu-id="9a2dd-151">W takim przypadku nie ma hasła i usługa wewnętrznej bazy danych nie jest wymagana do uwierzytelniania nazwy użytkownika, ponieważ uwierzytelnianie zostało już wykonane przez usługę fasadową.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-151">In this case, there is no password provided and the backend service is not required to authenticate the username because the authentication was already performed by the façade service.</span></span> <span data-ttu-id="9a2dd-152">Aby zaimplementować tę funkcję `UserNamePasswordValidator` w WCF, niestandardowe jest pod warunkiem, że tylko wymusza, że nazwa użytkownika jest określona w tokenie i nie wykonuje żadnych dodatkowych uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-152">To implement this functionality in WCF, a custom `UserNamePasswordValidator` is provided that only enforces that a username is specified in the token and does not perform any additional authentication.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="9a2dd-153">Niestandardowy walidator jest skonfigurowany `serviceCredentials` do użycia wewnątrz zachowania w pliku konfiguracyjnym usługi fasadowej.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-153">The custom validator is configured to be used inside the `serviceCredentials` behavior in the façade service configuration file.</span></span>  
  
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
  
 <span data-ttu-id="9a2dd-154">Aby wyodrębnić informacje o nazwie użytkownika i informacje o zaufanego konta `ServiceSecurityContext` usługi fasadowej, implementacja usługi wewnętrznej bazy danych używa klasy.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-154">To extract the username information and information about the trusted façade service account, the backend service implementation uses the `ServiceSecurityContext` class.</span></span> <span data-ttu-id="9a2dd-155">Poniższy kod pokazuje, `GetCallerIdentity` jak metoda jest implementowana.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-155">The following code shows how the `GetCallerIdentity` method is implemented.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="9a2dd-156">Informacje o koncie usługi elewacyjnej są pobierane za pomocą `ServiceSecurityContext.Current.WindowsIdentity` obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-156">The façade service account information is extracted using the `ServiceSecurityContext.Current.WindowsIdentity` property.</span></span> <span data-ttu-id="9a2dd-157">Aby uzyskać dostęp do informacji o wywołaniu początkowym usługa wewnętrznej bazy danych używa `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` właściwości.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-157">To access the information about the initial caller the backend service uses the `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` property.</span></span> <span data-ttu-id="9a2dd-158">Szuka `Identity` roszczenia z typem `Name`.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-158">It looks for an `Identity` claim with a type `Name`.</span></span> <span data-ttu-id="9a2dd-159">To oświadczenie jest automatycznie generowane przez infrastrukturę zabezpieczeń WCF na podstawie informacji zawartych w tokenie zabezpieczającym. `Username`</span><span class="sxs-lookup"><span data-stu-id="9a2dd-159">This claim is automatically generated by WCF security infrastructure from the information contained in the `Username` security token.</span></span>  
  
## <a name="running-the-sample"></a><span data-ttu-id="9a2dd-160">Uruchamianie przykładowej aplikacji</span><span class="sxs-lookup"><span data-stu-id="9a2dd-160">Running the sample</span></span>  
 <span data-ttu-id="9a2dd-161">Po uruchomieniu próbki żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-161">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="9a2dd-162">Naciśnij klawisz ENTER w oknie klienta, aby zamknąć klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-162">Press ENTER in the client window to shut down the client.</span></span> <span data-ttu-id="9a2dd-163">Aby wyłączyć usługi, można nacisnąć klawisz ENTER w oknach konsoli elewacji i konsoli wewnętrznej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-163">You can press ENTER in the façade and backend service console windows to shut down the services.</span></span>  
  
```console  
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
  
 <span data-ttu-id="9a2dd-164">Plik wsadowy Setup.bat dołączony do przykładu scenariusza Zaufana fasada umożliwia skonfigurowanie serwera z odpowiednim certyfikatem do uruchomienia usługi fasadowej, która wymaga zabezpieczeń opartych na certyfikatach do uwierzytelniania się w kliencie.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-164">The Setup.bat batch file included with the Trusted Facade scenario sample enables you to configure the server with a relevant certificate to run the façade service that requires certificate-based security to authenticate itself to the client.</span></span> <span data-ttu-id="9a2dd-165">Szczegółowe informacje można znaleźć w procedurze konfiguracji na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-165">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="9a2dd-166">Poniżej przedstawiono krótkie omówienie różnych sekcji plików wsadowych.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-166">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="9a2dd-167">Tworzenie certyfikatu serwera.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-167">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="9a2dd-168">Następujące wiersze z pliku wsadowego Setup.bat tworzą certyfikat serwera, który ma być używany.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-168">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```console  
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="9a2dd-169">Zmienna `%SERVER_NAME%` określa nazwę serwera - wartością domyślną jest localhost.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-169">The `%SERVER_NAME%` variable specifies the server name - the default value is localhost.</span></span> <span data-ttu-id="9a2dd-170">Certyfikat jest przechowywany w magazynie LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-170">The certificate is stored in the LocalMachine store.</span></span>  
  
- <span data-ttu-id="9a2dd-171">Instalowanie certyfikatu usługi fasadowej w magazynie certyfikatów zaufanych klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-171">Installing the façade service's certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="9a2dd-172">Poniższy wiersz kopiuje certyfikat usługi fasadowej do magazynu zaufanych osób klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-172">The following line copies the façade service's certificate into the client trusted people store.</span></span> <span data-ttu-id="9a2dd-173">Ten krok jest wymagany, ponieważ certyfikaty generowane przez plik Makecert.exe nie są niejawnie zaufane przez system kliencki.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-173">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="9a2dd-174">Jeśli masz już certyfikat zakorzeniony w zaufanym certyfikacie głównym klienta — na przykład certyfikat wystawiony przez firmę Microsoft — ten etap wypełniania magazynu certyfikatów klienta certyfikatem serwera nie jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-174">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9a2dd-175">Aby skonfigurować, skompilować i uruchomić próbkę</span><span class="sxs-lookup"><span data-stu-id="9a2dd-175">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="9a2dd-176">Upewnij się, że wykonano [procedurę jednorazowej instalacji dla przykładów fundacji komunikacji systemu Windows](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a2dd-176">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="9a2dd-177">Aby utworzyć wersję C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami w [tworzenie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9a2dd-177">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="9a2dd-178">Aby uruchomić próbkę na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="9a2dd-178">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="9a2dd-179">Upewnij się, że ścieżka zawiera folder, w którym znajduje się plik Makecert.exe.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-179">Ensure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="9a2dd-180">Uruchom plik Setup.bat z przykładowego folderu instalacyjnego.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-180">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="9a2dd-181">Spowoduje to zainstalowanie wszystkich certyfikatów wymaganych do uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-181">This installs all the certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="9a2dd-182">Uruchamianie programu BackendService.exe z katalogu \BackendService\bin w osobnym oknie konsoli</span><span class="sxs-lookup"><span data-stu-id="9a2dd-182">Launch the BackendService.exe from \BackendService\bin directory in a separate console window</span></span>  
  
4. <span data-ttu-id="9a2dd-183">Uruchamianie programu FacadeService.exe z katalogu \FacadeService\bin w osobnym oknie konsoli</span><span class="sxs-lookup"><span data-stu-id="9a2dd-183">Launch the FacadeService.exe from \FacadeService\bin directory in a separate console window</span></span>  
  
5. <span data-ttu-id="9a2dd-184">Uruchom program Client.exe z pliku \client\bin.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-184">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="9a2dd-185">Aktywność klienta jest wyświetlana w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-185">Client activity is displayed on the client console application.</span></span>  
  
6. <span data-ttu-id="9a2dd-186">Jeśli klient i usługa nie mogą się komunikować, zobacz [Porady dotyczące rozwiązywania problemów dla przykładów WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="9a2dd-186">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="9a2dd-187">Aby oczyścić po próbce</span><span class="sxs-lookup"><span data-stu-id="9a2dd-187">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="9a2dd-188">Uruchom Cleanup.bat w folderze przykłady po zakończeniu uruchamiania próbki.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-188">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9a2dd-189">Próbki mogą być już zainstalowane na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-189">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9a2dd-190">Przed kontynuowaniem sprawdź następujący (domyślny) katalog.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-190">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="9a2dd-191">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) Przykłady dla platformy .NET Framework 4,](https://www.microsoft.com/download/details.aspx?id=21459) aby pobrać wszystkie Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] przykłady.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-191">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9a2dd-192">Ten przykład znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9a2dd-192">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\TrustedFacade`  
