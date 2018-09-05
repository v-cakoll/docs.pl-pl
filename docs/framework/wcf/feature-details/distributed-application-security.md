---
title: Rozproszone zabezpieczenia aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0dbc06afd4695b85f426fad2859b4c6d4b6684d6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661077"
---
# <a name="distributed-application-security"></a>Rozproszone zabezpieczenia aplikacji
Zabezpieczenia usług Windows Communication Foundation (WCF) jest dzielony na trzy główne obszary funkcjonalne: transfer zabezpieczeń, kontroli dostępu i inspekcji. Bezpieczeństwie transferu zapewnia integralność, poufności i uwierzytelniania. Zabezpieczenia transferu za pomocą jednej z następujących czynności: zabezpieczenia, zabezpieczenia komunikatów transportu lub `TransportWithMessageCredential`.  
  
 Aby uzyskać omówienie zabezpieczeń komunikatów WCF, zobacz [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat dwie części zabezpieczeń WCF zobacz [autoryzacji](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) i [inspekcji](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Scenariusze zabezpieczeń transferu  
 Typowe scenariusze, korzystających z usługi WCF bezpieczeństwie transferu obejmują:  
  
-   Bezpiecznego transferu za pomocą Windows. Klient WCF i usługi są wdrażane w Windows (lub w domenie w lesie Windows). Komunikaty zawierają dane osobowe, więc wymagane jest miedzy innymi wzajemnego uwierzytelniania klienta i usługi, integralność komunikatów i poufność komunikatów. Ponadto wymagany jest dowód, określonej transakcji wystąpił, na przykład odbiorcy wiadomości powinien rejestrować informacje o podpisie.  
  
-   Bezpiecznego transferu za pomocą `UserName` i HTTPS. Klient WCF i usługi muszą zostać opracowany, aby działały w Internecie. Poświadczenia klienta uwierzytelniania względem bazy danych par nazwa/hasło użytkownika. Usługa jest wdrażana na adres HTTPS, przy użyciu zaufanego certyfikatu Secure Sockets Layer (SSL). Ponieważ komunikaty przesyłane za pośrednictwem Internetu, klienta i usługi potrzebne uwierzytelniali się wzajemnie i poufności i integralności wiadomości muszą zostać zachowane podczas transferu.  
  
-   Bezpiecznego transferu za pomocą certyfikatów. Klienta WCF i usługi muszą być tworzone do pracy za pośrednictwem publicznej sieci internet. Klienta i usługi mają certyfikaty, które mogą służyć do zabezpieczenia wiadomości. Klient i usługa używać Internetu komunikują się ze sobą i wykonywanie transakcji o wysokiej wartości, które wymagają integralność wiadomości, poufności i wzajemnego uwierzytelniania.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integralność, poufności i uwierzytelniania  
 Trzy funkcje — integralności, poufność i uwierzytelnianie — są ze sobą nazywane bezpieczeństwie transferu. Bezpieczeństwie transferu zawiera funkcje, które pomogą zminimalizować zagrożenia aplikacji rozproszonej. W poniższej tabeli krótko opisano trzy funkcje, które składają się na bezpieczeństwie transferu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|Integralność|*Integralność* gwarancji, że dane są kompletne i dokładne, szczególnie po-przenoszone z jednego miejsca do drugiego i prawdopodobnie została przeczytana przy wielu uczestników. Integralność musi zostać zachowany w celu uniknięcia niepowołanych manipulacji danymi i zwykle odbywa się cyfrowego podpisywania wiadomości.|  
|Poufność|*Poufność* gwarancji, że komunikat nie został odczytany przez nikogo innego niż zamierzony czytnika. Na przykład numer karty kredytowej muszą być przechowywane zawierających poufne dane podczas ich przesyłania przez Internet. Poufność często jest zapewniana przez szyfrowanie danych przy użyciu publicznego klucza i prywatnego klucza systemu.|  
|Uwierzytelnianie|*Uwierzytelnianie* jest weryfikacja tożsamości. Na przykład korzystając z konta bankowego, należy bezwzględnie możliwość rzeczywiste właściciela konta do wycofania środków. Za pomocą różnych oznacza, że można podać uwierzytelniania. Jednej wspólnej metody to system użytkownika i hasło. Drugi polega na użyciu certyfikatu X.509, dostarczone przez stronę trzecią.|  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 Usługi WCF ma kilka trybów bezpieczeństwie transferu, które są opisane w poniższej tabeli.  
  
|Tryb|Opis|  
|----------|-----------------|  
|Brak|Bez zabezpieczeń znajduje się w warstwie transportowej lub warstwie wiadomości. Brak wstępnie zdefiniowanych powiązań Użyj tego trybu domyślnie z wyjątkiem [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element lub, w przypadku korzystania z kodu, <xref:System.ServiceModel.BasicHttpBinding> klasy.|  
|Transportu|Używa bezpiecznym transportem, taki jak HTTPS integralności, poufności i wzajemnego uwierzytelniania.|  
|Komunikat|Używa zabezpieczeń komunikatu protokołu SOAP integralności, poufność i wzajemnego uwierzytelniania. Komunikaty protokołu SOAP są zabezpieczone zgodnie ze standardami WS-Security.|  
|W trybie mieszanym|Zastosowań transportu zabezpieczeń uwierzytelniania integralności, poufności i serwera. Używa komunikatu zabezpieczenia (WS-Security i innych standardów) do uwierzytelniania klientów.<br /><br /> (Jest to wyliczenie, w tym trybie `TransportWithMessageCredential`.)|  
|Oba|Wykonuje ochrony i uwierzytelnianie na obu poziomach. Ten tryb jest dostępna tylko w [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) elementu.|  
  
## <a name="credentials-and-transfer-security"></a>Poświadczenia i bezpieczeństwie transferu  
 A *poświadczeń* to dane, które są prezentowane w celu ustalenia tożsamości lub funkcji. Umożliwienie korzystania z poświadczeń obejmuje prezentowanie danych i dowodu posiadania danych. Usługi WCF obsługuje różne typy poświadczeń na poziomach zabezpieczeń transportu i komunikatu. Można określić typ poświadczeń dla wiązania WCF.  
  
 W wielu krajach lub regionach prawa jazdy jest przykładem poświadczenia. Licencja zawiera reprezentujący tożsamości i możliwości swoich danych. Zawiera ono dowód przesyłany w postaci obrazu inicjator. Licencja jest wystawiony przez zaufany urząd, zwykle rządowych działu licencjonowania. Licencja jest zapieczętowany i może zawierać hologram, pokazujący, że nie został zmodyfikowany lub podrobić.  
  
 Na przykład należy wziąć pod uwagę dwa typy obsługiwanych w programie WCF poświadczeń: nazwa użytkownika oraz (X.509) certyfikatu poświadczeń.  
  
 Poświadczenie nazwy użytkownika, aby uzyskać nazwę użytkownika reprezentuje tożsamości, a hasło przedstawia dowodu posiadania. Zaufany urząd w tym przypadku to system, który sprawdza poprawność nazwy użytkownika i hasła.  
  
 W poświadczenie certyfikatu nazwa podmiotu, alternatywna nazwa podmiotu lub określonych pól w ramach certyfikatu może służyć do reprezentowania tożsamości i/lub funkcji. Dowód przesyłany danych w poświadczeniu została ustanowiona przy użyciu skojarzony klucz prywatny do generowania podpisu.  
  
 Więcej informacji na temat programowania transferu zabezpieczeń i określania poświadczeń można zobaczyć [powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) i [zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Typy poświadczeń klienta transportu  
 W poniższej tabeli przedstawiono możliwe wartości, które są używane podczas tworzenia aplikacji, która korzysta z transferu zabezpieczeń. Można użyć tych wartości za pomocą kodu lub ustawienia powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, klient musi przedstawić żadnych poświadczeń. Przekłada się to anonimowym klientem.|  
|Podstawowy|Określa uwierzytelnianie podstawowe.  Aby uzyskać więcej informacji, zobacz RFC2617, "[uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Podsumowanie|Określa uwierzytelnianie szyfrowane.  Aby uzyskać więcej informacji, zobacz RFC2617, "[uwierzytelnianie HTTP: podstawowe i uwierzytelnianie szyfrowane](https://go.microsoft.com/fwlink/?LinkId=88313)."|  
|Uwierzytelnianie NTLM|Określa uwierzytelnianie Windows do domeny Windows przy użyciu negocjacji interfejsu SSPI.<br /><br /> Negocjacji interfejsu SSPI powoduje przy użyciu protokołu Kerberos lub NT LanMan (NTLM).|  
|Windows|Określa uwierzytelnianie Windows do domeny Windows przy użyciu interfejsu SSPI. Interfejs SSPI wybiera z protokołu Kerberos lub NTLM jako usługi uwierzytelniania.<br /><br /> Najpierw; próbuje interfejsu SSPI protokołu Kerberos Jeśli ono zawiedzie, następnie używa protokołu NTLM.|  
|Certyfikat|Wykonuje uwierzytelnianie klientów przy użyciu certyfikatu X.509 zwykle.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta wiadomości  
 W poniższej tabeli przedstawiono możliwe wartości, które są używane podczas tworzenia aplikacji, która używa zabezpieczenia wiadomości. Można użyć tych wartości za pomocą kodu lub ustawienia powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Umożliwia usłudze na współdziałanie z anonimowych klientów.|  
|Windows|Umożliwia wymianę komunikatów SOAP występuje w kontekście uwierzytelnionych poświadczeń Windows. Używa mechanizmu negocjacji interfejsu SSPI, do wyboru protokołu Kerberos lub NTLM jako usługi uwierzytelniania.|  
|Nazwa użytkownika|Umożliwia usłudze wymagają uwierzytelnienia klienta za pomocą poświadczenie nazwy użytkownika. Należy pamiętać, usługi WCF nie zezwala na wszystkie operacje kryptograficzne przy użyciu nazwy użytkownika, np. generowania podpisu i szyfrowania danych. W efekcie WCF wymusza, czy transport jest zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|  
|Certyfikat|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą certyfikatu.|  
|[!INCLUDE[infocard](../../../../includes/infocard-md.md)]|Umożliwia usłudze wymagają który uwierzytelnienia klienta za pomocą [!INCLUDE[infocard](../../../../includes/infocard-md.md)].|  
  
### <a name="programming-credentials"></a>Programowanie poświadczeń  
 Dla każdego typu poświadczeń klienta model programowania WCF umożliwia określanie wartości poświadczeń i poświadczeń moduły weryfikacji za pomocą zachowań usługi i zachowania kanału.  
  
 Zabezpieczenia WCF ma dwa typy poświadczeń: zachowania poświadczeń i zachowania poświadczeń kanału usługi. Poświadczenie zachowań w programie WCF Określ rzeczywistych danych, to znaczy, poświadczenia używane do spełniają wymogi bezpieczeństwa wyrażona za pomocą powiązania. W programie WCF Klasa klienta jest składnik czasu wykonywania, który wykonuje konwersję między wywołania operacji i komunikatów. Wszyscy klienci dziedziczyć <xref:System.ServiceModel.ClientBase%601> klasy. <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> Właściwości w klasie bazowej można określić różne wartości poświadczeń klienta.  
  
 W programie WCF zachowania usługi są atrybuty stosowane do klasy Implementowanie kontraktu usługi (interfejs), aby programistycznie sterować usługi. <xref:System.ServiceModel.Description.ServiceCredentials> Klasy można określić certyfikaty dla ustawienia usługi poświadczenia i klienta sprawdzania poprawności dla różnych typów poświadczeń klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Model negocjowanie zabezpieczeń komunikatów  
 Tryb zabezpieczeń wiadomości umożliwia wykonywanie bezpieczeństwie transferu, dzięki czemu poświadczenia usługi jest skonfigurowana na klientem poza pasmem. Na przykład jeśli używasz certyfikatu przechowywanego w magazynie certyfikatów Windows, należy użyć narzędzia, takiego jak przystawka programu Microsoft Management Console (MMC).  
  
 Tryb zabezpieczeń wiadomości umożliwia wykonywanie bezpieczeństwie transferu, dzięki czemu poświadczenia usługi są wymieniane przy użyciu klienta w ramach początkowego negocjowania. Aby włączyć negocjacji, ustaw <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> właściwość `true`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
