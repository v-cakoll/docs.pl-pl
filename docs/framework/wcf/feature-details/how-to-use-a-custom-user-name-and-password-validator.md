---
title: 'Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 3d01a29671f42e80fdb7ca45223007aa60273ba9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283259"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="2a46c-102">Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="2a46c-102">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="2a46c-103">Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="2a46c-103">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="2a46c-104">Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*.</span><span class="sxs-lookup"><span data-stu-id="2a46c-104">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="2a46c-105">Aby dołączyć niestandardową nazwę użytkownika i moduł sprawdzania haseł, Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a następnie skonfiguruj ją.</span><span class="sxs-lookup"><span data-stu-id="2a46c-105">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="2a46c-106">Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-106">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="2a46c-107">Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="2a46c-107">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="2a46c-108">Utwórz klasę pochodzącą z <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="2a46c-108">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="2a46c-109">Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a46c-109">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="2a46c-110">Nie należy używać kodu w poniższym przykładzie, który zastępuje metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2a46c-110">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="2a46c-111">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2a46c-111">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="2a46c-112">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, zgłoś <xref:System.ServiceModel.FaultException> w metodzie <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a46c-112">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="2a46c-113">Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="2a46c-113">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="2a46c-114">Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="2a46c-114">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="2a46c-115">W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takich jak [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)lub [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , który obsługuje zabezpieczenia komunikatów i typ poświadczeń `UserName`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-115">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="2a46c-116">W przypadku korzystania z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy dodać [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub [\<BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md),\<[NetTcpBinding >](../../configure-apps/file-schema/wcf/nettcpbinding.md) lub [\<CustomBinding >](../../configure-apps/file-schema/wcf/custombinding.md) , który używa protokołu HTTP (S) i schematu uwierzytelniania `Basic`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-116">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2a46c-117">W przypadku korzystania z .NET Framework 3,5 lub nowszych wersji można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu.</span><span class="sxs-lookup"><span data-stu-id="2a46c-117">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="2a46c-118">Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="2a46c-118">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="2a46c-119">Aby uzyskać więcej informacji na temat używania \<netTcpBinding > w tym kontekście, zobacz [\<security >](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-119">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="2a46c-120">W pliku konfiguracji, w obszarze [\<system. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) , dodaj element [> powiązania\<](../../configure-apps/file-schema/wcf/bindings.md) .</span><span class="sxs-lookup"><span data-stu-id="2a46c-120">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="2a46c-121">Dodaj element [\<wsHttpBinding >](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub [\<BasicHttpBinding >](../../configure-apps/file-schema/wcf/basichttpbinding.md) do sekcji powiązania.</span><span class="sxs-lookup"><span data-stu-id="2a46c-121">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="2a46c-122">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-122">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="2a46c-123">Ustaw `mode` atrybut [\<security >](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [\<security >](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) na `Message`, `Transport`lub `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-123">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="2a46c-124">Ustaw atrybut `clientCredentialType` [komunikatu\<>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [\<Transport >](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-124">Set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="2a46c-125">W przypadku korzystania z zabezpieczeń wiadomości Ustaw `clientCredentialType` atrybut [\<komunikatu >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-125">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="2a46c-126">W przypadku korzystania z zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP należy ustawić atrybut `clientCredentialType` [> transportu\<](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [\<transportu >](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) `Basic`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-126">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="2a46c-127">Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu, a właściwość <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, niestandardowy schemat uwierzytelniania używa podzestawu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="2a46c-127">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="2a46c-128">Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.</span><span class="sxs-lookup"><span data-stu-id="2a46c-128">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="2a46c-129">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-129">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="2a46c-130">Poniższy przykład pokazuje kod konfiguracji dla powiązania:</span><span class="sxs-lookup"><span data-stu-id="2a46c-130">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="2a46c-131">Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania par nazw użytkowników i haseł dla przychodzących tokenów zabezpieczających <xref:System.IdentityModel.Tokens.UserNameSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="2a46c-131">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="2a46c-132">Jako element podrzędny dla elementu [\<system. serviceModel >](../../configure-apps/file-schema/wcf/system-servicemodel.md) dodaj element [> zachowań\<](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2a46c-132">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="2a46c-133">Dodaj [>\<serviceBehaviors](../../configure-apps/file-schema/wcf/servicebehaviors.md) do elementu [> zachowań\<](../../configure-apps/file-schema/wcf/behaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2a46c-133">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="2a46c-134">Dodaj [\<zachowanie >](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) elementu i ustaw dla atrybutu `name` odpowiednią wartość.</span><span class="sxs-lookup"><span data-stu-id="2a46c-134">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="2a46c-135">Dodaj [>\<ServiceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md) do elementu [> zachowanie\<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2a46c-135">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="2a46c-136">Dodaj [>\<userNameAuthentication](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [>\<ServiceCredentials](../../configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="2a46c-136">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="2a46c-137">Ustaw `userNamePasswordValidationMode` na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2a46c-137">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="2a46c-138">Jeśli wartość `userNamePasswordValidationMode` nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu weryfikacji hasła.</span><span class="sxs-lookup"><span data-stu-id="2a46c-138">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="2a46c-139">Ustaw `customUserNamePasswordValidatorType` na typ, który reprezentuje swoją niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="2a46c-139">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="2a46c-140">Poniższy przykład pokazuje `<serviceCredentials>` fragmentu tego punktu:</span><span class="sxs-lookup"><span data-stu-id="2a46c-140">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="2a46c-141">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a46c-141">Example</span></span>

<span data-ttu-id="2a46c-142">Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="2a46c-142">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="2a46c-143">Nie należy używać kodu, który zastępuje metodę <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2a46c-143">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="2a46c-144">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2a46c-144">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="2a46c-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2a46c-145">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="2a46c-146">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2a46c-146">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="2a46c-147">Uwierzytelnianie</span><span class="sxs-lookup"><span data-stu-id="2a46c-147">Authentication</span></span>](authentication-in-wcf.md)
