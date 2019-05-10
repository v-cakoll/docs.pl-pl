---
title: <idn>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 369decf8551c76293ca513b8a3e58b4142a74773
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592760"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="24a2e-102">\<IDN >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="24a2e-102">\<idn> Element (Uri Settings)</span></span>
<span data-ttu-id="24a2e-103">Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazwy domeny.</span><span class="sxs-lookup"><span data-stu-id="24a2e-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="24a2e-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="24a2e-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="24a2e-105">\<Konfiguracja > Element</span><span class="sxs-lookup"><span data-stu-id="24a2e-105">\<configuration> Element</span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [<span data-ttu-id="24a2e-106">\<Identyfikator URI >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="24a2e-106">\<Uri> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [<span data-ttu-id="24a2e-107">\<idn></span><span class="sxs-lookup"><span data-stu-id="24a2e-107">\<idn></span></span>](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="24a2e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="24a2e-108">Syntax</span></span>  
  
```xml  
<idn  
  enabled="All|AllExceptIntranet|None"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="24a2e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="24a2e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="24a2e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="24a2e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="24a2e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="24a2e-111">Attributes</span></span>  
  
|<span data-ttu-id="24a2e-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="24a2e-112">**Element**</span></span>|<span data-ttu-id="24a2e-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="24a2e-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="24a2e-114">Określa, czy analizy Zinternacjonalizowanych nazw domen (IDN) jest stosowany do nazwy domeny wartość domyślna to Brak.</span><span class="sxs-lookup"><span data-stu-id="24a2e-114">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="24a2e-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="24a2e-115">Child Elements</span></span>  
 <span data-ttu-id="24a2e-116">Brak</span><span class="sxs-lookup"><span data-stu-id="24a2e-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="24a2e-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="24a2e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="24a2e-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="24a2e-118">**Element**</span></span>|<span data-ttu-id="24a2e-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="24a2e-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="24a2e-120">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="24a2e-120">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="24a2e-121">Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="24a2e-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24a2e-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24a2e-122">Remarks</span></span>  
 <span data-ttu-id="24a2e-123">Istniejące <xref:System.Uri> klasy został rozszerzony w .NET Framework 3.5.</span><span class="sxs-lookup"><span data-stu-id="24a2e-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="24a2e-124">3.0 z dodatkiem SP1 i 2.0 z dodatkiem SP1 z obsługą międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="24a2e-124">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="24a2e-125">Bieżący użytkownicy nie będą widzieć wszelkie zmiany w zachowaniu .NET Framework 2.0, chyba że umożliwiają one specjalnie IRI i IDN pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="24a2e-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="24a2e-126">Dzięki temu zgodność aplikacji z wcześniejszych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="24a2e-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="24a2e-127">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="24a2e-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="24a2e-128">Dodaj następujący wiersz do pliku machine.config w katalogu .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="24a2e-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="24a2e-129">Określić, czy analizy Zinternacjonalizowanych nazw domen (IDN) stosowane do nazwy domeny i czy powinny być stosowane IRI podczas analizowania reguły.</span><span class="sxs-lookup"><span data-stu-id="24a2e-129">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="24a2e-130">Można to zrobić w pliku machine.config lub w pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="24a2e-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="24a2e-131">Istnieją trzy możliwe wartości IDN w zależności od serwerów DNS, które są używane:</span><span class="sxs-lookup"><span data-stu-id="24a2e-131">There are three possible values for IDN depending on the DNS servers that are used:</span></span>  
  
- <span data-ttu-id="24a2e-132">IDN, włączone = All</span><span class="sxs-lookup"><span data-stu-id="24a2e-132">idn enabled = All</span></span>  
  
     <span data-ttu-id="24a2e-133">Ta wartość spowoduje przekonwertowanie wszystkie nazwy domen, Unicode na ich odpowiedniki Punycode (nazwy IDN).</span><span class="sxs-lookup"><span data-stu-id="24a2e-133">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>  
  
- <span data-ttu-id="24a2e-134">IDN, włączone = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="24a2e-134">idn enabled = AllExceptIntranet</span></span>  
  
     <span data-ttu-id="24a2e-135">Ta wartość będzie przekonwertować wszystkie nazwy domeny Unicode nie w lokalnej sieci Intranet w celu użyj odpowiedników Punycode (nazwy IDN).</span><span class="sxs-lookup"><span data-stu-id="24a2e-135">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="24a2e-136">W tym przypadku do obsługi międzynarodowe nazwy w lokalnym intranecie, serwerów DNS, które są używane dla dostępu z intranetu powinien obsługiwać rozpoznawanie nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="24a2e-136">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>  
  
- <span data-ttu-id="24a2e-137">IDN, włączone = None</span><span class="sxs-lookup"><span data-stu-id="24a2e-137">idn enabled = None</span></span>  
  
     <span data-ttu-id="24a2e-138">Ta wartość nie zostanie przekonwertować wszystkie nazwy domen Unicode, aby użyć Punycode.</span><span class="sxs-lookup"><span data-stu-id="24a2e-138">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="24a2e-139">Jest to wartość domyślna, która jest zgodna z zachowaniem .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="24a2e-139">This is the default value which is consistent with the .NET Framework 2.0 behaviour.</span></span>  
  
 <span data-ttu-id="24a2e-140">Włączanie IDN, spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki Punycode.</span><span class="sxs-lookup"><span data-stu-id="24a2e-140">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="24a2e-141">Nazwy Punycode zawierać tylko znaki ASCII i zawsze rozpoczynają się prefiksem xn —.</span><span class="sxs-lookup"><span data-stu-id="24a2e-141">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="24a2e-142">Przyczyną tego jest do obsługi istniejących serwerów DNS w Internecie, ponieważ większość serwery DNS obsługują tylko znaki ASCII (zobacz RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="24a2e-142">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="24a2e-143">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="24a2e-143">Configuration Files</span></span>  
 <span data-ttu-id="24a2e-144">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="24a2e-144">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24a2e-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="24a2e-145">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="24a2e-146">Opis</span><span class="sxs-lookup"><span data-stu-id="24a2e-146">Description</span></span>  
 <span data-ttu-id="24a2e-147">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN.</span><span class="sxs-lookup"><span data-stu-id="24a2e-147">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="24a2e-148">Kod</span><span class="sxs-lookup"><span data-stu-id="24a2e-148">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="24a2e-149">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24a2e-149">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="24a2e-150">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="24a2e-150">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
