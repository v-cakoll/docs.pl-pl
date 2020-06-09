---
title: 'Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 5ada34ca2d0d757ea333fed60aef179d6578356c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601182"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła

Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła. Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*. Aby uwzględnić niestandardową nazwę użytkownika i moduł weryfikacji hasła, należy utworzyć klasę pochodzącą od, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a następnie ją skonfigurować.

Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła

1. Utwórz klasę, która pochodzi od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.

    Nie należy używać kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

    Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła

1. Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).

    W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takich jak [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) które obsługuje zabezpieczenia komunikatów i `UserName` Typ poświadczenia.

    W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S) należy dodać albo [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) lub a, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) który używa protokołu HTTP (s) i `Basic` schematu uwierzytelniania.

    > [!NOTE]
    > W przypadku korzystania z .NET Framework 3,5 lub nowszych wersji można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu. Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.

    > [!TIP]
    > Aby uzyskać więcej informacji na temat korzystania \<netTcpBinding> z programu w tym kontekście, zobacz [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .

    1. W pliku konfiguracji, w obszarze [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.

    2. Dodaj [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element lub [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) do sekcji powiązań. Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).

    3. Ustaw `mode` atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message` , `Transport` lub `TransportWithMessageCredential` .

    4. Ustaw `clientCredentialType` atrybut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .

        W przypadku korzystania z zabezpieczeń komunikatów należy ustawić `clientCredentialType` atrybut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName` .

        W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S) Ustaw `clientCredentialType` atrybut [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic` .

        > [!NOTE]
        > Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu, a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> Właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , schemat uwierzytelniania niestandardowego używa podzestawu uwierzytelniania systemu Windows. Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.

    Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).

    Poniższy przykład pokazuje kod konfiguracji dla powiązania:

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

2. Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania poprawności nazwy użytkownika i hasła dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.

    1. Jako element podrzędny do [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.

    2. Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element do elementu.

    3. Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` odpowiednią wartość atrybutu.

    4. Dodaj [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do elementu.

    5. Dodaj [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .

    6. Ustaw wartość `userNamePasswordValidationMode` na `Custom` .

        > [!IMPORTANT]
        > Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu sprawdzania poprawności hasła.

    7. Ustaw wartość `customUserNamePasswordValidatorType` na typ, który reprezentuje swoją niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.

    W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment tego punktu:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła. Nie należy używać kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Zobacz też

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](how-to-use-the-aspnet-membership-provider.md)
- [Authentication](authentication-in-wcf.md)
