---
title: Zabezpieczenia w aplikacjach gRPC — gRPC dla deweloperów WCF
description: Omówienie uwierzytelniania wywołań i kanałów oraz autoryzacji w programie gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: d0b7ff5bef755c5eeb9b3c419dcda1cb75ac4031
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846232"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="51a49-103">Zabezpieczenia w aplikacjach gRPC</span><span class="sxs-lookup"><span data-stu-id="51a49-103">Security in gRPC applications</span></span>

<span data-ttu-id="51a49-104">W dowolnym rzeczywistym scenariuszu Zabezpieczanie aplikacji i usług jest niezbędne.</span><span class="sxs-lookup"><span data-stu-id="51a49-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="51a49-105">Zabezpieczenia obejmują trzy kluczowe obszary: szyfrowanie ruchu sieciowego w celu uniemożliwienia jego przechwytywania przez złe uczestników; Uwierzytelnianie klientów i serwerów w celu ustanowienia tożsamości i zaufania; i Autoryzuj klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="51a49-105">Security covers three key areas: encrypting network traffic to prevent it from being intercepted by bad actors; authenticating clients and servers to establish identity and trust; and authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="51a49-106">**Uwierzytelnianie** dotyczy ustanowienia tożsamości klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="51a49-106">**Authentication** is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="51a49-107">**Autoryzacja** jest zaangażowana w ustalanie, czy klient ma uprawnienia dostępu do zasobu, czy wydać polecenie.</span><span class="sxs-lookup"><span data-stu-id="51a49-107">**Authorization** is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="51a49-108">Ten rozdział obejmuje funkcje uwierzytelniania i autoryzacji w programie gRPC dla ASP.NET Core i omówienia zabezpieczeń sieci przy użyciu szyfrowanych połączeń TLS.</span><span class="sxs-lookup"><span data-stu-id="51a49-108">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core, and discuss network security using TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="51a49-109">Uwierzytelnianie i autoryzacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="51a49-109">WCF authentication and authorization</span></span>

<span data-ttu-id="51a49-110">W programie WCF uwierzytelnianie i autoryzacja zostały obsłużone na różne sposoby w zależności od używanych transportów i powiązań.</span><span class="sxs-lookup"><span data-stu-id="51a49-110">In WCF, authentication and authorization were handled in different ways depending on the transports and bindings being used.</span></span> <span data-ttu-id="51a49-111">Obsługiwane są różne standardy zabezpieczeń WS-\*, a także uwierzytelnianie systemu Windows dla usług HTTP uruchomionych w usługach IIS lub NetTCP Services między systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="51a49-111">WCF supported various WS-\* security standards, as well as Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="51a49-112">uwierzytelnianie i autoryzacja gRPC</span><span class="sxs-lookup"><span data-stu-id="51a49-112">gRPC authentication and authorization</span></span>

<span data-ttu-id="51a49-113">uwierzytelnianie i autoryzacja gRPC działają na dwóch poziomach.</span><span class="sxs-lookup"><span data-stu-id="51a49-113">gRPC authentication and authorization works on two levels.</span></span> <span data-ttu-id="51a49-114">Uwierzytelnianie na poziomie wywołań/Autoryzacja jest zwykle obsługiwana przy użyciu tokenów, które są stosowane w metadanych podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="51a49-114">Call-level authentication/authorization is usually handled using tokens that are applied in metadata when the call is made.</span></span> <span data-ttu-id="51a49-115">Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia, i może również obejmować poświadczenia uwierzytelniania/autoryzacji na poziomie wywołań, które mają być stosowane do każdego wywołania w kanale automatycznie.</span><span class="sxs-lookup"><span data-stu-id="51a49-115">Channel-level authentication uses a client certificate that is applied at the connection level, and can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> <span data-ttu-id="51a49-116">Do zabezpieczenia usługi można użyć jednego lub obu tych mechanizmów.</span><span class="sxs-lookup"><span data-stu-id="51a49-116">You can use either or both of these mechanisms to secure your service.</span></span>

<span data-ttu-id="51a49-117">ASP.NET Core implementacja gRPC obsługuje uwierzytelnianie i autoryzację przy użyciu większości standardowych mechanizmów ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="51a49-117">The ASP.NET Core implementation of gRPC supports authentication and authorization using most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="51a49-118">Uwierzytelnianie wywołań</span><span class="sxs-lookup"><span data-stu-id="51a49-118">Call authentication</span></span>
  - <span data-ttu-id="51a49-119">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="51a49-119">Azure Active Directory</span></span>
  - <span data-ttu-id="51a49-120">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="51a49-120">IdentityServer</span></span>
  - <span data-ttu-id="51a49-121">Token okaziciela JWT</span><span class="sxs-lookup"><span data-stu-id="51a49-121">JWT Bearer Token</span></span>
  - <span data-ttu-id="51a49-122">OAuth 2,0</span><span class="sxs-lookup"><span data-stu-id="51a49-122">OAuth 2.0</span></span>
  - <span data-ttu-id="51a49-123">OpenID Connect połączenie</span><span class="sxs-lookup"><span data-stu-id="51a49-123">OpenID Connect</span></span>
  - <span data-ttu-id="51a49-124">Usługa WS-Federation</span><span class="sxs-lookup"><span data-stu-id="51a49-124">WS-Federation</span></span>
- <span data-ttu-id="51a49-125">Uwierzytelnianie kanałów</span><span class="sxs-lookup"><span data-stu-id="51a49-125">Channel authentication</span></span>
  - <span data-ttu-id="51a49-126">Certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="51a49-126">Client Certificate</span></span>

<span data-ttu-id="51a49-127">Metody uwierzytelniania wywołań są wszystkie oparte na *tokenach*.</span><span class="sxs-lookup"><span data-stu-id="51a49-127">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="51a49-128">Jedyną rzeczywistą różnicą jest to, w jaki sposób generowany jest token, oraz biblioteki, które są używane do weryfikacji tokenów w usłudze ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="51a49-128">The only real difference is how the token is generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="51a49-129">Aby uzyskać więcej informacji, zobacz [dokumentację dotyczącą uwierzytelniania i autoryzacji na Microsoft docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="51a49-129">For more information, see the [Authentication and authorization documentation on Microsoft Docs](https://docs.microsoft.com/aspnet/core/grpc/authn-and-authz?view=aspnetcore-3.0).</span></span>

> [!NOTE]
> <span data-ttu-id="51a49-130">W przypadku korzystania z gRPC za pośrednictwem protokołu HTTP/2 zaszyfrowanego przy użyciu protokołu TLS cały ruch między klientami a serwerami jest szyfrowany, nawet jeśli nie jest używane uwierzytelnianie na poziomie kanału.</span><span class="sxs-lookup"><span data-stu-id="51a49-130">When using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="51a49-131">W tym rozdziale pokazano, jak zastosować poświadczenia wywołania i poświadczenia kanału do usługi gRPC oraz jak używać poświadczeń z klienta platformy .NET Core gRPC do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="51a49-131">This chapter will show how to apply call credentials and channel credentials to a gRPC service, and how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="51a49-132">[Poprzedni](client-libraries.md)
>[Następny](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="51a49-132">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
