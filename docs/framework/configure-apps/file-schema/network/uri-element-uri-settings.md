---
title: <Uri> — Element (Ustawienia identyfikatora Uri)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: f432be7594b1659dfcae0c6eee706358230f2cbb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269253"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="c3448-102">\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="c3448-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="c3448-103">Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="c3448-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="c3448-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="c3448-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="c3448-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="c3448-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c3448-106">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="c3448-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="c3448-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3448-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3448-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c3448-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c3448-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c3448-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3448-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c3448-110">Attributes</span></span>  
 <span data-ttu-id="c3448-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c3448-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c3448-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c3448-112">Child Elements</span></span>  
  
|<span data-ttu-id="c3448-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="c3448-113">**Element**</span></span>|<span data-ttu-id="c3448-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c3448-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3448-115">idn</span><span class="sxs-lookup"><span data-stu-id="c3448-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="c3448-116">Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="c3448-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="c3448-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="c3448-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="c3448-118">Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="c3448-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="c3448-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="c3448-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="c3448-120">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="c3448-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3448-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c3448-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c3448-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="c3448-122">**Element**</span></span>|<span data-ttu-id="c3448-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c3448-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c3448-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c3448-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c3448-125">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c3448-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3448-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3448-126">Remarks</span></span>  
 <span data-ttu-id="c3448-127">`uri` Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c3448-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="c3448-128">Ustawienia skonfigurować obsługę IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="c3448-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c3448-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c3448-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c3448-130">Opis</span><span class="sxs-lookup"><span data-stu-id="c3448-130">Description</span></span>  
 <span data-ttu-id="c3448-131">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="c3448-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="c3448-132">Przykład czyści także wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="c3448-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c3448-133">Kod</span><span class="sxs-lookup"><span data-stu-id="c3448-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c3448-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3448-134">See also</span></span>
- [<span data-ttu-id="c3448-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c3448-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
