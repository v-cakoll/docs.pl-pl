---
title: <identityConfiguration>
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 0fa8c574fd5663606cf081f1000a24884306edfe
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251995"
---
# \<identityConfiguration>

Określa ustawienia tożsamości na poziomie usług.

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<identityConfiguration>**  

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
|name|Nazwa sekcji konfiguracji tożsamości. Tej nazwy można użyć, aby odwołać się do określonej sekcji konfiguracji. Jeśli żaden `name` atrybut nie jest określony, sekcja definiuje konfigurację domyślną. Domyślna konfiguracja jest zawsze używana w scenariuszach pasywnych Federacji. Aby uzyskać więcej informacji, zobacz [\<federationConfiguration>](federationconfiguration.md) element.|
|saveBootstrapContext|Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji. Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu dla [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu. Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|
|maximumClockSkew|A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara. Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00:05:00". Aby uzyskać więcej informacji na temat sposobu określania <xref:System.TimeSpan> wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md). Maksymalne przechylenie zegara może być również ustawione w kolekcji obsługi tokenów przez ustawienie `maximumClockSkew` atrybutu dla [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu. Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[\<caches>](caches.md)|Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|
|[\<certificateValidation>](certificatevalidation.md)|Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|
|[\<claimsAuthenticationManager>](claimsauthenticationmanager.md)|Rejestruje Menedżera uwierzytelniania oświadczeń dla oświadczeń przychodzących. Opcjonalny.|
|[\<claimsAuthorizationManager>](claimsauthorizationmanager.md)|Rejestruje Menedżera autoryzacji oświadczeń dla oświadczeń przychodzących. Opcjonalny.|
|[\<claimTypeRequired>](claimtyperequired.md)|Określa zestaw wymaganych oświadczeń dla przychodzących tokenów zabezpieczających. Opcjonalny.|
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenów zabezpieczających. Można określić zero lub więcej kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalny.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[\<system.identityModel>](system-identitymodel.md)|Zapewnia konfigurację umożliwiającą włączanie opcji Windows Identity Foundation (WIF) w aplikacjach.|

## <a name="remarks"></a>Uwagi

Można zdefiniować wiele konfiguracji tożsamości, z których każda ma unikatową nazwę. Zachowanie jest następujące:

1. Jeśli żaden `<identityConfiguration>` element nie jest określony. Domyślna konfiguracja tożsamości jest tworzona w czasie wykonywania i wypełniana wartościami domyślnymi.

2. Jeśli określono pojedynczy `<identityConfiguration>` element. Jest to domyślna konfiguracja tożsamości. Nie ma znaczenia, czy ma on nazwę lub nie ma nazwy.

3. Jeśli `<identityConfiguration>` określono wiele elementów. Nienazwany element Określa domyślną konfigurację tożsamości. Zaleca się, aby po określeniu wielu `<identityConfiguration>` elementów jeden z nich powinien być nienazwany.

> [!WARNING]
> W przypadku określenia wielu `<identityConfiguration>` elementów jeden z nich powinien być nienazwany. Nienazwany element będzie domyślną konfiguracją tożsamości.

 Niektóre ustawienia określone w `<identityConfiguration>` elemencie mogą zostać zastąpione przez ustawienia w kolekcji obsługi tokenów zabezpieczających lub przez ustawienia dla poszczególnych programów obsługi tokenów zabezpieczających.

> [!IMPORTANT]
> W przypadku użycia <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> lub <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> klasy w celu zapewnienia kontroli dostępu opartej na oświadczeniach w kodzie Konfiguracja tożsamości, do której odwołuje się `<federationConfiguration>` element, konfiguruje Menedżera autoryzacji oświadczeń i zasady, które są używane w celu podejmowania decyzji dotyczących autoryzacji. Dotyczy to nawet scenariuszy, które nie są pasywnymi scenariuszami sieci Web, na przykład aplikacji Windows Communication Foundation (WCF) lub aplikacji, które nie są oparte na sieci Web. Jeśli aplikacja nie jest pasywną aplikacją sieci Web, [\<claimsAuthorizationManager>](claimsauthorizationmanager.md) element (i jego elementy zasad podrzędnych, jeśli istnieją) przywoływanej konfiguracji tożsamości są jedynymi stosowanymi ustawieniami. Wszystkie inne ustawienia są ignorowane. Aby uzyskać więcej informacji, zobacz [\<federationConfiguration>](federationconfiguration.md) element.

`<identityConfiguration>`Element jest reprezentowany przez <xref:System.IdentityModel.Configuration.IdentityConfigurationElement> klasę. Sekcja konfiguracji tożsamości jest reprezentowana przez <xref:System.IdentityModel.Configuration.IdentityConfiguration> klasę.

> [!IMPORTANT]
> Określanie następujących elementów jako elementów podrzędnych `<identityConfiguration>` elementu jest przestarzałe, mimo że zachowanie jest nadal obsługiwane w celu zapewnienia zgodności z poprzednimi wersjami. Elementy te powinny być określone w [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elemencie.
>
> - [\<audienceUris>](audienceuris.md)
> - [\<issuerNameRegistry>](issuernameregistry.md)
> - [\<issuerTokenResolver>](issuertokenresolver.md)
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
