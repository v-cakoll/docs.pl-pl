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
# <a name="protocol-buffers"></a><span data-ttu-id="9e7ad-103">Bufory protokołu</span><span class="sxs-lookup"><span data-stu-id="9e7ad-103">Protocol buffers</span></span>

<span data-ttu-id="9e7ad-104">Usługi gRPC wysyłają i odbierają dane jako *komunikaty buforu protokołu (Protobuf),* podobne do umów dotyczących danych w programie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9e7ad-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9e7ad-105">Protobuf to skuteczny sposób serializacji danych strukturalnych dla maszyn do odczytu i zapisu, bez narzutów, które ponoszą formaty czytelne dla człowieka, takie jak XML lub JSON.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="9e7ad-106">W tym rozdziale opisano, jak działa protobuf i jak zdefiniować własne wiadomości Protobuf.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="9e7ad-107">Jak działa protobuf</span><span class="sxs-lookup"><span data-stu-id="9e7ad-107">How Protobuf works</span></span>

<span data-ttu-id="9e7ad-108">Większość technik serializacji obiektów .NET, w tym kontrakty danych WCF, działa przy użyciu odbicia do analizowania struktury obiektu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="9e7ad-109">Natomiast większość bibliotek Protobuf wymaga zdefiniowania struktury z góry przy użyciu dedykowanego `.proto` języka *(język buforu protokołu)* w pliku.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="9e7ad-110">Kompilator następnie używa tego pliku do generowania kodu dla dowolnej z obsługiwanych platform.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="9e7ad-111">Obsługiwane platformy obejmują .NET, Java, C/C++, JavaScript i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span>

<span data-ttu-id="9e7ad-112">Kompilator Protobuf, `protoc`, jest utrzymywany przez Google, chociaż dostępne są alternatywne implementacje.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="9e7ad-113">Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="9e7ad-114">Format przewodu Protobuf jest kodowaniem binarnym.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="9e7ad-115">Używa kilka sprytnych sztuczek, aby zminimalizować liczbę bajtów używanych do reprezentowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="9e7ad-116">Znajomość formatu kodowania binarnego nie jest konieczna do korzystania z Protobuf.</span><span class="sxs-lookup"><span data-stu-id="9e7ad-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="9e7ad-117">Ale jeśli jesteś zainteresowany, możesz dowiedzieć się więcej na ten temat [na stronie internetowej Bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="9e7ad-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9e7ad-118">[Poprzedni](why-grpc.md)
>[następny](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="9e7ad-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
