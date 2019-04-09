---
title: 'Instrukcje: używanie dostawcy członkostwa platformy ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: df86f87bfc2456d77e3c1ee209cb8b4c61f53b21
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140611"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="d742e-102">Instrukcje: używanie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="d742e-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="d742e-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy członkostwa jest funkcją, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych użytkowników kombinacji nazwy i hasła.</span><span class="sxs-lookup"><span data-stu-id="d742e-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="d742e-104">Za pomocą tej funkcji każdy użytkownik może ustanowić konto w witrynie i logowanie za wyłączny dostęp do witryn i usług.</span><span class="sxs-lookup"><span data-stu-id="d742e-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="d742e-105">Jest to w przeciwieństwie do zabezpieczeń Windows, która wymaga od użytkowników mają konta w domenie Windows.</span><span class="sxs-lookup"><span data-stu-id="d742e-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="d742e-106">Zamiast tego można użyć każdemu użytkownikowi, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), lokacji i jej usługi.</span><span class="sxs-lookup"><span data-stu-id="d742e-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="d742e-107">Dla przykładowej aplikacji, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="d742e-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="d742e-108">Aby uzyskać informacje o korzystaniu z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] funkcję dostawcy ról, zobacz [jak: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="d742e-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="d742e-109">Funkcja członkostwa wymaga, korzystanie z bazy danych programu SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="d742e-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="d742e-110">Funkcja obejmuje również metody monit z pytaniem użytkownicy, którzy zapomni swojego hasła.</span><span class="sxs-lookup"><span data-stu-id="d742e-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 <span data-ttu-id="d742e-111">Windows Communication Foundation (WCF) deweloperom korzystać z zalet tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="d742e-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="d742e-112">Po zintegrowaniu aplikacji WCF, użytkownicy muszą podać kombinacja nazwy i hasła użytkownika do aplikacji klienta programu WCF.</span><span class="sxs-lookup"><span data-stu-id="d742e-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="d742e-113">Aby transferu danych do usługi WCF, należy użyć powiązania, które obsługuje poświadczenia nazwy i hasła użytkownika, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i Ustaw typ poświadczeń do klienta`UserName`.</span><span class="sxs-lookup"><span data-stu-id="d742e-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="d742e-114">W usłudze WCF zabezpieczeń uwierzytelnia użytkownika, w oparciu o nazwę użytkownika i hasło i przypisuje rolę określonego przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli.</span><span class="sxs-lookup"><span data-stu-id="d742e-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d742e-115">Usługi WCF nie udostępnia metody służące do wypełniania bazy danych przy użyciu kombinacji nazwy i hasła użytkownika lub inne informacje o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="d742e-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="d742e-116">Aby skonfigurować dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="d742e-116">To configure the membership provider</span></span>  
  
1.  <span data-ttu-id="d742e-117">W pliku Web.config w obszarze <`system.web`> element, Utwórz <`membership`> element.</span><span class="sxs-lookup"><span data-stu-id="d742e-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2.  <span data-ttu-id="d742e-118">W obszarze `<membership>` elementu, Utwórz `<providers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d742e-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3.  <span data-ttu-id="d742e-119">Jako element podrzędny <`providers`> elementu Dodawanie `<clear />` element, aby opróżnić kolekcja dostawców.</span><span class="sxs-lookup"><span data-stu-id="d742e-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4.  <span data-ttu-id="d742e-120">W obszarze `<clear />` elementu, Utwórz <`add`> element z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, i `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="d742e-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="d742e-121">`name` Atrybut jest używany później jako wartość w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d742e-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="d742e-122">Poniższy przykład ustawia ją na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d742e-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="d742e-123">Sekcja konfiguracji można znaleźć w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d742e-123">The following example shows the configuration section.</span></span>  
  
    ```xml  
    <!-- Configure the Sql Membership Provider -->  
    <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
      <providers>  
        <clear />  
          <add   
            name="SqlMembershipProvider"   
            type="System.Web.Security.SqlMembershipProvider"   
            connectionStringName="SqlConn"  
            applicationName="MembershipAndRoleProviderSample"  
            enablePasswordRetrieval="false"  
            enablePasswordReset="false"  
            requiresQuestionAndAnswer="false"  
            requiresUniqueEmail="true"  
            passwordFormat="Hashed" />  
      </providers>  
    </membership>  
    ```  
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="d742e-124">Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacja nazwy i hasła użytkownika</span><span class="sxs-lookup"><span data-stu-id="d742e-124">To configure service security to accept the user name/password combination</span></span>  
  
1.  <span data-ttu-id="d742e-125">W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodawanie [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="d742e-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2.  <span data-ttu-id="d742e-126">Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji wiązania.</span><span class="sxs-lookup"><span data-stu-id="d742e-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="d742e-127">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF zobacz [jak: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d742e-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3.  <span data-ttu-id="d742e-128">Ustaw atrybut `mode` elementu `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="d742e-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4.  <span data-ttu-id="d742e-129">Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName`.</span><span class="sxs-lookup"><span data-stu-id="d742e-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="d742e-130">Określa, że pary nazwa/hasło użytkownika będzie służyć jako poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="d742e-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="d742e-131">Poniższy przykład pokazuje kod konfiguracji dla wiązania.</span><span class="sxs-lookup"><span data-stu-id="d742e-131">The following example shows the configuration code for the binding.</span></span>  
  
    ```xml  
    <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
      <!-- Set up a binding that uses UserName as the client credential type -->  
        <binding name="MembershipBinding">  
          <security mode ="Message">  
            <message clientCredentialType ="UserName"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    </system.serviceModel>  
    ```  
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="d742e-132">Aby skonfigurować usługę do używania dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="d742e-132">To configure a service to use the membership provider</span></span>  
  
1.  <span data-ttu-id="d742e-133">Jako element podrzędny `<system.serviceModel>` elementu Dodawanie [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) — element</span><span class="sxs-lookup"><span data-stu-id="d742e-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2.  <span data-ttu-id="d742e-134">Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> element.</span><span class="sxs-lookup"><span data-stu-id="d742e-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3.  <span data-ttu-id="d742e-135">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu do odpowiedniej wartości.</span><span class="sxs-lookup"><span data-stu-id="d742e-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="d742e-136">Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do <`behavior`> element.</span><span class="sxs-lookup"><span data-stu-id="d742e-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5.  <span data-ttu-id="d742e-137">Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d742e-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6.  <span data-ttu-id="d742e-138">Ustaw `userNamePasswordValidationMode` atrybutu `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="d742e-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="d742e-139">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, usługi WCF korzysta z uwierzytelniania Windows zamiast [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.</span><span class="sxs-lookup"><span data-stu-id="d742e-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7.  <span data-ttu-id="d742e-140">Ustaw `membershipProviderName` atrybutu Nazwa dostawcy (określone podczas dodawania dostawcy w pierwszej procedurze w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="d742e-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="d742e-141">W poniższym przykładzie przedstawiono `<serviceCredentials>` fragmentu do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="d742e-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
    ```xml  
    <behaviors>  
       <serviceBehaviors>  
          <behavior name="MyServiceBehavior">  
             <serviceCredentials>  
                <userNameAuthentication   
                userNamePasswordValidationMode="MembershipProvider"  
                membershipProviderName="SqlMembershipProvider" />  
             </serviceCredentials>  
          </behavior>  
       </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="d742e-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="d742e-142">Example</span></span>  
 <span data-ttu-id="d742e-143">Poniższy kod pokazuje konfigurację to usługa, która używa funkcji członkostwa ASP.</span><span class="sxs-lookup"><span data-stu-id="d742e-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="MyServiceBehavior" name="Microsoft.Samples.GettingStarted.CalculatorService">  
        <endpoint address="http://microsoft.com/WCFservices/Calculator"  
          binding="wsHttpBinding" bindingConfiguration="MembershipBinding"  
          name="ASPmemberUserName" contract="Microsoft.Samples.GettingStarted.ICalculator" />  
      </service>  
    </services>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyServiceBehavior">  
          <serviceCredentials>  
            <userNameAuthentication   
              userNamePasswordValidationMode="MembershipProvider"  
              membershipProviderName="SqlMembershipProvider" />  
          </serviceCredentials>  
        </behavior>  
          </serviceBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="MembershipBinding">  
          <security mode="Message">  
            <message clientCredentialType="UserName" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d742e-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d742e-144">See also</span></span>

- [<span data-ttu-id="d742e-145">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="d742e-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="d742e-146">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="d742e-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
