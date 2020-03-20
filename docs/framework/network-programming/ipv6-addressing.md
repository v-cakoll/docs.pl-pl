---
title: Adresowanie IPv6
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
ms.openlocfilehash: 1bad43b96fc6f66724e5e40cdf0ae6d76b46d867
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047853"
---
# <a name="ipv6-addressing"></a>Adresowanie IPv6

W protokole internetowym w wersji 6 (IPv6) adresy mają 128 bitów długości. Jedną z przyczyn tak dużej przestrzeni adresowej jest podzielenie dostępnych adresów na hierarchię domen routingu, które odzwierciedlają topologię Internetu. Innym powodem jest mapowanie adresów kart sieciowych (lub interfejsów), które łączą urządzenia z siecią. IPv6 oferuje nieodłączną możliwość rozpoznawania adresów na najniższym poziomie, który znajduje się na poziomie interfejsu sieciowego, a także ma możliwości automatycznej konfiguracji.

## <a name="text-representation"></a>Reprezentacja tekstu

Poniżej przedstawiono trzy konwencjonalne formularze używane do reprezentowania adresów IPv6 jako ciągi tekstowe:

- **Postać dwukropek-szesnastkowa**. This is the preferred form n:n:n:n:n:n:n:n. Każdy n reprezentuje wartość szesnastową jednego z ośmiu 16-bitowych elementów adresu. Na przykład: `3FFE:FFFF:7654:FEDA:1245:BA98:3210:4562`.

- **Skompresowana forma**. Ze względu na długość adresu jest wspólne, aby mieć adresy zawierające długi ciąg zer. Aby uprościć zapisywanie tych adresów, należy użyć skompresowanej formy, w której pojedyncza ciągła sekwencja 0 bloków jest reprezentowana przez symbol podwójnego dwukropeku (::). Ten symbol może pojawić się tylko raz w adresie. Na przykład adres multiemisji `FFED:0:0:0:0:BA98:3210:4562` w `FFED::BA98:3210:4562`formie skompresowanej jest . Adres `3FFE:FFFF:0:0:8:800:20C4:0` emisji pojedynczej w `3FFE:FFFF::8:800:20C4:0`skompresowanej formie to . Adres `0:0:0:0:0:0:0:1` sprzężenia zwrotnego `::`w postaci skompresowanej wynosi 1. Nieokreślony adres `0:0:0:0:0:0:0:0` w skompresowanej `::`formie to .

- **Forma mieszana**. Ten formularz łączy adresy IPv4 i IPv6. In this case, the address format is n:n:n:n:n:n:d.d.d.d, where each n represents the hexadecimal values of the six IPv6 high-order 16-bit address elements, and each d represents the decimal value of an IPv4 address.

## <a name="address-types"></a>Typy adresów

Bity wiodące w adresie definiują określony typ adresu IPv6. Pole o zmiennej długości zawierające te bity wiodące jest nazywane prefiksem formatu (FP).

Adres emisji pojedynczej IPv6 jest podzielony na dwie części. Pierwsza część zawiera prefiks adresu, a druga część zawiera identyfikator interfejsu. Zwięzły sposób wyrażania kombinacji adresu/prefiksu IPv6 jest następujący: ipv6-address/prefix-length.

Poniżej przedstawiono przykład adresu z prefiksem 64-bitowym.

`3FFE:FFFF:0:CD30:0:0:0:0/64`.

Prefiks w tym `3FFE:FFFF:0:CD30`przykładzie jest . Adres można również zapisać w skompresowanej `3FFE:FFFF:0:CD30::/64`formie, jako .

IPv6 definiuje następujące typy adresów:

- **Adres emisji pojedynczej**. Identyfikator dla pojedynczego interfejsu. Pakiet wysłany na ten adres jest dostarczany do zidentyfikowanego interfejsu. Adresy emisji pojedynczej różnią się od adresów multiemisji wartością oktetu wysokiego rzędu. Oktet wysokiego rzędu adresów multiemisji ma wartość szesnastkową FF. Każda inna wartość dla tego oktetu identyfikuje adres emisji pojedynczej. Poniżej przedstawiono różne typy adresów emisji pojedynczej:

  - **Adresy lokalne łącza**. Adresy te są używane na jednym łączu i mają następujący format: FE80::*InterfaceID*. Adresy lokalne łącza są używane między węzłami w łączu dla konfiguracji adresu automatycznego, odnajdowania sąsiada lub gdy nie ma routerów. Adres lokalny łącza jest używany głównie podczas uruchamiania i gdy system nie uzyskał jeszcze adresów o większym zakresie.

  - **Adresy lokalne witryny**. Adresy te są używane w jednej witrynie i mają następujący format: FEC0::*Podsieć:**InterfaceID*. Adresy lokalne witryny są używane do adresowania wewnątrz lokacji bez konieczności stosowania prefiksu globalnego.

  - **Globalne adresy emisji pojedynczej IPv6**. Adresy te mogą być używane w Internecie i mają następujący format: 010(FP, 3 bity) Identyfikator TLA (13 bitów) Zastrzeżony (8 bitów) IDENTYFIKATOR NLA (24 bity) Identyfikator SLA (16 bitów) *InterfaceID* (64 bity).

- **Adres multiemisji**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłów). Pakiet wysłany na ten adres jest dostarczany do wszystkich interfejsów identyfikowanych przez adres. Typy adresów multiemisji zastępują adresy emisji IPv4.

- **Adres anycast**. Identyfikator zestawu interfejsów (zazwyczaj należących do różnych węzłów). Pakiet wysłany na ten adres jest dostarczany tylko do jednego interfejsu identyfikowanego przez adres. Jest to najbliższy interfejs identyfikowany przez metryki routingu. Adresy emisji dowolnej są pobierane z przestrzeni adresowej emisji pojedynczej i nie są syntaktycznie rozróżnialne. Adresowany interfejs wykonuje rozróżnienie między adresami emisji pojedynczej i anycast w funkcji jego konfiguracji.

Ogólnie rzecz biorąc węzeł zawsze ma adres lokalny łącza. Może mieć adres lokalny witryny i jeden lub więcej adresów globalnych.

## <a name="see-also"></a>Zobacz też

- [Protokół internetowy w wersji 6](internet-protocol-version-6.md)
- [Gniazda](sockets.md)
