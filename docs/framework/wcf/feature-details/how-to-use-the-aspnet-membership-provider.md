---
title: "Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6c5042e73945c54da2b1ee71fc5ea61727dc73c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="6673c-102">Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6673c-102">How to: Use the ASP.NET Membership Provider</span></span>
<span data-ttu-id="6673c-103">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Dostawcy członkostwa jest funkcją, która umożliwia [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] deweloperom tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie użytkownika unikatowych kombinacji nazwy i hasła.</span><span class="sxs-lookup"><span data-stu-id="6673c-103">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider is a feature that enables [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="6673c-104">Z tej funkcji każdy użytkownik można założyć konto w witrynie i zaloguj się do wyłącznego dostępu do lokacji i jej usług.</span><span class="sxs-lookup"><span data-stu-id="6673c-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="6673c-105">Dzięki temu nie trzeba zabezpieczenia systemu Windows, który wymaga od użytkowników mają konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6673c-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="6673c-106">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy i hasła użytkownika), można użyć lokacji i jej usługi.</span><span class="sxs-lookup"><span data-stu-id="6673c-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>  
  
 <span data-ttu-id="6673c-107">Przykładową aplikację, zobacz [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6673c-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="6673c-108">Informacji o używaniu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli dostawcy funkcji, zobacz [porady: Używanie dostawcy ról ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="6673c-108">For information about using the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>  
  
 <span data-ttu-id="6673c-109">Funkcja członkostwa wymaga, korzystanie z bazy danych programu SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="6673c-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="6673c-110">Funkcja zawiera również metody w celu wyświetlenia monitu z pytaniem wszyscy użytkownicy, którzy pamiętasz swojego hasła.</span><span class="sxs-lookup"><span data-stu-id="6673c-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="6673c-111">Deweloperzy mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="6673c-111"> developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="6673c-112">Po zintegrowaniu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji, użytkowników należy podać kombinacji nazwa/hasło użytkownika, aby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji klienckiej.</span><span class="sxs-lookup"><span data-stu-id="6673c-112">When integrated into an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application, users must supply a user name/password combination to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span> <span data-ttu-id="6673c-113">Na przesyłanie danych do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, użyj powiązania, które obsługuje poświadczenia nazwy i hasła użytkownika, takich jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i Ustaw poświadczenia klienta Typ `UserName`.</span><span class="sxs-lookup"><span data-stu-id="6673c-113">To transfer the data to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="6673c-114">W usłudze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń uwierzytelnia użytkownika, w oparciu o nazwę użytkownika i hasło, a następnie przypisuje także rola określona przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] roli.</span><span class="sxs-lookup"><span data-stu-id="6673c-114">On the service, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security authenticates the user based on the user name and password, and also assigns the role specified by the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] role.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="6673c-115">nie zawiera metody służące do wypełniania bazy danych z kombinacji nazwy i hasła użytkownika lub inne informacje o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="6673c-115"> does not provide methods to populate the database with user name/password combinations or other user information.</span></span>  
  
### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="6673c-116">Aby skonfigurować dostawcę członkostwa</span><span class="sxs-lookup"><span data-stu-id="6673c-116">To configure the membership provider</span></span>  
  
1.  <span data-ttu-id="6673c-117">W pliku Web.config w obszarze <`system.web`> elementu, Utwórz <`membership`> elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>  
  
2.  <span data-ttu-id="6673c-118">W obszarze `<membership>` elementu, Utwórz `<providers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-118">Under the `<membership>` element, create a `<providers>` element.</span></span>  
  
3.  <span data-ttu-id="6673c-119">Jako element podrzędny <`providers`> elementu, Dodaj `<clear />` element, aby opróżnić kolekcji dostawców.</span><span class="sxs-lookup"><span data-stu-id="6673c-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>  
  
4.  <span data-ttu-id="6673c-120">W obszarze `<clear />` elementu, Utwórz <`add`> elementu z następującymi atrybutami Ustaw odpowiednie wartości: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer` , `requiresUniqueEmail`, i `passwordFormat`.</span><span class="sxs-lookup"><span data-stu-id="6673c-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="6673c-121">`name` Atrybut jest później używany jako wartość w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6673c-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="6673c-122">Poniższy przykład ustawia ją na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="6673c-122">The following example sets it to `SqlMembershipProvider`.</span></span>  
  
     <span data-ttu-id="6673c-123">W poniższym przykładzie pokazano sekcję konfiguracyjną.</span><span class="sxs-lookup"><span data-stu-id="6673c-123">The following example shows the configuration section.</span></span>  
  
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
  
### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="6673c-124">Aby skonfigurować zabezpieczenia usługi, aby zaakceptować kombinacja nazwy i hasła użytkownika</span><span class="sxs-lookup"><span data-stu-id="6673c-124">To configure service security to accept the user name/password combination</span></span>  
  
1.  <span data-ttu-id="6673c-125">W pliku konfiguracji w obszarze [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [ \<powiązania >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
2.  <span data-ttu-id="6673c-126">Dodaj [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="6673c-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="6673c-127">Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania elementu, zobacz [porady: Określanie wiązań usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="6673c-127"> creating an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>  
  
3.  <span data-ttu-id="6673c-128">Ustaw atrybut `mode` elementu `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="6673c-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>  
  
4.  <span data-ttu-id="6673c-129">Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName`.</span><span class="sxs-lookup"><span data-stu-id="6673c-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="6673c-130">Określa, że pary nazwa/hasło użytkownika będzie służyć jako poświadczeń klienta.</span><span class="sxs-lookup"><span data-stu-id="6673c-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>  
  
     <span data-ttu-id="6673c-131">Poniższy przykład przedstawia kod konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="6673c-131">The following example shows the configuration code for the binding.</span></span>  
  
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
  
### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="6673c-132">Aby skonfigurować usługę do używania dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="6673c-132">To configure a service to use the membership provider</span></span>  
  
1.  <span data-ttu-id="6673c-133">Jako element podrzędny `<system.serviceModel>` elementu, Dodaj [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) — element</span><span class="sxs-lookup"><span data-stu-id="6673c-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>  
  
2.  <span data-ttu-id="6673c-134">Dodaj [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>  
  
3.  <span data-ttu-id="6673c-135">Dodaj [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybutu odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="6673c-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="6673c-136">Dodaj [ \<serviceCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do <`behavior`> elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>  
  
5.  <span data-ttu-id="6673c-137">Dodaj [ \<userNameAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="6673c-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>  
  
6.  <span data-ttu-id="6673c-138">Ustaw `userNamePasswordValidationMode` atrybutu `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="6673c-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6673c-139">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] używa uwierzytelniania systemu Windows zamiast [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] dostawcy członkostwa.</span><span class="sxs-lookup"><span data-stu-id="6673c-139">If the `userNamePasswordValidationMode` value is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses Windows authentication instead of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] membership provider.</span></span>  
  
7.  <span data-ttu-id="6673c-140">Ustaw `membershipProviderName` atrybutu nazwę dostawcy (określona podczas dodawania dostawcy w pierwszej procedurze w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="6673c-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="6673c-141">W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="6673c-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6673c-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="6673c-142">Example</span></span>  
 <span data-ttu-id="6673c-143">Poniższy kod przedstawia konfigurację dla usługi, która jest używana funkcja członkostwa ASP.</span><span class="sxs-lookup"><span data-stu-id="6673c-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6673c-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6673c-144">See Also</span></span>  
 [<span data-ttu-id="6673c-145">Instrukcje: używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="6673c-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 [<span data-ttu-id="6673c-146">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="6673c-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
