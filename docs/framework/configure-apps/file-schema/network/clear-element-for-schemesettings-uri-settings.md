---
title: '&lt;Wyczyść&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)'
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 32c7a9e07b48536584f7ca5588226fb4479bacb5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742526"
---
# <a name="ltcleargt-element-for-schemesettings-uri-settings"></a><span data-ttu-id="dd49e-102">&lt;Wyczyść&gt; elementu schemeSettings (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="dd49e-102">&lt;clear&gt; Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="dd49e-103">Usuwa wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="dd49e-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="dd49e-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="dd49e-104">\<configuration></span></span>  
<span data-ttu-id="dd49e-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="dd49e-105">\<uri></span></span>  
<span data-ttu-id="dd49e-106">\<schemeSettings ></span><span class="sxs-lookup"><span data-stu-id="dd49e-106">\<schemeSettings></span></span>  
<span data-ttu-id="dd49e-107">\<Wyczyść ></span><span class="sxs-lookup"><span data-stu-id="dd49e-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd49e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd49e-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd49e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="dd49e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dd49e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="dd49e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd49e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="dd49e-111">Attributes</span></span>  
 <span data-ttu-id="dd49e-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="dd49e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dd49e-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="dd49e-113">Child Elements</span></span>  
 <span data-ttu-id="dd49e-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="dd49e-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd49e-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="dd49e-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dd49e-116">Element</span><span class="sxs-lookup"><span data-stu-id="dd49e-116">Element</span></span>|<span data-ttu-id="dd49e-117">Opis</span><span class="sxs-lookup"><span data-stu-id="dd49e-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd49e-118">\<schemeSettings > elementu (ustawienia identyfikatorów Uri)</span><span class="sxs-lookup"><span data-stu-id="dd49e-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="dd49e-119">Określa sposób <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="dd49e-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd49e-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dd49e-120">Remarks</span></span>  
 <span data-ttu-id="dd49e-121">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un specjalne klasy zakodowane ogranicznik ścieżki przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="dd49e-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="dd49e-122">To zostało zaimplementowane jako mechanizm zabezpieczenia przed atakami podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="dd49e-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="dd49e-123">Jeśli ten identyfikator URI jest przekazywane do modułów nie obsługuje procent zakodowane znaków prawidłowo, może spowodować następujące polecenie, które było wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="dd49e-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="dd49e-124">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasy pierwszy ogranicznik ścieżki un specjalne, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="dd49e-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="dd49e-125">Wynik przekazywanie złośliwego adres URL powyżej, aby <xref:System.Uri?displayProperty=nameWithType> klasy konstruktora powoduje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="dd49e-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="dd49e-126">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowanego un ucieczki ograniczniki przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="dd49e-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="dd49e-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="dd49e-127">Configuration Files</span></span>  
 <span data-ttu-id="dd49e-128">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="dd49e-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd49e-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="dd49e-129">Example</span></span>  
 <span data-ttu-id="dd49e-130">W poniższym przykładzie przedstawiono konfiguracji używane przez <xref:System.Uri> klasy, która usuwa wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowanie procent, kodowane ścieżki ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="dd49e-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="dd49e-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd49e-131">See Also</span></span>  
 <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>  
 <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection?displayProperty=nameWithType>  
 <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>  
 <xref:System.GenericUriParserOptions?displayProperty=nameWithType>  
 <xref:System.Uri?displayProperty=nameWithType>  
 [<span data-ttu-id="dd49e-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="dd49e-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
