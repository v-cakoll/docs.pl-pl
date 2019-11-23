---
title: <iriParsing>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698094"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="1fa6f-102">\<element > iriParsing (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="1fa6f-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="1fa6f-103">Określa, czy do <xref:System.Uri> jest stosowana analiza międzynarodowego identyfikatora zasobów (IRI) i czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[<span data-ttu-id="1fa6f-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="1fa6f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="1fa6f-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="1fa6f-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="1fa6f-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<iriParsing >**</span><span class="sxs-lookup"><span data-stu-id="1fa6f-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fa6f-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="1fa6f-107">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1fa6f-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="1fa6f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="1fa6f-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1fa6f-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="1fa6f-110">Attributes</span></span>  
  
|<span data-ttu-id="1fa6f-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="1fa6f-111">**Element**</span></span>|<span data-ttu-id="1fa6f-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1fa6f-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="1fa6f-113">Określa, czy jest włączone analizowanie IRI.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-113">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="1fa6f-114">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-114">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1fa6f-115">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="1fa6f-115">Child Elements</span></span>  
 <span data-ttu-id="1fa6f-116">Brak</span><span class="sxs-lookup"><span data-stu-id="1fa6f-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1fa6f-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="1fa6f-117">Parent Elements</span></span>  
  
|<span data-ttu-id="1fa6f-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="1fa6f-118">**Element**</span></span>|<span data-ttu-id="1fa6f-119">**Opis**</span><span class="sxs-lookup"><span data-stu-id="1fa6f-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1fa6f-120">uri</span><span class="sxs-lookup"><span data-stu-id="1fa6f-120">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="1fa6f-121">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="1fa6f-121">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1fa6f-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1fa6f-122">Remarks</span></span>  
 <span data-ttu-id="1fa6f-123">Istniejąca Klasa <xref:System.Uri> została rozszerzona w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-123">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="1fa6f-124">3,0 SP1 i 2,0 SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="1fa6f-124">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="1fa6f-125">Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-125">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="1fa6f-126">Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-126">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="1fa6f-127">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="1fa6f-127">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="1fa6f-128">Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="1fa6f-128">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="1fa6f-129">Określ, czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-129">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="1fa6f-130">Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-130">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="1fa6f-131">Włączenie analizy IRI (iriParsing Enabled = `true`) umożliwi normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-131">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="1fa6f-132">Wartość domyślna to `false` i będzie wykonywać normalizację i sprawdzanie znaków zgodnie ze standardami RFC 2396 i RFC 3986 (dla literałów IPv6).</span><span class="sxs-lookup"><span data-stu-id="1fa6f-132">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="1fa6f-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1fa6f-133">Configuration Files</span></span>  
 <span data-ttu-id="1fa6f-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="1fa6f-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fa6f-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fa6f-135">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="1fa6f-136">Opis</span><span class="sxs-lookup"><span data-stu-id="1fa6f-136">Description</span></span>  
 <span data-ttu-id="1fa6f-137">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi analizy IRI i nazw IDN.</span><span class="sxs-lookup"><span data-stu-id="1fa6f-137">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="1fa6f-138">Kod</span><span class="sxs-lookup"><span data-stu-id="1fa6f-138">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fa6f-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1fa6f-139">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="1fa6f-140">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="1fa6f-140">Network Settings Schema</span></span>](index.md)
