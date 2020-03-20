---
title: 'Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 5b15d56c7150a8478bc32651538903778e3b877d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184795"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="558c2-102">Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="558c2-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="558c2-103">Dostawca członkostwa ASP.NET jest funkcją, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="558c2-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="558c2-104">Dzięki tej funkcji każdy użytkownik może założyć konto w witrynie i zalogować się, aby uzyskać wyłączny dostęp do witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="558c2-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="558c2-105">Jest to w przeciwieństwie do zabezpieczeń systemu Windows, który wymaga od użytkowników, aby mieć konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="558c2-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="558c2-106">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwa użytkownika/hasło) może korzystać z witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="558c2-106">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="558c2-107">Aby zapoznać się z przykładową aplikacją, zobacz [Członkostwo i Dostawca roli](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="558c2-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="558c2-108">Aby uzyskać informacje na temat korzystania z funkcji dostawcy roli ASP.NET, zobacz [Jak: Korzystanie z ASP.NET dostawcy roli z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="558c2-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="558c2-109">Funkcja członkostwa wymaga użycia bazy danych programu SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="558c2-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="558c2-110">Funkcja ta zawiera również metody monitowania z pytaniem wszystkich użytkowników, którzy zapomnieli hasła.</span><span class="sxs-lookup"><span data-stu-id="558c2-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="558c2-111">Deweloperzy programu Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="558c2-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="558c2-112">Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika/hasła do aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="558c2-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="558c2-113">Aby przenieść dane do usługi WCF, należy użyć powiązania obsługującego <xref:System.ServiceModel.WSHttpBinding> poświadczenia nazwy użytkownika/hasła, takiego jak (w konfiguracji [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i ustawić typ poświadczeń klienta na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="558c2-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="558c2-114">W usłudze zabezpieczenia WCF uwierzytelnia użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez ASP.NET roli.</span><span class="sxs-lookup"><span data-stu-id="558c2-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="558c2-115">WCF nie udostępnia metod wypełniania bazy danych kombinacjami nazwy użytkownika/hasła ani innych informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="558c2-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="558c2-116">Aby skonfigurować dostawcę członkostwa</span><span class="sxs-lookup"><span data-stu-id="558c2-116">To configure the membership provider</span></span>

1. <span data-ttu-id="558c2-117">W pliku Web.config w obszarze `system.web` <> element utwórz element `membership` <>.</span><span class="sxs-lookup"><span data-stu-id="558c2-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="558c2-118">W `<membership>` obszarze elementu `<providers>` utwórz element.</span><span class="sxs-lookup"><span data-stu-id="558c2-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="558c2-119">Jako element podrzędny do `providers` <> element, `<clear />` dodaj element do opróżnienia kolekcji dostawców.</span><span class="sxs-lookup"><span data-stu-id="558c2-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="558c2-120">W `<clear />` obszarze elementu utwórz <`add`> element z następującymi atrybutami ustawionymi `type` `connectionStringName`na `applicationName` `enablePasswordRetrieval`odpowiednie `enablePasswordReset` `requiresQuestionAndAnswer`wartości: `name` `passwordFormat`, , , , , , , `requiresUniqueEmail`, i .</span><span class="sxs-lookup"><span data-stu-id="558c2-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="558c2-121">Atrybut `name` jest później używany jako wartość w pliku konfiguracyjnym.</span><span class="sxs-lookup"><span data-stu-id="558c2-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="558c2-122">W poniższym przykładzie ustawia go na `SqlMembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="558c2-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="558c2-123">W poniższym przykładzie przedstawiono sekcję konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="558c2-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="558c2-124">Aby skonfigurować zabezpieczenia usługi w celu zaakceptowania kombinacji nazwy użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="558c2-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="558c2-125">W pliku konfiguracyjnym w [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<ramach elementu system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) dodaj powiązania>element.</span><span class="sxs-lookup"><span data-stu-id="558c2-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="558c2-126">Dodaj [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązań.</span><span class="sxs-lookup"><span data-stu-id="558c2-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="558c2-127">Aby uzyskać więcej informacji na temat tworzenia elementu wiązania WCF, zobacz [Jak: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="558c2-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="558c2-128">Ustaw atrybut `mode` elementu `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="558c2-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="558c2-129">Ustaw `clientCredentialType` atrybut <`message`> elementu na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="558c2-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="558c2-130">Określa to, że para nazwa użytkownika/hasło będzie używana jako poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="558c2-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="558c2-131">W poniższym przykładzie przedstawiono kod konfiguracji powiązania.</span><span class="sxs-lookup"><span data-stu-id="558c2-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="558c2-132">Aby skonfigurować usługę do korzystania z dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="558c2-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="558c2-133">Jako dziecko do `<system.serviceModel>` elementu dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span><span class="sxs-lookup"><span data-stu-id="558c2-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="558c2-134">Dodaj [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.</span><span class="sxs-lookup"><span data-stu-id="558c2-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="558c2-135">Dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybut na odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="558c2-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="558c2-136">Dodaj [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do elementu `behavior`> <.</span><span class="sxs-lookup"><span data-stu-id="558c2-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="558c2-137">Dodaj [ \<>userNameAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.</span><span class="sxs-lookup"><span data-stu-id="558c2-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="558c2-138">Ustaw `userNamePasswordValidationMode` atrybut na `MembershipProvider`.</span><span class="sxs-lookup"><span data-stu-id="558c2-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="558c2-139">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="558c2-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="558c2-140">Ustaw `membershipProviderName` atrybut na nazwę dostawcy (określoną podczas dodawania dostawcy w pierwszej procedurze w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="558c2-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="558c2-141">Poniższy przykład `<serviceCredentials>` pokazuje fragment do tego punktu.</span><span class="sxs-lookup"><span data-stu-id="558c2-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="558c2-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="558c2-142">Example</span></span>

<span data-ttu-id="558c2-143">Poniższy kod przedstawia konfigurację usługi korzystającej z funkcji członkostwa ASP.</span><span class="sxs-lookup"><span data-stu-id="558c2-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="558c2-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="558c2-144">See also</span></span>

- [<span data-ttu-id="558c2-145">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="558c2-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="558c2-146">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="558c2-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
