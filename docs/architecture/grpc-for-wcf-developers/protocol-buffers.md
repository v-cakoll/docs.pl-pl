---
title: Bufory protokołu — gRPC dla deweloperów WCF
description: Wprowadzenie do formatu buforów protokołów używanych do obsługi sieci gRPC.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 6b47c7f3576134d8ee44f79e329cc4879661e6c3
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846302"
---
# <a name="protocol-buffers"></a>Bufory protokołu

usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych usługi WCF. Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.

W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.

## <a name="how-protobuf-works"></a>Jak działa protobuf

Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia, aby analizować strukturę obiektów w czasie wykonywania. Z kolei większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w pliku `.proto`. Ten plik jest następnie używany przez kompilator do generowania kodu dla dowolnej z obsługiwanych platform, w tym .NET, Java, C/C++, JavaScript i wielu innych. Kompilator protobuf, `protoc`, jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje. Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.

Sam format sieci protobuf jest kodowaniem binarnym, który używa niektórych sprytne lew do zminimalizowania liczby bajtów używanych do reprezentowania komunikatów. Znajomość formatu kodowania danych binarnych nie jest konieczna do korzystania z protobuf, ale jeśli chcesz uzyskać więcej informacji na jego temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Poprzedni](why-grpc.md)
>[Następny](protobuf-messages.md)
