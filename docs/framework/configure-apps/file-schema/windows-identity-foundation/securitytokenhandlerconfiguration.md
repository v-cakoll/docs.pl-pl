---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 168bdc4fbf640b201ebc61462d04727c23f838f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32758428"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a><span data-ttu-id="3af0c-102">&lt;securityTokenHandlerConfiguration&gt;</span><span class="sxs-lookup"><span data-stu-id="3af0c-102">&lt;securityTokenHandlerConfiguration&gt;</span></span>
<span data-ttu-id="3af0c-103">Udostępnia konfiguracji dla kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-103">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="3af0c-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="3af0c-104">\<system.identityModel></span></span>  
<span data-ttu-id="3af0c-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3af0c-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3af0c-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="3af0c-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="3af0c-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3af0c-107">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3af0c-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3af0c-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3af0c-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3af0c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3af0c-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3af0c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3af0c-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3af0c-111">Attributes</span></span>  
  
|<span data-ttu-id="3af0c-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3af0c-112">Attribute</span></span>|<span data-ttu-id="3af0c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3af0c-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3af0c-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="3af0c-114">saveBootstrapContext</span></span>|<span data-ttu-id="3af0c-115">Określa, czy tokeny bootstrap powinny być objęte tokenu sesji.</span><span class="sxs-lookup"><span data-stu-id="3af0c-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="3af0c-116">Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3af0c-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="3af0c-117">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="3af0c-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="3af0c-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="3af0c-118">maximumClockSkew</span></span>|<span data-ttu-id="3af0c-119">A <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara.</span><span class="sxs-lookup"><span data-stu-id="3af0c-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="3af0c-120">Steruje maksymalna dopuszczalna niedokładność zegara podczas wykonywania operacji harmonogramów, takich jak sprawdzanie poprawności czasu wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="3af0c-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="3af0c-121">Wartość domyślna to 5 minut, "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="3af0c-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="3af0c-122">Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartości Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3af0c-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="3af0c-123">Maksymalna niedokładność zegara mogą także umieszczać na poziomie usługi przez ustawienie `maximumClockSkew` atrybutu [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="3af0c-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span> <span data-ttu-id="3af0c-124">Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.</span><span class="sxs-lookup"><span data-stu-id="3af0c-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3af0c-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3af0c-125">Child Elements</span></span>  
  
|<span data-ttu-id="3af0c-126">Element</span><span class="sxs-lookup"><span data-stu-id="3af0c-126">Element</span></span>|<span data-ttu-id="3af0c-127">Opis</span><span class="sxs-lookup"><span data-stu-id="3af0c-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3af0c-128">\<audienceUris ></span><span class="sxs-lookup"><span data-stu-id="3af0c-128">\<audienceUris></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|<span data-ttu-id="3af0c-129">Określa zestaw identyfikatorów URI, które są dopuszczalne identyfikatory tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="3af0c-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="3af0c-130">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-130">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-131">\<buforuje ></span><span class="sxs-lookup"><span data-stu-id="3af0c-131">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="3af0c-132">Rejestruje pamięci podręczne tokeny sesji i wykrywania powtórzeń tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="3af0c-133">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3af0c-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3af0c-134">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-134">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="3af0c-135">\<certificateValidation></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|<span data-ttu-id="3af0c-136">Określa ustawienia, które programy obsługi token służący do weryfikowania certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="3af0c-137">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3af0c-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3af0c-138">Te ustawienia zostały zastąpione, jeśli określony program obsługi jest skonfigurowany z własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="3af0c-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="3af0c-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-139">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-140">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="3af0c-140">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="3af0c-141">Konfiguruje rejestru nazwy dostawcy, który jest używany przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3af0c-142">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-142">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="3af0c-143">\<issuerTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|<span data-ttu-id="3af0c-144">Rejestruje mechanizm rozpoznawania tokenów wystawcy, używanego przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3af0c-145">Program rozpoznawania nazw tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="3af0c-146">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-146">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-147">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="3af0c-147">\<serviceTokenResolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|<span data-ttu-id="3af0c-148">Rejestruje mechanizm rozpoznawania tokenu usługi, używany przez programy obsługi zdarzeń w kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="3af0c-149">Program rozpoznawania nazw tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="3af0c-150">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-150">Optional.</span></span>|  
|[<span data-ttu-id="3af0c-151">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="3af0c-151">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|<span data-ttu-id="3af0c-152">Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="3af0c-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="3af0c-153">Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3af0c-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="3af0c-154">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="3af0c-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3af0c-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3af0c-155">Parent Elements</span></span>  
  
|<span data-ttu-id="3af0c-156">Element</span><span class="sxs-lookup"><span data-stu-id="3af0c-156">Element</span></span>|<span data-ttu-id="3af0c-157">Opis</span><span class="sxs-lookup"><span data-stu-id="3af0c-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3af0c-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="3af0c-158">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="3af0c-159">Określa kolekcję programów obsługi tokenu zabezpieczeń, które są zarejestrowane z punktem końcowym.</span><span class="sxs-lookup"><span data-stu-id="3af0c-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3af0c-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3af0c-160">Remarks</span></span>  
 <span data-ttu-id="3af0c-161">Ta sekcja zawiera wartości właściwości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3af0c-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="3af0c-162">Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="3af0c-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="3af0c-163">Niektóre z tych ustawień z kolei można zastąpić ustawienia, które są określone, gdy program obsługi zostanie dodany do kolekcji programu obsługi tokenów zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="3af0c-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3af0c-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="3af0c-164">Example</span></span>  
  
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
