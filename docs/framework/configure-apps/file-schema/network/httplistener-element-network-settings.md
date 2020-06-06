---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: 0054be3d2002e4ea5247f25d8094386ac7242422
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088376"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="93ff2-102">\<httpListener>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="93ff2-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="93ff2-103">Dostosowuje parametry używane przez <xref:System.Net.HttpListener> klasę.</span><span class="sxs-lookup"><span data-stu-id="93ff2-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpListener>**

## <a name="syntax"></a><span data-ttu-id="93ff2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93ff2-104">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="93ff2-105">Typ</span><span class="sxs-lookup"><span data-stu-id="93ff2-105">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93ff2-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="93ff2-106">Attributes and Elements</span></span>  
 <span data-ttu-id="93ff2-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="93ff2-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93ff2-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="93ff2-108">Attributes</span></span>  
  
|<span data-ttu-id="93ff2-109">Atrybut</span><span class="sxs-lookup"><span data-stu-id="93ff2-109">Attribute</span></span>|<span data-ttu-id="93ff2-110">Opis</span><span class="sxs-lookup"><span data-stu-id="93ff2-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="93ff2-111">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="93ff2-111">unescapeRequestUrl</span></span>|<span data-ttu-id="93ff2-112">Wartość logiczna wskazująca, czy <xref:System.Net.HttpListener> wystąpienie używa nieprzetworzonego niezmienionego identyfikatora URI zamiast przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="93ff2-112">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93ff2-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="93ff2-113">Child Elements</span></span>  
 <span data-ttu-id="93ff2-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="93ff2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93ff2-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="93ff2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="93ff2-116">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="93ff2-116">**Element**</span></span>|<span data-ttu-id="93ff2-117">**Opis**</span><span class="sxs-lookup"><span data-stu-id="93ff2-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="93ff2-118">ustawienia</span><span class="sxs-lookup"><span data-stu-id="93ff2-118">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="93ff2-119">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="93ff2-119">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93ff2-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93ff2-120">Remarks</span></span>  
 <span data-ttu-id="93ff2-121">Atrybut **unescapeRequestUrl** wskazuje, czy <xref:System.Net.HttpListener> używa nieprzetworzonego NIEzmienionego identyfikatora URI zamiast PRZEKONWERTOWANEgo identyfikatora URI, gdzie wszystkie wartości kodowane w procentach są konwertowane i są wykonywane inne czynności normalizacji.</span><span class="sxs-lookup"><span data-stu-id="93ff2-121">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="93ff2-122">Gdy <xref:System.Net.HttpListener> wystąpienie odbiera żądanie przez `http.sys` usługę, tworzy wystąpienie ciągu identyfikatora URI dostarczonego przez `http.sys` i uwidacznia je jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> Właściwość.</span><span class="sxs-lookup"><span data-stu-id="93ff2-122">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="93ff2-123">`http.sys`Usługa ujawnia dwa ciągi identyfikatorów URI żądania:</span><span class="sxs-lookup"><span data-stu-id="93ff2-123">The `http.sys` service exposes two request URI strings:</span></span>  
  
- <span data-ttu-id="93ff2-124">Nieprzetworzony identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="93ff2-124">Raw URI</span></span>  
  
- <span data-ttu-id="93ff2-125">Przekonwertowany identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="93ff2-125">Converted URI</span></span>  
  
 <span data-ttu-id="93ff2-126">Nieprzetworzony identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> podany w wierszu żądania żądania http:</span><span class="sxs-lookup"><span data-stu-id="93ff2-126">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="93ff2-127">Nieprzetworzony identyfikator URI podany `http.sys` na żądanie wymienione powyżej ma wartość "/Path/".</span><span class="sxs-lookup"><span data-stu-id="93ff2-127">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="93ff2-128">Reprezentuje ciąg następujący po zleceniu HTTP, który został wysłany przez sieć.</span><span class="sxs-lookup"><span data-stu-id="93ff2-128">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="93ff2-129">`http.sys`Usługa tworzy przekonwertowany identyfikator URI z informacji znajdujących się w żądaniu przy użyciu identyfikatora URI podanego w wierszu żądania HTTP i nagłówka hosta w celu określenia serwera pochodzenia, do którego zostanie przesłane żądanie.</span><span class="sxs-lookup"><span data-stu-id="93ff2-129">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="93ff2-130">W tym celu należy porównać informacje z żądania z zestawem zarejestrowanych prefiksów URI.</span><span class="sxs-lookup"><span data-stu-id="93ff2-130">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="93ff2-131">Dokumentacja zestawu SDK serwera HTTP dotyczy tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="93ff2-131">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="93ff2-132">Aby można było porównać żądanie z zarejestrowanymi prefiksami URI, należy wykonać pewne normalizacji żądania.</span><span class="sxs-lookup"><span data-stu-id="93ff2-132">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="93ff2-133">W przypadku przykładu powyżej przekonwertowanego identyfikatora URI można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="93ff2-133">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="93ff2-134">`http.sys`Usługa łączy <xref:System.Uri.Host%2A?displayProperty=nameWithType> wartość właściwości i ciąg w wierszu żądania w celu utworzenia przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="93ff2-134">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="93ff2-135">Ponadto `http.sys` <xref:System.Uri?displayProperty=nameWithType> Klasa wykonuje również następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="93ff2-135">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
- <span data-ttu-id="93ff2-136">Cofa wszystkie wartości zakodowane procentowo.</span><span class="sxs-lookup"><span data-stu-id="93ff2-136">Un-escapes all percent encoded values.</span></span>  
  
- <span data-ttu-id="93ff2-137">Konwertuje znaki nienależące do zestawu znaków ASCII, które nie są zakodowane w formacie UTF-16.</span><span class="sxs-lookup"><span data-stu-id="93ff2-137">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="93ff2-138">Należy zauważyć, że znaki UTF-8 i ANSI/DBCS są obsługiwane, a także znaki Unicode (kodowanie Unicode przy użyciu formatu% uXXXX).</span><span class="sxs-lookup"><span data-stu-id="93ff2-138">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
- <span data-ttu-id="93ff2-139">Wykonuje inne kroki normalizacji, takie jak kompresja ścieżki.</span><span class="sxs-lookup"><span data-stu-id="93ff2-139">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="93ff2-140">Ponieważ żądanie nie zawiera żadnych informacji o kodowaniu używanym dla wartości zakodowanych w procentach, może nie być możliwe określenie poprawnego kodowania tylko przez analizowanie wartości zakodowanych w procentach.</span><span class="sxs-lookup"><span data-stu-id="93ff2-140">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="93ff2-141">`http.sys`W związku z tym są dostępne dwa klucze rejestru do modyfikacji procesu:</span><span class="sxs-lookup"><span data-stu-id="93ff2-141">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="93ff2-142">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="93ff2-142">Registry Key</span></span>|<span data-ttu-id="93ff2-143">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="93ff2-143">Default Value</span></span>|<span data-ttu-id="93ff2-144">Opis</span><span class="sxs-lookup"><span data-stu-id="93ff2-144">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="93ff2-145">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="93ff2-145">EnableNonUTF8</span></span>|<span data-ttu-id="93ff2-146">1</span><span class="sxs-lookup"><span data-stu-id="93ff2-146">1</span></span>|<span data-ttu-id="93ff2-147">Jeśli zero, `http.sys` akceptuje tylko adresy URL zakodowane w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="93ff2-147">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="93ff2-148">Jeśli wartość jest różna od zera, `http.sys` w żądaniach akceptowane są również adresy URL kodowane w formacie ANSI lub DBCS.</span><span class="sxs-lookup"><span data-stu-id="93ff2-148">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="93ff2-149">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="93ff2-149">FavorUTF8</span></span>|<span data-ttu-id="93ff2-150">1</span><span class="sxs-lookup"><span data-stu-id="93ff2-150">1</span></span>|<span data-ttu-id="93ff2-151">Jeśli wartość jest różna od zera, program `http.sys` zawsze próbuje zdekodować adres URL jako pierwszy w formacie UTF-8. Jeśli konwersja nie powiedzie się, a EnableNonUTF8 jest różna od zera, http. sys próbuje zdekodować ją jako ANSI lub DBCS.</span><span class="sxs-lookup"><span data-stu-id="93ff2-151">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="93ff2-152">Jeśli zero (i EnableNonUTF8 jest różna od zera), `http.sys` próbuje zdekodować ją jako ANSI lub DBCS; Jeśli to nie powiodło się, próbuje konwersję UTF-8.</span><span class="sxs-lookup"><span data-stu-id="93ff2-152">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="93ff2-153">Po <xref:System.Net.HttpListener> odebraniu żądania korzysta z przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="93ff2-153">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="93ff2-154">Istnieje potrzeba obsługi znaków oprócz znaków i cyfr w identyfikatorach URI.</span><span class="sxs-lookup"><span data-stu-id="93ff2-154">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="93ff2-155">Przykładem jest następujący identyfikator URI, który służy do pobierania informacji o kliencie dla numeru klienta "1/3812":</span><span class="sxs-lookup"><span data-stu-id="93ff2-155">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="93ff2-156">Zwróć uwagę na ukośnik zakodowany procentowo w identyfikatorze URI (% 2F).</span><span class="sxs-lookup"><span data-stu-id="93ff2-156">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="93ff2-157">Jest to konieczne, ponieważ w tym przypadku znak ukośnika reprezentuje dane, a nie ogranicznik ścieżki.</span><span class="sxs-lookup"><span data-stu-id="93ff2-157">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="93ff2-158">Przekazywanie ciągu do konstruktora identyfikatora URI będzie prowadzić do następującego identyfikatora URI:</span><span class="sxs-lookup"><span data-stu-id="93ff2-158">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="93ff2-159">Podział ścieżki na segmenty spowoduje następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="93ff2-159">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="93ff2-160">Nie jest to cel nadawcy żądania.</span><span class="sxs-lookup"><span data-stu-id="93ff2-160">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="93ff2-161">Jeśli atrybut **unescapeRequestUrl** ma wartość **false**, wtedy, gdy <xref:System.Net.HttpListener> otrzyma żądanie, używa nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="93ff2-161">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="93ff2-162">Wartość domyślna atrybutu **unescapeRequestUrl** ma wartość **true**.</span><span class="sxs-lookup"><span data-stu-id="93ff2-162">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="93ff2-163"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A>Właściwość może służyć do uzyskiwania bieżącej wartości atrybutu **unescapeRequestUrl** z odpowiednich plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="93ff2-163">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93ff2-164">Przykład</span><span class="sxs-lookup"><span data-stu-id="93ff2-164">Example</span></span>  
 <span data-ttu-id="93ff2-165">Poniższy przykład pokazuje, jak skonfigurować klasę, <xref:System.Net.HttpListener> gdy odbierze żądanie użycia nieprzetworzonego identyfikatora URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="93ff2-165">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="93ff2-166">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="93ff2-166">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="93ff2-167">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="93ff2-167">Namespace</span></span>|<span data-ttu-id="93ff2-168">System.Net</span><span class="sxs-lookup"><span data-stu-id="93ff2-168">System.Net</span></span>|  
|<span data-ttu-id="93ff2-169">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="93ff2-169">Schema Name</span></span>||  
|<span data-ttu-id="93ff2-170">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="93ff2-170">Validation File</span></span>||  
|<span data-ttu-id="93ff2-171">Może być puste</span><span class="sxs-lookup"><span data-stu-id="93ff2-171">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="93ff2-172">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93ff2-172">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="93ff2-173">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="93ff2-173">Network Settings Schema</span></span>](index.md)
