---
title: Zabezpieczenia w aplikacjach gRPC — gRPC dla deweloperów WCF
description: Omówienie uwierzytelniania wywołań i kanałów oraz autoryzacji w programie gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: d5804ad5de4a834eb81b90fa1ea7a61969a0b42f
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503409"
---
# <a name="security-in-grpc-applications"></a><span data-ttu-id="44cf6-103">Zabezpieczenia w aplikacjach gRPC</span><span class="sxs-lookup"><span data-stu-id="44cf6-103">Security in gRPC applications</span></span>

<span data-ttu-id="44cf6-104">W dowolnym rzeczywistym scenariuszu Zabezpieczanie aplikacji i usług jest niezbędne.</span><span class="sxs-lookup"><span data-stu-id="44cf6-104">In any real-world scenario, securing applications and services is essential.</span></span> <span data-ttu-id="44cf6-105">Zabezpieczenia obejmują trzy kluczowe obszary:</span><span class="sxs-lookup"><span data-stu-id="44cf6-105">Security covers three key areas:</span></span> 

* <span data-ttu-id="44cf6-106">Szyfrowanie ruchu sieciowego, aby zapobiec przechwyceniu go przez złośliwych hakerów.</span><span class="sxs-lookup"><span data-stu-id="44cf6-106">Encrypting network traffic to prevent malicious hackers from intercepting it.</span></span>
* <span data-ttu-id="44cf6-107">Uwierzytelnianie klientów i serwerów w celu ustanowienia tożsamości i zaufania.</span><span class="sxs-lookup"><span data-stu-id="44cf6-107">Authenticating clients and servers to establish identity and trust.</span></span>
* <span data-ttu-id="44cf6-108">Autoryzowanie klientów do kontrolowania dostępu do systemów i stosowania uprawnień na podstawie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="44cf6-108">Authorizing clients to control access to systems and apply permissions based on identity.</span></span>

> [!NOTE]
> <span data-ttu-id="44cf6-109">*Uwierzytelnianie* dotyczy ustanowienia tożsamości klienta lub serwera.</span><span class="sxs-lookup"><span data-stu-id="44cf6-109">*Authentication* is concerned with establishing the identity of a client or server.</span></span> <span data-ttu-id="44cf6-110">*Autoryzacja* jest zaangażowana w ustalanie, czy klient ma uprawnienia dostępu do zasobu, czy wydać polecenie.</span><span class="sxs-lookup"><span data-stu-id="44cf6-110">*Authorization* is concerned with determining whether a client has permission to access a resource or issue a command.</span></span>

<span data-ttu-id="44cf6-111">Ten rozdział obejmuje funkcje uwierzytelniania i autoryzacji w programie gRPC dla ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44cf6-111">This chapter will cover the facilities for authentication and authorization in gRPC for ASP.NET Core.</span></span> <span data-ttu-id="44cf6-112">Będzie również omawiać zabezpieczenia sieci przy użyciu szyfrowanych połączeń TLS.</span><span class="sxs-lookup"><span data-stu-id="44cf6-112">It will also discuss network security through TLS encrypted connections.</span></span>

## <a name="wcf-authentication-and-authorization"></a><span data-ttu-id="44cf6-113">Uwierzytelnianie i autoryzacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="44cf6-113">WCF authentication and authorization</span></span>

<span data-ttu-id="44cf6-114">W programie Windows Communication Foundation (WCF) uwierzytelnianie i autoryzacja zostały obsłużone na różne sposoby, w zależności od używanych transportów i powiązań.</span><span class="sxs-lookup"><span data-stu-id="44cf6-114">In Windows Communication Foundation (WCF), authentication and authorization were handled in different ways, depending on the transports and bindings being used.</span></span> <span data-ttu-id="44cf6-115">Obsługiwane są różne standardy zabezpieczeń WS-\* WCF.</span><span class="sxs-lookup"><span data-stu-id="44cf6-115">WCF supported various WS-\* security standards.</span></span> <span data-ttu-id="44cf6-116">Obsługiwane jest również uwierzytelnianie systemu Windows dla usług HTTP uruchomionych w usługach IIS lub NetTCP Services między systemami Windows.</span><span class="sxs-lookup"><span data-stu-id="44cf6-116">It also supported Windows authentication for HTTP services running in IIS or NetTCP services between Windows systems.</span></span>

## <a name="grpc-authentication-and-authorization"></a><span data-ttu-id="44cf6-117">uwierzytelnianie i autoryzacja gRPC</span><span class="sxs-lookup"><span data-stu-id="44cf6-117">gRPC authentication and authorization</span></span>

<span data-ttu-id="44cf6-118">uwierzytelnianie i autoryzacja gRPC odbywają się na dwóch poziomach:</span><span class="sxs-lookup"><span data-stu-id="44cf6-118">gRPC authentication and authorization works on two levels:</span></span>

* <span data-ttu-id="44cf6-119">Uwierzytelnianie na poziomie wywołań/Autoryzacja jest zwykle obsługiwana za pomocą tokenów, które są stosowane w metadanych podczas wywołania.</span><span class="sxs-lookup"><span data-stu-id="44cf6-119">Call-level authentication/authorization is usually handled through tokens that are applied in metadata when the call is made.</span></span> 
* <span data-ttu-id="44cf6-120">Uwierzytelnianie na poziomie kanału używa certyfikatu klienta, który jest stosowany na poziomie połączenia.</span><span class="sxs-lookup"><span data-stu-id="44cf6-120">Channel-level authentication uses a client certificate that's applied at the connection level.</span></span> <span data-ttu-id="44cf6-121">Może również uwzględniać poświadczenia uwierzytelniania/autoryzacji na poziomie wywołań, które mają być stosowane do każdego wywołania w kanale automatycznie.</span><span class="sxs-lookup"><span data-stu-id="44cf6-121">It can also include call-level authentication/authorization credentials to be applied to every call on the channel automatically.</span></span> 

<span data-ttu-id="44cf6-122">Można użyć jednego lub obu tych mechanizmów, aby pomóc w zabezpieczeniu usługi.</span><span class="sxs-lookup"><span data-stu-id="44cf6-122">You can use either or both of these mechanisms to help secure your service.</span></span>

<span data-ttu-id="44cf6-123">ASP.NET Core implementacja gRPC obsługuje uwierzytelnianie i autoryzację za pomocą większości standardowych mechanizmów ASP.NET Core:</span><span class="sxs-lookup"><span data-stu-id="44cf6-123">The ASP.NET Core implementation of gRPC supports authentication and authorization through most of the standard ASP.NET Core mechanisms:</span></span>

- <span data-ttu-id="44cf6-124">Uwierzytelnianie wywołań</span><span class="sxs-lookup"><span data-stu-id="44cf6-124">Call authentication</span></span>
  - <span data-ttu-id="44cf6-125">Azure Active Directory</span><span class="sxs-lookup"><span data-stu-id="44cf6-125">Azure Active Directory</span></span>
  - <span data-ttu-id="44cf6-126">IdentityServer</span><span class="sxs-lookup"><span data-stu-id="44cf6-126">IdentityServer</span></span>
  - <span data-ttu-id="44cf6-127">Token okaziciela JWT</span><span class="sxs-lookup"><span data-stu-id="44cf6-127">JWT Bearer Token</span></span>
  - <span data-ttu-id="44cf6-128">OAuth 2.0</span><span class="sxs-lookup"><span data-stu-id="44cf6-128">OAuth 2.0</span></span>
  - <span data-ttu-id="44cf6-129">OpenID Connect</span><span class="sxs-lookup"><span data-stu-id="44cf6-129">OpenID Connect</span></span>
  - <span data-ttu-id="44cf6-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="44cf6-130">WS-Federation</span></span>
- <span data-ttu-id="44cf6-131">Uwierzytelnianie kanałów</span><span class="sxs-lookup"><span data-stu-id="44cf6-131">Channel authentication</span></span>
  - <span data-ttu-id="44cf6-132">certyfikat klienta</span><span class="sxs-lookup"><span data-stu-id="44cf6-132">Client certificate</span></span>

<span data-ttu-id="44cf6-133">Metody uwierzytelniania wywołań są wszystkie oparte na *tokenach*.</span><span class="sxs-lookup"><span data-stu-id="44cf6-133">The call authentication methods are all based on *tokens*.</span></span> <span data-ttu-id="44cf6-134">Jedyną rzeczywistą różnicą jest to, w jaki sposób generowane są tokeny, oraz biblioteki, które są używane do weryfikacji tokenów w usłudze ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="44cf6-134">The only real difference is how the tokens are generated and the libraries that are used to validate the tokens in the ASP.NET Core service.</span></span>

<span data-ttu-id="44cf6-135">Aby uzyskać więcej informacji, zobacz artykuł dotyczący [uwierzytelniania i autoryzacji](/aspnet/core/grpc/authn-and-authz) .</span><span class="sxs-lookup"><span data-stu-id="44cf6-135">For more information, see the [Authentication and authorization](/aspnet/core/grpc/authn-and-authz) article.</span></span>

> [!NOTE]
> <span data-ttu-id="44cf6-136">W przypadku korzystania z gRPC za pośrednictwem protokołu HTTP/2 zaszyfrowanego przy użyciu protokołu TLS cały ruch między klientami a serwerami jest szyfrowany, nawet jeśli nie jest używane uwierzytelnianie na poziomie kanału.</span><span class="sxs-lookup"><span data-stu-id="44cf6-136">When you're using gRPC over a TLS-encrypted HTTP/2 connection, all traffic between clients and servers is encrypted, even if you don't use channel-level authentication.</span></span>

<span data-ttu-id="44cf6-137">W tym rozdziale przedstawiono sposób stosowania poświadczeń wywołań i poświadczeń kanału do usługi gRPC.</span><span class="sxs-lookup"><span data-stu-id="44cf6-137">This chapter will show how to apply call credentials and channel credentials to a gRPC service.</span></span> <span data-ttu-id="44cf6-138">Pokazano również, jak używać poświadczeń z klienta programu .NET Core gRPC do uwierzytelniania w usłudze.</span><span class="sxs-lookup"><span data-stu-id="44cf6-138">It will also show how to use credentials from a .NET Core gRPC client to authenticate with the service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="44cf6-139">[Poprzednie](client-libraries.md)
>[dalej](call-credentials.md)</span><span class="sxs-lookup"><span data-stu-id="44cf6-139">[Previous](client-libraries.md)
[Next](call-credentials.md)</span></span>
