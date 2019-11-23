---
title: Uwierzytelnianie i autoryzacja w aplikacjach natywnych w chmurze
description: Tworzenie architektury natywnych aplikacji .NET w chmurze dla platformy Azure | Uwierzytelnianie i autoryzacja w natywnych aplikacjach w chmurze
ms.date: 06/30/2019
ms.openlocfilehash: a397175e98c2e8103d2a8c372c81fcca65f19b11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183729"
---
# <a name="authentication-and-authorization-in-cloud-native-apps"></a><span data-ttu-id="0e247-103">Uwierzytelnianie i autoryzacja w aplikacjach natywnych dla chmury</span><span class="sxs-lookup"><span data-stu-id="0e247-103">Authentication and authorization in cloud-native apps</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="0e247-104">*Uwierzytelnianie* to proces określania tożsamości podmiotu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="0e247-104">*Authentication* is the process of determining the identity of a security principal.</span></span> <span data-ttu-id="0e247-105">*Autoryzacja* to czynność udzielenia uwierzytelnionego uprawnienia podmiotowi do wykonania akcji lub uzyskania dostępu do zasobu.</span><span class="sxs-lookup"><span data-stu-id="0e247-105">*Authorization* is the act of granting an authenticated principal permission to perform an action or access a resource.</span></span> <span data-ttu-id="0e247-106">Czasami uwierzytelnianie jest skracane do `AuthN` a Autoryzacja jest skracana do `AuthZ`.</span><span class="sxs-lookup"><span data-stu-id="0e247-106">Sometimes authentication is shortened to `AuthN` and authorization is shortened to `AuthZ`.</span></span> <span data-ttu-id="0e247-107">Aplikacje natywne w chmurze muszą polegać na otwartych protokołach opartych na protokole HTTP w celu uwierzytelniania podmiotów zabezpieczeń, ponieważ zarówno klienci, jak i aplikacje mogą działać w dowolnym miejscu na świecie na dowolnej platformie lub urządzeniu.</span><span class="sxs-lookup"><span data-stu-id="0e247-107">Cloud-native applications need to rely on open HTTP-based protocols to authenticate security principals since both clients and applications could be running anywhere in the world on any platform or device.</span></span> <span data-ttu-id="0e247-108">Jedynym wspólnym czynnikiem jest protokół HTTP.</span><span class="sxs-lookup"><span data-stu-id="0e247-108">The only common factor is HTTP.</span></span>

<span data-ttu-id="0e247-109">W wielu organizacjach nadal opierają się lokalne usługi uwierzytelniania, takie jak Active Directory Federation Services (AD FS).</span><span class="sxs-lookup"><span data-stu-id="0e247-109">Many organizations still rely on local authentication services like Active Directory Federation Services (ADFS).</span></span> <span data-ttu-id="0e247-110">Chociaż ta metoda ma tradycyjnie obsługiwane organizacje dotyczące lokalnych potrzeb związanych z uwierzytelnianiem, aplikacje natywne dla chmury korzystają z systemów zaprojektowanych specjalnie dla chmury.</span><span class="sxs-lookup"><span data-stu-id="0e247-110">While this approach has traditionally served organizations well for on premises authentication needs, cloud-native applications benefit from systems designed specifically for the cloud.</span></span> <span data-ttu-id="0e247-111">W ostatnim 2019 w Zjednoczonym Królestwie National cybernetycznymi Security Centre (NCSC) poradnik "Organizacje korzystające z usługi Azure AD jako podstawowego źródła uwierzytelniania" w rzeczywistości obniżą ryzyko w porównaniu z usługami ADFS ".</span><span class="sxs-lookup"><span data-stu-id="0e247-111">A recent 2019 United Kingdom National Cyber Security Centre (NCSC) advisory states that "organizations using Azure AD as their primary authentication source will actually lower their risk compared to ADFS."</span></span> <span data-ttu-id="0e247-112">Niektóre przyczyny przedstawione w [tej analizie](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) obejmują:</span><span class="sxs-lookup"><span data-stu-id="0e247-112">Some reasons outlined in [this analysis](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/) include:</span></span>

- <span data-ttu-id="0e247-113">Dostęp do pełnego zestawu technologii ochrony poświadczeń firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0e247-113">Access to full set of Microsoft credential protection technologies.</span></span>
- <span data-ttu-id="0e247-114">Większość organizacji korzysta już z usługi Azure AD w pewnym zakresie.</span><span class="sxs-lookup"><span data-stu-id="0e247-114">Most organizations are already relying on Azure AD to some extent.</span></span>
- <span data-ttu-id="0e247-115">Podwójne mieszanie skrótów NTLM gwarantuje naruszenie nie będzie zezwalać na poświadczenia, które działają w lokalnym Active Directory.</span><span class="sxs-lookup"><span data-stu-id="0e247-115">Double hashing of NTLM hashes ensures compromise won't allow credentials that work in local Active Directory.</span></span>

## <a name="references"></a><span data-ttu-id="0e247-116">Odwołania</span><span class="sxs-lookup"><span data-stu-id="0e247-116">References</span></span>

- [<span data-ttu-id="0e247-117">Podstawowe informacje o uwierzytelnianiu</span><span class="sxs-lookup"><span data-stu-id="0e247-117">Authentication basics</span></span>](https://docs.microsoft.com/azure/active-directory/develop/authentication-scenarios)
- [<span data-ttu-id="0e247-118">Tokeny dostępu i oświadczenia</span><span class="sxs-lookup"><span data-stu-id="0e247-118">Access tokens and claims</span></span>](https://docs.microsoft.com/azure/active-directory/develop/access-tokens)
- [<span data-ttu-id="0e247-119">Zrezygnować usług uwierzytelniania lokalnego może być czasochłonne</span><span class="sxs-lookup"><span data-stu-id="0e247-119">It may be time to ditch your on premises authentication services</span></span>](https://oxfordcomputergroup.com/resources/o365-security-native-cloud-authentication/)

>[!div class="step-by-step"]
><span data-ttu-id="0e247-120">[Poprzedni](identity.md)
>[Następny](azure-active-directory.md)</span><span class="sxs-lookup"><span data-stu-id="0e247-120">[Previous](identity.md)
[Next](azure-active-directory.md)</span></span>
