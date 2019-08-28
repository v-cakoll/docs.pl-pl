---
title: 'Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7df6ec57204990066ce59700e5c2582701f2a81a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045911"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła

Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła. Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*. Aby uwzględnić niestandardową nazwę użytkownika i moduł weryfikacji hasła, należy utworzyć klasę pochodzącą od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie ją skonfigurować.

Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła

1. Utwórz klasę, która pochodzi od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.

    Nie należy używać kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

    Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła

1. Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).

    W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takich jak [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)lub niestandardowy elementbinding [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , który obsługuje zabezpieczenia komunikatów i `UserName` typ poświadczenia.

    W przypadku korzystania z [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy dodać WSHttpBinding > lub [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) [ \<BasicHttpBinding >, NetTcpBinding > lub niestandardowybinding > ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)używa protokołu HTTP (S) i `Basic` schematu uwierzytelniania.

    > [!NOTE]
    > Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] jest używany program lub nowszy, można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu. Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.

    > [!TIP]
    > Aby uzyskać więcej informacji o \<korzystaniu z NetTcpBinding > w tym kontekście, zobacz [ \<zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)

    1. W pliku konfiguracji, w obszarze [ \<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , Dodaj [ \<element > powiązania](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .

    2. Dodaj element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) WSHttpBinding > lub BasicHttpBinding > do sekcji powiązania. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

    3. `mode` Ustaw atrybut `Message` [ >zabezpieczeńlub\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [ >\<zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na, ,`Transport`lub .`TransportWithMessageCredential`

    4. `clientCredentialType` Ustaw [atrybut komunikatu>lub\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ >\<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)transportowego.

        W przypadku korzystania z zabezpieczeń wiadomości Ustaw `clientCredentialType` atrybut [ \<> komunikatu](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na. `UserName`

        W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S `clientCredentialType` ) ustaw atrybut [ \<> transportu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<> transportu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic`.

        > [!NOTE]
        > Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> , a właściwość jest <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>ustawiona na, schemat uwierzytelniania niestandardowego używa podzestawu uwierzytelniania systemu Windows. Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.

    Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

    Poniższy przykład pokazuje kod konfiguracji dla powiązania.

    ```xml
    <system.serviceModel>
      <bindings>
      <wsHttpBinding>
          <binding name="Binding1">
            <security mode="Message">
              <message clientCredentialType="UserName" />
            </security>
          </binding>
        </wsHttpBinding>
      </bindings>
    </system.serviceModel>
    ```

2. Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania poprawności nazwy użytkownika i <xref:System.IdentityModel.Tokens.UserNameSecurityToken> hasła dla przychodzących tokenów zabezpieczających.

    1. Jako element podrzędny do [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu System. ServiceModel >, Dodaj > element Behaviors.

    2. Dodaj > serviceBehaviors do [> zachowań elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)

    3. Dodaj zachowanie [ >elementuiustawodpowiedniąwartośćatrybutu.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) `name`

    4. Dodaj > ServiceCredentials do [> zachowań elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)

    5. Dodaj [> userNameAuthentication do > ServiceCredentials. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)

    6. Ustaw wartość `Custom`na. `userNamePasswordValidationMode`

        > [!IMPORTANT]
        > `userNamePasswordValidationMode` Jeśli wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu sprawdzania poprawności hasła.

    7. Ustaw wartość `customUserNamePasswordValidatorType` na typ, który reprezentuje swoją niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.

    Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła. Nie należy używać kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Instrukcje: Korzystanie z dostawcy członkostwa ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
