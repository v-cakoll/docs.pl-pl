---
title: <remove>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089146"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="58fb9-102">\<remove>, element dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="58fb9-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="58fb9-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="58fb9-103">Removes a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="58fb9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58fb9-104">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58fb9-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="58fb9-105">Attributes and Elements</span></span>  
 <span data-ttu-id="58fb9-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="58fb9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58fb9-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="58fb9-107">Attributes</span></span>  
  
|<span data-ttu-id="58fb9-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="58fb9-108">Attribute</span></span>|<span data-ttu-id="58fb9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="58fb9-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58fb9-110">name</span><span class="sxs-lookup"><span data-stu-id="58fb9-110">name</span></span>|<span data-ttu-id="58fb9-111">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="58fb9-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="58fb9-112">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="58fb9-112">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58fb9-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="58fb9-113">Child Elements</span></span>  
 <span data-ttu-id="58fb9-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="58fb9-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58fb9-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="58fb9-115">Parent Elements</span></span>  
  
|<span data-ttu-id="58fb9-116">Element</span><span class="sxs-lookup"><span data-stu-id="58fb9-116">Element</span></span>|<span data-ttu-id="58fb9-117">Opis</span><span class="sxs-lookup"><span data-stu-id="58fb9-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58fb9-118">\<schemeSettings>— Element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="58fb9-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="58fb9-119">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="58fb9-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58fb9-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58fb9-120">Remarks</span></span>  
 <span data-ttu-id="58fb9-121">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="58fb9-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="58fb9-122">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="58fb9-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="58fb9-123">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="58fb9-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="58fb9-124">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="58fb9-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="58fb9-125">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="58fb9-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="58fb9-126">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="58fb9-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="58fb9-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="58fb9-127">Configuration Files</span></span>  
 <span data-ttu-id="58fb9-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="58fb9-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58fb9-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="58fb9-129">Example</span></span>  
 <span data-ttu-id="58fb9-130">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę, która usuwa wszystkie ustawienia schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="58fb9-130">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="58fb9-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="58fb9-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="58fb9-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="58fb9-132">Network Settings Schema</span></span>](index.md)
