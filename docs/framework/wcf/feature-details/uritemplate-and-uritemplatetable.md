---
title: Klasy UriTemplate i UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: b0dc3b2b747bc08da239490db7db3ba77d1e7ed8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130250"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="de73a-102">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="de73a-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="de73a-103">Deweloperzy sieci Web muszą mieć możliwość opisują kształt i układ identyfikatory URI, które ich usługom, odpowiadanie na.</span><span class="sxs-lookup"><span data-stu-id="de73a-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="de73a-104">Windows Communication Foundation (WCF) dodano dwa nowe klasy oferuje deweloperom kontrolę nad ich identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <xref:System.UriTemplate> <span data-ttu-id="de73a-105">i <xref:System.UriTemplateTable> stanowią podstawę aparatu wysyłania na podstawie identyfikatora URI programu WCF.</span><span class="sxs-lookup"><span data-stu-id="de73a-105">and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="de73a-106">Te klasy można również na mechanizmie własnych, dzięki czemu deweloperzy mogą korzystać ze szablonów i identyfikatora URI mapowania bez implementacji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="de73a-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="de73a-107">Szablony</span><span class="sxs-lookup"><span data-stu-id="de73a-107">Templates</span></span>  
 <span data-ttu-id="de73a-108">Szablon jest sposób opisania zestawu względne identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="de73a-109">Zestaw szablonów identyfikatora URI w poniższej tabeli przedstawiono, jak mogą być zdefiniowane system, który pobiera różne rodzaje informacji o pogodzie.</span><span class="sxs-lookup"><span data-stu-id="de73a-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="de73a-110">Dane</span><span class="sxs-lookup"><span data-stu-id="de73a-110">Data</span></span>|<span data-ttu-id="de73a-111">Szablon</span><span class="sxs-lookup"><span data-stu-id="de73a-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="de73a-112">Krajowe prognozy</span><span class="sxs-lookup"><span data-stu-id="de73a-112">National Forecast</span></span>|<span data-ttu-id="de73a-113">pogoda/national</span><span class="sxs-lookup"><span data-stu-id="de73a-113">weather/national</span></span>|  
|<span data-ttu-id="de73a-114">Stan prognozy</span><span class="sxs-lookup"><span data-stu-id="de73a-114">State Forecast</span></span>|<span data-ttu-id="de73a-115">pogoda / {state}</span><span class="sxs-lookup"><span data-stu-id="de73a-115">weather/{state}</span></span>|  
|<span data-ttu-id="de73a-116">Miasto prognozy</span><span class="sxs-lookup"><span data-stu-id="de73a-116">City Forecast</span></span>|<span data-ttu-id="de73a-117">pogoda / {state} / {Miasto}</span><span class="sxs-lookup"><span data-stu-id="de73a-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="de73a-118">Działanie prognozy</span><span class="sxs-lookup"><span data-stu-id="de73a-118">Activity Forecast</span></span>|<span data-ttu-id="de73a-119">pogoda / {state} / {Miasto} / {działania}</span><span class="sxs-lookup"><span data-stu-id="de73a-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="de73a-120">W tej tabeli opisano zestaw strukturalnie podobne identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="de73a-121">Każdego wpisu jest szablon identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-121">Each entry is a URI template.</span></span> <span data-ttu-id="de73a-122">Segmenty w nawiasach klamrowych opisano zmienne.</span><span class="sxs-lookup"><span data-stu-id="de73a-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="de73a-123">Segmenty w nawiasy klamrowe nie opisano ciągami tekstowymi.</span><span class="sxs-lookup"><span data-stu-id="de73a-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="de73a-124">Klasy szablonu WCF umożliwiają deweloperom używają przychodzącego identyfikatora URI, na przykład, "/ pogody/wa/seattle/cykliczny" i dopasować go do szablonu, który opisuje, "/weather/ {stan} / {Miasto} / {działania}".</span><span class="sxs-lookup"><span data-stu-id="de73a-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="de73a-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="de73a-125">UriTemplate</span></span>  
 <xref:System.UriTemplate> <span data-ttu-id="de73a-126">jest to klasa, która hermetyzuje szablon identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-126">is a class that encapsulates a URI template.</span></span> <span data-ttu-id="de73a-127">Konstruktor przyjmuje jako parametr ciągu, który definiuje szablon.</span><span class="sxs-lookup"><span data-stu-id="de73a-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="de73a-128">Ten ciąg zawiera szablon w formacie opisanym w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="de73a-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="de73a-129"><xref:System.UriTemplate> Klasa dostarcza metody, które pozwalają dopasować identyfikatora URI przychodzącego do szablonu, wygenerować identyfikator URI na podstawie szablonu, pobieranie kolekcji nazwy zmiennych, używany w szablonie, określić, czy dwa szablony są równoważne i zwraca szablonu ciąg.</span><span class="sxs-lookup"><span data-stu-id="de73a-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> <span data-ttu-id="de73a-130">pobiera adres podstawowy i Kandydat, identyfikator URI i próbuje dopasować identyfikatora URI do szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-130">takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="de73a-131">Jeśli dopasowanie się powiedzie, <xref:System.UriTemplateMatch> wystąpienie jest zwracane.</span><span class="sxs-lookup"><span data-stu-id="de73a-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="de73a-132"><xref:System.UriTemplateMatch> Obiekt zawiera podstawowy identyfikator URI Release candidate identyfikatora URI kolekcji nazwa/wartość parametrów zapytania, Tablica segmentów ścieżki względnej, kolekcji nazw i wartości zmiennych, które zostały dopasowane <xref:System.UriTemplate> wystąpienie używane do wykonania dopasowania , ciąg, który zawiera Niedopasowany jakiejkolwiek jego części Release candidate identyfikatora URI (stosowane, gdy szablon ma symbol wieloznaczny), a obiekt, który jest skojarzony z szablonem.</span><span class="sxs-lookup"><span data-stu-id="de73a-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de73a-133"><xref:System.UriTemplate> Klasy ignoruje schemat i numer portu podczas dopasowywania Release candidate identyfikatora URI do szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="de73a-134">Istnieją dwie metody, które umożliwiają Generowanie identyfikatora URI z szablonem, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="de73a-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> <span data-ttu-id="de73a-135">pobiera adres podstawowy i kolekcji nazwa/wartość parametrów.</span><span class="sxs-lookup"><span data-stu-id="de73a-135">takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="de73a-136">Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązana.</span><span class="sxs-lookup"><span data-stu-id="de73a-136">These parameters are substituted for variables when the template is bound.</span></span> <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> <span data-ttu-id="de73a-137">pobiera pary nazwa/wartość i zastępuje je od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="de73a-137">takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <xref:System.UriTemplate.ToString> <span data-ttu-id="de73a-138">Zwraca ciąg szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-138">returns the template string.</span></span>  
  
 <span data-ttu-id="de73a-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Właściwość zawiera kolekcję nazw zmiennych, używane w ramach segmenty ścieżki w parametrach szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> <span data-ttu-id="de73a-140">Trwa <xref:System.UriTemplate> jako parametr i zwraca wartość logiczną, która określa, czy dwa szablony są równoważne.</span><span class="sxs-lookup"><span data-stu-id="de73a-140">takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="de73a-141">Aby uzyskać więcej informacji zobacz sekcję szablonu równoważności w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="de73a-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <xref:System.UriTemplate> <span data-ttu-id="de73a-142">jest przeznaczona do pracy z dowolnego schematu identyfikatora URI, który jest zgodny z gramatyki identyfikator URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="de73a-142">is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="de73a-143">Poniżej przedstawiono przykłady obsługiwane schematy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="de73a-144">http://</span><span class="sxs-lookup"><span data-stu-id="de73a-144">http://</span></span>  
  
- <span data-ttu-id="de73a-145">https://</span><span class="sxs-lookup"><span data-stu-id="de73a-145">https://</span></span>  
  
- <span data-ttu-id="de73a-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="de73a-146">net.tcp://</span></span>  
  
- <span data-ttu-id="de73a-147">net.pipe://</span><span class="sxs-lookup"><span data-stu-id="de73a-147">net.pipe://</span></span>  
  
- <span data-ttu-id="de73a-148">sb://</span><span class="sxs-lookup"><span data-stu-id="de73a-148">sb://</span></span>  
  
 <span data-ttu-id="de73a-149">Schematy, takich jak file:// i urn: / / nie są zgodne z gramatyki identyfikator URI protokołu HTTP i powodować nieprzewidywalne skutki, gdy jest używana z szablonami identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="de73a-150">Składnia ciągu szablonu</span><span class="sxs-lookup"><span data-stu-id="de73a-150">Template String Syntax</span></span>  
 <span data-ttu-id="de73a-151">Szablon ma trzy części: ścieżki, opcjonalne zapytanie i fragment opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="de73a-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="de73a-152">Aby uzyskać przykład zobacz następujący szablon:</span><span class="sxs-lookup"><span data-stu-id="de73a-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="de73a-153">Ścieżka składa się z "/weather/ {stan} / {Miasto}", zapytanie składa się z"? prognozy = {length}, i zawiera fragmentu"#frag1".</span><span class="sxs-lookup"><span data-stu-id="de73a-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="de73a-154">Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="de73a-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="de73a-155">Wyrażenia zapytań i fragment można pominąć całkowicie.</span><span class="sxs-lookup"><span data-stu-id="de73a-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="de73a-156">Ścieżka składa się z szeregu segmentów rozdzielonych przez '/', każdy z segmentów może mieć wartości literału, nazwa zmiennej (napisanego w {nawiasów klamrowych}) lub symbol wieloznaczny (zapisane jako\*").</span><span class="sxs-lookup"><span data-stu-id="de73a-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="de73a-157">W szablonie poprzedniego "\weather\ segmentu jest literałem wartości podczas"{state}"i"{city}"są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="de73a-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="de73a-158">Zmienne pobrać nazwy z zawartości ich nawiasów klamrowych i ich później można zastąpić wartością konkretną wartość, aby utworzyć *zamknięte URI*.</span><span class="sxs-lookup"><span data-stu-id="de73a-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="de73a-159">Symbol wieloznaczny jest opcjonalne, ale może wystąpić tylko na końcu identyfikatora URI, których logicznie odpowiada "pozostałą część ścieżki".</span><span class="sxs-lookup"><span data-stu-id="de73a-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="de73a-160">Wyrażenie zapytania, jeśli jest obecny, określa szereg nieuporządkowaną nazwę/pary wartości rozdzielane znakami "&".</span><span class="sxs-lookup"><span data-stu-id="de73a-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="de73a-161">Elementy wyrażenia zapytania może to być literał pary (x = 2) lub pary zmiennej (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="de73a-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="de73a-162">Tylko po prawej stronie zapytania może mieć zmiennej wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="de73a-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="de73a-163">({JakaśNazwa} = {wartość someValue} nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="de73a-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="de73a-164">Niesparowane wartości (? x) nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="de73a-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="de73a-165">Nie ma żadnej różnicy między wyrażenie pustego zapytania i składający się z tylko jednego wyrażenia zapytania "?" (zarówno oznacza "dowolne zapytanie").</span><span class="sxs-lookup"><span data-stu-id="de73a-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="de73a-166">Wyrażenie fragmentacji może składać się z wartością literału, zmienne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="de73a-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="de73a-167">Wszystkie nazwy zmiennej szablonu w ciągu szablonu muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="de73a-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="de73a-168">Nazwy zmiennych szablonu jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="de73a-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="de73a-169">Przykłady ciągów prawidłowy szablon:</span><span class="sxs-lookup"><span data-stu-id="de73a-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="de73a-170">""</span><span class="sxs-lookup"><span data-stu-id="de73a-170">""</span></span>  
  
- <span data-ttu-id="de73a-171">"/ uniesienia"</span><span class="sxs-lookup"><span data-stu-id="de73a-171">"/shoe"</span></span>  
  
- <span data-ttu-id="de73a-172">"/shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="de73a-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="de73a-173">"{buta} / łodzi"</span><span class="sxs-lookup"><span data-stu-id="de73a-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="de73a-174">"{shoe}/{boat}/bed/{quilt}"</span><span class="sxs-lookup"><span data-stu-id="de73a-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="de73a-175">"uniesienia / {łodzi}"</span><span class="sxs-lookup"><span data-stu-id="de73a-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="de73a-176">"uniesienia / {łodzi} /\*"</span><span class="sxs-lookup"><span data-stu-id="de73a-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="de73a-177">"buta/łodzi? x = 2"</span><span class="sxs-lookup"><span data-stu-id="de73a-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="de73a-178">"uniesienia / {łodzi}? x = {bielizny}"</span><span class="sxs-lookup"><span data-stu-id="de73a-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="de73a-179">"uniesienia / {łodzi}? x = {bielizny} & y = poza pasmem"</span><span class="sxs-lookup"><span data-stu-id="de73a-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="de73a-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="de73a-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="de73a-181">"buta? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="de73a-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="de73a-182">Przykłady ciągów nieprawidłowy szablon:</span><span class="sxs-lookup"><span data-stu-id="de73a-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="de73a-183">"{buta} / {UNIESIENIA} / x = 2" — zduplikowane nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="de73a-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="de73a-184">"{buta} /boat/? bielizny = {buta}" — zduplikowane nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="de73a-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="de73a-185">"? x = 2 & x = 3" — pary nazwa/wartość w ciągu zapytania musi być unikatowa, nawet jeśli są literały.</span><span class="sxs-lookup"><span data-stu-id="de73a-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="de73a-186">"? x = 2 &" — ciąg zapytania jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="de73a-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="de73a-187">"? 2 & x = {buta}" — ciąg zapytania musi być pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="de73a-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="de73a-188">"? y = 2 & & X = 3" — ciąg zapytania musi być pary nazwa / wartość, nazwy nie może zaczynać 'i'.</span><span class="sxs-lookup"><span data-stu-id="de73a-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="de73a-189">Segmenty ścieżki złożona (c)</span><span class="sxs-lookup"><span data-stu-id="de73a-189">Compound Path Segments</span></span>  
 <span data-ttu-id="de73a-190">Segmenty ścieżki złożonej zezwala na pojedynczy segment ścieżki identyfikatora URI zawiera wiele zmiennych, a także zmienne w połączeniu z literałami.</span><span class="sxs-lookup"><span data-stu-id="de73a-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="de73a-191">Poniżej przedstawiono przykłady segmentów prawidłową ścieżkę złożoną.</span><span class="sxs-lookup"><span data-stu-id="de73a-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="de73a-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="de73a-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="de73a-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="de73a-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="de73a-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="de73a-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="de73a-195">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="de73a-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="de73a-196">Poniżej przedstawiono przykłady segmentów nieprawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="de73a-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="de73a-197">/{} — Zmienne musi mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="de73a-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="de73a-198">/ {uniesienia} {łodzi} — zmienne muszą być rozdzielone literału.</span><span class="sxs-lookup"><span data-stu-id="de73a-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="de73a-199">Zgodne i złożone segmenty ścieżki</span><span class="sxs-lookup"><span data-stu-id="de73a-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="de73a-200">Segmenty ścieżki złożonej umożliwiają definiowanie UriTemplate, który ma wiele zmiennych w segmencie pojedynczą ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="de73a-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="de73a-201">Na przykład w następujący ciąg szablonu: "Adresów / {state}. {Miasto} "w tym samym segmencie są zdefiniowane dwie zmienne (stanu i miasta).</span><span class="sxs-lookup"><span data-stu-id="de73a-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="de73a-202">Ten szablon będzie odpowiadać takie jak adres URL `http://example.com/Washington.Redmond` , ale również pokaże adresu URL, takich jak `http://example.com/Washington.Redmond.Microsoft`.</span><span class="sxs-lookup"><span data-stu-id="de73a-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="de73a-203">W tym ostatnim przypadku zmiennej stanu będzie zawierać "Waszyngton", a zmienna Miasto będzie zawierać "Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="de73a-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="de73a-204">W takim przypadku dowolny tekst (z wyjątkiem "/") będzie odpowiadał zmiennej {miasto}.</span><span class="sxs-lookup"><span data-stu-id="de73a-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="de73a-205">Szablon, który nie będą zgodne z tekstem "dodatkowe", umieść zmienną w segmencie oddzielne szablonu, na przykład: "Adresów / {state} / {miasto}.</span><span class="sxs-lookup"><span data-stu-id="de73a-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="de73a-206">Segmenty nazwanych symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="de73a-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="de73a-207">Segment nazwanych symboli wieloznacznych jest żadnych zmiennych segmentu ścieżki którego nazwa zmiennej zaczyna się od znaku wieloznacznego "\*".</span><span class="sxs-lookup"><span data-stu-id="de73a-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="de73a-208">Następujący ciąg szablonu zawiera nazwanych symboli wieloznacznych segment o nazwie "buta".</span><span class="sxs-lookup"><span data-stu-id="de73a-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="de73a-209">Segmenty symboli wieloznacznych, należy wykonać następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="de73a-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="de73a-210">Może być co najwyżej jeden segment nazwanych symboli wieloznacznych dla każdego ciągu szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="de73a-211">Segment o nazwie symbolu wieloznacznego musi znajdować się w segmencie najdalej z prawej strony w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="de73a-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="de73a-212">Segment o nazwie symbolu wieloznacznego nie może współistnieć z segment wieloznaczny anonimowe, w ramach tych samych parametrach szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="de73a-213">Nazwa segmentu nazwany symbol wieloznaczny musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="de73a-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="de73a-214">Segmenty, o nazwie symbolu wieloznacznego nie może mieć wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="de73a-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="de73a-215">Segmentów nazwanych symboli wieloznacznych nie może kończyć się znakiem "/".</span><span class="sxs-lookup"><span data-stu-id="de73a-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="de73a-216">Domyślne wartości zmiennej</span><span class="sxs-lookup"><span data-stu-id="de73a-216">Default Variable Values</span></span>  
 <span data-ttu-id="de73a-217">Domyślne wartości zmiennej umożliwiają określanie wartości domyślnych dla zmiennych w szablonie.</span><span class="sxs-lookup"><span data-stu-id="de73a-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="de73a-218">Domyślne zmienne można określić za pomocą nawiasów klamrowych, które Zadeklaruj zmienną lub jako kolekcja przekazany do konstruktora UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="de73a-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="de73a-219">Następujący szablon przedstawia dwa sposoby określania <xref:System.UriTemplate> za pomocą zmiennych z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="de73a-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="de73a-220">Ten szablon deklaruje zmienną o nazwie `a` z wartością domyślną `1` i zmienną o nazwie `b` z wartością domyślną `5`.</span><span class="sxs-lookup"><span data-stu-id="de73a-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de73a-221">Tylko zmienne segmentu ścieżki mogą mają przypisane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="de73a-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="de73a-222">Zmiennych ciągu zapytania, zmienne złożonego segmentu i zmiennych nazwanych symboli wieloznacznych nie mogą mieć wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="de73a-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="de73a-223">Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas dopasowywania identyfikatora URI Kandydat.</span><span class="sxs-lookup"><span data-stu-id="de73a-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");

UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);
Uri candidate = new Uri("http://localhost:8000/OR");

UriTemplateMatch m1 = t.Match(baseAddress, candidate);

Console.WriteLine($"Template: {t}");
Console.WriteLine($"Candidate URI: {candidate}");

// Display contents of BoundVariables
Console.WriteLine("BoundVariables:");
foreach (string key in m1.BoundVariables.AllKeys)
{
    Console.WriteLine($"\t{key}={m1.BoundVariables[key]}");
}
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/
// Candidate URI: http://localhost:8000/OR
// BoundVariables:
//         STATE=OR
//         CITY=Redmond
```  
  
> [!NOTE]
> <span data-ttu-id="de73a-224">Identyfikator URI, takich jak `http://localhost:8000///` jest niezgodna z szablonu wymienionych w poprzednim kodzie jednak identyfikatora URI, takich jak `http://localhost:8000/` jest.</span><span class="sxs-lookup"><span data-stu-id="de73a-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="de73a-225">Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas tworzenia identyfikatora URI za pomocą szablonu.</span><span class="sxs-lookup"><span data-stu-id="de73a-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```csharp
Uri baseAddress = new Uri("http://localhost:8000/");  
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);  
NameValueCollection vals = new NameValueCollection();  
vals.Add("a", "10");  
  
Uri boundUri = t.BindByName(baseAddress, vals);  
Console.WriteLine("BaseAddress: {0}", baseAddress);  
Console.WriteLine("Template: {0}", t.ToString());  
  
Console.WriteLine("Values: ");  
foreach (string key in vals.AllKeys)  
{  
    Console.WriteLine("\tKey = {0}, Value = {1}", key, vals[key]);  
}  
Console.WriteLine("Bound URI: {0}", boundUri);  
  
// The output of the preceding code is  
// BaseAddress: http://localhost:8000/  
// Template: /test/{a}/{b}  
// Values:  
//     Key = a, Value = 10  
// Bound URI: http://localhost:8000/test/10/5  
```  
  
<span data-ttu-id="de73a-226">Gdy zmienna ta otrzymuje wartość domyślną `null` istnieją pewne dodatkowe ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="de73a-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="de73a-227">Zmienna może mieć wartość domyślną `null` czy zmienna jest zawarty w prawo większość segment ciąg szablonu, czy wszystkie segmenty po prawej stronie segmentu mają przypisane wartości domyślne dla `null`.</span><span class="sxs-lookup"><span data-stu-id="de73a-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="de73a-228">Poniżej podano prawidłowy szablon ciągi z wartościami domyślnymi `null`:</span><span class="sxs-lookup"><span data-stu-id="de73a-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="de73a-229">Poniżej podano nieprawidłowy szablon ciągi z wartościami domyślnymi `null`:</span><span class="sxs-lookup"><span data-stu-id="de73a-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="de73a-230">Wartości domyślne i dopasowania</span><span class="sxs-lookup"><span data-stu-id="de73a-230">Default Values and Matching</span></span>  
 <span data-ttu-id="de73a-231">Podczas dopasowywania Release candidate identyfikatora URI za pomocą szablonu, który zawiera wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli wartości nie są określone w identyfikatorze URI Release candidate.</span><span class="sxs-lookup"><span data-stu-id="de73a-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="de73a-232">Template Equivalence</span><span class="sxs-lookup"><span data-stu-id="de73a-232">Template Equivalence</span></span>  
 <span data-ttu-id="de73a-233">Dwa szablony są określane jako *strukturalnie równoważne* kiedy wszystkie szablony literały odpowiadać i mają zmiennych w tej samej segmentów.</span><span class="sxs-lookup"><span data-stu-id="de73a-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="de73a-234">Na przykład poniższe szablony są strukturalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="de73a-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="de73a-235">b /b /a/ {var1} / {var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="de73a-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="de73a-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="de73a-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="de73a-238">Kilka istotnych kwestii:</span><span class="sxs-lookup"><span data-stu-id="de73a-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="de73a-239">Jeśli szablon zawiera ukośników wiodących, tylko pierwszy z nich jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="de73a-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="de73a-240">Podczas porównywania ciągi szablonu dla równoważności strukturalnych, wielkość liter jest ignorowana w nazwach zmiennych i segmenty ścieżki, ciągi zapytań jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="de73a-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="de73a-241">Ciągi zapytania są nieuporządkowane.</span><span class="sxs-lookup"><span data-stu-id="de73a-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="de73a-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="de73a-242">UriTemplateTable</span></span>  
 <span data-ttu-id="de73a-243"><xref:System.UriTemplateTable> Klasa reprezentuje asocjacyjnych tabelę <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera jego wybranie.</span><span class="sxs-lookup"><span data-stu-id="de73a-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="de73a-244">A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="de73a-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="de73a-245">Zawartość <xref:System.UriTemplateTable> można zmienić do czasu <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="de73a-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="de73a-246">Sprawdzanie poprawności jest wykonywane podczas <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="de73a-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="de73a-247">Typ weryfikacji, wykonywane są zależne od wartości `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="de73a-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="de73a-248">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `false`, <xref:System.UriTemplateTable> kontrole, aby upewnić się, Brak szablonów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="de73a-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="de73a-249">Jeśli zostaną znalezione żadne szablony strukturalnie równoważne, zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="de73a-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="de73a-250">Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gdy zachodzi potrzeba zapewnienia tylko jeden szablon pasuje do przychodzącego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="de73a-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="de73a-251">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `true`, <xref:System.UriTemplateTable> zezwala na wiele szablonów strukturalnie równoważne, muszą być zawarte w <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="de73a-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="de73a-252">Jeśli zestaw <xref:System.UriTemplate> obiekty dodane do <xref:System.UriTemplateTable> zawierających ciągi zapytań nie może być niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="de73a-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="de73a-253">Ciągi zapytań identyczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="de73a-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="de73a-254">Gdy <xref:System.UriTemplateTable> umożliwia base adresów tego schematów użycia innego niż HTTP, to schemat, a numer portu są ignorowane podczas dopasowywania Release candidate identyfikatorów URI do szablonów.</span><span class="sxs-lookup"><span data-stu-id="de73a-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="de73a-255">Niejednoznaczności ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="de73a-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="de73a-256">Szablony, które są równoważne ścieżkę udziału zawierają ciągi zapytań niejednoznaczne, jeśli identyfikator URI, który odpowiada więcej niż jeden szablon.</span><span class="sxs-lookup"><span data-stu-id="de73a-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="de73a-257">Następujące zestawy ciągów zapytań są jednoznaczne między sobą:</span><span class="sxs-lookup"><span data-stu-id="de73a-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="de73a-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-258">?x=1</span></span>  
  
- <span data-ttu-id="de73a-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="de73a-259">?x=2</span></span>  
  
- <span data-ttu-id="de73a-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="de73a-260">?x=3</span></span>  
  
- <span data-ttu-id="de73a-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="de73a-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="de73a-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="de73a-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="de73a-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="de73a-263">?x=3</span></span>  
  
- <span data-ttu-id="de73a-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-264">?x=1</span></span>  
  
- <span data-ttu-id="de73a-265">?</span><span class="sxs-lookup"><span data-stu-id="de73a-265">?</span></span>  
  
- <span data-ttu-id="de73a-266">?</span><span class="sxs-lookup"><span data-stu-id="de73a-266">?</span></span> <span data-ttu-id="de73a-267">x={var}</span><span class="sxs-lookup"><span data-stu-id="de73a-267">x={var}</span></span>  
  
- <span data-ttu-id="de73a-268">?</span><span class="sxs-lookup"><span data-stu-id="de73a-268">?</span></span>  
  
- <span data-ttu-id="de73a-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="de73a-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="de73a-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="de73a-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="de73a-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="de73a-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="de73a-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="de73a-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="de73a-273">Następujące zestawy szablony ciągów zapytania są niejednoznaczne między sobą:</span><span class="sxs-lookup"><span data-stu-id="de73a-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="de73a-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-274">?x=1</span></span>  
  
- <span data-ttu-id="de73a-275">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="de73a-275">?x={var}</span></span>  
  
 <span data-ttu-id="de73a-276">"x = 1"-dopasowuje oba szablony.</span><span class="sxs-lookup"><span data-stu-id="de73a-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="de73a-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-277">?x=1</span></span>  
  
- <span data-ttu-id="de73a-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="de73a-278">?y=2</span></span>  
  
 <span data-ttu-id="de73a-279">"x = 1 & y = 2" odpowiada oba szablony.</span><span class="sxs-lookup"><span data-stu-id="de73a-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="de73a-280">Jest to spowodowane ciągu zapytania może zawierać więcej zmiennych ciągu zapytania, a następnie dopasowuje szablon.</span><span class="sxs-lookup"><span data-stu-id="de73a-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="de73a-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="de73a-281">?x=1</span></span>  
  
- <span data-ttu-id="de73a-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="de73a-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="de73a-283">"x = 1 & y = 3" odpowiada oba szablony.</span><span class="sxs-lookup"><span data-stu-id="de73a-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="de73a-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="de73a-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="de73a-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="de73a-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de73a-286">Α znaków i Α są traktowane jako różne znaki pojawiających się jako część ścieżka identyfikatora URI lub <xref:System.UriTemplate> literał segmentu ścieżki (ale a znaków i A są traktowane jako taki sam).</span><span class="sxs-lookup"><span data-stu-id="de73a-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="de73a-287">Α znaków i Α są uznawane za te same znaki pojawiających się jako część a <xref:System.UriTemplate> {variableName} lub ciąg zapytania (i a i A są również uważana za te same znaki).</span><span class="sxs-lookup"><span data-stu-id="de73a-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de73a-288">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="de73a-288">See also</span></span>

- [<span data-ttu-id="de73a-289">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="de73a-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="de73a-290">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="de73a-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="de73a-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="de73a-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="de73a-292">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="de73a-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="de73a-293">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="de73a-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
