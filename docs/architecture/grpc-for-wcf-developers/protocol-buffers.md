---
title: Bufory protokołu — gRPC dla deweloperów WCF
description: Wprowadzenie do formatu buforów protokołów używanych do obsługi sieci gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503458"
---
# <a name="protocol-buffers"></a>Bufory protokołu

usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych w programie Windows Communication Foundation (WCF). Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.

W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.

## <a name="how-protobuf-works"></a>Jak działa protobuf

Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia w celu analizowania struktury obiektów w czasie wykonywania. Z kolei większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w pliku `.proto`. Kompilator używa tego pliku do wygenerowania kodu dla dowolnej z obsługiwanych platform. Obsługiwane platformy to .NET, Java, C/C++, JavaScript i wiele innych. 

Kompilator protobuf, `protoc`, jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje. Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.

Format sieci protobuf jest kodowaniem binarnym. Korzysta ona z sprytne lew, aby zminimalizować liczbę bajtów używanych do reprezentowania komunikatów. Znajomość formatu kodowania binarnego nie jest konieczna do korzystania z protobuf. Ale jeśli jesteś zainteresowany, możesz dowiedzieć się więcej na ten temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Poprzednie](why-grpc.md)
>[dalej](protobuf-messages.md)
