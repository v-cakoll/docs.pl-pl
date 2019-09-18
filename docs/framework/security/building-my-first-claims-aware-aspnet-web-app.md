---
title: Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia
ms.date: 03/30/2017
ms.assetid: 3ee8ee7f-caba-4267-9343-e313fae2876d
author: BrucePerlerMS
ms.openlocfilehash: 900ee49b4bf51eeb6e3b0c0cf6879cc12a0cb071
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045588"
---
# <a name="building-my-first-claims-aware-aspnet-web-application"></a><span data-ttu-id="45622-102">Tworzenie pierwszej aplikacji internetowej ASP.NET obsługującej oświadczenia</span><span class="sxs-lookup"><span data-stu-id="45622-102">Building My First Claims-Aware ASP.NET Web Application</span></span>
## <a name="applies-to"></a><span data-ttu-id="45622-103">Dotyczy:</span><span class="sxs-lookup"><span data-stu-id="45622-103">Applies To</span></span>  
  
- <span data-ttu-id="45622-104">Windows Identity Foundation (WIF)</span><span class="sxs-lookup"><span data-stu-id="45622-104">Windows Identity Foundation (WIF)</span></span>  
  
- <span data-ttu-id="45622-105">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="45622-105">ASP.NET</span></span>  
  
 <span data-ttu-id="45622-106">W tym temacie opisano scenariusz tworzenia przy użyciu programu WIF aplikacji internetowych programu ASP.NET obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="45622-106">This topic outlines the scenario of building claims-aware ASP.NET web applications using WIF.</span></span> <span data-ttu-id="45622-107">W scenariuszu aplikacji obsługującej oświadczenia zazwyczaj uczestniczą trzy strony: sama aplikacja, użytkownik końcowy i usługa tokenu zabezpieczającego (STS).</span><span class="sxs-lookup"><span data-stu-id="45622-107">There are usually three participants in a claims-aware application scenario: the application itself, the end user, and the Security Token Service (STS).</span></span> <span data-ttu-id="45622-108">Następujący rysunek opisuje ten scenariusz:</span><span class="sxs-lookup"><span data-stu-id="45622-108">The following figure describes this scenario:</span></span>  
  
 ![Diagram przedstawiający WIF podstawowe składniki aplikacji sieci Web.](./media/building-my-first-claims-aware-aspnet-web-app/windows-identity-foundation-basic-web-application.gif)  
  
1. <span data-ttu-id="45622-110">Aplikacja obsługująca oświadczenia używa programu WIF do identyfikowania nieuwierzytelnionych żądań i przekierowywania ich do usługi STS.</span><span class="sxs-lookup"><span data-stu-id="45622-110">The claims-aware application uses WIF to identify unauthenticated requests and to redirect them to the STS.</span></span>  
  
2. <span data-ttu-id="45622-111">Użytkownik końcowy podaje poświadczenia usłudze STS i po pomyślnym uwierzytelnieniu usługa STS wystawia mu token.</span><span class="sxs-lookup"><span data-stu-id="45622-111">The end user provides credentials to the STS and upon successful authentication the user is issued a token by the STS.</span></span>  
  
3. <span data-ttu-id="45622-112">Przy użyciu tokenu wystawionego przez usługę STS w żądaniu użytkownik jest przekierowywany z usługi STS do aplikacji obsługującej oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="45622-112">The user is redirected from the STS to the claims-aware application with the STS-issued token in the request.</span></span>  
  
4. <span data-ttu-id="45622-113">Aplikacja obsługująca oświadczenia jest skonfigurowana do ufania usłudze STS i wystawianym przez nią tokenem.</span><span class="sxs-lookup"><span data-stu-id="45622-113">The claims-aware application is configured to trust the STS and the tokens it issues.</span></span> <span data-ttu-id="45622-114">Aplikacja obsługująca oświadczenia używa programu WIF do weryfikacji i analizy tokenu.</span><span class="sxs-lookup"><span data-stu-id="45622-114">The claims-aware application uses WIF to validate the token and to parse it.</span></span> <span data-ttu-id="45622-115">Deweloperzy używają odpowiedniego interfejsu API WIF i typów, na przykład **ClaimsPrincipal** dla potrzeb aplikacji, takich jak implementacja autoryzacji dla tego programu.</span><span class="sxs-lookup"><span data-stu-id="45622-115">Developers use the appropriate WIF API and types, for example, **ClaimsPrincipal** for the application’s needs, such as implementing authorization for it.</span></span>  
  
 <span data-ttu-id="45622-116">Począwszy od platformy .NET 4,5, WIF jest częścią pakietu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="45622-116">Starting from .NET 4.5, WIF is part of the .NET Framework package.</span></span> <span data-ttu-id="45622-117">Posiadanie klas WIF bezpośrednio dostępnych w ramach platformy pozwala znacznie lepiej przeprowadzić integrację tożsamości opartej na oświadczeniach w programie .NET, ułatwiając korzystanie z oświadczeń.</span><span class="sxs-lookup"><span data-stu-id="45622-117">Having the WIF classes directly available in the framework allows a much deeper integration of claims-based identity in .NET, making it easier to use claims.</span></span> <span data-ttu-id="45622-118">Mając program WIF 4.5, nie trzeba instalować żadnych składników zewnętrznych, aby rozpocząć projektowanie aplikacji internetowych obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="45622-118">With WIF 4.5, you do not need to install any out-of-band components in order to start developing claims-aware web applications.</span></span> <span data-ttu-id="45622-119">Klasy programu WIF rozciągają się obecnie na rozmaite zestawy, z których najważniejsze to System.Security.Claims, System.IdentityModel i System.IdentityModel.Services.</span><span class="sxs-lookup"><span data-stu-id="45622-119">WIF classes are now spread across various assemblies, the main ones being System.Security.Claims, System.IdentityModel and System.IdentityModel.Services.</span></span>  
  
 <span data-ttu-id="45622-120">STS to usługa, która wystawia tokeny po pomyślnym uwierzytelnieniu.</span><span class="sxs-lookup"><span data-stu-id="45622-120">STS is a service that issues tokens upon successful authentication.</span></span> <span data-ttu-id="45622-121">Firma Microsoft oferuje dwie usługi STS będące standardami branżowymi:</span><span class="sxs-lookup"><span data-stu-id="45622-121">Microsoft offers two industry standard STS’s:</span></span>  
  
- [<span data-ttu-id="45622-122">Active Directory Federation Services (AD FS) 2.0</span><span class="sxs-lookup"><span data-stu-id="45622-122">Active Directory Federation Services (AD FS) 2.0</span></span>](https://go.microsoft.com/fwlink/?LinkID=247516)
  
- [<span data-ttu-id="45622-123">Access Control Service systemu Windows Azure (ACS)</span><span class="sxs-lookup"><span data-stu-id="45622-123">Windows Azure Access Control Service (ACS)</span></span>](https://go.microsoft.com/fwlink/?LinkID=247517)
  
 <span data-ttu-id="45622-124">Usługa AD FS 2.0 jest częścią systemu Windows Server R2 i może służyć jako usługa STS w scenariuszach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="45622-124">AD FS 2.0 is part of the Windows Server R2 and can be used as an STS for on-premise scenarios.</span></span> <span data-ttu-id="45622-125">ACS to usługa w chmurze oferowana jako część platformy Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="45622-125">ACS is a cloud service, offered as part of the Windows Azure Platform.</span></span> <span data-ttu-id="45622-126">Na potrzeby testowania lub w celach edukacyjnych można również używać innych usług STS do tworzenia aplikacji obsługujących oświadczenia.</span><span class="sxs-lookup"><span data-stu-id="45622-126">For testing or educational purposes, you can also use other STS’s in order to build your claims-aware applications.</span></span> <span data-ttu-id="45622-127">Można na przykład użyć lokalnego programu STS do tworzenia [tożsamości i narzędzia dostępu dla programu Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) , co jest dostępne w trybie online.</span><span class="sxs-lookup"><span data-stu-id="45622-127">For example, you can use the Local Development STS that is part of the [Identity and Access Tool for Visual Studio](https://go.microsoft.com/fwlink/?LinkID=245849) which is freely available online.</span></span>  
  
 <span data-ttu-id="45622-128">Aby przy użyciu programu WIF utworzyć swoją pierwszą aplikację programu ASP.NET obsługującą oświadczenia, postępuj zgodnie z instrukcjami podanymi w jednym z następujących tematów:</span><span class="sxs-lookup"><span data-stu-id="45622-128">To build your first claims-aware ASP.NET application using WIF, follow the instructions in one of the following:</span></span>  
  
- [<span data-ttu-id="45622-129">Instrukcje: Tworzenie aplikacji sieci Web ASP.NET MVC z obsługą oświadczeń przy użyciu WIF</span><span class="sxs-lookup"><span data-stu-id="45622-129">How To: Build Claims-Aware ASP.NET MVC Web Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-mvc-web-app-using-wif.md)  
  
- [<span data-ttu-id="45622-130">Instrukcje: Tworzenie aplikacji opartych na oświadczeniach ASP.NET Web Forms przy użyciu WIF</span><span class="sxs-lookup"><span data-stu-id="45622-130">How To: Build Claims-Aware ASP.NET Web Forms Application Using WIF</span></span>](how-to-build-claims-aware-aspnet-web-forms-app-using-wif.md)  
  
- [<span data-ttu-id="45622-131">Instrukcje: Tworzenie aplikacji ASP.NET obsługującej oświadczenia przy użyciu uwierzytelniania opartego na formularzach</span><span class="sxs-lookup"><span data-stu-id="45622-131">How To: Build Claims-Aware ASP.NET Application Using Forms-Based Authentication</span></span>](claims-aware-aspnet-app-forms-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="45622-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="45622-132">See also</span></span>

- [<span data-ttu-id="45622-133">Wprowadzenie do korzystania z programu WIF</span><span class="sxs-lookup"><span data-stu-id="45622-133">Getting Started With WIF</span></span>](getting-started-with-wif.md)
