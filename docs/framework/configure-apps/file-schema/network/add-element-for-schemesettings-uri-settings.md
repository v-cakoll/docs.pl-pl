---
title: '&lt;Dodaj&gt; Element dla schemeSettings (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9cca5e35bfc0aef448d2d515f5ac55ed9e2e2258
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206206"
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="71818-102">&lt;Dodaj&gt; Element dla schemeSettings (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="71818-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="71818-103">Dodaje ustawienia schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="71818-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="71818-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="71818-104">\<configuration></span></span>  
<span data-ttu-id="71818-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="71818-105">\<uri></span></span>  
<span data-ttu-id="71818-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="71818-106">\<schemeSettings></span></span>  
<span data-ttu-id="71818-107">\<add></span><span class="sxs-lookup"><span data-stu-id="71818-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71818-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="71818-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71818-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="71818-109">Attributes and Elements</span></span>  
 <span data-ttu-id="71818-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71818-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71818-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="71818-111">Attributes</span></span>  
  
|<span data-ttu-id="71818-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="71818-112">Attribute</span></span>|<span data-ttu-id="71818-113">Opis</span><span class="sxs-lookup"><span data-stu-id="71818-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71818-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="71818-114">name</span></span>|<span data-ttu-id="71818-115">Nazwa schematu, dla której to ustawienie ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="71818-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="71818-116">Tylko obsługiwane wartości to nazwa = "http" i nazwie = "https".</span><span class="sxs-lookup"><span data-stu-id="71818-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="71818-117">{Atrybut name} Atrybut</span><span class="sxs-lookup"><span data-stu-id="71818-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="71818-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="71818-118">Value</span></span>|<span data-ttu-id="71818-119">Opis</span><span class="sxs-lookup"><span data-stu-id="71818-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="71818-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="71818-120">genericUriParserOptions</span></span>|<span data-ttu-id="71818-121">Opcji analizatora składni dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="71818-121">The parser options for this scheme.</span></span> <span data-ttu-id="71818-122">Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="71818-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71818-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="71818-123">Child Elements</span></span>  
 <span data-ttu-id="71818-124">Brak</span><span class="sxs-lookup"><span data-stu-id="71818-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71818-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="71818-125">Parent Elements</span></span>  
  
|<span data-ttu-id="71818-126">Element</span><span class="sxs-lookup"><span data-stu-id="71818-126">Element</span></span>|<span data-ttu-id="71818-127">Opis</span><span class="sxs-lookup"><span data-stu-id="71818-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71818-128">\<schemeSettings >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="71818-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="71818-129">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="71818-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71818-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="71818-130">Remarks</span></span>  
 <span data-ttu-id="71818-131">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un wyprowadza klasy zakodowane ograniczniki ścieżka przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="71818-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="71818-132">Było to wdrożone jako mechanizm zabezpieczeń przed atakami, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="71818-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="71818-133">Jeśli ten identyfikator URI zostanie przekazany do modułów braku obsługi procent zakodowane znaków prawidłowo, może to spowodować następujące polecenie, które są wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="71818-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="71818-134">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> pierwszy ograniczniki ścieżki un wyprowadza klasy, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="71818-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="71818-135">Wynik przekazania złośliwy adres URL powyżej <xref:System.Uri?displayProperty=nameWithType> klasy Konstruktor skutkuje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="71818-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="71818-136">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowany un ucieczki ograniczniki za pomocą opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="71818-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="71818-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="71818-137">Configuration Files</span></span>  
 <span data-ttu-id="71818-138">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="71818-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="71818-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="71818-139">Example</span></span>  
 <span data-ttu-id="71818-140">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy do obsługi nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="71818-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71818-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="71818-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="71818-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="71818-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
