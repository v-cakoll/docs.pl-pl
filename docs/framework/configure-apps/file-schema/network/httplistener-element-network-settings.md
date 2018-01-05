---
title: '&lt;httpListener&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8d880583016e6ccc0ae57fea10c35cb32726c93e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lthttplistenergt-element-network-settings"></a><span data-ttu-id="46ef6-102">&lt;httpListener&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="46ef6-102">&lt;httpListener&gt; Element (Network Settings)</span></span>
<span data-ttu-id="46ef6-103">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="46ef6-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="46ef6-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="46ef6-104">\<configuration></span></span>  
<span data-ttu-id="46ef6-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="46ef6-105">\<system.net></span></span>  
<span data-ttu-id="46ef6-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="46ef6-106">\<settings></span></span>  
<span data-ttu-id="46ef6-107">\<httpListener ></span><span class="sxs-lookup"><span data-stu-id="46ef6-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46ef6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="46ef6-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="46ef6-109">Typ</span><span class="sxs-lookup"><span data-stu-id="46ef6-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46ef6-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="46ef6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="46ef6-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="46ef6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46ef6-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="46ef6-112">Attributes</span></span>  
  
|<span data-ttu-id="46ef6-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="46ef6-113">Attribute</span></span>|<span data-ttu-id="46ef6-114">Opis</span><span class="sxs-lookup"><span data-stu-id="46ef6-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46ef6-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="46ef6-115">unescapeRequestUrl</span></span>|<span data-ttu-id="46ef6-116">Wartość logiczna, która wskazuje, czy <xref:System.Net.HttpListener> wystąpienie korzysta raw URI niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46ef6-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="46ef6-117">Child Elements</span></span>  
 <span data-ttu-id="46ef6-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="46ef6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46ef6-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="46ef6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="46ef6-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="46ef6-120">**Element**</span></span>|<span data-ttu-id="46ef6-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="46ef6-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="46ef6-122">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="46ef6-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="46ef6-123">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="46ef6-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46ef6-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46ef6-124">Remarks</span></span>  
 <span data-ttu-id="46ef6-125">**UnescapeRequestUrl** atrybut wskazuje, czy <xref:System.Net.HttpListener> używa raw URI niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI, gdzie wartości procent, kodowane są konwertowane, i są pobierane z procedurą normalizacji.</span><span class="sxs-lookup"><span data-stu-id="46ef6-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="46ef6-126">Gdy <xref:System.Net.HttpListener> wystąpienia odbiera żądanie za pośrednictwem `http.sys` usługi, tworzy wystąpienie ciągu identyfikatora URI dostarczonych przez `http.sys`i uwidacznia go jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="46ef6-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="46ef6-127">`http.sys` Usługi udostępnia dwa ciągi identyfikatora URI żądania:</span><span class="sxs-lookup"><span data-stu-id="46ef6-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="46ef6-128">Nieprzetworzona identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-128">Raw URI</span></span>  
  
-   <span data-ttu-id="46ef6-129">Przekonwertowana identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-129">Converted URI</span></span>  
  
 <span data-ttu-id="46ef6-130">Nieprzetworzona identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> dostępne w wierszu żądania HTTP żądania:</span><span class="sxs-lookup"><span data-stu-id="46ef6-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="46ef6-131">Nieprzetworzone udostępniane przez identyfikator URI `http.sys` dla żądania wymienionych powyżej, jest "/ path /".</span><span class="sxs-lookup"><span data-stu-id="46ef6-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="46ef6-132">Reprezentuje ciąg następujący zlecenie HTTP, jak została wysłana przez sieć.</span><span class="sxs-lookup"><span data-stu-id="46ef6-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="46ef6-133">`http.sys` Usługi tworzy przekonwertowanego identyfikatora URI na podstawie informacji dostępnych w żądaniu za pomocą identyfikatora URI, dostępne w wierszu żądania HTTP i powinny zostać przekazane nagłówek hosta, aby określić serwer pochodzenia żądania.</span><span class="sxs-lookup"><span data-stu-id="46ef6-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="46ef6-134">Jest to realizowane przez porównanie informacji z żądania z zestawem zarejestrowanych prefiksów identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="46ef6-135">W dokumentacji zestawu SDK serwera HTTP odwołuje się do tego przekonwertowanego identyfikatora URI jako struktura HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="46ef6-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="46ef6-136">Aby można było porównać żądanie z zarejestrowanych prefiksów identyfikatorów URI, należy jednak wykonać niektóre normalizacji na żądanie.</span><span class="sxs-lookup"><span data-stu-id="46ef6-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="46ef6-137">Dla przykładu powyżej przekonwertowanego identyfikator URI będzie w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="46ef6-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="46ef6-138">`http.sys` Usługi łączy <xref:System.Uri.Host%2A?displayProperty=nameWithType> wartość właściwości i ciąg w wierszu żądania do utworzenia przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="46ef6-139">Ponadto `http.sys` i <xref:System.Uri?displayProperty=nameWithType> klasy również wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="46ef6-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="46ef6-140">Wyrejestruj specjalne procent wszystkich wartości zakodowany.</span><span class="sxs-lookup"><span data-stu-id="46ef6-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="46ef6-141">Konwertuje procent, kodowane znaki spoza zestawu ASCII w reprezentacji znaków UTF-16.</span><span class="sxs-lookup"><span data-stu-id="46ef6-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="46ef6-142">Należy pamiętać, że oraz znaków Unicode (kodowanie Unicode w formacie % uXXXX) są obsługiwane znaki UTF-8 i ANSI/zestawów znaków Dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="46ef6-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="46ef6-143">Wykonuje inne czynności normalizacji, takie jak ścieżka kompresji.</span><span class="sxs-lookup"><span data-stu-id="46ef6-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="46ef6-144">Ponieważ żądanie nie zawiera żadnych informacji o kodowanie używane z algorytmem procent wartości, nie może być określić poprawne kodowanie właśnie, analizując kodowany w formacie procent wartości.</span><span class="sxs-lookup"><span data-stu-id="46ef6-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="46ef6-145">W związku z tym `http.sys` zawiera dwa klucze rejestru do modyfikowania proces:</span><span class="sxs-lookup"><span data-stu-id="46ef6-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="46ef6-146">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="46ef6-146">Registry Key</span></span>|<span data-ttu-id="46ef6-147">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="46ef6-147">Default Value</span></span>|<span data-ttu-id="46ef6-148">Opis</span><span class="sxs-lookup"><span data-stu-id="46ef6-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="46ef6-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="46ef6-149">EnableNonUTF8</span></span>|<span data-ttu-id="46ef6-150">1</span><span class="sxs-lookup"><span data-stu-id="46ef6-150">1</span></span>|<span data-ttu-id="46ef6-151">Jeśli zero, `http.sys` akceptuje tylko adresy URL algorytmem UTF-8.</span><span class="sxs-lookup"><span data-stu-id="46ef6-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="46ef6-152">Jeśli niezerową, `http.sys` również akceptuje kodowaniu ANSI lub kodowany w formacie DBCS adresów URL w żądaniach.</span><span class="sxs-lookup"><span data-stu-id="46ef6-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="46ef6-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="46ef6-153">FavorUTF8</span></span>|<span data-ttu-id="46ef6-154">1</span><span class="sxs-lookup"><span data-stu-id="46ef6-154">1</span></span>|<span data-ttu-id="46ef6-155">Jeśli niezerową, `http.sys` zawsze próbuje dekodowanie adresu URL jako UTF-8 najpierw; Jeśli tej konwersji nie powiedzie się i EnableNonUTF8 jest różna od zera, sterownik Http.sys, a następnie próbuje zdekodować kodowaniu ANSI lub zestawów znaków Dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="46ef6-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="46ef6-156">Jeśli zero (i EnableNonUTF8 jest różna od zera) `http.sys` podejmuje próbę zdekodowania kodowaniu ANSI lub DBCS; Jeśli się nie powiedzie, próby konwersji UTF-8.</span><span class="sxs-lookup"><span data-stu-id="46ef6-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="46ef6-157">Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa przekonwertowanego identyfikatora URI z `http.sys` jako wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="46ef6-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="46ef6-158">Istnieje potrzeba do obsługi znaki oprócz znaków i liczb w identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="46ef6-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="46ef6-159">Przykładem jest następujący identyfikator URI, który służy do pobierania informacji klienta dla klienta numer "1/3812":</span><span class="sxs-lookup"><span data-stu-id="46ef6-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="46ef6-160">Należy zwrócić uwagę ukośnika procent, kodowane w identyfikatorze Uri (% 2F).</span><span class="sxs-lookup"><span data-stu-id="46ef6-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="46ef6-161">Jest to konieczne, ponieważ w takim przypadku znaku ukośnika reprezentuje danych i nie ogranicznik ścieżki.</span><span class="sxs-lookup"><span data-stu-id="46ef6-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="46ef6-162">Przekazywanie ciągu identyfikatora Uri konstruktora doprowadzi do następującego identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="46ef6-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="46ef6-163">Dzielenie na jego segmenty ścieżki spowoduje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="46ef6-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="46ef6-164">To nie jest celem nadawca żądania.</span><span class="sxs-lookup"><span data-stu-id="46ef6-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="46ef6-165">Jeśli **unescapeRequestUrl** atrybut ma ustawioną **false**, a następnie po <xref:System.Net.HttpListener> odbiera żądanie, używa raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="46ef6-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="46ef6-166">Wartość domyślna dla **unescapeRequestUrl** atrybutu **true**.</span><span class="sxs-lookup"><span data-stu-id="46ef6-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="46ef6-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Właściwości można pobrać wartości bieżącego **unescapeRequestUrl** atrybutu z plików zastosowania konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="46ef6-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46ef6-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="46ef6-168">Example</span></span>  
 <span data-ttu-id="46ef6-169">Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net.HttpListener> klasy, gdy odbiera żądanie użycia raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="46ef6-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpListener  
        unescapeRequestUrl="false"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="46ef6-170">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="46ef6-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="46ef6-171">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="46ef6-171">Namespace</span></span>|<span data-ttu-id="46ef6-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="46ef6-172">System.Net</span></span>|  
|<span data-ttu-id="46ef6-173">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="46ef6-173">Schema Name</span></span>||  
|<span data-ttu-id="46ef6-174">Sprawdzanie poprawności pliku</span><span class="sxs-lookup"><span data-stu-id="46ef6-174">Validation File</span></span>||  
|<span data-ttu-id="46ef6-175">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="46ef6-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="46ef6-176">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="46ef6-176">See Also</span></span>  
 <xref:System.Net.Configuration.HttpListenerElement>  
 <xref:System.Net.HttpListener>  
 <xref:System.Net.HttpListenerRequest.Url%2A>  
 [<span data-ttu-id="46ef6-177">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="46ef6-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
