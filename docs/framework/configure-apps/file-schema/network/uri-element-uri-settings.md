---
title: '&lt;Identyfikator URI&gt; — Element (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a58c27500c0258415c12a5fd8e552b3ee43f50e8
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47108913"
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="53a2e-102">&lt;Identyfikator URI&gt; — Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="53a2e-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="53a2e-103">Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="53a2e-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="53a2e-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="53a2e-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="53a2e-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="53a2e-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="53a2e-106">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="53a2e-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="53a2e-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="53a2e-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53a2e-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="53a2e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="53a2e-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="53a2e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53a2e-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="53a2e-110">Attributes</span></span>  
 <span data-ttu-id="53a2e-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="53a2e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="53a2e-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="53a2e-112">Child Elements</span></span>  
  
|<span data-ttu-id="53a2e-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="53a2e-113">**Element**</span></span>|<span data-ttu-id="53a2e-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="53a2e-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="53a2e-115">IDN</span><span class="sxs-lookup"><span data-stu-id="53a2e-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="53a2e-116">Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="53a2e-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="53a2e-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="53a2e-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="53a2e-118">Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="53a2e-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="53a2e-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="53a2e-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="53a2e-120">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="53a2e-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53a2e-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="53a2e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="53a2e-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="53a2e-122">**Element**</span></span>|<span data-ttu-id="53a2e-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="53a2e-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="53a2e-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="53a2e-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="53a2e-125">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="53a2e-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53a2e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53a2e-126">Remarks</span></span>  
 <span data-ttu-id="53a2e-127">`uri` Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="53a2e-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="53a2e-128">Ustawienia skonfigurować obsługę IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="53a2e-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53a2e-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="53a2e-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="53a2e-130">Opis</span><span class="sxs-lookup"><span data-stu-id="53a2e-130">Description</span></span>  
 <span data-ttu-id="53a2e-131">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="53a2e-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="53a2e-132">Przykład czyści także wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="53a2e-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="53a2e-133">Kod</span><span class="sxs-lookup"><span data-stu-id="53a2e-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53a2e-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53a2e-134">See Also</span></span>  
 [<span data-ttu-id="53a2e-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="53a2e-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
