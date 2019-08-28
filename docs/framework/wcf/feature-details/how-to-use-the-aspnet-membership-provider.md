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
# <a name="how-to-use-the-aspnet-membership-provider"></a>Instrukcje: używanie dostawcy członkostwa platformy ASP.NET

Dostawca członkostwa ASP.NET to funkcja, która umożliwia deweloperom ASP.NET tworzenie witryn sieci Web, które umożliwiają użytkownikom tworzenie unikatowych kombinacji nazw użytkowników i haseł. Korzystając z tej funkcji, każdy użytkownik może nawiązać konto z witryną i zalogować się w celu uzyskania wyłącznego dostępu do lokacji i jej usług. Jest to w przeciwieństwie do zabezpieczeń systemu Windows, co wymaga, aby użytkownicy mieli konta w domenie systemu Windows. Zamiast tego każdy użytkownik, który dostarcza swoje poświadczenia (kombinacja nazwy użytkownika/hasła) może korzystać z witryny i jej usług.

Aby zapoznać się z przykładową aplikacją, zobacz [członkostwo i dostawca ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md). Aby uzyskać informacje o korzystaniu z funkcji dostawcy roli ASP.NET [, zobacz How to: Używanie dostawcy roli ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).

Funkcja członkostwa wymaga użycia bazy danych SQL Server do przechowywania informacji o użytkowniku. Ta funkcja zawiera również metody wyświetlania monitu z pytaniem dla użytkowników, którzy zapominali swoje hasła.

Deweloperzy Windows Communication Foundation (WCF) mogą korzystać z tych funkcji ze względów bezpieczeństwa. Po zintegrowaniu z aplikacją WCF użytkownicy muszą podać kombinację nazwy użytkownika i hasła do aplikacji klienckiej WCF. Aby przesłać dane do usługi WCF, użyj powiązania, które obsługuje poświadczenia nazwy użytkownika/hasła, takie jak <xref:System.ServiceModel.WSHttpBinding> (w konfiguracji `UserName` [ \<, WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)) i ustaw typ poświadczeń klienta na. W usłudze zabezpieczenia WCF uwierzytelniają użytkownika na podstawie nazwy użytkownika i hasła, a także przypisuje rolę określoną przez rolę ASP.NET.

> [!NOTE]
> Funkcja WCF nie dostarcza metod do wypełniania bazy danych za pomocą kombinacji nazwy użytkownika/hasła lub innych informacji o użytkowniku.

### <a name="to-configure-the-membership-provider"></a>Aby skonfigurować dostawcę członkostwa

1. W pliku Web. config w elemencie <`system.web`> Utwórz element > <.`membership`

2. W obszarze `<providers>` elementu Utwórz element. `<membership>`

3. Jako element podrzędny do <`providers`>, `<clear />` Dodaj element, aby opróżnić kolekcję dostawców.

4. `type` `name``add` `connectionStringName` `enablePasswordReset` `applicationName` `requiresQuestionAndAnswer` `enablePasswordRetrieval`W obszarze elementuUtwórz<element>znastępującymiatrybutamiustawionyminaodpowiedniewartości:,,,,,`<clear />` , `requiresUniqueEmail`i .`passwordFormat` Ten `name` atrybut jest używany później jako wartość w pliku konfiguracji. W poniższym przykładzie jest `SqlMembershipProvider`ustawiana wartość.

    W poniższym przykładzie przedstawiono sekcję Konfiguracja.

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

### <a name="to-configure-service-security-to-accept-the-user-namepassword-combination"></a>Aby skonfigurować zabezpieczenia usługi do akceptowania kombinacji nazwy użytkownika/hasła

1. W pliku konfiguracji, w obszarze [ \<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , Dodaj [ \<element > powiązania](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .

2. Dodaj > WSHttpBinding do sekcji powiązań. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

3. Ustaw atrybut `mode` elementu `<security>` na `Message`.

4. Ustaw atrybut <`message`> elementu `UserName`. `clientCredentialType` Oznacza to, że para nazwa użytkownika/hasło zostanie użyta jako poświadczenia klienta.

    Poniższy przykład pokazuje kod konfiguracji dla powiązania.

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

1. Jako element podrzędny do `<system.serviceModel>` elementu [ \<Dodaj > zachowań](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu

2. Dodaj > serviceBehaviors do <`behaviors`> elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)

3. `name` [ Dodaj\<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) i ustaw odpowiednią wartość atrybutu.

4. Dodaj >`behavior`ServiceCredentials do < > elementu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)

5. Dodaj [> userNameAuthentication do elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) `<serviceCredentials>`

6. Ustaw atrybut na `MembershipProvider`. `userNamePasswordValidationMode`

    > [!IMPORTANT]
    > `userNamePasswordValidationMode` Jeśli wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast dostawcy członkostwa ASP.NET.

7. `membershipProviderName` Ustaw atrybut na nazwę dostawcy (określony podczas dodawania dostawcy w pierwszej procedurze w tym temacie). Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.

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

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Używanie dostawcy roli ASP.NET z usługą](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Dostawca członkostwa i ról](../../../../docs/framework/wcf/samples/membership-and-role-provider.md)
