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
# <a name="securitytokenhandlerconfiguration"></a>\<securityTokenHandlerConfiguration>
Zapewnia konfigurację kolekcji programów obsługi tokenów.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> System. identityModel**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> obiektów securityTokenHandler**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<securityTokenHandlerConfiguration >**  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|saveBootstrapContext|Określa, czy tokeny bootstrap mają być zawarte w tokenie sesji. Wartość można także ustawić w kolekcji obsługi tokenów przez ustawienie `saveBootstrapContext` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) . Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|  
|maximumClockSkew|A <xref:System.TimeSpan> , który określa maksymalny dozwolony przesunięcia zegara. Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak Walidacja czasu wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00:05:00". Aby uzyskać więcej informacji na temat sposobu <xref:System.TimeSpan> określania wartości, zobacz [wartości TimeSpan](../windows-workflow-foundation/index.md). Maksymalne przechylenie zegara może być również ustawiane na poziomie usługi przez ustawienie `maximumClockSkew` atrybutu [ \<dla elementu IdentityConfiguration >](identityconfiguration.md) . Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Określa zestaw identyfikatorów URI, które są akceptowalnymi identyfikatorami tej jednostki uzależnionej. Opcjonalny.|  
|[\<pamięć podręczna >](caches.md)|Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtarzania tokenu. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalna.|  
|[\<certificateValidation >](certificatevalidation.md)|Kontroluje ustawienia używane przez programy obsługi do sprawdzania poprawności certyfikatów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności. Opcjonalna.|  
|[\<issuerNameRegistry>](issuernameregistry.md)|Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenów. Opcjonalna.|  
|[\<issuerTokenResolver >](issuertokenresolver.md)|Rejestruje program rozpoznawania tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenów. Program rozpoznawania tokenów wystawcy służy do rozpoznawania tokenu podpisywania w przypadku przychodzących tokenów i komunikatów. Opcjonalny.|  
|[\<serviceTokenResolver>](servicetokenresolver.md)|Rejestruje program rozpoznawania tokenów usługi używany przez programy obsługi w kolekcji obsługi tokenów. Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania przychodzących tokenów i komunikatów. Opcjonalna.|  
|[\<tokenReplayDetection>](tokenreplaydetection.md)|Włącza wykrywanie powtarzania tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Opcjonalna.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera wartości właściwości dla <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu. Ustawienia skonfigurowane w tej sekcji zastępują te skonfigurowane w usłudze. Niektóre z tych ustawień mogą zostać zastąpione przez ustawienia, które są określone podczas dodawania programu obsługi do kolekcji obsługi tokenów zabezpieczających.  
  
## <a name="example"></a>Przykład  
  
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
