---
title: <securityTokenHandlerConfiguration>
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: e3e65820fa4dc341371d4f67689a288cd3f63951
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152570"
---
# <a name="securitytokenhandlerconfiguration"></a><span data-ttu-id="267d2-101">\<> konfiguracji securityTokenHandler</span><span class="sxs-lookup"><span data-stu-id="267d2-101">\<securityTokenHandlerConfiguration></span></span>
<span data-ttu-id="267d2-102">Zapewnia konfigurację dla kolekcji programów obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="267d2-102">Provides configuration for the collection of token handlers.</span></span>  
  
<span data-ttu-id="267d2-103">[**\<>konfiguracyjne**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="267d2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="267d2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="267d2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="267d2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="267d2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="267d2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="267d2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="267d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>konfiguracji securityTokenHandler**</span><span class="sxs-lookup"><span data-stu-id="267d2-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<securityTokenHandlerConfiguration>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267d2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="267d2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="267d2-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="267d2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="267d2-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="267d2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="267d2-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="267d2-111">Attributes</span></span>  
  
|<span data-ttu-id="267d2-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="267d2-112">Attribute</span></span>|<span data-ttu-id="267d2-113">Opis</span><span class="sxs-lookup"><span data-stu-id="267d2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="267d2-114">saveBootstrapContext</span><span class="sxs-lookup"><span data-stu-id="267d2-114">saveBootstrapContext</span></span>|<span data-ttu-id="267d2-115">Określa, czy tokeny bootstrap powinny być uwzględniane w tokenie sesji.</span><span class="sxs-lookup"><span data-stu-id="267d2-115">Specifies whether bootstrap tokens should be included in the session token.</span></span> <span data-ttu-id="267d2-116">Wartość może być również ustawiona w kolekcji obsługi tokenu, `saveBootstrapContext` ustawiając atrybut na [ \<identityConfiguration>](identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="267d2-116">The value may also be set on a token handler collection by setting the `saveBootstrapContext` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="267d2-117">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="267d2-117">A value set on the token handler collection overrides the value set on the service.</span></span>|  
|<span data-ttu-id="267d2-118">maksimumClockSkew</span><span class="sxs-lookup"><span data-stu-id="267d2-118">maximumClockSkew</span></span>|<span data-ttu-id="267d2-119">A, <xref:System.TimeSpan> który określa maksymalne dozwolone pochylenie zegara.</span><span class="sxs-lookup"><span data-stu-id="267d2-119">A <xref:System.TimeSpan> that specifies the maximum allowed clock skew.</span></span> <span data-ttu-id="267d2-120">Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak sprawdzanie poprawności czasu wygaśnięcia sesji logowania.</span><span class="sxs-lookup"><span data-stu-id="267d2-120">Controls the maximum allowed clock skew when performing time-sensitive operations, such as validating the expiration time of a sign-in session.</span></span> <span data-ttu-id="267d2-121">Wartość domyślna to 5 minut , "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="267d2-121">The default is 5 minutes, "00:05:00".</span></span> <span data-ttu-id="267d2-122">Aby uzyskać więcej informacji <xref:System.TimeSpan> na temat określania wartości, zobacz [Timespan Values](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="267d2-122">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span> <span data-ttu-id="267d2-123">Maksymalne pochylenie zegara można również `maximumClockSkew` ustawić na poziomie usługi, ustawiając atrybut na [ \<identityConfiguration>](identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="267d2-123">The maximum clock skew may also be set at the service level by setting the `maximumClockSkew` attribute on the [\<identityConfiguration>](identityconfiguration.md) element.</span></span> <span data-ttu-id="267d2-124">Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.</span><span class="sxs-lookup"><span data-stu-id="267d2-124">A value set on the token handler collection overrides the value set on the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="267d2-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="267d2-125">Child Elements</span></span>  
  
|<span data-ttu-id="267d2-126">Element</span><span class="sxs-lookup"><span data-stu-id="267d2-126">Element</span></span>|<span data-ttu-id="267d2-127">Opis</span><span class="sxs-lookup"><span data-stu-id="267d2-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="267d2-128">\<audienceUris></span><span class="sxs-lookup"><span data-stu-id="267d2-128">\<audienceUris></span></span>](audienceuris.md)|<span data-ttu-id="267d2-129">Określa zestaw identyfikatorów URI, które są dopuszczalnymi identyfikatorami tej jednostki uzależniającej.</span><span class="sxs-lookup"><span data-stu-id="267d2-129">Specifies the set of URIs that are acceptable identifiers of this relying party.</span></span> <span data-ttu-id="267d2-130">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-130">Optional.</span></span>|  
|[<span data-ttu-id="267d2-131">\<>pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="267d2-131">\<caches></span></span>](caches.md)|<span data-ttu-id="267d2-132">Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtórzeń tokenu.</span><span class="sxs-lookup"><span data-stu-id="267d2-132">Registers the caches used for session tokens and token replay detection.</span></span> <span data-ttu-id="267d2-133">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="267d2-133">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="267d2-134">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-134">Optional.</span></span>|  
|[<span data-ttu-id="267d2-135">\<>certyfikatuWeracja</span><span class="sxs-lookup"><span data-stu-id="267d2-135">\<certificateValidation></span></span>](certificatevalidation.md)|<span data-ttu-id="267d2-136">Steruje ustawieniami używanymi przez programy obsługi tokenów do sprawdzania poprawności certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="267d2-136">Controls the settings that token handlers use to validate certificates.</span></span> <span data-ttu-id="267d2-137">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="267d2-137">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="267d2-138">Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany z własnym walidatorem.</span><span class="sxs-lookup"><span data-stu-id="267d2-138">These settings are overridden if a specific handler is configured with its own validator.</span></span> <span data-ttu-id="267d2-139">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-139">Optional.</span></span>|  
|[<span data-ttu-id="267d2-140">\<></span><span class="sxs-lookup"><span data-stu-id="267d2-140">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="267d2-141">Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="267d2-141">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="267d2-142">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-142">Optional.</span></span>|  
|[<span data-ttu-id="267d2-143">\<>></span><span class="sxs-lookup"><span data-stu-id="267d2-143">\<issuerTokenResolver></span></span>](issuertokenresolver.md)|<span data-ttu-id="267d2-144">Rejestruje program rozpoznawania nazw tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="267d2-144">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="267d2-145">Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="267d2-145">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="267d2-146">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-146">Optional.</span></span>|  
|[<span data-ttu-id="267d2-147">\<>serviceTokenResolver</span><span class="sxs-lookup"><span data-stu-id="267d2-147">\<serviceTokenResolver></span></span>](servicetokenresolver.md)|<span data-ttu-id="267d2-148">Rejestruje program rozpoznawania tokenów usługi, który jest używany przez programy obsługi w kolekcji obsługi tokenu.</span><span class="sxs-lookup"><span data-stu-id="267d2-148">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="267d2-149">Program rozpoznawania nazw tokenów usługi służy do rozpoznawania tokenu szyfrowania na przychodzących tokenach i wiadomościach.</span><span class="sxs-lookup"><span data-stu-id="267d2-149">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="267d2-150">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-150">Optional.</span></span>|  
|[<span data-ttu-id="267d2-151">\<>tokenReplayDetection</span><span class="sxs-lookup"><span data-stu-id="267d2-151">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)|<span data-ttu-id="267d2-152">Włącza wykrywanie powtarzania tokenu i określa czas wygaśnięcia tokenów.</span><span class="sxs-lookup"><span data-stu-id="267d2-152">Enables token replay detection and specifies the expiration time for tokens.</span></span> <span data-ttu-id="267d2-153">Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="267d2-153">Can be specified at the service-level or on a security token handler collection.</span></span> <span data-ttu-id="267d2-154">Element opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="267d2-154">Optional.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="267d2-155">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="267d2-155">Parent Elements</span></span>  
  
|<span data-ttu-id="267d2-156">Element</span><span class="sxs-lookup"><span data-stu-id="267d2-156">Element</span></span>|<span data-ttu-id="267d2-157">Opis</span><span class="sxs-lookup"><span data-stu-id="267d2-157">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="267d2-158">\<>securityTokenHandlers</span><span class="sxs-lookup"><span data-stu-id="267d2-158">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="267d2-159">Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="267d2-159">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="267d2-160">Uwagi</span><span class="sxs-lookup"><span data-stu-id="267d2-160">Remarks</span></span>  
 <span data-ttu-id="267d2-161">Ta sekcja zawiera wartości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> właściwości dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="267d2-161">This section provides property values for a <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> object.</span></span> <span data-ttu-id="267d2-162">Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze.</span><span class="sxs-lookup"><span data-stu-id="267d2-162">Settings configured in this section override those configured on the service.</span></span> <span data-ttu-id="267d2-163">Niektóre z tych ustawień można z kolei zastąpić ustawieniami, które są określone, gdy program obsługi jest dodawany do kolekcji obsługi tokenów zabezpieczających.</span><span class="sxs-lookup"><span data-stu-id="267d2-163">Some of these settings can, in turn, be overridden by settings that are specified when a handler is added to the security token handler collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="267d2-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="267d2-164">Example</span></span>  
  
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
