---
title: Inspekcja zdarzeń dotyczących zabezpieczeń
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
caps.latest.revision: 27
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 948ff11cf1b7ecacc6f9f5fdebfc3a0cbd1ef5b1
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="auditing-security-events"></a>Inspekcja zdarzeń dotyczących zabezpieczeń
Aplikacje utworzone przy użyciu [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] może rejestrować zdarzeń zabezpieczeń (sukces, Niepowodzenie lub obie) z funkcji inspekcji. Zdarzenia są zapisywane w dzienniku zdarzeń systemu Windows i można zbadać za pomocą Podglądu zdarzeń.  
  
 Inspekcja umożliwia administratorowi wykrycia ataku, który już wystąpił, lub jest w toku. Ponadto inspekcja może ułatwić deweloperom debugowanie problemów związanych z zabezpieczeniami. Na przykład jeśli wystąpił błąd w konfiguracji autoryzacji lub Sprawdzanie, czy zasady przypadkowo nie zezwala na dostęp do autoryzowanych użytkowników, dewelopera można szybko odnajdywanie i izolowanie przyczynę tego błędu, sprawdzając dziennik zdarzeń.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczenia, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Programowanie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zobacz [podstawowe programowania WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Poziom inspekcji i zachowania  
 Istnieją dwa poziomy inspekcji zabezpieczeń:  
  
-   Poziom autoryzacji usługi, w którym obiekt wywołujący jest autoryzowany.  
  
-   Komunikat poziomu, w którym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sprawdza poprawność wiadomości i uwierzytelnia wywołującego.  
  
 Można sprawdzić zarówno inspekcji poziomy powodzenie lub niepowodzenie, znany jako *inspekcji zachowanie*.  
  
## <a name="audit-log-location"></a>Lokalizacja dziennika inspekcji  
 Po określeniu poziomu inspekcji i zachowanie, użytkownik (lub administrator) można określić lokalizację dziennika inspekcji. Dostępne są następujące trzy opcje: domyślny, aplikacji i zabezpieczeń. Po określeniu domyślnego dziennika rzeczywisty zależy od używasz który system i czy system obsługuje zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
 Do zapisania w dzienniku zabezpieczeń wymaga `SeAuditPrivilege`. Domyślnie tylko konta System lokalny jak i usługi sieciowej to uprawnienie. Zarządzanie funkcji dziennika zabezpieczeń `read` i `delete` wymaga `SeSecurityPrivilege`. Domyślnie to uprawnienie mają tylko Administratorzy.  
  
 Z kolei uwierzytelnionym użytkownikom można odczytu i zapisu do dziennika aplikacji. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zapisy inspekcji zdarzeń w dzienniku aplikacji domyślnie. Dziennik może również zawierać informacje osobiste, który jest widoczny dla wszystkich użytkowników uwierzytelnionych.  
  
## <a name="suppressing-audit-failures"></a>Pomijanie błędów inspekcji  
 Inną opcją podczas inspekcji jest Określa, czy pomijać jakiekolwiek niepowodzenie inspekcji. Domyślnie błąd inspekcji nie wpływa na aplikację. Jeśli jest to wymagane, jednak można ustawić opcji `false`, co powoduje, że wyjątek zostanie wygenerowany.  
  
## <a name="programming-auditing"></a>Inspekcja programowania  
 Programowo lub przy użyciu konfiguracji można określić zachowanie inspekcji.  
  
### <a name="auditing-classes"></a>Inspekcja klas  
 W poniższej tabeli opisano klasy i właściwości używanych do programów zachowanie inspekcji.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Umożliwia ustawianie opcji inspekcji jako zachowanie usługi.|  
|<xref:System.ServiceModel.AuditLogLocation>|Wyliczenie, aby określić, zaloguj się do zapisu. Możliwe wartości to domyślny, aplikacji i zabezpieczeń. Po wybraniu domyślnego systemu operacyjnego Określa lokalizację dziennika rzeczywistych. Zobacz sekcję "Wybór dziennik zdarzeń aplikacji i zabezpieczeń" w dalszej części tego tematu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Określa, jakie typy zdarzeń uwierzytelniania wiadomości są poddawane inspekcji na poziomie wiadomości. Dostępne są następujące `None`, `Failure`, `Success`, i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Określa, jakie typy zdarzeń autoryzacji usługi są poddawane inspekcji na poziomie usługi. Dostępne są następujące `None`, `Failure`, `Success`, i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Określa, co się dzieje z żądania klienta w przypadku inspekcji kończy się niepowodzeniem. Na przykład, gdy usługa próbuje zapisać do dziennika zabezpieczeń, ale nie ma `SeAuditPrivilege`. Domyślna wartość `true` wskazuje, że błędy są ignorowane i żądania klienta są przetwarzane w zwykły sposób.|  
  
 Aby uzyskać przykład konfigurowania aplikacji do rejestrowania zdarzeń inspekcji, zobacz [porady: zdarzenia inspekcji zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfiguracja  
 Umożliwia także konfiguracji można określić zachowanie inspekcji, dodając [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) w obszarze [ \<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Należy dodać element w obszarze [ \<zachowanie >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) jak pokazano w poniższym kodzie.  
  
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
  
 Po włączeniu inspekcji i `auditLogLocation` jest nie jest określony, domyślną nazwę dziennika w dzienniku platformy obsługi zapisu do dziennika zabezpieczeń "Zabezpieczenia"; w przeciwnym razie jest dziennik "Aplikacji". Tylko [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] i [!INCLUDE[wv](../../../../includes/wv-md.md)] systemy operacyjne obsługują zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli złośliwy użytkownik wie, że inspekcja jest włączona, niepowołana może wysyłać nieprawidłowe komunikaty, powodujących wpisy inspekcji do zapisania. Dziennik inspekcji jest wypełniony w ten sposób, inspekcji systemu nie powiedzie się. Aby temu zaradzić, ustaw <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> właściwości `true` i użyj właściwości podglądu zdarzeń w celu kontrolowania zachowania inspekcji. Aby uzyskać więcej informacji, zobacz artykuł Microsoft Support na wyświetlanie i zarządzanie dziennikami zdarzeń za pomocą Podglądu zdarzeń w systemie Windows XP dostępne pod adresem [sposobu wyświetlania i zarządzania dziennikami zdarzeń w Podglądzie zdarzeń w systemie Windows XP](http://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Inspekcja zdarzeń, które są zapisywane w dzienniku aplikacji na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] są widoczne dla żadnych uwierzytelnionego użytkownika.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Wybór między aplikacji i dziennikami zdarzeń zabezpieczeń  
 Poniższe tabele zawierają informacje ułatwiające można zdecydować, czy do zalogowania się do aplikacji lub w dzienniku zdarzeń zabezpieczeń.  
  
#### <a name="operating-system"></a>System operacyjny  
  
|System|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] lub nowszy|Obsługiwane|Nieobsługiwane|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] I [!INCLUDE[wv](../../../../includes/wv-md.md)]|Obsługiwane|Kontekst wątku musi posiadać `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Inne czynniki  
 Oprócz systemu operacyjnego w poniższej tabeli opisano inne ustawienia regulujące włączenie rejestrowania.  
  
|Współczynnik|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Zarządzanie zasadami inspekcji|Nie dotyczy.|Wraz z konfiguracji dziennika zabezpieczeń jest także kontrolowane przez zasady zabezpieczeń lokalnych (LSA) urzędu. Kategoria "Przeprowadź inspekcję dostępu do obiektów" również musi być włączony.|  
|Domyślne środowisko użytkownika|Wszystkim uwierzytelnionym użytkownikom może zapisywać do dziennika aplikacji, więc nie jest wymagane nie dodatkowe uprawnienia krok procesów aplikacji.|Proces aplikacji (context) musi mieć `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<zachowania >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
