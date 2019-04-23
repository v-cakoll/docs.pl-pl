---
title: <Uri>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
ms.openlocfilehash: 1f3573babd2e363a78f0ad454f0ba36c87ba6390
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212146"
---
# <a name="uri-element-uri-settings"></a><span data-ttu-id="e56d2-102">\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="e56d2-102">\<Uri> Element (Uri Settings)</span></span>
<span data-ttu-id="e56d2-103">Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="e56d2-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="e56d2-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="e56d2-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="e56d2-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="e56d2-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="e56d2-106">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="e56d2-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="e56d2-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="e56d2-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e56d2-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e56d2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e56d2-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e56d2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e56d2-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e56d2-110">Attributes</span></span>  
 <span data-ttu-id="e56d2-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="e56d2-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e56d2-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e56d2-112">Child Elements</span></span>  
  
|<span data-ttu-id="e56d2-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="e56d2-113">**Element**</span></span>|<span data-ttu-id="e56d2-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e56d2-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e56d2-115">idn</span><span class="sxs-lookup"><span data-stu-id="e56d2-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="e56d2-116">Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="e56d2-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="e56d2-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="e56d2-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="e56d2-118">Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="e56d2-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="e56d2-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="e56d2-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="e56d2-120">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="e56d2-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e56d2-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e56d2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e56d2-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="e56d2-122">**Element**</span></span>|<span data-ttu-id="e56d2-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="e56d2-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e56d2-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="e56d2-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="e56d2-125">Zawiera ustawienia dla wszystkich przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e56d2-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e56d2-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e56d2-126">Remarks</span></span>  
 <span data-ttu-id="e56d2-127">`uri` Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e56d2-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="e56d2-128">Ustawienia skonfigurować obsługę IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="e56d2-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56d2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="e56d2-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="e56d2-130">Opis</span><span class="sxs-lookup"><span data-stu-id="e56d2-130">Description</span></span>  
 <span data-ttu-id="e56d2-131">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="e56d2-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="e56d2-132">Przykład czyści także wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="e56d2-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="e56d2-133">Kod</span><span class="sxs-lookup"><span data-stu-id="e56d2-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e56d2-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e56d2-134">See also</span></span>

- [<span data-ttu-id="e56d2-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="e56d2-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
