---
title: Korzystanie z zabezpieczeń komunikatów
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
caps.latest.revision: 16
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 088b01151d0471527bbfc2ffa04b5b5064700081
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="securing-messages-using-message-security"></a>Korzystanie z zabezpieczeń komunikatów
W tej sekcji omówiono [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczenia wiadomości, korzystając z <xref:System.ServiceModel.NetMsmqBinding>.  
  
> [!NOTE]
>  Przed przeczytaniem za pośrednictwem tego tematu, zaleca się przeczytanie [pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md).  
  
 Następująca ilustracja przedstawia model koncepcyjny umieszczonych w kolejce komunikacji przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ta ilustracja i terminologia służą do wyjaśnienia  
  
 transport pojęć związanych z zabezpieczeniami.  
  
 ![Diagram aplikacji w kolejce](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "rozproszonych kolejki — rysunek")  
  
 Podczas wysyłania wiadomości z kolejki przy użyciu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości jest dołączony jako treść komunikatu usługi kolejkowania komunikatów (MSMQ). Gdy zabezpieczeń transportu zabezpiecza cały MSMQ komunikatu, komunikat (lub SOAP) zabezpieczeń tylko zabezpiecza treści wiadomości MSMQ.  
  
 Kluczowe pojęcia zabezpieczenia komunikatów jest, czy klient zabezpiecza wiadomości do aplikacji odbierającej (usługa), w przeciwieństwie do zabezpieczeń transportu, w którym klient zabezpiecza wiadomości do kolejki docelowej. W efekcie MSMQ odgrywa bez części zabezpieczania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości przy użyciu zabezpieczeń wiadomości.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpieczenia komunikatów dodaje nagłówek zabezpieczeń w celu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wiadomości, które integrują się z istniejącej infrastruktury zabezpieczeń, takie jak certyfikat lub protokołu Kerberos.  
  
## <a name="message-credential-type"></a>Typ poświadczeń komunikatu  
 Korzystanie z zabezpieczeń komunikatów, usługa i klient może stanowić poświadczenia umożliwiające uwierzytelnianie w każdym innym. Wybierz opcję zabezpieczenia komunikatów przez ustawienie <xref:System.ServiceModel.NetMsmqBinding.Security%2A> tryb `Message` lub `Both` (oznacza to, używają zarówno zabezpieczeń transportu i zabezpieczenia komunikatów).  
  
 Usługa może wykorzystać <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> właściwości, aby sprawdzić poświadczenia używane do uwierzytelniania klienta. To może być również używany dla dalszego sprawdzeń autoryzacji usługa wybierze do zaimplementowania.  
  
 W tej sekcji opisano typy różnych poświadczeń i sposób ich użycia w przypadku kolejek.  
  
### <a name="certificate"></a>certyfikat  
 Typ poświadczeń certyfikatu używa certyfikatu X.509 do identyfikowania usługi i klienta.  
  
 W typowy scenariusz, klient i usługa są prawidłowy certyfikat wystawiony przez zaufany urząd certyfikacji. Następnie połączenie zostanie nawiązane, klient uwierzytelnia ważności usługi za pomocą certyfikatu usługi można określić, czy można ufać usługi. Podobnie usługa używa certyfikatu klienta można sprawdzić poprawności zaufania klienta.  
  
 Rozłączona charakter kolejek, klient i usługa nie może być online w tym samym czasie. Tak klient i usługa trzeba wymienić certyfikaty poza pasmem. W szczególności klienta, na podstawie przechowywania w magazynie zaufanych certyfikatów usługi, (które można powiązać do urzędu certyfikacji) musi ufać jest podczas komunikacji z usługą poprawne. W celu uwierzytelniania klienta, używane przez usługę certyfikatu X.509, dołączone do wiadomości dopasowuje je przy użyciu certyfikatu w magazynie w celu sprawdzenia autentyczności klienta. Ponownie certyfikat musi być powiązany łańcuchem zależności urzędu certyfikacji.  
  
 Na komputerze z systemem Windows certyfikaty są przechowywane w kilku rodzajów magazynów. Aby uzyskać więcej informacji o różnych magazynach, zobacz [magazyny certyfikatów](http://go.microsoft.com/fwlink/?LinkId=87787).  
  
### <a name="windows"></a>Windows  
 Typ poświadczeń komunikatu systemu Windows używa protokołu Kerberos.  
  
 Protokół Kerberos jest mechanizmem zabezpieczeń uwierzytelnia użytkowników w domenie, który umożliwia uwierzytelnionym użytkownikom ustanowienia bezpiecznego konteksty z innymi osobami w domenie.  
  
 Problem przy użyciu protokołu Kerberos do komunikacji w kolejce to względnie krótkim okresie biletów, które zawierają tożsamości klienta, który rozprowadza Centrum dystrybucji kluczy (KDC). A *okres istnienia* jest skojarzony z bilet Kerberos, który wskazuje ważność biletu. Tak, biorąc pod uwagę duże opóźnienie, możesz nie może być się, że token jest ciągle ważny dla usługi, który uwierzytelnia klientów.  
  
 Należy pamiętać, że gdy przy użyciu tego typu poświadczeń, usługa musi działać na koncie usługi.  
  
 Protokół Kerberos jest używany domyślnie w przypadku wybrania poświadczeniami komunikatu. Aby uzyskać więcej informacji, zobacz [eksploracji protokołu Kerberos, protokół dla rozproszonych zabezpieczeń w systemie Windows 2000](http://go.microsoft.com/fwlink/?LinkId=87790).  
  
### <a name="username-password"></a>Hasło nazwy użytkownika  
 Za pomocą tej właściwości, klient może uwierzytelnić się na serwerze przy użyciu nazwy użytkownika hasła w nagłówku zabezpieczeń wiadomości.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Klient może używać usługi tokenu zabezpieczającego wystawianie tokenów, który można dołączyć do wiadomości dla usługi do uwierzytelniania klienta.  
  
## <a name="using-transport-and-message-security"></a>Przy użyciu transportu i zabezpieczeń komunikatów  
 Podczas korzystania zarówno z zabezpieczeń transportu i zabezpieczeń wiadomości, certyfikat używany do zabezpieczania komunikatów zarówno na poziomie komunikatu protokołu SOAP i transportu muszą być takie same.  
  
## <a name="see-also"></a>Zobacz też  
 [Ochrona komunikatów za pomocą zabezpieczeń transportu](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 [Zabezpieczenia komunikatów w ramach kolejkowania komunikatów](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)  
 [Pojęcia dotyczące zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-concepts.md)  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
