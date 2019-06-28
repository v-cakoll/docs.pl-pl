---
title: Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: db5060826d3bfcc259c098a160354892a050554c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422395"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="841f7-102">Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia</span><span class="sxs-lookup"><span data-stu-id="841f7-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="841f7-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="841f7-103">Applies To</span></span>  
  
- <span data-ttu-id="841f7-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="841f7-104">Windows Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="841f7-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="841f7-105">ASP.NET</span></span>  
  
 <span data-ttu-id="841f7-106">W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF aplikacji internetowych programu ASP.NET obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="841f7-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="841f7-107">W scenariuszu aplikacji obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama aplikacja, użytkownik końcowy i usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="841f7-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="841f7-108">Następujący rysunek opisuje ten scenariusz:</span><span class="sxs-lookup"><span data-stu-id="841f7-108">The following figure describes this scenario:</span></span>  
  
 ![Diagram przedstawiający składników WIF podstawową aplikację internetową.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. <span data-ttu-id="841f7-110">Aplikacja obsługująca oświadczenia używa programu WIF do identyfikowania nieuwierzytelnionych żądań i przekierowywania ich do usługi STS.</span><span class="sxs-lookup"><span data-stu-id="841f7-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2. <span data-ttu-id="841f7-111">Użytkownik końcowy podaje poświadczenia usłudze STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.</span><span class="sxs-lookup"><span data-stu-id="841f7-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3. <span data-ttu-id="841f7-112">Przy użyciu tokenu wystawionego przez usługę STS w żądaniu użytkownik jest przekierowywany z usługi STS do aplikacji obsługującej oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="841f7-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4. <span data-ttu-id="841f7-113">Aplikacja obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem.</span><span class="sxs-lookup"><span data-stu-id="841f7-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="841f7-114">Aplikacja obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu.</span><span class="sxs-lookup"><span data-stu-id="841f7-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="841f7-115">Deweloperzy Użyj odpowiedniego interfejsu API programu WIF i typy, na przykład **ClaimsPrincipal** do potrzeb aplikacji, takich jak zaimplementowanie dla niej autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="841f7-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="841f7-116">Począwszy od .NET 4.5, WIF jest częścią pakietu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="841f7-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="841f7-117">Klasy programu WIF bezpośrednio dostępne w ramach pozwala znacznie głębszą integrację tożsamości opartej na oświadczeniach na platformie .NET, ułatwiając korzystanie z oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="841f7-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="841f7-118">Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="841f7-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="841f7-119">Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="841f7-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="841f7-120">STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="841f7-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="841f7-121">Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:</span><span class="sxs-lookup"><span data-stu-id="841f7-121">Microsoft offers two industry standard STS’s:</span></span>  
  
- [<span data-ttu-id="841f7-122">Active Directory Federation Services (AD FS) 2.0</span><span class="sxs-lookup"><span data-stu-id="841f7-122">Active Directory Federation Services (AD FS) 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [<span data-ttu-id="841f7-123">Windows Azure usługa Access Control Service (ACS)</span><span class="sxs-lookup"><span data-stu-id="841f7-123">Windows Azure Access Control Service (ACS)</span></span>](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 <span data-ttu-id="841f7-124">Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="841f7-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="841f7-125">ACS to usługa w chmurze oferowana jako część platformy Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="841f7-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="841f7-126">Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="841f7-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="841f7-127">Na przykład, można użyć Local Development STS, która jest częścią [narzędzie tożsamości i dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) które jest dostępne bezpłatnie w trybie online.</span><span class="sxs-lookup"><span data-stu-id="841f7-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="841f7-128">Aby przy użyciu programu WIF utworzyć swoją pierwszą aplikację programu ASP.NET obsługującą oświadczenia, postępuj zgodnie z instrukcjami podanymi w jednym z następujących tematów:</span><span class="sxs-lookup"><span data-stu-id="841f7-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
- [<span data-ttu-id="841f7-129">Instrukcje: Tworzenie aplikacji sieci Web obsługującej oświadczenia platformy ASP.NET MVC przy użyciu programu WIF</span><span class="sxs-lookup"><span data-stu-id="841f7-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [<span data-ttu-id="841f7-130">Instrukcje: Tworzenie aplikacji formularzy sieci Web programu ASP.NET obsługującej oświadczenia za pomocą programu WIF</span><span class="sxs-lookup"><span data-stu-id="841f7-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](../../../docs/framework/security/how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [<span data-ttu-id="841f7-131">Instrukcje: Tworzenie aplikacji programu ASP.NET obsługującej oświadczenia, za pomocą uwierzytelniania opartego na formularzach</span><span class="sxs-lookup"><span data-stu-id="841f7-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](../../../docs/framework/security/claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="841f7-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="841f7-132">See also</span></span>

- [<span data-ttu-id="841f7-133">Wprowadzenie do korzystania z programu WIF</span><span class="sxs-lookup"><span data-stu-id="841f7-133">Getting Started With WIF</span></span>](../../../docs/framework/security/getting-started-with-wif.md)
