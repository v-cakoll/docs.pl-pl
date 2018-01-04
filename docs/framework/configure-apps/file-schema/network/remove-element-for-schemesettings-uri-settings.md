---
title: "&lt;Usuń&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ab053937587d9cfd9353fe53fa759e58859e3da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="518ba-102">&lt;Usuń&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="518ba-102">&lt;remove&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="518ba-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="518ba-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="518ba-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="518ba-104">\<configuration></span></span>  
<span data-ttu-id="518ba-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="518ba-105">\<uri></span></span>  
<span data-ttu-id="518ba-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="518ba-106">\<schemeSettings></span></span>  
<span data-ttu-id="518ba-107">\<Usuń ></span><span class="sxs-lookup"><span data-stu-id="518ba-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="518ba-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="518ba-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="518ba-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="518ba-109">Attributes and Elements</span></span>  
 <span data-ttu-id="518ba-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="518ba-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="518ba-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="518ba-111">Attributes</span></span>  
  
|<span data-ttu-id="518ba-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="518ba-112">Attribute</span></span>|<span data-ttu-id="518ba-113">Opis</span><span class="sxs-lookup"><span data-stu-id="518ba-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="518ba-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="518ba-114">name</span></span>|<span data-ttu-id="518ba-115">Nazwa schematu, którego dotyczy to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="518ba-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="518ba-116">Obsługiwane są tylko wartości name = "http" i nazwie = "https".</span><span class="sxs-lookup"><span data-stu-id="518ba-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="518ba-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="518ba-117">Child Elements</span></span>  
 <span data-ttu-id="518ba-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="518ba-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="518ba-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="518ba-119">Parent Elements</span></span>  
  
|<span data-ttu-id="518ba-120">Element</span><span class="sxs-lookup"><span data-stu-id="518ba-120">Element</span></span>|<span data-ttu-id="518ba-121">Opis</span><span class="sxs-lookup"><span data-stu-id="518ba-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="518ba-122">\<schemeSettings > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="518ba-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="518ba-123">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="518ba-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="518ba-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="518ba-124">Remarks</span></span>  
 <span data-ttu-id="518ba-125">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un specjalne klasy zakodowane ogranicznik ścieżki przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="518ba-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="518ba-126">To zostało zaimplementowane jako mechanizm zabezpieczenia przed atakami podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="518ba-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="518ba-127">Jeśli ten identyfikator URI jest przekazywane do modułów nie obsługuje procent zakodowane znaków prawidłowo, może spowodować następujące polecenie, które było wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="518ba-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="518ba-128">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasy pierwszy ogranicznik ścieżki un specjalne, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="518ba-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="518ba-129">Wynik przekazywanie złośliwego adres URL powyżej, aby <xref:System.Uri?displayProperty=nameWithType> klasy konstruktora powoduje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="518ba-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="518ba-130">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowanego un ucieczki ograniczniki przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="518ba-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="518ba-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="518ba-131">Configuration Files</span></span>  
 <span data-ttu-id="518ba-132">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="518ba-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="518ba-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="518ba-133">Example</span></span>  
 <span data-ttu-id="518ba-134">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy, która powoduje usunięcie wszystkich ustawień schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="518ba-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="518ba-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="518ba-135">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="518ba-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="518ba-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
