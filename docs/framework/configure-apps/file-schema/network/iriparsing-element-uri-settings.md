---
title: <iriParsing>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: fd617d1b4ac8e532c6f9aeaa01465e9866b059e9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "71698094"
---
# <a name="iriparsing-element-uri-settings"></a><span data-ttu-id="f3623-102">\<iriParsing>, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="f3623-102">\<iriParsing> Element (Uri Settings)</span></span>
<span data-ttu-id="f3623-103">Określa, czy do <xref:System.Uri> i czy należy zastosować analizę IRI (International Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="f3623-103">Specifies if International Resource Identifier (IRI) parsing is applied to a <xref:System.Uri> and whether IRI parsing rules should be applied.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<iriParsing>**  
  
## <a name="syntax"></a><span data-ttu-id="f3623-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f3623-104">Syntax</span></span>  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3623-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f3623-105">Attributes and Elements</span></span>  
 <span data-ttu-id="f3623-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f3623-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3623-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f3623-107">Attributes</span></span>  
  
|<span data-ttu-id="f3623-108">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="f3623-108">**Element**</span></span>|<span data-ttu-id="f3623-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3623-109">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="f3623-110">Określa, czy jest włączone analizowanie IRI.</span><span class="sxs-lookup"><span data-stu-id="f3623-110">Specifies whether IRI parsing is enabled.</span></span> <span data-ttu-id="f3623-111">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="f3623-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3623-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f3623-112">Child Elements</span></span>  
 <span data-ttu-id="f3623-113">Brak</span><span class="sxs-lookup"><span data-stu-id="f3623-113">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3623-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f3623-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f3623-115">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="f3623-115">**Element**</span></span>|<span data-ttu-id="f3623-116">**Opis**</span><span class="sxs-lookup"><span data-stu-id="f3623-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="f3623-117">adresu</span><span class="sxs-lookup"><span data-stu-id="f3623-117">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="f3623-118">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="f3623-118">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3623-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f3623-119">Remarks</span></span>  
 <span data-ttu-id="f3623-120">Istniejąca <xref:System.Uri> Klasa została rozszerzona w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="f3623-120">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="f3623-121">3,0 SP1 i 2,0 SP1, aby zapewnić obsługę międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="f3623-121">3.0 SP1, and 2.0 SP1 to provide support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="f3623-122">Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="f3623-122">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="f3623-123">Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f3623-123">This ensures application compatibility with prior versions of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f3623-124">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="f3623-124">To enable support for IRI, the following two changes are required:</span></span>  
  
1. <span data-ttu-id="f3623-125">Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0</span><span class="sxs-lookup"><span data-stu-id="f3623-125">Add the following line to the machine.config file under the .NET Framework 2.0 directory</span></span>  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="f3623-126">Określ, czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="f3623-126">Specify whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="f3623-127">Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.</span><span class="sxs-lookup"><span data-stu-id="f3623-127">This can be done in the machine.config or in the app.config file.</span></span>  
  
 <span data-ttu-id="f3623-128">Włączenie analizy IRI (iriParsing Enabled = `true` ) umożliwi normalizację i sprawdzanie znaków zgodnie z najnowszymi regułami IRI w dokumencie RFC 3987.</span><span class="sxs-lookup"><span data-stu-id="f3623-128">Enabling IRI parsing (iriParsing enabled = `true`) will do normalization and character checking according to the latest IRI rules in RFC 3987.</span></span> <span data-ttu-id="f3623-129">Wartość domyślna to `false` i umożliwia normalizację i sprawdzanie znaków zgodnie ze standardami rfc 2396 i rfc 3986 (dla literałów IPv6).</span><span class="sxs-lookup"><span data-stu-id="f3623-129">The default value is `false` and will do normalization and character checking according to RFC 2396 and RFC 3986 (for IPv6 literals).</span></span>  
  
### <a name="configuration-files"></a><span data-ttu-id="f3623-130">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f3623-130">Configuration Files</span></span>  
 <span data-ttu-id="f3623-131">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f3623-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3623-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="f3623-132">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="f3623-133">Opis</span><span class="sxs-lookup"><span data-stu-id="f3623-133">Description</span></span>  
 <span data-ttu-id="f3623-134">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi analizy IRI i nazw IDN.</span><span class="sxs-lookup"><span data-stu-id="f3623-134">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names.</span></span>  
  
### <a name="code"></a><span data-ttu-id="f3623-135">Kod</span><span class="sxs-lookup"><span data-stu-id="f3623-135">Code</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f3623-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f3623-136">See also</span></span>

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="f3623-137">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f3623-137">Network Settings Schema</span></span>](index.md)
