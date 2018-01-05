---
title: "Zachowanie inspekcji usługi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 140793e41be012a777dbfa4bf66528612ab33da7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="service-auditing-behavior"></a>Zachowanie inspekcji usługi
W tym przykładzie przedstawiono sposób użycia <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> Aby włączyć inspekcję zdarzeń zabezpieczenia podczas operacji usługi. Ten przykład jest oparty na [wprowadzenie](../../../../docs/framework/wcf/samples/getting-started-sample.md). Usługa i klient zostały skonfigurowane przy użyciu [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atrybutu [ \<zabezpieczeń >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) została ustawiona jako `Message` i `clientCredentialType` została ustawiona jako `Windows`. W tym przykładzie klient jest aplikacji konsoli (.exe), a usługa jest obsługiwana przez Internet Information Services (IIS).  
  
> [!NOTE]
>  Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.  
  
 Plik konfiguracji usługi używa `serviceSecurityAudit` element, aby skonfigurować inspekcję.  
  
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
  
 Po uruchomieniu próbki operację żądania i odpowiedzi są wyświetlane w oknie konsoli klienta. Naciśnij klawisz ENTER w oknie konsoli, aby zamknąć klienta.  
  
 Wynikowe dzienniki inspekcji będą widoczne przez uruchomienie podglądu zdarzeń. Domyślnie w systemie Windows XP zdarzeń inspekcji można przejrzeć w dzienniku aplikacji podczas w systemie Windows Server 2003 i Windows Vista można wyświetlić zdarzeń inspekcji w dzienniku zabezpieczeń. W systemie Windows Server 2008 i Windows 7 zdarzenia inspekcji są widoczne w dziennikach aplikacji i usług. Można określić lokalizację zdarzeń inspekcji przez ustawienie `auditLogLocation` atrybutu "Aplikacja" lub "Zabezpieczenia". Aby uzyskać więcej informacji, zobacz [porady: zdarzenia inspekcji zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Jeśli zdarzenia są zapisywane w dzienniku zabezpieczeń LocalSecurityPolicy -> Włącz dostęp do obiektów należy ustawić dla "Powodzenie" i "Niepowodzenie".  
  
 Podczas przeglądania dziennika zdarzeń, źródło zdarzeń inspekcji jest "ServiceModel inspekcji 3.0.0.0". Rekordów inspekcji uwierzytelniania wiadomości ma kategorii "MessageAuthentication", natomiast rekordów inspekcji usługi autoryzacji kategorii "ServiceAuthorization".  
  
 Zdarzeń inspekcji uwierzytelniania wiadomości obejmuje czy komunikat został zmodyfikowany, czy komunikat wygasł i określa, czy klient może uwierzytelnienia w usłudze. Zawierają informacje o czy uwierzytelnianie zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, a punkt końcowy wiadomość została wysłana do wraz z akcję skojarzoną z komunikatem.  
  
 Zdarzenia inspekcji autoryzacji usługi obejmują decyzję dotyczącą autoryzacji przez Menedżera autoryzacji usługi. Zawierają informacje o czy autoryzacji zakończyło się pomyślnie lub nie powiodło się wraz z tożsamością klienta, punkt końcowy wiadomość została wysłana do, akcję skojarzoną z komunikatem identyfikator kontekst autoryzacji, który został wygenerowany na podstawie Komunikat przychodzący, a typ Menedżera autoryzacji, zgłaszający decyzji dostępu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Tworzenie wersji języka C# lub Visual Basic .NET rozwiązania, postępuj zgodnie z instrukcjami [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Aby uruchomić przykładowy w konfiguracji pojedynczej lub między komputerami, postępuj zgodnie z instrukcjami w [uruchamiania przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
