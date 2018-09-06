---
title: Korzystanie z zabezpieczeń komunikatów
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: d895524d36895ad087f7394fcc3380573355eaad
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035947"
---
# <a name="securing-messages-using-message-security"></a>Korzystanie z zabezpieczeń komunikatów
W tej sekcji omówiono zabezpieczenie wiadomości WCF w przypadku korzystania z <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Przed odczytaniem za pośrednictwem tego tematu, zaleca się przeczytanie [pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Następująca ilustracja przedstawia model koncepcyjny umieszczonych w kolejce komunikacji przy użyciu usługi WCF. Ta ilustracja i terminologii służą do wyjaśnienia  
  
 transport pojęcia dotyczące zabezpieczeń.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejka rysunek")  
  
 Podczas wysyłania komunikatów z obsługą kolejek przy użyciu usługi WCF, wiadomości WCF jest dołączony jako treść komunikatu usługi kolejkowania komunikatów (MSMQ). Gdy zabezpieczenia transportu zabezpiecza całą MSMQ wiadomość, komunikat (lub protokołu SOAP) zabezpieczeń zabezpiecza tylko treści wiadomości usługi MSMQ.  
  
 Kluczowe pojęcia zabezpieczeń wiadomości jest, że klient zabezpiecza wiadomości dla aplikacji odbierającej (usługa), w przeciwieństwie do zabezpieczenia transportu, w której klient zabezpiecza komunikat do kolejki docelowej. W efekcie MSMQ odgrywa bez części, gdy zabezpieczenie wiadomości WCF, korzystanie z zabezpieczeń komunikatów.  
  
 Zabezpieczenie wiadomości WCF dodaje nagłówki zabezpieczeń wiadomości WCF, które integrują się z istniejącymi infrastrukturami zabezpieczeń, takie jak certyfikat lub protokołu Kerberos.  
  
## <a name="message-credential-type"></a>Typ poświadczeń komunikatu  
 Korzystanie z zabezpieczeń komunikatów, usługi i klienta może powodować poświadczeń w celu uwierzytelnienia każdego innego. Zabezpieczenia komunikatów można wybrać, ustawiając <xref:System.ServiceModel.NetMsmqBinding.Security%2A> tryb `Message` lub `Both` (oznacza to, użyj zarówno z zabezpieczeń transportu i zabezpieczenia komunikatów).  
  
 Można użyć usługa <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwości, aby sprawdzić poświadczenia używane do uwierzytelniania klienta. To umożliwia także do dalszego sprawdzania autoryzacji, usługa zdecyduje się na implementacji.  
  
 W tej sekcji opisano typy innego poświadczenia i jak z nich korzystać w przypadku kolejek.  
  
### <a name="certificate"></a>Certyfikat  
 Typ poświadczeń certyfikatu używa certyfikatu X.509 do identyfikowania usługi i klienta.  
  
 W typowym scenariuszu, klient i usługa są prawidłowy certyfikat wystawiony przez zaufany urząd certyfikacji. Następnie połączenie zostanie nawiązane, klient uwierzytelnia ważności usługę za pomocą certyfikatu usługi, aby określić, czy można ufać w niej usługi. Podobnie usługa korzysta z certyfikatu klienta można zweryfikować relacji zaufania klienta.  
  
 Ze względu na charakter odłączonego kolejek, klient i usługa może nie być online w tym samym czasie. W efekcie klienta i usługi muszą wymienić certyfikaty poza pasmem. W szczególności klienta, na podstawie zawierający certyfikat usługi, (które można powiązać do urzędu certyfikacji) w magazynie zaufanych muszą ufać, to podczas komunikacji z usługą poprawne. W przypadku uwierzytelniania klienta, używane przez usługę certyfikatu X.509, dołączone do wiadomości pasuje go za pomocą certyfikatu w magazynie w celu sprawdzenia autentyczności klienta. Ponownie certyfikatu muszą być powiązane do urzędu certyfikacji.  
  
 Na komputerze z systemem Windows certyfikaty są przechowywane w różnych typów magazynów. Aby uzyskać więcej informacji na temat różnych sklepach zobacz [magazyny certyfikatów](https://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ poświadczeń komunikatu Windows używa protokołu Kerberos.  
  
 Protokół Kerberos jest mechanizmem zabezpieczeń, który uwierzytelnia użytkowników w domenie i umożliwia uwierzytelnionym użytkownikom ustanowienia bezpiecznego kontekstów z innymi jednostkami w domenie.  
  
 Problem z używaniem protokołu Kerberos do komunikacji z obsługą kolejek są stosunkowo krótkotrwałe biletów, które zawierają tożsamości klienta, który rozdziela Centrum dystrybucji kluczy (KDC). A *okres istnienia* jest skojarzony z biletu protokołu Kerberos, który wskazuje na prawidłowość--ticket. Jako takie biorąc pod uwagę duże opóźnienie, nie można się upewnić, że token jest ciągle ważny dla usługi, która uwierzytelnia klientów.  
  
 Należy pamiętać, że podczas korzystania z tego typu poświadczeń, usługa musi być uruchomiona w ramach konta usługi.  
  
 Protokół Kerberos jest używany domyślnie podczas wybierania poświadczeniami komunikatu. Aby uzyskać więcej informacji, zobacz [Eksplorowanie protokołu Kerberos, protokół rozproszonych zabezpieczeń na platformie Windows 2000](https://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Hasło nazwy użytkownika  
 Używanie tej właściwości, umożliwia uwierzytelnienie klienta na serwerze przy użyciu hasła nazwy użytkownika w nagłówku zabezpieczenia wiadomości.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Klient może używać usługi tokenów zabezpieczeń można wystawić tokenu, który może następnie być dołączony do wiadomości dla usługi do uwierzytelniania klienta.  
  
## <a name="using-transport-and-message-security"></a>Za pomocą transportu i zabezpieczeń komunikatów  
 Korzystając z zabezpieczeń transportu i zabezpieczeń wiadomości, certyfikat używany do zabezpieczenia wiadomości, zarówno na poziomie transportu i protokołu SOAP wiadomości musi być taka sama.  
  
## <a name="see-also"></a>Zobacz też  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
