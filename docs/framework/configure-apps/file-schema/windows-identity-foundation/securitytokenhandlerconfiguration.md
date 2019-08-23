---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 0aefaa808dfc32085a208420fcd582b1671acc64
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942446"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="e2ee8-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e2ee8-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="e2ee8-102">Zapewnia konfigurację kolekcji programów obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-102">Provides configuration for the collection of token handlers.</span></span>  
  
 <span data-ttu-id="e2ee8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e2ee8-103">\<system.identityModel></span></span>  
<span data-ttu-id="e2ee8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e2ee8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="e2ee8-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e2ee8-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e2ee8-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="e2ee8-106">\<securityTokenHandlerConfiguration></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ee8-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e2ee8-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2ee8-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e2ee8-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e2ee8-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2ee8-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e2ee8-110">Attributes</span></span>  
  
|<span data-ttu-id="e2ee8-111">Atrybut</span><span class="sxs-lookup"><span data-stu-id="e2ee8-111">Attribute</span></span>|<span data-ttu-id="e2ee8-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ee8-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e2ee8-113">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="e2ee8-113">saveBootstrapContext</span></span>|<span data-ttu-id="e2ee8-114">Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-114">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="e2ee8-115">Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="e2ee8-115">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="e2ee8-116">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-116">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="e2ee8-117">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="e2ee8-117">maximumClockSkew</span></span>|<span data-ttu-id="e2ee8-118">A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-118">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="e2ee8-119">Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-119">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="e2ee8-120">Wartość domyślna to 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="e2ee8-120">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="e2ee8-121">Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="e2ee8-121">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="e2ee8-122">Maksymalne przechylenie zegara może być również ustawiane na poziomie usługi przez ustawienie `maximumClockSkew` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="e2ee8-122">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="e2ee8-123">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-123">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2ee8-124">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e2ee8-124">Child Elements</span></span>  
  
|<span data-ttu-id="e2ee8-125">Element</span><span class="sxs-lookup"><span data-stu-id="e2ee8-125">Element</span></span>|<span data-ttu-id="e2ee8-126">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ee8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2ee8-127">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="e2ee8-127">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="e2ee8-128">Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-128">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="e2ee8-129">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-129">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-130">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="e2ee8-130">\<caches></span></span>](caches.md)|<span data-ttu-id="e2ee8-131">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-131">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="e2ee8-132">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-132">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2ee8-133">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-133">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-134">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="e2ee8-134">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="e2ee8-135">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-135">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="e2ee8-136">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-136">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2ee8-137">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-137">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="e2ee8-138">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-138">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-139">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="e2ee8-139">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="e2ee8-140">Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-140">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2ee8-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-141">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-142">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e2ee8-142">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="e2ee8-143">Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-143">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2ee8-144">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-144">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="e2ee8-145">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-145">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-146">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="e2ee8-146">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="e2ee8-147">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-147">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e2ee8-148">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-148">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e2ee8-149">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-149">Optional.</span></span>|  
|[<span data-ttu-id="e2ee8-150">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="e2ee8-150">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="e2ee8-151">Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-151">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="e2ee8-152">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-152">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="e2ee8-153">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-153">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2ee8-154">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e2ee8-154">Parent Elements</span></span>  
  
|<span data-ttu-id="e2ee8-155">Element</span><span class="sxs-lookup"><span data-stu-id="e2ee8-155">Element</span></span>|<span data-ttu-id="e2ee8-156">Opis</span><span class="sxs-lookup"><span data-stu-id="e2ee8-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2ee8-157">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e2ee8-157">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="e2ee8-158">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-158">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2ee8-159">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2ee8-159">Remarks</span></span>  
 <span data-ttu-id="e2ee8-160">Ta sekcja zawiera wartości właściwości dla <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-160">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="e2ee8-161">Ustawienia skonfigurowane w tej sekcji zastępują te skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-161">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="e2ee8-162">Niektóre z tych ustawień mogą zostać zastąpione przez ustawienia, które są określone podczas dodawania programu obsługi do kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="e2ee8-162">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e2ee8-163">Przykład</span><span class="sxs-lookup"><span data-stu-id="e2ee8-163">Example</span></span>  
  
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
