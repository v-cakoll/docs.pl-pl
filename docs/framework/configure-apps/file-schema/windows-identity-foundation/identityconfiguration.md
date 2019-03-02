---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 91d64ce0d6a5cdbf32fec4a476fb111afe9a7952
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57212498"
---
# <a name="identityconfiguration"></a>\<identityConfiguration>

Określa ustawienia tożsamości na poziomie usługi.

 \<system.identityModel>\
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
|nazwa|Nazwa sekcji konfiguracji tożsamości. Ta nazwa służy do sekcji określonej konfiguracji. Jeśli nie `name` atrybut jest określony, w sekcji zdefiniowano domyślnej konfiguracji. Domyślna konfiguracja zawsze jest używany w scenariuszach pasywnego federacyjnej. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.|
|saveBootstrapContext|Określa, czy bootstrap tokeny mają być uwzględniane w tokenu sesji. Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu na [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|
|maximumClockSkew|Element <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara. Określa maksymalna dopuszczalna niedokładność zegara, podczas wykonywania operacji zależne od czasu, takich jak sprawdzanie poprawności czas wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00: 05:00". Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Niedokładność zegara maksymalnej również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `maximumClockSkew` atrybutu na [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<caches>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|
|[\<certificateValidation>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|
|[\<claimsAuthenticationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących. Opcjonalna.|
|[\<claimsAuthorizationManager>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących. Opcjonalna.|
|[\<claimTypeRequired>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|Określa zestaw wymagane oświadczenia przychodzące tokeny zabezpieczeń. Opcjonalna.|
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Określa kolekcję programy obsługi tokenów zabezpieczających. Można określić zero lub więcej kolekcji programy obsługi tokenów zabezpieczających. Opcjonalna.|
|[\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<system.identityModel>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|Udostępnia konfigurację dla Włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.|

## <a name="remarks"></a>Uwagi

Wiele tożsamości konfiguracji może być zdefiniowana, każdy z unikatową nazwą. To zachowanie jest następujący:

1. Jeśli nie `<identityConfiguration>` określony element. Domyślna konfiguracja tożsamości jest tworzony w czasie wykonywania i wypełnione wartościami domyślnymi.

2. Jeśli jeden `<identityConfiguration>` określony element. Jest domyślna konfiguracja tożsamości. Nie ma znaczenia, czy jest on o nazwie lub bez nazwy.

3. Jeśli wiele `<identityConfiguration>` są określone elementy. Nienazwane element określa domyślną konfigurację tożsamości. Zalecane jest, jeśli określisz wiele `<identityConfiguration>` elementów, jeden z nich należy bez nazwy.

> [!WARNING]
> Jeśli określisz wiele `<identityConfiguration>` elementów, jeden z nich należy bez nazwy. Element bez nazwy będzie domyślna konfiguracja tożsamości.

 Niektóre ustawienia określone w `<identityConfiguration>` element może być zastąpiona przez ustawienia w kolekcji programu obsługi tokenów zabezpieczeń lub ustawienia dotyczące programu obsługi tokenów zabezpieczeń.

> [!IMPORTANT]
> Korzystając z <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach, w kodzie, konfiguracja tożsamości, która odwołuje się do niej `<federationConfiguration>` element konfiguruje Menedżera autoryzacji oświadczeń i zasady, które jest używane do utworzenia decyzji dotyczących autoryzacji. Ta zasada obowiązuje, nawet w scenariuszach, które nie są pasywnym scenariusze sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, która nie jest oparte na sieci Web. Jeśli aplikacja nie jest pasywnym aplikacji sieci Web, [ \<składnika claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) — element (i jego zasady elementów podrzędnych, a jeśli jest obecna) konfiguracji odwołania tożsamości są tylko ustawienia zastosowane. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) elementu.

`<identityConfiguration>` Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> klasy. Sekcja konfiguracji tożsamości jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityConfiguration> klasy.

> [!IMPORTANT]
> Określając następujące elementy jako elementy podrzędne `<identityConfiguration>` elementu jest przestarzałe, mimo że zachowanie jest nadal obsługiwana w przypadku zgodności z poprzednimi wersjami. Te elementy zamiast tego należy określić w ramach [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu.
>
> - [\<audienceUris>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)
> - [\<issuerNameRegistry>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)
> - [\<issuerTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)
> - [\<serviceTokenResolver>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)

## <a name="example"></a>Przykład

Poniższy przykład umożliwia utworzenie konfiguracji adresu tożsamości o nazwie "alternateConfiguration". Konfiguracja tożsamości Określa domyślne ustawienia.

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
