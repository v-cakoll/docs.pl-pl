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
# <a name="securitytokenhandlerconfiguration"></a>\<> konfiguracji securityTokenHandler
Zapewnia konfigurację dla kolekcji programów obsługi tokenów.  
  
[**\<>konfiguracyjne**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>konfiguracji tożsamości**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>securityTokenHandlers**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>konfiguracji securityTokenHandler**  
  
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
|saveBootstrapContext|Określa, czy tokeny bootstrap powinny być uwzględniane w tokenie sesji. Wartość może być również ustawiona w kolekcji obsługi tokenu, `saveBootstrapContext` ustawiając atrybut na [ \<identityConfiguration>](identityconfiguration.md) element. Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|  
|maksimumClockSkew|A, <xref:System.TimeSpan> który określa maksymalne dozwolone pochylenie zegara. Steruje maksymalnym dozwolonym pochyleniem zegara podczas wykonywania operacji zależnych od czasu, takich jak sprawdzanie poprawności czasu wygaśnięcia sesji logowania. Wartość domyślna to 5 minut , "00:05:00". Aby uzyskać więcej informacji <xref:System.TimeSpan> na temat określania wartości, zobacz [Timespan Values](../windows-workflow-foundation/index.md). Maksymalne pochylenie zegara można również `maximumClockSkew` ustawić na poziomie usługi, ustawiając atrybut na [ \<identityConfiguration>](identityconfiguration.md) element. Wartość ustawiona w kolekcji obsługi tokenów zastępuje wartość ustawioną w usłudze.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<audienceUris>](audienceuris.md)|Określa zestaw identyfikatorów URI, które są dopuszczalnymi identyfikatorami tej jednostki uzależniającej. Element opcjonalny.|  
|[\<>pamięci podręcznej](caches.md)|Rejestruje pamięci podręczne używane do tokenów sesji i wykrywania powtórzeń tokenu. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Element opcjonalny.|  
|[\<>certyfikatuWeracja](certificatevalidation.md)|Steruje ustawieniami używanymi przez programy obsługi tokenów do sprawdzania poprawności certyfikatów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Te ustawienia są zastępowane, jeśli określony program obsługi jest skonfigurowany z własnym walidatorem. Element opcjonalny.|  
|[\<>](issuernameregistry.md)|Konfiguruje rejestr nazw wystawców, który jest używany przez programy obsługi w kolekcji obsługi tokenu. Element opcjonalny.|  
|[\<>>](issuertokenresolver.md)|Rejestruje program rozpoznawania nazw tokenów wystawcy, który jest używany przez programy obsługi w kolekcji obsługi tokenu. Program rozpoznawania nazw tokenów wystawcy służy do rozpoznawania tokenu podpisywania na przychodzących tokenach i wiadomościach. Element opcjonalny.|  
|[\<>serviceTokenResolver](servicetokenresolver.md)|Rejestruje program rozpoznawania tokenów usługi, który jest używany przez programy obsługi w kolekcji obsługi tokenu. Program rozpoznawania nazw tokenów usługi służy do rozpoznawania tokenu szyfrowania na przychodzących tokenach i wiadomościach. Element opcjonalny.|  
|[\<>tokenReplayDetection](tokenreplaydetection.md)|Włącza wykrywanie powtarzania tokenu i określa czas wygaśnięcia tokenów. Można określić na poziomie usługi lub w kolekcji obsługi tokenów zabezpieczających. Element opcjonalny.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<>securityTokenHandlers](securitytokenhandlers.md)|Określa kolekcję programów obsługi tokenów zabezpieczających, które są zarejestrowane w punkcie końcowym.|  
  
## <a name="remarks"></a>Uwagi  
 Ta sekcja zawiera wartości <xref:System.IdentityModel.Tokens.SecurityTokenHandlerConfiguration> właściwości dla obiektu. Ustawienia skonfigurowane w tej sekcji zastępują ustawienia skonfigurowane w usłudze. Niektóre z tych ustawień można z kolei zastąpić ustawieniami, które są określone, gdy program obsługi jest dodawany do kolekcji obsługi tokenów zabezpieczających.  
  
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
