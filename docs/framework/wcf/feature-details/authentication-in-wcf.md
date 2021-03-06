---
title: Uwierzytelnianie w programie WCF
description: Poznaj kilka mechanizmów w programie WCF, które zapewniają uwierzytelnianie, takie jak uwierzytelnianie systemu Windows, certyfikaty X. 509 i nazwa użytkownika i hasło.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 4c3348cfb84b8571dc1f24b774ffcd691aaa5001
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247523"
---
# <a name="authentication-in-wcf"></a>Uwierzytelnianie w programie WCF
W poniższych tematach przedstawiono szereg różnych mechanizmów programu Windows Communication Foundation (WCF), które zapewniają uwierzytelnianie, na przykład uwierzytelnianie systemu Windows, certyfikaty X. 509 oraz nazwy użytkownika i hasła.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: użycie dostawcy członkostwa platformy ASP.NET](how-to-use-the-aspnet-membership-provider.md)  
 Funkcje ASP.NET obejmują członkostwo i dostawcę ról, bazę danych do przechowywania par nazw użytkowników i haseł na potrzeby uwierzytelniania oraz role użytkowników na potrzeby autoryzacji. W tym temacie wyjaśniono, w jaki sposób usługi WCF mogą używać tej samej bazy danych do uwierzytelniania i autoryzowania użytkowników.  
  
 [Instrukcje: używanie niestandardowej nazwy użytkownika i modułu weryfikacji hasła](how-to-use-a-custom-user-name-and-password-validator.md)  
 Pokazuje, jak zintegrować niestandardową nazwę użytkownika/moduł sprawdzania poprawności hasła.  
  
 [Uwierzytelnianie i tożsamość usług](service-identity-and-authentication.md)  
 Aby zapewnić dodatkową ochronę, klient może uwierzytelnić usługę, określając oczekiwaną *tożsamość* usługi. Jeśli Oczekiwana tożsamość i tożsamość zwrócona przez usługę nie są zgodne, uwierzytelnianie kończy się niepowodzeniem.  
  
 [Negocjacje i limity czasu dotyczące zabezpieczeń](security-negotiation-and-timeouts.md)  
 Opisuje sposób użycia <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> właściwości w <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> klasie.  
  
 [Debugowanie błędów uwierzytelniania systemu Windows](debugging-windows-authentication-errors.md)  
 Koncentruje się na typowych problemach występujących podczas korzystania z uwierzytelniania systemu Windows.  
  
## <a name="reference"></a>Dokumentacja  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Typowe scenariusze zabezpieczeń](common-security-scenarios.md)  
  
## <a name="see-also"></a>Zobacz też

- [Przegląd zabezpieczeń](security-overview.md)
- [Model zabezpieczeń dla sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
