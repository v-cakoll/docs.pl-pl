---
title: 'Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła'
description: Dowiedz się, jak dołączyć niestandardowy moduł sprawdzania poprawności haseł dla aplikacji WFC zamiast domyślnej weryfikacji nazwy użytkownika i hasła systemu Windows.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, username and password
ms.assetid: 8e08b74b-fa44-4018-b63d-0d0805f85e3f
ms.openlocfilehash: 7f69db7bf8248593b64cdae4378983c2460de597
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246795"
---
# <a name="how-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a37d0-103">Instrukcje: Używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="a37d0-103">How to: Use a Custom User Name and Password Validator</span></span>

<span data-ttu-id="a37d0-104">Domyślnie, gdy nazwa użytkownika i hasło są używane do uwierzytelniania, Windows Communication Foundation (WCF) używa systemu Windows do sprawdzania poprawności nazwy użytkownika i hasła.</span><span class="sxs-lookup"><span data-stu-id="a37d0-104">By default, when a user name and password is used for authentication, Windows Communication Foundation (WCF) uses Windows to validate the user name and password.</span></span> <span data-ttu-id="a37d0-105">Jednak funkcja WCF umożliwia używanie niestandardowych schematów nazw użytkowników i haseł, znanych również jako *walidatorów*.</span><span class="sxs-lookup"><span data-stu-id="a37d0-105">However, WCF allows for custom user name and password authentication schemes, also known as *validators*.</span></span> <span data-ttu-id="a37d0-106">Aby uwzględnić niestandardową nazwę użytkownika i moduł weryfikacji hasła, należy utworzyć klasę pochodzącą od, <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> a następnie ją skonfigurować.</span><span class="sxs-lookup"><span data-stu-id="a37d0-106">To incorporate a custom user name and password validator, create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> and then configure it.</span></span>

<span data-ttu-id="a37d0-107">Aby uzyskać przykładową aplikację, zobacz [Walidacja hasła nazwy użytkownika](../samples/user-name-password-validator.md).</span><span class="sxs-lookup"><span data-stu-id="a37d0-107">For a sample application, see [User Name Password Validator](../samples/user-name-password-validator.md).</span></span>

### <a name="to-create-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a37d0-108">Aby utworzyć niestandardową nazwę użytkownika i moduł weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="a37d0-108">To create a custom user name and password validator</span></span>

1. <span data-ttu-id="a37d0-109">Utwórz klasę, która pochodzi od <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> .</span><span class="sxs-lookup"><span data-stu-id="a37d0-109">Create a class that derives from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#3)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#3](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#3)]

2. <span data-ttu-id="a37d0-110">Zaimplementuj niestandardowy schemat uwierzytelniania, zastępując <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="a37d0-110">Implement the custom authentication scheme by overriding the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    <span data-ttu-id="a37d0-111">Nie należy używać kodu w poniższym przykładzie, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a37d0-111">Do not use the code in the following example that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="a37d0-112">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a37d0-112">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

    <span data-ttu-id="a37d0-113">Aby przywrócić błędy uwierzytelniania z powrotem do klienta, należy zgłosić <xref:System.ServiceModel.FaultException> <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="a37d0-113">To return authentication errors back to the client, throw a <xref:System.ServiceModel.FaultException> in the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method.</span></span>

    [!code-csharp[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#4)]
    [!code-vb[C_CustomUsernameAndPasswordValidator#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#4)]

### <a name="to-configure-a-service-to-use-a-custom-user-name-and-password-validator"></a><span data-ttu-id="a37d0-114">Aby skonfigurować usługę do korzystania z niestandardowej nazwy użytkownika i modułu weryfikacji hasła</span><span class="sxs-lookup"><span data-stu-id="a37d0-114">To configure a service to use a custom user name and password validator</span></span>

1. <span data-ttu-id="a37d0-115">Skonfiguruj powiązanie, które korzysta z zabezpieczeń komunikatów przed wszelkimi transportami lub zabezpieczeniami na poziomie transportu za pośrednictwem protokołu HTTP (S).</span><span class="sxs-lookup"><span data-stu-id="a37d0-115">Configure a binding that uses message security over any transport or transport-level security over HTTP(S).</span></span>

    <span data-ttu-id="a37d0-116">W przypadku korzystania z zabezpieczeń komunikatów należy dodać jedno z powiązań dostarczonych przez system, takich jak [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) lub, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) które obsługuje zabezpieczenia komunikatów i `UserName` Typ poświadczenia.</span><span class="sxs-lookup"><span data-stu-id="a37d0-116">When using message security, add one of the system-provided bindings, such as a  [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that supports message security and the `UserName` credential type.</span></span>

    <span data-ttu-id="a37d0-117">W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S) należy dodać albo [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) , a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) lub a, [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) który używa protokołu HTTP (s) i `Basic` schematu uwierzytelniania.</span><span class="sxs-lookup"><span data-stu-id="a37d0-117">When using transport-level security over HTTP(S), add either the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md), a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) or a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) that uses HTTP(S) and the `Basic` authentication scheme.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a37d0-118">W przypadku korzystania z .NET Framework 3,5 lub nowszych wersji można użyć niestandardowej nazwy użytkownika i modułu sprawdzania haseł z zabezpieczeniami komunikatów i transportu.</span><span class="sxs-lookup"><span data-stu-id="a37d0-118">When using .NET Framework 3.5 or later versions, you can use a custom username and password validator with message and transport security.</span></span> <span data-ttu-id="a37d0-119">Korzystając z programu WinFX, niestandardowa nazwa użytkownika i walidacja hasła mogą być używane tylko z zabezpieczeniami komunikatów.</span><span class="sxs-lookup"><span data-stu-id="a37d0-119">With WinFX, a custom username and password validator can only be used with message security.</span></span>

    > [!TIP]
    > <span data-ttu-id="a37d0-120">Aby uzyskać więcej informacji na temat korzystania \<netTcpBinding> z programu w tym kontekście, zobacz [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a37d0-120">For more information on using \<netTcpBinding> in this context, see [\<security>](../../configure-apps/file-schema/wcf/security-of-nettcpbinding.md).</span></span>

    1. <span data-ttu-id="a37d0-121">W pliku konfiguracji, w obszarze [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu, Dodaj [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span><span class="sxs-lookup"><span data-stu-id="a37d0-121">In the configuration file, under the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) element.</span></span>

    2. <span data-ttu-id="a37d0-122">Dodaj [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element lub [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) do sekcji powiązań.</span><span class="sxs-lookup"><span data-stu-id="a37d0-122">Add a [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) or [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) element to the bindings section.</span></span> <span data-ttu-id="a37d0-123">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a37d0-123">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    3. <span data-ttu-id="a37d0-124">Ustaw `mode` atrybut [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) lub [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) do `Message` , `Transport` lub `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="a37d0-124">Set the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) or [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

    4. <span data-ttu-id="a37d0-125">Ustaw `clientCredentialType` atrybut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) lub [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="a37d0-125">Set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md).</span></span>

        <span data-ttu-id="a37d0-126">W przypadku korzystania z zabezpieczeń komunikatów należy ustawić `clientCredentialType` atrybut [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) na `UserName` .</span><span class="sxs-lookup"><span data-stu-id="a37d0-126">When using message security, set the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) to `UserName`.</span></span>

        <span data-ttu-id="a37d0-127">W przypadku używania zabezpieczeń na poziomie transportu za pośrednictwem protokołu HTTP (S) Ustaw `clientCredentialType` atrybut [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) lub [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) na `Basic` .</span><span class="sxs-lookup"><span data-stu-id="a37d0-127">When using transport-level security over HTTP(S), set the `clientCredentialType` attribute of the [\<transport>](../../configure-apps/file-schema/wcf/transport-of-wshttpbinding.md) or [\<transport>](../../configure-apps/file-schema/wcf/transport-of-basichttpbinding.md) to `Basic`.</span></span>

        > [!NOTE]
        > <span data-ttu-id="a37d0-128">Gdy usługa WCF jest hostowana w usłudze Internet Information Services (IIS) przy użyciu zabezpieczeń na poziomie transportu, a <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> Właściwość jest ustawiona na <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom> , schemat uwierzytelniania niestandardowego używa podzestawu uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a37d0-128">When a WCF service is hosted in Internet Information Services (IIS) using transport-level security and the <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential.UserNamePasswordValidationMode%2A> property is set to <xref:System.ServiceModel.Security.UserNamePasswordValidationMode.Custom>, the custom authentication scheme uses a subset of Windows authentication.</span></span> <span data-ttu-id="a37d0-129">Oznacza to, że w tym scenariuszu usługi IIS wykonują uwierzytelnianie systemu Windows przed wywołaniem niestandardowego wystawcy uwierzytelnienia w usłudze WCF.</span><span class="sxs-lookup"><span data-stu-id="a37d0-129">That is because in this scenario, IIS performs Windows authentication prior to WCF invoking the custom authenticator.</span></span>

    <span data-ttu-id="a37d0-130">Aby uzyskać więcej informacji na temat tworzenia elementu powiązania WCF, zobacz [How to: Określanie powiązania usługi w konfiguracji](../how-to-specify-a-service-binding-in-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a37d0-130">For more information about creating an WCF binding element, see [How to: Specify a Service Binding in Configuration](../how-to-specify-a-service-binding-in-configuration.md).</span></span>

    <span data-ttu-id="a37d0-131">Poniższy przykład pokazuje kod konfiguracji dla powiązania:</span><span class="sxs-lookup"><span data-stu-id="a37d0-131">The following example shows the configuration code for the binding:</span></span>

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

2. <span data-ttu-id="a37d0-132">Skonfiguruj zachowanie, które określa, że niestandardowa nazwa użytkownika i walidacja hasła są używane do sprawdzania poprawności nazwy użytkownika i hasła dla przychodzących <xref:System.IdentityModel.Tokens.UserNameSecurityToken> tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="a37d0-132">Configure a behavior that specifies that a custom user name and password validator is used to validate user name and password pairs for incoming <xref:System.IdentityModel.Tokens.UserNameSecurityToken> security tokens.</span></span>

    1. <span data-ttu-id="a37d0-133">Jako element podrzędny do [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) elementu Dodaj [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span><span class="sxs-lookup"><span data-stu-id="a37d0-133">As a child to the [\<system.serviceModel>](../../configure-apps/file-schema/wcf/system-servicemodel.md) element, add a [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    2. <span data-ttu-id="a37d0-134">Dodaj [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element do elementu.</span><span class="sxs-lookup"><span data-stu-id="a37d0-134">Add a [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) element.</span></span>

    3. <span data-ttu-id="a37d0-135">Dodaj [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element i ustaw `name` odpowiednią wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a37d0-135">Add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element and set the `name` attribute to an appropriate value.</span></span>

    4. <span data-ttu-id="a37d0-136">Dodaj [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element do elementu.</span><span class="sxs-lookup"><span data-stu-id="a37d0-136">Add a [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) to the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) element.</span></span>

    5. <span data-ttu-id="a37d0-137">Dodaj [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) do [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="a37d0-137">Add a [\<userNameAuthentication>](../../configure-apps/file-schema/wcf/usernameauthentication.md) to the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md).</span></span>

    6. <span data-ttu-id="a37d0-138">Ustaw wartość `userNamePasswordValidationMode` na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="a37d0-138">Set the `userNamePasswordValidationMode` to `Custom`.</span></span>

        > [!IMPORTANT]
        > <span data-ttu-id="a37d0-139">Jeśli `userNamePasswordValidationMode` wartość nie jest ustawiona, WCF używa uwierzytelniania systemu Windows zamiast niestandardowej nazwy użytkownika i modułu sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="a37d0-139">If the `userNamePasswordValidationMode` value is not set, WCF uses Windows authentication instead of the custom user name and password validator.</span></span>

    7. <span data-ttu-id="a37d0-140">Ustaw wartość `customUserNamePasswordValidatorType` na typ, który reprezentuje swoją niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="a37d0-140">Set the `customUserNamePasswordValidatorType` to the type that represents your custom user name and password validator.</span></span>

    <span data-ttu-id="a37d0-141">W poniższym przykładzie przedstawiono `<serviceCredentials>` fragment tego punktu:</span><span class="sxs-lookup"><span data-stu-id="a37d0-141">The following example shows the `<serviceCredentials>` fragment to this point:</span></span>

    ```xml
    <serviceCredentials>
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService.CustomUserNameValidator, service" />
    </serviceCredentials>
    ```

## <a name="example"></a><span data-ttu-id="a37d0-142">Przykład</span><span class="sxs-lookup"><span data-stu-id="a37d0-142">Example</span></span>

<span data-ttu-id="a37d0-143">Poniższy przykład kodu pokazuje, jak utworzyć niestandardową nazwę użytkownika i moduł sprawdzania poprawności hasła.</span><span class="sxs-lookup"><span data-stu-id="a37d0-143">The following code example demonstrates how to create a custom user name and password validator.</span></span> <span data-ttu-id="a37d0-144">Nie należy używać kodu, który zastępuje <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> metodę w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a37d0-144">Do not use the code that overrides the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method in a production environment.</span></span> <span data-ttu-id="a37d0-145">Zastąp kod własną niestandardową nazwą użytkownika i schematem walidacji hasła, co może wiązać się z pobraniem par nazw użytkowników i haseł z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a37d0-145">Replace the code with your custom user name and password validation scheme, which might involve retrieving user name and password pairs from a database.</span></span>

[!code-csharp[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#1)]
[!code-vb[C_CustomUsernameAndPasswordValidator#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#1)]
[!code-csharp[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_customusernameandpasswordvalidator/cs/service.cs#2)]
[!code-vb[C_CustomUsernameAndPasswordValidator#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_customusernameandpasswordvalidator/vb/service.vb#2)]

## <a name="see-also"></a><span data-ttu-id="a37d0-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a37d0-146">See also</span></span>

- <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>
- [<span data-ttu-id="a37d0-147">Instrukcje: użycie dostawcy członkostwa platformy ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a37d0-147">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)
- [<span data-ttu-id="a37d0-148">Authentication</span><span class="sxs-lookup"><span data-stu-id="a37d0-148">Authentication</span></span>](authentication-in-wcf.md)
