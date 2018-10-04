---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793282"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="44637-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="44637-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="44637-103">Udostępnia konfigurację dla kolekcji programy obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="44637-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="44637-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="44637-104">\<system.identityModel></span></span>  
<span data-ttu-id="44637-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="44637-105">\<identityConfiguration></span></span>  
<span data-ttu-id="44637-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="44637-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="44637-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="44637-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44637-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="44637-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44637-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="44637-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44637-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="44637-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44637-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="44637-111">Attributes</span></span>  
  
|<span data-ttu-id="44637-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="44637-112">Attribute</span></span>|<span data-ttu-id="44637-113">Opis</span><span class="sxs-lookup"><span data-stu-id="44637-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44637-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="44637-114">saveBootstrapContext</span></span>|<span data-ttu-id="44637-115">Określa, czy bootstrap tokeny mają być uwzględniane w tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="44637-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="44637-116">Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="44637-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="44637-117">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="44637-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="44637-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="44637-118">maximumClockSkew</span></span>|<span data-ttu-id="44637-119">Element <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara.</span><span class="sxs-lookup"><span data-stu-id="44637-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="44637-120">Określa maksymalna dopuszczalna niedokładność zegara, podczas wykonywania operacji zależne od czasu, takich jak sprawdzanie poprawności czas wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="44637-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="44637-121">Wartość domyślna to 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="44637-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="44637-122">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="44637-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="44637-123">Niedokładność zegara maksymalna mogą również ustawiać na poziomie usługi, ustawiając `maximumClockSkew` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="44637-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="44637-124">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="44637-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44637-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="44637-125">Child Elements</span></span>  
  
|<span data-ttu-id="44637-126">Element</span><span class="sxs-lookup"><span data-stu-id="44637-126">Element</span></span>|<span data-ttu-id="44637-127">Opis</span><span class="sxs-lookup"><span data-stu-id="44637-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44637-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="44637-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="44637-129">Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatory tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="44637-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="44637-130">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-130">Optional.</span></span>|  
|[<span data-ttu-id="44637-131">\<pamięci podręczne ></span><span class="sxs-lookup"><span data-stu-id="44637-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="44637-132">Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="44637-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="44637-133">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="44637-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="44637-134">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-134">Optional.</span></span>|  
|[<span data-ttu-id="44637-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="44637-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="44637-136">Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="44637-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="44637-137">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="44637-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="44637-138">Te ustawienia zostaną zastąpione, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="44637-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="44637-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-139">Optional.</span></span>|  
|[<span data-ttu-id="44637-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="44637-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="44637-141">Konfiguruje rejestru nazwy wystawcy, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="44637-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="44637-142">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-142">Optional.</span></span>|  
|[<span data-ttu-id="44637-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="44637-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="44637-144">Rejestruje wystawcy program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="44637-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="44637-145">Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="44637-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="44637-146">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-146">Optional.</span></span>|  
|[<span data-ttu-id="44637-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="44637-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="44637-148">Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="44637-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="44637-149">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="44637-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="44637-150">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-150">Optional.</span></span>|  
|[<span data-ttu-id="44637-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="44637-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="44637-152">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="44637-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="44637-153">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="44637-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="44637-154">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="44637-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="44637-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="44637-155">Parent Elements</span></span>  
  
|<span data-ttu-id="44637-156">Element</span><span class="sxs-lookup"><span data-stu-id="44637-156">Element</span></span>|<span data-ttu-id="44637-157">Opis</span><span class="sxs-lookup"><span data-stu-id="44637-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44637-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="44637-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="44637-159">Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="44637-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44637-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44637-160">Remarks</span></span>  
 <span data-ttu-id="44637-161">Ta sekcja zawiera wartości właściwości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="44637-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="44637-162">Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="44637-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="44637-163">Niektóre z tych ustawień z kolei można zastąpić za pomocą ustawień, które są określone, gdy program obsługi zostanie dodany do kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="44637-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44637-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="44637-164">Example</span></span>  
  
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
