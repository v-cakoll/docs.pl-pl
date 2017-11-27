---
title: Rozproszone zabezpieczenia aplikacji
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
caps.latest.revision: "32"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 842ce0efefcc026ad33d9be3b2b681fcfc9c0b59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="distributed-application-security"></a>Rozproszone zabezpieczenia aplikacji
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]zabezpieczeń jest podzielone na trzy główne obszary funkcjonalności: transfer zabezpieczeń, kontroli dostępu i inspekcji. Transfer zabezpieczeń zapewnia integralność, poufność i uwierzytelniania. Zabezpieczenia transferu za pomocą jednej z następujących czynności: transportu zabezpieczenia, zabezpieczenia wiadomości lub `TransportWithMessageCredential`.  
  
 Omówienie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dwie części z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczeń, zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) i [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Transfer scenariusze zabezpieczeń  
 Typowych scenariuszy korzystających z [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transfer zabezpieczeń są następujące:  
  
-   Zapewnienia bezpiecznego transferu przy użyciu systemu Windows. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta i usługi są wdrażane w domenie systemu Windows (lub lasu systemu Windows). Komunikaty zawierają dane osobowe, wymagania dotyczące obejmują wzajemnego uwierzytelniania klienta i usługi, integralności i poufności komunikatów. Ponadto wymagane jest potwierdzenie czy danej transakcji wystąpił, na przykład zarejestrować informacje o podpisie odbiorcy wiadomości.  
  
-   Zapewnienia bezpiecznego transferu za pomocą `UserName` i HTTPS. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient i usługa muszą być opracowany, aby działały w Internecie. Poświadczenia klienta uwierzytelniania względem bazy danych par nazwa/hasło użytkownika. Usługa jest wdrażana na adres HTTPS przy użyciu zaufanego certyfikatu Secure Sockets Layer (SSL). Ponieważ komunikaty są przesyłane za pośrednictwem Internetu, klient i usługa muszą być wzajemnie uwierzytelniane i poufności i integralności wiadomości, które muszą zostać zachowane podczas transferu.  
  
-   Zapewnienia bezpiecznego transferu za pomocą certyfikatów. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klient i usługa musi zostać opracowana do pracy za pośrednictwem publicznego Internetu. Klient i usługa mają certyfikaty, które mogą służyć do zabezpieczenia wiadomości. Klient i usługa korzystanie z Internetu, aby komunikować się ze sobą i wykonywać transakcje wysokiej wartości, które wymagają integralności komunikatu, poufności i wzajemnego uwierzytelniania.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integralność, poufności i uwierzytelniania  
 Trzy funkcje — integralności i poufności uwierzytelniania — łącznie są nazywane transfer zabezpieczeń. Transfer zabezpieczeń zawiera funkcje, które pomogą zminimalizować zagrożenia w aplikacji rozproszonej. W poniższej tabeli opisano krótko trzy funkcje, które tworzą transfer zabezpieczeń.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|Integralność|*Integralność* pewności, że dane są kompletne i dokładne, szczególnie po przechodzić z jednego miejsca do innego i prawdopodobnie został odczytany wiele złośliwych użytkowników. Integralność muszą zostać zachowane, aby zapobiec modyfikowaniu danych i zazwyczaj jest to osiągane przez cyfrowego podpisywania wiadomości.|  
|Poufność|*Poufność* gwarancji, że komunikat nie został odczytany przez nikt inny oprócz zamierzone czytnika. Na przykład numer karty kredytowej musi poufne podczas ich przesyłania przez Internet. Poufność często są udostępniane przez szyfrowania danych przy użyciu publicznego klucza i prywatnego klucza systemu.|  
|Uwierzytelnianie|*Uwierzytelnianie* jest weryfikacja tożsamości. Na przykład korzystając z konta bankowego, należy bezwzględnie możliwość rzeczywiste właściciela konta do wycofania środków. Uwierzytelnianie może być udostępniane przez różnych środków. Jednej wspólnej metody to system użytkownika i hasło. Drugim jest użycie certyfikatu X.509, który jest świadczona przez inną firmę.|  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]trybach kilka transfer zabezpieczeń, które zostały opisane w poniższej tabeli.  
  
|Tryb|Opis|  
|----------|-----------------|  
|Brak|Nie zabezpieczenia w przypadku warstwy transportu lub w warstwie wiadomości. Brak wstępnie zdefiniowanych powiązań tego trybu należy używać domyślnie z wyjątkiem [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element lub przy użyciu kodu, <xref:System.ServiceModel.BasicHttpBinding> klasy.|  
|Transportu|Używa bezpiecznego transportu, taki jak HTTPS integralności, poufności i wzajemnego uwierzytelniania.|  
|Komunikat|Używa komunikatu protokołu SOAP zabezpieczeń integralności, poufność i wzajemnego uwierzytelniania. Według standardów WS-Security zabezpieczonych wiadomości SOAP.|  
|Tryb mieszany|Używa transportu zabezpieczeń uwierzytelniania integralności, poufności i serwera. Używa komunikatu zabezpieczenia (WS-Security i innych standardów) do uwierzytelniania klientów.<br /><br /> (Jest to wyliczenie w tym trybie `TransportWithMessageCredential`.)|  
|Zarówno|Wykonuje ochrony i uwierzytelniania na obu poziomach. Ten tryb jest dostępny tylko w [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) elementu.|  
  
## <a name="credentials-and-transfer-security"></a>Poświadczenia i Transfer zabezpieczeń  
 A *poświadczeń* się dane, które są prezentowane w celu ustalenia tożsamości lub funkcji. Umożliwienie korzystania z poświadczeń polega na prezentacji danych i dowodu posiadania danych. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsługuje różne typy poświadczeń na poziomie zabezpieczeń transportu i komunikatu. Można określić rodzajem poświadczenia dla [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania.  
  
 W wielu krajach lub regionach jazdy jest przykładem poświadczenie. Licencji zawiera dane reprezentujące tożsamości i możliwości w jeden. Zawiera ona dowodu posiadania w formie obrazu właściciel. Licencji wystawiony przez zaufany urząd zwykle rządowych działu licencjonowania. Licencja jest zapieczętowany i może zawierać hologram, pokazujący, że nie został zmieniony przez niepowołane lub podrobić.  
  
 Na przykład należy wziąć pod uwagę dwa typy obsługiwanych w poświadczeń [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: nazwa użytkownika oraz (X.509) certyfikatu poświadczeń.  
  
 Poświadczenie nazwy użytkownika tożsamości reprezentuje nazwę użytkownika i hasło stanowi potwierdzenie posiadania. Zaufany urząd to w takim przypadku system, który sprawdza poprawność nazwy użytkownika i hasła.  
  
 W poświadczeniach certyfikatu do reprezentowania tożsamości i/lub możliwości można użyć nazwy podmiotu, alternatywna nazwa podmiotu lub określonych pól w certyfikacie. Potwierdzenie posiadania danych w poświadczeniu została ustanowiona przy użyciu skojarzony klucz prywatny do generowania podpisu.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Programowanie zabezpieczeń transfer i określania poświadczeń, zobacz [powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) i [zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Typy poświadczeń klienta transportu  
 W poniższej tabeli przedstawiono możliwe wartości używane podczas tworzenia aplikacji, która korzysta z transferu zabezpieczeń. Możesz użyć tych wartości za pomocą kodu lub ustawienia powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient musi przedstawiać żadnego poświadczenia. Umożliwia to anonimowym klientem.|  
|Podstawowy|Określa uwierzytelnianie podstawowe.  Aby uzyskać dodatkowe informacje, zobacz RFC2617, "[uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Skrót|Określa uwierzytelnianie szyfrowane.  Aby uzyskać dodatkowe informacje, zobacz RFC2617, "[uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego](http://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Uwierzytelnianie NTLM|Określa uwierzytelnianie systemu Windows przy użyciu negocjacji SSPI w domenie systemu Windows.<br /><br /> Negocjowanie interfejsu SSPI powoduje przy użyciu protokołu Kerberos lub LanMan NT (NTLM).|  
|Windows|Określa uwierzytelnianie systemu Windows przy użyciu interfejsu SSPI w domenie systemu Windows. Interfejs SSPI wybiera z protokołu Kerberos lub NTLM jako usługa uwierzytelniania.<br /><br /> Najpierw; próbuje interfejsu SSPI protokołu Kerberos w przypadku niepowodzenia następnie używa uwierzytelniania NTLM.|  
|certyfikat|Wykonuje uwierzytelnianie klientów za pomocą certyfikatu X.509 zwykle.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta komunikatu  
 W poniższej tabeli przedstawiono możliwe wartości używane podczas tworzenia aplikacji, która korzysta z zabezpieczeń wiadomości. Możesz użyć tych wartości za pomocą kodu lub ustawienia powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Umożliwia usłudze na współdziałanie z anonimowego klientów.|  
|Windows|Umożliwia wymianę wiadomości SOAP występuje w kontekście uwierzytelnionych poświadczeń systemu Windows. Używa mechanizmu negocjacji SSPI z protokołu Kerberos lub NTLM jako usługi uwierzytelniania.|  
|Nazwa użytkownika|Umożliwia usłudze wymagają uwierzytelnienia klienta z poświadczenie nazwy użytkownika. Należy pamiętać, że [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie zezwala na wszystkie operacje kryptograficzne z nazwą użytkownika, takie jak generowania podpis i szyfrowanie danych. W efekcie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymusza, czy transport jest zabezpieczony, korzystając z poświadczeń nazwy użytkownika.|  
|certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Programowanie poświadczeń  
 Dla każdego typu poświadczeń klienta [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model programowania umożliwia określenie wartości poświadczeń i modułów sprawdzania poprawności poświadczeń przy użyciu usługi zachowania i zachowania kanału.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpieczenia mają dwa rodzaje poświadczeń: poświadczenia zachowania i zachowania poświadczeń kanału usługi service. Poświadczeń zachowania w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Określ dane, a mianowicie, poświadczenia używane w celu spełnienia wymagań zabezpieczeń wyrazić za pomocą powiązania. W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], klasa klienta to składnik czasu wykonywania, który wykonuje konwersję między wywołania operacji i komunikatów. Wszyscy klienci dziedziczyć <xref:System.ServiceModel.ClientBase%601> klasy. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwości dla klasy podstawowej można określić różne wartości poświadczeń klienta.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], zachowania usługi są atrybuty stosowane do klasy Implementowanie kontraktu usługi (interface), można programowo zarządzać usługi. <xref:System.ServiceModel.Description.ServiceCredentials> Klasy można określić certyfikaty dla ustawienia usługi poświadczenia i klienta sprawdzania poprawności dla różnych typów poświadczeń klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Wzór negocjacji zabezpieczeń komunikatów  
 Trybu zabezpieczenia wiadomości umożliwia wykonywanie transfer zabezpieczeń, tak aby poświadczenie usługi jest skonfigurowany po stronie klienta poza pasmem. Na przykład jeśli używasz certyfikat przechowywany w magazynie certyfikatów systemu Windows, należy użyć narzędzia, takiego jak przystawki programu Microsoft Management Console (MMC).  
  
 Trybu zabezpieczenia wiadomości umożliwia również wykonywanie transfer zabezpieczeń tak, aby poświadczenie usługi są wymieniane z klientem w ramach początkowej negocjacji. Aby włączyć negocjacji, ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwości `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń systemu Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
