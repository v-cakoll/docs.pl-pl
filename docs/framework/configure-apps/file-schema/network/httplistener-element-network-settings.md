---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 3f75096681ab07dd6d4788fbded5ca5c4a024aef
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698195"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="9efff-102">\<httpListener >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="9efff-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="9efff-103">Dostosowuje parametry używane przez klasę <xref:System.Net.HttpListener>.</span><span class="sxs-lookup"><span data-stu-id="9efff-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
[<span data-ttu-id="9efff-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="9efff-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="9efff-105">&nbsp; @ no__t-1[ **@no__t -4system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9efff-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="9efff-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="9efff-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="9efff-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<httpListener >**</span><span class="sxs-lookup"><span data-stu-id="9efff-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9efff-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="9efff-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="9efff-109">Typ</span><span class="sxs-lookup"><span data-stu-id="9efff-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9efff-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="9efff-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9efff-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="9efff-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9efff-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="9efff-112">Attributes</span></span>  
  
|<span data-ttu-id="9efff-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="9efff-113">Attribute</span></span>|<span data-ttu-id="9efff-114">Opis</span><span class="sxs-lookup"><span data-stu-id="9efff-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9efff-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="9efff-115">unescapeRequestUrl</span></span>|<span data-ttu-id="9efff-116">Wartość logiczna wskazująca, czy wystąpienie <xref:System.Net.HttpListener> używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="9efff-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9efff-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="9efff-117">Child Elements</span></span>  
 <span data-ttu-id="9efff-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="9efff-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9efff-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="9efff-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9efff-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="9efff-120">**Element**</span></span>|<span data-ttu-id="9efff-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="9efff-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="9efff-122">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="9efff-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="9efff-123">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="9efff-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9efff-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9efff-124">Remarks</span></span>  
 <span data-ttu-id="9efff-125">Atrybut **unescapeRequestUrl** wskazuje, czy <xref:System.Net.HttpListener> używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI, gdzie wszystkie wartości kodowane w procentach są konwertowane i są wykonywane inne czynności normalizacji.</span><span class="sxs-lookup"><span data-stu-id="9efff-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="9efff-126">Gdy wystąpienie <xref:System.Net.HttpListener> odbiera żądanie za pomocą usługi `http.sys`, tworzy wystąpienie ciągu identyfikatora URI dostarczonego przez `http.sys` i uwidacznia je jako właściwość <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9efff-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="9efff-127">Usługa `http.sys` ujawnia dwa ciągi identyfikatorów URI żądania:</span><span class="sxs-lookup"><span data-stu-id="9efff-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="9efff-128">Nieprzetworzony identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="9efff-128">Raw URI</span></span>  
  
- <span data-ttu-id="9efff-129">Przekonwertowany identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="9efff-129">Converted URI</span></span>  
  
 <span data-ttu-id="9efff-130">Nieprzetworzony identyfikator URI to <xref:System.Uri?displayProperty=nameWithType> podany w wierszu żądania żądania HTTP:</span><span class="sxs-lookup"><span data-stu-id="9efff-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="9efff-131">Nieprzetworzony identyfikator URI podany przez `http.sys` dla żądania wymienionego powyżej ma wartość "/Path/".</span><span class="sxs-lookup"><span data-stu-id="9efff-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="9efff-132">Reprezentuje ciąg następujący po zleceniu HTTP, który został wysłany przez sieć.</span><span class="sxs-lookup"><span data-stu-id="9efff-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="9efff-133">Usługa `http.sys` tworzy przekonwertowany identyfikator URI z informacji zawartych w żądaniu przy użyciu identyfikatora URI podanego w wierszu żądania HTTP i nagłówka hosta, aby określić serwer pierwotny, do którego ma zostać przesłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="9efff-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="9efff-134">W tym celu należy porównać informacje z żądania z zestawem zarejestrowanych prefiksów URI.</span><span class="sxs-lookup"><span data-stu-id="9efff-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="9efff-135">Dokumentacja zestawu SDK serwera HTTP dotyczy tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="9efff-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="9efff-136">Aby można było porównać żądanie z zarejestrowanymi prefiksami URI, należy wykonać pewne normalizacji żądania.</span><span class="sxs-lookup"><span data-stu-id="9efff-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="9efff-137">W przypadku przykładu powyżej przekonwertowanego identyfikatora URI można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9efff-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="9efff-138">Usługa `http.sys` łączy wartość właściwości <xref:System.Uri.Host%2A?displayProperty=nameWithType> i ciąg w wierszu żądania w celu utworzenia przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="9efff-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="9efff-139">Ponadto `http.sys` i Klasa <xref:System.Uri?displayProperty=nameWithType> wykonuje również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="9efff-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="9efff-140">Cofa wszystkie wartości zakodowane procentowo.</span><span class="sxs-lookup"><span data-stu-id="9efff-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="9efff-141">Konwertuje znaki nienależące do zestawu znaków ASCII, które nie są zakodowane w formacie UTF-16.</span><span class="sxs-lookup"><span data-stu-id="9efff-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="9efff-142">Należy zauważyć, że znaki UTF-8 i ANSI/DBCS są obsługiwane, a także znaki Unicode (kodowanie Unicode przy użyciu formatu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="9efff-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="9efff-143">Wykonuje inne kroki normalizacji, takie jak kompresja ścieżki.</span><span class="sxs-lookup"><span data-stu-id="9efff-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="9efff-144">Ponieważ żądanie nie zawiera żadnych informacji o kodowaniu używanym dla wartości zakodowanych w procentach, może nie być możliwe określenie poprawnego kodowania tylko przez analizowanie wartości zakodowanych w procentach.</span><span class="sxs-lookup"><span data-stu-id="9efff-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="9efff-145">W związku z tym `http.sys` oferuje dwa klucze rejestru do modyfikacji procesu:</span><span class="sxs-lookup"><span data-stu-id="9efff-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="9efff-146">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="9efff-146">Registry Key</span></span>|<span data-ttu-id="9efff-147">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="9efff-147">Default Value</span></span>|<span data-ttu-id="9efff-148">Opis</span><span class="sxs-lookup"><span data-stu-id="9efff-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="9efff-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="9efff-149">EnableNonUTF8</span></span>|<span data-ttu-id="9efff-150">1</span><span class="sxs-lookup"><span data-stu-id="9efff-150">1</span></span>|<span data-ttu-id="9efff-151">Jeśli wartość jest równa zero, `http.sys` akceptuje tylko adresy URL kodowane w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9efff-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="9efff-152">Jeśli wartość jest różna od zera, `http.sys` również akceptuje adresy URL zakodowane ANSI lub DBCS w żądaniach.</span><span class="sxs-lookup"><span data-stu-id="9efff-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="9efff-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="9efff-153">FavorUTF8</span></span>|<span data-ttu-id="9efff-154">1</span><span class="sxs-lookup"><span data-stu-id="9efff-154">1</span></span>|<span data-ttu-id="9efff-155">Jeśli wartość jest różna od zera, `http.sys` zawsze próbuje zdekodować adres URL jako pierwszy w formacie UTF-8; Jeśli konwersja nie powiedzie się, a EnableNonUTF8 jest różna od zera, http. sys próbuje zdekodować ją jako ANSI lub DBCS.</span><span class="sxs-lookup"><span data-stu-id="9efff-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="9efff-156">Jeśli zero (i EnableNonUTF8 jest różna od zera), `http.sys` próbuje zdekodować ją jako ANSI lub DBCS; Jeśli to się nie powiedzie, próbuje konwersję UTF-8.</span><span class="sxs-lookup"><span data-stu-id="9efff-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="9efff-157">Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe do właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="9efff-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="9efff-158">Istnieje potrzeba obsługi znaków oprócz znaków i cyfr w identyfikatorach URI.</span><span class="sxs-lookup"><span data-stu-id="9efff-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="9efff-159">Przykładem jest następujący identyfikator URI, który służy do pobierania informacji o kliencie dla numeru klienta "1/3812":</span><span class="sxs-lookup"><span data-stu-id="9efff-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="9efff-160">Zwróć uwagę na ukośnik zakodowany procentowo w identyfikatorze URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="9efff-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="9efff-161">Jest to konieczne, ponieważ w tym przypadku znak ukośnika reprezentuje dane, a nie ogranicznik ścieżki.</span><span class="sxs-lookup"><span data-stu-id="9efff-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="9efff-162">Przekazywanie ciągu do konstruktora identyfikatora URI będzie prowadzić do następującego identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="9efff-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="9efff-163">Podział ścieżki na segmenty spowoduje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="9efff-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="9efff-164">Nie jest to cel nadawcy żądania.</span><span class="sxs-lookup"><span data-stu-id="9efff-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="9efff-165">Jeśli atrybut **unescapeRequestUrl** ma wartość **false**, wtedy, gdy <xref:System.Net.HttpListener> odbiera żądanie, używa nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="9efff-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="9efff-166">Wartość domyślna atrybutu **unescapeRequestUrl** ma wartość **true**.</span><span class="sxs-lookup"><span data-stu-id="9efff-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="9efff-167">Właściwość <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> umożliwia uzyskanie bieżącej wartości atrybutu **unescapeRequestUrl** z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="9efff-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9efff-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="9efff-168">Example</span></span>  
 <span data-ttu-id="9efff-169">Poniższy przykład przedstawia sposób konfigurowania klasy <xref:System.Net.HttpListener>, gdy odbierze żądanie użycia nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe do właściwości <xref:System.Net.HttpListenerRequest.Url%2A>.</span><span class="sxs-lookup"><span data-stu-id="9efff-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="9efff-170">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="9efff-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="9efff-171">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9efff-171">Namespace</span></span>|<span data-ttu-id="9efff-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="9efff-172">System.Net</span></span>|  
|<span data-ttu-id="9efff-173">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="9efff-173">Schema Name</span></span>||  
|<span data-ttu-id="9efff-174">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="9efff-174">Validation File</span></span>||  
|<span data-ttu-id="9efff-175">Może być puste</span><span class="sxs-lookup"><span data-stu-id="9efff-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="9efff-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9efff-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="9efff-177">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="9efff-177">Network Settings Schema</span></span>](index.md)
