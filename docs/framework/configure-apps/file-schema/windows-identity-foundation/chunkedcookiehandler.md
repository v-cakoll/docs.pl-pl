---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252106"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="d52ca-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="d52ca-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="d52ca-102">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="d52ca-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="d52ca-103">Ten element może być obecny tylko wtedy, `mode` gdy atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="d52ca-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="d52ca-104">[ **\<> konfiguracji**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d52ca-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d52ca-105">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="d52ca-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="d52ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d52ca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="d52ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="d52ca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="d52ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="d52ca-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d52ca-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d52ca-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d52ca-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d52ca-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d52ca-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d52ca-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d52ca-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d52ca-112">Attributes</span></span>  
  
|<span data-ttu-id="d52ca-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d52ca-113">Attribute</span></span>|<span data-ttu-id="d52ca-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d52ca-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d52ca-115">Rozmiaru fragmentu</span><span class="sxs-lookup"><span data-stu-id="d52ca-115">chunkSize</span></span>|<span data-ttu-id="d52ca-116">Maksymalny rozmiar (w znakach) danych plików cookie protokołu HTTP dla dowolnego z plików cookie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d52ca-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="d52ca-117">Należy zachować ostrożność podczas dopasowywania rozmiaru fragmentu.</span><span class="sxs-lookup"><span data-stu-id="d52ca-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="d52ca-118">Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczby dozwolone dla poszczególnych domen.</span><span class="sxs-lookup"><span data-stu-id="d52ca-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="d52ca-119">Na przykład oryginalna Specyfikacja Netscape zaznaczył te limity: 300 plików cookie łącznie, 4096 bajtów na nagłówek pliku cookie (w tym metadane, a nie tylko wartość cookie) oraz 20 plików cookie na domenę.</span><span class="sxs-lookup"><span data-stu-id="d52ca-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="d52ca-120">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="d52ca-120">The default is 2000.</span></span> <span data-ttu-id="d52ca-121">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d52ca-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d52ca-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d52ca-122">Child Elements</span></span>  
 <span data-ttu-id="d52ca-123">Brak</span><span class="sxs-lookup"><span data-stu-id="d52ca-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d52ca-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d52ca-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d52ca-125">Element</span><span class="sxs-lookup"><span data-stu-id="d52ca-125">Element</span></span>|<span data-ttu-id="d52ca-126">Opis</span><span class="sxs-lookup"><span data-stu-id="d52ca-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d52ca-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="d52ca-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="d52ca-128">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> <xref:System.IdentityModel.Services.SessionAuthenticationModule> , że program (sam) używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="d52ca-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d52ca-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d52ca-129">Remarks</span></span>  
 <span data-ttu-id="d52ca-130">W przypadku określenia <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez `mode` ustawienie atrybutu `<cookieHandler>` elementu na "domyślny" lub "podzielony" można określić rozmiar fragmentu, którego program obsługi plików cookie używa `<chunkedCookieHandler>` do odczytu i zapisu plików cookie, włączając element podrzędny i `chunkSize` Ustawianie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d52ca-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="d52ca-131">`<chunkedCookieHandler>` Jeśli element nie jest obecny, używany jest domyślny rozmiar fragmentu wynoszący 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d52ca-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="d52ca-132">Nie można określić tego elementu, `mode` gdy atrybut jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="d52ca-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="d52ca-133">Element jest reprezentowany <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> przez klasę. `<chunkedCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="d52ca-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d52ca-134">Przykład</span><span class="sxs-lookup"><span data-stu-id="d52ca-134">Example</span></span>  
 <span data-ttu-id="d52ca-135">Poniższy przykład służy do konfigurowania programu obsługi plików cookie fragmentarycznego, który zapisuje pliki cookie w fragmentach 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="d52ca-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d52ca-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d52ca-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
