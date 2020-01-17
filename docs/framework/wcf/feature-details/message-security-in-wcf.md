---
title: Zabezpieczenia komunikatów w architekturze WCF
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: 32f6659f6ac744ab7af07c23e7e26ea1124d020c
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212071"
---
# <a name="message-security-in-wcf"></a>Zabezpieczenia komunikatów w architekturze WCF

Windows Communication Foundation (WCF) ma dwa główne tryby zapewniania bezpieczeństwa (`Transport` i `Message`) oraz trzeci tryb (`TransportWithMessageCredential`) łączący te dwa. W tym temacie omówiono zabezpieczenia komunikatów i przyczyny ich użycia.

## <a name="what-is-message-security"></a>Co to jest zabezpieczenia komunikatów?

Zabezpieczenia komunikatów używają specyfikacji WS-Security do zabezpieczania komunikatów. Specyfikacja WS-Security opisuje usprawnienia funkcji SOAP Messaging, aby zapewnić poufność, integralność i uwierzytelnianie na poziomie komunikatów SOAP (zamiast na poziomie transportu).

W skrócie zabezpieczenia komunikatów różnią się od zabezpieczeń transportu poprzez Hermetyzowanie poświadczeń zabezpieczeń i oświadczeń z każdym komunikatem oraz wszelkimi ochroną komunikatów (podpisywania lub szyfrowania). Zastosowanie zabezpieczeń bezpośrednio do wiadomości przez zmodyfikowanie jej zawartości pozwala na samodzielne wiadomości, w odniesieniu do aspektów zabezpieczeń. Pozwala to na niektóre scenariusze, które nie są możliwe, gdy używane są zabezpieczenia transportu.

## <a name="reasons-to-use-message-security"></a>Przyczyny używania zabezpieczeń komunikatów

W zabezpieczeniach na poziomie komunikatów wszystkie informacje o zabezpieczeniach są hermetyzowane w wiadomości. Zabezpieczenie wiadomości z zabezpieczeniami na poziomie wiadomości zamiast zabezpieczeń na poziomie transportu ma następujące zalety:

- Kompleksowe zabezpieczenia. Zabezpieczenia transportu, takie jak SSL (SSL), chronią tylko komunikaty, gdy komunikacja jest punktem-punkt. Jeśli komunikat jest kierowany do co najmniej jednego wystawcy protokołu SOAP (na przykład routera) przed osiągnięciem odbiorcy końcowego, sam komunikat nie jest chroniony po odczytaniu przez niego pośrednika z sieci. Ponadto informacje o uwierzytelnianiu klienta są dostępne tylko dla pierwszej pośrednika i muszą zostać ponownie przesłane do odbiorcy końcowego w sposób, w razie potrzeby. Ma to zastosowanie, nawet jeśli cała trasa używa zabezpieczeń SSL między indywidualnymi przeskokami. Ze względu na to, że zabezpieczenia komunikatów działają bezpośrednio wraz z wiadomością i zabezpieczają w niej kod XML, zabezpieczenia pozostają z komunikatem bez względu na liczbę pośredników, które są wykorzystywane przed docieraniem do ostatecznego odbiorcy. Umożliwia to kompleksowe scenariusze zabezpieczeń.

- Większa elastyczność. Część komunikatu, a nie cały komunikat, może być podpisana lub zaszyfrowana. Oznacza to, że pośrednicy mogą przeglądać części wiadomości, które są przeznaczone dla nich. Jeśli nadawca musi udostępnić część informacji w komunikacie widocznym dla pośredników, ale chce mieć pewność, że nie jest ona naruszona, może po prostu podpisać ją, ale pozostawić ją niezaszyfrowaną. Ponieważ podpis jest częścią komunikatu, odbiorca końcowy może sprawdzić, czy informacje w wiadomości zostały odebrane bez zmian. Jeden scenariusz może mieć usługę pośredniczącą protokołu SOAP, która kieruje komunikat zgodnie z wartością nagłówka akcji. Domyślnie usługa WCF nie szyfruje wartości akcji, ale podpisuje ją, jeśli jest używana funkcja zabezpieczenia komunikatów. W związku z tym te informacje są dostępne dla wszystkich pośredników, ale nikt nie może go zmienić.

- Obsługa wielu transportów. Można wysyłać zabezpieczone komunikaty za pośrednictwem wielu różnych transportów, takich jak potoki nazwane i TCP, bez konieczności polegania na protokole zabezpieczeń. W przypadku zabezpieczeń na poziomie transportu wszystkie informacje o zabezpieczeniach są ograniczone do jednego konkretnego połączenia transportowego i nie są dostępne w samej zawartości wiadomości. Zabezpieczenia komunikatów zabezpieczają komunikat niezależnie od tego, jaki transport jest używany do przesyłania wiadomości, a kontekst zabezpieczeń jest bezpośrednio osadzony w komunikacie.

- Obsługa szerokiego zestawu poświadczeń i oświadczeń. Zabezpieczenia komunikatów opierają się na specyfikacji WS-Security, która zapewnia rozszerzalną platformę, która umożliwia przekazywanie dowolnego typu roszczeń wewnątrz komunikatu protokołu SOAP. W przeciwieństwie do zabezpieczeń transportu, zestaw mechanizmów uwierzytelniania lub oświadczeń, których można użyć, nie jest ograniczony przez możliwości transportu. Zabezpieczenia komunikatów WCF obejmują wiele typów uwierzytelniania i transmisji, które mogą być rozszerzane w celu obsługi dodatkowych typów w razie potrzeby. Z tego względu scenariusz poświadczeń federacyjnych nie jest możliwy bez zabezpieczeń wiadomości. Aby uzyskać więcej informacji na temat scenariuszy federacyjnych obsługiwanych przez WCF, zobacz [federacyjne i wystawione tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).

## <a name="how-message-and-transport-security-compare"></a>Jak porównać zabezpieczenia komunikatów i transportu

### <a name="pros-and-cons-of-transport-level-security"></a>Specjaliści i wady zabezpieczeń na poziomie transportu

Zabezpieczenia transportu mają następujące zalety:

- Nie wymaga, aby strony komunikują się zrozumieć koncepcje zabezpieczeń na poziomie XML. Może to poprawić współdziałanie, na przykład podczas zabezpieczania komunikacji przy użyciu protokołu HTTPS.

- Ogólnie zwiększona wydajność.

- Akceleratory sprzętu są dostępne.

- Przesyłanie strumieniowe jest możliwe.

 Zabezpieczenia transportu mają następujące wady:

- Tylko przeskok do przeskoku.

- Ograniczony i nierozszerzalny zestaw poświadczeń.

- Zależne od transportu.

### <a name="disadvantages-of-message-level-security"></a>Wady zabezpieczeń na poziomie komunikatów

Zabezpieczenia komunikatów mają następujące wady:

- Wydajność

- Nie można użyć strumieniowego przesyłania komunikatów.

- Wymaga implementacji mechanizmów zabezpieczeń na poziomie XML i obsługi specyfikacji WS-Security. Może to mieć wpływ na współdziałanie.

## <a name="see-also"></a>Zobacz także

- [Zabezpieczanie usług i klientów](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Zabezpieczenia transportu](../../../../docs/framework/wcf/feature-details/transport-security.md)
- [Instrukcje: korzystanie z zabezpieczeń transportu i poświadczeń komunikatów](../../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [Wzorce i praktyki firmy Microsoft, rozdział 3: implementowanie transportu i zabezpieczenia warstwy komunikatów](https://docs.microsoft.com/previous-versions/msp-n-p/ff647370(v=pandp.10))
