---
title: Bufory protokołu — gRPC dla deweloperów WCF
description: Wprowadzenie do formatu buforów protokołów używanych do obsługi sieci gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: dbe8cb43475cfeec19051daf68452ef86269372f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967294"
---
# <a name="protocol-buffers"></a><span data-ttu-id="3b25a-103">Bufory protokołu</span><span class="sxs-lookup"><span data-stu-id="3b25a-103">Protocol buffers</span></span>

<span data-ttu-id="3b25a-104">usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="3b25a-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to WCF's data contracts.</span></span> <span data-ttu-id="3b25a-105">Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.</span><span class="sxs-lookup"><span data-stu-id="3b25a-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="3b25a-106">W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.</span><span class="sxs-lookup"><span data-stu-id="3b25a-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="3b25a-107">Jak działa protobuf</span><span class="sxs-lookup"><span data-stu-id="3b25a-107">How Protobuf works</span></span>

<span data-ttu-id="3b25a-108">Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia, aby analizować strukturę obiektów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3b25a-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at run time.</span></span> <span data-ttu-id="3b25a-109">Z kolei większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="3b25a-109">By contrast, most Protobuf libraries require you to define the structure up front using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="3b25a-110">Ten plik jest następnie używany przez kompilator do generowania kodu dla dowolnej z obsługiwanych platform, w tym .NET, Java, C/C++, JavaScript i wielu innych.</span><span class="sxs-lookup"><span data-stu-id="3b25a-110">This file is then used by a compiler to generate code for any of the supported platforms, including .NET, Java, C/C++, JavaScript, and many more.</span></span> <span data-ttu-id="3b25a-111">Kompilator protobuf, `protoc`, jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje.</span><span class="sxs-lookup"><span data-stu-id="3b25a-111">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="3b25a-112">Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="3b25a-112">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="3b25a-113">Sam format sieci protobuf jest kodowaniem binarnym, który używa niektórych sprytne lew do zminimalizowania liczby bajtów używanych do reprezentowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="3b25a-113">The Protobuf wire format itself is a binary encoding, which uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="3b25a-114">Znajomość formatu kodowania danych binarnych nie jest konieczna do korzystania z protobuf, ale jeśli chcesz uzyskać więcej informacji na jego temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="3b25a-114">Knowledge of the binary encoding format isn't necessary to use Protobuf, but if you're interested you can learn more about it on [the Protocol Buffers web site](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="3b25a-115">[Poprzedni](why-grpc.md)
>[Następny](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="3b25a-115">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
