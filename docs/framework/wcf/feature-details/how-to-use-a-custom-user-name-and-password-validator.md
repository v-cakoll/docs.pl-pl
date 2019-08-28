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
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="8aef6-102">Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="8aef6-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="8aef6-103">Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="8aef6-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="8aef6-104">Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*.</span><span class="sxs-lookup"><span data-stu-id="8aef6-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="8aef6-105">Aby uwzględnić niestandardową nazwę użytkownika i moduł weryfikacji hasła, należy utworzyć klasę pochodzącą od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> , a następnie ją skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="8aef6-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="8aef6-106">Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="8aef6-106">For a sample application, see [User Name Password Validator](../../../../docs/framework/wcf/samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="8aef6-107">Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="8aef6-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="8aef6-108">Utwórz klasę, która pochodzi od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="8aef6-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="8aef6-109">Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="8aef6-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="8aef6-110">Nie należy używać kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="8aef6-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="8aef6-111">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8aef6-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="8aef6-112">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="8aef6-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="8aef6-113">Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="8aef6-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="8aef6-114">Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="8aef6-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="8aef6-115">W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takich jak [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)lub niestandardowy elementbinding [ \<>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , który obsługuje zabezpieczenia komunikatów i `UserName` typ poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="8aef6-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="8aef6-116">W przypadku korzystania z [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy dodać WSHttpBinding > lub [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) [ \<BasicHttpBinding >, NetTcpBinding > lub niestandardowybinding > ](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)używa protokołu HTTP (S) i `Basic` schematu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="8aef6-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8aef6-117">Gdy [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] jest używany program lub nowszy, można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu.</span><span class="sxs-lookup"><span data-stu-id="8aef6-117">When [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] or later is used, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="8aef6-118">Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8aef6-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="8aef6-119">Aby uzyskać więcej informacji o \<korzystaniu z NetTcpBinding > w tym kontekście, zobacz [ \<zabezpieczenia >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8aef6-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)</span></span>

    1. <span data-ttu-id="8aef6-120">W pliku konfiguracji, w obszarze [ \<system. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) , Dodaj [ \<element > powiązania](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="8aef6-120">In the configuration file, under the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="8aef6-121">Dodaj element [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) WSHttpBinding > lub BasicHttpBinding > do sekcji powiązania. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="8aef6-121">Add a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="8aef6-122">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8aef6-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="8aef6-123">`mode` Ustaw atrybut `Message` [ >zabezpieczeńlub\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) [ >\<zabezpieczeń](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na, ,`Transport`lub .`TransportWithMessageCredential`</span><span class="sxs-lookup"><span data-stu-id="8aef6-123">Set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="8aef6-124">`clientCredentialType` Ustaw [atrybut komunikatu>lub\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) [ >\<](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md)transportowego.</span><span class="sxs-lookup"><span data-stu-id="8aef6-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="8aef6-125">W przypadku korzystania z zabezpieczeń wiadomości Ustaw `clientCredentialType` atrybut [ \<> komunikatu](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na. `UserName`</span><span class="sxs-lookup"><span data-stu-id="8aef6-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="8aef6-126">W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S `clientCredentialType` ) ustaw atrybut [ \<> transportu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [ \<> transportu](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic`.</span><span class="sxs-lookup"><span data-stu-id="8aef6-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="8aef6-127">Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> , a właściwość jest <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>ustawiona na, schemat uwierzytelniania niestandardowego używa podzestawu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8aef6-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="8aef6-128">Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.</span><span class="sxs-lookup"><span data-stu-id="8aef6-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="8aef6-129">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, [zobacz How to: Określ powiązanie usługi w konfiguracji](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="8aef6-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="8aef6-130">Poniższy przykład pokazuje kod konfiguracji dla powiązania.</span><span class="sxs-lookup"><span data-stu-id="8aef6-130">The following example shows the configuration code for the binding.</span></span>

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

2. <span data-ttu-id="8aef6-131">Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania poprawności nazwy użytkownika i <xref:System.IdentityModel.Tokens.UserNameSecurityToken> hasła dla przychodzących tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="8aef6-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="8aef6-132">Jako element podrzędny do [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) elementu System. ServiceModel >, Dodaj > element Behaviors.</span><span class="sxs-lookup"><span data-stu-id="8aef6-132">As a child to the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="8aef6-133">Dodaj > serviceBehaviors do [> zachowań elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="8aef6-133">Add a [\<serviceBehaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="8aef6-134">Dodaj zachowanie [ >elementuiustawodpowiedniąwartośćatrybutu.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) `name`</span><span class="sxs-lookup"><span data-stu-id="8aef6-134">Add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="8aef6-135">Dodaj > ServiceCredentials do [> zachowań elementu. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8aef6-135">Add a [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="8aef6-136">Dodaj [> userNameAuthentication do > ServiceCredentials. \<](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="8aef6-136">Add a [\<userNameAuthentication>](../../../../docs/framework/configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="8aef6-137">Ustaw wartość `Custom`na. `userNamePasswordValidationMode`</span><span class="sxs-lookup"><span data-stu-id="8aef6-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="8aef6-138">`userNamePasswordValidationMode` Jeśli wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="8aef6-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="8aef6-139">Ustaw wartość `customUserNamePasswordValidatorType` na typ, który reprezentuje swoją niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="8aef6-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="8aef6-140">Poniższy przykład pokazuje `<serviceCredentials>` fragment tego punktu.</span><span class="sxs-lookup"><span data-stu-id="8aef6-140">The following example shows the `<serviceCredentials>` fragment to this point.</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="8aef6-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="8aef6-141">Example</span></span>

<span data-ttu-id="8aef6-142">Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="8aef6-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="8aef6-143">Nie należy używać kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="8aef6-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="8aef6-144">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="8aef6-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="8aef6-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aef6-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="8aef6-146">Instrukcje: Korzystanie z dostawcy członkostwa ASP.NET</span><span class="sxs-lookup"><span data-stu-id="8aef6-146">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="8aef6-147">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="8aef6-147">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)
