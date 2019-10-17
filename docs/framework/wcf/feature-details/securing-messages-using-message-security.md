---
title: Korzystanie z zabezpieczeń komunikatów
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 1098057042c0842161258fd081d3ee63e82b4c5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395714"
---
# <a name="securing-messages-using-message-security"></a>Korzystanie z zabezpieczeń komunikatów
W tej części omówiono zabezpieczenia komunikatów WCF podczas korzystania z <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
> Przed przeczytaniem z tego tematu zaleca się zapoznanie się z [pojęciami dotyczącymi zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Poniższa ilustracja przedstawia model koncepcyjny komunikacji kolejkowanej przy użyciu programu WCF. Ta ilustracja i terminologia są używane do wyjaśnienia  
  
 zagadnienia dotyczące zabezpieczeń transportu.  
  
 ![Diagram aplikacji znajdujących się w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Rozproszona-Queueed-Figure")  
  
 Podczas wysyłania komunikatów umieszczonych w kolejce przy użyciu programu WCF komunikat WCF jest dołączany jako treść komunikatu usługi kolejkowania komunikatów (MSMQ). Chociaż zabezpieczenia transportu zabezpieczają cały komunikat MSMQ, zabezpieczenia komunikatów (lub SOAP) zabezpieczają tylko treść wiadomości MSMQ.  
  
 Najważniejszym pojęciem zabezpieczeń komunikatów jest, że klient zabezpieczy komunikat dla aplikacji odbiorczej (usługi), w przeciwieństwie do zabezpieczeń transportu, gdy klient zabezpieczy komunikat dla kolejki docelowej. W związku z tym usługa MSMQ nie pełni żadnej części podczas zabezpieczania wiadomości WCF przy użyciu zabezpieczeń komunikatów.  
  
 Funkcja zabezpieczenia komunikatów WCF dodaje nagłówki zabezpieczeń do wiadomości WCF, która integruje się z istniejącymi infrastrukturami zabezpieczeń, takimi jak certyfikat lub protokół Kerberos.  
  
## <a name="message-credential-type"></a>Typ poświadczeń wiadomości  
 Korzystając z zabezpieczeń komunikatów, usługa i klient mogą przedstawić poświadczenia do wzajemnego uwierzytelniania. Aby wybrać opcję Zabezpieczenia komunikatów, należy ustawić tryb <xref:System.ServiceModel.NetMsmqBinding.Security%2A> na `Message` lub `Both` (to jest użycie zabezpieczeń transport i zabezpieczenia komunikatów).  
  
 Usługa może użyć właściwości <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> do sprawdzenia poświadczeń używanych do uwierzytelniania klienta. Można go również użyć do dalszej kontroli autoryzacji, którą usługa wybiera do wdrożenia.  
  
 W tej sekcji objaśniono różne typy poświadczeń i sposoby ich używania z kolejkami.  
  
### <a name="certificate"></a>Certyfikatu  
 Typ poświadczeń certyfikatu używa certyfikatu X. 509, aby zidentyfikować usługę i klienta.  
  
 W typowym scenariuszu klient i usługa otrzymują prawidłowy certyfikat przez zaufany urząd certyfikacji. Następnie połączenie zostanie nawiązane, a klient uwierzytelnia ważność usługi przy użyciu certyfikatu usługi, aby zdecydować, czy może ufać usłudze. Podobnie usługa używa certyfikatu klienta do sprawdzania poprawności zaufania klienta.  
  
 Ze względu na rozłączoną naturę kolejek, klient i usługa nie mogą być w trybie online w tym samym czasie. W związku z tym klient i usługa muszą wymieniać certyfikaty poza pasmem. W szczególności klient z tytułu posiadania certyfikatu usługi (który może być łańcuchem do urzędu certyfikacji) w swoim zaufanym magazynie, musi ufać, że komunikuje się z poprawną usługą. Aby można było uwierzytelniać klienta, usługa używa certyfikatu X. 509 dołączonego do wiadomości w celu dopasowania go do certyfikatu w magazynie w celu zweryfikowania autentyczności klienta. Ponownie certyfikat musi być łańcuchem do urzędu certyfikacji.  
  
 Na komputerze z systemem Windows certyfikaty są przechowywane w kilku rodzajach magazynów. Aby uzyskać więcej informacji na temat różnych magazynów, zobacz [magazyny certyfikatów](https://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ poświadczeń komunikatu systemu Windows używa protokołu Kerberos.  
  
 Protokół Kerberos jest mechanizmem zabezpieczeń, który uwierzytelnia użytkowników w domenie i zezwala uwierzytelnionym użytkownikom na ustanawianie bezpiecznych kontekstów z innymi jednostkami w domenie.  
  
 Problem z korzystaniem z protokołu Kerberos na potrzeby komunikacji w kolejce polega na tym, że bilety zawierające tożsamość klienta dystrybuowaną przez centrum dystrybucji kluczy (KDC) są stosunkowo krótko. *Okres istnienia* jest skojarzony z biletem protokołu Kerberos, który wskazuje na ważność biletu. W związku z tym duże opóźnienie nie można mieć pewności, że token jest nadal ważny dla usługi, która uwierzytelnia klienta.  
  
 Należy pamiętać, że w przypadku korzystania z tego typu poświadczeń usługa musi być uruchomiona w ramach konta usługi.  
  
 Protokół Kerberos jest używany domyślnie podczas wybierania poświadczeń wiadomości.
  
### <a name="username-password"></a>Hasło użytkownika  
 Korzystając z tej właściwości, klient może uwierzytelniać się na serwerze przy użyciu hasła użytkownika w nagłówku zabezpieczeń wiadomości.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Klient może użyć usługi tokenu zabezpieczającego, aby wystawić token, który następnie może zostać dołączony do wiadomości dla usługi w celu uwierzytelnienia klienta.  
  
## <a name="using-transport-and-message-security"></a>Korzystanie z usługi transport i zabezpieczenia komunikatów  
 W przypadku korzystania z zabezpieczeń transportu i zabezpieczeń komunikatów certyfikat używany do zabezpieczenia komunikatu zarówno w transportie, jak i na poziomie komunikatu protokołu SOAP musi być taki sam.  
  
## <a name="see-also"></a>Zobacz także

- [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
