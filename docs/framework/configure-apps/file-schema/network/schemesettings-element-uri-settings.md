---
title: "&lt;schemeSettings&gt; elementu (ustawienia identyfikatorów Uri)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 19bcb64beb7b022d20bbde1210ae6d844690d891
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ltschemesettingsgt-element-uri-settings"></a><span data-ttu-id="4df5c-102">&lt;schemeSettings&gt; elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="4df5c-102">&lt;schemeSettings&gt; Element (Uri Settings)</span></span>
<span data-ttu-id="4df5c-103">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="4df5c-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="4df5c-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="4df5c-104">\<configuration></span></span>  
<span data-ttu-id="4df5c-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="4df5c-105">\<uri></span></span>  
<span data-ttu-id="4df5c-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="4df5c-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4df5c-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="4df5c-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4df5c-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="4df5c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4df5c-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="4df5c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4df5c-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="4df5c-110">Attributes</span></span>  
 <span data-ttu-id="4df5c-111">Brak</span><span class="sxs-lookup"><span data-stu-id="4df5c-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4df5c-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="4df5c-112">Child Elements</span></span>  
  
|<span data-ttu-id="4df5c-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="4df5c-113">**Element**</span></span>|<span data-ttu-id="4df5c-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4df5c-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4df5c-115">add</span><span class="sxs-lookup"><span data-stu-id="4df5c-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4df5c-116">Dodaje ustawienia schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="4df5c-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="4df5c-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="4df5c-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4df5c-118">Usuwa wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="4df5c-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="4df5c-119">remove</span><span class="sxs-lookup"><span data-stu-id="4df5c-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="4df5c-120">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="4df5c-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4df5c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="4df5c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4df5c-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="4df5c-122">**Element**</span></span>|<span data-ttu-id="4df5c-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="4df5c-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4df5c-124">Identyfikator URI</span><span class="sxs-lookup"><span data-stu-id="4df5c-124">uri</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|<span data-ttu-id="4df5c-125">Zawiera ustawienia, które określają, jak programu .NET Framework obsługuje adresy URL wyrazić przy użyciu uniform resource identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="4df5c-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4df5c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4df5c-126">Remarks</span></span>  
 <span data-ttu-id="4df5c-127">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un specjalne klasy zakodowane ogranicznik ścieżki przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4df5c-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="4df5c-128">To zostało zaimplementowane jako mechanizm zabezpieczenia przed atakami podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="4df5c-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4df5c-129">Jeśli ten identyfikator URI jest przekazywane do modułów nie obsługuje procent zakodowane znaków prawidłowo, może spowodować następujące polecenie, które było wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="4df5c-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="4df5c-130">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasy pierwszy ogranicznik ścieżki un specjalne, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="4df5c-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="4df5c-131">Wynik przekazywanie złośliwego adres URL powyżej, aby <xref:System.Uri?displayProperty=nameWithType> klasy konstruktora powoduje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="4df5c-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="4df5c-132">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowanego un ucieczki ograniczniki przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="4df5c-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="4df5c-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="4df5c-133">Configuration Files</span></span>  
 <span data-ttu-id="4df5c-134">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4df5c-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4df5c-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="4df5c-135">Example</span></span>  
 <span data-ttu-id="4df5c-136">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy do obsługi nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="4df5c-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="4df5c-137">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="4df5c-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="4df5c-138">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4df5c-138">Namespace</span></span>|<span data-ttu-id="4df5c-139">System</span><span class="sxs-lookup"><span data-stu-id="4df5c-139">System</span></span>|  
|<span data-ttu-id="4df5c-140">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="4df5c-140">Schema Name</span></span>||  
|<span data-ttu-id="4df5c-141">Sprawdzanie poprawności pliku</span><span class="sxs-lookup"><span data-stu-id="4df5c-141">Validation File</span></span>||  
|<span data-ttu-id="4df5c-142">Może być pusta</span><span class="sxs-lookup"><span data-stu-id="4df5c-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="4df5c-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4df5c-143">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="4df5c-144">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="4df5c-144">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
