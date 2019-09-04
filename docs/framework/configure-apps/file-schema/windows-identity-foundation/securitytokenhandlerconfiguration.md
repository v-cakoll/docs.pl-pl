---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: 330e52bd73a8032e4073fe434c852e5bdf8e1d47
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251888"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="cd1b9-101">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="cd1b9-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="cd1b9-102">Zapewnia konfigurację kolekcji programów obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="cd1b9-103">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cd1b9-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cd1b9-104">&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="cd1b9-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="cd1b9-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="cd1b9-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="cd1b9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="cd1b9-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="cd1b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**</span><span class="sxs-lookup"><span data-stu-id="cd1b9-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd1b9-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd1b9-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1b9-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="cd1b9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cd1b9-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1b9-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="cd1b9-111">Attributes</span></span>  
  
|<span data-ttu-id="cd1b9-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="cd1b9-112">Attribute</span></span>|<span data-ttu-id="cd1b9-113">Opis</span><span class="sxs-lookup"><span data-stu-id="cd1b9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd1b9-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="cd1b9-114">saveBootstrapContext</span></span>|<span data-ttu-id="cd1b9-115">Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="cd1b9-116">Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="cd1b9-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="cd1b9-117">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="cd1b9-118">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="cd1b9-118">maximumClockSkew</span></span>|<span data-ttu-id="cd1b9-119">A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="cd1b9-120">Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="cd1b9-121">Wartość domyślna to 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="cd1b9-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="cd1b9-122">Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="cd1b9-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="cd1b9-123">Maksymalne przechylenie zegara może być również ustawiane na poziomie usługi przez ustawienie `maximumClockSkew` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="cd1b9-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="cd1b9-124">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1b9-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="cd1b9-125">Child Elements</span></span>  
  
|<span data-ttu-id="cd1b9-126">Element</span><span class="sxs-lookup"><span data-stu-id="cd1b9-126">Element</span></span>|<span data-ttu-id="cd1b9-127">Opis</span><span class="sxs-lookup"><span data-stu-id="cd1b9-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd1b9-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="cd1b9-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="cd1b9-129">Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="cd1b9-130">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-130">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-131">\<pamięć podręczna ></span><span class="sxs-lookup"><span data-stu-id="cd1b9-131">\<caches></span></span>](caches.md)|<span data-ttu-id="cd1b9-132">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="cd1b9-133">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="cd1b9-134">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-134">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-135">\<certificateValidation ></span><span class="sxs-lookup"><span data-stu-id="cd1b9-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="cd1b9-136">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="cd1b9-137">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="cd1b9-138">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="cd1b9-139">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-139">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-140">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="cd1b9-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="cd1b9-141">Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="cd1b9-142">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-142">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-143">\<issuerTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="cd1b9-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="cd1b9-144">Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="cd1b9-145">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="cd1b9-146">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-146">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-147">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="cd1b9-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="cd1b9-148">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="cd1b9-149">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="cd1b9-150">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-150">Optional.</span></span>|  
|[<span data-ttu-id="cd1b9-151">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="cd1b9-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="cd1b9-152">Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="cd1b9-153">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="cd1b9-154">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1b9-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="cd1b9-155">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1b9-156">Element</span><span class="sxs-lookup"><span data-stu-id="cd1b9-156">Element</span></span>|<span data-ttu-id="cd1b9-157">Opis</span><span class="sxs-lookup"><span data-stu-id="cd1b9-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd1b9-158">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cd1b9-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="cd1b9-159">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd1b9-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd1b9-160">Remarks</span></span>  
 <span data-ttu-id="cd1b9-161">Ta sekcja zawiera wartości właściwości dla <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="cd1b9-162">Ustawienia skonfigurowane w tej sekcji zastępują te skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="cd1b9-163">Niektóre z tych ustawień mogą zostać zastąpione przez ustawienia, które są określone podczas dodawania programu obsługi do kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="cd1b9-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1b9-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd1b9-164">Example</span></span>  
  
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
