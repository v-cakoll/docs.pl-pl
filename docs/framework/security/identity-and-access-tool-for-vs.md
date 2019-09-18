---
title: Narzędzie tożsamości i dostępu dla programu Visual Studio 2012
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: d58cca13dc3ac67742e5371aed628a6a680e61e1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045414"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a><span data-ttu-id="cdd6d-102">Narzędzie tożsamości i dostępu dla programu Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="cdd6d-102">Identity and Access Tool for Visual Studio 2012</span></span>
<span data-ttu-id="cdd6d-103">W tym temacie opisano nowe narzędzie tożsamości i dostępu dla programu Visual Studio 11.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-103">This topic describes the new Identity and Access Tool for Visual Studio 11.</span></span> <span data-ttu-id="cdd6d-104">Możesz pobrać to narzędzie z następującego adresu URL: <https://go.microsoft.com/fwlink/?LinkID=245849> lub bezpośrednio z programu Visual Studio 11, wyszukując frazę "Identity" bezpośrednio w Menedżerze rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-104">You can download this tool from the following URL: <https://go.microsoft.com/fwlink/?LinkID=245849> or directly from within Visual Studio 11 by searching for "identity" directly in the Extensions Manager.</span></span>  
  
 <span data-ttu-id="cdd6d-105">Narzędzie tożsamości i dostępu dla programu Visual Studio 11 znacznie upraszcza projektowanie aplikacji dzięki następującym głównym funkcjom:</span><span class="sxs-lookup"><span data-stu-id="cdd6d-105">The Identity and Access Tool for Visual Studio 11 delivers a dramatically simplified development-time experience with the following highlights:</span></span>  
  
- <span data-ttu-id="cdd6d-106">Za pomocą tego nowego narzędzia możesz tworzyć aplikacje przy użyciu typów projektów aplikacji internetowych i szybko integrować je z programem IIS.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-106">Using the new tool, you can develop using web applications project types and target IIS express.</span></span>  
  
- <span data-ttu-id="cdd6d-107">W odróżnieniu od uwierzytelniania mającego zapewnić samą ochronę, za pomocą tego nowego narzędzia możesz określić stronę wykrywania/kontroler w lokalnym obszarze głównym (lub dowolny inny punkt końcowy obsługujący uwierzytelnianie w aplikacji), a program WIF skonfiguruje wszystkie nieuwierzytelnione żądania do docierania tam zamiast przekierowywać je do usługi STS.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-107">Unlike with the blanket protection-only authentication, with the new tool, you can specify your local home realm discovery page/controller (or any other endpoint handling the authentication experience within your application) and WIF will configure all unauthenticated requests to go there, instead of redirecting them to the STS.</span></span>  
  
- <span data-ttu-id="cdd6d-108">To narzędzie zawiera usługę tokenu zabezpieczającego (STS), która jest uruchamiana na komputerze lokalnym z chwilą rozpoczęcia sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-108">The tool includes a test Security Token Service (STS) which runs on your local machine when you launch a debug session.</span></span> <span data-ttu-id="cdd6d-109">W związku z tym nie musisz już tworzyć niestandardowych projektów usługi STS i dostosowywać ich w celu uzyskania oświadczeń potrzebnych do testowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-109">Therefore, you no longer need to create custom STS projects and tweak them in order to get the claims you need to test your applications.</span></span> <span data-ttu-id="cdd6d-110">Typy i wartości oświadczeń są w pełni konfigurowalne.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-110">The claim types and values are fully customizable.</span></span>  
  
- <span data-ttu-id="cdd6d-111">Typowe ustawienia możesz modyfikować bezpośrednio za pośrednictwem interfejsu użytkownika tego narzędzia, bez konieczności modyfikowania pliku web.config.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-111">You can modify common settings directly via the tool’s UI, without the need to edit web.config.</span></span>  
  
- <span data-ttu-id="cdd6d-112">Za pomocą jednego ekranu możesz ustanowić federację z usługą Active Directory Federation Services (AD FS) 2.0 (lub innymi dostawcami protokołu WS-Federation).</span><span class="sxs-lookup"><span data-stu-id="cdd6d-112">You can establish federation with Active Directory Federation Services (AD FS) 2.0 (or other WS-Federation providers) in a single screen.</span></span>  
  
- <span data-ttu-id="cdd6d-113">Narzędzie korzysta z możliwości usługi Microsoft Azure Access Control Service (ACS) z prostą listą pól wyboru dla wszystkich dostawców tożsamości, których chcesz użyć: Facebook, Google, Live ID, Yahoo!, dowolny dostawca OpenID Connect i dowolny Dostawca usługi WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-113">The tool leverages Windows Azure Access Control Service (ACS) capabilities with a simple list of checkboxes for all the identity providers that you want to use: Facebook, Google, Live ID, Yahoo!, any OpenID provider, and any WS-Federation provider.</span></span> <span data-ttu-id="cdd6d-114">Wybierz swoich dostawców tożsamości, kliknij przycisk OK, a następnie naciśnij klawisz F5, i aplikacja i usługa ACS zostaną automatycznie skonfigurowane, a aplikacja testowa będzie obsługiwać usługę ACS.</span><span class="sxs-lookup"><span data-stu-id="cdd6d-114">Select your identity providers, click OK, then F5, and both your application and ACS will be automatically configured and your test application will be ACS-aware.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd6d-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdd6d-115">See also</span></span>

- [<span data-ttu-id="cdd6d-116">Funkcje programu WIF</span><span class="sxs-lookup"><span data-stu-id="cdd6d-116">WIF Features</span></span>](wif-features.md)
