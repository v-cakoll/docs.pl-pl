---
title: Rozszerzanie architektury WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795536"
---
# <a name="extending-wcf"></a>Rozszerzanie architektury WCF
Windows Communication Foundation (WCF) pozwala modyfikować i zwiększać składniki czasu wykonywania w celu precyzyjnego kontrolowania i rozbudowania aplikacji opartych na usługach. W tematach w tej sekcji opisano architekturę rozszerzalności. Aby uzyskać więcej informacji na temat programowania podstawowego, zobacz [podstawowe programowanie WCF](../basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Rozszerzanie elementu ServiceHost i warstwy modelu usług](extending-servicehost-and-the-service-model-layer.md)  
 Warstwa modelu usług jest odpowiedzialna za ściąganie komunikatów przychodzących z kanałów, tłumaczenie ich na wywołania metod w kodzie aplikacji i wysyłanie wyników z powrotem do obiektu wywołującego.  Rozszerzenia modelu usług modyfikują lub implementują działania związane z wykonywaniem lub komunikacją, a także funkcje, w tym funkcje dyspozytora, niestandardowe zachowania, komunikat i przechwycenie parametru oraz inne funkcje rozszerzalności.  
  
 [Rozszerzanie powiązań](extending-bindings.md)  
 Powiązania są obiektami, które opisują szczegóły komunikacji wymagane do nawiązania połączenia z punktem końcowym. Rozszerzenia powiązań lub powiązania niestandardowe implementują funkcję komunikacji niestandardowej, która jest wymagana do obsługi funkcji aplikacji.  
  
 [Rozszerzanie warstwy kanału](extending-the-channel-layer.md)  
 Warstwa kanału znajduje się poniżej warstwy modelu usług i jest odpowiedzialna za wymianę komunikatów między klientami i usługami. Rozszerzenia kanału mogą implementować nowe funkcje protokołu, takie jak zabezpieczenia. Rozszerzenia kanału umożliwiają również transport funkcji, takich jak implementacja nowego transportu sieciowego do przenoszenia komunikatów protokołu SOAP.  
  
 [Rozszerzanie zabezpieczeń](extending-security.md)  
 Zabezpieczenia w programie WCF obejmują zabezpieczenia transferu (integralność, poufność i uwierzytelnianie), kontrolę dostępu (autoryzacja) i inspekcję. Klasy Znalezione w `IdentityModel` przestrzeni nazw są używane przez funkcję WCF do kontroli dostępu. Zrozumienie architektury zabezpieczeń umożliwia tworzenie niestandardowych typów zgłoszeń w celu uwzględnienia niestandardowych systemów kontroli dostępu.  
  
 [Rozszerzanie systemu metadanych](extending-the-metadata-system.md)  
 System metadanych WCF jest grupą klas i interfejsów, które reprezentują metadane wymagane do implementowania aplikacji opartych na usługach. Modyfikuj lub rozszerzaj klasy albo Implementuj i Konfiguruj interfejsy do eksportowania i importowania niestandardowych metadanych, takich jak rozszerzenia Web Services Description Language (WSDL) lub niestandardowe potwierdzenia WS-PolicyAttachments.  
  
 [Rozszerzanie koderów i serializatorów](extending-encoders-and-serializers.md)  
 Kodery i serializatory tłumaczą dane z jednej postaci na inną. W tematach w tej sekcji omówiono, jak zwiększyć liczbę dostarczonych klas w celu spełnienia specjalnych wymagań.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Podstawy programowania przy użyciu programu WCF](../basic-wcf-programming.md)  
  
 [Szczegóły funkcji WCF](../feature-details/index.md)  
  
 [Wskazówki i najlepsze rozwiązania](../guidelines-and-best-practices.md)
