---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252106"
---
# \<chunkedCookieHandler>
<span data-ttu-id="b34f7-101">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="b34f7-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="b34f7-102">Ten element może być obecny tylko wtedy, gdy `mode` atrybut `<cookieHandler>` elementu ma wartość "default" lub "fragmentaryczne".</span><span class="sxs-lookup"><span data-stu-id="b34f7-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="b34f7-103">Składnia</span><span class="sxs-lookup"><span data-stu-id="b34f7-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b34f7-104">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b34f7-104">Attributes and Elements</span></span>  
 <span data-ttu-id="b34f7-105">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b34f7-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b34f7-106">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b34f7-106">Attributes</span></span>  
  
|<span data-ttu-id="b34f7-107">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b34f7-107">Attribute</span></span>|<span data-ttu-id="b34f7-108">Opis</span><span class="sxs-lookup"><span data-stu-id="b34f7-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b34f7-109">Rozmiaru fragmentu</span><span class="sxs-lookup"><span data-stu-id="b34f7-109">chunkSize</span></span>|<span data-ttu-id="b34f7-110">Maksymalny rozmiar (w znakach) danych plików cookie protokołu HTTP dla dowolnego z plików cookie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b34f7-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="b34f7-111">Należy zachować ostrożność podczas dopasowywania rozmiaru fragmentu.</span><span class="sxs-lookup"><span data-stu-id="b34f7-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="b34f7-112">Przeglądarki sieci Web mają różne limity rozmiaru plików cookie i liczby dozwolone dla poszczególnych domen.</span><span class="sxs-lookup"><span data-stu-id="b34f7-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="b34f7-113">Na przykład oryginalna Specyfikacja programu Netscape zakłada następujące limity: 300 plików cookie łącznie, 4096 bajtów na nagłówek pliku cookie (w tym metadanych, a nie tylko wartość cookie) oraz 20 plików cookie na domenę.</span><span class="sxs-lookup"><span data-stu-id="b34f7-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="b34f7-114">Wartość domyślna to 2000.</span><span class="sxs-lookup"><span data-stu-id="b34f7-114">The default is 2000.</span></span> <span data-ttu-id="b34f7-115">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b34f7-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b34f7-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b34f7-116">Child Elements</span></span>  
 <span data-ttu-id="b34f7-117">Brak</span><span class="sxs-lookup"><span data-stu-id="b34f7-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b34f7-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b34f7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b34f7-119">Element</span><span class="sxs-lookup"><span data-stu-id="b34f7-119">Element</span></span>|<span data-ttu-id="b34f7-120">Opis</span><span class="sxs-lookup"><span data-stu-id="b34f7-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="b34f7-121">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , że program <xref:System.IdentityModel.Services.SessionAuthenticationModule> (sam) używa do odczytu i zapisu plików cookie.</span><span class="sxs-lookup"><span data-stu-id="b34f7-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b34f7-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b34f7-122">Remarks</span></span>  
 <span data-ttu-id="b34f7-123">W przypadku określenia <xref:System.IdentityModel.Services.ChunkedCookieHandler> przez ustawienie `mode` atrybutu `<cookieHandler>` elementu na "domyślny" lub "podzielony" można określić rozmiar fragmentu, którego program obsługi plików cookie używa do odczytu i zapisu plików cookie, dołączając `<chunkedCookieHandler>` element podrzędny i ustawiając jego `chunkSize` atrybut.</span><span class="sxs-lookup"><span data-stu-id="b34f7-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="b34f7-124">Jeśli `<chunkedCookieHandler>` element nie jest obecny, używany jest domyślny rozmiar fragmentu wynoszący 2000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b34f7-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="b34f7-125">Nie można określić tego elementu, gdy `mode` atrybut jest ustawiony na wartość "Custom".</span><span class="sxs-lookup"><span data-stu-id="b34f7-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="b34f7-126">`<chunkedCookieHandler>`Element jest reprezentowany przez <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> klasę.</span><span class="sxs-lookup"><span data-stu-id="b34f7-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b34f7-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="b34f7-127">Example</span></span>  
 <span data-ttu-id="b34f7-128">Poniższy przykład służy do konfigurowania programu obsługi plików cookie fragmentarycznego, który zapisuje pliki cookie w fragmentach 3000 bajtów.</span><span class="sxs-lookup"><span data-stu-id="b34f7-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b34f7-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b34f7-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>
