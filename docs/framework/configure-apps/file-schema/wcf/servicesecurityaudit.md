---
title: '&lt;serviceSecurityAudit&gt;'
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 36215709f0ede32c25739ea47f2f285e4122f098
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144441"
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczeń podczas operacji usługi.  
  
 \<system.ServiceModel>  
\<zachowania >  
\<serviceBehaviors>  
\<zachowanie >  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceSecurityAudit   
   auditLogLocation="Default/Application/Security"  
   messageAuthenticationAuditLevel= None/Success/Failure/SuccessOrFailure"   serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"  
   suppressAuditFailure="Boolean"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|auditLogLocation|Określa lokalizację dziennika inspekcji. Prawidłowe wartości są następujące:<br /><br /> — Wartość domyślna: Zdarzenia zabezpieczeń są zapisywane w dzienniku aplikacji na Windows XP, a w dzienniku zdarzeń w systemie Windows Server 2003 i Windows Vista.<br />— Aplikacja: Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń aplikacji.<br />-Zabezpieczeń: Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń zabezpieczeń.<br /><br /> Wartością domyślną jest domyślna. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Wartość logiczna określająca zachowanie w sytuacji pominięcia błędów zapisu do dziennika inspekcji.<br /><br /> Aplikacje powinny być powiadamiany o błędów zapisu do dziennika inspekcji. Jeśli aplikacja nie jest przeznaczony do obsługi błędów inspekcji, należy użyć tego atrybutu, aby pominąć błędy podczas zapisywania do dziennika inspekcji.<br /><br /> Jeśli ten atrybut jest `true`, wyjątki inne niż OutOfMemoryException, stackoverflowexception —, ThreadAbortException i ArgumentException, które są wynikiem próby zapisania zdarzeń inspekcji są obsługiwane przez system i nie są propagowane do aplikacja. Jeśli ten atrybut jest `false`, wszystkie wyjątki, które są wynikiem próby zapisu zdarzenia inspekcji są przekazywane do aplikacji.<br /><br /> Wartość domyślna to `true`.|  
|serviceAuthorizationAuditLevel|Określa typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak inspekcji zdarzeń autoryzacji usługi jest wykonywane.<br />-Sukcesu: Tylko pomyślne usługi autoryzacji zdarzenia są poddawane inspekcji.<br />-Nie powiodła się: Tylko usługi autoryzacji zdarzenia błędów są poddawane inspekcji.<br />-SuccessOrFailure: Sukcesów i niepowodzeń zdarzenia autoryzacji usługi są poddawane inspekcji.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Określa typ zarejestrowanych zdarzeń inspekcji uwierzytelniania wiadomości. Prawidłowe wartości są następujące:<br /><br /> -Brak: Zdarzenia inspekcji nie są generowane.<br />-Sukcesu: Rejestrowane są tylko zdarzenia (m.in. Weryfikacja podpisu wiadomości, szyfrowania i walidacji tokenów pełnej weryfikacji) zabezpieczeń.<br />-Nie powiodła się: Rejestrowane są tylko zdarzenia błędu.<br />-SuccessOrFailure: Sukcesów i niepowodzeń zdarzenia są rejestrowane.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji służy do inspekcji zdarzeń uwierzytelniania Windows Communication Foundation (WCF). Po włączeniu inspekcji można przeprowadzać inspekcję uwierzytelniania powodzeniem lub niepowodzeniem prób (lub obu). Zdarzenia są zapisywane do jednej z trzech dzienników zdarzeń: aplikacji, zabezpieczeń lub domyślny dziennik dla wersji systemu operacyjnego. Dzienniki zdarzeń wszystkich można wyświetlić za pomocą Podglądu zdarzeń Windows.  
  
 Aby uzyskać szczegółowy przykład przy użyciu tego elementu konfiguracji, zobacz [zachowanie inspekcji usługi](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Domyślnie Windows XP zdarzenia inspekcji są widoczne w dzienniku aplikacji; w systemie Windows Server 2003 i Windows Vista, zdarzenia inspekcji są widoczne w dzienniku zabezpieczeń. Lokalizacja zdarzenia inspekcji można określić, ustawiając `auditLogLocation` atrybutu "Aplikacja" lub "Zabezpieczenia". Aby uzyskać więcej informacji, zobacz [jak: Inspekcja zdarzeń zabezpieczeń](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń, LocalSecurityPolicy -> Włącz dostęp do obiektów powinna być ustawiona na "Powodzenie" i "Niepowodzenie".  
  
 Podczas wyszukiwania w dzienniku zdarzeń, źródła zdarzeń inspekcji jest "ServiceModel inspekcji 3.0.0.0". Rekordy inspekcji uwierzytelniania wiadomości mają kategorię "MessageAuthentication", a rekordy inspekcji autoryzacji usługi kategorią "ServiceAuthorization".  
  
 Zdarzeń inspekcji uwierzytelniania wiadomości obejmują, czy wiadomość została naruszona, czy komunikat utracił ważność i tego, czy klient może uwierzytelniać w usłudze. Zapewniają one informacji na temat tego, czy uwierzytelnianie zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta i punktu końcowego wiadomość została wysłana do wraz z akcji skojarzonych z wiadomością.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzja przez Menedżera usług autoryzacji. Zapewniają one informacji na temat tego, czy Autoryzacja powiodła się lub nie powiodło się, wraz z tożsamością klienta, punktu końcowego wiadomość została wysłana do akcji skojarzonych z wiadomością identyfikator kontekst autoryzacji, który został wygenerowany z przychodząca wiadomość i typ Menedżera autoryzacji, który podjęła decyzję dostępu.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.serviceModel>  
   <serviceBehaviors>  
      <behavior name="NewBehavior">  
         <serviceSecurityAudit auditLogLocation="Application"   
             suppressAuditFailure="true"  
             serviceAuthorizationAuditLevel="Success"   
             messageAuthenticationAuditLevel="Success" />  
      </behavior>  
   </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 [Zachowania zabezpieczeń](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Inspekcja](../../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Jak: Inspekcja zdarzeń zabezpieczeń](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Zachowanie inspekcji usługi](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
