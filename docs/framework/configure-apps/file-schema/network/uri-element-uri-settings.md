---
title: <Uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 80d71da5ca680872e4948fa8ff135fbbdf08cffe
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663965"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="5c0f3-102">\<Identyfikator URI > element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="5c0f3-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="5c0f3-103">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="5c0f3-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="5c0f3-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="5c0f3-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="5c0f3-105">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="5c0f3-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="5c0f3-106">\<> identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="5c0f3-106">\<uri></span></span>](uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="5c0f3-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c0f3-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c0f3-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="5c0f3-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5c0f3-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c0f3-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="5c0f3-110">Attributes</span></span>  
 <span data-ttu-id="5c0f3-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c0f3-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="5c0f3-112">Child Elements</span></span>  
  
|<span data-ttu-id="5c0f3-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="5c0f3-113">**Element**</span></span>|<span data-ttu-id="5c0f3-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5c0f3-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5c0f3-115">IDN</span><span class="sxs-lookup"><span data-stu-id="5c0f3-115">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="5c0f3-116">Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="5c0f3-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="5c0f3-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="5c0f3-117">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="5c0f3-118">Określa <xref:System.Uri> , czy ma zostać zastosowana Analiza IRI (International Resource Identifier) i czy mają być stosowane IRI reguły analizy.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="5c0f3-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="5c0f3-119">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="5c0f3-120">Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5c0f3-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="5c0f3-121">Parent Elements</span></span>  
  
|<span data-ttu-id="5c0f3-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="5c0f3-122">**Element**</span></span>|<span data-ttu-id="5c0f3-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="5c0f3-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5c0f3-124">skonfigurować</span><span class="sxs-lookup"><span data-stu-id="5c0f3-124">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="5c0f3-125">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c0f3-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c0f3-126">Remarks</span></span>  
 <span data-ttu-id="5c0f3-127">Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy <xref:System.Net> używanej przez klasy w przestrzeni nazw. `uri`</span><span class="sxs-lookup"><span data-stu-id="5c0f3-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="5c0f3-128">Ustawienia umożliwiają skonfigurowanie obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c0f3-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="5c0f3-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="5c0f3-130">Opis</span><span class="sxs-lookup"><span data-stu-id="5c0f3-130">Description</span></span>  
 <span data-ttu-id="5c0f3-131">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi analizy IRI i nazw IDN.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="5c0f3-132">W przykładzie zostanie również wyczyszczone wszystkie ustawienia schematu, a następnie dodano obsługę ograniczników ścieżek o wartości procentowo zakodowanych w schemacie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="5c0f3-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="5c0f3-133">Kod</span><span class="sxs-lookup"><span data-stu-id="5c0f3-133">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c0f3-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5c0f3-134">See also</span></span>

- [<span data-ttu-id="5c0f3-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="5c0f3-135">Network Settings Schema</span></span>](index.md)
