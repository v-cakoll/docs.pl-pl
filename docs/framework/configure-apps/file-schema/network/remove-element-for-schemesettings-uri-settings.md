---
title: <remove>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 4a891eb8a2fd2d66b6435e2ae774ecd4a157c0f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659220"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="34183-102">\<Usuń element > dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="34183-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="34183-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="34183-103">Removes a scheme setting for a scheme name.</span></span>  
  
 <span data-ttu-id="34183-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="34183-104">\<configuration></span></span>  
<span data-ttu-id="34183-105">\<> identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="34183-105">\<uri></span></span>  
<span data-ttu-id="34183-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="34183-106">\<schemeSettings></span></span>  
<span data-ttu-id="34183-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="34183-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34183-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="34183-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="34183-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="34183-109">Attributes and Elements</span></span>  
 <span data-ttu-id="34183-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="34183-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="34183-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="34183-111">Attributes</span></span>  
  
|<span data-ttu-id="34183-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="34183-112">Attribute</span></span>|<span data-ttu-id="34183-113">Opis</span><span class="sxs-lookup"><span data-stu-id="34183-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="34183-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="34183-114">name</span></span>|<span data-ttu-id="34183-115">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="34183-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="34183-116">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="34183-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="34183-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="34183-117">Child Elements</span></span>  
 <span data-ttu-id="34183-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="34183-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="34183-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="34183-119">Parent Elements</span></span>  
  
|<span data-ttu-id="34183-120">Element</span><span class="sxs-lookup"><span data-stu-id="34183-120">Element</span></span>|<span data-ttu-id="34183-121">Opis</span><span class="sxs-lookup"><span data-stu-id="34183-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="34183-122">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="34183-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="34183-123">Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="34183-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34183-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34183-124">Remarks</span></span>  
 <span data-ttu-id="34183-125">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="34183-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="34183-126">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="34183-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34183-127">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="34183-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="34183-128">Z <xref:System.Uri?displayProperty=nameWithType> tego powodu Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="34183-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="34183-129">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="34183-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="34183-130">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="34183-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="34183-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="34183-131">Configuration Files</span></span>  
 <span data-ttu-id="34183-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="34183-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="34183-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="34183-133">Example</span></span>  
 <span data-ttu-id="34183-134">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę, która usuwa wszystkie ustawienia schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="34183-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="34183-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34183-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="34183-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="34183-136">Network Settings Schema</span></span>](index.md)
