---
title: 'Instrukcje: używanie dostawcy członkostwa platformy ASP.NET'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: b86287440b2265349b853265f12a2f6e48b4cff3
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045269"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="dd364-102">Instrukcje: używanie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="dd364-102">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="dd364-103">Dostawca członkostwa ASP.NET to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="dd364-103">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="dd364-104">Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z witryną i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług.</span><span class="sxs-lookup"><span data-stu-id="dd364-104">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="dd364-105">Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="dd364-105">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="dd364-106">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy użytkownika/hasła) może korzystać z witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="dd364-106">Instead, any user that supplies his or her credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="dd364-107">Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="dd364-107">For a sample application, see [Membership and Role Provider](../../../../docs/framework/wcf/samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="dd364-108">Aby uzyskać informacje o korzystaniu z funkcji dostawcy roli ASP.NET [, zobacz How to: Używanie dostawcy roli ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="dd364-108">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="dd364-109">Funkcja członkostwa wymaga użycia bazy danych SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="dd364-109">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="dd364-110">Ta funkcja zawiera również metody wyświetlania monitu z pytaniem dla użytkowników, którzy zapominali swoje hasła.</span><span class="sxs-lookup"><span data-stu-id="dd364-110">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="dd364-111">Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="dd364-111">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="dd364-112">Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="dd364-112">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="dd364-113">Aby przesłać dane do usługi WCF, użyj powiązania, które obsługuje poświadczenia nazwy użytkownika/hasła, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i ustaw typ poświadczeń klienta na.</span><span class="sxs-lookup"><span data-stu-id="dd364-113">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="dd364-114">W usłudze zabezpieczenia WCF uwierzytelniają użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez rolę ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dd364-114">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="dd364-115">Funkcja WCF nie dostarcza metod do wypełniania bazy danych za pomocą kombinacji nazwy użytkownika/hasła lub innych informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="dd364-115">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="dd364-116">Aby skonfigurować dostawcę członkostwa</span><span class="sxs-lookup"><span data-stu-id="dd364-116">To configure the membership provider</span></span>

1. <span data-ttu-id="dd364-117">W pliku Web. config w elemencie <`system.web`> Utwórz element > <.`membership`</span><span class="sxs-lookup"><span data-stu-id="dd364-117">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="dd364-118">W obszarze `<providers>` elementu Utwórz element. `<membership>`</span><span class="sxs-lookup"><span data-stu-id="dd364-118">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="dd364-119">Jako element podrzędny do <`providers`>, `<clear />` Dodaj element, aby opróżnić kolekcję dostawców.</span><span class="sxs-lookup"><span data-stu-id="dd364-119">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="dd364-120">`type` `name``add` `connectionStringName` `enablePasswordReset` `applicationName` `requiresQuestionAndAnswer` `enablePasswordRetrieval`W obszarze elementuUtwórz<element>znastępującymiatrybutamiustawionyminaodpowiedniewartości:,,,,,`<clear />` , `requiresUniqueEmail`i .`passwordFormat`</span><span class="sxs-lookup"><span data-stu-id="dd364-120">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="dd364-121">Ten `name` atrybut jest używany później jako wartość w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="dd364-121">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="dd364-122">W poniższym przykładzie jest `SqlMembershipProvider`ustawiana wartość.</span><span class="sxs-lookup"><span data-stu-id="dd364-122">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="dd364-123">W poniższym przykładzie przedstawiono sekcję Konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="dd364-123">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="dd364-124">Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacji nazwy użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="dd364-124">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="dd364-125">W pliku konfiguracji, w obszarze [ \<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , Dodaj [ \<element > powiązania](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="dd364-125">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="dd364-126">Dodaj > WSHttpBinding do sekcji powiązań. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="dd364-126">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="dd364-127">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="dd364-127">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="dd364-128">Ustaw atrybut `mode` elementu `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="dd364-128">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="dd364-129">Ustaw atrybut <`message`> elementu `UserName`. `clientCredentialType`</span><span class="sxs-lookup"><span data-stu-id="dd364-129">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="dd364-130">Oznacza to, że para nazwa użytkownika/hasło zostanie użyta jako poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="dd364-130">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="dd364-131">Poniższy przykład pokazuje kod konfiguracji dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="dd364-131">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="dd364-132">Aby skonfigurować usługę do korzystania z dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="dd364-132">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="dd364-133">Jako element podrzędny do `<system.serviceModel>` elementu [ \<Dodaj > zachowań](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu</span><span class="sxs-lookup"><span data-stu-id="dd364-133">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="dd364-134">Dodaj > serviceBehaviors do <`behaviors`> elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="dd364-134">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="dd364-135">`name` [ Dodaj\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="dd364-135">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="dd364-136">Dodaj >`behavior`ServiceCredentials do < > elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="dd364-136">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="dd364-137">Dodaj [> userNameAuthentication do elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>`</span><span class="sxs-lookup"><span data-stu-id="dd364-137">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="dd364-138">Ustaw atrybut na `MembershipProvider`. `userNamePasswordValidationMode`</span><span class="sxs-lookup"><span data-stu-id="dd364-138">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="dd364-139">`userNamePasswordValidationMode` Jeśli wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dd364-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="dd364-140">`membershipProviderName` Ustaw atrybut na nazwę dostawcy (określony podczas dodawania dostawcy w pierwszej procedurze w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="dd364-140">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="dd364-141">Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.</span><span class="sxs-lookup"><span data-stu-id="dd364-141">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="dd364-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd364-142">Example</span></span>

<span data-ttu-id="dd364-143">Poniższy kod przedstawia konfigurację usługi korzystającej z funkcji członkostwa ASP.</span><span class="sxs-lookup"><span data-stu-id="dd364-143">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dd364-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dd364-144">See also</span></span>

- [<span data-ttu-id="dd364-145">Instrukcje: Używanie dostawcy roli ASP.NET z usługą</span><span class="sxs-lookup"><span data-stu-id="dd364-145">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="dd364-146">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="dd364-146">Membership and Role Provider</span></span>](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
