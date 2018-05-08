---
title: Współdziałanie z aplikacjami COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: 292892ef572bd63fff055aeed88073573fadb934
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="integrating-with-com-applications"></a>Współdziałanie z aplikacjami COM
Usługi Windows Communication Foundation (WCF) można zintegrować bezpośrednio do istniejącego kodu za pomocą moniker usługi WCF. Krótka nazwa usługi może służyć w środowiskach programistycznych szeroki zakres modelu COM opartych, na przykład VBA pakietu Office, Visual Basic 6.0 lub Visual C++ 6.0.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Przegląd integrowania z aplikacjami COM](../../../../docs/framework/wcf/feature-details/integrating-with-com-applications-overview.md)  
 Zawiera omówienie głównych części procesu integracji.  
  
 [Instrukcje: rejestrowanie i konfigurowanie monikera usługi](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)  
 Aby użyć moniker usługi WCF w ramach aplikacji modelu COM, należy zarejestrować wymagane typy oparte na atrybutach w modelu COM i skonfigurować aplikacji modelu COM i krótka nazwa za pomocą konfiguracji powiązania wymagany.  
  
 [Instrukcje: używanie monikera programu Windows Communication Foundation bez rejestracji](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)  
 Wyjaśniono, jak uzyskać definicję kontraktu w formie dokumentu sieci Web Services Definition Language (WSDL) lub z punktu końcowego usługi WS-MetadataExchange.  
  
 [Instrukcje: używanie krótkiej nazwy z kontraktami WSDL](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 Opisuje sposób wywołania próbkę WCF za pomocą moniker WCF WSDL.  
  
 [Instrukcje: używanie krótkiej nazwy z kontraktami wymiany metadanych](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Opisuje sposób wywołania próbkę WCF za pomocą usługi WCF krótkiej nazwy, która określa punkt końcowy Mex.  
  
 [Instrukcje: określanie poświadczeń zabezpieczeń kanału](../../../../docs/framework/wcf/feature-details/how-to-specify-channel-security-credentials.md)  
 Obsługuje moniker usługi WCF `IChannelCredentials` interfejs, umożliwiający szereg alternatywnych metod dotyczących określania poświadczeń kanału.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie z aplikacjami COM+](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
