---
title: Inspekcja zdarzeń dotyczących zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: e1c3e3d7697bf9a85cf0ab7df35a4755939d1df0
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921411"
---
# <a name="auditing-security-events"></a>Inspekcja zdarzeń dotyczących zabezpieczeń
Aplikacje utworzone za pomocą Windows Communication Foundation (WCF) mogą rejestrować zdarzenia zabezpieczeń (sukces, Niepowodzenie lub oba) przy użyciu funkcji inspekcji. Zdarzenia są zapisywane w dzienniku zdarzeń systemu Windows i można je zbadać przy użyciu Podgląd zdarzeń.  
  
 Inspekcja zapewnia administratorowi możliwość wykrywania ataku, który już się zakończył lub w toku. Ponadto inspekcja może pomóc deweloperowi w debugowaniu problemów związanych z zabezpieczeniami. Na przykład jeśli błąd w konfiguracji zasad autoryzacji lub sprawdzania przypadkowo odmówi dostępu autoryzowanemu użytkownikowi, deweloper może szybko wykryć i odizolować przyczynę tego błędu, sprawdzając dziennik zdarzeń.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń WCF, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat programowania WCF, zobacz [podstawowe programowanie WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Poziom inspekcji i zachowanie  
 Istnieją dwa poziomy inspekcji zabezpieczeń:  
  
- Poziom autoryzacji usługi, w którym obiekt wywołujący jest autoryzowany.  
  
- Poziom komunikatu, w którym usługa WCF sprawdza poprawność komunikatów i uwierzytelnia obiekt wywołujący.  
  
 Można sprawdzić zarówno poziomy inspekcji, jak i błędy, które są znane jako *zachowanie inspekcji*.  
  
## <a name="audit-log-location"></a>Lokalizacja dziennika inspekcji  
 Po określeniu poziomu inspekcji i zachowania, użytkownik (lub administrator) może określić lokalizację dziennika inspekcji. Dostępne są trzy opcje: domyślne, aplikacja i zabezpieczenia. Po określeniu wartości domyślnej rzeczywisty dziennik zależy od używanego systemu i od tego, czy system obsługuje zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji, zobacz sekcję "system operacyjny" w dalszej części tego tematu.  
  
 Aby można było zapisać w dzienniku zabezpieczeń, wymagany jest `SeAuditPrivilege`. Domyślnie tylko konta systemu lokalnego i usługi sieciowej mają to uprawnienie. Zarządzanie funkcjami dziennika zabezpieczeń `read` i `delete` wymaga `SeSecurityPrivilege`. Domyślnie tylko Administratorzy mają to uprawnienie.  
  
 Z drugiej strony uwierzytelnieni użytkownicy mogą odczytywać i zapisywać dane w dzienniku aplikacji. System Windows XP zapisuje zdarzenia inspekcji domyślnie do dziennika aplikacji. Dziennik może również zawierać informacje osobiste, które są widoczne dla wszystkich uwierzytelnionych użytkowników.  
  
## <a name="suppressing-audit-failures"></a>Pomijanie błędów inspekcji  
 Inna opcja podczas inspekcji wskazuje, czy pomijać błędy inspekcji. Domyślnie Niepowodzenie inspekcji nie ma wpływu na aplikację. Jeśli jednak jest to wymagane, można ustawić opcję na `false`, co spowoduje zgłoszenie wyjątku.  
  
## <a name="programming-auditing"></a>Inspekcja programowania  
 Możesz określić zachowanie inspekcji programowo lub za pomocą konfiguracji.  
  
### <a name="auditing-classes"></a>Klasy inspekcji  
 W poniższej tabeli opisano klasy i właściwości używane do programowania zachowań inspekcji.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Włącza ustawienie opcji inspekcji jako zachowania usługi.|  
|<xref:System.ServiceModel.AuditLogLocation>|Wyliczenie, aby określić, który Dziennik ma zostać zapisany. Możliwe wartości to domyślne, aplikacja i zabezpieczenia. Po wybraniu opcji domyślne system operacyjny określi rzeczywistą lokalizację dziennika. Zobacz sekcję "wybór dziennika zdarzeń aplikacji lub zabezpieczeń" w dalszej części tego tematu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Określa, które typy zdarzeń uwierzytelniania wiadomości są poddawane inspekcji na poziomie wiadomości. Dostępne są następujące opcje `None`, `Failure`, `Success`i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Określa, które typy zdarzeń autoryzacji usługi są poddawane inspekcji na poziomie usługi. Dostępne są następujące opcje `None`, `Failure`, `Success`i `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Określa, co się dzieje z żądaniem klienta, gdy Inspekcja nie powiedzie się. Na przykład gdy usługa próbuje zapisać w dzienniku zabezpieczeń, ale nie ma `SeAuditPrivilege`. Wartość domyślna `true` wskazuje, że błędy są ignorowane, a żądanie klienta jest przetwarzane normalnie.|  
  
 Przykład konfigurowania aplikacji do rejestrowania zdarzeń inspekcji można znaleźć w temacie [How to: Audit Events Security](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfiguracja  
 Można również użyć opcji konfiguracja, aby określić zachowanie inspekcji poprzez dodanie [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pod [> zachowania\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Należy dodać element pod [\<zachowaniem >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) , jak pokazano w poniższym kodzie.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
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
  
 Jeśli inspekcja jest włączona i nie określono `auditLogLocation`, domyślną nazwą dziennika jest dziennik "zabezpieczenia" dla platformy obsługującej zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie jest to dziennik "aplikacja". Tylko systemy operacyjne Windows Server 2003 i Windows Vista obsługują zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji, zobacz sekcję "system operacyjny" w dalszej części tego tematu.  
  
## <a name="security-considerations"></a>Zagadnienia dotyczące zabezpieczeń  
 Jeśli złośliwy użytkownik wie, że inspekcja jest włączona, osoba atakująca może wysłać nieprawidłowe komunikaty, które powodują zapisanie wpisów inspekcji. Jeśli dziennik inspekcji zostanie wypełniony w ten sposób, system inspekcji zakończy się niepowodzeniem. Aby rozwiązać ten problem, ustaw właściwość <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true` i Użyj właściwości Podgląd zdarzeń, aby kontrolować zachowanie inspekcji.  
  
 Zdarzenia inspekcji, które są zapisywane w dzienniku aplikacji w systemie Windows XP, są widoczne dla każdego uwierzytelnionego użytkownika.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Wybieranie między aplikacjami a dziennikami zdarzeń zabezpieczeń  
 Poniższe tabele zawierają informacje ułatwiające określenie, czy należy zalogować się do aplikacji, czy dziennika zdarzeń zabezpieczeń.  
  
#### <a name="operating-system"></a>System operacyjny  
  
|System|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Windows XP z dodatkiem SP2 lub nowszym|Obsługiwana|Nieobsługiwane|  
|Windows Server 2003 z dodatkiem SP1 i Windows Vista|Obsługiwana|Kontekst wątku musi mieć `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Inne czynniki  
 Oprócz systemu operacyjnego w poniższej tabeli opisano inne ustawienia kontrolujące włączenie rejestrowania.  
  
|współczynnik|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Inspekcja zarządzania zasadami|Nie dotyczy.|Wraz z konfiguracją dziennik zabezpieczeń jest również kontrolowany przez zasady urzędu zabezpieczeń lokalnych (LSA). Należy również włączyć kategorię "Przeprowadź inspekcję dostępu do obiektów".|  
|Środowisko użytkownika domyślnego|Wszyscy uwierzytelnieni użytkownicy mogą zapisywać w dzienniku aplikacji, więc nie jest wymagany żaden dodatkowy krok uprawnień dla procesów aplikacji.|Proces aplikacji (Context) musi mieć `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [zachowania \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
