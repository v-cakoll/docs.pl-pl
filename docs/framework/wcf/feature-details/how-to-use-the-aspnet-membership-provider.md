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
# <a name="how-to-use-the-aspnet-membership-provider"></a>Instrukcje: Użycie dostawcy członkostwa platformy ASP.NET

Dostawca członkostwa ASP.NET jest funkcją, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł. Dzięki tej funkcji każdy użytkownik może założyć konto w witrynie i zalogować się, aby uzyskać wyłączny dostęp do witryny i jej usług. Jest to w przeciwieństwie do zabezpieczeń systemu Windows, który wymaga od użytkowników, aby mieć konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwa użytkownika/hasło) może korzystać z witryny i jej usług.

Aby zapoznać się z przykładową aplikacją, zobacz [Członkostwo i Dostawca roli](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać informacje na temat korzystania z funkcji dostawcy roli ASP.NET, zobacz [Jak: Korzystanie z ASP.NET dostawcy roli z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).

Funkcja członkostwa wymaga użycia bazy danych programu SQL Server do przechowywania informacji o użytkowniku. Funkcja ta zawiera również metody monitowania z pytaniem wszystkich użytkowników, którzy zapomnieli hasła.

Deweloperzy programu Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika/hasła do aplikacji klienckiej WCF. Aby przenieść dane do usługi WCF, należy użyć powiązania obsługującego <xref:System.ServiceModel.WSHttpBinding> poświadczenia nazwy użytkownika/hasła, takiego jak (w konfiguracji [ \<>wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i ustawić typ poświadczeń klienta na `UserName`. W usłudze zabezpieczenia WCF uwierzytelnia użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez ASP.NET roli.

> [!NOTE]
> WCF nie udostępnia metod wypełniania bazy danych kombinacjami nazwy użytkownika/hasła ani innych informacji o użytkowniku.

### <a name="to-configure-the-membership-provider"></a>Aby skonfigurować dostawcę członkostwa

1. W pliku Web.config w obszarze `system.web` <> element utwórz element `membership` <>.

2. W `<membership>` obszarze elementu `<providers>` utwórz element.

3. Jako element podrzędny do `providers` <> element, `<clear />` dodaj element do opróżnienia kolekcji dostawców.

4. W `<clear />` obszarze elementu utwórz <`add`> element z następującymi atrybutami ustawionymi `type` `connectionStringName`na `applicationName` `enablePasswordRetrieval`odpowiednie `enablePasswordReset` `requiresQuestionAndAnswer`wartości: `name` `passwordFormat`, , , , , , , `requiresUniqueEmail`, i . Atrybut `name` jest później używany jako wartość w pliku konfiguracyjnym. W poniższym przykładzie ustawia go na `SqlMembershipProvider`.

    W poniższym przykładzie przedstawiono sekcję konfiguracji.

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Aby skonfigurować zabezpieczenia usługi w celu zaakceptowania kombinacji nazwy użytkownika/hasła

1. W pliku konfiguracyjnym w [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) [ \<ramach elementu system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) dodaj powiązania>element.

2. Dodaj [ \<>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) do sekcji powiązań. Aby uzyskać więcej informacji na temat tworzenia elementu wiązania WCF, zobacz [Jak: Określanie powiązania usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

3. Ustaw atrybut `mode` elementu `<security>` na `Message`.

4. Ustaw `clientCredentialType` atrybut <`message`> elementu na `UserName`. Określa to, że para nazwa użytkownika/hasło będzie używana jako poświadczenia klienta.

    W poniższym przykładzie przedstawiono kod konfiguracji powiązania.

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

### <a name="to-configure-a-service-to-use-the-membership-provider"></a>Aby skonfigurować usługę do korzystania z dostawcy członkostwa

1. Jako dziecko do `<system.serviceModel>` elementu dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element

2. Dodaj [ \<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) do <`behaviors`> elementu.

3. Dodaj [ \<zachowanie>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw `name` atrybut na odpowiednią wartość.

4. Dodaj [ \<>serviceCredentials](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) do elementu `behavior`> <.

5. Dodaj [ \<>userNameAuthentication](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) do `<serviceCredentials>` elementu.

6. Ustaw `userNamePasswordValidationMode` atrybut na `MembershipProvider`.

    > [!IMPORTANT]
    > Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.

7. Ustaw `membershipProviderName` atrybut na nazwę dostawcy (określoną podczas dodawania dostawcy w pierwszej procedurze w tym temacie). Poniższy przykład `<serviceCredentials>` pokazuje fragment do tego punktu.

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

## <a name="example"></a>Przykład

Poniższy kod przedstawia konfigurację usługi korzystającej z funkcji członkostwa ASP.

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

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Używanie dostawcy ról ASP.NET razem z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
