---
title: Migrowanie rozwiązania WCF do gRPC-gRPC dla deweloperów WCF
description: Jak migrować różne typy usługi WCF do wartości równoważnej w gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 65c30b777d9981cb3291b846f698f2a69b4498fc
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846592"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="dd6b8-103">Migrowanie rozwiązania WCF do usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="dd6b8-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="dd6b8-104">W tym rozdziale zawarto informacje na temat pracy z projektami ASP.NET Core gRPC 3,0 i zademonstrowania migracji różnych typów usług WCF do gRPC równoważnej:</span><span class="sxs-lookup"><span data-stu-id="dd6b8-104">This chapter will look at how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of WCF service to the gRPC equivalent:</span></span>

- <span data-ttu-id="dd6b8-105">Utwórz projekt ASP.NET Core 3,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="dd6b8-106">Proste operacje typu żądanie-odpowiedź do gRPC jednoargumentowego wywołania procedury (RPC).</span><span class="sxs-lookup"><span data-stu-id="dd6b8-106">Simple Request-Reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="dd6b8-107">Jednokierunkowa operacja gRPC RPC przesyłania strumieniowego klienta.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="dd6b8-108">Usługi pełnego dupleksu do gRPC dwukierunkowego wywołania RPC.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-108">Full Duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="dd6b8-109">Istnieje również porównanie dotyczące korzystania z usług przesyłania strumieniowego i powtarzających się pól w celu zwracania zestawów danych i używania bibliotek klienckich na końcu rozdziału.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-109">There's also a comparison of using streaming services versus repeated fields for returning data sets, and the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="dd6b8-110">Przykładowa aplikacja WCF jest minimalnym elementem zastępczym zestawu giełdowych usług handlowych przy użyciu biblioteki kontenerów typu Open Source (IoC) o nazwie *Autofac* na potrzeby iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-110">The sample WCF application is a minimal stub of a set of stock trading services, using the open-source Inversion of Control (IoC) container library called *Autofac* for dependency injection.</span></span> <span data-ttu-id="dd6b8-111">Obejmuje ona trzy usługi, po jednej dla każdego typu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-111">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="dd6b8-112">Usługi zostaną omówione bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-112">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="dd6b8-113">Rozwiązania można pobrać z programu [dotnet-Architecture/GRPC-for-WCF — deweloperzy](https://github.com/dotnet-architecture/grpc-for-wcf-developers) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-113">The solutions can be downloaded from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="dd6b8-114">Usługi wykorzystują fałszywe dane, aby zminimalizować zależności zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-114">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="dd6b8-115">Przykłady obejmują implementacje WCF i gRPC każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="dd6b8-115">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dd6b8-116">[Poprzedni](ws-protocols.md)
>[Następny](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="dd6b8-116">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
