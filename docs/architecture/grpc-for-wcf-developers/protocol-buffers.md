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
# <a name="protocol-buffers"></a><span data-ttu-id="af1ae-103">Bufory protokołu</span><span class="sxs-lookup"><span data-stu-id="af1ae-103">Protocol buffers</span></span>

<span data-ttu-id="af1ae-104">usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="af1ae-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="af1ae-105">Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.</span><span class="sxs-lookup"><span data-stu-id="af1ae-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="af1ae-106">W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.</span><span class="sxs-lookup"><span data-stu-id="af1ae-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="af1ae-107">Jak działa protobuf</span><span class="sxs-lookup"><span data-stu-id="af1ae-107">How Protobuf works</span></span>

<span data-ttu-id="af1ae-108">Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia, aby analizować strukturę obiektów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="af1ae-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="af1ae-109">Z kolei większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="af1ae-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="af1ae-110">Ten plik jest następnie używany przez kompilator do generowania kodu dla dowolnej z obsługiwanych platform, w tym .NET, Java, C/C++, JavaScript i wielu innych.</span><span class="sxs-lookup"><span data-stu-id="af1ae-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="af1ae-111">Kompilator protobuf, `protoc`, jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje.</span><span class="sxs-lookup"><span data-stu-id="af1ae-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="af1ae-112">Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="af1ae-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="af1ae-113">Sam format sieci protobuf jest kodowaniem binarnym, który używa niektórych sprytne lew do zminimalizowania liczby bajtów używanych do reprezentowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="af1ae-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="af1ae-114">Znajomość formatu kodowania danych binarnych nie jest konieczna do korzystania z protobuf, ale jeśli chcesz uzyskać więcej informacji na jego temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="af1ae-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="af1ae-115">[Poprzedni](why-grpc.md)
>[Następny](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="af1ae-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
