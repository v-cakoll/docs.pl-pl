---
title: <clear>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 51c669aff767948523172aa075677ad3fb6478a2
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664181"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="f27c2-102">\<Wyczyść element > dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="f27c2-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="f27c2-103">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="f27c2-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="f27c2-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f27c2-104">\<configuration></span></span>  
<span data-ttu-id="f27c2-105">\<> identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="f27c2-105">\<uri></span></span>  
<span data-ttu-id="f27c2-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="f27c2-106">\<schemeSettings></span></span>  
<span data-ttu-id="f27c2-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="f27c2-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27c2-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="f27c2-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f27c2-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="f27c2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f27c2-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="f27c2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f27c2-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="f27c2-111">Attributes</span></span>  
 <span data-ttu-id="f27c2-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="f27c2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f27c2-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="f27c2-113">Child Elements</span></span>  
 <span data-ttu-id="f27c2-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="f27c2-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f27c2-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="f27c2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="f27c2-116">Element</span><span class="sxs-lookup"><span data-stu-id="f27c2-116">Element</span></span>|<span data-ttu-id="f27c2-117">Opis</span><span class="sxs-lookup"><span data-stu-id="f27c2-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f27c2-118">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="f27c2-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="f27c2-119">Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="f27c2-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f27c2-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f27c2-120">Remarks</span></span>  
 <span data-ttu-id="f27c2-121">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f27c2-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="f27c2-122">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="f27c2-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f27c2-123">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="f27c2-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="f27c2-124">Z <xref:System.Uri?displayProperty=nameWithType> tego powodu Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="f27c2-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="f27c2-125">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="f27c2-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="f27c2-126">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="f27c2-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f27c2-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f27c2-127">Configuration Files</span></span>  
 <span data-ttu-id="f27c2-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="f27c2-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f27c2-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="f27c2-129">Example</span></span>  
 <span data-ttu-id="f27c2-130">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę, która czyści wszystkie ustawienia schematu, a następnie dodaje obsługę nieprawidłowych ograniczników Path (procentowo) dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="f27c2-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f27c2-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f27c2-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="f27c2-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="f27c2-132">Network Settings Schema</span></span>](index.md)
