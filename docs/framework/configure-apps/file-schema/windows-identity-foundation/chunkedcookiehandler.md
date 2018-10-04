---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: f5592e0fd02d34b2882182196e0aa9425672a8fe
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244942"
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="8d5cc-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="8d5cc-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="8d5cc-103">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="8d5cc-104">Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element to "Default" lub "Fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="8d5cc-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="8d5cc-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="8d5cc-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="8d5cc-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="8d5cc-106">\<federationConfiguration></span></span>  
<span data-ttu-id="8d5cc-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8d5cc-107">\<cookieHandler></span></span>  
<span data-ttu-id="8d5cc-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8d5cc-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d5cc-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d5cc-109">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d5cc-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="8d5cc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d5cc-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d5cc-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="8d5cc-112">Attributes</span></span>  
  
|<span data-ttu-id="8d5cc-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="8d5cc-113">Attribute</span></span>|<span data-ttu-id="8d5cc-114">Opis</span><span class="sxs-lookup"><span data-stu-id="8d5cc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8d5cc-115">Fragmentu</span><span class="sxs-lookup"><span data-stu-id="8d5cc-115">chunkSize</span></span>|<span data-ttu-id="8d5cc-116">Maksymalny rozmiar w znakach dane pliku cookie HTTP dla dowolnego jednego pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="8d5cc-117">Należy zachować ostrożność podczas dostosowywania rozmiaru fragmentu.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="8d5cc-118">Przeglądarki sieci Web mają różne limity dotyczące rozmiaru plików cookie i liczbę dozwolonych w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="8d5cc-119">Na przykład pierwotną specyfikację Netscape określone limity: łącznie 300 plików cookie, 4096 bajtów na nagłówek cookie (w tym metadane i nie tylko wartości pliku cookie) i 20 plików cookie dla domeny.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="8d5cc-120">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-120">The default is 2000.</span></span> <span data-ttu-id="8d5cc-121">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8d5cc-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="8d5cc-122">Child Elements</span></span>  
 <span data-ttu-id="8d5cc-123">Brak</span><span class="sxs-lookup"><span data-stu-id="8d5cc-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d5cc-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="8d5cc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="8d5cc-125">Element</span><span class="sxs-lookup"><span data-stu-id="8d5cc-125">Element</span></span>|<span data-ttu-id="8d5cc-126">Opis</span><span class="sxs-lookup"><span data-stu-id="8d5cc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d5cc-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="8d5cc-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="8d5cc-128">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używa na odczytywanie i zapisywanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d5cc-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d5cc-129">Remarks</span></span>  
 <span data-ttu-id="8d5cc-130">Po określeniu <xref:System.IdentityModel.Services.ChunkedCookieHandler> , ustawiając `mode` atrybutu `<cookieHandler>` element "Default" lub "Fragmentaryczne", można określić rozmiar fragmentu, używającej obsługi plików cookie na odczytywanie i zapisywanie plików cookie, umieszczając `<chunkedCookieHandler>` element podrzędny i ustawienie jego `chunkSize` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="8d5cc-131">Jeśli `<chunkedCookieHandler>` element nie jest obecny, jest używany domyślny rozmiar fragmentu 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="8d5cc-132">Ten element nie może być określony, gdy `mode` atrybut jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="8d5cc-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="8d5cc-133">`<chunkedCookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5cc-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="8d5cc-134">Example</span></span>  
 <span data-ttu-id="8d5cc-135">Poniższy przykład umożliwia skonfigurowanie plik cookie z podziałem program obsługi, który zapisuje pliki cookie we fragmentach 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="8d5cc-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d5cc-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8d5cc-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
