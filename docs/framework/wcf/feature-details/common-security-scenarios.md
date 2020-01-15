---
title: Typowe scenariusze zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: 578ec2d7d5abe1285007ad22d8bacd69e695b1d3
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964284"
---
# <a name="common-security-scenarios"></a>Typowe scenariusze zabezpieczeń
Tematy w tej sekcji wykazują wiele możliwych konfiguracji zabezpieczeń klientów i usług. Konfiguracje różnią się w zależności od liczby czynników. Na przykład, czy usługa lub klient znajduje się w intranecie, czy też zabezpieczenia są dostarczane przez system Windows lub transport (na przykład HTTPS).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezabezpieczony klient internetowy i usługa](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Przykład publicznego, niezabezpieczonego klienta i usługi.  
  
 [Niezabezpieczony klient i usługa w intranecie](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Podstawowa usługa Windows Communication Foundation (WCF) opracowana w celu zapewnienia informacji o bezpiecznej sieci prywatnej do aplikacji WCF.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikacja umożliwia klientom logowanie się przy użyciu uwierzytelniania niestandardowego.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem systemu Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Pokazuje klienta i usługę zabezpieczone przez zabezpieczenia systemu Windows.  
  
 [Zabezpieczanie transportu za pomocą anonimowego klienta](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 W tym scenariuszu są stosowane zabezpieczenia transportu (takie jak HTTPS), aby zapewnić poufność i integralność.  
  
 [Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Pokazuje klienta i usługę zabezpieczone przez certyfikat.  
  
 [Zabezpieczenia komunikatów z anonimowym klientem](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Pokazuje klienta i usługę zabezpieczone przez zabezpieczenia komunikatów WCF.  
  
 [Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient jest aplikacją Windows Forms, która umożliwia klientom logowanie się przy użyciu nazwy użytkownika domeny i hasła.  
  
 [Zabezpieczenia komunikatów z klientem dysponującym certyfikatem](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiany za pomocą negocjacji Transport Layer Security (TLS).  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Odmiana klienta certyfikatu. Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiany za pomocą negocjacji TLS.  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Pokazuje klienta i usługę zabezpieczone przez domenę protokołu Kerberos.  
  
 [Zabezpieczenia komunikatów ze wzajemnymi certyfikatami](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Certyfikat serwera jest dystrybuowany z aplikacją i jest dostępny poza pasmem.  
  
 [Zabezpieczenia komunikatów z wystawionymi tokenami](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Zabezpieczenia federacyjne, które umożliwiają ustanowienie zaufania między domenami niezależnymi.  
  
 [Zaufany podsystem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient uzyskuje dostęp do co najmniej jednej usługi sieci Web, która jest dystrybuowana przez sieć. Usługi sieci Web uzyskują dostęp do dodatkowych zasobów (np. baz danych lub innych usług sieci Web), które muszą być zabezpieczone.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Przegląd zabezpieczeń](../../../../docs/framework/wcf/feature-details/security-overview.md)  
  
 [Zabezpieczenia](../../../../docs/framework/wcf/feature-details/security.md)  
  
 [Powiązania i zabezpieczenia](../../../../docs/framework/wcf/feature-details/bindings-and-security.md)  
  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
  
 [Uwierzytelnianie](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
 [Autoryzacja](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md)  
  
 [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
  
 [Inspekcja](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
  
## <a name="see-also"></a>Zobacz także

- [Wytyczne dotyczące zabezpieczeń i najlepsze rozwiązania](../../../../docs/framework/wcf/feature-details/security-guidance-and-best-practices.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
