---
title: Zachowanie inspekcji usługi
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: e92f50005870b1c02571cebe0f532bd1810a40dc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574953"
---
# <a name="service-auditing-behavior"></a>Zachowanie inspekcji usługi
W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> Aby włączyć inspekcję zdarzeń zabezpieczenia podczas operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługi i klienta zostały skonfigurowane przy użyciu [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) został ustawiony na `Message` i `clientCredentialType` został ustawiony na `Windows`. W tym przykładzie klient to aplikacja konsoli (.exe), a usługa jest hostowana przez Internetowe usługi informacyjne (IIS).  
  
> [!NOTE]
>  Procedury i kompilacja instrukcje dotyczące instalacji w tym przykładzie znajdują się na końcu tego tematu.  
  
 Korzysta z pliku konfiguracji usługi `serviceSecurityAudit` element, aby skonfigurować inspekcję.  
  
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
  
 Po uruchomieniu przykładu, operacja żądań i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.  
  
 Wynikowy dzienników inspekcji można wyświetlić, uruchamiając w Podglądzie zdarzeń. Domyślnie w systemie Windows XP zdarzenia inspekcji są widoczne w dzienniku aplikacji podczas w systemie Windows Server 2003 i Windows Vista zdarzenia inspekcji są widoczne w dzienniku zabezpieczeń. W systemie Windows Server 2008 i Windows 7 zdarzenia inspekcji są widoczne w dziennikach aplikacji i usług. Lokalizacja zdarzenia inspekcji można określić, ustawiając `auditLogLocation` atrybutu "Aplikacja" lub "Zabezpieczenia". Aby uzyskać więcej informacji, zobacz [jak: Inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń -> LocalSecurityPolicy Włączanie dostępu do obiektów powinna być ustawiona na "Powodzenie" i "Błąd".  
  
 Podczas wyszukiwania w dzienniku zdarzeń, źródła zdarzeń inspekcji jest "ServiceModel inspekcji 3.0.0.0". Rekordy inspekcji uwierzytelniania wiadomości mają kategorię "MessageAuthentication", a rekordy inspekcji autoryzacji usługi kategorią "ServiceAuthorization".  
  
 Zdarzeń inspekcji uwierzytelniania wiadomości obejmują, czy wiadomość została naruszona, czy komunikat utracił ważność i tego, czy klient może uwierzytelniać w usłudze. Zapewniają one informacji na temat tego, czy uwierzytelnianie zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, a punkt końcowy wiadomość została wysłana do wraz z akcji skojarzonych z wiadomością.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzja przez Menedżera usług autoryzacji. Zapewniają one informacji na temat tego, czy Autoryzacja powiodła się lub nie powiodło się, wraz z tożsamością klienta, punktu końcowego wiadomość została wysłana do akcji skojarzonych z wiadomością identyfikator kontekst autoryzacji, który został wygenerowany z przychodząca wiadomość, a typ Menedżera autoryzacji, który podjęła decyzję dostępu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, tworzenie i uruchamianie aplikacji przykładowej  
  
1.  Upewnij się, że wykonano [procedura konfiguracji jednorazowe dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Aby kompilować rozwiązania w wersji języka C# lub Visual Basic .NET, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Do uruchomienia przykładu w konfiguracji o jednym lub między komputerami, postępuj zgodnie z instrukcjami [uruchamianie przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz także
- [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Instrukcje: Inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
