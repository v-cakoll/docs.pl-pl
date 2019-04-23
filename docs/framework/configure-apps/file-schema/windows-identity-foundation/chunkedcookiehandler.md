---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120786"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="73b75-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="73b75-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="73b75-102">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="73b75-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="73b75-103">Ten element może być tylko obecne Jeśli `mode` atrybutu `<cookieHandler>` element to "Default" lub "Fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="73b75-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="73b75-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="73b75-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="73b75-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="73b75-105">\<federationConfiguration></span></span>  
<span data-ttu-id="73b75-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="73b75-106">\<cookieHandler></span></span>  
<span data-ttu-id="73b75-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="73b75-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b75-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="73b75-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73b75-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="73b75-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73b75-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="73b75-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73b75-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="73b75-111">Attributes</span></span>  
  
|<span data-ttu-id="73b75-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="73b75-112">Attribute</span></span>|<span data-ttu-id="73b75-113">Opis</span><span class="sxs-lookup"><span data-stu-id="73b75-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73b75-114">chunkSize</span><span class="sxs-lookup"><span data-stu-id="73b75-114">chunkSize</span></span>|<span data-ttu-id="73b75-115">Maksymalny rozmiar w znakach dane pliku cookie HTTP dla dowolnego jednego pliku cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="73b75-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="73b75-116">Należy zachować ostrożność podczas dostosowywania rozmiaru fragmentu.</span><span class="sxs-lookup"><span data-stu-id="73b75-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="73b75-117">Przeglądarki sieci Web mają różne limity dotyczące rozmiaru plików cookie i liczbę dozwolonych w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="73b75-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="73b75-118">Na przykład pierwotną specyfikację Netscape określone limity: Łączna liczba plików cookie 300, 4096 bajtów na nagłówek cookie (w tym metadane i nie tylko wartości pliku cookie) i 20 plików cookie dla domeny.</span><span class="sxs-lookup"><span data-stu-id="73b75-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="73b75-119">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="73b75-119">The default is 2000.</span></span> <span data-ttu-id="73b75-120">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="73b75-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73b75-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="73b75-121">Child Elements</span></span>  
 <span data-ttu-id="73b75-122">Brak</span><span class="sxs-lookup"><span data-stu-id="73b75-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73b75-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="73b75-123">Parent Elements</span></span>  
  
|<span data-ttu-id="73b75-124">Element</span><span class="sxs-lookup"><span data-stu-id="73b75-124">Element</span></span>|<span data-ttu-id="73b75-125">Opis</span><span class="sxs-lookup"><span data-stu-id="73b75-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73b75-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="73b75-126">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="73b75-127">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) używa na odczytywanie i zapisywanie plików cookie.</span><span class="sxs-lookup"><span data-stu-id="73b75-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73b75-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="73b75-128">Remarks</span></span>  
 <span data-ttu-id="73b75-129">Po określeniu <xref:System.IdentityModel.Services.ChunkedCookieHandler> , ustawiając `mode` atrybutu `<cookieHandler>` element "Default" lub "Fragmentaryczne", można określić rozmiar fragmentu, używającej obsługi plików cookie na odczytywanie i zapisywanie plików cookie, umieszczając `<chunkedCookieHandler>` element podrzędny i ustawienie jego `chunkSize` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="73b75-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="73b75-130">Jeśli `<chunkedCookieHandler>` element nie jest obecny, jest używany domyślny rozmiar fragmentu 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="73b75-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="73b75-131">Ten element nie może być określony, gdy `mode` atrybut jest ustawiony na "Niestandardowe".</span><span class="sxs-lookup"><span data-stu-id="73b75-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="73b75-132">`<chunkedCookieHandler>` Element jest reprezentowany przez <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="73b75-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73b75-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="73b75-133">Example</span></span>  
 <span data-ttu-id="73b75-134">Poniższy przykład umożliwia skonfigurowanie plik cookie z podziałem program obsługi, który zapisuje pliki cookie we fragmentach 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="73b75-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="73b75-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73b75-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
