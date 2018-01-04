---
title: "&lt;Dodaj&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 2d617e78231bd0b9f4e332c4b7fbe58b78598868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ab2bc-102">&lt;Dodaj&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="ab2bc-102">&lt;add&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ab2bc-103">Dodaje ustawienia schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-103">Adds a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="ab2bc-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ab2bc-104">\<configuration></span></span>  
<span data-ttu-id="ab2bc-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="ab2bc-105">\<uri></span></span>  
<span data-ttu-id="ab2bc-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="ab2bc-106">\<schemeSettings></span></span>  
<span data-ttu-id="ab2bc-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="ab2bc-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2bc-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab2bc-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab2bc-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ab2bc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab2bc-110">W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab2bc-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab2bc-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ab2bc-111">Attributes</span></span>  
  
|<span data-ttu-id="ab2bc-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab2bc-112">Attribute</span></span>|<span data-ttu-id="ab2bc-113">Opis</span><span class="sxs-lookup"><span data-stu-id="ab2bc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab2bc-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="ab2bc-114">name</span></span>|<span data-ttu-id="ab2bc-115">Nazwa schematu, którego dotyczy to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="ab2bc-116">Obsługiwane są tylko wartości name = "http" i nazwie = "https".</span><span class="sxs-lookup"><span data-stu-id="ab2bc-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="ab2bc-117">{Nazwa atrybutu} Atrybut</span><span class="sxs-lookup"><span data-stu-id="ab2bc-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="ab2bc-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="ab2bc-118">Value</span></span>|<span data-ttu-id="ab2bc-119">Opis</span><span class="sxs-lookup"><span data-stu-id="ab2bc-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ab2bc-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="ab2bc-120">genericUriParserOptions</span></span>|<span data-ttu-id="ab2bc-121">Opcji analizatora składni dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-121">The parser options for this scheme.</span></span> <span data-ttu-id="ab2bc-122">Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="ab2bc-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab2bc-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ab2bc-123">Child Elements</span></span>  
 <span data-ttu-id="ab2bc-124">Brak</span><span class="sxs-lookup"><span data-stu-id="ab2bc-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab2bc-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ab2bc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="ab2bc-126">Element</span><span class="sxs-lookup"><span data-stu-id="ab2bc-126">Element</span></span>|<span data-ttu-id="ab2bc-127">Opis</span><span class="sxs-lookup"><span data-stu-id="ab2bc-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab2bc-128">\<schemeSettings > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="ab2bc-128">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="ab2bc-129">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab2bc-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab2bc-130">Remarks</span></span>  
 <span data-ttu-id="ab2bc-131">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un specjalne klasy zakodowane ogranicznik ścieżki przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ab2bc-132">To zostało zaimplementowane jako mechanizm zabezpieczenia przed atakami podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="ab2bc-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ab2bc-133">Jeśli ten identyfikator URI jest przekazywane do modułów nie obsługuje procent zakodowane znaków prawidłowo, może spowodować następujące polecenie, które było wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="ab2bc-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ab2bc-134">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasy pierwszy ogranicznik ścieżki un specjalne, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ab2bc-135">Wynik przekazywanie złośliwego adres URL powyżej, aby <xref:System.Uri?displayProperty=nameWithType> klasy konstruktora powoduje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="ab2bc-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ab2bc-136">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowanego un ucieczki ograniczniki przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ab2bc-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ab2bc-137">Configuration Files</span></span>  
 <span data-ttu-id="ab2bc-138">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ab2bc-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab2bc-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="ab2bc-139">Example</span></span>  
 <span data-ttu-id="ab2bc-140">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="ab2bc-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ab2bc-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab2bc-141">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="ab2bc-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ab2bc-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
