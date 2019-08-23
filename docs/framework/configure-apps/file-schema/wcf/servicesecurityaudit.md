---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: a1fcc59550904a34eced8e87fa9bc54a334acd03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937174"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczeń podczas operacji usługi.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<serviceSecurityAudit>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|auditLogLocation|Określa lokalizację dziennika inspekcji. Prawidłowe wartości to:<br /><br /> Wartooć Zdarzenia zabezpieczeń są zapisywane w dzienniku aplikacji w systemie Windows XP i w dzienniku zdarzeń w systemach Windows Server 2003 i Windows Vista.<br />Aplikacja Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń aplikacji.<br />Bezpieczeństw Zdarzenia inspekcji są zapisywane w dzienniku zdarzeń zabezpieczeń.<br /><br /> Wartość domyślna to default. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Wartość logiczna określająca zachowanie w przypadku pomijania błędów zapisu do dziennika inspekcji.<br /><br /> Aplikacje powinny być powiadamiane o błędach zapisu do dziennika inspekcji. Jeśli aplikacja nie jest zaprojektowana do obsługi błędów inspekcji, należy użyć tego atrybutu, aby pominąć błędy podczas zapisywania w dzienniku inspekcji.<br /><br /> Jeśli ten atrybut jest `true`, wyjątki inne niż OutOfMemoryException, StackOverflowException, ThreadAbortException i ArgumentException, które wynikają z próby zapisu zdarzeń inspekcji, są obsługiwane przez system i nie są propagowane do Aplikacja. Jeśli ten atrybut ma `false`wartość, wszystkie wyjątki, które wynikają z próby zapisu zdarzeń inspekcji, są przesyłane do aplikacji.<br /><br /> Wartość domyślna to `true`.|  
|serviceAuthorizationAuditLevel|Określa typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji. Prawidłowe wartości to:<br /><br /> Dawaj Inspekcja zdarzeń autoryzacji usługi nie jest przeprowadzana.<br />Prawnego Inspekcja jest przeprowadzana tylko przez pomyślne zdarzenia autoryzacji usługi.<br />Spraw Inspekcja zdarzeń autoryzacji usługi nie jest przeprowadzana.<br />- SuccessOrFailure: Inspekcja zdarzeń autoryzacji sukcesów i niepowodzeń podlega inspekcji.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Określa typ zarejestrowanych zdarzeń inspekcji uwierzytelniania wiadomości. Prawidłowe wartości to:<br /><br /> Dawaj Nie są generowane żadne zdarzenia inspekcji.<br />Prawnego Rejestrowane są tylko udane zabezpieczenia (pełna Walidacja, w tym weryfikacja podpisu komunikatu, szyfrowanie i sprawdzanie poprawności tokenu).<br />Spraw Rejestrowane są tylko zdarzenia niepowodzeń.<br />- SuccessOrFailure: Rejestrowane są zdarzenia sukces i niepowodzenie.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<> zachowania](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używany do inspekcji zdarzeń uwierzytelniania Windows Communication Foundation (WCF). Gdy inspekcja jest włączona, może być przeprowadzana inspekcja nieudanych lub nieudanych prób uwierzytelnienia (lub obydwu). Zdarzenia są zapisywane w jednym z trzech dzienników zdarzeń: aplikacji, zabezpieczeń lub dziennika domyślnego dla wersji systemu operacyjnego. Wszystkie dzienniki zdarzeń można wyświetlić za pomocą podglądu zdarzeń systemu Windows.  
  
 Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zapoznaj się z tematem [zachowanie inspekcji usługi](../../../wcf/samples/service-auditing-behavior.md).  
  
 Domyślnie w systemie Windows XP zdarzenia inspekcji mogą być widoczne w dzienniku aplikacji. w systemie Windows Server 2003 i Windows Vista zdarzenia inspekcji mogą być widoczne w dzienniku zabezpieczeń. Lokalizację zdarzeń inspekcji można określić przez ustawienie `auditLogLocation` atrybutu na wartość "aplikacja" lub "zabezpieczenia". Aby uzyskać więcej informacji, zobacz [jak: Inspekcja zdarzeń](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)zabezpieczeń. Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń, LocalSecurityPolicy-> Włącz dostęp do obiektu powinien być ustawiony dla "powodzenie" i "Niepowodzenie".  
  
 Podczas przeglądania dziennika zdarzeń źródło zdarzeń inspekcji ma wartość "ServiceModel Audit 3.0.0.0". Rekordy inspekcji uwierzytelniania komunikatów mają kategorię "MessageAuthentication", podczas gdy rekordy inspekcji autoryzacji usług mają kategorię "ServiceAuthorization".  
  
 Zdarzenia inspekcji uwierzytelniania komunikatów dotyczą tego, czy wiadomość została naruszona, czy wiadomość wygasła i czy klient może uwierzytelniać się w usłudze. Dostarczają informacji na temat tego, czy uwierzytelnianie zakończyło się powodzeniem, czy niepowodzeniem wraz z tożsamością klienta i punktem końcowym, do którego wiadomość została wysłana, wraz z akcją skojarzoną z wiadomością.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzje dotyczące autoryzacji podejmowane przez Menedżera autoryzacji usług. Dostarczają informacji na temat tego, czy autoryzacja zakończyła się powodzeniem, czy niepowodzeniem wraz z tożsamością klienta, punkt końcowy, do którego wiadomość została wysłana, Akcja skojarzona z komunikatem, identyfikator kontekstu autoryzacji, który został wygenerowany z komunikat przychodzący i typ Menedżera autoryzacji, który dokonał decyzji o dostępie.  
  
## <a name="example"></a>Przykład  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [Zachowania zabezpieczeń](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Inspekcja](../../../wcf/feature-details/auditing-security-events.md)
- [Instrukcje: Inspekcja zdarzeń zabezpieczeń](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Zachowanie inspekcji usługi](../../../wcf/samples/service-auditing-behavior.md)
