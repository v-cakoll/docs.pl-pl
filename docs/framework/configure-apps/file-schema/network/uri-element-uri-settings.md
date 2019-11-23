---
title: <uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: a492baf9951466383ca0277a2927b8554e5bb332
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697441"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="e0b4e-102">\<> elementu URI (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="e0b4e-102">\<uri> Element (Uri Settings)</span></span>
<span data-ttu-id="e0b4e-103">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e0b4e-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
[<span data-ttu-id="e0b4e-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="e0b4e-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="e0b4e-105">&nbsp;&nbsp; **\<uri >**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-105">&nbsp;&nbsp;**\<uri>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0b4e-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0b4e-106">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0b4e-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e0b4e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="e0b4e-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0b4e-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e0b4e-109">Attributes</span></span>  
 <span data-ttu-id="e0b4e-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e0b4e-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e0b4e-111">Child Elements</span></span>  
  
|<span data-ttu-id="e0b4e-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-112">**Element**</span></span>|<span data-ttu-id="e0b4e-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0b4e-114">IDN</span><span class="sxs-lookup"><span data-stu-id="e0b4e-114">idn</span></span>](idn-element-uri-settings.md)|<span data-ttu-id="e0b4e-115">Określa, czy do nazw domen są stosowane analizowanie międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="e0b4e-115">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="e0b4e-116">iriParsing</span><span class="sxs-lookup"><span data-stu-id="e0b4e-116">iriParsing</span></span>](iriparsing-element-uri-settings.md)|<span data-ttu-id="e0b4e-117">Określa, czy do <xref:System.Uri> jest stosowana analiza międzynarodowego identyfikatora zasobów (IRI) i czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-117">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="e0b4e-118">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="e0b4e-118">schemeSettings</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="e0b4e-119">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e0b4e-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e0b4e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e0b4e-121">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-121">**Element**</span></span>|<span data-ttu-id="e0b4e-122">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e0b4e-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0b4e-123">skonfigurować</span><span class="sxs-lookup"><span data-stu-id="e0b4e-123">configuration</span></span>](../configuration-element.md)|<span data-ttu-id="e0b4e-124">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-124">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0b4e-125">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0b4e-125">Remarks</span></span>  
 <span data-ttu-id="e0b4e-126">Element `uri` zawiera ustawienia dla elementów członkowskich klasy <xref:System.Uri> używane przez klasy w przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-126">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="e0b4e-127">Ustawienia umożliwiają skonfigurowanie obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-127">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0b4e-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="e0b4e-128">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e0b4e-129">Opis</span><span class="sxs-lookup"><span data-stu-id="e0b4e-129">Description</span></span>  
 <span data-ttu-id="e0b4e-130">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi analizy IRI i nazw IDN.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-130">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="e0b4e-131">W przykładzie zostanie również wyczyszczone wszystkie ustawienia schematu, a następnie dodano obsługę ograniczników ścieżek o wartości procentowo zakodowanych w schemacie protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e0b4e-131">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e0b4e-132">Kod</span><span class="sxs-lookup"><span data-stu-id="e0b4e-132">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0b4e-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0b4e-133">See also</span></span>

- [<span data-ttu-id="e0b4e-134">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e0b4e-134">Network Settings Schema</span></span>](index.md)
