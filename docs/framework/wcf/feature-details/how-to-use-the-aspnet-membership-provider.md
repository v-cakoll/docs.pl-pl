---
title: 'Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET'
description: Dowiedz się, w jaki sposób dostawca członkostwa ASP.NET obsługuje witryny sieci Web, które umożliwiają użytkownikom tworzenie nazwy użytkownika i hasła w celu uzyskania dostępu bez konta domeny systemu Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- WCF and ASP.NET
- WCF, authorization
- WCF, security
ms.assetid: 322c56e0-938f-4f19-a981-7b6530045b90
ms.openlocfilehash: 6d527993dcf1fc5d5cd39bf22c3e772baf60e62f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246730"
---
# <a name="how-to-use-the-aspnet-membership-provider"></a><span data-ttu-id="737f3-103">Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="737f3-103">How to: Use the ASP.NET Membership Provider</span></span>

<span data-ttu-id="737f3-104">Dostawca członkostwa ASP.NET to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł.</span><span class="sxs-lookup"><span data-stu-id="737f3-104">The ASP.NET membership provider is a feature that enables ASP.NET developers to create Web sites that allow users to create unique user name and password combinations.</span></span> <span data-ttu-id="737f3-105">Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z witryną i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług.</span><span class="sxs-lookup"><span data-stu-id="737f3-105">With this facility, any user can establish an account with the site, and sign in for exclusive access to the site and its services.</span></span> <span data-ttu-id="737f3-106">Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="737f3-106">This is in contrast to Windows security, which requires users to have accounts in a Windows domain.</span></span> <span data-ttu-id="737f3-107">Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy użytkownika/hasła), może korzystać z witryny i jej usług.</span><span class="sxs-lookup"><span data-stu-id="737f3-107">Instead, any user that supplies their credentials (the user name/password combination) can use the site and its services.</span></span>

<span data-ttu-id="737f3-108">Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../samples/membership-and-role-provider.md).</span><span class="sxs-lookup"><span data-stu-id="737f3-108">For a sample application, see [Membership and Role Provider](../samples/membership-and-role-provider.md).</span></span> <span data-ttu-id="737f3-109">Aby uzyskać informacje o korzystaniu z funkcji dostawcy roli ASP.NET, zobacz [How to: Use the ASP.NET role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span><span class="sxs-lookup"><span data-stu-id="737f3-109">For information about using the ASP.NET role provider feature, see [How to: Use the ASP.NET Role Provider with a Service](how-to-use-the-aspnet-role-provider-with-a-service.md).</span></span>

<span data-ttu-id="737f3-110">Funkcja członkostwa wymaga użycia bazy danych SQL Server do przechowywania informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="737f3-110">The membership feature requires using a SQL Server database to store the user information.</span></span> <span data-ttu-id="737f3-111">Ta funkcja zawiera również metody wyświetlania monitu z pytaniem dla użytkowników, którzy zapominali swoje hasła.</span><span class="sxs-lookup"><span data-stu-id="737f3-111">The feature also includes methods for prompting with a question any users who have forgotten their password.</span></span>

<span data-ttu-id="737f3-112">Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="737f3-112">Windows Communication Foundation (WCF) developers can take advantage of these features for security purposes.</span></span> <span data-ttu-id="737f3-113">Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF.</span><span class="sxs-lookup"><span data-stu-id="737f3-113">When integrated into an WCF application, users must supply a user name/password combination to the WCF client application.</span></span> <span data-ttu-id="737f3-114">Aby przesłać dane do usługi WCF, użyj powiązania, które obsługuje poświadczenia nazwy użytkownika/hasła, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji, [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) a) i ustaw typ poświadczeń klienta na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="737f3-114">To transfer the data to the WCF service, use a binding that supports user name/password credentials, such as the <xref:System.ServiceModel.WSHttpBinding> (in configuration, the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)) and set the client credential type to `UserName`.</span></span> <span data-ttu-id="737f3-115">W usłudze zabezpieczenia WCF uwierzytelniają użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez rolę ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="737f3-115">On the service, WCF security authenticates the user based on the user name and password, and also assigns the role specified by the ASP.NET role.</span></span>

> [!NOTE]
> <span data-ttu-id="737f3-116">Funkcja WCF nie dostarcza metod do wypełniania bazy danych za pomocą kombinacji nazwy użytkownika/hasła lub innych informacji o użytkowniku.</span><span class="sxs-lookup"><span data-stu-id="737f3-116">WCF does not provide methods to populate the database with user name/password combinations or other user information.</span></span>

### <a name="to-configure-the-membership-provider"></a><span data-ttu-id="737f3-117">Aby skonfigurować dostawcę członkostwa</span><span class="sxs-lookup"><span data-stu-id="737f3-117">To configure the membership provider</span></span>

1. <span data-ttu-id="737f3-118">W pliku Web.config w obszarze <`system.web`> Utwórz `membership` element <>.</span><span class="sxs-lookup"><span data-stu-id="737f3-118">In the Web.config file, under the <`system.web`> element, create a <`membership`> element.</span></span>

2. <span data-ttu-id="737f3-119">W obszarze `<membership>` elementu Utwórz `<providers>` element.</span><span class="sxs-lookup"><span data-stu-id="737f3-119">Under the `<membership>` element, create a `<providers>` element.</span></span>

3. <span data-ttu-id="737f3-120">Jako element podrzędny do <`providers`>, Dodaj `<clear />` element, aby opróżnić kolekcję dostawców.</span><span class="sxs-lookup"><span data-stu-id="737f3-120">As a child to the <`providers`> element, add a `<clear />` element to flush the collection of providers.</span></span>

4. <span data-ttu-id="737f3-121">W obszarze `<clear />` elementu Utwórz <`add` element> z następującymi atrybutami ustawionymi na odpowiednie wartości:,,,,,,,, `name` `type` `connectionStringName` `applicationName` `enablePasswordRetrieval` `enablePasswordReset` `requiresQuestionAndAnswer` `requiresUniqueEmail` i `passwordFormat` .</span><span class="sxs-lookup"><span data-stu-id="737f3-121">Under the `<clear />` element, create an <`add`> element with the following attributes set to appropriate values: `name`, `type`, `connectionStringName`, `applicationName`, `enablePasswordRetrieval`, `enablePasswordReset`, `requiresQuestionAndAnswer`, `requiresUniqueEmail`, and `passwordFormat`.</span></span> <span data-ttu-id="737f3-122">Ten `name` atrybut jest używany później jako wartość w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="737f3-122">The `name` attribute is used later as a value in the configuration file.</span></span> <span data-ttu-id="737f3-123">W poniższym przykładzie jest ustawiana wartość `SqlMembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="737f3-123">The following example sets it to `SqlMembershipProvider`.</span></span>

    <span data-ttu-id="737f3-124">W poniższym przykładzie przedstawiono sekcję Konfiguracja.</span><span class="sxs-lookup"><span data-stu-id="737f3-124">The following example shows the configuration section.</span></span>

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a><span data-ttu-id="737f3-125">Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacji nazwy użytkownika/hasła</span><span class="sxs-lookup"><span data-stu-id="737f3-125">To configure service security to accept the user name/password combination</span></span>

1. <span data-ttu-id="737f3-126">W pliku konfiguracji, w obszarze [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="737f3-126">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

2. <span data-ttu-id="737f3-127">Dodaj [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązań.</span><span class="sxs-lookup"><span data-stu-id="737f3-127">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) to the bindings section.</span></span> <span data-ttu-id="737f3-128">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="737f3-128">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

3. <span data-ttu-id="737f3-129">Ustaw atrybut `mode` elementu `<security>` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="737f3-129">Set the `mode` attribute of the `<security>` element to `Message`.</span></span>

4. <span data-ttu-id="737f3-130">Ustaw `clientCredentialType` atrybut <`message`> elementu `UserName` .</span><span class="sxs-lookup"><span data-stu-id="737f3-130">Set the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span> <span data-ttu-id="737f3-131">Oznacza to, że para nazwa użytkownika/hasło zostanie użyta jako poświadczenia klienta.</span><span class="sxs-lookup"><span data-stu-id="737f3-131">This specifies that a user name/password pair will be used as the client's credential.</span></span>

    <span data-ttu-id="737f3-132">Poniższy przykład pokazuje kod konfiguracji dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="737f3-132">The following example shows the configuration code for the binding.</span></span>

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a><span data-ttu-id="737f3-133">Aby skonfigurować usługę do korzystania z dostawcy członkostwa</span><span class="sxs-lookup"><span data-stu-id="737f3-133">To configure a service to use the membership provider</span></span>

1. <span data-ttu-id="737f3-134">Jako element podrzędny do `<system.serviceModel>` elementu, Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span><span class="sxs-lookup"><span data-stu-id="737f3-134">As a child to the `<system.serviceModel>` element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element</span></span>

2. <span data-ttu-id="737f3-135">Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) do `behaviors` elementu> <.</span><span class="sxs-lookup"><span data-stu-id="737f3-135">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the <`behaviors`> element.</span></span>

3. <span data-ttu-id="737f3-136">Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) a i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="737f3-136">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) and set the `name` attribute to an appropriate value.</span></span>

4. <span data-ttu-id="737f3-137">Dodaj [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) do `behavior` elementu> <.</span><span class="sxs-lookup"><span data-stu-id="737f3-137">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the <`behavior`> element.</span></span>

5. <span data-ttu-id="737f3-138">Dodaj [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>` element do elementu.</span><span class="sxs-lookup"><span data-stu-id="737f3-138">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the `<serviceCredentials>` element.</span></span>

6. <span data-ttu-id="737f3-139">Ustaw `userNamePasswordValidationMode` atrybut na `MembershipProvider` .</span><span class="sxs-lookup"><span data-stu-id="737f3-139">Set the `userNamePasswordValidationMode` attribute to `MembershipProvider`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="737f3-140">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="737f3-140">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the ASP.NET membership provider.</span></span>

7. <span data-ttu-id="737f3-141">Ustaw `membershipProviderName` atrybut na nazwę dostawcy (określony podczas dodawania dostawcy w pierwszej procedurze w tym temacie).</span><span class="sxs-lookup"><span data-stu-id="737f3-141">Set the `membershipProviderName` attribute to the name of the provider (specified when adding the provider in the first procedure in this topic).</span></span> <span data-ttu-id="737f3-142">Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.</span><span class="sxs-lookup"><span data-stu-id="737f3-142">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

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

## <a name="example"></a><span data-ttu-id="737f3-143">Przykład</span><span class="sxs-lookup"><span data-stu-id="737f3-143">Example</span></span>

<span data-ttu-id="737f3-144">Poniższy kod przedstawia konfigurację usługi korzystającej z funkcji członkostwa ASP.</span><span class="sxs-lookup"><span data-stu-id="737f3-144">The following code shows the configuration for a service that uses the ASP membership feature.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="737f3-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="737f3-145">See also</span></span>

- [<span data-ttu-id="737f3-146">Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą</span><span class="sxs-lookup"><span data-stu-id="737f3-146">How to: Use the ASP.NET Role Provider with a Service</span></span>](how-to-use-the-aspnet-role-provider-with-a-service.md)
- [<span data-ttu-id="737f3-147">Dostawca członkostwa i ról</span><span class="sxs-lookup"><span data-stu-id="737f3-147">Membership and Role Provider</span></span>](../samples/membership-and-role-provider.md)
