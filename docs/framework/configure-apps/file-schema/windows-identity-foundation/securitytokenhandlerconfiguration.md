---
title: '&lt;securityTokenHandlerConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 28724cc6-020c-4a06-9a1f-d7594f315019
author: BrucePerlerMS
ms.openlocfilehash: d66771ec7ed52ace52df6bb3bfafdcf9cce989b5
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/04/2018
ms.locfileid: "48793282"
---
# <a name="ltsecuritytokenhandlerconfigurationgt"></a>&lt;securityTokenHandlerConfiguration&gt;
Udostępnia konfigurację dla kolekcji programy obsługi tokenów.  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<securityTokenHandlerConfiguration >  
  
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
|saveBootstrapContext|Określa, czy bootstrap tokeny mają być uwzględniane w tokenu sesji. Wartość również mogą zostać ustawione dla kolekcji programu obsługi tokenów, ustawiając `saveBootstrapContext` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|  
|maximumClockSkew|Element <xref:System.TimeSpan> , który określa maksymalna dopuszczalna niedokładność zegara. Określa maksymalna dopuszczalna niedokładność zegara, podczas wykonywania operacji zależne od czasu, takich jak sprawdzanie poprawności czas wygaśnięcia sesji logowania. Wartość domyślna to 5 minut, "00: 05:00". Aby uzyskać więcej informacji o sposobie określania <xref:System.TimeSpan> wartości, zobacz [wartościach Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md). Niedokładność zegara maksymalna mogą również ustawiać na poziomie usługi, ustawiając `maximumClockSkew` atrybutu na [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu. Wartość w kolekcji programu obsługi tokenów zastępuje wartość ustawiona w usłudze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)|Określa zbiór identyfikatorów URI, które są dopuszczalne identyfikatory tej jednostki uzależnionej. Opcjonalna.|  
|[\<pamięci podręczne >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|Rejestruje pamięci podręcznych służy do tokenów sesji i wykrywania powtarzania tokenu. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|Określa ustawienia, które programy obsługi tokenów służący do weryfikowania certyfikatów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Te ustawienia zostaną zastąpione, jeśli określony program obsługi jest skonfigurowany przy użyciu własnego modułu sprawdzania poprawności. Opcjonalna.|  
|[\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|Konfiguruje rejestru nazwy wystawcy, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów. Opcjonalna.|  
|[\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)|Rejestruje wystawcy program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów. Program rozpoznawania tokenów wystawcy jest używany do rozpoznawania token podpisujący na przychodzące tokeny i komunikatów. Opcjonalna.|  
|[\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)|Rejestruje usługę program rozpoznawania tokenów, który jest używany przez programy obsługi w kolekcji programu obsługi tokenów. Program rozpoznawania tokenów usługi jest używany do rozpoznawania tokenu szyfrowania na przychodzące tokeny i komunikatów. Opcjonalna.|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|Włącza wykrywanie powtórzeń tokenów i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub kolekcji programu obsługi tokenów zabezpieczeń. Opcjonalna.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|Określa kolekcję programy obsługi tokenów zabezpieczających, które są zarejestrowane z punktem końcowym.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera wartości właściwości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> obiektu. Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze. Niektóre z tych ustawień z kolei można zastąpić za pomocą ustawień, które są określone, gdy program obsługi zostanie dodany do kolekcji programu obsługi tokenów zabezpieczeń.  
  
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
