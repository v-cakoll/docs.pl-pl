---
title: '&lt;serviceSecurityAudit&gt;'
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 293cd3118ace2e073933e4c124664c775902e7d8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751184"
---
# <a name="ltservicesecurityauditgt"></a>&lt;serviceSecurityAudit&gt;
Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczenia podczas operacji usługi.  
  
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
|AuditLogLocation|Określa lokalizację dziennika inspekcji. Prawidłowe wartości są następujące:<br /><br /> — Wartość domyślna: Zdarzenia zabezpieczeń są zapisywane w dzienniku aplikacji w systemie Windows XP, a w dzienniku zdarzeń systemu Windows Server 2003 i Windows Vista.<br />-Aplikacji: Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń aplikacji.<br />-Zabezpieczeń: Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń zabezpieczeń.<br /><br /> Wartością domyślną jest domyślna. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLogLocation>.|  
|SuppressAuditFailure|Wartość logiczna określająca zachowanie w sytuacji wystąpienia błędów zapisu do dziennika inspekcji.<br /><br /> Aplikacje powinny być powiadamiany o błędów zapisu do dziennika inspekcji. Jeśli aplikacja nie jest przeznaczony do obsługi błędów inspekcji, należy użyć tego atrybutu do pomijania błędów zapisu do dziennika inspekcji.<br /><br /> Jeśli ten atrybut jest `true`, wyjątki inne niż OutOfMemoryException, stackoverflowexception — ThreadAbortException i ArgumentException, które są wynikiem próby zapisania zdarzeń inspekcji są obsługiwane przez system i nie są propagowane do aplikacja. Jeśli ten atrybut jest `false`, wszystkie wyjątki, które są wynikiem próby zapisania zdarzeń inspekcji są przekazywane do aplikacji.<br /><br /> Wartość domyślna to `true`.|  
|serviceAuthorizationAuditLevel|Określa typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji. Prawidłowe wartości są następujące:<br /><br /> -Brak: Inspekcja nie zdarzeń autoryzacji usługi jest przeprowadzana.<br />-SUKCES: Tylko usługi pomyślnej autoryzacji zdarzenia są poddawane inspekcji.<br />-Nie powiodła się: Tylko awarii usługi autoryzacji zdarzenia są poddawane inspekcji.<br />-SuccessOrFailure: Zarówno są poddawane inspekcji zdarzeń autoryzacji usługi sukces i niepowodzenie.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Określa typ zarejestrowanych zdarzeń inspekcji uwierzytelniania wiadomości. Prawidłowe wartości są następujące:<br /><br /> -Brak: Brak zdarzeń inspekcji są generowane.<br />— Powodzenie: Rejestrowane są tylko zdarzenia (pełne sprawdzanie poprawności w tym Walidacja podpisu wiadomości, szyfrowania i weryfikacji tokenu) zabezpieczeń.<br />-Nie powiodła się: Tylko zdarzenia błędów są rejestrowane.<br />-SuccessOrFailure: Zarówno sukces i niepowodzenie zdarzenia są rejestrowane.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<zachowanie >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element Wyświetl służy do inspekcji zdarzeń uwierzytelniania systemu Windows Communication Foundation (WCF). Po włączeniu inspekcji można przeprowadzać inspekcję pomyślnym lub niepomyślnym uwierzytelniania prób (albo obu). Zdarzenia są zapisywane do jednej z trzech dzienniki zdarzeń: aplikacji, zabezpieczeń lub domyślnego dziennika dla wersji systemu operacyjnego. Dzienniki zdarzeń wszystkich można wyświetlić za pomocą Podglądu zdarzeń systemu Windows.  
  
 Aby uzyskać szczegółowy przykład za pomocą tego elementu konfiguracji, zobacz [zachowanie inspekcji usługi](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md).  
  
 Domyślnie w systemie Windows XP zdarzeń inspekcji można przejrzeć w dzienniku aplikacji; w systemie Windows Server 2003 i Windows Vista, można wyświetlić zdarzeń inspekcji w dzienniku zabezpieczeń. Można określić lokalizację zdarzeń inspekcji przez ustawienie `auditLogLocation` atrybutu "Aplikacja" lub "Zabezpieczenia". Aby uzyskać więcej informacji, zobacz [porady: zdarzenia inspekcji zabezpieczeń](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń, LocalSecurityPolicy -> Włącz dostęp do obiektów powinien być ustawiony na "Powodzenie" i "Niepowodzenie".  
  
 Podczas przeglądania dziennika zdarzeń, źródło zdarzeń inspekcji jest "ServiceModel inspekcji 3.0.0.0". Rekordów inspekcji uwierzytelniania wiadomości ma kategorii "MessageAuthentication", natomiast rekordów inspekcji usługi autoryzacji kategorii "ServiceAuthorization".  
  
 Zdarzeń inspekcji uwierzytelniania wiadomości obejmuje czy komunikat został zmodyfikowany, czy wiadomość utracił ważność i określa, czy klient może uwierzytelnienia w usłudze. Zawierają one informacje o czy uwierzytelnianie zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta i punktu końcowego wiadomość została wysłana do wraz z akcję skojarzoną z komunikatem.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzję dotyczącą autoryzacji przez Menedżera autoryzacji usługi. Zawierają informacje o czy autoryzacji zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, punkt końcowy wiadomość została wysłana do, akcję skojarzoną z komunikatem identyfikator kontekst autoryzacji, który został wygenerowany na podstawie Komunikat przychodzący i typ zgłaszającego decyzji dostępu Menedżera autoryzacji.  
  
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
 [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [Zachowanie inspekcji usługi](../../../../../docs/framework/wcf/samples/service-auditing-behavior.md)
