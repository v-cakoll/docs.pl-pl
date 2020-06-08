---
title: Adresowanie IPv6
description: Informacje na temat protokołu internetowego w wersji 6 (IPv6), adresy, w tym Reprezentacja tekstowa i typy adresów.
ms.date: 03/30/2017
helpviewer_keywords:
- Internet Protocol version 6, addresses in
- Neighbor Discovery
- IPv6, enabling
- IPv6, mobility and
- Internet Protocol version 6, anycast addresses
- IPv6, Neighbor Discovery
- Internet Protocol version 6, auto-configuring
- Internet Protocol version 6, enabling
- IPv6, unicast addresses
- IPv6, auto-configuring
- Internet Protocol version 6, routing
- IPv6, RFC documents
- IPv6, routing
- Internet Protocol version 6, disabling
- Internet Protocol version 6, unicast addresses
- IPv6, multicast addresses
- Internet Protocol version 6, mobility and
- Internet Protocol version 6, RFC documents
- Internet Protocol version 6, Neighbor Discovery
- IPv6, anycast addresses
- Internet Protocol version 6, multicast addresses
- IPv6, addresses in
- IPv6, disabling
ms.assetid: 20a104ae-1649-4649-a005-531a5cf74c93
ms.openlocfilehash: fbf68cb5f40450c2f9ecf4900801ee55e326fcb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502343"
---
# <a name="ipv6-addressing"></a>Adresowanie IPv6

W przypadku protokołu internetowego w wersji 6 (IPv6) adresy mają długość 128 bitów. Jedną z przyczyn takiej dużej przestrzeni adresowej jest podział dostępnych adresów w hierarchię domen routingu, które odzwierciedlają topologię internetową. Kolejną przyczyną jest zamapowanie adresów kart sieciowych (lub interfejsów), które łączą urządzenia z siecią. Protokół IPv6 oferuje nieodłączną możliwość rozpoznawania adresów na ich najniższym poziomie, które znajdują się na poziomie interfejsu sieciowego, a także udostępnia funkcje automatycznej konfiguracji.

## <a name="text-representation"></a>Reprezentacja tekstu

Poniżej przedstawiono trzy konwencjonalne formularze używane do reprezentowania adresów IPv6 jako ciągi tekstowe:

- **Dwukropek — forma szesnastkowa**. Jest to preferowana postać n:n: n:n: n:n: n:n. Każdy n reprezentuje wartość szesnastkową jednego z 8 16-bitowych elementów adresu. Na przykład: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Forma skompresowana**. Ze względu na długość adresu często istnieją adresy zawierające długi ciąg zer. Aby uprościć Zapisywanie tych adresów, użyj skompresowanego formularza, w którym jedna ciągła sekwencja bloków jest reprezentowana przez symbol dwukropka (::). Ten symbol może wystąpić tylko raz w adresie. Na przykład adres multiemisji `FFED:0:0:0:0:BA98:3210:4562` w postaci skompresowanej to `FFED::BA98:3210:4562` . Adres emisji pojedynczej `3FFE:FFFF:0:0:8:800:20C4:0` w postaci skompresowanej to `3FFE:FFFF::8:800:20C4:0` . Adres sprzężenia zwrotnego `0:0:0:0:0:0:0:1` w postaci skompresowanej wynosi `::` 1. Nieokreślony adres `0:0:0:0:0:0:0:0` w postaci skompresowanej to `::` .

- **Formularz mieszany**. Ten formularz łączy adresy IPv4 i IPv6. W tym przypadku format adresu to n:n: n:n: n:n: d. d. d. d, gdzie każda n reprezentuje wartości szesnastkowe z sześciu elementów 16-bitowych o dużej kolejności IPv6, a każda d reprezentuje wartość dziesiętną adresu IPv4.

## <a name="address-types"></a>Typy adresów

Wiodące bity w adresie definiują konkretny typ adresu IPv6. Pole o zmiennej długości zawierające te wiodące bity nosi nazwę prefiksu formatu (FP).

Adres IPv6 emisji pojedynczej jest podzielony na dwie części. Pierwsza część zawiera prefiks adresu, a druga część zawiera identyfikator interfejsu. Zwięzły sposób wyrażenia kombinacji adresu IPv6/prefiksu jest następujący: IPv6-Address/prefix-length.

Poniżej znajduje się przykład adresu z prefiksem 64-bitowym.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Prefiks w tym przykładzie to `3FFE:FFFF:0:CD30` . Adres może być również zapisany w postaci skompresowanej, tak jak `3FFE:FFFF:0:CD30::/64` .

Protokół IPv6 definiuje następujące typy adresów:

- **Adres emisji pojedynczej**. Identyfikator jednego interfejsu. Pakiet wysłany do tego adresu jest dostarczany do zidentyfikowanego interfejsu. Adresy emisji pojedynczej są rozróżniane na podstawie adresów multiemisji przez wartość oktetu o dużej kolejności. Oktet o wysokim poziomie adresów multiemisji ma wartość szesnastkową FF. Wszystkie inne wartości dla tego oktetu identyfikują adres emisji pojedynczej. Poniżej wymieniono różne typy adresów emisji pojedynczej:

  - **Adresy lokalne łącza**. Te adresy są używane na jednym łączu i mają następujący format: FE80::*InterfaceID*. Adresy lokalne linków są używane między węzłami w linku do konfiguracji autoadres, odnajdywania sąsiadów lub gdy nie są obecne żadne routery. Adres lokalny łącza jest używany głównie podczas uruchamiania, a system nie uzyskał jeszcze adresów większych zakresów.

  - **Adresy lokalne lokacji**. Te adresy są używane w jednej lokacji i mają następujący format: FEC0::*SubnetID*:*InterfaceID*. Adresy lokalne lokacji są używane do adresowania wewnątrz lokacji bez konieczności stosowania prefiksu globalnego.

  - **Adresy globalne IPv6 emisji pojedynczej**. Te adresy mogą być używane przez Internet i mają następujący format: 010 (FP, 3 bity) TLA identyfikator (13 bitów) zarezerwowany (8 bitów) identyfikator NLA (24 bity) (16 bitów) *InterfaceID* (64 bitów).

- **Adres multiemisji**. Identyfikator zestawu interfejsów (zwykle należący do różnych węzłów). Pakiet wysłany do tego adresu jest dostarczany do wszystkich interfejsów identyfikowanych przez adres. Typy adresów multiemisji zastępują adresy emisji IPv4.

- **Adres emisji**. Identyfikator zestawu interfejsów (zwykle należący do różnych węzłów). Pakiet wysłany do tego adresu jest dostarczany tylko do jednego interfejsu identyfikowanego przez adres. Jest to najbliższy interfejs identyfikowany przez metryki routingu. Adresy emisji dowolnej są pobierane z przestrzeni adresowej emisji pojedynczej i nie są syntaktycznie odróżniane. Interfejs rozłożony wykonuje rozróżnienie między adresami emisji pojedynczej i emisji.

Ogólnie rzecz biorąc, węzeł zawsze ma adres lokalny łącza. Może być adresem lokalnym lokacji i co najmniej jednym adresem globalnym.

## <a name="see-also"></a>Zobacz także

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
