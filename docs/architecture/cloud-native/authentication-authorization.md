---
title: Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury
description: Projektowanie aplikacji platformy .NET natywnych dla chmury na platformie Azure | Uwierzytelnianie i autoryzacja w aplikacjach natywnych w chmurze
ms.date: 03/02/2020
ms.openlocfilehash: 6261a0a72405bc1c984a04a7851aea4dd6664ddf
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805545"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="ce737-103">Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury</span><span class="sxs-lookup"><span data-stu-id="ce737-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="ce737-104">*Uwierzytelnianie* to proces określania tożsamości podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="ce737-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="ce737-105">*Autoryzacja* jest aktem udzielania uwierzytelnionego uprawnienia głównego do wykonywania akcji lub uzyskiwania dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="ce737-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="ce737-106">Czasami uwierzytelnianie jest `AuthN` skrócone, a `AuthZ`autoryzacja jest skracana do .</span><span class="sxs-lookup"><span data-stu-id="ce737-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="ce737-107">Aplikacje natywne w chmurze muszą polegać na otwartych protokołach opartych na protokole HTTP w celu uwierzytelnienia podmiotów zabezpieczeń, ponieważ zarówno klienci, jak i aplikacje mogą być uruchomione w dowolnym miejscu na świecie na dowolnej platformie lub urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="ce737-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="ce737-108">Jedynym częstym czynnikiem jest HTTP.</span><span class="sxs-lookup"><span data-stu-id="ce737-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="ce737-109">Wiele organizacji nadal korzysta z lokalnych usług uwierzytelniania, takich jak Usługi federacyjne Active Directory (ADFS).</span><span class="sxs-lookup"><span data-stu-id="ce737-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="ce737-110">Chociaż takie podejście tradycyjnie służył organizacjom dobrze na potrzeby uwierzytelniania lokalnego, aplikacje natywne w chmurze korzystają z systemów zaprojektowanych specjalnie dla chmury.</span><span class="sxs-lookup"><span data-stu-id="ce737-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="ce737-111">Niedawne doradztwo Narodowego Centrum Bezpieczeństwa Cybernetycznego (NCSC) 2019 stwierdza, że "organizacje korzystające z usługi Azure AD jako głównego źródła uwierzytelniania faktycznie obniżą swoje ryzyko w porównaniu z usługą ADFS".</span><span class="sxs-lookup"><span data-stu-id="ce737-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="ce737-112">Niektóre powody opisane w [tej analizie](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) obejmują:</span><span class="sxs-lookup"><span data-stu-id="ce737-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="ce737-113">Dostęp do pełnego zestawu technologii ochrony poświadczeń firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ce737-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="ce737-114">Większość organizacji już w pewnym stopniu polega na usłudze Azure AD.</span><span class="sxs-lookup"><span data-stu-id="ce737-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="ce737-115">Podwójne mieszanie skrótów NTLM gwarantuje, że kompromis nie pozwoli na poświadczenia, które działają w lokalnej usłudze Active Directory.</span><span class="sxs-lookup"><span data-stu-id="ce737-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="ce737-116">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="ce737-116">References</span></span>

- [<span data-ttu-id="ce737-117">Podstawowe informacje o uwierzytelnianiu</span><span class="sxs-lookup"><span data-stu-id="ce737-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="ce737-118">Dostęp do tokenów i oświadczeń</span><span class="sxs-lookup"><span data-stu-id="ce737-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="ce737-119">Być może nadszedł czas, aby porzucić usługi uwierzytelniania lokalnego</span><span class="sxs-lookup"><span data-stu-id="ce737-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="ce737-120">[Poprzedni](identity.md)
>[następny](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="ce737-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
