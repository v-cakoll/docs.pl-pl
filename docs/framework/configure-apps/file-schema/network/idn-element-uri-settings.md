---
title: "&lt;IDN&gt; elementu (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 44e2db95ec354fff4356a3619fa8230faf67544d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltidngt-element-uri-settings"></a><span data-ttu-id="a6ff3-102">&lt;IDN&gt; elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="a6ff3-102">&lt;idn&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="a6ff3-103">Określa, czy podczas analizowania międzynarodowych nazw domen (IDN) została zastosowana do nazwy domeny.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="a6ff3-104">Schemat hierarchii</span><span class="sxs-lookup"><span data-stu-id="a6ff3-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="a6ff3-105">\<Konfiguracja > — Element</span><span class="sxs-lookup"><span data-stu-id="a6ff3-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="a6ff3-106">\<Identyfikator URI > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="a6ff3-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="a6ff3-107">\<IDN ></span><span class="sxs-lookup"><span data-stu-id="a6ff3-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="a6ff3-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6ff3-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6ff3-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="a6ff3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a6ff3-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6ff3-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="a6ff3-111">Attributes</span></span>  
  
|<span data-ttu-id="a6ff3-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="a6ff3-112">**Element**</span></span>|<span data-ttu-id="a6ff3-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a6ff3-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="a6ff3-114">Określa, czy podczas analizowania międzynarodowych nazw domen (IDN) jest stosowana do nazwy domeny wartością domyślną jest Brak.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6ff3-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="a6ff3-115">Child Elements</span></span>  
 <span data-ttu-id="a6ff3-116">Brak</span><span class="sxs-lookup"><span data-stu-id="a6ff3-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6ff3-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="a6ff3-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a6ff3-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="a6ff3-118">**Element**</span></span>|<span data-ttu-id="a6ff3-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="a6ff3-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a6ff3-120">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="a6ff3-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="a6ff3-121">Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6ff3-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6ff3-122">Remarks</span></span>  
 <span data-ttu-id="a6ff3-123">Istniejące <xref:System.Uri> klasy został rozszerzony w programie .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="a6ff3-124">3.0 z dodatkiem SP1, a 2.0 z dodatkiem SP1 z obsługą międzynarodowej identyfikatory zasobów (IRI) oraz międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="a6ff3-125">Bieżący użytkownicy nie będą widzieli zmiany z zachowaniem .NET Framework 2.0, o ile nie są jawnie włączyć IRI i IDN obsługuje.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="a6ff3-126">Dzięki temu zgodność aplikacji we wcześniejszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a6ff3-127">Aby włączyć obsługę IRI, wymagane są następujące zmiany dwóch:</span><span class="sxs-lookup"><span data-stu-id="a6ff3-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1.  <span data-ttu-id="a6ff3-128">Dodaj następujący wiersz w pliku machine.config w katalogu .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="a6ff3-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  <span data-ttu-id="a6ff3-129">Określ, czy mają być stosowane podczas analizowania międzynarodowych nazw domen (IDN) na nazwę domeny i czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="a6ff3-130">Można to zrobić w pliku machine.config lub w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="a6ff3-131">Istnieją trzy możliwe wartości IDN w zależności od serwerów DNS, które są używane:</span><span class="sxs-lookup"><span data-stu-id="a6ff3-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
-   <span data-ttu-id="a6ff3-132">IDN włączone = All</span><span class="sxs-lookup"><span data-stu-id="a6ff3-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="a6ff3-133">Ta wartość przekonwertuje wszystkie nazwy domen Unicode odpowiedniki Punycode (nazwy IDN).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
-   <span data-ttu-id="a6ff3-134">IDN włączone = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="a6ff3-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="a6ff3-135">Ta wartość przekonwertuje wszystkie nazwy domen Unicode nie w lokalnym intranecie używania odpowiedniki Punycode (nazwy IDN).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="a6ff3-136">W takim przypadku do obsługi międzynarodowe nazwy w lokalnym intranecie, serwery DNS, które będą używane dla dostępu z intranetu powinien obsługiwać rozpoznawania nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
-   <span data-ttu-id="a6ff3-137">IDN włączone = Brak</span><span class="sxs-lookup"><span data-stu-id="a6ff3-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="a6ff3-138">Ta wartość nie przekonwertuje wszystkie nazwy domen Unicode do użycia Punycode.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="a6ff3-139">Jest to wartość domyślna, zgodnie z zachowania programu .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="a6ff3-140">Włączanie IDN przekonwertuje wszystkich etykiet Unicode w domenie o nazwie odpowiedniki ciąg Punycode.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="a6ff3-141">Ciąg Punycode nazwy zawierają tylko znaki ASCII i zawsze rozpoczyna się od prefiksu xn--.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="a6ff3-142">Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz dokument RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="a6ff3-143">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a6ff3-143">Configuration Files</span></span>  
 <span data-ttu-id="a6ff3-144">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a6ff3-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a6ff3-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a6ff3-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a6ff3-146">Opis</span><span class="sxs-lookup"><span data-stu-id="a6ff3-146">Description</span></span>  
 <span data-ttu-id="a6ff3-147">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="a6ff3-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="a6ff3-148">Kod</span><span class="sxs-lookup"><span data-stu-id="a6ff3-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6ff3-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6ff3-149">See Also</span></span>  
 <xref:System.Configuration.IdnElement?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 [<span data-ttu-id="a6ff3-150">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="a6ff3-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
