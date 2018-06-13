---
title: '&lt;identityConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 5070d9e886b8f5a8a0abf27593d40df8b5281267
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759000"
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
Określa ustawienia tożsamości poziomu usług.  
  
 \<system.identityModel>  
\<identityConfiguration>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|nazwa|Nazwa sekcji konfiguracji tożsamości. Ta nazwa służy do sekcji określonej konfiguracji. Jeśli nie `name` atrybut został określony, sekcja definiuje konfigurację domyślną. Domyślna konfiguracja zawsze jest używany w scenariuszach passive federation. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.|  
|saveBootstrapContext|Określa, czy tokeny bootstrap powinny być objęte tokenu sesji. Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|  
|maximumClockSkew|A <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara. Steruje maksymalna dopuszczalna niedokładność zegara podczas wykonywania operacji harmonogramów, takich jak sprawdzanie poprawności czasu wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00: 05:00". Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartości Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Maksymalna niedokładność zegara również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `maximumClockSkew` atrybutu [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<buforuje >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Rejestruje pamięci podręczne tokeny sesji i wykrywania powtórzeń tokenów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Określa ustawienia, które programy obsługi token służący do weryfikowania certyfikatów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Rejestruje Menedżer uwierzytelniania oświadczeń oświadczeń przychodzących. Opcjonalna.|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących. Opcjonalna.|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Określa zestaw żądanych oświadczeń przychodzących tokenów zabezpieczających. Opcjonalna.|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenu zabezpieczeń. Można określić zero lub więcej kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Zapewnia konfigurację Włączanie opcji Windows Identity Foundation (WIF) w aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 Wiele tożsamości konfiguracji może być zdefiniowana, każde z nich unikatową nazwę. Zachowanie jest następujący:  
  
1.  Jeśli nie `<identityConfiguration>` określony element. Domyślna konfiguracja tożsamości jest tworzony w czasie wykonywania i wypełnić wartościami domyślnymi.  
  
2.  Jeśli jeden `<identityConfiguration>` określony element. Jest domyślna konfiguracja tożsamości. Nie ma znaczenia, czy jest o nazwie lub bez nazwy.  
  
3.  Jeśli wiele `<identityConfiguration>` są określone elementy. Element bez nazwy Określa domyślnej konfiguracji tożsamości. Jest zalecane w przypadku określenia wielu `<identityConfiguration>` elementów, jeden z nich należy bez nazwy.  
  
> [!WARNING]
>  Jeśli określisz wiele `<identityConfiguration>` elementów, jeden z nich należy bez nazwy. Element bez nazwy będzie domyślna konfiguracja tożsamości.  
  
 Niektóre ustawienia określone w `<identityConfiguration>` element może zostać zastąpiona przez ustawienia w kolekcji programu obsługi tokenów zabezpieczeń lub ustawienia dotyczące programu obsługi tokenów zabezpieczeń.  
  
> [!IMPORTANT]
>  Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie, konfiguracja tożsamości, który odwołuje się do niego `<federationConfiguration>` element konfiguruje Menedżera autoryzacji oświadczeń i zasad, które jest używane do obliczania decyzji dotyczących autoryzacji. Dotyczy to przypadków, nawet w przypadku scenariuszy, które nie są pasywnym scenariusze sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web. Jeśli aplikacja nie jest pasywny aplikacji sieci Web, [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) — element (i jego zasady elementów podrzędnych, a jeśli istnieje) konfiguracji przywoływanego tożsamości są tylko ustawienia zastosowane. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.  
  
 `<identityConfiguration>` Reprezentowany przez element <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> klasy. Sekcja konfiguracji tożsamości jest reprezentowana przez <xref:System.IdentityModel.Configuration.IdentityConfiguration> klasy.  
  
> [!IMPORTANT]
>  Określanie następujące elementy jako elementy podrzędne `<identityConfiguration>` elementu jest przestarzałe, mimo że zachowanie jest nadal obsługiwane dla zgodności z poprzednimi wersjami. Te elementy zamiast tego należy określić w obszarze [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu.  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy konfigurację tożsamości o nazwie "alternateConfiguration". Konfiguracja tożsamości Określa domyślne ustawienia.  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
