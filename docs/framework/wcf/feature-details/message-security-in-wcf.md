---
title: Zabezpieczenia komunikatów w architekturze WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 81d9acde3c8fab1860904074199066cca55c7186
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43724503"
---
# <a name="message-security-in-wcf"></a>Zabezpieczenia komunikatów w architekturze WCF
Windows Communication Foundation (WCF) ma dwa główne tryby zapewnianie bezpieczeństwa (`Transport` i `Message`) i trzeci trybu (`TransportWithMessageCredential`) który łączy dwie. W tym temacie omówiono zabezpieczenia komunikatów i przyczyny, które z niej korzystać.  
  
## <a name="what-is-message-security"></a>Zabezpieczenia komunikatów co to jest?  
 Zabezpieczenia komunikatów używa specyfikacji WS-Security do zabezpieczenia wiadomości. WS-Securityspecification opis ulepszeń protokołu SOAP wiadomości, aby zapewnić poufność, integralność i uwierzytelnianie na poziomie komunikatu protokołu SOAP (zamiast poziom transportu).  
  
 Krótko mówiąc zabezpieczenia komunikatów różni się od zabezpieczeń transportu zawierający poświadczenia zabezpieczeń i oświadczenia, za pomocą każdy komunikat i odtworzy żadnej ochrony wiadomości (podpisywanie lub szyfrowanie). Stosowanie zabezpieczeń bezpośrednio na tę wiadomość, modyfikując jego zawartość pozwala samodzielnie zawierające odniesieniu aspekty zabezpieczeń zabezpieczoną wiadomość. Dzięki temu kilka scenariuszy, które nie są możliwe, gdy jest używany z zabezpieczeń transportu.  
  
## <a name="reasons-to-use-message-security"></a>Powody korzystania z zabezpieczeń komunikatów  
 W zabezpieczenia na poziomie komunikatu wszystkie informacje o zabezpieczeniach są hermetyzowane w komunikacie. Zabezpieczanie komunikatów za pomocą zabezpieczeń na poziomie komunikatu zamiast zabezpieczenia na poziomie transportu ma następujące zalety:  
  
-   Zabezpieczenia end-to-end. Zabezpieczenia transportu, takich jak Secure Sockets Layer (SSL) tylko zabezpiecza wiadomości, komunikacja punkt-punkt. Jeśli komunikat jest kierowany do jednego lub kilku pośredników SOAP (na przykład router) przed osiągnięciem ultimate odbiorcy, wiadomości nie jest chroniony, po pośrednik odczyta go z sieci. Ponadto informacje dotyczące uwierzytelniania klienta jest dostępna tylko dla pierwszego pośrednika i musi zostać ponownie przekazana ultimate odbiorcy w sposób poza pasmem, jeśli to konieczne. Ma to zastosowanie, nawet jeśli trasy całego używa zabezpieczeń protokołu SSL między poszczególnych przeskoków. Zabezpieczenia komunikatów współpracuje bezpośrednio z komunikatem i zabezpiecza XML w nim, dlatego bezpieczeństwo pozostaje komunikatem niezależnie od tego, ile pośredników zaangażowanych przed osiągnięciem przez nią ultimate odbiorcy. Dzięki temu scenariusz true zabezpieczeń end-to-end.  
  
-   Większa elastyczność. Części wiadomości, a nie cały komunikat może być podpisana lub zaszyfrowana. Oznacza to, że pośredników można wyświetlić części wiadomości, które są przeznaczone dla nich. Jeśli nadawca wymaga uwidocznić część informacji w komunikacie pośredników, ale chce mieć pewność, że nie zostanie naruszony, jest to możliwe po prostu podpisać go, ale pozostawić ją bez szyfrowania. Ponieważ podpis jest część komunikatu, ultimate adresat może sprawdzić, czy opublikowane Odebrano informacje w wiadomości. Jeden scenariusz może być pośrednik protokołu SOAP, usługi tego komunikatu trasy, zgodnie z akcji wartość nagłówka. Domyślnie usługi WCF nie szyfruje wartość akcji, ale podpisuje go, jeśli używane są zabezpieczenia wiadomości. Dlatego te informacje są dostępne dla wszystkich pośredników, ale nie można go zmienić.  
  
-   Obsługa wielu transportów. Możesz wysłać zabezpieczonych wiadomości na wiele różnych protokołów transportowych, takich jak nazwane potoki i TCP, bez konieczności opierają się na protokole zabezpieczeń. Z zabezpieczeniami na poziomie transportu wszystkie informacje o zabezpieczeniach jest ograniczone do pojedynczego danego transportu połączenia i nie jest dostępna z samej zawartości komunikatu. Zabezpieczenia komunikatów sprawia, że wiadomość jest bezpieczne, niezależnie od używanego do przesyłania wiadomości i kontekst zabezpieczeń transportu bezpośrednio jest osadzony w wiadomości.  
  
-   Obsługa szerokiego zestawu poświadczeń i oświadczeń. Zabezpieczenia komunikatów jest oparty na specyfikacji WS-Security udostępnia rozszerzalną strukturą mogą przenosić dowolnego typu oświadczenia wewnątrz komunikatu protokołu SOAP. W przeciwieństwie do zabezpieczenia transportu zestaw mechanizmów uwierzytelniania lub oświadczeń, których można użyć nie jest ograniczone możliwości transportu. Zabezpieczenie wiadomości WCF zawiera wiele typów uwierzytelniania i oświadczenia transmisji i można rozszerzyć do obsługi dodatkowych typów zgodnie z potrzebami. Z tych powodów na przykład scenariusz poświadczeń federacyjnych nie jest możliwe bez zabezpieczeń wiadomości. Aby uzyskać więcej informacji na temat obsługuje WCF scenariuszach Federacji zobacz [Federacja i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="how-message-and-transport-security-compare"></a>Porównanie wiadomości i zabezpieczeń transportu  
  
### <a name="pros-and-cons-of-transport-level-security"></a>Zalety i wady zabezpieczeń na poziomie transportu  
 Zabezpieczenia transportu ma następujące zalety:  
  
-   Nie jest wymagane, czy strony komunikujące się zrozumienie pojęcia dotyczące zabezpieczeń poziomie XML. Może to poprawić współdziałania, na przykład, gdy HTTPS jest używany do zabezpieczenia komunikacji.  
  
-   Ogólnie lepszą wydajność.  
  
-   Akceleratory sprzętowe są dostępne.  
  
-   Możliwe jest przesyłanie strumieniowe.  
  
 Zabezpieczenia transportu ma następujące wady:  
  
-   Przeskoku do-tylko przeskoku.  
  
-   Ograniczone i niewyginający zestawu poświadczeń.  
  
-   Zależne od transportu.  
  
### <a name="disadvantages-of-message-level-security"></a>Wady zabezpieczeń na poziomie komunikatu  
 Zabezpieczenia komunikatów ma następujące wady:  
  
-   Wydajność  
  
-   Nie można użyć komunikatów przesyłania strumieniowego.  
  
-   Wymaga stosowania mechanizmów zabezpieczeń poziomie XML i pomoc techniczna dla specyfikacji WS-Security. Może to mieć wpływ na współdziałanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)  
 [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)  
 [Microsoft Patterns and Practices, rozdział 3: Implementowanie transportu i komunikat warstwy zabezpieczeń](https://go.microsoft.com/fwlink/?LinkId=88897)
