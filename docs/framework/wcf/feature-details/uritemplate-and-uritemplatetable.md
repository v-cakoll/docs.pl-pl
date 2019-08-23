---
title: Klasy UriTemplate i UriTemplateTable
ms.date: 03/30/2017
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
ms.openlocfilehash: f51d6fa5c78d97cf11a3c0005be7656013b30e90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955281"
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="d8e03-102">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d8e03-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="d8e03-103">Deweloperzy sieci Web wymagają możliwości opisania kształtu i układu identyfikatorów URI, na które odpowiada ich usługi.</span><span class="sxs-lookup"><span data-stu-id="d8e03-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> <span data-ttu-id="d8e03-104">Windows Communication Foundation (WCF) dodał dwie nowe klasy, aby umożliwić deweloperom kontrolę nad ich identyfikatorami URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-104">Windows Communication Foundation (WCF) added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="d8e03-105"><xref:System.UriTemplate>i <xref:System.UriTemplateTable> stanowi podstawę aparatu wysyłania opartego na identyfikatorze URI w programie WCF.</span><span class="sxs-lookup"><span data-stu-id="d8e03-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in WCF.</span></span> <span data-ttu-id="d8e03-106">Te klasy mogą być również używane samodzielnie, co pozwala deweloperom korzystać z szablonów i mechanizmu mapowania identyfikatorów URI bez implementowania usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="d8e03-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a WCF service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="d8e03-107">Szablony</span><span class="sxs-lookup"><span data-stu-id="d8e03-107">Templates</span></span>  
 <span data-ttu-id="d8e03-108">Szablon jest sposobem opisu zestawu względnych identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="d8e03-109">Zestaw szablonów identyfikatorów URI w poniższej tabeli pokazuje, jak można zdefiniować system, który pobiera różne typy informacji o pogodzie.</span><span class="sxs-lookup"><span data-stu-id="d8e03-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="d8e03-110">Dane</span><span class="sxs-lookup"><span data-stu-id="d8e03-110">Data</span></span>|<span data-ttu-id="d8e03-111">Szablon</span><span class="sxs-lookup"><span data-stu-id="d8e03-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="d8e03-112">Prognoza krajowa</span><span class="sxs-lookup"><span data-stu-id="d8e03-112">National Forecast</span></span>|<span data-ttu-id="d8e03-113">Pogoda/narodowe</span><span class="sxs-lookup"><span data-stu-id="d8e03-113">weather/national</span></span>|  
|<span data-ttu-id="d8e03-114">Prognoza stanu</span><span class="sxs-lookup"><span data-stu-id="d8e03-114">State Forecast</span></span>|<span data-ttu-id="d8e03-115">Pogoda/{State}</span><span class="sxs-lookup"><span data-stu-id="d8e03-115">weather/{state}</span></span>|  
|<span data-ttu-id="d8e03-116">Prognoza miejscowości</span><span class="sxs-lookup"><span data-stu-id="d8e03-116">City Forecast</span></span>|<span data-ttu-id="d8e03-117">Pogoda/{State}/{City}</span><span class="sxs-lookup"><span data-stu-id="d8e03-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="d8e03-118">Prognoza działań</span><span class="sxs-lookup"><span data-stu-id="d8e03-118">Activity Forecast</span></span>|<span data-ttu-id="d8e03-119">Pogoda/{State}/{City}/{Activity}</span><span class="sxs-lookup"><span data-stu-id="d8e03-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="d8e03-120">W tej tabeli opisano zestaw podobnych identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="d8e03-121">Każdy wpis jest szablonem identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-121">Each entry is a URI template.</span></span> <span data-ttu-id="d8e03-122">Segmenty w nawiasach klamrowych opisują zmienne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="d8e03-123">Segmenty nie w nawiasach klamrowych opisują ciągi literału.</span><span class="sxs-lookup"><span data-stu-id="d8e03-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="d8e03-124">Klasy szablonów WCF umożliwiają deweloperowi przejęcie przychodzącego identyfikatora URI, na przykład "/Weather/wa/Seattle/Cycling" i dopasowanie go do szablonu opisującego go, "/Weather/{State}/{City}/{Activity}".</span><span class="sxs-lookup"><span data-stu-id="d8e03-124">The WCF template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="d8e03-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8e03-125">UriTemplate</span></span>  
 <span data-ttu-id="d8e03-126"><xref:System.UriTemplate>jest klasą, która hermetyzuje szablon identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="d8e03-127">Konstruktor przyjmuje parametr ciągu, który definiuje szablon.</span><span class="sxs-lookup"><span data-stu-id="d8e03-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="d8e03-128">Ten ciąg zawiera szablon w formacie opisanym w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d8e03-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="d8e03-129"><xref:System.UriTemplate> Klasa zawiera metody, które umożliwiają dopasowanie przychodzącego identyfikatora URI do szablonu, generowanie identyfikatora URI na podstawie szablonu, pobieranie kolekcji nazw zmiennych używanych w szablonie, określanie, czy dwa szablony są równoważne i zwracają szablon parametry.</span><span class="sxs-lookup"><span data-stu-id="d8e03-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="d8e03-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>Pobiera adres podstawowy i identyfikator URI kandydata, a następnie próbuje dopasować identyfikator URI do szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="d8e03-131">Jeśli dopasowanie zakończyło się pomyślnie <xref:System.UriTemplateMatch> , zostanie zwrócone wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="d8e03-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="d8e03-132">Obiekt zawiera podstawowy identyfikator URI, identyfikator URI kandydata, kolekcję nazw/wartości parametrów zapytania, tablicę segmentów ścieżki względnej, kolekcję nazw/wartości zmiennych, które zostały dopasowane <xref:System.UriTemplate> , wystąpienie użyte do przeprowadzenia dopasowania <xref:System.UriTemplateMatch> , ciąg, który zawiera niedopasowaną część identyfikatora URI kandydata (używany, gdy szablon ma symbol wieloznaczny), oraz obiekt, który jest skojarzony z szablonem.</span><span class="sxs-lookup"><span data-stu-id="d8e03-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8e03-133"><xref:System.UriTemplate> Klasa ignoruje schemat i numer portu podczas dopasowywania do szablonu identyfikatora URI kandydata.</span><span class="sxs-lookup"><span data-stu-id="d8e03-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="d8e03-134">Istnieją dwie metody, które umożliwiają generowanie identyfikatora URI na podstawie szablonu <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i. <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29></span><span class="sxs-lookup"><span data-stu-id="d8e03-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="d8e03-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>przyjmuje adres podstawowy i kolekcję nazw/wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="d8e03-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="d8e03-136">Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="d8e03-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="d8e03-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>przyjmuje pary nazwa/wartość i zastępuje je lewej strony.</span><span class="sxs-lookup"><span data-stu-id="d8e03-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="d8e03-138"><xref:System.UriTemplate.ToString>Zwraca ciąg szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="d8e03-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Właściwość zawiera kolekcję nazw zmiennych używanych w segmentach ścieżki w ciągu szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="d8e03-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29><xref:System.UriTemplate> przyjmuje jako parametr i zwraca wartość logiczną określającą, czy dwa szablony są równoważne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> <span data-ttu-id="d8e03-141">Aby uzyskać więcej informacji, zobacz sekcję równoważność szablonu w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-141">For more information, see the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="d8e03-142"><xref:System.UriTemplate>Program jest przeznaczony do pracy z dowolnym schematem identyfikatorów URI, który jest zgodny z gramatyką URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="d8e03-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="d8e03-143">Poniżej przedstawiono przykłady obsługiwanych schematów URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-143">The following are examples of supported URI schemes.</span></span>  
  
- <span data-ttu-id="d8e03-144">http://</span><span class="sxs-lookup"><span data-stu-id="d8e03-144">http://</span></span>  
  
- <span data-ttu-id="d8e03-145">https://</span><span class="sxs-lookup"><span data-stu-id="d8e03-145">https://</span></span>  
  
- <span data-ttu-id="d8e03-146">net.tcp://</span><span class="sxs-lookup"><span data-stu-id="d8e03-146">net.tcp://</span></span>  
  
- <span data-ttu-id="d8e03-147">NET. pipe://</span><span class="sxs-lookup"><span data-stu-id="d8e03-147">net.pipe://</span></span>  
  
- <span data-ttu-id="d8e03-148">sb://</span><span class="sxs-lookup"><span data-stu-id="d8e03-148">sb://</span></span>  
  
 <span data-ttu-id="d8e03-149">Schematy, takie jak file://i urn://, nie są zgodne z gramatyką URI HTTP i powodują nieprzewidywalne wyniki w przypadku używania z szablonami identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="d8e03-150">Składnia ciągu szablonu</span><span class="sxs-lookup"><span data-stu-id="d8e03-150">Template String Syntax</span></span>  
 <span data-ttu-id="d8e03-151">Szablon składa się z trzech części: ścieżki, opcjonalnego zapytania i opcjonalnego fragmentu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="d8e03-152">Aby zapoznać się z przykładem, zobacz następujący szablon:</span><span class="sxs-lookup"><span data-stu-id="d8e03-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="d8e03-153">Ścieżka składa się z "/Weather/{State}/{City}", zapytanie składa się z "? Prognoza = {Length}, a fragment składa się z" #frag1 ".</span><span class="sxs-lookup"><span data-stu-id="d8e03-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="d8e03-154">Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="d8e03-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="d8e03-155">Wyrażenia zapytania i fragmentu można pominąć całkowicie.</span><span class="sxs-lookup"><span data-stu-id="d8e03-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="d8e03-156">Ścieżka składa się z serii segmentów rozdzielonych znakiem "/", każdy segment może mieć wartość literału, nazwę zmiennej (zapisaną w {nawiasy klamrowe}) lub symbol wieloznaczny (\*zapisany jako "").</span><span class="sxs-lookup"><span data-stu-id="d8e03-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="d8e03-157">W poprzednim szablonie "segment \weather\ jest wartością literału, podczas gdy" {State} "i" {City} "są zmiennymi.</span><span class="sxs-lookup"><span data-stu-id="d8e03-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="d8e03-158">Zmienne przyjmują swoją nazwę z zawartości swoich nawiasów klamrowych i później mogą zostać zastąpione konkretną wartością w celu utworzenia *zamkniętego identyfikatora URI*.</span><span class="sxs-lookup"><span data-stu-id="d8e03-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="d8e03-159">Symbol wieloznaczny jest opcjonalny, ale może występować tylko na końcu identyfikatora URI, gdzie logicznie pasuje do "reszty ścieżki".</span><span class="sxs-lookup"><span data-stu-id="d8e03-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="d8e03-160">Wyrażenie zapytania, jeśli istnieje, określa serię nieuporządkowanych par nazwa/wartość, które są ograniczone przez "&".</span><span class="sxs-lookup"><span data-stu-id="d8e03-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="d8e03-161">Elementy wyrażenia zapytania mogą być parami literałów (x = 2) lub parę zmiennej (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="d8e03-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="d8e03-162">Tylko prawa strona zapytania może mieć wyrażenie zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d8e03-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="d8e03-163">({niektóre} = {wartość someValue} są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="d8e03-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="d8e03-164">Wartości niesparowane (? x) są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="d8e03-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="d8e03-165">Nie ma różnicy między pustym wyrażeniem zapytania i wyrażeniem zapytania składającym się z tylko jednego elementu "?" (oba oznaczają "dowolne zapytanie").</span><span class="sxs-lookup"><span data-stu-id="d8e03-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="d8e03-166">Wyrażenie fragmentu może składać się z wartości literału, ale nie są dozwolone żadne zmienne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="d8e03-167">Wszystkie nazwy zmiennych szablonu w ciągu szablonu muszą być unikatowe.</span><span class="sxs-lookup"><span data-stu-id="d8e03-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="d8e03-168">Nazwy zmiennych szablonów nie uwzględniają wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="d8e03-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="d8e03-169">Przykłady prawidłowych ciągów szablonu:</span><span class="sxs-lookup"><span data-stu-id="d8e03-169">Examples of valid template strings:</span></span>  
  
- <span data-ttu-id="d8e03-170">""</span><span class="sxs-lookup"><span data-stu-id="d8e03-170">""</span></span>  
  
- <span data-ttu-id="d8e03-171">"/shoe"</span><span class="sxs-lookup"><span data-stu-id="d8e03-171">"/shoe"</span></span>  
  
- <span data-ttu-id="d8e03-172">"/Shoe/\*"</span><span class="sxs-lookup"><span data-stu-id="d8e03-172">"/shoe/\*"</span></span>  
  
- <span data-ttu-id="d8e03-173">"{szczęka}/Boat"</span><span class="sxs-lookup"><span data-stu-id="d8e03-173">"{shoe}/boat"</span></span>  
  
- <span data-ttu-id="d8e03-174">"{szczęka}/{Boat}/Bed/{Quilt}"</span><span class="sxs-lookup"><span data-stu-id="d8e03-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
- <span data-ttu-id="d8e03-175">"obuwie/{łodzi}"</span><span class="sxs-lookup"><span data-stu-id="d8e03-175">"shoe/{boat}"</span></span>  
  
- <span data-ttu-id="d8e03-176">"szczęka/{łodzi}\*/"</span><span class="sxs-lookup"><span data-stu-id="d8e03-176">"shoe/{boat}/\*"</span></span>  
  
- <span data-ttu-id="d8e03-177">"obuwie/łódź? x = 2"</span><span class="sxs-lookup"><span data-stu-id="d8e03-177">"shoe/boat?x=2"</span></span>  
  
- <span data-ttu-id="d8e03-178">"obuwie/{łodzi}? x = {łóżka}"</span><span class="sxs-lookup"><span data-stu-id="d8e03-178">"shoe/{boat}?x={bed}"</span></span>  
  
- <span data-ttu-id="d8e03-179">"obuwie/{łodzi}? x = {łóżka} & y = pasmo"</span><span class="sxs-lookup"><span data-stu-id="d8e03-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
- <span data-ttu-id="d8e03-180">"?x={shoe}"</span><span class="sxs-lookup"><span data-stu-id="d8e03-180">"?x={shoe}"</span></span>  
  
- <span data-ttu-id="d8e03-181">"obuwie? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="d8e03-182">Przykłady nieprawidłowych ciągów szablonu:</span><span class="sxs-lookup"><span data-stu-id="d8e03-182">Examples of invalid template strings:</span></span>  
  
- <span data-ttu-id="d8e03-183">"{szczęka}/{SHOE}/x = 2" — zduplikowane nazwy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d8e03-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="d8e03-184">"{szczęka}/Boat/? łóżka = {szczęka}" — zduplikowane nazwy zmiennych.</span><span class="sxs-lookup"><span data-stu-id="d8e03-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
- <span data-ttu-id="d8e03-185">"? x = 2 & x = 3" — pary nazwa/wartość w ciągu zapytania muszą być unikatowe, nawet jeśli są literałami.</span><span class="sxs-lookup"><span data-stu-id="d8e03-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
- <span data-ttu-id="d8e03-186">"? x = 2 &" — ciąg zapytania jest źle sformułowany.</span><span class="sxs-lookup"><span data-stu-id="d8e03-186">"?x=2&" – Query string is malformed.</span></span>  
  
- <span data-ttu-id="d8e03-187">"? 2 & x = {szczęka}" — ciąg zapytania musi być par nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="d8e03-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
- <span data-ttu-id="d8e03-188">"? y = 2 & & X = 3" — ciąg zapytania musi być parami wartości nazwy, nazwy nie mogą rozpoczynać się od "&".</span><span class="sxs-lookup"><span data-stu-id="d8e03-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="d8e03-189">Segmenty ścieżki złożonej</span><span class="sxs-lookup"><span data-stu-id="d8e03-189">Compound Path Segments</span></span>  
 <span data-ttu-id="d8e03-190">Segmenty ścieżki złożonej umożliwiają pojedynczemu segmentowi ścieżki URI zawiera wiele zmiennych, a także zmienne połączone z literałami.</span><span class="sxs-lookup"><span data-stu-id="d8e03-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="d8e03-191">Poniżej przedstawiono przykłady prawidłowych segmentów ścieżki złożonej.</span><span class="sxs-lookup"><span data-stu-id="d8e03-191">The following are examples of valid compound path segments.</span></span>  
  
- <span data-ttu-id="d8e03-192">/filename.{ext}/</span><span class="sxs-lookup"><span data-stu-id="d8e03-192">/filename.{ext}/</span></span>  
  
- <span data-ttu-id="d8e03-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="d8e03-193">/{filename}.jpg/</span></span>  
  
- <span data-ttu-id="d8e03-194">/{filename}.{ext}/</span><span class="sxs-lookup"><span data-stu-id="d8e03-194">/{filename}.{ext}/</span></span>  
  
- <span data-ttu-id="d8e03-195">/{a}.{b}someLiteral{c}({d})/</span><span class="sxs-lookup"><span data-stu-id="d8e03-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="d8e03-196">Poniżej przedstawiono przykłady nieprawidłowych segmentów ścieżek.</span><span class="sxs-lookup"><span data-stu-id="d8e03-196">The following are examples of invalid path segments.</span></span>  
  
- <span data-ttu-id="d8e03-197">{} Zmienne muszą mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="d8e03-197">/{} - Variables must be named.</span></span>  
  
- <span data-ttu-id="d8e03-198">/{Shoe}{Boat} — zmienne muszą być rozdzielone literałem.</span><span class="sxs-lookup"><span data-stu-id="d8e03-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="d8e03-199">Dopasowywanie i złożone segmenty ścieżki</span><span class="sxs-lookup"><span data-stu-id="d8e03-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="d8e03-200">Segmenty ścieżki złożonej umożliwiają zdefiniowanie elementu UriTemplate, który ma wiele zmiennych w obrębie jednego segmentu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="d8e03-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="d8e03-201">Na przykład, w następującym ciągu szablonu: "Addresss/{State}. {Miasto} "dwie zmienne (województwo i miejscowość) są zdefiniowane w obrębie tego samego segmentu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="d8e03-202">Ten szablon będzie pasował do adresu URL, `http://example.com/Washington.Redmond` takiego jak, ale również będzie pasował do `http://example.com/Washington.Redmond.Microsoft`adresu URL, takiego jak.</span><span class="sxs-lookup"><span data-stu-id="d8e03-202">This template would match a URL such as `http://example.com/Washington.Redmond` but it will also match an URL like `http://example.com/Washington.Redmond.Microsoft`.</span></span> <span data-ttu-id="d8e03-203">W tym ostatnim przypadku zmienna stanu będzie zawierać wartość "Waszyngton", a zmienna miasto będzie zawierać "Redmond. Microsoft".</span><span class="sxs-lookup"><span data-stu-id="d8e03-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="d8e03-204">W takim przypadku dowolny tekst (z wyjątkiem "/") będzie pasował do zmiennej {City}.</span><span class="sxs-lookup"><span data-stu-id="d8e03-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="d8e03-205">Jeśli chcesz, aby szablon, który nie był zgodny z tekstem "Extra", umieść zmienną w osobnym segmencie szablonu, na przykład: "Addresss/{State}/{City}.</span><span class="sxs-lookup"><span data-stu-id="d8e03-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="d8e03-206">Nazwane segmenty wieloznaczne</span><span class="sxs-lookup"><span data-stu-id="d8e03-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="d8e03-207">Nazwany segment symboli wieloznacznych jest dowolnym segmentem zmiennej PATH, którego nazwa zmiennej zaczyna się\*od symbolu wieloznacznego "".</span><span class="sxs-lookup"><span data-stu-id="d8e03-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘\*’.</span></span> <span data-ttu-id="d8e03-208">Następujący ciąg szablonu zawiera nazwany segment wieloznaczny o nazwie "obuwie".</span><span class="sxs-lookup"><span data-stu-id="d8e03-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="d8e03-209">Wieloznaczne segmenty muszą być zgodne z następującymi regułami:</span><span class="sxs-lookup"><span data-stu-id="d8e03-209">Wildcard segments must follow the following rules:</span></span>  
  
- <span data-ttu-id="d8e03-210">Dla każdego ciągu szablonu może istnieć co najwyżej jeden nazwany segment wieloznaczny.</span><span class="sxs-lookup"><span data-stu-id="d8e03-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
- <span data-ttu-id="d8e03-211">Nazwany segment symboli wieloznacznych musi znajdować się w segmencie znajdującym się w prawym największej ścieżce.</span><span class="sxs-lookup"><span data-stu-id="d8e03-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
- <span data-ttu-id="d8e03-212">Nazwany segment wieloznaczny nie może współistnieć z anonimowym segmentem wieloznacznym w tym samym ciągu szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
- <span data-ttu-id="d8e03-213">Nazwa pojedynczego segmentu wieloznacznego musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="d8e03-213">The name of a named wildcard segment must be unique.</span></span>  
  
- <span data-ttu-id="d8e03-214">Nazwane segmenty wieloznaczne nie mogą mieć wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d8e03-214">Named wildcard segments cannot have default values.</span></span>  
  
- <span data-ttu-id="d8e03-215">Nazwane segmenty wieloznaczne nie mogą kończyć się znakiem "/".</span><span class="sxs-lookup"><span data-stu-id="d8e03-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="d8e03-216">Domyślne wartości zmiennych</span><span class="sxs-lookup"><span data-stu-id="d8e03-216">Default Variable Values</span></span>  
 <span data-ttu-id="d8e03-217">Domyślne wartości zmiennych umożliwiają określanie wartości domyślnych dla zmiennych w ramach szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="d8e03-218">Zmienne domyślne można określić za pomocą nawiasów klamrowych, które deklarują zmienną lub jako kolekcję przekazaną do konstruktora UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="d8e03-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="d8e03-219">Poniższy szablon przedstawia dwa sposoby określania <xref:System.UriTemplate> zmiennych z wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="d8e03-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```csharp
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="d8e03-220">Ten szablon deklaruje zmienną o `a` nazwie z `1` wartością domyślną i zmienną o nazwie `b` z wartością `5`domyślną.</span><span class="sxs-lookup"><span data-stu-id="d8e03-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8e03-221">Tylko zmienne segmentu ścieżki mogą mieć wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="d8e03-222">Zmienne ciągu zapytania, zmienne segmentu złożonego i nazwane zmienne symboli wieloznacznych nie mogą mieć wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="d8e03-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="d8e03-223">Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas dopasowywania identyfikatora URI kandydata.</span><span class="sxs-lookup"><span data-stu-id="d8e03-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
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
> <span data-ttu-id="d8e03-224">Identyfikator URI, taki `http://localhost:8000///` jak nie jest zgodny z szablonem wymienionym w powyższym kodzie, jednak `http://localhost:8000/` identyfikator URI, taki jak.</span><span class="sxs-lookup"><span data-stu-id="d8e03-224">A URI such as `http://localhost:8000///` does not match the template listed in the preceding code, however a URI such as `http://localhost:8000/` does.</span></span>  
  
 <span data-ttu-id="d8e03-225">Poniższy kod pokazuje, jak domyślne wartości zmiennych są obsługiwane podczas tworzenia identyfikatora URI przy użyciu szablonu.</span><span class="sxs-lookup"><span data-stu-id="d8e03-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
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
  
<span data-ttu-id="d8e03-226">Gdy zmienna otrzymuje wartość `null` domyślną, istnieją pewne dodatkowe ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="d8e03-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="d8e03-227">Zmienna może mieć wartość `null` domyślną, jeśli zmienna jest zawarta w prawym najbardziej segmencie ciągu szablonu lub jeśli wszystkie segmenty z prawej strony segmentu mają `null`wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="d8e03-228">Poniżej podano prawidłowe ciągi szablonów z wartościami `null`domyślnymi:</span><span class="sxs-lookup"><span data-stu-id="d8e03-228">The following are valid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("shoe/{boat=null}");`

- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");`
  
- `UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");`

 <span data-ttu-id="d8e03-229">Poniżej znajdują się nieprawidłowe ciągi szablonów z wartościami `null`domyślnymi:</span><span class="sxs-lookup"><span data-stu-id="d8e03-229">The following are invalid template strings with default values of `null`:</span></span>  
  
- `UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment`
  
- `UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value`

### <a name="default-values-and-matching"></a><span data-ttu-id="d8e03-230">Wartości domyślne i dopasowanie</span><span class="sxs-lookup"><span data-stu-id="d8e03-230">Default Values and Matching</span></span>  
 <span data-ttu-id="d8e03-231">W przypadku dopasowania identyfikatora URI kandydata z szablonem, który ma wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli wartości nie są określone w identyfikatorze URI kandydata.</span><span class="sxs-lookup"><span data-stu-id="d8e03-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="d8e03-232">Równoważność szablonu</span><span class="sxs-lookup"><span data-stu-id="d8e03-232">Template Equivalence</span></span>  
 <span data-ttu-id="d8e03-233">Dwa szablony są uważane za *strukturalnie równoważne* , gdy wszystkie literały szablonów pasują do siebie i mają zmienne w tych samych segmentach.</span><span class="sxs-lookup"><span data-stu-id="d8e03-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="d8e03-234">Na przykład następujące szablony są strukturalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="d8e03-234">For example the following templates are structurally equivalent:</span></span>  
  
- <span data-ttu-id="d8e03-235">/a/{var1}/b b/{var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="d8e03-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
- <span data-ttu-id="d8e03-236">a/{x}/b%20b/{var1}?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
- <span data-ttu-id="d8e03-237">a/{y}/B%20B/{z}/?y=2&x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="d8e03-238">Kilka kwestii, które należy zauważyć:</span><span class="sxs-lookup"><span data-stu-id="d8e03-238">A few things to notice:</span></span>  
  
- <span data-ttu-id="d8e03-239">Jeśli szablon zawiera wiodące ukośniki, tylko pierwszy z nich jest ignorowany.</span><span class="sxs-lookup"><span data-stu-id="d8e03-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
- <span data-ttu-id="d8e03-240">Podczas porównywania ciągów szablonów dla równoważności strukturalnej, wielkość liter jest ignorowana w przypadku nazw zmiennych i segmentów ścieżki, w których ciągi zapytań są rozróżniane wielkości liter.</span><span class="sxs-lookup"><span data-stu-id="d8e03-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
- <span data-ttu-id="d8e03-241">Ciągi zapytań są nieuporządkowane.</span><span class="sxs-lookup"><span data-stu-id="d8e03-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="d8e03-242">UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="d8e03-242">UriTemplateTable</span></span>  
 <span data-ttu-id="d8e03-243">Klasa reprezentuje tabelę asocjacyjną obiektów powiązaną z obiektem wyboru dewelopera. <xref:System.UriTemplate> <xref:System.UriTemplateTable></span><span class="sxs-lookup"><span data-stu-id="d8e03-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="d8e03-244">A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="d8e03-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="d8e03-245">Zawartość elementu <xref:System.UriTemplateTable> można zmienić do momentu <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> wywołania.</span><span class="sxs-lookup"><span data-stu-id="d8e03-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="d8e03-246">Walidacja jest wykonywana <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> , gdy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d8e03-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="d8e03-247">Typ wykonywanej walidacji zależy od wartości `allowMultiple` parametru do. <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29></span><span class="sxs-lookup"><span data-stu-id="d8e03-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="d8e03-248">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana `false`, <xref:System.UriTemplateTable> sprawdza, czy nie ma żadnych szablonów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="d8e03-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="d8e03-249">W przypadku znalezienia wszelkich odpowiedników strukturalnych szablony zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d8e03-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="d8e03-250">Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> , gdy chcesz zapewnić, że tylko jeden szablon pasuje do przychodzącego identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="d8e03-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="d8e03-251">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest nazywana `true`przekazywaniem <xref:System.UriTemplateTable> , umożliwia korzystanie z wielu szablonów równoważnych, które mają być zawarte <xref:System.UriTemplateTable>w.</span><span class="sxs-lookup"><span data-stu-id="d8e03-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="d8e03-252">Jeśli zestaw <xref:System.UriTemplate> obiektów dodanych do zawiera ciągi <xref:System.UriTemplateTable> zapytania, nie mogą być niejednoznaczne.</span><span class="sxs-lookup"><span data-stu-id="d8e03-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="d8e03-253">Identyczne ciągi zapytań są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="d8e03-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8e03-254">Chociaż zezwala <xref:System.UriTemplateTable> na adresy podstawowe wykorzystujące schematy inne niż http, schemat i numer portu są ignorowane podczas dopasowywania identyfikatorów URI kandydujących do szablonów.</span><span class="sxs-lookup"><span data-stu-id="d8e03-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="d8e03-255">Niejednoznaczność ciągu zapytania</span><span class="sxs-lookup"><span data-stu-id="d8e03-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="d8e03-256">Szablony, które współdzielą równoważną ścieżkę, zawierają niejednoznaczne ciągi zapytań, jeśli istnieje identyfikator URI, który odpowiada więcej niż jednemu szablonowi.</span><span class="sxs-lookup"><span data-stu-id="d8e03-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="d8e03-257">Następujące zestawy ciągów zapytań są niejednoznaczne w samym sobie:</span><span class="sxs-lookup"><span data-stu-id="d8e03-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
- <span data-ttu-id="d8e03-258">?x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-258">?x=1</span></span>  
  
- <span data-ttu-id="d8e03-259">?x=2</span><span class="sxs-lookup"><span data-stu-id="d8e03-259">?x=2</span></span>  
  
- <span data-ttu-id="d8e03-260">?x=3</span><span class="sxs-lookup"><span data-stu-id="d8e03-260">?x=3</span></span>  
  
- <span data-ttu-id="d8e03-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-261">?x=1&y={var}</span></span>  
  
- <span data-ttu-id="d8e03-262">?x=2&z={var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-262">?x=2&z={var}</span></span>  
  
- <span data-ttu-id="d8e03-263">?x=3</span><span class="sxs-lookup"><span data-stu-id="d8e03-263">?x=3</span></span>  
  
- <span data-ttu-id="d8e03-264">?x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-264">?x=1</span></span>  
  
- <span data-ttu-id="d8e03-265">?</span><span class="sxs-lookup"><span data-stu-id="d8e03-265">?</span></span>  
  
- <span data-ttu-id="d8e03-266">?</span><span class="sxs-lookup"><span data-stu-id="d8e03-266">?</span></span> <span data-ttu-id="d8e03-267">x = {var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-267">x={var}</span></span>  
  
- <span data-ttu-id="d8e03-268">?</span><span class="sxs-lookup"><span data-stu-id="d8e03-268">?</span></span>  
  
- <span data-ttu-id="d8e03-269">?m=get&c=rss</span><span class="sxs-lookup"><span data-stu-id="d8e03-269">?m=get&c=rss</span></span>  
  
- <span data-ttu-id="d8e03-270">?m=put&c=rss</span><span class="sxs-lookup"><span data-stu-id="d8e03-270">?m=put&c=rss</span></span>  
  
- <span data-ttu-id="d8e03-271">?m=get&c=atom</span><span class="sxs-lookup"><span data-stu-id="d8e03-271">?m=get&c=atom</span></span>  
  
- <span data-ttu-id="d8e03-272">?m=put&c=atom</span><span class="sxs-lookup"><span data-stu-id="d8e03-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="d8e03-273">Następujące zestawy szablonów ciągu zapytania są niejednoznaczne w obrębie siebie:</span><span class="sxs-lookup"><span data-stu-id="d8e03-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
- <span data-ttu-id="d8e03-274">?x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-274">?x=1</span></span>  
  
- <span data-ttu-id="d8e03-275">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-275">?x={var}</span></span>  
  
 <span data-ttu-id="d8e03-276">"x = 1" — dopasowuje oba szablony.</span><span class="sxs-lookup"><span data-stu-id="d8e03-276">"x=1" - Matches both templates.</span></span>  
  
- <span data-ttu-id="d8e03-277">?x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-277">?x=1</span></span>  
  
- <span data-ttu-id="d8e03-278">?y=2</span><span class="sxs-lookup"><span data-stu-id="d8e03-278">?y=2</span></span>  
  
 <span data-ttu-id="d8e03-279">"x = 1 & y = 2" pasuje do obu szablonów.</span><span class="sxs-lookup"><span data-stu-id="d8e03-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="d8e03-280">Wynika to z faktu, że ciąg zapytania może zawierać więcej zmiennych ciągu zapytania, a następnie szablon, który jest zgodny.</span><span class="sxs-lookup"><span data-stu-id="d8e03-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
- <span data-ttu-id="d8e03-281">?x=1</span><span class="sxs-lookup"><span data-stu-id="d8e03-281">?x=1</span></span>  
  
- <span data-ttu-id="d8e03-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="d8e03-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="d8e03-283">"x = 1 & y = 3" dopasowuje oba szablony.</span><span class="sxs-lookup"><span data-stu-id="d8e03-283">"x=1&y=3" matches both templates.</span></span>  
  
- <span data-ttu-id="d8e03-284">?x=3&y=4</span><span class="sxs-lookup"><span data-stu-id="d8e03-284">?x=3&y=4</span></span>  
  
- <span data-ttu-id="d8e03-285">?x=3&z=5</span><span class="sxs-lookup"><span data-stu-id="d8e03-285">?x=3&z=5</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8e03-286">Znaki i i. są uważane za różne znaki, gdy są wyświetlane jako część ścieżki URI lub <xref:System.UriTemplate> literału segmentu ścieżki (ale znaki a i a są uważane za takie same).</span><span class="sxs-lookup"><span data-stu-id="d8e03-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="d8e03-287">Znaki i, są uznawane za te same znaki, gdy pojawiają się jako część <xref:System.UriTemplate> {VariableName} lub ciągu zapytania (a i a są również uznawane za te same znaki).</span><span class="sxs-lookup"><span data-stu-id="d8e03-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8e03-288">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8e03-288">See also</span></span>

- [<span data-ttu-id="d8e03-289">Omówienie modelu programowania usług HTTP w sieci Web przy użyciu programu WCF</span><span class="sxs-lookup"><span data-stu-id="d8e03-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)
- [<span data-ttu-id="d8e03-290">Model obiektowy programowania protokołu HTTP sieci Web w programie WCF</span><span class="sxs-lookup"><span data-stu-id="d8e03-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
- [<span data-ttu-id="d8e03-291">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8e03-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
- [<span data-ttu-id="d8e03-292">Tabela UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8e03-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="d8e03-293">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="d8e03-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
