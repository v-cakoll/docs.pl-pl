---
title: Korzystanie z zabezpieczeń komunikatów
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 70c645101033c31da01d79f624ab03ce328dd3a6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589984"
---
# <a name="securing-messages-using-message-security"></a>Korzystanie z zabezpieczeń komunikatów
W tej części omówiono zabezpieczenia komunikatów WCF podczas korzystania z programu <xref:System.ServiceModel.NetMsmqBinding> .  
  
> [!NOTE]
> Przed przeczytaniem z tego tematu zaleca się zapoznanie się z [pojęciami dotyczącymi zabezpieczeń](security-concepts.md).  
  
 Poniższa ilustracja przedstawia model koncepcyjny komunikacji kolejkowanej przy użyciu programu WCF. Ta ilustracja i terminologia są używane do wyjaśnienia  
  
 zagadnienia dotyczące zabezpieczeń transportu.  
  
 ![Diagram aplikacji znajdujących się w kolejce](media/distributed-queue-figure.jpg "Rozproszona-Queueed-Figure")  
  
 Podczas wysyłania komunikatów umieszczonych w kolejce przy użyciu programu WCF komunikat WCF jest dołączany jako treść komunikatu usługi kolejkowania komunikatów (MSMQ). Chociaż zabezpieczenia transportu zabezpieczają cały komunikat MSMQ, zabezpieczenia komunikatów (lub SOAP) zabezpieczają tylko treść wiadomości MSMQ.  
  
 Najważniejszym pojęciem zabezpieczeń komunikatów jest, że klient zabezpieczy komunikat dla aplikacji odbiorczej (usługi), w przeciwieństwie do zabezpieczeń transportu, gdy klient zabezpieczy komunikat dla kolejki docelowej. W związku z tym usługa MSMQ nie pełni żadnej części podczas zabezpieczania wiadomości WCF przy użyciu zabezpieczeń komunikatów.  
  
 Funkcja zabezpieczenia komunikatów WCF dodaje nagłówki zabezpieczeń do wiadomości WCF, która integruje się z istniejącymi infrastrukturami zabezpieczeń, takimi jak certyfikat lub protokół Kerberos.  
  
## <a name="message-credential-type"></a>Typ poświadczeń wiadomości  
 Korzystając z zabezpieczeń komunikatów, usługa i klient mogą przedstawić poświadczenia do wzajemnego uwierzytelniania. Możesz wybrać opcję Zabezpieczenia komunikatów, ustawiając <xref:System.ServiceModel.NetMsmqBinding.Security%2A> tryb na `Message` lub (to `Both` oznacza, że są używane zabezpieczenia transportu i zabezpieczenia komunikatów).  
  
 Usługa może użyć właściwości, <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> Aby sprawdzić poświadczenie używane do uwierzytelniania klienta. Można go również użyć do dalszej kontroli autoryzacji, którą usługa wybiera do wdrożenia.  
  
 W tej sekcji objaśniono różne typy poświadczeń i sposoby ich używania z kolejkami.  
  
### <a name="certificate"></a>Certyfikat  
 Typ poświadczeń certyfikatu używa certyfikatu X. 509, aby zidentyfikować usługę i klienta.  
  
 W typowym scenariuszu klient i usługa otrzymują prawidłowy certyfikat przez zaufany urząd certyfikacji. Następnie połączenie zostanie nawiązane, a klient uwierzytelnia ważność usługi przy użyciu certyfikatu usługi, aby zdecydować, czy może ufać usłudze. Podobnie usługa używa certyfikatu klienta do sprawdzania poprawności zaufania klienta.  
  
 Ze względu na rozłączoną naturę kolejek, klient i usługa nie mogą być w trybie online w tym samym czasie. W związku z tym klient i usługa muszą wymieniać certyfikaty poza pasmem. W szczególności klient z tytułu posiadania certyfikatu usługi (który może być łańcuchem do urzędu certyfikacji) w swoim zaufanym magazynie, musi ufać, że komunikuje się z poprawną usługą. Aby można było uwierzytelniać klienta, usługa używa certyfikatu X. 509 dołączonego do wiadomości w celu dopasowania go do certyfikatu w magazynie w celu zweryfikowania autentyczności klienta. Ponownie certyfikat musi być łańcuchem do urzędu certyfikacji.  
  
 Na komputerze z systemem Windows certyfikaty są przechowywane w kilku rodzajach magazynów. Aby uzyskać więcej informacji na temat różnych magazynów, zobacz [magazyny certyfikatów](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).  
  
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
  
## <a name="see-also"></a>Zobacz też

- [Ochrona komunikatów za pomocą zabezpieczeń transportu](securing-messages-using-transport-security.md)
- [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../samples/message-security-over-message-queuing.md)
- [Pojęcia dotyczące zabezpieczeń](security-concepts.md)
- [Zabezpieczanie usług i klientów](securing-services-and-clients.md)
