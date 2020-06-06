---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152570"
---
# \<securityTokenHandlerConfiguration>
<span data-ttu-id="7c9b0-101">Zapewnia konfigurację kolekcji programów obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-101">Provides configuration for the collection of token handlers.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**  
  
## <a name="syntax"></a><span data-ttu-id="7c9b0-102">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c9b0-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c9b0-103">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="7c9b0-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7c9b0-104">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c9b0-105">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="7c9b0-105">Attributes</span></span>  
  
|<span data-ttu-id="7c9b0-106">Atrybut</span><span class="sxs-lookup"><span data-stu-id="7c9b0-106">Attribute</span></span>|<span data-ttu-id="7c9b0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7c9b0-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7c9b0-108">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="7c9b0-108">saveBootstrapContext</span></span>|<span data-ttu-id="7c9b0-109">Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-109">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="7c9b0-110">Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu dla [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-110">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="7c9b0-111">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-111">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="7c9b0-112">maximumClockSkew</span><span class="sxs-lookup"><span data-stu-id="7c9b0-112">maximumClockSkew</span></span>|<span data-ttu-id="7c9b0-113">A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-113">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="7c9b0-114">Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-114">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="7c9b0-115">Wartość domyślna to 5 minut, "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="7c9b0-115">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="7c9b0-116">Aby uzyskać więcej informacji na temat sposobu określania <xref:System.TimeSpan> wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="7c9b0-116">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="7c9b0-117">Maksymalne przechylenie zegara może być również ustawiane na poziomie usługi przez ustawienie `maximumClockSkew` atrybutu dla [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-117">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="7c9b0-118">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-118">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7c9b0-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="7c9b0-119">Child Elements</span></span>  
  
|<span data-ttu-id="7c9b0-120">Element</span><span class="sxs-lookup"><span data-stu-id="7c9b0-120">Element</span></span>|<span data-ttu-id="7c9b0-121">Opis</span><span class="sxs-lookup"><span data-stu-id="7c9b0-121">Description</span></span>|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|<span data-ttu-id="7c9b0-122">Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami tej jednostki uzależnionej.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-122">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="7c9b0-123">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-123">Optional.</span></span>|  
|[\<caches>](caches.md)|<span data-ttu-id="7c9b0-124">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-124">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="7c9b0-125">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-125">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="7c9b0-126">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-126">Optional.</span></span>|  
|[\<certificateValidation>](certificatevalidation.md)|<span data-ttu-id="7c9b0-127">Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-127">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="7c9b0-128">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-128">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="7c9b0-129">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-129">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="7c9b0-130">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-130">Optional.</span></span>|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="7c9b0-131">Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-131">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="7c9b0-132">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-132">Optional.</span></span>|  
|[\<issuerTokenResolver>](issuertokenresolver.md)|<span data-ttu-id="7c9b0-133">Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-133">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="7c9b0-134">Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-134">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="7c9b0-135">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-135">Optional.</span></span>|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|<span data-ttu-id="7c9b0-136">Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-136">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="7c9b0-137">Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-137">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="7c9b0-138">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-138">Optional.</span></span>|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|<span data-ttu-id="7c9b0-139">Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-139">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="7c9b0-140">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-140">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="7c9b0-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-141">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7c9b0-142">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="7c9b0-142">Parent Elements</span></span>  
  
|<span data-ttu-id="7c9b0-143">Element</span><span class="sxs-lookup"><span data-stu-id="7c9b0-143">Element</span></span>|<span data-ttu-id="7c9b0-144">Opis</span><span class="sxs-lookup"><span data-stu-id="7c9b0-144">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="7c9b0-145">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-145">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9b0-146">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c9b0-146">Remarks</span></span>  
 <span data-ttu-id="7c9b0-147">Ta sekcja zawiera wartości właściwości dla <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-147">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="7c9b0-148">Ustawienia skonfigurowane w tej sekcji zastępują te skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-148">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="7c9b0-149">Niektóre z tych ustawień mogą zostać zastąpione przez ustawienia, które są określone podczas dodawania programu obsługi do kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="7c9b0-149">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c9b0-150">Przykład</span><span class="sxs-lookup"><span data-stu-id="7c9b0-150">Example</span></span>  
  
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
