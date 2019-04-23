---
title: Typowe scenariusze zabezpieczeń
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], scenarios
ms.assetid: 201923b5-5162-4a8a-8d4c-e7bd242748d5
ms.openlocfilehash: af58d6b529fba32380bedb9a892a2b1fd4807d96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199274"
---
# <a name="common-security-scenarios"></a>Typowe scenariusze zabezpieczeń
Tematy w tej sekcji wykazu pewną liczbę możliwych klienta i konfiguracje zabezpieczeń usługi. Konfiguracje różnić w zależności od szeregu czynników. Na przykład czy usługi lub klienta jest w sieci intranet lub tego, czy zabezpieczenia są dostarczane przez Windows lub transportu (np. HTTPS).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Niezabezpieczony klient internetowy i usługa](../../../../docs/framework/wcf/feature-details/internet-unsecured-client-and-service.md)  
 Przykład publicznych, niezabezpieczony klient i usługa.  
  
 [Niezabezpieczony klient i usługa w intranecie](../../../../docs/framework/wcf/feature-details/intranet-unsecured-client-and-service.md)  
 Opracowana podstawowej usługi Windows Communication Foundation (WCF) zawiera informacje na temat bezpiecznego sieci prywatnej dla aplikacji WCF.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem podstawowym](../../../../docs/framework/wcf/feature-details/transport-security-with-basic-authentication.md)  
 Aplikacja umożliwia klientom zalogować się przy użyciu uwierzytelniania niestandardowego.  
  
 [Zabezpieczenia transportu z uwierzytelnianiem systemu Windows](../../../../docs/framework/wcf/feature-details/transport-security-with-windows-authentication.md)  
 Pokazuje, klient i usługa zabezpieczane na Windows.  
  
 [Zabezpieczanie transportu za pomocą anonimowego klienta](../../../../docs/framework/wcf/feature-details/transport-security-with-an-anonymous-client.md)  
 W tym scenariuszu zabezpieczenia transportu (np. HTTPS) w celu zapewnienia poufności i integralności.  
  
 [Zabezpieczanie transportu przy użyciu uwierzytelniania certyfikatów](../../../../docs/framework/wcf/feature-details/transport-security-with-certificate-authentication.md)  
 Pokazuje klientów i usług zabezpieczonych za pomocą certyfikatu.  
  
 [Zabezpieczenia komunikatów z anonimowym klientem](../../../../docs/framework/wcf/feature-details/message-security-with-an-anonymous-client.md)  
 Przedstawia klientów i usług zabezpieczonych przez zabezpieczeń komunikatów WCF.  
  
 [Zabezpieczenia na poziomie komunikatu z użyciem klienta nazwy użytkownika](../../../../docs/framework/wcf/feature-details/message-security-with-a-user-name-client.md)  
 Klient jest aplikacji Windows Forms, która umożliwia klientom zalogować się przy użyciu nazwy użytkownika domeny i hasła.  
  
 [Zabezpieczenia komunikatów z klientem dysponującym certyfikatem](../../../../docs/framework/wcf/feature-details/message-security-with-a-certificate-client.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiany za pośrednictwem negocjowanie zabezpieczeń TLS (Transport Layer).  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client.md)  
 Odmiana certyfikatu klienta. Serwery mają certyfikaty, a każdy klient ma certyfikat. Kontekst zabezpieczeń jest ustanawiane przy użyciu negocjacji protokołu TLS.  
  
 [Zabezpieczanie komunikatów za pomocą klienta systemu Windows bez negocjowania poświadczeń](../../../../docs/framework/wcf/feature-details/message-security-with-a-windows-client-without-credential-negotiation.md)  
 Przedstawia klientów i usług zabezpieczonych przez domenę protokołu Kerberos.  
  
 [Zabezpieczenia komunikatów ze wzajemnymi certyfikatami](../../../../docs/framework/wcf/feature-details/message-security-with-mutual-certificates.md)  
 Serwery mają certyfikaty, a każdy klient ma certyfikat. Certyfikat serwera jest rozpowszechniana z aplikacją i znajduje się poza pasmem.  
  
 [Zabezpieczenia komunikatów z wystawionymi tokenami](../../../../docs/framework/wcf/feature-details/message-security-with-issued-tokens.md)  
 Federacyjnego zabezpieczenia, która umożliwia ustanowienie relacji zaufania między domenami niezależnie od.  
  
 [Zaufany podsystem](../../../../docs/framework/wcf/feature-details/trusted-subsystem.md)  
 Klient uzyskuje dostęp do usług sieci Web, które są rozpowszechniane w sieci. Usługi sieci Web dostęp do dodatkowych zasobów (np. baz danych lub inne usługi sieci Web), które muszą być chronione.  
  
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
- [Model zabezpieczeń dla systemu Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
