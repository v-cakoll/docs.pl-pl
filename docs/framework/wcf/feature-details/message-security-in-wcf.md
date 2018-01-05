---
title: "Zabezpieczenia komunikatów w architekturze WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 92422e40742909dbf338ec2660e5494ffcdd31cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="message-security-in-wcf"></a>Zabezpieczenia komunikatów w architekturze WCF
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]ma dwa tryby głównych zabezpieczeń (`Transport` i `Message`) i tryb trzeci (`TransportWithMessageCredential`) łączącą dwa. W tym temacie omówiono zabezpieczeń komunikatów i powodów z niego korzystać.  
  
## <a name="what-is-message-security"></a>Co to jest komunikat zabezpieczeń?  
 Zabezpieczenia komunikatów używa specyfikacji WS-Security do zabezpieczenia wiadomości. WS-Securityspecification opisano ulepszenia protokołu SOAP wiadomości, aby zapewnić poufność, integralność i uwierzytelniania na poziomie komunikatu SOAP (zamiast poziomu transportu).  
  
 Krótko mówiąc zabezpieczenia komunikatów różni się od zabezpieczeń transportu hermetyzując poświadczenia zabezpieczeń i oświadczeń z każdej wiadomości oraz ochrony wiadomości (podpisywania lub szyfrowania). Stosowania zabezpieczeń bezpośrednio do wiadomości, modyfikując jego zawartość pozwala własnym zawierającego względem aspekty zabezpieczeń zabezpieczoną wiadomość. Dzięki temu kilka scenariuszy, które nie są możliwe, gdy używane są zabezpieczenia transportu.  
  
## <a name="reasons-to-use-message-security"></a>Ze względu na korzystanie z zabezpieczeń komunikatów  
 W przypadku zabezpieczenia na poziomie komunikatu wszystkie informacje dotyczące zabezpieczeń jest hermetyzowany w komunikacie. Zabezpieczanie wiadomości z zabezpieczeniami na poziomie wiadomości zamiast zabezpieczenia na poziomie transportu ma następujące zalety:  
  
-   Zabezpieczeń na trasie. Zabezpieczenia transportu, takich jak Secure Sockets Layer (SSL) chroni tylko wiadomości komunikacja punkt-punkt. Jeśli komunikat jest kierowany do jednego lub więcej pośredników SOAP (na przykład router) przed osiągnięciem ultimate odbiornik, wiadomości nie jest chroniony, po pośrednik odczytuje go z sieci. Ponadto informacje o uwierzytelnianiu klienta jest dostępna tylko dla pierwszego pośrednik i muszą zostać ponownie przesłane ultimate odbiorcy w sposób poza pasmem, w razie potrzeby. Dotyczy to również zabezpieczeń SSL między poszczególnych przeskoków używa całego trasy. Zabezpieczenia komunikatów współpracuje bezpośrednio z komunikatu i zabezpiecza XML w nim, dlatego bezpieczeństwo utrzymane komunikat niezależnie od tego, ile pośredników obejmuje przed jego ultimate odbiornika. Dzięki temu scenariusza true zabezpieczeń na trasie.  
  
-   Większa elastyczność. Części wiadomości, a nie cały komunikat może być podpisana lub zaszyfrowana. Oznacza to, że pośredników można wyświetlić części wiadomości, które są przeznaczone dla nich. Jeśli trzeba uwidaczniania część informacji w komunikacie pośredników nadawcy, ale chce mieć pewność, że nie zostanie naruszony, może po prostu podpisz go, ale pozostawić go bez szyfrowania. Ponieważ podpis jest częścią komunikatu, ultimate adresat może sprawdzić nienaruszonej otrzymanie informacje zawarte w wiadomości. Jednym ze scenariuszy może być pośredników SOAP, usługi zgodnie z akcji wartość nagłówka wiadomości trasy. Domyślnie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie szyfruje wartość akcji, ale podpisuje go, jeśli używane są zabezpieczenia wiadomości. Dlatego te informacje są dostępne dla wszystkich pośredników, ale nie można go zmienić.  
  
-   Obsługa wielu transportów. Zabezpieczonych wiadomości można wysyłać na wielu różnych transportów, np. potoków nazwanych i TCP, bez konieczności polegają na protokole zabezpieczeń. Z zabezpieczeniami na poziomie transportu wszystkich informacji o zabezpieczeniach jest zakresem połączenia pojedynczego danego transportu i nie jest dostępna z zawartości wiadomości. Zabezpieczenia komunikatów sprawia, że komunikat bezpiecznego niezależnie od używanego do przesyłania wiadomości i kontekstu zabezpieczeń transportu bezpośrednio jest osadzony w wiadomości.  
  
-   Obsługa wielu różnych poświadczeń i oświadczenia. Zabezpieczenia wiadomości są oparte na specyfikacji WS-Security, który udostępnia rozszerzalną strukturą mogą przenosić dowolny typ oświadczenia wewnątrz komunikatu protokołu SOAP. W przeciwieństwie do zabezpieczenia transportu zestaw mechanizmów uwierzytelniania lub oświadczeń, których można użyć nie jest ograniczone możliwości transportu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zabezpieczenia komunikatów zawiera wiele typów uwierzytelniania i oświadczeń transmisji i może zostać rozszerzony do obsługi dodatkowych typów w razie potrzeby. Z tych powodów na przykład scenariusz poświadczeń federacyjnych nie jest możliwe bez zabezpieczeń wiadomości. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]obsługuje WCF scenariuszach Federacji, zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Porównanie komunikat i zabezpieczeń transportu  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Zalet i wad zabezpieczenia na poziomie transportu  
 Zabezpieczenia transportu ma następujące zalety:  
  
-   Nie wymaga, aby komunikującymi się Stronami pojęciami XML poziom zabezpieczeń. Może to poprawić współdziałanie, na przykład gdy HTTPS jest używany do zabezpieczenia komunikacji.  
  
-   Ogólnie rzecz biorąc lepszą wydajność.  
  
-   Sprzęt akceleratorów są dostępne.  
  
-   Możliwe jest przesyłania strumieniowego.  
  
 Zabezpieczenia transportu ma następujące wady:  
  
-   Przeskoku do-tylko przeskoku.  
  
-   Ograniczona i niewyginający zestaw poświadczeń.  
  
-   Zależne od transportu.  
  
### <a name="disadvantages-of-message-level-security"></a>Wady zabezpieczenia na poziomie komunikatu  
 Zabezpieczenia komunikatów ma następujące wady:  
  
-   Wydajność  
  
-   Nie można użyć strumienia wiadomości.  
  
-   Wymaga wykonania XML poziomie mechanizmy zabezpieczeń i pomocy technicznej dla specyfikacji WS-Security. Może to mieć wpływ na współdziałanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices, rozdział 3: Wdrażanie transportu i komunikat warstwy zabezpieczeń](http://go.microsoft.com/fwlink/?LinkId=88897)
