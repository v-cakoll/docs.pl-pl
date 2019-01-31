---
title: <remove> — Element dla schemeSettings (Ustawienia identyfikatora Uri)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: fd137c86d7373947f57364c13eb3875cba46b269
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55262646"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="54423-102">\<Usuń >, Element dla schemeSettings (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="54423-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="54423-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="54423-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="54423-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="54423-104">\<configuration></span></span>  
<span data-ttu-id="54423-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="54423-105">\<uri></span></span>  
<span data-ttu-id="54423-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="54423-106">\<schemeSettings></span></span>  
<span data-ttu-id="54423-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="54423-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54423-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="54423-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54423-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="54423-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54423-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="54423-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54423-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="54423-111">Attributes</span></span>  
  
|<span data-ttu-id="54423-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="54423-112">Attribute</span></span>|<span data-ttu-id="54423-113">Opis</span><span class="sxs-lookup"><span data-stu-id="54423-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54423-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="54423-114">name</span></span>|<span data-ttu-id="54423-115">Nazwa schematu, dla której to ustawienie ma zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="54423-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="54423-116">Tylko obsługiwane wartości to nazwa = "http" i nazwie = "https".</span><span class="sxs-lookup"><span data-stu-id="54423-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54423-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="54423-117">Child Elements</span></span>  
 <span data-ttu-id="54423-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="54423-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54423-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="54423-119">Parent Elements</span></span>  
  
|<span data-ttu-id="54423-120">Element</span><span class="sxs-lookup"><span data-stu-id="54423-120">Element</span></span>|<span data-ttu-id="54423-121">Opis</span><span class="sxs-lookup"><span data-stu-id="54423-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54423-122">\<schemeSettings >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="54423-122">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="54423-123">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="54423-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54423-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54423-124">Remarks</span></span>  
 <span data-ttu-id="54423-125">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un wyprowadza klasy zakodowane ograniczniki ścieżka przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="54423-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="54423-126">Było to wdrożone jako mechanizm zabezpieczeń przed atakami, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="54423-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="54423-127">Jeśli ten identyfikator URI zostanie przekazany do modułów braku obsługi procent zakodowane znaków prawidłowo, może to spowodować następujące polecenie, które są wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="54423-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="54423-128">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> pierwszy ograniczniki ścieżki un wyprowadza klasy, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="54423-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="54423-129">Wynik przekazania złośliwy adres URL powyżej <xref:System.Uri?displayProperty=nameWithType> klasy Konstruktor skutkuje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="54423-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="54423-130">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowany un ucieczki ograniczniki za pomocą opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="54423-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="54423-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="54423-131">Configuration Files</span></span>  
 <span data-ttu-id="54423-132">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="54423-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54423-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="54423-133">Example</span></span>  
 <span data-ttu-id="54423-134">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasę, która usuwa wszystkie ustawienia schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="54423-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="54423-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="54423-135">See also</span></span>
- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="54423-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="54423-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
