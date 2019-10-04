---
title: 'Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 98ffad7e717aac949509fa701c77d8ba2b80a695
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834692"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a>Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła

Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła. Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*. Aby uwzględnić niestandardową nazwę użytkownika i sprawdzanie hasła, Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, a następnie skonfiguruj ją.

Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../samples/user-name-password-validator.md).

### <a name="to-create-a-custom-user-name-and-password-validator"></a>Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła

1. Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    Nie należy używać kodu w poniższym przykładzie, który zastępuje metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

    Aby przywrócić błędy uwierzytelniania z powrotem do klienta, zgłoś <xref:System.ServiceModel.FaultException> w metodzie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a>Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła

1. Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).

    W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takie jak [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)lub [> \<customBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , które obsługuje zabezpieczenia komunikatów i typ poświadczeń `UserName`.

    W przypadku korzystania z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy dodać [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md), @no__t [5NetTcpBinding >](../../configure-apps/file-schema/wcf/nettcpbinding.md) lub @no__t [-7customBinding >](../../configure-apps/file-schema/wcf/custombinding.md) , który używa protokołu HTTP (S) i schemat uwierzytelniania `Basic`.

    > [!NOTE]
    > W przypadku użycia wartości [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] lub nowszej można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu. Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.

    > [!TIP]
    > Aby uzyskać więcej informacji na temat używania \<netTcpBinding > w tym kontekście, zobacz [\<security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).

    1. W pliku konfiguracji, w obszarze [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) , dodaj element [> \<bindings](../../configure-apps/file-schema/wcf/bindings.md) .

    2. Dodaj element [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub [\<basicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) do sekcji powiązania. Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).

    3. Ustaw atrybut `mode` [\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message`, `Transport` lub `TransportWithMessageCredential`.

    4. Ustaw atrybut `clientCredentialType` [> \<message](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [\<Transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).

        W przypadku korzystania z zabezpieczeń wiadomości ustaw atrybut `clientCredentialType` [> \<message](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName`.

        W przypadku korzystania z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy ustawić atrybut `clientCredentialType` [> \<Transport](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [\<transport >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic`.

        > [!NOTE]
        > Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu, a właściwość <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, schemat niestandardowego uwierzytelniania używa podzestawu uwierzytelniania systemu Windows. Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.

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

2. Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania poprawności nazwy użytkownika i hasła dla przychodzących tokenów zabezpieczających <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.

    1. Jako element podrzędny do [\<System. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) , dodaj element [> \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    2. Dodaj [> \<serviceBehaviors](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [> \<behaviors](../../configure-apps/file-schema/wcf/behaviors.md) .

    3. Dodaj element [\<behavior >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) i ustaw dla atrybutu `name` odpowiednią wartość.

    4. Dodaj [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) do elementu [> \<behavior](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .

    5. Dodaj [> \<userNameAuthentication](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [> \<serviceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md).

    6. Ustaw wartość `userNamePasswordValidationMode` na `Custom`.

        > [!IMPORTANT]
        > Jeśli wartość `userNamePasswordValidationMode` nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu weryfikacji hasła.

    7. Ustaw wartość `customUserNamePasswordValidatorType` na typ, który reprezentuje niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.

    Poniższy przykład pokazuje fragment `<serviceCredentials>` w tym punkcie:

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a>Przykład

Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła. Nie należy używać kodu, który zastępuje metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> w środowisku produkcyjnym. Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [Instrukcje: korzystanie z dostawcy członkostwa ASP.NET](how-to-use-the-aspnet-membership-provider.md)
- [Uwierzytelnianie](authentication-in-wcf.md)
