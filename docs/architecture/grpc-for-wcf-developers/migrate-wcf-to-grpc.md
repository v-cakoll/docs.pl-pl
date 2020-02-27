---
title: Migrowanie rozwiązania WCF do gRPC-gRPC dla deweloperów WCF
description: Jak migrować różne typy usług WCF do równoważnej w gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 12e724ab46a33547d352da7a604a5a994e617bc2
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628517"
---
# <a name="migrate-a-wcf-solution-to-grpc"></a><span data-ttu-id="0ca9e-103">Migrowanie rozwiązania WCF do usługi gRPC</span><span class="sxs-lookup"><span data-stu-id="0ca9e-103">Migrate a WCF solution to gRPC</span></span>

<span data-ttu-id="0ca9e-104">W tym rozdziale opisano sposób pracy z projektami ASP.NET Core gRPC 3,0 i zademonstrowanie migracji różnych typów usług Windows Communication Foundation (WCF) do gRPC równoważnej:</span><span class="sxs-lookup"><span data-stu-id="0ca9e-104">This chapter will describe how to work with ASP.NET Core 3.0 gRPC projects and demonstrate migrating different types of Windows Communication Foundation (WCF) services to the gRPC equivalent:</span></span>

- <span data-ttu-id="0ca9e-105">Utwórz projekt ASP.NET Core 3,0 gRPC.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-105">Create an ASP.NET Core 3.0 gRPC project.</span></span>
- <span data-ttu-id="0ca9e-106">Proste operacje typu żądanie-odpowiedź do gRPC jednoargumentowego wywołania procedury (RPC).</span><span class="sxs-lookup"><span data-stu-id="0ca9e-106">Simple request-reply operations to gRPC unary RPC.</span></span>
- <span data-ttu-id="0ca9e-107">Jednokierunkowa operacja gRPC RPC przesyłania strumieniowego klienta.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-107">One-way operations to gRPC client streaming RPC.</span></span>
- <span data-ttu-id="0ca9e-108">Usługi pełnego dupleksu do gRPC dwukierunkowego wywoływania procedur RPC.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-108">Full-duplex services to gRPC bidirectional streaming RPC.</span></span>

<span data-ttu-id="0ca9e-109">Istnieje również porównanie dotyczące korzystania z usług przesyłania strumieniowego i powtarzających się pól w celu zwrócenia zestawów danych i istnieje dyskusja na temat używania bibliotek klienckich na końcu rozdziału.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-109">There's also a comparison of using streaming services versus repeated fields for returning datasets, and there's a discussion of the use of client libraries at the end of the chapter.</span></span>

<span data-ttu-id="0ca9e-110">Przykładowa aplikacja WCF jest minimalnym elementem zastępczym zestawu giełdowych usług handlowych.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-110">The sample WCF application is a minimal stub of a set of stock trading services.</span></span> <span data-ttu-id="0ca9e-111">Używa ona biblioteki kontenerów kontroli (IoC) typu open source o nazwie Autofac na potrzeby iniekcji zależności.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-111">It uses the open-source Inversion of Control (IoC) container library called Autofac for dependency injection.</span></span> <span data-ttu-id="0ca9e-112">Obejmuje ona trzy usługi, po jednej dla każdego typu usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-112">It includes three services, one for each WCF service type.</span></span> <span data-ttu-id="0ca9e-113">Usługi zostaną omówione bardziej szczegółowo w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-113">The services will be discussed in more detail in the following sections.</span></span> <span data-ttu-id="0ca9e-114">Możesz pobrać rozwiązania z programu [dotnet-Architecture/GRPC-for-WCF — deweloperzy](https://github.com/dotnet-architecture/grpc-for-wcf-developers) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-114">You can download the solutions from [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers) on GitHub.</span></span> <span data-ttu-id="0ca9e-115">Usługi wykorzystują fałszywe dane, aby zminimalizować zależności zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-115">The services use fake data to minimize external dependencies.</span></span>

<span data-ttu-id="0ca9e-116">Przykłady obejmują implementacje WCF i gRPC każdej usługi.</span><span class="sxs-lookup"><span data-stu-id="0ca9e-116">The samples include the WCF and gRPC implementations of each service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0ca9e-117">[Poprzednie](ws-protocols.md)
>[dalej](create-project.md)</span><span class="sxs-lookup"><span data-stu-id="0ca9e-117">[Previous](ws-protocols.md)
[Next](create-project.md)</span></span>
