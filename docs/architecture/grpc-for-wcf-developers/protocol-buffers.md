---
title: Bufory protokołu - gRPC dla deweloperów WCF
description: Wprowadzenie do formatu przewodu Bufory protokołu używane dla sieci gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147935"
---
# <a name="protocol-buffers"></a>Bufory protokołu

Usługi gRPC wysyłają i odbierają dane jako *komunikaty buforu protokołu (Protobuf),* podobne do umów dotyczących danych w programie Windows Communication Foundation (WCF). Protobuf to skuteczny sposób serializacji danych strukturalnych dla maszyn do odczytu i zapisu, bez narzutów, które ponoszą formaty czytelne dla człowieka, takie jak XML lub JSON.

W tym rozdziale opisano, jak działa protobuf i jak zdefiniować własne wiadomości Protobuf.

## <a name="how-protobuf-works"></a>Jak działa protobuf

Większość technik serializacji obiektów .NET, w tym kontrakty danych WCF, działa przy użyciu odbicia do analizowania struktury obiektu w czasie wykonywania. Natomiast większość bibliotek Protobuf wymaga zdefiniowania struktury z góry przy użyciu dedykowanego `.proto` języka *(język buforu protokołu)* w pliku. Kompilator następnie używa tego pliku do generowania kodu dla dowolnej z obsługiwanych platform. Obsługiwane platformy obejmują .NET, Java, C/C++, JavaScript i wiele innych.

Kompilator Protobuf, `protoc`, jest utrzymywany przez Google, chociaż dostępne są alternatywne implementacje. Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.

Format przewodu Protobuf jest kodowaniem binarnym. Używa kilka sprytnych sztuczek, aby zminimalizować liczbę bajtów używanych do reprezentowania wiadomości. Znajomość formatu kodowania binarnego nie jest konieczna do korzystania z Protobuf. Ale jeśli jesteś zainteresowany, możesz dowiedzieć się więcej na ten temat [na stronie internetowej Bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Poprzedni](why-grpc.md)
>[następny](protobuf-messages.md)
