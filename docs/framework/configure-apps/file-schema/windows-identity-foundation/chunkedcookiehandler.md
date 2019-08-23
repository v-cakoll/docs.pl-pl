---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941890"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="4df0e-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="4df0e-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="4df0e-102">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="4df0e-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="4df0e-103">Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="4df0e-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="4df0e-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="4df0e-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="4df0e-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="4df0e-105">\<federationConfiguration></span></span>  
<span data-ttu-id="4df0e-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="4df0e-106">\<cookieHandler></span></span>  
<span data-ttu-id="4df0e-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="4df0e-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df0e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="4df0e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4df0e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4df0e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4df0e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4df0e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4df0e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4df0e-111">Attributes</span></span>  
  
|<span data-ttu-id="4df0e-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="4df0e-112">Attribute</span></span>|<span data-ttu-id="4df0e-113">Opis</span><span class="sxs-lookup"><span data-stu-id="4df0e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4df0e-114">Rozmiaru fragmentu</span><span class="sxs-lookup"><span data-stu-id="4df0e-114">chunkSize</span></span>|<span data-ttu-id="4df0e-115">Maksymalny rozmiar (w znakach) danych plików cookie protokołu HTTP dla dowolnego z plików cookie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4df0e-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="4df0e-116">Należy zachować ostrożność podczas dopasowywania rozmiaru fragmentu.</span><span class="sxs-lookup"><span data-stu-id="4df0e-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="4df0e-117">Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczby dozwolone dla poszczególnych domen.</span><span class="sxs-lookup"><span data-stu-id="4df0e-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="4df0e-118">Na przykład oryginalna Specyfikacja Netscape zaznaczył te limity: 300 plików cookie łącznie, 4096 bajtów na nagłówek pliku cookie (w tym metadane, a nie tylko wartość cookie) oraz 20 plików cookie na domenę.</span><span class="sxs-lookup"><span data-stu-id="4df0e-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="4df0e-119">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="4df0e-119">The default is 2000.</span></span> <span data-ttu-id="4df0e-120">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="4df0e-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4df0e-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4df0e-121">Child Elements</span></span>  
 <span data-ttu-id="4df0e-122">Brak</span><span class="sxs-lookup"><span data-stu-id="4df0e-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4df0e-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4df0e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="4df0e-124">Element</span><span class="sxs-lookup"><span data-stu-id="4df0e-124">Element</span></span>|<span data-ttu-id="4df0e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="4df0e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4df0e-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="4df0e-126">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="4df0e-127">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , że program (sam) używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="4df0e-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df0e-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4df0e-128">Remarks</span></span>  
 <span data-ttu-id="4df0e-129">W przypadku określenia <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez `mode` ustawienie atrybutu `<cookieHandler>` elementu na "domyślny" lub "podzielony" można określić rozmiar fragmentu, którego program obsługi plików cookie używa `<chunkedCookieHandler>` do odczytu i zapisu plików cookie, włączając element podrzędny i `chunkSize` Ustawianie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="4df0e-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="4df0e-130">`<chunkedCookieHandler>` Jeśli element nie jest obecny, używany jest domyślny rozmiar fragmentu wynoszący 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="4df0e-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="4df0e-131">Nie można określić tego elementu, `mode` gdy atrybut jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="4df0e-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="4df0e-132">Element jest reprezentowany <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> przez klasę. `<chunkedCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="4df0e-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df0e-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="4df0e-133">Example</span></span>  
 <span data-ttu-id="4df0e-134">Poniższy przykład służy do konfigurowania programu obsługi plików cookie fragmentarycznego, który zapisuje pliki cookie w fragmentach 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="4df0e-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4df0e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4df0e-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
