---
title: <iriParsing>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 2c99edf2f1a03e0e510858c106cad43b0eaa27b4
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664085"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="1d830-102">\<iriParsing >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="1d830-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="1d830-103">Określa <xref:System.Uri> , czy do i czy należy zastosować analizę IRI (International Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="1d830-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
## <a name="schema-hierarchy"></a><span data-ttu-id="1d830-104">Hierarchia schematu</span><span class="sxs-lookup"><span data-stu-id="1d830-104">Schema Hierarchy</span></span>  
 [<span data-ttu-id="1d830-105">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d830-105">\<configuration> Element</span></span>](../configuration-element.md)  
  
 [<span data-ttu-id="1d830-106">\<Identyfikator URI > element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="1d830-106">\<Uri> Element (Uri Settings)</span></span>](uri-element-uri-settings.md)  
  
 [<span data-ttu-id="1d830-107">\<iriParsing ></span><span class="sxs-lookup"><span data-stu-id="1d830-107">\<iriParsing></span></span>](iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a><span data-ttu-id="1d830-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="1d830-108">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d830-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1d830-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d830-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1d830-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d830-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1d830-111">Attributes</span></span>  
  
|<span data-ttu-id="1d830-112">**Element**</span><span class="sxs-lookup"><span data-stu-id="1d830-112">**Element**</span></span>|<span data-ttu-id="1d830-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1d830-113">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="1d830-114">Określa, czy jest włączone analizowanie IRI.</span><span class="sxs-lookup"><span data-stu-id="1d830-114">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="1d830-115">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="1d830-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d830-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1d830-116">Child Elements</span></span>  
 <span data-ttu-id="1d830-117">Brak</span><span class="sxs-lookup"><span data-stu-id="1d830-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d830-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1d830-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1d830-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="1d830-119">**Element**</span></span>|<span data-ttu-id="1d830-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1d830-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1d830-121">uri</span><span class="sxs-lookup"><span data-stu-id="1d830-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="1d830-122">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="1d830-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d830-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1d830-123">Remarks</span></span>  
 <span data-ttu-id="1d830-124">Istniejąca <xref:System.Uri> Klasa została rozszerzona w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="1d830-124">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="1d830-125">3,0 SP1 i 2,0 SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="1d830-125">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="1d830-126">Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="1d830-126">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="1d830-127">Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d830-127">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1d830-128">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="1d830-128">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="1d830-129">Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="1d830-129">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="1d830-130">Określ, czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="1d830-130">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="1d830-131">Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.</span><span class="sxs-lookup"><span data-stu-id="1d830-131">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="1d830-132">Włączenie analizy IRI (iriParsing Enabled = `true`) umożliwi normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="1d830-132">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="1d830-133">Wartość domyślna to `false` i umożliwia normalizację i sprawdzanie znaków zgodnie ze standardami RFC 2396 i RFC 3986 (dla literałów IPv6).</span><span class="sxs-lookup"><span data-stu-id="1d830-133">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="1d830-134">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1d830-134">Configuration Files</span></span>  
 <span data-ttu-id="1d830-135">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1d830-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d830-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="1d830-136">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1d830-137">Opis</span><span class="sxs-lookup"><span data-stu-id="1d830-137">Description</span></span>  
 <span data-ttu-id="1d830-138">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi analizy IRI i nazw IDN.</span><span class="sxs-lookup"><span data-stu-id="1d830-138">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1d830-139">Kod</span><span class="sxs-lookup"><span data-stu-id="1d830-139">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d830-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1d830-140">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="1d830-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1d830-141">Network Settings Schema</span></span>](index.md)
