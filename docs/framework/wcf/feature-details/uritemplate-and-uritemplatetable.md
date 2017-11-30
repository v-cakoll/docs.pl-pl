---
title: Klasy UriTemplate i UriTemplateTable
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cbbe03f-4a9e-4d44-9e02-c5773239cf52
caps.latest.revision: "24"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7ef3f2a71280595d58291863a1852cc4c590008c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="uritemplate-and-uritemplatetable"></a><span data-ttu-id="07699-102">Klasy UriTemplate i UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="07699-102">UriTemplate and UriTemplateTable</span></span>
<span data-ttu-id="07699-103">Deweloperzy sieci Web wymagają możliwości opis kształtu i układu identyfikatory URI, które odpowiadają swoich usług.</span><span class="sxs-lookup"><span data-stu-id="07699-103">Web developers require the ability to describe the shape and layout of the URIs that their services respond to.</span></span> [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="07699-104">dodano dwa nowe klasy umożliwiają deweloperom kontrolę nad ich identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="07699-104"> added two new classes to give developers control over their URIs.</span></span> <span data-ttu-id="07699-105"><xref:System.UriTemplate>i <xref:System.UriTemplateTable> stanowią podstawę aparat wysyłki na podstawie identyfikatora URI w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07699-105"><xref:System.UriTemplate> and <xref:System.UriTemplateTable> form the basis of the URI-based dispatch engine in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="07699-106">Te klasy można również na ich własnych, dzięki czemu deweloperzy mógł korzystać z szablonów i mechanizmu mapowanie identyfikatora URI bez stosowania [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi.</span><span class="sxs-lookup"><span data-stu-id="07699-106">These classes can also be used on their own, allowing developers to take advantage of templates and the URI mapping mechanism without implementing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
## <a name="templates"></a><span data-ttu-id="07699-107">Szablony</span><span class="sxs-lookup"><span data-stu-id="07699-107">Templates</span></span>  
 <span data-ttu-id="07699-108">Szablon jest umożliwia opisywanie zestaw względne identyfikatory URI.</span><span class="sxs-lookup"><span data-stu-id="07699-108">A template is a way to describe a set of relative URIs.</span></span> <span data-ttu-id="07699-109">Zestaw szablonów identyfikatora URI w poniższej tabeli pokazano, jak można zdefiniować systemu, które pobierają różne rodzaje informacji o pogodzie.</span><span class="sxs-lookup"><span data-stu-id="07699-109">The set of URI templates in the following table shows how a system that retrieves various types of weather information might be defined.</span></span>  
  
|<span data-ttu-id="07699-110">Dane</span><span class="sxs-lookup"><span data-stu-id="07699-110">Data</span></span>|<span data-ttu-id="07699-111">Szablon</span><span class="sxs-lookup"><span data-stu-id="07699-111">Template</span></span>|  
|----------|--------------|  
|<span data-ttu-id="07699-112">Prognozy National</span><span class="sxs-lookup"><span data-stu-id="07699-112">National Forecast</span></span>|<span data-ttu-id="07699-113">pogody/national</span><span class="sxs-lookup"><span data-stu-id="07699-113">weather/national</span></span>|  
|<span data-ttu-id="07699-114">Prognozy stanu</span><span class="sxs-lookup"><span data-stu-id="07699-114">State Forecast</span></span>|<span data-ttu-id="07699-115">pogody / {stanu}</span><span class="sxs-lookup"><span data-stu-id="07699-115">weather/{state}</span></span>|  
|<span data-ttu-id="07699-116">Prognozy miasta</span><span class="sxs-lookup"><span data-stu-id="07699-116">City Forecast</span></span>|<span data-ttu-id="07699-117">pogody / {stanu} / {Miasto}</span><span class="sxs-lookup"><span data-stu-id="07699-117">weather/{state}/{city}</span></span>|  
|<span data-ttu-id="07699-118">Prognozy działania</span><span class="sxs-lookup"><span data-stu-id="07699-118">Activity Forecast</span></span>|<span data-ttu-id="07699-119">pogody / {stanu} / {Miasto} / {działania}</span><span class="sxs-lookup"><span data-stu-id="07699-119">weather/{state}/{city}/{activity}</span></span>|  
  
 <span data-ttu-id="07699-120">Poniższa tabela zawiera opis zestawu strukturę podobną identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="07699-120">This table describes a set of structurally similar URIs.</span></span> <span data-ttu-id="07699-121">Każdy wpis jest szablon identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="07699-121">Each entry is a URI template.</span></span> <span data-ttu-id="07699-122">Segmenty w nawiasach klamrowych opisano zmienne.</span><span class="sxs-lookup"><span data-stu-id="07699-122">The segments in curly braces describe variables.</span></span> <span data-ttu-id="07699-123">Segmenty nie w nawiasach klamrowych opisano ciągi literału.</span><span class="sxs-lookup"><span data-stu-id="07699-123">The segments not in curly braces describe literal strings.</span></span> <span data-ttu-id="07699-124">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Szablonu klasy umożliwiają dewelopera zająć przychodzący identyfikator URI, na przykład "/ pogody/wa/seattle/cyklicznie", i porównuje ją do szablonu, który opisuje, "/weather/ {stanu} / {Miasto} / {działania}".</span><span class="sxs-lookup"><span data-stu-id="07699-124">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] template classes allow a developer to take an incoming URI, for example, "/weather/wa/seattle/cycling", and match it to a template that describes it, "/weather/{state}/{city}/{activity}".</span></span>  
  
## <a name="uritemplate"></a><span data-ttu-id="07699-125">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="07699-125">UriTemplate</span></span>  
 <span data-ttu-id="07699-126"><xref:System.UriTemplate>jest klasa, która hermetyzuje szablon identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="07699-126"><xref:System.UriTemplate> is a class that encapsulates a URI template.</span></span> <span data-ttu-id="07699-127">Konstruktor ma parametr typu string, który definiuje szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-127">The constructor takes a string parameter that defines the template.</span></span> <span data-ttu-id="07699-128">Ten ciąg zawiera szablon w formacie opisany w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="07699-128">This string contains the template in the format described in the next section.</span></span> <span data-ttu-id="07699-129"><xref:System.UriTemplate> Klasa udostępnia metody, które należy spełnić odpowiada przychodzący identyfikator URI do szablonu, wygenerować identyfikator URI na podstawie szablonu, pobierania kolekcję nazwy zmiennych używane w szablonie, określić, czy dwa szablony są równoważne i zwracać szablon ciąg.</span><span class="sxs-lookup"><span data-stu-id="07699-129">The <xref:System.UriTemplate> class provides methods that allow you match an incoming URI to a template, generate a URI from a template, retrieve a collection of variable names used in the template, determine whether two templates are equivalent, and return the template's string.</span></span>  
  
 <span data-ttu-id="07699-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29>pobiera adres podstawowy i kandydatem identyfikatora URI i próbuje dopasować identyfikatora URI do szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-130"><xref:System.UriTemplate.Match%28System.Uri%2CSystem.Uri%29> takes a base address and a candidate URI and attempts to match the URI to the template.</span></span> <span data-ttu-id="07699-131">Gdy dopasowanie jest pomyślne, <xref:System.UriTemplateMatch> zwrócone wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="07699-131">If the match is successful, a <xref:System.UriTemplateMatch> instance is returned.</span></span> <span data-ttu-id="07699-132"><xref:System.UriTemplateMatch> Podstawowy identyfikator URI candidate identyfikatora URI kolekcji nazw i wartości parametrów zapytania, Tablica segmentów ścieżki względnej, kolekcji nazw i wartości zmiennych, które zostały spełnione, zawiera obiekt <xref:System.UriTemplate> wystąpienie używane w celu wykonania dopasowania , ciąg, który zawiera niedopasowane części candidate identyfikatora URI (stosowane, gdy szablon ma symboli wieloznacznych), a obiekt, który jest skojarzony z szablonem.</span><span class="sxs-lookup"><span data-stu-id="07699-132">The <xref:System.UriTemplateMatch> object contains a base URI, the candidate URI, a name/value collection of the query parameters, an array of the relative path segments, a name/value collection of variables that were matched, the <xref:System.UriTemplate> instance used to perform the match, a string that contains any unmatched portion of the candidate URI (used when the template has a wildcard), and an object that is associated with the template.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07699-133"><xref:System.UriTemplate> Klasy ignoruje schemat i numer portu podczas dopasowywania identyfikatora URI kandydatem do szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-133">The <xref:System.UriTemplate> class ignores the scheme and port number when matching a candidate URI to a template.</span></span>  
  
 <span data-ttu-id="07699-134">Istnieją dwie metody, dzięki którym można wygenerować identyfikatora URI na podstawie szablonu, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> i <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span><span class="sxs-lookup"><span data-stu-id="07699-134">There are two methods that allow you to generate a URI from a template, <xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> and <xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>.</span></span> <span data-ttu-id="07699-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29>pobiera adres podstawowy i kolekcję nazw i wartości parametrów.</span><span class="sxs-lookup"><span data-stu-id="07699-135"><xref:System.UriTemplate.BindByName%28System.Uri%2CSystem.Collections.Specialized.NameValueCollection%29> takes a base address and a name/value collection of parameters.</span></span> <span data-ttu-id="07699-136">Te parametry są zastępowane dla zmiennych, gdy szablon jest powiązana.</span><span class="sxs-lookup"><span data-stu-id="07699-136">These parameters are substituted for variables when the template is bound.</span></span> <span data-ttu-id="07699-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29>pobiera pary nazwa/wartość i zastępuje je od lewej do prawej.</span><span class="sxs-lookup"><span data-stu-id="07699-137"><xref:System.UriTemplate.BindByPosition%28System.Uri%2CSystem.String%5B%5D%29> takes the name/value pairs and substitutes them left to right.</span></span>  
  
 <span data-ttu-id="07699-138"><xref:System.UriTemplate.ToString>Zwraca ciąg szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-138"><xref:System.UriTemplate.ToString> returns the template string.</span></span>  
  
 <span data-ttu-id="07699-139"><xref:System.UriTemplate.PathSegmentVariableNames%2A> Właściwość zawiera kolekcję nazw zmiennych w segmentach ścieżki w ciągu szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-139">The <xref:System.UriTemplate.PathSegmentVariableNames%2A> property contains a collection of the names of the variables used within path segments in the template string.</span></span>  
  
 <span data-ttu-id="07699-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29>Trwa <xref:System.UriTemplate> jako parametr i zwraca wartość logiczną, która określa, czy dwa szablony są równoważne.</span><span class="sxs-lookup"><span data-stu-id="07699-140"><xref:System.UriTemplate.IsEquivalentTo%28System.UriTemplate%29> takes a <xref:System.UriTemplate> as a parameter and returns a Boolean value that specifies whether the two templates are equivalent.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="07699-141">w sekcji równoważność szablonu w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="07699-141"> the Template Equivalence section later in this topic.</span></span>  
  
 <span data-ttu-id="07699-142"><xref:System.UriTemplate>jest przeznaczona do pracy z dowolnego schemat URI, który odpowiada gramatyki identyfikator URI protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="07699-142"><xref:System.UriTemplate> is designed to work with any URI scheme that conforms to the HTTP URI grammar.</span></span> <span data-ttu-id="07699-143">Poniżej przedstawiono przykłady obsługiwane schematy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="07699-143">The following are examples of supported URI schemes.</span></span>  
  
-   <span data-ttu-id="07699-144">http://</span><span class="sxs-lookup"><span data-stu-id="07699-144">http://</span></span>  
  
-   <span data-ttu-id="07699-145">https://</span><span class="sxs-lookup"><span data-stu-id="07699-145">https://</span></span>  
  
-   <span data-ttu-id="07699-146">NET.TCP://</span><span class="sxs-lookup"><span data-stu-id="07699-146">net.tcp://</span></span>  
  
-   <span data-ttu-id="07699-147">NET.pipe://</span><span class="sxs-lookup"><span data-stu-id="07699-147">net.pipe://</span></span>  
  
-   <span data-ttu-id="07699-148">SB: / /</span><span class="sxs-lookup"><span data-stu-id="07699-148">sb://</span></span>  
  
 <span data-ttu-id="07699-149">Systemy, takie jak file:// i urn: / / nie odpowiadać gramatyce identyfikator URI protokołu HTTP i spowodować nieprzewidywalne skutki, gdy jest używany z szablonów identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="07699-149">Schemes like file:// and urn:// do not conform to the HTTP URI grammar and cause unpredictable results when used with URI templates.</span></span>  
  
### <a name="template-string-syntax"></a><span data-ttu-id="07699-150">Składnia ciągu szablonu</span><span class="sxs-lookup"><span data-stu-id="07699-150">Template String Syntax</span></span>  
 <span data-ttu-id="07699-151">Szablon ma trzy części: ścieżki, opcjonalne zapytania i opcjonalne fragmentu.</span><span class="sxs-lookup"><span data-stu-id="07699-151">A template has three parts: a path, an optional query, and an optional fragment.</span></span> <span data-ttu-id="07699-152">Na przykład zobacz następujący szablon:</span><span class="sxs-lookup"><span data-stu-id="07699-152">For an example, see the following template:</span></span>  
  
```  
"/weather/{state}/{city}?forecast={length)#frag1  
```  
  
 <span data-ttu-id="07699-153">Ścieżka składa się z "/weather/ {stanu} / {Miasto}", zapytanie składa się z"? prognozy = {długość}, a fragment składa się z"#frag1".</span><span class="sxs-lookup"><span data-stu-id="07699-153">The path consists of "/weather/{state}/{city}", the query consists of "?forecast={length}, and the fragment consists of "#frag1".</span></span>  
  
 <span data-ttu-id="07699-154">Początkowe i końcowe ukośniki są opcjonalne w wyrażeniu ścieżki.</span><span class="sxs-lookup"><span data-stu-id="07699-154">Leading and trailing slashes are optional in the path expression.</span></span> <span data-ttu-id="07699-155">Wyrażenia zapytania i fragment można całkowicie pominąć.</span><span class="sxs-lookup"><span data-stu-id="07699-155">Both the query and fragment expressions can be omitted entirely.</span></span> <span data-ttu-id="07699-156">Ścieżka składa się z szeregu segmentów rozdzielonych przez '/', każdy z segmentów może mieć wartość literału, nazwa zmiennej (zapisany w {nawiasy klamrowe}) lub symbolem wieloznacznym (zapisane jako\*").</span><span class="sxs-lookup"><span data-stu-id="07699-156">A path consists of a series of segments delimited by '/', each segment can have a literal value, a variable name (written in {curly braces}), or a wildcard (written as '\*').</span></span> <span data-ttu-id="07699-157">W szablonie poprzedniej "\weather\ segmentu jest literałem wartość podczas"stan {}"i"{Miasto}"są zmienne.</span><span class="sxs-lookup"><span data-stu-id="07699-157">In the previous template the "\weather\ segment is a literal value while "{state}" and "{city}" are variables.</span></span> <span data-ttu-id="07699-158">Zmienne podjąć odpowiednią nazwę z zawartości ich nawiasy klamrowe, a później mogą być zastępowane z konkretną wartość, aby utworzyć *zamknięte URI*.</span><span class="sxs-lookup"><span data-stu-id="07699-158">Variables take their name from the contents of their curly braces and they can later be replaced with a concrete value to create a *closed URI*.</span></span> <span data-ttu-id="07699-159">Symbol wieloznaczny jest opcjonalne, ale może wystąpić tylko na końcu identyfikator URI, których logicznie pasuje "pozostałej części ścieżki".</span><span class="sxs-lookup"><span data-stu-id="07699-159">The wildcard is optional, but can only appear at the end of the URI, where it logically matches "the rest of the path".</span></span>  
  
 <span data-ttu-id="07699-160">Wyrażenia zapytania, jeśli jest dostępna Określa ciąg par nazwa/wartość nieuporządkowaną rozdzielone 'i'.</span><span class="sxs-lookup"><span data-stu-id="07699-160">The query expression, if present, specifies a series of unordered name/value pairs delimited by '&'.</span></span> <span data-ttu-id="07699-161">Elementy wyrażenia zapytania mogą być pary literału (x = 2) dysków lub para zmiennej (x = {var}).</span><span class="sxs-lookup"><span data-stu-id="07699-161">Elements of the query expression can either be literal pairs (x=2) or a variable pair (x={var}).</span></span> <span data-ttu-id="07699-162">Tylko po prawej stronie zapytania może mieć zmiennej wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="07699-162">Only the right side of the query can have a variable expression.</span></span> <span data-ttu-id="07699-163">({JakaśNazwa} = {someValue} nie jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="07699-163">({someName} = {someValue} is not allowed.</span></span> <span data-ttu-id="07699-164">Nieparzysty wartości (? x) nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="07699-164">Unpaired values (?x) are not permitted.</span></span> <span data-ttu-id="07699-165">Nie ma żadnej różnicy między wyrażeniem zapytania pusta w wyrażeniu kwerendy składające się z tylko jedną "?" (zarówno oznacza "wszelkie zapytania").</span><span class="sxs-lookup"><span data-stu-id="07699-165">There is no difference between an empty query expression and a query expression consisting of just a single '?' (both mean "any query").</span></span>  
  
 <span data-ttu-id="07699-166">Wyrażenie fragmentacji może składać się z wartością literałową, zmienne nie są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="07699-166">The fragment expression can consist of a literal value, no variables are allowed.</span></span>  
  
 <span data-ttu-id="07699-167">Wszystkie nazwy zmiennych szablonu w ciągu szablonu musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="07699-167">All template variable names within a template string must be unique.</span></span> <span data-ttu-id="07699-168">Nazwy zmiennych szablonu jest rozróżniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="07699-168">Template variable names are case-insensitive.</span></span>  
  
 <span data-ttu-id="07699-169">Przykłady ciągów prawidłowego szablonu:</span><span class="sxs-lookup"><span data-stu-id="07699-169">Examples of valid template strings:</span></span>  
  
-   <span data-ttu-id="07699-170">""</span><span class="sxs-lookup"><span data-stu-id="07699-170">""</span></span>  
  
-   <span data-ttu-id="07699-171">"/ uniesienia"</span><span class="sxs-lookup"><span data-stu-id="07699-171">"/shoe"</span></span>  
  
-   <span data-ttu-id="07699-172">"/ buta / *"</span><span class="sxs-lookup"><span data-stu-id="07699-172">"/shoe/*"</span></span>  
  
-   <span data-ttu-id="07699-173">"{buta} / łodzi"</span><span class="sxs-lookup"><span data-stu-id="07699-173">"{shoe}/boat"</span></span>  
  
-   <span data-ttu-id="07699-174">"{buta} / {łodzi} /bed/ {patchworkowa}"</span><span class="sxs-lookup"><span data-stu-id="07699-174">"{shoe}/{boat}/bed/{quilt}"</span></span>  
  
-   <span data-ttu-id="07699-175">"uniesienia / {łodzi}"</span><span class="sxs-lookup"><span data-stu-id="07699-175">"shoe/{boat}"</span></span>  
  
-   <span data-ttu-id="07699-176">"uniesienia / {łodzi} / *"</span><span class="sxs-lookup"><span data-stu-id="07699-176">"shoe/{boat}/*"</span></span>  
  
-   <span data-ttu-id="07699-177">"buta/łodzi? x = 2"</span><span class="sxs-lookup"><span data-stu-id="07699-177">"shoe/boat?x=2"</span></span>  
  
-   <span data-ttu-id="07699-178">"uniesienia / {łodzi}? x = {bielizny}"</span><span class="sxs-lookup"><span data-stu-id="07699-178">"shoe/{boat}?x={bed}"</span></span>  
  
-   <span data-ttu-id="07699-179">"uniesienia / {łodzi}? x = {bielizny} & y = poza pasmem"</span><span class="sxs-lookup"><span data-stu-id="07699-179">"shoe/{boat}?x={bed}&y=band"</span></span>  
  
-   <span data-ttu-id="07699-180">"? x = {buta}"</span><span class="sxs-lookup"><span data-stu-id="07699-180">"?x={shoe}"</span></span>  
  
-   <span data-ttu-id="07699-181">"buta? x = 3 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-181">"shoe?x=3&y={var}</span></span>  
  
 <span data-ttu-id="07699-182">Przykłady parametrów szablonu jest nieprawidłowa:</span><span class="sxs-lookup"><span data-stu-id="07699-182">Examples of invalid template strings:</span></span>  
  
-   <span data-ttu-id="07699-183">"{buta} / {UNIESIENIA} / x = 2" — zduplikowane nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="07699-183">"{shoe}/{SHOE}/x=2" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="07699-184">"{buta} /boat/? bielizny = {buta}" — zduplikowane nazwy zmiennej.</span><span class="sxs-lookup"><span data-stu-id="07699-184">"{shoe}/boat/?bed={shoe}" – Duplicate variable names.</span></span>  
  
-   <span data-ttu-id="07699-185">"? x = 2 & x = 3" — pary nazwa/wartość ciągu zapytania musi być unikatowa, nawet jeśli są one literały.</span><span class="sxs-lookup"><span data-stu-id="07699-185">"?x=2&x=3" – Name/value pairs within a query string must be unique, even if they are literals.</span></span>  
  
-   <span data-ttu-id="07699-186">"? x = 2 &" — ciąg zapytania jest nieprawidłowo sformułowany.</span><span class="sxs-lookup"><span data-stu-id="07699-186">"?x=2&" – Query string is malformed.</span></span>  
  
-   <span data-ttu-id="07699-187">"? 2 & x = {buta}" — ciąg zapytania musi mieć pary nazwa/wartość.</span><span class="sxs-lookup"><span data-stu-id="07699-187">"?2&x={shoe}" – Query string must be name/value pairs.</span></span>  
  
-   <span data-ttu-id="07699-188">"? y = 2 & & X = 3" — ciąg zapytania musi być par wartości nazw, nazwa nie może rozpoczynać się 'i'.</span><span class="sxs-lookup"><span data-stu-id="07699-188">"?y=2&&X=3" – Query string must be name value pairs, names cannot start with '&'.</span></span>  
  
### <a name="compound-path-segments"></a><span data-ttu-id="07699-189">Segmenty ścieżki złożone</span><span class="sxs-lookup"><span data-stu-id="07699-189">Compound Path Segments</span></span>  
 <span data-ttu-id="07699-190">Segmenty ścieżki złożonej Zezwalaj pojedynczy segment ścieżki identyfikatora URI zawiera wiele zmiennych, a także zmienne w połączeniu z literały.</span><span class="sxs-lookup"><span data-stu-id="07699-190">Compound path segments allow a single URI path segment to contain multiple variables as well as variables combined with literals.</span></span> <span data-ttu-id="07699-191">Poniżej przedstawiono przykłady segmentów prawidłową ścieżkę złożonego.</span><span class="sxs-lookup"><span data-stu-id="07699-191">The following are examples of valid compound path segments.</span></span>  
  
-   <span data-ttu-id="07699-192">argumentu/FILENAME. {ext} /</span><span class="sxs-lookup"><span data-stu-id="07699-192">/filename.{ext}/</span></span>  
  
-   <span data-ttu-id="07699-193">/{filename}.jpg/</span><span class="sxs-lookup"><span data-stu-id="07699-193">/{filename}.jpg/</span></span>  
  
-   <span data-ttu-id="07699-194">/ {filename}. {ext} /</span><span class="sxs-lookup"><span data-stu-id="07699-194">/{filename}.{ext}/</span></span>  
  
-   <span data-ttu-id="07699-195">/ {}. {b}someLiteral{c}({d}) /</span><span class="sxs-lookup"><span data-stu-id="07699-195">/{a}.{b}someLiteral{c}({d})/</span></span>  
  
 <span data-ttu-id="07699-196">Poniżej przedstawiono przykłady segmentów nieprawidłową ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="07699-196">The following are examples of invalid path segments.</span></span>  
  
-   <span data-ttu-id="07699-197">/{} — Zmienne musi mieć nazwę.</span><span class="sxs-lookup"><span data-stu-id="07699-197">/{} - Variables must be named.</span></span>  
  
-   <span data-ttu-id="07699-198">/ {łodzi} - {uniesienia} zmiennych muszą być oddzielone literału.</span><span class="sxs-lookup"><span data-stu-id="07699-198">/{shoe}{boat} - Variables must be separated by a literal.</span></span>  
  
### <a name="matching-and-compound-path-segments"></a><span data-ttu-id="07699-199">Segmenty ścieżki dopasowywania i złożone</span><span class="sxs-lookup"><span data-stu-id="07699-199">Matching and Compound Path Segments</span></span>  
 <span data-ttu-id="07699-200">Segmenty ścieżki złożonej zezwala na określanie obiektu UriTemplate, która ma wiele zmiennych w segmencie pojedynczą ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="07699-200">Compound path segments allow you to define a UriTemplate that has multiple variables within a single path segment.</span></span> <span data-ttu-id="07699-201">Na przykład w poniższym ciągu szablonu: "adresy / {stanu}. {Miasto} "dwie zmienne (stanu i miasta) są zdefiniowane w ten sam segment.</span><span class="sxs-lookup"><span data-stu-id="07699-201">For example, in the following template string: "Addresses/{state}.{city}" two variables (state and city) are defined within the same segment.</span></span> <span data-ttu-id="07699-202">Ten szablon będzie zgodne adresu URL, takie jak "http://example.com/Washington.Redmond", ale również będzie odpowiadała adresu URL, takie jak "http://example.com/Washington.Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="07699-202">This template would match a URL such as "http://example.com/Washington.Redmond" but it will also match an URL like "http://example.com/Washington.Redmond.Microsoft".</span></span> <span data-ttu-id="07699-203">W drugim przypadku zmiennej stanu będzie zawierać "W stanie Waszyngton" i zmiennej Miasto będzie zawierać "Redmond.Microsoft".</span><span class="sxs-lookup"><span data-stu-id="07699-203">In the latter case, the state variable will contain "Washington" and the city variable will contain "Redmond.Microsoft".</span></span> <span data-ttu-id="07699-204">W takim przypadku tekstem (z wyjątkiem "/") będzie odpowiadała zmiennej {miasto}.</span><span class="sxs-lookup"><span data-stu-id="07699-204">In this case any text (except ‘/’) will match the {city} variable.</span></span> <span data-ttu-id="07699-205">Szablon, który nie będzie odpowiadała "dodatkowy" tekst, umieść zmiennej w segmencie oddzielnego szablonu, na przykład: "adresy / {stanu} / {miasto}.</span><span class="sxs-lookup"><span data-stu-id="07699-205">If you want a template that will not match the "extra" text, place the variable in a separate template segment, for example: "Addresses/{state}/{city}.</span></span>  
  
### <a name="named-wildcard-segments"></a><span data-ttu-id="07699-206">Segmenty nazwanego symboli wieloznacznych</span><span class="sxs-lookup"><span data-stu-id="07699-206">Named Wildcard Segments</span></span>  
 <span data-ttu-id="07699-207">Segment o nazwie symboli wieloznacznych jest żadnych segment zmiennej ścieżki których nazwa zmiennej rozpoczyna się od znaku wieloznacznego "*".</span><span class="sxs-lookup"><span data-stu-id="07699-207">A named wildcard segment is any path variable segment whose variable name begins with the wildcard character ‘*’.</span></span> <span data-ttu-id="07699-208">Następujący ciąg szablonu zawiera segment wieloznaczny nazwane o nazwie "buta".</span><span class="sxs-lookup"><span data-stu-id="07699-208">The following template string contains a named wildcard segment named "shoe".</span></span>  
  
```  
"literal/{*shoe}"  
```  
  
 <span data-ttu-id="07699-209">Segmenty symboli wieloznacznych, należy wykonać następujące reguły:</span><span class="sxs-lookup"><span data-stu-id="07699-209">Wildcard segments must follow the following rules:</span></span>  
  
-   <span data-ttu-id="07699-210">Może istnieć co najwyżej jeden segment o nazwie symboli wieloznacznych dla każdego ciąg szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-210">There can be at most one named wildcard segment for each template string.</span></span>  
  
-   <span data-ttu-id="07699-211">Segment o nazwie symbolu wieloznacznego musi znajdować się na prawej segment w ścieżce.</span><span class="sxs-lookup"><span data-stu-id="07699-211">A named wildcard segment must appear at the right-most segment in the path.</span></span>  
  
-   <span data-ttu-id="07699-212">Segment o nazwie wieloznaczny nie może współistnieć z segment wieloznaczny anonimowe ciągu szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-212">A named wildcard segment cannot coexist with an anonymous wildcard segment within the same template string.</span></span>  
  
-   <span data-ttu-id="07699-213">Nazwa segment wieloznaczny nazwanego musi być unikatowa.</span><span class="sxs-lookup"><span data-stu-id="07699-213">The name of a named wildcard segment must be unique.</span></span>  
  
-   <span data-ttu-id="07699-214">O nazwie symbolu wieloznacznego segmentów nie może mieć wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="07699-214">Named wildcard segments cannot have default values.</span></span>  
  
-   <span data-ttu-id="07699-215">Segmenty nazwanego symbolu wieloznacznego nie może kończyć się "/".</span><span class="sxs-lookup"><span data-stu-id="07699-215">Named wildcard segments cannot end with "/".</span></span>  
  
### <a name="default-variable-values"></a><span data-ttu-id="07699-216">Domyślne wartości zmiennej</span><span class="sxs-lookup"><span data-stu-id="07699-216">Default Variable Values</span></span>  
 <span data-ttu-id="07699-217">Domyślne wartości zmiennej umożliwiają określanie wartości domyślnych do zmiennych w ramach szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-217">Default variable values allow you to specify default values for variables within a template.</span></span> <span data-ttu-id="07699-218">Można określić domyślne zmienne w nawiasach klamrowych, które zadeklarować zmienną lub jako kolekcja przekazany do konstruktora obiektu UriTemplate.</span><span class="sxs-lookup"><span data-stu-id="07699-218">Default variables can be specified with the curly braces that declare the variable or as a collection passed to the UriTemplate constructor.</span></span> <span data-ttu-id="07699-219">Następujący szablon przedstawia dwa sposoby określ <xref:System.UriTemplate> ze zmiennymi wartościami domyślnymi.</span><span class="sxs-lookup"><span data-stu-id="07699-219">The following template shows two ways to specify a <xref:System.UriTemplate> with variables with default values.</span></span>  
  
```  
UriTemplate t = new UriTemplate("/test/{a=1}/{b=5}");  
```  
  
 <span data-ttu-id="07699-220">Ten szablon deklaruje zmienną o nazwie `a` z wartością domyślną `1` i zmiennej o nazwie `b` z wartością domyślną `5`.</span><span class="sxs-lookup"><span data-stu-id="07699-220">This template declares a variable named `a` with a default value of `1` and a variable named `b` with a default value of `5`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07699-221">Tylko zmienne segmentu ścieżki mogą mają przypisane wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="07699-221">Only path segment variables are allowed to have default values.</span></span> <span data-ttu-id="07699-222">Zmiennych ciągu zapytania, zmienne złożonego segmentu i zmienne nazwanego symbolu wieloznacznego nie mogą mieć wartości domyślne.</span><span class="sxs-lookup"><span data-stu-id="07699-222">Query string variables, compound segment variables, and named wildcard variables are not permitted to have default values.</span></span>  
  
 <span data-ttu-id="07699-223">Poniższy kod przedstawia sposób obsługi domyślnych wartości zmiennych podczas dopasowywania identyfikatora URI kandydatem.</span><span class="sxs-lookup"><span data-stu-id="07699-223">The following code shows how default variable values are handled when matching a candidate URI.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:800   
Dictionary<string,string> defVals = new Dictionary<string,string> {{"a","1"}, {"b", "5"}};  
UriTemplate t = new UriTemplate("/test/{a}/{b}", defVals);0");  
UriTemplate t = new UriTemplate("/{state=WA}/{city=Redmond}/", true);  
Uri candidate = new Uri("http://localhost:8000/OR");  
  
UriTemplateMatch m1 = t.Match(baseAddress, candidate);  
  
// Display contents of BoundVariables  
foreach (string key in m1.BoundVariables.AllKeys)  
{  
    Console.WriteLine("\t\t{0}={1}", key, m1.BoundVariables[key]);  
}  
// The output of the above code is  
// Template: /{state=WA}/{city=Redmond}/  
// Candidate URI: http://localhost:8000/OR  
// BoundVariables:  
//      STATE=OR  
//       CITY=Redmond  
```  
  
> [!NOTE]
>  <span data-ttu-id="07699-224">Identyfikator URI, np. http://localhost: 8000 / / / jest niezgodna z szablonu wymienionych w powyższym kodzie, jednak identyfikatora URI, np. http://localhost: 8000 / jest.</span><span class="sxs-lookup"><span data-stu-id="07699-224">A URI such as http://localhost:8000/// does not match the template listed in the preceding code, however a URI such as http://localhost:8000/ does.</span></span>  
  
 <span data-ttu-id="07699-225">Poniższy kod przedstawia sposób obsługi domyślnych wartości zmiennych podczas tworzenia identyfikator URI przy użyciu szablonu.</span><span class="sxs-lookup"><span data-stu-id="07699-225">The following code shows how default variable values are handled when creating a URI with a template.</span></span>  
  
```  
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
  
 <span data-ttu-id="07699-226">Gdy zmienna znajduje się wartość domyślną równą `null` istnieją pewne dodatkowe ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="07699-226">When a variable is given a default value of `null` there are some additional constraints.</span></span> <span data-ttu-id="07699-227">Zmienna może mieć wartości domyślnej równej `null` Jeśli zmienna jest zawarty w prawo większości segment ciąg szablonu lub wszystkie segmenty z prawej strony segmentu ma domyślne wartości `null`.</span><span class="sxs-lookup"><span data-stu-id="07699-227">A variable can have a default value of `null` if the variable is contained within the right most segment of the template string or if all segments to the right of the segment have default values of `null`.</span></span> <span data-ttu-id="07699-228">Poniżej podano prawidłowy szablon parametry z wartościami domyślnymi `null`:</span><span class="sxs-lookup"><span data-stu-id="07699-228">The following are valid template strings with default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("shoe/{boat=null}");  
    ```  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=null}");  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=1}/{boat=null}");  
    ```  
 <span data-ttu-id="07699-229">Poniżej podano nieprawidłowy szablon parametry z wartościami domyślnymi `null`:</span><span class="sxs-lookup"><span data-stu-id="07699-229">The following are invalid template strings with  default values of `null`:</span></span>  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/boat"); // null default must be in the right most path segment  
    ```  
  
-   ```  
    UriTemplate t = new UriTemplate("{shoe=null}/{boat=x}/{bed=null}"); // shoe cannot have a null default because boat does not have a default null value  
    ```  
### <a name="default-values-and-matching"></a><span data-ttu-id="07699-230">Wartości domyślne i dopasowywanie</span><span class="sxs-lookup"><span data-stu-id="07699-230">Default Values and Matching</span></span>  
 <span data-ttu-id="07699-231">Podczas dopasowywania candidate identyfikator URI przy użyciu szablonu, który zawiera wartości domyślne, wartości domyślne są umieszczane w <xref:System.UriTemplateMatch.BoundVariables%2A> kolekcji, jeśli nie określono wartości w candidate identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="07699-231">When matching a candidate URI with a template that has default values, the default values are placed in the <xref:System.UriTemplateMatch.BoundVariables%2A> collection if values are not specified in the candidate URI.</span></span>  
  
### <a name="template-equivalence"></a><span data-ttu-id="07699-232">Równoważność szablonu</span><span class="sxs-lookup"><span data-stu-id="07699-232">Template Equivalence</span></span>  
 <span data-ttu-id="07699-233">Dwa szablony są określane jako *strukturę równoważne* gdy wszystkie te szablony literałów odpowiadać i mają zmiennych w segmentach tego samego.</span><span class="sxs-lookup"><span data-stu-id="07699-233">Two templates are said to be *structurally equivalent* when all of the templates' literals match and they have variables in the same segments.</span></span> <span data-ttu-id="07699-234">Na przykład następujące szablony są strukturalnie równoważne:</span><span class="sxs-lookup"><span data-stu-id="07699-234">For example the following templates are structurally equivalent:</span></span>  
  
-   <span data-ttu-id="07699-235">b /b /a/ {var1} / {var2}? x = 1 & y = 2</span><span class="sxs-lookup"><span data-stu-id="07699-235">/a/{var1}/b b/{var2}?x=1&y=2</span></span>  
  
-   <span data-ttu-id="07699-236">a/{x}/b%20b/{var1}?y=2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-236">a/{x}/b%20b/{var1}?y=2&x=1</span></span>  
  
-   <span data-ttu-id="07699-237">a/{y}/B%20b/{z}/?y=2 & x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-237">a/{y}/B%20B/{z}/?y=2&x=1</span></span>  
  
 <span data-ttu-id="07699-238">Zwróć uwagę kilka istotnych:</span><span class="sxs-lookup"><span data-stu-id="07699-238">A few things to notice:</span></span>  
  
-   <span data-ttu-id="07699-239">Jeśli szablon zawiera początkowe ukośniki, tylko pierwszy z nich jest ignorowana.</span><span class="sxs-lookup"><span data-stu-id="07699-239">If a template contains leading slashes, only the first one is ignored.</span></span>  
  
-   <span data-ttu-id="07699-240">Podczas porównywania ciągów szablonów do pełnienia roli równoważnika strukturalnych, wielkość liter jest ignorowana w nazwach zmiennych i segmentów ścieżki, ciągów zapytania jest uwzględniana wielkość liter.</span><span class="sxs-lookup"><span data-stu-id="07699-240">When comparing template strings for structural equivalence, case is ignored for variable names and path segments, query strings are case sensitive.</span></span>  
  
-   <span data-ttu-id="07699-241">Ciągi zapytań są nieuporządkowane.</span><span class="sxs-lookup"><span data-stu-id="07699-241">Query strings are unordered.</span></span>  
  
## <a name="uritemplatetable"></a><span data-ttu-id="07699-242">Obiekt UriTemplateTable</span><span class="sxs-lookup"><span data-stu-id="07699-242">UriTemplateTable</span></span>  
 <span data-ttu-id="07699-243"><xref:System.UriTemplateTable> Klasa reprezentuje asocjacyjnej spis <xref:System.UriTemplate> obiekty powiązane z obiektu dewelopera na wybór.</span><span class="sxs-lookup"><span data-stu-id="07699-243">The <xref:System.UriTemplateTable> class represents an associative table of <xref:System.UriTemplate> objects bound to an object of the developer's choosing.</span></span> <span data-ttu-id="07699-244">A <xref:System.UriTemplateTable> musi zawierać co najmniej jeden <xref:System.UriTemplate> przed wywołaniem <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="07699-244">A <xref:System.UriTemplateTable> must contain at least one <xref:System.UriTemplate> prior to calling <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span> <span data-ttu-id="07699-245">Zawartość <xref:System.UriTemplateTable> można go zmienić, dopóki <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="07699-245">The contents of a <xref:System.UriTemplateTable> can be changed until <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="07699-246">Sprawdzanie poprawności jest wykonywane podczas <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="07699-246">Validation is performed when <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called.</span></span> <span data-ttu-id="07699-247">Typ weryfikacji wykonać zależy od wartości `allowMultiple` parametr <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span><span class="sxs-lookup"><span data-stu-id="07699-247">The type of validation performed depends upon the value of the `allowMultiple` parameter to <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29>.</span></span>  
  
 <span data-ttu-id="07699-248">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `false`, <xref:System.UriTemplateTable> kontroli, aby upewnić się, że nie ma szablonów w tabeli.</span><span class="sxs-lookup"><span data-stu-id="07699-248">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `false`, the <xref:System.UriTemplateTable> checks to make sure there are no templates in the table.</span></span> <span data-ttu-id="07699-249">Jeśli znajdzie żadnych szablonów strukturalnie równoważne zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="07699-249">If it finds any structurally equivalent templates, it throws an exception.</span></span> <span data-ttu-id="07699-250">Jest on używany w połączeniu z <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> gdy chcesz zapewnić tylko jeden szablon URI przychodzącego jest zgodna.</span><span class="sxs-lookup"><span data-stu-id="07699-250">This is used in conjunction with <xref:System.UriTemplateTable.MatchSingle%28System.Uri%29> when you want to ensure only one template matches an incoming URI.</span></span>  
  
 <span data-ttu-id="07699-251">Gdy <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> jest wywoływana, przekazując `true`, <xref:System.UriTemplateTable> umożliwia wielu strukturalnie równoważne szablony mają być zawarte w <xref:System.UriTemplateTable>.</span><span class="sxs-lookup"><span data-stu-id="07699-251">When <xref:System.UriTemplateTable.MakeReadOnly%28System.Boolean%29> is called passing in `true`, <xref:System.UriTemplateTable> allows multiple, structurally-equivalent templates to be contained within a <xref:System.UriTemplateTable>.</span></span>  
  
 <span data-ttu-id="07699-252">Jeśli zestaw <xref:System.UriTemplate> obiekty dodane do <xref:System.UriTemplateTable> zawiera ciągi zapytań nie może być niejednoznaczna.</span><span class="sxs-lookup"><span data-stu-id="07699-252">If a set of <xref:System.UriTemplate> objects added to a <xref:System.UriTemplateTable> contain query strings they must not be ambiguous.</span></span> <span data-ttu-id="07699-253">Ciągi zapytań identyczne są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="07699-253">Identical query strings are allowed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07699-254">Gdy <xref:System.UriTemplateTable> umożliwia base adresów tego użycia systemów innych niż HTTP, schemat i numer portu są ignorowane podczas dopasowywania candidate identyfikatorów URI do szablonów.</span><span class="sxs-lookup"><span data-stu-id="07699-254">While the <xref:System.UriTemplateTable> allows base addresses that use schemes other than HTTP, the scheme and port number are ignored when matching candidate URIs to templates.</span></span>  
  
### <a name="query-string-ambiguity"></a><span data-ttu-id="07699-255">Niejednoznaczności ciąg zapytania</span><span class="sxs-lookup"><span data-stu-id="07699-255">Query String Ambiguity</span></span>  
 <span data-ttu-id="07699-256">Szablonów mających równoważną ścieżkę zawiera ciągi zapytań niejednoznaczny, jeśli identyfikator URI, który odpowiada więcej niż jeden szablon.</span><span class="sxs-lookup"><span data-stu-id="07699-256">Templates that share an equivalent path contain ambiguous query strings if there is a URI that matches more than one template.</span></span>  
  
 <span data-ttu-id="07699-257">Następujące zestawy ciągi zapytań są jednoznaczne między sobą:</span><span class="sxs-lookup"><span data-stu-id="07699-257">The following sets of query strings are unambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="07699-258">? x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-258">?x=1</span></span>  
  
-   <span data-ttu-id="07699-259">? x = 2</span><span class="sxs-lookup"><span data-stu-id="07699-259">?x=2</span></span>  
  
-   <span data-ttu-id="07699-260">? x = 3</span><span class="sxs-lookup"><span data-stu-id="07699-260">?x=3</span></span>  
  
-   <span data-ttu-id="07699-261">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-261">?x=1&y={var}</span></span>  
  
-   <span data-ttu-id="07699-262">? x = 2 & z = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-262">?x=2&z={var}</span></span>  
  
-   <span data-ttu-id="07699-263">? x = 3</span><span class="sxs-lookup"><span data-stu-id="07699-263">?x=3</span></span>  
  
-   <span data-ttu-id="07699-264">? x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-264">?x=1</span></span>  
  
-   <span data-ttu-id="07699-265">?</span><span class="sxs-lookup"><span data-stu-id="07699-265">?</span></span>  
  
-   <span data-ttu-id="07699-266">?</span><span class="sxs-lookup"><span data-stu-id="07699-266">?</span></span> <span data-ttu-id="07699-267">x = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-267">x={var}</span></span>  
  
-   <span data-ttu-id="07699-268">?</span><span class="sxs-lookup"><span data-stu-id="07699-268">?</span></span>  
  
-   <span data-ttu-id="07699-269">? m = get & c = rss</span><span class="sxs-lookup"><span data-stu-id="07699-269">?m=get&c=rss</span></span>  
  
-   <span data-ttu-id="07699-270">? m = put & c = rss</span><span class="sxs-lookup"><span data-stu-id="07699-270">?m=put&c=rss</span></span>  
  
-   <span data-ttu-id="07699-271">? m = get & c = atom</span><span class="sxs-lookup"><span data-stu-id="07699-271">?m=get&c=atom</span></span>  
  
-   <span data-ttu-id="07699-272">? m = put & c = atom</span><span class="sxs-lookup"><span data-stu-id="07699-272">?m=put&c=atom</span></span>  
  
 <span data-ttu-id="07699-273">Następujące zestawy szablonów ciąg zapytania są niejednoznaczne między sobą:</span><span class="sxs-lookup"><span data-stu-id="07699-273">The following sets of query string templates are ambiguous within themselves:</span></span>  
  
-   <span data-ttu-id="07699-274">? x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-274">?x=1</span></span>  
  
-   <span data-ttu-id="07699-275">? x = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-275">?x={var}</span></span>  
  
 <span data-ttu-id="07699-276">"x = 1" — jest zgodny zarówno szablonów.</span><span class="sxs-lookup"><span data-stu-id="07699-276">"x=1" - Matches both templates.</span></span>  
  
-   <span data-ttu-id="07699-277">? x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-277">?x=1</span></span>  
  
-   <span data-ttu-id="07699-278">? y = 2</span><span class="sxs-lookup"><span data-stu-id="07699-278">?y=2</span></span>  
  
 <span data-ttu-id="07699-279">"x = 1 & y = 2" jest zgodny zarówno szablonów.</span><span class="sxs-lookup"><span data-stu-id="07699-279">"x=1&y=2" matches both templates.</span></span> <span data-ttu-id="07699-280">Jest to spowodowane ciąg zapytania mogą zawierać więcej zmiennych ciągu zapytania, a następnie szablon zgodny.</span><span class="sxs-lookup"><span data-stu-id="07699-280">This is because a query string may contain more query string variables then the template it matches.</span></span>  
  
-   <span data-ttu-id="07699-281">? x = 1</span><span class="sxs-lookup"><span data-stu-id="07699-281">?x=1</span></span>  
  
-   <span data-ttu-id="07699-282">? x = 1 & y = {var}</span><span class="sxs-lookup"><span data-stu-id="07699-282">?x=1&y={var}</span></span>  
  
 <span data-ttu-id="07699-283">"x = 1 & y = 3" jest zgodny zarówno szablonów.</span><span class="sxs-lookup"><span data-stu-id="07699-283">"x=1&y=3" matches both templates.</span></span>  
  
-   <span data-ttu-id="07699-284">? x = 3 & y = 4</span><span class="sxs-lookup"><span data-stu-id="07699-284">?x=3&y=4</span></span>  
  
-   <span data-ttu-id="07699-285">? x = 3 & z = 5</span><span class="sxs-lookup"><span data-stu-id="07699-285">?x=3&z=5</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07699-286">Α znaków i Α są traktowane jako różne znaki gdy są one wyświetlane jako część ścieżka identyfikatora URI lub <xref:System.UriTemplate> literał segmentu ścieżki (ale a znaków i A są traktowane jako taki sam).</span><span class="sxs-lookup"><span data-stu-id="07699-286">The characters á and Á are considered to be different characters when they appear as part of a URI path or <xref:System.UriTemplate> path segment literal (but the characters a and A are considered to be the same).</span></span> <span data-ttu-id="07699-287">Α znaków i Α są traktowane jako znaków gdy są one wyświetlane jako część a <xref:System.UriTemplate> {variableName} lub ciąg kwerendy (i a i A są także traktowane jako znaków).</span><span class="sxs-lookup"><span data-stu-id="07699-287">The characters á and Á are considered to be the same characters when they appear as part of a <xref:System.UriTemplate> {variableName} or a query string (and a and A are also considered to be the same characters).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07699-288">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07699-288">See Also</span></span>  
 [<span data-ttu-id="07699-289">Omówienie modelu programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="07699-289">WCF Web HTTP Programming Model Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model-overview.md)  
 [<span data-ttu-id="07699-290">Model obiektowy programowania protokołu HTTP sieci Web WCF</span><span class="sxs-lookup"><span data-stu-id="07699-290">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)  
 [<span data-ttu-id="07699-291">Obiekt UriTemplate</span><span class="sxs-lookup"><span data-stu-id="07699-291">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)  
 [<span data-ttu-id="07699-292">Tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="07699-292">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)  
 [<span data-ttu-id="07699-293">Dyspozytor tabeli UriTemplate</span><span class="sxs-lookup"><span data-stu-id="07699-293">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
