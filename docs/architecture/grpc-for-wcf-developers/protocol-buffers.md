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
# <a name="protocol-buffers"></a><span data-ttu-id="18f90-103">Bufory protokołu</span><span class="sxs-lookup"><span data-stu-id="18f90-103">Protocol buffers</span></span>

<span data-ttu-id="18f90-104">usługi gRPC Services wysyłają i odbierają dane jako *komunikaty o buforze protokołu (protobuf)* , podobnie jak w przypadku kontraktów danych w programie Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="18f90-104">gRPC services send and receive data as *Protocol Buffer (Protobuf) messages*, similar to data contracts in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="18f90-105">Protobuf to wydajny sposób serializowania danych strukturalnych dla maszyn w celu odczytu i zapisu, bez konieczności narzutu na to, że formaty, takie jak XML lub JSON, pozostały.</span><span class="sxs-lookup"><span data-stu-id="18f90-105">Protobuf is an efficient way of serializing structured data for machines to read and write, without the overhead that human-readable formats like XML or JSON incur.</span></span>

<span data-ttu-id="18f90-106">W tym rozdziale opisano, jak działa protobuf oraz jak definiować własne wiadomości protobuf.</span><span class="sxs-lookup"><span data-stu-id="18f90-106">This chapter covers how Protobuf works, and how to define your own Protobuf messages.</span></span>

## <a name="how-protobuf-works"></a><span data-ttu-id="18f90-107">Jak działa protobuf</span><span class="sxs-lookup"><span data-stu-id="18f90-107">How Protobuf works</span></span>

<span data-ttu-id="18f90-108">Większość technik serializacji obiektów .NET, w tym kontraktów danych WCF, działa przy użyciu odbicia w celu analizowania struktury obiektów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="18f90-108">Most .NET object serialization techniques, including WCF's data contracts, work by using reflection to analyze the object structure at runtime.</span></span> <span data-ttu-id="18f90-109">Z kolei większość bibliotek protobuf wymaga zdefiniowania na początku struktury przy użyciu dedykowanego języka (*Język buforowania protokołu*) w pliku `.proto`.</span><span class="sxs-lookup"><span data-stu-id="18f90-109">By contrast, most Protobuf libraries require you to define the structure up front by using a dedicated language (*Protocol Buffer Language*) in a `.proto` file.</span></span> <span data-ttu-id="18f90-110">Kompilator używa tego pliku do wygenerowania kodu dla dowolnej z obsługiwanych platform.</span><span class="sxs-lookup"><span data-stu-id="18f90-110">A compiler then uses this file to generate code for any of the supported platforms.</span></span> <span data-ttu-id="18f90-111">Obsługiwane platformy to .NET, Java, C/C++, JavaScript i wiele innych.</span><span class="sxs-lookup"><span data-stu-id="18f90-111">Supported platforms include .NET, Java, C/C++, JavaScript, and many more.</span></span> 

<span data-ttu-id="18f90-112">Kompilator protobuf, `protoc`, jest obsługiwany przez firmę Google, chociaż dostępne są alternatywne implementacje.</span><span class="sxs-lookup"><span data-stu-id="18f90-112">The Protobuf compiler, `protoc`, is maintained by Google, although alternative implementations are available.</span></span> <span data-ttu-id="18f90-113">Wygenerowany kod jest wydajny i zoptymalizowany pod kątem szybkiej serializacji i deserializacji danych.</span><span class="sxs-lookup"><span data-stu-id="18f90-113">The generated code is efficient and optimized for fast serialization and deserialization of data.</span></span>

<span data-ttu-id="18f90-114">Format sieci protobuf jest kodowaniem binarnym.</span><span class="sxs-lookup"><span data-stu-id="18f90-114">The Protobuf wire format is a binary encoding.</span></span> <span data-ttu-id="18f90-115">Korzysta ona z sprytne lew, aby zminimalizować liczbę bajtów używanych do reprezentowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="18f90-115">It uses some clever tricks to minimize the number of bytes used to represent messages.</span></span> <span data-ttu-id="18f90-116">Znajomość formatu kodowania binarnego nie jest konieczna do korzystania z protobuf.</span><span class="sxs-lookup"><span data-stu-id="18f90-116">Knowledge of the binary encoding format isn't necessary to use Protobuf.</span></span> <span data-ttu-id="18f90-117">Ale jeśli jesteś zainteresowany, możesz dowiedzieć się więcej na ten temat w [witrynie sieci Web bufory protokołu](https://developers.google.com/protocol-buffers/docs/encoding).</span><span class="sxs-lookup"><span data-stu-id="18f90-117">But if you're interested, you can learn more about it on [the Protocol Buffers website](https://developers.google.com/protocol-buffers/docs/encoding).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="18f90-118">[Poprzednie](why-grpc.md)
>[dalej](protobuf-messages.md)</span><span class="sxs-lookup"><span data-stu-id="18f90-118">[Previous](why-grpc.md)
[Next](protobuf-messages.md)</span></span>
