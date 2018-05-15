---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 193b783e44fe4386d3575e180dc5baa6a7f9a8be
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="bac2f-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="bac2f-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="bac2f-103">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="bac2f-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="bac2f-104">Ten element może być tylko obecny Jeśli `mode` atrybutu `<cookieHandler>` jest element "Default" lub "Fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="bac2f-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="bac2f-105">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="bac2f-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="bac2f-106">\<federationConfiguration ></span><span class="sxs-lookup"><span data-stu-id="bac2f-106">\<federationConfiguration></span></span>  
<span data-ttu-id="bac2f-107">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bac2f-107">\<cookieHandler></span></span>  
<span data-ttu-id="bac2f-108">\<chunkedCookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bac2f-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bac2f-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="bac2f-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bac2f-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="bac2f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bac2f-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="bac2f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bac2f-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="bac2f-112">Attributes</span></span>  
  
|<span data-ttu-id="bac2f-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="bac2f-113">Attribute</span></span>|<span data-ttu-id="bac2f-114">Opis</span><span class="sxs-lookup"><span data-stu-id="bac2f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bac2f-115">niż rozmiar segmentu</span><span class="sxs-lookup"><span data-stu-id="bac2f-115">chunkSize</span></span>|<span data-ttu-id="bac2f-116">Maksymalny rozmiar w znakach dane pliku cookie HTTP dla dowolnego jednego pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="bac2f-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="bac2f-117">Należy zachować ostrożność podczas dostosowywania rozmiar fragmentu.</span><span class="sxs-lookup"><span data-stu-id="bac2f-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="bac2f-118">Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczbę dozwolonych dla jednej domeny.</span><span class="sxs-lookup"><span data-stu-id="bac2f-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="bac2f-119">Na przykład pierwotnej specyfikacji Netscape określone te limity: łączna liczba 300 plików cookie, 4096 bajtów na nagłówek cookie (w tym metadane, nie tylko wartości pliku cookie) i 20 plików cookie dla domeny.</span><span class="sxs-lookup"><span data-stu-id="bac2f-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="bac2f-120">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="bac2f-120">The default is 2000.</span></span> <span data-ttu-id="bac2f-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="bac2f-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bac2f-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="bac2f-122">Child Elements</span></span>  
 <span data-ttu-id="bac2f-123">Brak</span><span class="sxs-lookup"><span data-stu-id="bac2f-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bac2f-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="bac2f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="bac2f-125">Element</span><span class="sxs-lookup"><span data-stu-id="bac2f-125">Element</span></span>|<span data-ttu-id="bac2f-126">Opis</span><span class="sxs-lookup"><span data-stu-id="bac2f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bac2f-127">\<cookieHandler ></span><span class="sxs-lookup"><span data-stu-id="bac2f-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="bac2f-128">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> który <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używany do odczytywania i zapisywania plików cookie.</span><span class="sxs-lookup"><span data-stu-id="bac2f-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bac2f-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bac2f-129">Remarks</span></span>  
 <span data-ttu-id="bac2f-130">Po określeniu <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez ustawienie `mode` atrybutu `<cookieHandler>` element "Default" lub "Fragmentaryczne", można określić rozmiar fragmentu, używaną do odczytu i zapisu plików cookie przez dołączenie obsługi plików cookie `<chunkedCookieHandler>` element podrzędny i ustawienie jej `chunkSize` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bac2f-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="bac2f-131">Jeśli `<chunkedCookieHandler>` element nie jest obecny, jest używany domyślny rozmiar fragmentu 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="bac2f-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="bac2f-132">Ten element nie może być określona gdy `mode` atrybut jest ustawiony na "Custom".</span><span class="sxs-lookup"><span data-stu-id="bac2f-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="bac2f-133">`<chunkedCookieHandler>` Reprezentowany przez element <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="bac2f-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bac2f-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="bac2f-134">Example</span></span>  
 <span data-ttu-id="bac2f-135">Poniższy przykład służy do konfigurowania obsługi podzielony plik cookie, który zapisuje pliki cookie w fragmentów 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="bac2f-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bac2f-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bac2f-136">See Also</span></span>  
 <xref:System.IdentityModel.Services.ChunkedCookieHandler>
