---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 29e18cdda9e18addef4f0f32fd30e9abf6af78fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793851"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="068b3-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="068b3-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="068b3-102">Udostępnia konfigurację dla kolekcji programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="068b3-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="068b3-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="068b3-103">\<system.identityModel></span></span>  
<span data-ttu-id="068b3-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="068b3-104">\<identityConfiguration></span></span>  
<span data-ttu-id="068b3-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="068b3-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="068b3-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="068b3-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="068b3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="068b3-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration saveBootstrapContext=xs:boolean  
          maximumClockSkew=TimeSpan>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="068b3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="068b3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="068b3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="068b3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="068b3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="068b3-110">Attributes</span></span>  
  
|<span data-ttu-id="068b3-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="068b3-111">Attribute</span></span>|<span data-ttu-id="068b3-112">Opis</span><span class="sxs-lookup"><span data-stu-id="068b3-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="068b3-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="068b3-113">saveBootstrapContext</span></span>|<span data-ttu-id="068b3-114">Określa, czy bootstrap tokeny mają być uwzględniane w tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="068b3-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="068b3-115">Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="068b3-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="068b3-116">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="068b3-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="068b3-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="068b3-117">maximumClockSkew</span></span>|<span data-ttu-id="068b3-118">Element <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara.</span><span class="sxs-lookup"><span data-stu-id="068b3-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="068b3-119">Określa maksymalna dopuszczalna niedokładność zegara, podczas wykonywania operacji zależne od czasu, takich jak sprawdzanie poprawności czas wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="068b3-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="068b3-120">Wartość domyślna to 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="068b3-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="068b3-121">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="068b3-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="068b3-122">Niedokładność zegara maksymalna mogą również ustawiać na poziomie usługi, ustawiając `maximumClockSkew` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="068b3-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="068b3-123">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="068b3-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="068b3-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="068b3-124">Child Elements</span></span>  
  
|<span data-ttu-id="068b3-125">Element</span><span class="sxs-lookup"><span data-stu-id="068b3-125">Element</span></span>|<span data-ttu-id="068b3-126">Opis</span><span class="sxs-lookup"><span data-stu-id="068b3-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="068b3-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="068b3-127">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="068b3-128">Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatory tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="068b3-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="068b3-129">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-129">Optional.</span></span>|  
|[<span data-ttu-id="068b3-130">\<caches></span><span class="sxs-lookup"><span data-stu-id="068b3-130">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="068b3-131">Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="068b3-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="068b3-132">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="068b3-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="068b3-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-133">Optional.</span></span>|  
|[<span data-ttu-id="068b3-134">\<certificateValidation></span><span class="sxs-lookup"><span data-stu-id="068b3-134">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="068b3-135">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="068b3-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="068b3-136">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="068b3-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="068b3-137">Te ustawienia zostaną zastąpione, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="068b3-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="068b3-138">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-138">Optional.</span></span>|  
|[<span data-ttu-id="068b3-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="068b3-139">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="068b3-140">Konfiguruje rejestru nazwy wystawcy, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="068b3-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="068b3-141">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-141">Optional.</span></span>|  
|[<span data-ttu-id="068b3-142">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="068b3-142">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="068b3-143">Rejestruje wystawcy program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="068b3-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="068b3-144">Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="068b3-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="068b3-145">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-145">Optional.</span></span>|  
|[<span data-ttu-id="068b3-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="068b3-146">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="068b3-147">Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="068b3-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="068b3-148">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="068b3-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="068b3-149">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-149">Optional.</span></span>|  
|[<span data-ttu-id="068b3-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="068b3-150">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="068b3-151">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="068b3-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="068b3-152">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="068b3-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="068b3-153">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="068b3-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="068b3-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="068b3-154">Parent Elements</span></span>  
  
|<span data-ttu-id="068b3-155">Element</span><span class="sxs-lookup"><span data-stu-id="068b3-155">Element</span></span>|<span data-ttu-id="068b3-156">Opis</span><span class="sxs-lookup"><span data-stu-id="068b3-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="068b3-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="068b3-157">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="068b3-158">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="068b3-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="068b3-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="068b3-159">Remarks</span></span>  
 <span data-ttu-id="068b3-160">Ta sekcja zawiera wartości właściwości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="068b3-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="068b3-161">Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="068b3-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="068b3-162">Niektóre z tych ustawień z kolei można zastąpić za pomocą ustawień, które są określone, gdy program obsługi zostanie dodany do kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="068b3-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="068b3-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="068b3-163">Example</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>   
      <securityTokenHandlerConfiguration>  
  
        <audienceUris>  
          <clear/>  
          <add value="http://www.example.com/myapp/" />  
        </audienceUris>  
  
        <issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel">  
          <trustedIssuers>  
            <add thumbprint="97249e1a … 4c9158de" name="contoso.com" />  
          </trustedIssuers>  
        </issuerNameRegistry>  
  
        <issuerTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
        <serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```
