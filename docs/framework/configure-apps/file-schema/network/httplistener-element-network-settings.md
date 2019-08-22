---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: cb24dc7296e2f2f6ea292566330d3d6ae4f25f85
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664142"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="f0d80-102">\<Odbiornika HttpListener >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="f0d80-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="f0d80-103">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasę.</span><span class="sxs-lookup"><span data-stu-id="f0d80-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="f0d80-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f0d80-104">\<configuration></span></span>  
<span data-ttu-id="f0d80-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="f0d80-105">\<system.net></span></span>  
<span data-ttu-id="f0d80-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="f0d80-106">\<settings></span></span>  
<span data-ttu-id="f0d80-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="f0d80-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0d80-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0d80-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="f0d80-109">Typ</span><span class="sxs-lookup"><span data-stu-id="f0d80-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0d80-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f0d80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f0d80-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f0d80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0d80-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f0d80-112">Attributes</span></span>  
  
|<span data-ttu-id="f0d80-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="f0d80-113">Attribute</span></span>|<span data-ttu-id="f0d80-114">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d80-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0d80-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="f0d80-115">unescapeRequestUrl</span></span>|<span data-ttu-id="f0d80-116">Wartość logiczna wskazująca, czy <xref:System.Net.HttpListener> wystąpienie używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f0d80-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0d80-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f0d80-117">Child Elements</span></span>  
 <span data-ttu-id="f0d80-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="f0d80-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0d80-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f0d80-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f0d80-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="f0d80-120">**Element**</span></span>|<span data-ttu-id="f0d80-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f0d80-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f0d80-122">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="f0d80-122">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="f0d80-123">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f0d80-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d80-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0d80-124">Remarks</span></span>  
 <span data-ttu-id="f0d80-125">Atrybut **unescapeRequestUrl** wskazuje, czy <xref:System.Net.HttpListener> używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI, gdzie wszystkie wartości kodowane w procentach są konwertowane i są wykonywane inne czynności normalizacji.</span><span class="sxs-lookup"><span data-stu-id="f0d80-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="f0d80-126">Gdy wystąpienie odbiera żądanie `http.sys` przez usługę, tworzy wystąpienie ciągu identyfikatora URI dostarczonego przez `http.sys`i uwidacznia je jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> właściwość. <xref:System.Net.HttpListener></span><span class="sxs-lookup"><span data-stu-id="f0d80-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="f0d80-127">`http.sys` Usługa ujawnia dwa ciągi identyfikatorów URI żądania:</span><span class="sxs-lookup"><span data-stu-id="f0d80-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="f0d80-128">Nieprzetworzony identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="f0d80-128">Raw URI</span></span>  
  
- <span data-ttu-id="f0d80-129">Przekonwertowany identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="f0d80-129">Converted URI</span></span>  
  
 <span data-ttu-id="f0d80-130">Nieprzetworzony identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> podany w wierszu żądania żądania http:</span><span class="sxs-lookup"><span data-stu-id="f0d80-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="f0d80-131">Nieprzetworzony identyfikator URI podany `http.sys` na żądanie wymienione powyżej ma wartość "/Path/".</span><span class="sxs-lookup"><span data-stu-id="f0d80-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="f0d80-132">Reprezentuje ciąg następujący po zleceniu HTTP, który został wysłany przez sieć.</span><span class="sxs-lookup"><span data-stu-id="f0d80-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="f0d80-133">`http.sys` Usługa tworzy przekonwertowany identyfikator URI z informacji znajdujących się w żądaniu przy użyciu identyfikatora URI podanego w wierszu żądania HTTP i nagłówka hosta w celu określenia serwera pochodzenia, do którego zostanie przesłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="f0d80-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="f0d80-134">W tym celu należy porównać informacje z żądania z zestawem zarejestrowanych prefiksów URI.</span><span class="sxs-lookup"><span data-stu-id="f0d80-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="f0d80-135">Dokumentacja zestawu SDK serwera HTTP dotyczy tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="f0d80-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="f0d80-136">Aby można było porównać żądanie z zarejestrowanymi prefiksami URI, należy wykonać pewne normalizacji żądania.</span><span class="sxs-lookup"><span data-stu-id="f0d80-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="f0d80-137">W przypadku przykładu powyżej przekonwertowanego identyfikatora URI można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f0d80-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="f0d80-138">`http.sys` Usługa łączywartośćwłaściwościiciągwwierszużądaniawceluutworzeniaprzekonwertowanego<xref:System.Uri.Host%2A?displayProperty=nameWithType> identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="f0d80-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="f0d80-139">`http.sys` Ponadto<xref:System.Uri?displayProperty=nameWithType> Klasa wykonuje również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f0d80-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="f0d80-140">Cofa wszystkie wartości zakodowane procentowo.</span><span class="sxs-lookup"><span data-stu-id="f0d80-140">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="f0d80-141">Konwertuje znaki nienależące do zestawu znaków ASCII, które nie są zakodowane w formacie UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f0d80-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="f0d80-142">Należy zauważyć, że znaki UTF-8 i ANSI/DBCS są obsługiwane, a także znaki Unicode (kodowanie Unicode przy użyciu formatu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="f0d80-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="f0d80-143">Wykonuje inne kroki normalizacji, takie jak kompresja ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f0d80-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="f0d80-144">Ponieważ żądanie nie zawiera żadnych informacji o kodowaniu używanym dla wartości zakodowanych w procentach, może nie być możliwe określenie poprawnego kodowania tylko przez analizowanie wartości zakodowanych w procentach.</span><span class="sxs-lookup"><span data-stu-id="f0d80-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="f0d80-145">W `http.sys` związku z tym są dostępne dwa klucze rejestru do modyfikacji procesu:</span><span class="sxs-lookup"><span data-stu-id="f0d80-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="f0d80-146">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="f0d80-146">Registry Key</span></span>|<span data-ttu-id="f0d80-147">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="f0d80-147">Default Value</span></span>|<span data-ttu-id="f0d80-148">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d80-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="f0d80-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="f0d80-149">EnableNonUTF8</span></span>|<span data-ttu-id="f0d80-150">1</span><span class="sxs-lookup"><span data-stu-id="f0d80-150">1</span></span>|<span data-ttu-id="f0d80-151">Jeśli zero, `http.sys` akceptuje tylko adresy URL zakodowane w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f0d80-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="f0d80-152">Jeśli wartość jest różna od `http.sys` zera, w żądaniach akceptowane są również adresy URL kodowane w formacie ANSI lub DBCS.</span><span class="sxs-lookup"><span data-stu-id="f0d80-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="f0d80-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="f0d80-153">FavorUTF8</span></span>|<span data-ttu-id="f0d80-154">1</span><span class="sxs-lookup"><span data-stu-id="f0d80-154">1</span></span>|<span data-ttu-id="f0d80-155">Jeśli wartość jest różna od `http.sys` zera, program zawsze próbuje zdekodować adres URL jako pierwszy w formacie UTF-8. Jeśli konwersja nie powiedzie się, a EnableNonUTF8 jest różna od zera, http. sys próbuje zdekodować ją jako ANSI lub DBCS.</span><span class="sxs-lookup"><span data-stu-id="f0d80-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="f0d80-156">Jeśli zero (i EnableNonUTF8 jest różna od zera), `http.sys` próbuje zdekodować ją jako ANSI lub DBCS; Jeśli to nie powiodło się, próbuje konwersję UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f0d80-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="f0d80-157">Po <xref:System.Net.HttpListener> odebraniu żądania korzysta z przekonwertowanego identyfikatora URI `http.sys` z jako danych wejściowych <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0d80-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="f0d80-158">Istnieje potrzeba obsługi znaków oprócz znaków i cyfr w identyfikatorach URI.</span><span class="sxs-lookup"><span data-stu-id="f0d80-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="f0d80-159">Przykładem jest następujący identyfikator URI, który służy do pobierania informacji o kliencie dla numeru klienta "1/3812":</span><span class="sxs-lookup"><span data-stu-id="f0d80-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="f0d80-160">Zwróć uwagę na ukośnik zakodowany procentowo w identyfikatorze URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="f0d80-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="f0d80-161">Jest to konieczne, ponieważ w tym przypadku znak ukośnika reprezentuje dane, a nie ogranicznik ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f0d80-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="f0d80-162">Przekazywanie ciągu do konstruktora identyfikatora URI będzie prowadzić do następującego identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="f0d80-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="f0d80-163">Podział ścieżki na segmenty spowoduje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="f0d80-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="f0d80-164">Nie jest to cel nadawcy żądania.</span><span class="sxs-lookup"><span data-stu-id="f0d80-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="f0d80-165">Jeśli atrybut **unescapeRequestUrl** ma wartość **false**, <xref:System.Net.HttpListener> wtedy, gdy otrzyma żądanie, używa nieprzetworzonego identyfikatora URI zamiast przekonwertowanego <xref:System.Net.HttpListenerRequest.Url%2A> identyfikatora URI z `http.sys` jako danych wejściowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0d80-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="f0d80-166">Wartość domyślna atrybutu **unescapeRequestUrl** ma wartość **true**.</span><span class="sxs-lookup"><span data-stu-id="f0d80-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="f0d80-167">Właściwość może służyć do uzyskiwania bieżącej wartości atrybutu unescapeRequestUrl z odpowiednich plików konfiguracji. <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A></span><span class="sxs-lookup"><span data-stu-id="f0d80-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0d80-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0d80-168">Example</span></span>  
 <span data-ttu-id="f0d80-169">Poniższy przykład pokazuje, jak skonfigurować klasę, <xref:System.Net.HttpListener> gdy odbierze żądanie użycia nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f0d80-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="f0d80-170">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="f0d80-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="f0d80-171">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f0d80-171">Namespace</span></span>|<span data-ttu-id="f0d80-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="f0d80-172">System.Net</span></span>|  
|<span data-ttu-id="f0d80-173">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="f0d80-173">Schema Name</span></span>||  
|<span data-ttu-id="f0d80-174">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="f0d80-174">Validation File</span></span>||  
|<span data-ttu-id="f0d80-175">Może być puste</span><span class="sxs-lookup"><span data-stu-id="f0d80-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="f0d80-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d80-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="f0d80-177">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f0d80-177">Network Settings Schema</span></span>](index.md)
