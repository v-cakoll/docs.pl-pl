---
title: "&lt;Identyfikator URI&gt; elementu (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 735a6596b22e6d6fdcff776dd79224230db5b7b3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lturigt-element-uri-settings"></a><span data-ttu-id="c17ef-102">&lt;Identyfikator URI&gt; elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="c17ef-102">&lt;Uri&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="c17ef-103">Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="c17ef-103">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="c17ef-104">Schemat hierarchii</span><span class="sxs-lookup"><span data-stu-id="c17ef-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="c17ef-105">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="c17ef-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="c17ef-106">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="c17ef-106">\<uri></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="c17ef-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="c17ef-107">Syntax</span></span>  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c17ef-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="c17ef-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c17ef-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="c17ef-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c17ef-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="c17ef-110">Attributes</span></span>  
 <span data-ttu-id="c17ef-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="c17ef-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c17ef-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="c17ef-112">Child Elements</span></span>  
  
|<span data-ttu-id="c17ef-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="c17ef-113">**Element**</span></span>|<span data-ttu-id="c17ef-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c17ef-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c17ef-115">IDN</span><span class="sxs-lookup"><span data-stu-id="c17ef-115">idn</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|<span data-ttu-id="c17ef-116">Określa, czy międzynarodowych nazw domen (IDN) podczas analizowania została zastosowana do nazw domen.</span><span class="sxs-lookup"><span data-stu-id="c17ef-116">Specifies if Internationalized Domain Name (IDN) parsing is applied to domain names.</span></span>|  
|[<span data-ttu-id="c17ef-117">iriParsing</span><span class="sxs-lookup"><span data-stu-id="c17ef-117">iriParsing</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|<span data-ttu-id="c17ef-118">Określa identyfikator zasobu międzynarodowych (IRI) podczas analizowania odnosi się do <xref:System.Uri> i określa, czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="c17ef-118">Specifies if International Resource Identifier (IRI) parsing is applied to <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>|  
|[<span data-ttu-id="c17ef-119">schemeSettings</span><span class="sxs-lookup"><span data-stu-id="c17ef-119">schemeSettings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="c17ef-120">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="c17ef-120">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c17ef-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="c17ef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c17ef-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="c17ef-122">**Element**</span></span>|<span data-ttu-id="c17ef-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="c17ef-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="c17ef-124">Konfiguracja</span><span class="sxs-lookup"><span data-stu-id="c17ef-124">configuration</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="c17ef-125">Zawiera ustawienia dla wszystkich obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="c17ef-125">Contains settings for all namespaces.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c17ef-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c17ef-126">Remarks</span></span>  
 <span data-ttu-id="c17ef-127">`uri` Element zawiera ustawienia dla członków <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c17ef-127">The `uri` element contains settings for members of the <xref:System.Uri> class used by classes in the <xref:System.Net> namespace.</span></span> <span data-ttu-id="c17ef-128">Ustawienia skonfigurować obsługę IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="c17ef-128">The settings configure support for IRI and IDN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c17ef-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="c17ef-129">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="c17ef-130">Opis</span><span class="sxs-lookup"><span data-stu-id="c17ef-130">Description</span></span>  
 <span data-ttu-id="c17ef-131">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="c17ef-131">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span> <span data-ttu-id="c17ef-132">Przykład także czyści wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="c17ef-132">The example also clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
### <a name="code"></a><span data-ttu-id="c17ef-133">Kod</span><span class="sxs-lookup"><span data-stu-id="c17ef-133">Code</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c17ef-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c17ef-134">See Also</span></span>  
 [<span data-ttu-id="c17ef-135">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="c17ef-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
