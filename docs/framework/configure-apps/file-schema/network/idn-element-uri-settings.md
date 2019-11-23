---
title: <idn>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 16c8e869-1791-4cf5-9244-3d3c738f60ec
ms.openlocfilehash: 533b2562f6e5c8d6c2bf452e56dff9a8bf8ab376
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698173"
---
# <a name="idn-element-uri-settings"></a><span data-ttu-id="b4b68-102">\<IDN > element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="b4b68-102">\<idn> Element (Uri Settings)</span></span>

<span data-ttu-id="b4b68-103">Określa, czy do nazwy domeny jest stosowane analizowanie międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="b4b68-103">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name.</span></span>
  
[<span data-ttu-id="b4b68-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="b4b68-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="b4b68-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b4b68-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="b4b68-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<idn >**</span><span class="sxs-lookup"><span data-stu-id="b4b68-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<idn>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4b68-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4b68-107">Syntax</span></span>  
  
```xml
<idn
  enabled="All|AllExceptIntranet|None"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4b68-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b4b68-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b4b68-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b4b68-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4b68-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b4b68-110">Attributes</span></span>  

|<span data-ttu-id="b4b68-111">**Element**</span><span class="sxs-lookup"><span data-stu-id="b4b68-111">**Element**</span></span>|<span data-ttu-id="b4b68-112">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b4b68-112">**Description**</span></span>|  
|-----------------|---------------------|  
|`enabled`|<span data-ttu-id="b4b68-113">Określa, czy do nazwy domeny jest stosowane analizowanie międzynarodowych nazw domen (IDN), wartość domyślna to None.</span><span class="sxs-lookup"><span data-stu-id="b4b68-113">Specifies if Internationalized Domain Name (IDN) parsing is applied to a domain name The default value is none.</span></span>|  

### <a name="child-elements"></a><span data-ttu-id="b4b68-114">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b4b68-114">Child elements</span></span>

<span data-ttu-id="b4b68-115">Brak</span><span class="sxs-lookup"><span data-stu-id="b4b68-115">None</span></span>
  
### <a name="parent-elements"></a><span data-ttu-id="b4b68-116">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b4b68-116">Parent elements</span></span>

|<span data-ttu-id="b4b68-117">**Element**</span><span class="sxs-lookup"><span data-stu-id="b4b68-117">**Element**</span></span>|<span data-ttu-id="b4b68-118">**Opis**</span><span class="sxs-lookup"><span data-stu-id="b4b68-118">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b4b68-119">uri</span><span class="sxs-lookup"><span data-stu-id="b4b68-119">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="b4b68-120">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="b4b68-120">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  

## <a name="remarks"></a><span data-ttu-id="b4b68-121">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4b68-121">Remarks</span></span>

<span data-ttu-id="b4b68-122">Istniejąca Klasa <xref:System.Uri> została rozszerzona w .NET Framework 3,5.</span><span class="sxs-lookup"><span data-stu-id="b4b68-122">The existing <xref:System.Uri> class has been extended in .NET Framework 3.5.</span></span> <span data-ttu-id="b4b68-123">3,0 SP1 i 2,0 SP1 z obsługą międzynarodowych identyfikatorów zasobów (IRI) i międzynarodowych nazw domen (IDN).</span><span class="sxs-lookup"><span data-stu-id="b4b68-123">3.0 SP1, and 2.0 SP1 with support for International Resource Identifiers (IRI) and Internationalized Domain Names (IDN).</span></span> <span data-ttu-id="b4b68-124">Bieżąca użytkownicy nie będą widzieć żadnych zmian w zachowaniu .NET Framework 2,0, o ile nie włączą one obsługi IRI i IDN.</span><span class="sxs-lookup"><span data-stu-id="b4b68-124">Current users will not see any change from the .NET Framework 2.0 behavior unless they specifically enable IRI and IDN support.</span></span> <span data-ttu-id="b4b68-125">Zapewnia to zgodność aplikacji z wcześniejszymi wersjami .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4b68-125">This ensures application compatibility with prior versions of the .NET Framework.</span></span>

<span data-ttu-id="b4b68-126">Aby włączyć obsługę IRI, wymagane są następujące dwie zmiany:</span><span class="sxs-lookup"><span data-stu-id="b4b68-126">To enable support for IRI, the following two changes are required:</span></span>

1. <span data-ttu-id="b4b68-127">Dodaj następujący wiersz do pliku Machine. config w katalogu .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="b4b68-127">Add the following line to the machine.config file under the .NET Framework 2.0 directory:</span></span>
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2. <span data-ttu-id="b4b68-128">Określ, czy do nazwy domeny mają być stosowane analizy międzynarodowej nazwy domeny (IDN) i czy mają być stosowane reguły analizy IRI.</span><span class="sxs-lookup"><span data-stu-id="b4b68-128">Specify whether you want Internationalized Domain Name (IDN) parsing applied to the domain name and whether IRI parsing rules should be applied.</span></span> <span data-ttu-id="b4b68-129">Tę czynność można wykonać w pliku Machine. config lub w oknie App. config.</span><span class="sxs-lookup"><span data-stu-id="b4b68-129">This can be done in the machine.config or in the app.config file.</span></span>

 <span data-ttu-id="b4b68-130">Istnieją trzy możliwe wartości IDN w zależności od używanych serwerów DNS:</span><span class="sxs-lookup"><span data-stu-id="b4b68-130">There are three possible values for IDN depending on the DNS servers that are used:</span></span>

- <span data-ttu-id="b4b68-131">włączono IDN = wszystkie</span><span class="sxs-lookup"><span data-stu-id="b4b68-131">idn enabled = All</span></span>  

     <span data-ttu-id="b4b68-132">Ta wartość spowoduje przekonwertowanie dowolnych nazw domen Unicode na ich odpowiedniki formacie Punycode (nazwy IDN).</span><span class="sxs-lookup"><span data-stu-id="b4b68-132">This value will convert any Unicode domain names to their Punycode equivalents (IDN names).</span></span>

- <span data-ttu-id="b4b68-133">włączono IDN = AllExceptIntranet</span><span class="sxs-lookup"><span data-stu-id="b4b68-133">idn enabled = AllExceptIntranet</span></span>

     <span data-ttu-id="b4b68-134">Ta wartość spowoduje przekonwertowanie wszystkich nazw domen Unicode, które nie są w lokalnym intranecie, aby użyć odpowiedników formacie Punycode (nazw IDN).</span><span class="sxs-lookup"><span data-stu-id="b4b68-134">This value will convert all Unicode domain names not on the local Intranet to use the Punycode equivalents (IDN names).</span></span> <span data-ttu-id="b4b68-135">W takim przypadku, aby obsługiwać nazwy międzynarodowe w lokalnym intranecie, serwery DNS, które są używane do sieci intranet, powinny obsługiwać rozpoznawanie nazw Unicode.</span><span class="sxs-lookup"><span data-stu-id="b4b68-135">In this case to handle international names on the local Intranet, the DNS servers that are used for the Intranet should support Unicode name resolution.</span></span>

- <span data-ttu-id="b4b68-136">włączono obsługę IDN = brak</span><span class="sxs-lookup"><span data-stu-id="b4b68-136">idn enabled = None</span></span>

     <span data-ttu-id="b4b68-137">Ta wartość nie spowoduje konwersji nazw domen Unicode w celu użycia formacie Punycode.</span><span class="sxs-lookup"><span data-stu-id="b4b68-137">This value will not convert any Unicode domain names to use Punycode.</span></span> <span data-ttu-id="b4b68-138">Jest to wartość domyślna, która jest zgodna z zachowaniem .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="b4b68-138">This is the default value which is consistent with the .NET Framework 2.0 behavior.</span></span>

 <span data-ttu-id="b4b68-139">Włączenie IDN spowoduje przekonwertowanie wszystkich etykiet Unicode w nazwie domeny na ich odpowiedniki formacie Punycode.</span><span class="sxs-lookup"><span data-stu-id="b4b68-139">Enabling IDN will convert all Unicode labels in a domain name to their Punycode equivalents.</span></span> <span data-ttu-id="b4b68-140">Nazwy formacie Punycode zawierają tylko znaki ASCII i zawsze zaczynają się od Xn--prefix.</span><span class="sxs-lookup"><span data-stu-id="b4b68-140">Punycode names contain only ASCII characters and always start with the xn-- prefix.</span></span> <span data-ttu-id="b4b68-141">Przyczyną tego problemu jest obsługa istniejących serwerów DNS w Internecie, ponieważ większość serwerów DNS obsługuje tylko znaki ASCII (patrz dokument RFC 3940).</span><span class="sxs-lookup"><span data-stu-id="b4b68-141">The reason for this is to support existing DNS servers on the Internet, since most DNS servers only support ASCII characters (see RFC 3940).</span></span>

### <a name="configuration-files"></a><span data-ttu-id="b4b68-142">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b4b68-142">Configuration files</span></span>

<span data-ttu-id="b4b68-143">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b4b68-143">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>

## <a name="example"></a><span data-ttu-id="b4b68-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4b68-144">Example</span></span>

<span data-ttu-id="b4b68-145">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi IRI analizy i nazw IDN:</span><span class="sxs-lookup"><span data-stu-id="b4b68-145">The following example shows a configuration used by the <xref:System.Uri> class to support IRI parsing and IDN names:</span></span>

```xml
<configuration>
  <uri>
    <idn enabled="All" />
    <iriParsing enabled="true" />
  </uri>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b4b68-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4b68-146">See also</span></span>

- <xref:System.Configuration.IdnElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [<span data-ttu-id="b4b68-147">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b4b68-147">Network Settings Schema</span></span>](index.md)
