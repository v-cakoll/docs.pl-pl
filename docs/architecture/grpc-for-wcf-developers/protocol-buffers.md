---
title: Bufory protokołu — gRPC dla deweloperów WCF
description: Wprowadzenie do formatu buforów protokołów używanych do obsługi sieci gRPC.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 4f9031c86731ea7ded4a812be9967237e52c4b39
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184170"
---
# <a name="protocol-buffers"></a>Bufory protokołu

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych usługi WCF. Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.

W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.

## <a name="how-protobuf-works"></a>Jak działa protobuf

Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia, aby analizować strukturę obiektów w czasie wykonywania. W przeciwieństwie do tego większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w `.proto` pliku. Ten plik jest następnie używany przez kompilator do generowania kodu dla dowolnej z obsługiwanych platform, w tym .NET, Java, C/C++, JavaScript i wielu innych. Kompilator `protoc`protobuf jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje. Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.

Sam format sieci protobuf jest kodowaniem binarnym, który używa niektórych sprytne lew do zminimalizowania liczby bajtów używanych do reprezentowania komunikatów. Znajomość formatu kodowania danych binarnych nie jest konieczna do korzystania z protobuf, ale jeśli chcesz uzyskać więcej informacji na jego temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Poprzedni](why-grpc.md)
>[Następny](protobuf-messages.md)
