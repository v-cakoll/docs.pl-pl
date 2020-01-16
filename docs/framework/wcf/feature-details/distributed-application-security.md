---
title: Zabezpieczenia aplikacji rozproszonej
ms.date: 03/30/2017
helpviewer_keywords:
- distributed application security [WCF]
- security [WCF], transfer
ms.assetid: 53928a10-e474-46d0-ab90-5f98f8d7b668
ms.openlocfilehash: cb271bcf8fb27bae4c8ef6b60df0f8d2940ecb9a
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964828"
---
# <a name="distributed-application-security"></a>Zabezpieczenia aplikacji rozproszonej
Zabezpieczenia Windows Communication Foundation (WCF) są podzielone na trzy główne obszary funkcjonalne: zabezpieczenia transferu, kontrola dostępu i inspekcja. Zabezpieczenia transferu zapewniają integralność, poufność i uwierzytelnianie. Zabezpieczenia transferu są udostępniane przez jedną z następujących czynności: zabezpieczenia transportu, zabezpieczenia komunikatów lub `TransportWithMessageCredential`.  
  
 Aby zapoznać się z omówieniem zabezpieczeń komunikatów WCF, zobacz [Omówienie zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md). Aby uzyskać więcej informacji na temat pozostałych dwóch elementów zabezpieczeń WCF, zobacz [autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md) i [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
## <a name="transfer-security-scenarios"></a>Przenieś scenariusze zabezpieczeń  
 Typowe scenariusze wykorzystujące zabezpieczenia transferu WCF obejmują następujące elementy:  
  
- Bezpieczny transfer przy użyciu systemu Windows. Klient i usługa WCF są wdrażane w domenie systemu Windows (lub w lesie systemu Windows). Komunikaty zawierają dane osobowe, dlatego wymagania obejmują wzajemne uwierzytelnianie klienta i usługi, integralność komunikatów i poufność komunikatów. Ponadto należy sprawdzić, czy dana transakcja wystąpiła, na przykład, odbiorca wiadomości powinien zarejestrować informacje o podpisie.  
  
- Bezpieczny transfer przy użyciu `UserName` i protokołu HTTPS. Aby pracować przez Internet, należy opracować klienta i usługę programu WCF. Poświadczenia klienta są uwierzytelniane względem bazy danych par nazwa/hasło użytkownika. Usługa jest wdrażana pod adresem HTTPS przy użyciu zaufanego certyfikatu SSL (SSL). Ze względu na to, że komunikaty są przesyłane przez Internet, klient i usługa muszą być uwierzytelniane wzajemnie, a podczas przesyłania należy zachować poufność i integralność komunikatów.  
  
- Bezpieczny transfer przy użyciu certyfikatów. Aby pracować nad publicznym Internetem, należy opracować klienta i usługę programu WCF. Klient i usługa mają certyfikaty, których można użyć do zabezpieczenia komunikatów. Klient i usługa używają Internetu do komunikowania się ze sobą i wykonywania transakcji wysokiej wartości, które wymagają integralności komunikatów, poufności i wzajemnego uwierzytelniania.  
  
## <a name="integrity-confidentiality-and-authentication"></a>Integralność, poufność i uwierzytelnianie  
 Trzy funkcje — integralność, poufność i uwierzytelnianie — są razem nazywane zabezpieczeniami transferu. Zabezpieczenia transferu udostępniają funkcje, które pomagają w ograniczeniu zagrożeń do aplikacji rozproszonej. W poniższej tabeli krótko opisano trzy funkcje, które składają się na zabezpieczenia transferu.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|Integralność|*Integralność* stanowi gwarancję, że dane są kompletne i dokładne, zwłaszcza wtedy, gdy przechodzą z jednego punktu do drugiego i prawdopodobnie zostały odczytane przez wiele aktorów. Należy zachować integralność, aby uniemożliwić manipulowanie danymi i jest zazwyczaj osiągane przez cyfrowe podpisywanie wiadomości.|  
|Poufność|*Poufność* stanowi gwarancję, że wiadomość nie została odczytana przez żadną osobę inną niż zamierzony czytnik. Na przykład numer karty kredytowej musi być poufny, ponieważ jest wysyłany przez Internet. Poufność jest często zapewniana przez szyfrowanie danych przy użyciu klucza publicznego/schematu klucza prywatnego.|  
|Uwierzytelnianie|*Uwierzytelnianie* jest weryfikacją tożsamości, której dotyczy żądanie. Na przykład w przypadku korzystania z konta bankowego konieczne jest, aby tylko rzeczywisty właściciel konta mógł wycofać fundusze. Uwierzytelnianie może być zapewniane przez różne sposoby. Jedną z typowych metod jest system użytkownika/hasła. Drugi to użycie certyfikatu X. 509, który jest dostarczany przez inną firmę.|  
  
## <a name="security-modes"></a>Tryby zabezpieczeń  
 Funkcja WCF ma kilka trybów zabezpieczeń transferu, które opisano w poniższej tabeli.  
  
|Tryb|Opis|  
|----------|-----------------|  
|Brak|W warstwie transportowej lub w warstwie wiadomości nie są dostępne żadne zabezpieczenia. Żadne ze wstępnie zdefiniowanych powiązań domyślnie nie korzysta z tego trybu, z wyjątkiem [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elementu lub, w przypadku użycia kodu, klasy <xref:System.ServiceModel.BasicHttpBinding>.|  
|Transport|Używa bezpiecznego transportu, takiego jak HTTPS w celu zapewnienia integralności, poufności i uwierzytelniania wzajemnego.|  
|Komunikat|Używa zabezpieczeń protokołu SOAP w celu zapewnienia integralności, poufności i uwierzytelniania wzajemnego. Komunikaty protokołu SOAP są zabezpieczone zgodnie ze standardami WS-Security.|  
|Tryb mieszany|Stosuje zabezpieczenia transportu w celu zapewnienia integralności, poufności i uwierzytelniania serwera. Używa zabezpieczeń komunikatów (WS-Security i innych standardów) do uwierzytelniania klientów.<br /><br /> (To Wyliczenie dla tego trybu jest `TransportWithMessageCredential`.)|  
|Oba|Wykonuje ochronę i uwierzytelnianie na obu poziomach. Ten tryb jest dostępny tylko w [> elementu\<ow msmqbinding](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md) .|  
  
## <a name="credentials-and-transfer-security"></a>Poświadczenia i zabezpieczenia transferu  
 *Poświadczenie* to dane, które są prezentowane w celu ustalenia tożsamości lub możliwości. Przedstawienie poświadczeń obejmuje przedstawienie danych i potwierdzenie posiadania danych. Usługa WCF obsługuje różne typy poświadczeń zarówno na poziomie zabezpieczeń transportu, jak i komunikatów. Możesz określić typ poświadczenia dla powiązania WCF.  
  
 W wielu krajach lub regionach licencja sterownika jest przykładem poświadczenia. Licencja zawiera dane reprezentujące tożsamość i możliwości. Zawiera dowód posiadania w postaci obrazu posiadacza. Licencja jest wystawiana przez zaufany urząd, zazwyczaj dział licencjonowania dla instytucji rządowych. Licencja jest zapieczętowana i może zawierać hologram, co oznacza, że nie została naruszona ani sfałszowana.  
  
 Przykładowo Rozważmy dwa typy poświadczeń obsługiwane w programie WCF: nazwy użytkownika i (X. 509) poświadczenia certyfikatu.  
  
 W przypadku poświadczenia nazwy użytkownika nazwa użytkownika reprezentuje zażądaną tożsamość, a hasło przedstawia potwierdzenie posiadania. W tym przypadku zaufany urząd sprawdza poprawność nazwy użytkownika i hasła.  
  
 W poświadczeniu o certyfikatach nazwa podmiotu, alternatywna nazwa podmiotu lub określone pola w ramach certyfikatu mogą służyć do reprezentowania zatwierdzono tożsamości i/lub możliwości. Potwierdzenie posiadania danych w poświadczeniem jest ustanawiane przy użyciu skojarzonego klucza prywatnego w celu wygenerowania podpisu.  
  
 Aby uzyskać więcej informacji na temat programowania zabezpieczeń transferu i określania poświadczeń, zobacz [powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md) i [zachowania zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
### <a name="transport-client-credential-types"></a>Typy poświadczeń klienta transportu  
 W poniższej tabeli przedstawiono możliwe wartości używane podczas tworzenia aplikacji, która korzysta z zabezpieczeń transferu. Możesz użyć tych wartości w ustawieniach kodu lub powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Określa, że klient nie musi zaprezentować żadnego poświadczenia. Powoduje to przetłumaczenie na klienta anonimowego.|  
|Podstawowy|Określa podstawowe uwierzytelnianie. Aby uzyskać więcej informacji, zobacz RFC2617, "[uwierzytelnianie http: uwierzytelnianie podstawowe i szyfrowane](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)".|  
|Szyfrowane|Określa uwierzytelnianie szyfrowane. Aby uzyskać więcej informacji, zobacz RFC2617, "[uwierzytelnianie http: uwierzytelnianie podstawowe i szyfrowane](http://schemas.xmlsoap.org/ws/2004/10/discovery/ws-discovery.pdf)".|  
|NTLM|Określa uwierzytelnianie systemu Windows przy użyciu negocjacji interfejsu SSPI w domenie systemu Windows.<br /><br /> W wyniku negocjacji interfejsu SSPI jest używany protokół Kerberos lub serwer NT LanMan (NTLM).|  
|Windows|Określa uwierzytelnianie systemu Windows przy użyciu interfejsu SSPI w domenie systemu Windows. Interfejs SSPI wybiera z protokołu Kerberos lub NTLM jako usługę uwierzytelniania.<br /><br /> Interfejs SSPI najpierw próbuje protokół Kerberos; Jeśli to się nie powiedzie, użyje protokołu NTLM.|  
|Certyfikat|Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu, zazwyczaj X. 509.|  
  
### <a name="message-client-credential-types"></a>Typy poświadczeń klienta wiadomości  
 W poniższej tabeli przedstawiono możliwe wartości używane podczas tworzenia aplikacji, która korzysta z zabezpieczeń komunikatów. Możesz użyć tych wartości w ustawieniach kodu lub powiązania.  
  
|Ustawienie|Opis|  
|-------------|-----------------|  
|Brak|Umożliwia usłudze współpracującie z klientami anonimowymi.|  
|Windows|Zezwala wymianie komunikatów protokołu SOAP w ramach uwierzytelnionego kontekstu poświadczeń systemu Windows. Używa mechanizmu negocjacji interfejsu SSPI do wybrania z protokołu Kerberos lub NTLM jako usługi uwierzytelniania.|  
|Nazwa użytkownika|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu poświadczeń nazwy użytkownika. Należy pamiętać, że WCF nie zezwala na wykonywanie operacji kryptograficznych o nazwie użytkownika, takich jak generowanie podpisu lub szyfrowanie danych. W związku z tym WCF wymusza, aby transport był zabezpieczony przy użyciu poświadczeń nazwy użytkownika.|  
|Certyfikat|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu certyfikatu.|  
|CardSpace|Zezwala usłudze na wymaganie uwierzytelniania klienta przy użyciu programu CardSpace.|  
  
### <a name="programming-credentials"></a>Poświadczenia programowania  
 Dla każdego z typów poświadczeń klienta model programowania WCF pozwala określić wartości poświadczeń i walidacji poświadczeń przy użyciu zachowań usługi i zachowań kanału.  
  
 Zabezpieczenia WCF mają dwa typy poświadczeń: zachowania poświadczeń usługi i zachowania poświadczeń kanału. Zachowania poświadczeń w programie WCF określają rzeczywiste dane, czyli poświadczenia używane do spełnienia wymagań dotyczących zabezpieczeń wyrażonych przez powiązania. W programie WCF Klasa klienta to składnik czasu wykonywania, który konwertuje między wywołaniem i komunikatami operacji. Wszyscy klienci dziedziczą z klasy <xref:System.ServiceModel.ClientBase%601>. Właściwość <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> w klasie bazowej pozwala określić różne wartości poświadczeń klienta.  
  
 W programie WCF zachowania usługi są atrybutami stosowanymi do klasy implementującej kontrakt usługi (interfejs) do programowego sterowania usługą. Klasa <xref:System.ServiceModel.Description.ServiceCredentials> pozwala określić certyfikaty dla poświadczeń usługi i ustawień weryfikacji klienta dla różnych typów poświadczeń klienta.  
  
### <a name="negotiation-model-for-message-security"></a>Model negocjacji dla zabezpieczeń komunikatów  
 Tryb zabezpieczeń wiadomości umożliwia przeprowadzenie zabezpieczenia transferu w taki sposób, aby poświadczenia usługi zostały skonfigurowane na kliencie poza pasmem. Na przykład jeśli używasz certyfikatu przechowywanego w magazynie certyfikatów systemu Windows, musisz użyć narzędzia, takiego jak przystawka programu Microsoft Management Console (MMC).  
  
 Tryb zabezpieczeń wiadomości umożliwia również przeprowadzenie zabezpieczenia transferu, dzięki czemu poświadczenia usługi są wymieniane z klientem w ramach początkowej negocjacji. Aby włączyć negocjowanie, ustaw właściwość <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> na `true`.  
  
## <a name="see-also"></a>Zobacz także

- [Przegląd tworzenia punktów końcowych](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
