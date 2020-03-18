---
title: Zabezpieczenia w aplikacjach gRPC - gRPC dla programistów WCF
description: Omówienie uwierzytelniania i autoryzacji połączeń i kanałów w gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 70cbf441bbc1b299b997f7d1f02bcd2bf7fde60c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147818"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="fb1d2-103">Zabezpieczenia w aplikacjach gRPC</span><span class="sxs-lookup"><span data-stu-id="fb1d2-103">Security in gRPC applications</span></span>

<span data-ttu-id="fb1d2-104">W każdym scenariuszu rzeczywistym zabezpieczenie aplikacji i usług jest niezbędne.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="fb1d2-105">Zabezpieczenia obejmują trzy kluczowe obszary:</span><span class="sxs-lookup"><span data-stu-id="fb1d2-105">Security covers three key areas:</span></span>

* <span data-ttu-id="fb1d2-106">Szyfrowanie ruchu sieciowego w celu uniemożliwienia przechwyceniu go przez złośliwych hakerów.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="fb1d2-107">Uwierzytelnianie klientów i serwerów w celu ustalenia tożsamości i zaufania.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="fb1d2-108">Autoryzowanie klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="fb1d2-109">*Uwierzytelnianie* dotyczy ustalenia tożsamości klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="fb1d2-110">*Autoryzacja* dotyczy określenia, czy klient ma uprawnienia dostępu do zasobu lub wydania polecenia.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="fb1d2-111">Niniejszy rozdział obejmie udogodnienia uwierzytelniania i autoryzacji w gRPC dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="fb1d2-112">Omówi również zabezpieczenia sieci za pośrednictwem szyfrowanych połączeń TLS.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="fb1d2-113">Uwierzytelnianie i autoryzacja WCF</span><span class="sxs-lookup"><span data-stu-id="fb1d2-113">WCF authentication and authorization</span></span>

<span data-ttu-id="fb1d2-114">W programie Windows Communication Foundation (WCF) uwierzytelnianie i autoryzacja były obsługiwane na różne sposoby, w zależności od używanych transportów i powiązań.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="fb1d2-115">WCF obsługiwane różne Standardy\* zabezpieczeń WS.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="fb1d2-116">Obsługa uwierzytelniania systemu Windows dla usług HTTP działających w usługach IIS lub NetTCP między systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="fb1d2-117">uwierzytelnianie i autoryzacja gRPC</span><span class="sxs-lookup"><span data-stu-id="fb1d2-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="fb1d2-118">Uwierzytelnianie i autoryzacja gRPC działa na dwóch poziomach:</span><span class="sxs-lookup"><span data-stu-id="fb1d2-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="fb1d2-119">Uwierzytelnianie/autoryzacja na poziomie wywołania jest zwykle obsługiwane za pomocą tokenów, które są stosowane w metadanych po nadaniu wywołania.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span>
* <span data-ttu-id="fb1d2-120">Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="fb1d2-121">Może również zawierać poświadczenia uwierzytelniania/autoryzacji na poziomie wywołania, które mają być stosowane do każdego wywołania na kanale automatycznie.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span>

<span data-ttu-id="fb1d2-122">Można użyć jednego lub obu tych mechanizmów, aby pomóc zabezpieczyć usługę.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="fb1d2-123">Implementacja ASP.NET Core gRPC obsługuje uwierzytelnianie i autoryzację za pośrednictwem większości standardowych mechanizmów ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="fb1d2-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="fb1d2-124">Uwierzytelnianie połączeń</span><span class="sxs-lookup"><span data-stu-id="fb1d2-124">Call authentication</span></span>
  - <span data-ttu-id="fb1d2-125">Usługa Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="fb1d2-125">Azure Active Directory</span></span>
  - <span data-ttu-id="fb1d2-126">Serwer tożsamości</span><span class="sxs-lookup"><span data-stu-id="fb1d2-126">IdentityServer</span></span>
  - <span data-ttu-id="fb1d2-127">Token nośny JWT</span><span class="sxs-lookup"><span data-stu-id="fb1d2-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="fb1d2-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="fb1d2-128">OAuth 2.0</span></span>
  - <span data-ttu-id="fb1d2-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="fb1d2-129">OpenID Connect</span></span>
  - <span data-ttu-id="fb1d2-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="fb1d2-130">WS-Federation</span></span>
- <span data-ttu-id="fb1d2-131">Uwierzytelnianie kanału</span><span class="sxs-lookup"><span data-stu-id="fb1d2-131">Channel authentication</span></span>
  - <span data-ttu-id="fb1d2-132">Certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="fb1d2-132">Client certificate</span></span>

<span data-ttu-id="fb1d2-133">Wszystkie metody uwierzytelniania wywołań są oparte na *tokenach*.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="fb1d2-134">Jedyną rzeczywistą różnicą jest sposób generowania tokenów i bibliotek, które są używane do sprawdzania poprawności tokenów w usłudze ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="fb1d2-135">Aby uzyskać więcej informacji, zobacz [artykuł Uwierzytelnianie i autoryzacja.](/aspnet/core/grpc/authn-and-authz)</span><span class="sxs-lookup"><span data-stu-id="fb1d2-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="fb1d2-136">Jeśli używasz gRPC za pośrednictwem szyfrowanego tls połączenia HTTP/2, cały ruch między klientami i serwerami jest szyfrowany, nawet jeśli nie używasz uwierzytelniania na poziomie kanału.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="fb1d2-137">W tym rozdziale pokaże, jak zastosować poświadczenia wywołania i poświadczenia kanału do usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="fb1d2-138">Pokaże również, jak używać poświadczeń z klienta gRPC .NET Core do uwierzytelniania z usługą.</span><span class="sxs-lookup"><span data-stu-id="fb1d2-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fb1d2-139">[Poprzedni](client-libraries.md)
>[następny](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="fb1d2-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
