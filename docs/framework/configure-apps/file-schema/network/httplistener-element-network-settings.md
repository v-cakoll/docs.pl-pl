---
title: <httpListener>, element (ustawienia sieci)
ms.date: 03/30/2017
ms.assetid: 62f121fd-3f2e-4033-bb39-48ae996bfbd9
ms.openlocfilehash: b3a6d527bc1bf8210bb85424fa218fda495a2a2d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59099747"
---
# <a name="httplistener-element-network-settings"></a><span data-ttu-id="75cd1-102">\<httpListener >, Element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="75cd1-102">\<httpListener> Element (Network Settings)</span></span>
<span data-ttu-id="75cd1-103">Dostosowuje parametrów używanych przez <xref:System.Net.HttpListener> klasy.</span><span class="sxs-lookup"><span data-stu-id="75cd1-103">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>  
  
 <span data-ttu-id="75cd1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="75cd1-104">\<configuration></span></span>  
<span data-ttu-id="75cd1-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="75cd1-105">\<system.net></span></span>  
<span data-ttu-id="75cd1-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="75cd1-106">\<settings></span></span>  
<span data-ttu-id="75cd1-107">\<httpListener></span><span class="sxs-lookup"><span data-stu-id="75cd1-107">\<httpListener></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75cd1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="75cd1-108">Syntax</span></span>  
  
```xml  
<httpListener  
  unescapeRequestUrl="true|false"  
/>  
```  
  
## <a name="type"></a><span data-ttu-id="75cd1-109">Typ</span><span class="sxs-lookup"><span data-stu-id="75cd1-109">Type</span></span>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75cd1-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="75cd1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="75cd1-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="75cd1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75cd1-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="75cd1-112">Attributes</span></span>  
  
|<span data-ttu-id="75cd1-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="75cd1-113">Attribute</span></span>|<span data-ttu-id="75cd1-114">Opis</span><span class="sxs-lookup"><span data-stu-id="75cd1-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75cd1-115">unescapeRequestUrl</span><span class="sxs-lookup"><span data-stu-id="75cd1-115">unescapeRequestUrl</span></span>|<span data-ttu-id="75cd1-116">Wartość logiczna, która wskazuje, czy <xref:System.Net.HttpListener> wystąpienie używa pierwotne URI o niezmienionym znaczeniu zamiast przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="75cd1-116">A Boolean value that indicates if a <xref:System.Net.HttpListener> instance uses the raw unescaped URI instead of the converted URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75cd1-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="75cd1-117">Child Elements</span></span>  
 <span data-ttu-id="75cd1-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="75cd1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75cd1-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="75cd1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="75cd1-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="75cd1-120">**Element**</span></span>|<span data-ttu-id="75cd1-121">**Opis**</span><span class="sxs-lookup"><span data-stu-id="75cd1-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="75cd1-122">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="75cd1-122">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="75cd1-123">Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="75cd1-123">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75cd1-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75cd1-124">Remarks</span></span>  
 <span data-ttu-id="75cd1-125">**UnescapeRequestUrl** atrybut wskazuje, jeśli <xref:System.Net.HttpListener> używa pierwotne URI o niezmienionym znaczeniu zamiast przekonwertowanego identyfikator URI, gdzie wszystkie zakodowane w formacie procent wartości są konwertowane i są podjąć inne kroki normalizacji.</span><span class="sxs-lookup"><span data-stu-id="75cd1-125">The **unescapeRequestUrl** attribute indicates if <xref:System.Net.HttpListener> uses the raw unescaped URI instead of the converted URI where any percent-encoded values are converted and other normalization steps are taken.</span></span>  
  
 <span data-ttu-id="75cd1-126">Gdy <xref:System.Net.HttpListener> wystąpienia odbiera żądanie za pośrednictwem `http.sys` usługi, tworzy wystąpienie ciągu identyfikatora URI, dostarczone przez `http.sys`i uwidacznia go jako <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="75cd1-126">When a <xref:System.Net.HttpListener> instance receives a request through the `http.sys` service, it creates an instance of the URI string provided by `http.sys`, and exposes it as the <xref:System.Net.HttpListenerRequest.Url%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="75cd1-127">`http.sys` Service udostępnia dwa ciągi identyfikatora URI żądania:</span><span class="sxs-lookup"><span data-stu-id="75cd1-127">The `http.sys` service exposes two request URI strings:</span></span>  
  
-   <span data-ttu-id="75cd1-128">Identyfikator URI nieprzetworzone</span><span class="sxs-lookup"><span data-stu-id="75cd1-128">Raw URI</span></span>  
  
-   <span data-ttu-id="75cd1-129">Przekonwertowana identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="75cd1-129">Converted URI</span></span>  
  
 <span data-ttu-id="75cd1-130">Nieprzetworzone identyfikator URI jest <xref:System.Uri?displayProperty=nameWithType> podane w wierszu żądania żądania HTTP:</span><span class="sxs-lookup"><span data-stu-id="75cd1-130">The raw URI is the <xref:System.Uri?displayProperty=nameWithType> provided in the request line of a HTTP request:</span></span>  
  
 `GET /path/`  
  
 `Host: www.contoso.com`  
  
 <span data-ttu-id="75cd1-131">Nieprzetworzone dostarczone przez identyfikator URI `http.sys` dla żądania, o których wspomniano powyżej, jest "/ path /".</span><span class="sxs-lookup"><span data-stu-id="75cd1-131">The raw URI provided by `http.sys` for the request mentioned above, is "/path/".</span></span> <span data-ttu-id="75cd1-132">Reprezentuje ciąg po zlecenie HTTP, ponieważ została wysłana przez sieć.</span><span class="sxs-lookup"><span data-stu-id="75cd1-132">This represents the string following the HTTP verb as it was sent over the network.</span></span>  
  
 <span data-ttu-id="75cd1-133">`http.sys` Usługa tworzy przekonwertowanego identyfikatora URI z informacjami w żądaniu przy użyciu podanego w wierszu żądania HTTP identyfikatora URI i nagłówek hosta, aby określić serwer pochodzenia żądania powinien być przekazywany do.</span><span class="sxs-lookup"><span data-stu-id="75cd1-133">The `http.sys` service creates a converted URI from the information provided in the request by using the URI provided in the HTTP request line and the Host header to determine the origin server the request should be forwarded to.</span></span> <span data-ttu-id="75cd1-134">Odbywa się przez porównywanie informacji dotyczących z żądania z zestawem zarejestrowanych prefiksów identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="75cd1-134">This is done by comparing the information from the request with a set of registered URI prefixes.</span></span> <span data-ttu-id="75cd1-135">W dokumentacji zestawu SDK serwera HTTP odwołuje się do tego przekonwertowanego identyfikatora URI jako struktury HTTP_COOKED_URL.</span><span class="sxs-lookup"><span data-stu-id="75cd1-135">The HTTP Server SDK documentation refers to this converted URI as the HTTP_COOKED_URL structure.</span></span>  
  
 <span data-ttu-id="75cd1-136">Aby można było porównać żądania przy użyciu zarejestrowanego prefiksów identyfikatorów URI, musi wykonać niektóre normalizacji na żądanie.</span><span class="sxs-lookup"><span data-stu-id="75cd1-136">In order to be able to compare the request with registered URI prefixes, some normalization to the request needs to be done.</span></span> <span data-ttu-id="75cd1-137">W przykładzie powyżej przekonwertowanego identyfikator URI będzie następujący:</span><span class="sxs-lookup"><span data-stu-id="75cd1-137">For the sample above the converted URI would be as follows:</span></span>  
  
 `http://www.contoso.com/path/`  
  
 <span data-ttu-id="75cd1-138">`http.sys` Usługi łączy w sobie <xref:System.Uri.Host%2A?displayProperty=nameWithType> wartości właściwości, a ciąg w wierszu żądania do utworzenia przekonwertowanego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="75cd1-138">The `http.sys` service combines the <xref:System.Uri.Host%2A?displayProperty=nameWithType> property value and the string in the request line to create a converted URI.</span></span> <span data-ttu-id="75cd1-139">Ponadto `http.sys` i <xref:System.Uri?displayProperty=nameWithType> klasy również wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="75cd1-139">In addition, `http.sys` and the <xref:System.Uri?displayProperty=nameWithType> class also does the following:</span></span>  
  
-   <span data-ttu-id="75cd1-140">ONZ anuluje wszystkie zakodowany wartość procentowa.</span><span class="sxs-lookup"><span data-stu-id="75cd1-140">Un-escapes all percent encoded values.</span></span>  
  
-   <span data-ttu-id="75cd1-141">Konwertuje kodowany w formacie procent znaki spoza zestawu ASCII w reprezentacji znaków UTF-16.</span><span class="sxs-lookup"><span data-stu-id="75cd1-141">Converts percent-encoded non-ASCII characters into a UTF-16 character representation.</span></span> <span data-ttu-id="75cd1-142">Należy pamiętać, że UTF-8 i ANSI/DBCS są obsługiwane znaki oraz znaki Unicode (kodowanie Unicode przy użyciu formatu uXXXX %).</span><span class="sxs-lookup"><span data-stu-id="75cd1-142">Note that UTF-8 and ANSI/DBCS characters are supported as well as Unicode characters (Unicode encoding using the %uXXXX format).</span></span>  
  
-   <span data-ttu-id="75cd1-143">Wykonuje inne czynności normalizacji, takie jak kompresja ścieżki.</span><span class="sxs-lookup"><span data-stu-id="75cd1-143">Executes other normalization steps, like path compression.</span></span>  
  
 <span data-ttu-id="75cd1-144">Ponieważ żądanie nie zawiera żadnych informacji o kodowanie używane do zakodowane w formacie procent wartości, nie może być określić poprawne kodowanie przez analizowanie zakodowane w formacie procent wartości.</span><span class="sxs-lookup"><span data-stu-id="75cd1-144">Since the request doesn't contain any information about the encoding used for percent-encoded values, it may not be possible to determine the correct encoding just by parsing the percent-encoded values.</span></span>  
  
 <span data-ttu-id="75cd1-145">W związku z tym `http.sys` zawiera dwa klucze rejestru do modyfikowania procesu:</span><span class="sxs-lookup"><span data-stu-id="75cd1-145">Therefore `http.sys` provides two registry keys for modifying the process:</span></span>  
  
|<span data-ttu-id="75cd1-146">Klucz rejestru</span><span class="sxs-lookup"><span data-stu-id="75cd1-146">Registry Key</span></span>|<span data-ttu-id="75cd1-147">Wartość domyślna</span><span class="sxs-lookup"><span data-stu-id="75cd1-147">Default Value</span></span>|<span data-ttu-id="75cd1-148">Opis</span><span class="sxs-lookup"><span data-stu-id="75cd1-148">Description</span></span>|  
|------------------|-------------------|-----------------|  
|<span data-ttu-id="75cd1-149">EnableNonUTF8</span><span class="sxs-lookup"><span data-stu-id="75cd1-149">EnableNonUTF8</span></span>|<span data-ttu-id="75cd1-150">1</span><span class="sxs-lookup"><span data-stu-id="75cd1-150">1</span></span>|<span data-ttu-id="75cd1-151">Jeśli zero, `http.sys` akceptuje tylko adresy URL algorytmem UTF-8.</span><span class="sxs-lookup"><span data-stu-id="75cd1-151">If zero, `http.sys` accepts only UTF-8-encoded URLs.</span></span><br /><br /> <span data-ttu-id="75cd1-152">Jeśli różna od zera, `http.sys` akceptuje także kodowaniu ANSI lub zakodowane w formacie DBCS adresy URL w żądaniach.</span><span class="sxs-lookup"><span data-stu-id="75cd1-152">If non-zero, `http.sys` also accepts ANSI-encoded or DBCS-encoded URLs in requests.</span></span>|  
|<span data-ttu-id="75cd1-153">FavorUTF8</span><span class="sxs-lookup"><span data-stu-id="75cd1-153">FavorUTF8</span></span>|<span data-ttu-id="75cd1-154">1</span><span class="sxs-lookup"><span data-stu-id="75cd1-154">1</span></span>|<span data-ttu-id="75cd1-155">Jeśli różna od zera, `http.sys` zawsze próbuje dekodowanie adresu URL jako UTF-8 najpierw; Jeśli tej konwersji nie powiedzie się i EnableNonUTF8 jest różna od zera, sterownik Http.sys, a następnie próbuje go dekodować w kodowaniu ANSI lub znaków Dwubajtowych.</span><span class="sxs-lookup"><span data-stu-id="75cd1-155">If non-zero, `http.sys` always tries to decode a URL as UTF-8 first; if that conversion fails and EnableNonUTF8 is non-zero, Http.sys then tries to decode it as ANSI or DBCS.</span></span><br /><br /> <span data-ttu-id="75cd1-156">Jeśli zero i EnableNonUTF8 jest różna od zera, `http.sys` podejmuje próbę zdekodowania kodowaniu ANSI lub znaków Dwubajtowych; Jeśli to się nie powiedzie, podejmuje próby konwersji UTF-8.</span><span class="sxs-lookup"><span data-stu-id="75cd1-156">If zero (and EnableNonUTF8 is non-zero), `http.sys` tries to decode it as ANSI or DBCS; if that is not successful, it tries a UTF-8 conversion.</span></span>|  
  
 <span data-ttu-id="75cd1-157">Gdy <xref:System.Net.HttpListener> odbiera żądanie, używa ona przekonwertowana identyfikatora URI z `http.sys` jako danych wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="75cd1-157">When <xref:System.Net.HttpListener> receives a request, it uses the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="75cd1-158">Istnieje potrzeba do obsługi znaki oprócz znaków i numery identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="75cd1-158">There is a need for supporting characters besides characters and numbers in URIs.</span></span> <span data-ttu-id="75cd1-159">Przykładem jest następujący identyfikator URI, który służy do pobierania informacji klienta dla klientów number "1/3812":</span><span class="sxs-lookup"><span data-stu-id="75cd1-159">An example is the following URI, which is used to retrieve customer information for customer number "1/3812":</span></span>  
  
 `http://www.contoso.com/Customer('1%2F3812')/`  
  
 <span data-ttu-id="75cd1-160">Należy pamiętać, ukośnika procent, kodowane w identyfikatorze Uri (% 2F).</span><span class="sxs-lookup"><span data-stu-id="75cd1-160">Note the percent-encoded slash in the Uri (%2F).</span></span> <span data-ttu-id="75cd1-161">Jest to konieczne, ponieważ w tym przypadku reprezentuje znak ukośnika, danych i nie ogranicznika ścieżka.</span><span class="sxs-lookup"><span data-stu-id="75cd1-161">This is necessary, since in this case the slash character represents data and not a path delimiter.</span></span>  
  
 <span data-ttu-id="75cd1-162">Przekazywanie ciągu identyfikatora Uri konstruktora doprowadzi do następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="75cd1-162">Passing the string to Uri constructor will lead to the following URI:</span></span>  
  
 `http://www.contoso.com/Customer('1/3812')/`  
  
 <span data-ttu-id="75cd1-163">Dzielenie ścieżkę na jej segmenty mogłoby spowodować następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="75cd1-163">Splitting the path into its segments would result in the following elements:</span></span>  
  
 `Customer('1`  
  
 `3812')`  
  
 <span data-ttu-id="75cd1-164">Nie jest celem nadawca żądania.</span><span class="sxs-lookup"><span data-stu-id="75cd1-164">This is not the intent of the sender of the request.</span></span>  
  
 <span data-ttu-id="75cd1-165">Jeśli **unescapeRequestUrl** ma ustawioną wartość atrybutu **false**, a następnie po <xref:System.Net.HttpListener> odbiera żądanie, używa raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako dane wejściowe <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="75cd1-165">If the **unescapeRequestUrl** attribute is set to **false**, then when the <xref:System.Net.HttpListener> receives a request, it uses the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
 <span data-ttu-id="75cd1-166">Wartością domyślną dla **unescapeRequestUrl** atrybut jest **true**.</span><span class="sxs-lookup"><span data-stu-id="75cd1-166">The default value for the **unescapeRequestUrl** attribute is **true**.</span></span>  
  
 <span data-ttu-id="75cd1-167"><xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> Właściwość może służyć do uzyskania bieżącej wartości **unescapeRequestUrl** atrybut z właściwych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="75cd1-167">The <xref:System.Net.Configuration.HttpListenerElement.UnescapeRequestUrl%2A> property can be used to get the current value of the **unescapeRequestUrl** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75cd1-168">Przykład</span><span class="sxs-lookup"><span data-stu-id="75cd1-168">Example</span></span>  
 <span data-ttu-id="75cd1-169">Poniższy przykład przedstawia sposób konfigurowania <xref:System.Net.HttpListener> klasy po odebraniu żądania do używania raw URI zamiast przekonwertowanego identyfikatora URI z `http.sys` jako danych wejściowych do <xref:System.Net.HttpListenerRequest.Url%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="75cd1-169">The following example shows how to configure the <xref:System.Net.HttpListener> class when it receives a request to use the raw URI instead of the converted URI from `http.sys` as input to the <xref:System.Net.HttpListenerRequest.Url%2A> property.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="75cd1-170">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="75cd1-170">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="75cd1-171">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="75cd1-171">Namespace</span></span>|<span data-ttu-id="75cd1-172">System.Net</span><span class="sxs-lookup"><span data-stu-id="75cd1-172">System.Net</span></span>|  
|<span data-ttu-id="75cd1-173">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="75cd1-173">Schema Name</span></span>||  
|<span data-ttu-id="75cd1-174">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="75cd1-174">Validation File</span></span>||  
|<span data-ttu-id="75cd1-175">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="75cd1-175">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="75cd1-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75cd1-176">See also</span></span>

- <xref:System.Net.Configuration.HttpListenerElement>
- <xref:System.Net.HttpListener>
- <xref:System.Net.HttpListenerRequest.Url%2A>
- [<span data-ttu-id="75cd1-177">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="75cd1-177">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
