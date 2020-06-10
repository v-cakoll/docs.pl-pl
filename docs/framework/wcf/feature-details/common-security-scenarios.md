---
title: Typowe scenariusze zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: f36ebdb5ea248ec8134c688f89eb5d0be38dfe38
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579739"
---
# <a name="common-security-scenarios"></a>Typowe scenariusze zabezpieczeń
Tematy w tej sekcji wykazują wiele możliwych konfiguracji zabezpieczeń klientów i usług. Konfiguracje różnią się w zależności od liczby czynników. Na przykład, czy usługa lub klient znajduje się w intranecie, czy też zabezpieczenia są dostarczane przez system Windows lub transport (na przykład HTTPS).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezabezpieczony klient internetowy i usługa](internet-unsecured-client-and-service.md)  
 Przykład publicznego, niezabezpieczonego klienta i usługi.  
  
 [Niezabezpieczony klient i usługa w intranecie](intranet-unsecured-client-and-service.md)  
 Podstawowa usługa Windows Communication Foundation (WCF) opracowana w celu zapewnienia informacji o bezpiecznej sieci prywatnej do aplikacji WCF.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](transport-security-with-basic-authentication.md)  
 Aplikacja umożliwia klientom logowanie się przy użyciu uwierzytelniania niestandardowego.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem systemu Windows](transport-security-with-windows-authentication.md)  
 Pokazuje klienta i usługę zabezpieczone przez zabezpieczenia systemu Windows.  
  
 [Zabezpieczanie transportu za pomocą anonimowego klienta](transport-security-with-an-anonymous-client.md)  
 W tym scenariuszu są stosowane zabezpieczenia transportu (takie jak HTTPS), aby zapewnić poufność i integralność.  
  
 [Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów](transport-security-with-certificate-authentication.md)  
 Pokazuje klienta i usługę zabezpieczone przez certyfikat.  
  
 [Zabezpieczenia komunikatów z anonimowym klientem](message-security-with-an-anonymous-client.md)  
 Pokazuje klienta i usługę zabezpieczone przez zabezpieczenia komunikatów WCF.  
  
 [Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika](message-security-with-a-user-name-client.md)  
 Klient jest aplikacją Windows Forms, która umożliwia klientom logowanie się przy użyciu nazwy użytkownika domeny i hasła.  
  
 [Zabezpieczenia komunikatów z klientem dysponującym certyfikatem](message-security-with-a-certificate-client.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiany za pomocą negocjacji Transport Layer Security (TLS).  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](message-security-with-a-windows-client.md)  
 Odmiana klienta certyfikatu. Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiany za pomocą negocjacji TLS.  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń](message-security-with-a-windows-client-without-credential-negotiation.md)  
 Pokazuje klienta i usługę zabezpieczone przez domenę protokołu Kerberos.  
  
 [Zabezpieczenia komunikatów ze wzajemnymi certyfikatami](message-security-with-mutual-certificates.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Certyfikat serwera jest dystrybuowany z aplikacją i jest dostępny poza pasmem.  
  
 [Zabezpieczenia komunikatów z wystawionymi tokenami](message-security-with-issued-tokens.md)  
 Zabezpieczenia federacyjne, które umożliwiają ustanowienie zaufania między domenami niezależnymi.  
  
 [Zaufany podsystem](trusted-subsystem.md)  
 Klient uzyskuje dostęp do co najmniej jednej usługi sieci Web, która jest dystrybuowana przez sieć. Usługi sieci Web uzyskują dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web), które muszą być zabezpieczone.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Autoryzacja](authorization-in-wcf.md)  
  
 [Przegląd zabezpieczeń](security-overview.md)  
  
 [Bezpieczeństwo](security.md)  
  
 [Wiązania i zabezpieczenia](bindings-and-security.md)  
  
 [Zabezpieczanie usług i klientów](securing-services-and-clients.md)  
  
 [Authentication](authentication-in-wcf.md)  
  
 [Autoryzacja](authorization-in-wcf.md)  
  
 [Federacja i wystawione tokeny](federation-and-issued-tokens.md)  
  
 [Inspekcja](auditing-security-events.md)  
  
## <a name="see-also"></a>Zobacz też

- [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](security-guidance-and-best-practices.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
