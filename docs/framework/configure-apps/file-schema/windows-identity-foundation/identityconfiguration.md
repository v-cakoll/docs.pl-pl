---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 9f5e0c5ded3d750a1102492c7a506e6d5643b2d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942749"
---
# <a name="identityconfiguration"></a>\<identityConfiguration>

Określa ustawienia tożsamości na poziomie usług.

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
|nazwa|Nazwa sekcji konfiguracji tożsamości. Tej nazwy można użyć, aby odwołać się do określonej sekcji konfiguracji. Jeśli żaden `name` atrybut nie jest określony, sekcja definiuje konfigurację domyślną. Domyślna konfiguracja jest zawsze używana w scenariuszach pasywnych Federacji. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](federationconfiguration.md) elementu.|
|saveBootstrapContext|Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji. Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu [ \<dla elementu securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) . Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|
|maximumClockSkew|A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara. Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00:05:00". Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md). Maksymalne przechylenie zegara może być również ustawione w kolekcji obsługi tokenów przez ustawienie `maximumClockSkew` atrybutu [ \<dla elementu securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) . Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<pamięć podręczna >](caches.md)|Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalna.|
|[\<certificateValidation >](certificatevalidation.md)|Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|
|[\<claimsAuthenticationManager >](claimsauthenticationmanager.md)|Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących. Opcjonalny.|
|[\<Składnika ClaimsAuthorizationManager >](claimsauthorizationmanager.md)|Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących. Opcjonalny.|
|[\<claimTypeRequired >](claimtyperequired.md)|Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających. Opcjonalny.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenów zabezpieczających. Można określić zero lub więcej kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalna.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.|

## <a name="remarks"></a>Uwagi

Można zdefiniować wiele konfiguracji tożsamości, z których każda ma unikatową nazwę. Zachowanie jest następujące:

1. Jeśli żaden `<identityConfiguration>` element nie jest określony. Domyślna konfiguracja tożsamości jest tworzona w czasie wykonywania i wypełniana wartościami domyślnymi.

2. Jeśli określono pojedynczy `<identityConfiguration>` element. Jest to domyślna konfiguracja tożsamości. Nie ma znaczenia, czy ma on nazwę lub nie ma nazwy.

3. Jeśli określono `<identityConfiguration>` wiele elementów. Nienazwany element Określa domyślną konfigurację tożsamości. Zaleca się, aby po określeniu wielu `<identityConfiguration>` elementów jeden z nich powinien być nienazwany.

> [!WARNING]
> W przypadku określenia wielu `<identityConfiguration>` elementów jeden z nich powinien być nienazwany. Nienazwany element będzie domyślną konfiguracją tożsamości.

 Niektóre ustawienia określone w `<identityConfiguration>` elemencie mogą zostać zastąpione przez ustawienia w kolekcji obsługi tokenów zabezpieczających lub przez ustawienia dla poszczególnych programów obsługi tokenów zabezpieczających.

> [!IMPORTANT]
> W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> lub klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości `<federationConfiguration>` , do której odwołuje się element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane do wykonania decyzje dotyczące autoryzacji. Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, [ \<element składnika ClaimsAuthorizationManager >](claimsauthorizationmanager.md) (i jego elementy podrzędne, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [ \<federationConfiguration >](federationconfiguration.md) elementu.

Element jest reprezentowany <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> przez klasę. `<identityConfiguration>` Sekcja konfiguracji tożsamości jest reprezentowana przez <xref:System.IdentityModel.Configuration.IdentityConfiguration> klasę.

> [!IMPORTANT]
> Określanie następujących elementów jako elementów `<identityConfiguration>` podrzędnych elementu jest przestarzałe, mimo że zachowanie jest nadal obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Te elementy należy zamiast tego określić w [ \<elemencie securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) .
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver >](issuertokenresolver.md)
> - [\<serviceTokenResolver>](servicetokenresolver.md)

## <a name="example"></a>Przykład

Poniższy przykład tworzy konfigurację tożsamości o nazwie "alternateConfiguration". Konfiguracja tożsamości określa ustawienia domyślne.

```xml
<system.identityModel>
    <identityConfiguration name="alternateConfiguration"/>
</system.identityModel>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.IdentityModel.Configuration.IdentityConfiguration>
- <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
