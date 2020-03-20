---
title: Inspekcja zdarzeń dotyczących zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 535f19741ff26e9472ce56ff06b670f7d0523be8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185453"
---
# <a name="auditing-security-events"></a>Inspekcja zdarzeń dotyczących zabezpieczeń
Aplikacje utworzone za pomocą programu Windows Communication Foundation (WCF) mogą rejestrować zdarzenia zabezpieczeń (powodzenie, niepowodzenie lub oba te aplikacje) za pomocą funkcji inspekcji. Zdarzenia są zapisywane w dzienniku zdarzeń systemu Windows i mogą być badane za pomocą Podglądu zdarzeń.  
  
 Inspekcja umożliwia administratorowi wykrycie ataku, który już wystąpił lub jest w toku. Ponadto inspekcja może pomóc deweloperowi w debugowaniu problemów związanych z zabezpieczeniami. Na przykład jeśli błąd w konfiguracji autoryzacji lub sprawdzania zasad przypadkowo odmawia dostępu do autoryzowanego użytkownika, deweloper może szybko odkryć i wyizolować przyczynę tego błędu, sprawdzając dziennik zdarzeń.  
  
 Aby uzyskać więcej informacji na temat zabezpieczeń WCF, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat programowania WCF, zobacz [Podstawowe programowanie WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Poziom inspekcji i zachowanie  
 Istnieją dwa poziomy audytów zabezpieczeń:  
  
- Poziom autoryzacji usługi, w którym osoba dzwoniąca jest autoryzowana.  
  
- Poziom wiadomości, w którym WCF sprawdza ważność wiadomości i uwierzytelnia wywołującego.  
  
 Można sprawdzić oba poziomy inspekcji pod kątem powodzenia lub niepowodzenia, który jest znany jako *zachowanie inspekcji*.  
  
## <a name="audit-log-location"></a>Lokalizacja dziennika inspekcji  
 Po określeniu poziomu inspekcji i zachowania użytkownik (lub administrator) może określić lokalizację dziennika inspekcji. Trzy opcje obejmują: Domyślne, Aplikacja i Zabezpieczenia. Po określeniu domyślne, rzeczywisty dziennik zależy od tego, który system jest używany i czy system obsługuje zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji, zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
 Aby zapisać w dzienniku `SeAuditPrivilege`zabezpieczeń wymaga . Domyślnie uprawnienie to mają tylko konta systemu lokalnego i usługi sieciowej. Aby zarządzać funkcjami `read` `delete` dziennika `SeSecurityPrivilege`zabezpieczeń i wymaga pliku . Domyślnie tylko administratorzy mają to uprawnienie.  
  
 Natomiast uwierzytelnieni użytkownicy mogą odczytywać i zapisywać w dzienniku aplikacji. System Windows XP domyślnie zapisuje zdarzenia inspekcji w dzienniku aplikacji. Dziennik może również zawierać informacje osobiste, które są widoczne dla wszystkich uwierzytelnionych użytkowników.  
  
## <a name="suppressing-audit-failures"></a>Pomijanie błędów inspekcji  
 Inną opcją podczas inspekcji jest, czy pominąć wszelkie niepowodzenia inspekcji. Domyślnie błąd inspekcji nie wpływa na aplikację. W razie potrzeby można jednak ustawić `false`opcję , co powoduje, że wyjątek ma zostać zgłoszony.  
  
## <a name="programming-auditing"></a>Inspekcja programowania  
 Zachowanie inspekcji można określić programowo lub za pomocą konfiguracji.  
  
### <a name="auditing-classes"></a>Klasy inspekcji  
 W poniższej tabeli opisano klasy i właściwości używane do programowania zachowania inspekcji.  
  
|Klasa|Opis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Włącza opcje ustawiania inspekcji jako zachowanie usługi.|  
|<xref:System.ServiceModel.AuditLogLocation>|Wyliczenie, aby określić, który dziennik do zapisu. Możliwe wartości to Domyślne, Aplikacja i Zabezpieczenia. Po wybraniu opcji Domyślna system operacyjny określa rzeczywistą lokalizację dziennika. Zobacz sekcję "Wybór dziennika zdarzeń aplikacji lub zabezpieczeń" w dalszej części tego tematu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Określa, które typy zdarzeń uwierzytelniania wiadomości są poddane inspekcji na poziomie wiadomości. Dostępne są `None` `Failure`opcje `Success`, `SuccessOrFailure`, i .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Określa, które typy zdarzeń autoryzacji usługi są poddane inspekcji na poziomie usługi. Dostępne są `None` `Failure`opcje `Success`, `SuccessOrFailure`, i .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Określa, co dzieje się z żądaniem klienta, gdy inspekcja nie powiedzie się. Na przykład, gdy usługa próbuje zapisać w dzienniku `SeAuditPrivilege`zabezpieczeń, ale nie ma . Wartość domyślna `true` wskazuje, że błędy są ignorowane, a żądanie klienta jest przetwarzane normalnie.|  
  
 Na przykład konfigurowania aplikacji do rejestrowania zdarzeń inspekcji, zobacz [Jak: Inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurowanie  
 Można również użyć konfiguracji, aby określić zachowanie inspekcji, dodając [ \<>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) w obszarze [ \<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Należy dodać element w [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) zachowaniu>jak pokazano w poniższym kodzie.  
  
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
  
 Jeśli inspekcja jest włączona, a nie jest określony, domyślną `auditLogLocation` nazwą dziennika jest dziennik "Zabezpieczenia" dla platformy obsługującej zapisywanie w dzienniku zabezpieczeń; w przeciwnym razie jest to dziennik "Application". Tylko systemy operacyjne Windows Server 2003 i Windows Vista obsługują zapisywanie w dzienniku zabezpieczeń. Aby uzyskać więcej informacji, zobacz sekcję "System operacyjny" w dalszej części tego tematu.  
  
## <a name="security-considerations"></a>Zagadnienia związane z zabezpieczeniami  
 Jeśli złośliwy użytkownik wie, że inspekcja jest włączona, osoba atakująca może wysyłać nieprawidłowe wiadomości, które powodują wpisy inspekcji do zapisania. Jeśli dziennik inspekcji jest wypełniony w ten sposób, system inspekcji kończy się niepowodzeniem. Aby to złagodzić, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> ustaw `true` właściwość i użyj właściwości Podglądu zdarzeń, aby kontrolować zachowanie inspekcji.  
  
 Zdarzenia inspekcji zapisane w dzienniku aplikacji w systemie Windows XP są widoczne dla każdego uwierzytelnionego użytkownika.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Wybieranie między dziennikami zdarzeń aplikacji i zabezpieczeń  
 Poniższe tabele zawierają informacje ułatwiające wybór, czy należy zalogować się do aplikacji lub dziennika zdarzeń zabezpieczeń.  
  
#### <a name="operating-system"></a>System operacyjny  
  
|System|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Dodatek SP2 dla systemu Windows XP lub nowszy|Obsługiwane|Nieobsługiwane|  
|Systemy Windows Server 2003 z sp1 i Windows Vista|Obsługiwane|Kontekst wątku musi posiadać`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Inne czynniki  
 Oprócz systemu operacyjnego w poniższej tabeli opisano inne ustawienia, które kontrolują włączenie rejestrowania.  
  
|Czynnikiem|Dziennik aplikacji|Dziennik zabezpieczeń|  
|------------|---------------------|------------------|  
|Zarządzanie zasadami inspekcji|Nie dotyczy.|Wraz z konfiguracją dziennik zabezpieczeń jest również kontrolowany przez zasady lokalnego urzędu zabezpieczeń (LSA). Należy również włączyć kategorię "Inspekcja dostępu do obiektów".|  
|Domyślne środowisko użytkownika|Wszyscy uwierzytelnieni użytkownicy mogą zapisywać w dzienniku aplikacji, więc dla procesów aplikacji nie jest potrzebny żaden dodatkowy krok uprawnień.|Proces składania wniosków (kontekst) musi mieć `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Podstawy programowania przy użyciu programu WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Instrukcje: inspekcja zdarzeń zabezpieczeń](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<>serwissecurityaudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<zachowania>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
