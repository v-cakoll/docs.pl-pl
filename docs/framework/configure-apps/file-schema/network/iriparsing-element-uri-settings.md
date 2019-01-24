---
title: '&lt;iriParsing&gt; — Element (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: ca8fc86b5b64b971e54eec8f7338010394b73239
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552947"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="b2762-102">&lt;iriParsing&gt; — Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="b2762-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="b2762-103">Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="b2762-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="b2762-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="b2762-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="b2762-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="b2762-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="b2762-106">\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="b2762-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="b2762-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="b2762-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="b2762-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b2762-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b2762-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b2762-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b2762-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b2762-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b2762-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b2762-111">Attributes</span></span>  
  
|<span data-ttu-id="b2762-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="b2762-112">**Element**</span></span>|<span data-ttu-id="b2762-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b2762-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="b2762-114">Określa, czy analiza kodu IRI jest włączone.</span><span class="sxs-lookup"><span data-stu-id="b2762-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="b2762-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="b2762-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b2762-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b2762-116">Child Elements</span></span>  
 <span data-ttu-id="b2762-117">Brak</span><span class="sxs-lookup"><span data-stu-id="b2762-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b2762-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b2762-118">Parent Elements</span></span>  
  
|<span data-ttu-id="b2762-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="b2762-119">**Element**</span></span>|<span data-ttu-id="b2762-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b2762-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b2762-121">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="b2762-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="b2762-122">Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="b2762-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b2762-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b2762-123">Remarks</span></span>  
 <span data-ttu-id="b2762-124">Istniejące <xref:System.Uri> klasy został rozszerzony w .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="b2762-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="b2762-125">3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="b2762-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="b2762-126">Bieżący użytkownicy nie będą widzieć wszelkie zmiany w zachowaniu .NET Framework 2.0, chyba że umożliwiają one specjalnie IRI i IDN pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="b2762-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="b2762-127">Dzięki temu zgodność aplikacji z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2762-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="b2762-128">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="b2762-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="b2762-129">Dodaj następujący wiersz do pliku machine.config w katalogu .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="b2762-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="b2762-130">Określ, czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="b2762-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="b2762-131">Można to zrobić w pliku machine.config lub w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="b2762-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="b2762-132">Włączanie analizy IRI (iriParsing włączone = `true`) będziesz robić normalizacji i znak sprawdzanie zgodnie z IRI najnowsze reguły w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="b2762-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="b2762-133">Wartość domyślna to `false` będzie czy normalizacji i znak sprawdzanie zgodnie z RFC 2396 i ze standardem RFC 3986 (dla literałów IPv6).</span><span class="sxs-lookup"><span data-stu-id="b2762-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="b2762-134">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b2762-134">Configuration Files</span></span>  
 <span data-ttu-id="b2762-135">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="b2762-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2762-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="b2762-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="b2762-137">Opis</span><span class="sxs-lookup"><span data-stu-id="b2762-137">Description</span></span>  
 <span data-ttu-id="b2762-138">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="b2762-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="b2762-139">Kod</span><span class="sxs-lookup"><span data-stu-id="b2762-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b2762-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b2762-140">See also</span></span>
- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="b2762-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b2762-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
