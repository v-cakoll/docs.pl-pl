---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 10888f26053014ffb1fec49d1dfe87c7fd09ab54
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399577"
---
# \<serviceSecurityAudit>
Określa ustawienia, które włączają inspekcję zdarzeń zabezpieczeń podczas operacji usługi.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceSecurityAudit>**  
  
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
|auditLogLocation|Określa lokalizację dziennika inspekcji. Prawidłowe wartości to:<br /><br /> -Domyślnie: zdarzenia zabezpieczeń są zapisywane w dzienniku aplikacji w systemie Windows XP i w dzienniku zdarzeń w systemie Windows Server 2003 i Windows Vista.<br />-Aplikacja: zdarzenia inspekcji są zapisywane w dzienniku zdarzeń aplikacji.<br />-Zabezpieczenia: zdarzenia inspekcji są zapisywane w dzienniku zdarzeń zabezpieczeń.<br /><br /> Wartość domyślna to default. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Wartość logiczna określająca zachowanie w przypadku pomijania błędów zapisu do dziennika inspekcji.<br /><br /> Aplikacje powinny być powiadamiane o błędach zapisu do dziennika inspekcji. Jeśli aplikacja nie jest zaprojektowana do obsługi błędów inspekcji, należy użyć tego atrybutu, aby pominąć błędy podczas zapisywania w dzienniku inspekcji.<br /><br /> Jeśli ten atrybut jest `true` , wyjątki inne niż OutOfMemoryException, StackOverflowException, ThreadAbortException i ArgumentException, które wynikają z próby zapisu zdarzeń inspekcji, są obsługiwane przez system i nie są propagowane do aplikacji. Jeśli ten atrybut ma wartość `false` , wszystkie wyjątki, które wynikają z próby zapisu zdarzeń inspekcji, są przesyłane do aplikacji.<br /><br /> Wartość domyślna to `true`.|  
|serviceAuthorizationAuditLevel|Określa typy zdarzeń autoryzacji, które są rejestrowane w dzienniku inspekcji. Prawidłowe wartości to:<br /><br /> -Brak: Inspekcja zdarzeń autoryzacji usługi nie jest wykonywana.<br />-Sukces: Inspekcja zdarzeń autoryzacji usługi odbywa się tylko pomyślnie.<br />-Failure: Inspekcja zdarzeń autoryzacji usługi nie powiodła się.<br />-SuccessOrFailure: Przeprowadź inspekcję zdarzeń autoryzacji dotyczącej sukcesów i niepowodzeń usługi.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Określa typ zarejestrowanych zdarzeń inspekcji uwierzytelniania wiadomości. Prawidłowe wartości to:<br /><br /> -Brak: nie są generowane żadne zdarzenia inspekcji.<br />-Sukces: zarejestrowano tylko pomyślne zabezpieczenia (pełna Walidacja, w tym sprawdzanie poprawności podpisów komunikatów, szyfrowanie i sprawdzanie poprawności tokenów).<br />-Błąd: rejestrowane są tylko zdarzenia niepowodzeń.<br />-SuccessOrFailure: rejestrowane są zdarzenia sukces i niepowodzeń.<br /><br /> Wartość domyślna to Brak. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|Określa zachowanie elementu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten element konfiguracji jest używany do inspekcji zdarzeń uwierzytelniania Windows Communication Foundation (WCF). Gdy inspekcja jest włączona, może być przeprowadzana inspekcja nieudanych lub nieudanych prób uwierzytelnienia (lub obydwu). Zdarzenia są zapisywane w jednym z trzech dzienników zdarzeń: aplikacji, zabezpieczeń lub dziennika domyślnego dla wersji systemu operacyjnego. Wszystkie dzienniki zdarzeń można wyświetlić za pomocą podglądu zdarzeń systemu Windows.  
  
 Aby zapoznać się ze szczegółowym przykładem użycia tego elementu konfiguracji, zapoznaj się z tematem [zachowanie inspekcji usługi](../../../wcf/samples/service-auditing-behavior.md).  
  
 Domyślnie w systemie Windows XP zdarzenia inspekcji mogą być widoczne w dzienniku aplikacji. w systemie Windows Server 2003 i Windows Vista zdarzenia inspekcji mogą być widoczne w dzienniku zabezpieczeń. Lokalizację zdarzeń inspekcji można określić przez ustawienie `auditLogLocation` atrybutu na wartość "aplikacja" lub "zabezpieczenia". Aby uzyskać więcej informacji, zobacz [jak: Inspekcja zdarzeń zabezpieczeń](../../../wcf/feature-details/how-to-audit-wcf-security-events.md). Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń, LocalSecurityPolicy-> Włącz dostęp do obiektu powinien być ustawiony dla "powodzenie" i "Niepowodzenie".  
  
 Podczas przeglądania dziennika zdarzeń źródło zdarzeń inspekcji ma wartość "ServiceModel Audit 3.0.0.0". Rekordy inspekcji uwierzytelniania komunikatów mają kategorię "MessageAuthentication", podczas gdy rekordy inspekcji autoryzacji usług mają kategorię "ServiceAuthorization".  
  
 Zdarzenia inspekcji uwierzytelniania komunikatów dotyczą tego, czy wiadomość została naruszona, czy wiadomość wygasła i czy klient może uwierzytelniać się w usłudze. Dostarczają informacji na temat tego, czy uwierzytelnianie zakończyło się powodzeniem, czy niepowodzeniem wraz z tożsamością klienta i punktem końcowym, do którego wiadomość została wysłana, wraz z akcją skojarzoną z wiadomością.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzje dotyczące autoryzacji podejmowane przez Menedżera autoryzacji usług. Dostarczają informacji o tym, czy autoryzacja zakończyła się powodzeniem, czy też niepowodzeniem wraz z tożsamością klienta, punktem końcowym, do którego wiadomość została wysłana, akcją skojarzoną z komunikatem, identyfikatorem kontekstu autoryzacji wygenerowanym na podstawie komunikatu przychodzącego i typem Menedżera autoryzacji, który dokonał decyzji o dostępie.  
  
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
- [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Zachowanie inspekcji usługi](../../../wcf/samples/service-auditing-behavior.md)
