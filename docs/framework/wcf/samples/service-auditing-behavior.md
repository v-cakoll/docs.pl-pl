---
title: Zachowanie inspekcji usługi
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 6d5f254f4f94adfaeaf5632ddd696891af177e93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964544"
---
# <a name="service-auditing-behavior"></a>Zachowanie inspekcji usługi
W tym przykładzie przedstawiono sposób użycia programu <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> w celu włączenia inspekcji zdarzeń zabezpieczeń podczas operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa i klient zostały skonfigurowane przy użyciu [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `Message` `clientCredentialType`Atrybut> zabezpieczeń został ustawiony na wartość i został ustawiony na `Windows`. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `mode` W tym przykładzie klient jest aplikacją konsolową (. exe), a usługa jest hostowana przez Internet Information Services (IIS).  
  
> [!NOTE]
> Procedura instalacji i instrukcje dotyczące kompilacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa elementu, `serviceSecurityAudit` aby skonfigurować inspekcję.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Po uruchomieniu przykładu żądania operacji i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta programu.  
  
 Wyniki dzienników inspekcji można wyświetlić, uruchamiając Podgląd zdarzeń. Domyślnie w systemie Windows XP zdarzenia inspekcji mogą być widoczne w dzienniku aplikacji w systemie Windows Server 2003 i Windows Vista zdarzenia inspekcji mogą być widoczne w dzienniku zabezpieczeń. W systemach Windows Server 2008 i Windows 7 zdarzenia inspekcji mogą być widoczne w dziennikach aplikacji i usług. Lokalizację zdarzeń inspekcji można określić przez ustawienie `auditLogLocation` atrybutu na "aplikacja" lub "zabezpieczenia". Aby uzyskać więcej informacji, zobacz [jak: Inspekcja zdarzeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)zabezpieczeń. Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń, LocalSecurityPolicy-> Włącz dostęp do obiektu powinien być ustawiony dla "powodzenie" i "Niepowodzenie".  
  
 Podczas przeglądania dziennika zdarzeń źródło zdarzeń inspekcji ma wartość "ServiceModel Audit 3.0.0.0". Rekordy inspekcji uwierzytelniania komunikatów mają kategorię "MessageAuthentication", podczas gdy rekordy inspekcji autoryzacji usług mają kategorię "ServiceAuthorization".  
  
 Zdarzenia inspekcji uwierzytelniania komunikatów dotyczą tego, czy wiadomość została naruszona, czy wiadomość wygasła i czy klient może uwierzytelniać się w usłudze. Dostarczają informacji na temat tego, czy uwierzytelnianie zakończyło się powodzeniem, czy też nie powiodło się wraz z tożsamością klienta, a także punktem końcowym, do którego wysłano wiadomość, wraz z akcją skojarzoną z wiadomością.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzje dotyczące autoryzacji podejmowane przez Menedżera autoryzacji usług. Dostarczają informacji na temat tego, czy autoryzacja zakończyła się powodzeniem, czy niepowodzeniem wraz z tożsamością klienta, punkt końcowy, do którego wiadomość została wysłana, Akcja skojarzona z komunikatem, identyfikator kontekstu autoryzacji, który został wygenerowany z komunikat przychodzący i typ Menedżera autoryzacji, który dokonał decyzji o dostępie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, skompilować i uruchomić przykład  
  
1. Upewnij się, że została wykonana [Procedura konfiguracji jednorazowej dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Aby skompilować C# lub Visual Basic wersję .NET rozwiązania, postępuj zgodnie z instrukcjami w temacie [Tworzenie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Aby uruchomić przykład w konfiguracji na jednym lub wielu komputerach, postępuj zgodnie z instrukcjami w temacie [Uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także

- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Instrukcje: Inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
