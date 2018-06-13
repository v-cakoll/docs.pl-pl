---
title: '&lt;iriParsing&gt; elementu (ustawienia identyfikatorów Uri)'
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f05f7e35d69f789d3ebb371689aafbc84004b732
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743306"
---
# <a name="ltiriparsinggt-element-uri-settings"></a><span data-ttu-id="eff72-102">&lt;iriParsing&gt; elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="eff72-102">&lt;iriParsing&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="eff72-103">Określa identyfikator zasobu międzynarodowych (IRI) podczas analizowania odnosi się do <xref:System.Uri> i określa, czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="eff72-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="eff72-104">Schemat hierarchii</span><span class="sxs-lookup"><span data-stu-id="eff72-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="eff72-105">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="eff72-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="eff72-106">\<Identyfikator URI > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="eff72-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="eff72-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="eff72-107">\<iriParsing></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="eff72-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="eff72-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eff72-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="eff72-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eff72-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="eff72-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eff72-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="eff72-111">Attributes</span></span>  
  
|<span data-ttu-id="eff72-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="eff72-112">**Element**</span></span>|<span data-ttu-id="eff72-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="eff72-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="eff72-114">Określa, czy włączono IRI analizy.</span><span class="sxs-lookup"><span data-stu-id="eff72-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="eff72-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="eff72-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eff72-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="eff72-116">Child Elements</span></span>  
 <span data-ttu-id="eff72-117">Brak</span><span class="sxs-lookup"><span data-stu-id="eff72-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eff72-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="eff72-118">Parent Elements</span></span>  
  
|<span data-ttu-id="eff72-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="eff72-119">**Element**</span></span>|<span data-ttu-id="eff72-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="eff72-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eff72-121">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="eff72-121">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="eff72-122">Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="eff72-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eff72-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eff72-123">Remarks</span></span>  
 <span data-ttu-id="eff72-124">Istniejące <xref:System.Uri> klasy został rozszerzony w programie .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="eff72-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="eff72-125">3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1, aby zapewnić obsługę międzynarodowej identyfikatory zasobów (IRI) oraz międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="eff72-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="eff72-126">Bieżący użytkownicy nie będą widzieli zmiany z zachowaniem .NET Framework 2.0, o ile nie są jawnie włączyć IRI i IDN obsługuje.</span><span class="sxs-lookup"><span data-stu-id="eff72-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="eff72-127">Dzięki temu zgodność aplikacji we wcześniejszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="eff72-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="eff72-128">Aby włączyć obsługę IRI, wymagane są następujące zmiany dwóch:</span><span class="sxs-lookup"><span data-stu-id="eff72-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="eff72-129">Dodaj następujący wiersz w pliku machine.config w katalogu .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="eff72-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="eff72-130">Określ, czy podczas analizowania reguły IRI powinny być stosowane.</span><span class="sxs-lookup"><span data-stu-id="eff72-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="eff72-131">Można to zrobić w pliku machine.config lub w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="eff72-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="eff72-132">Włączenie analizy IRI (iriParsing włączone = `true`) wykona normalizacji i znak sprawdzanie zgodnie z najnowszą IRI reguł w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="eff72-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="eff72-133">Wartość domyślna to `false` i zostanie nie normalizacji i znak sprawdzanie zgodnie z RFC 2396 i RFC 3986 (dla literałów IPv6).</span><span class="sxs-lookup"><span data-stu-id="eff72-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="eff72-134">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eff72-134">Configuration Files</span></span>  
 <span data-ttu-id="eff72-135">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="eff72-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff72-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="eff72-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="eff72-137">Opis</span><span class="sxs-lookup"><span data-stu-id="eff72-137">Description</span></span>  
 <span data-ttu-id="eff72-138">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="eff72-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="eff72-139">Kod</span><span class="sxs-lookup"><span data-stu-id="eff72-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eff72-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eff72-140">See Also</span></span>  
 <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="eff72-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="eff72-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
