---
title: Inspekcja zdarzeń dotyczących zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 70bd756c9de2cf6ffb43479b0b28a6d51340f905
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198085"
---
# <a name="auditing-security-events"></a>Inspekcja zdarzeń dotyczących zabezpieczeń
Aplikacje utworzone przy użyciu programu Windows Communication Foundation (WCF) umożliwia rejestrowanie zdarzeń związanych z zabezpieczeniami (Powodzenie, Niepowodzenie lub obie) za pomocą funkcji inspekcji. Zdarzenia są zapisywane w dzienniku zdarzeń systemu Windows i można zbadać za pomocą Podglądu zdarzeń.  
  
 Inspekcja umożliwia administratorom wykrywanie ataku, który już wystąpił, lub jest w toku. Ponadto inspekcja może pomóc dewelopera do debugowania problemów związanych z zabezpieczeniami. Na przykład jeśli wystąpił błąd podczas konfiguracji autoryzacji lub Sprawdzanie, czy zasady przypadkowo nie zezwala na dostęp do autoryzowanego klienta, deweloper może szybko odnajdywanie i izolowania przyczynę tego błędu, sprawdzając dziennik zdarzeń.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń programu WCF zobacz [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat programowania WCF, zobacz [programowanie WCF Basic](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Poziom inspekcji i zachowania  
 Istnieją dwa poziomy inspekcji zabezpieczeń:  
  
-   Poziom autoryzacji usługi, w którym obiekt wywołujący jest autoryzowany.  
  
-   Poziom komunikatu, w którym WCF sprawdza poprawność wiadomości, a obiekt wywołujący uwierzytelnia.  
  
 Możesz sprawdzić zarówno inspekcji poziomy powodzenie lub niepowodzenie, który jest znany jako *inspekcji zachowanie*.  
  
## <a name="audit-log-location"></a>Lokalizacja dziennika inspekcji  
 Po określeniu poziomu inspekcji i zachowanie użytkownika (lub administratora) można określić lokalizację dziennika inspekcji. Dostępne są następujące trzy opcje: domyślny, aplikacji i zabezpieczeń. Podczas określania domyślny dziennik rzeczywisty zależy od używasz od systemu i tego, czy system obsługuje zapisu w dzienniku zabezpieczeń. Aby uzyskać więcej informacji zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
 Aby zapisać w dzienniku zabezpieczeń wymaga `SeAuditPrivilege`. Domyślnie tylko konta System lokalny i Usługa sieciowa mają to uprawnienie. Aby zarządzać funkcji dziennika zabezpieczeń `read` i `delete` wymaga `SeSecurityPrivilege`. Domyślnie tylko administratorzy mają to uprawnienie.  
  
 Z kolei uwierzytelnionych użytkowników może odczytywać i zapisywać w dzienniku aplikacji. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zapisy inspekcji zdarzenia w dzienniku aplikacji domyślnie. Dziennik może również zawierać informacje osobiste, który jest widoczny dla wszystkich uwierzytelnionych użytkowników.  
  
## <a name="suppressing-audit-failures"></a>Pomijanie Inspekcja niepowodzeń  
 Inną opcją podczas inspekcji jest, czy pominąć jakiekolwiek niepowodzenie inspekcji. Domyślnie Niepowodzenie inspekcji nie ma wpływu na aplikację. Jeśli jest to wymagane, jednak można ustawić opcję `false`, która powoduje zgłoszenie wyjątku.  
  
## <a name="programming-auditing"></a>Inspekcja programowania  
 Zachowanie inspekcji można określić programowo lub za pośrednictwem konfiguracji.  
  
### <a name="auditing-classes"></a>Inspekcja klas  
 W poniższej tabeli opisano klasy i właściwości używanych do programów zachowania inspekcji.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Umożliwia ustawianie opcji inspekcji jako zachowanie usługi.|  
|<xref:System.ServiceModel.AuditLogLocation>|Wyliczenie, aby określić, zaloguj się do zapisu. Możliwe wartości to domyślne, aplikacji i zabezpieczeń. Po wybraniu domyślnego, system operacyjny Określa lokalizację dziennika rzeczywistych. Zobacz sekcję "Wybór dziennik zdarzeń aplikacji lub zabezpieczeń" w dalszej części tego tematu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Określa, jakie typy zdarzeń uwierzytelniania wiadomości są poddawane inspekcji na poziomie komunikatu. Dostępne są następujące mechanizmy `None`, `Failure`, `Success`, i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Określa, jakie typy zdarzeń autoryzacji usługi są poddawane inspekcji na poziomie usługi. Dostępne są następujące mechanizmy `None`, `Failure`, `Success`, i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Określa, co się dzieje z żądania klienta, w przypadku inspekcji kończy się niepowodzeniem. Na przykład, gdy usługa próbuje zapisać do dziennika zabezpieczeń, ale nie ma `SeAuditPrivilege`. Wartość domyślna `true` wskazuje, że błędy są ignorowane i żądania klienta są przetwarzane w zwykły sposób.|  
  
 Aby uzyskać przykład konfigurowania aplikacji do rejestrowania zdarzeń inspekcji, zobacz [instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfiguracja  
 Można również użyć konfiguracji określające zachowanie inspekcji, dodając [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) w obszarze [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Należy dodać element pod [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) jak pokazano w poniższym kodzie.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!— auditLogLocation="Application" or "Security" -—>  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Jeśli inspekcja jest włączona i `auditLogLocation` nie określony, domyślna nazwa dziennika to "Zabezpieczenia" Dziennik platformy obsługi zapisu w dzienniku zabezpieczeń; w przeciwnym razie jest dziennik "Aplikacji". Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)] systemy operacyjne obsługują zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli złośliwy użytkownik wie, że inspekcja jest włączona, że atakujący może wysłać nieprawidłowe komunikaty, które powodują wpisy inspekcji są zapisywane. Jeśli wprowadzono w dzienniku inspekcji w ten sposób, inspekcji systemu nie powiedzie się. Aby rozwiązać ten problem, należy ustawić <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwość `true` i używać właściwości podglądu zdarzeń w celu sterowania zachowaniem inspekcji. Aby uzyskać więcej informacji, zobacz artykuł Microsoft Support wyświetlanie i zarządzanie dziennikami zdarzeń za pomocą Podglądu zdarzeń w Windows XP dostępne pod adresem [sposobu wyświetlania i zarządzania dziennikami zdarzeń w Podglądzie zdarzeń w Windows XP](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Przeprowadź inspekcję zdarzeń, które są zapisywane w dzienniku aplikacji na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] są widoczne dla każdego uwierzytelnionego użytkownika.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Wybieranie między aplikacją i dzienniki zdarzeń zabezpieczeń  
 Poniższe tabele zawierają informacje ułatwiające wybranie, czy do zalogowania się do aplikacji lub w dzienniku zdarzeń zabezpieczeń.  
  
#### <a name="operating-system"></a>System operacyjny  
  
|System|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] lub nowszy|Obsługiwane|Nieobsługiwane|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)]|Obsługiwane|Kontekst wątku musi posiadać `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Inne czynniki  
 Oprócz systemu operacyjnego w poniższej tabeli opisano inne ustawienia regulujące włączenie rejestrowania.  
  
|współczynnik|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Zarządzanie zasadami inspekcji|Nie dotyczy.|Wraz z konfiguracji dziennika zabezpieczeń jest także kontrolowane przez zasady zabezpieczeń lokalnych (LSA) urzędu. Kategoria "Przeprowadź inspekcję dostępu do obiektów" musi być także włączona.|  
|Domyślne środowisko użytkownika|Wszystkim uwierzytelnionym użytkownikom można napisać w dzienniku aplikacji, dzięki czemu nie dodatkowe uprawnienia krok jest niezbędny do procesów aplikacji.|Proces aplikacji (kontekstu) musi mieć `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
