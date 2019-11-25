---
title: <remove>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: faf254174527ea74638442a139841eb2365d1e5d
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089146"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="b1a52-102">\<usunąć elementu > dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="b1a52-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="b1a52-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="b1a52-103">Removes a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="b1a52-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b1a52-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1a52-105">&nbsp;&nbsp;[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1a52-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="b1a52-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b1a52-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="b1a52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**</span><span class="sxs-lookup"><span data-stu-id="b1a52-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b1a52-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1a52-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1a52-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b1a52-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1a52-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b1a52-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1a52-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b1a52-111">Attributes</span></span>  
  
|<span data-ttu-id="b1a52-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="b1a52-112">Attribute</span></span>|<span data-ttu-id="b1a52-113">Opis</span><span class="sxs-lookup"><span data-stu-id="b1a52-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1a52-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="b1a52-114">name</span></span>|<span data-ttu-id="b1a52-115">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="b1a52-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="b1a52-116">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="b1a52-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1a52-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b1a52-117">Child Elements</span></span>  
 <span data-ttu-id="b1a52-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="b1a52-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1a52-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b1a52-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b1a52-120">Element</span><span class="sxs-lookup"><span data-stu-id="b1a52-120">Element</span></span>|<span data-ttu-id="b1a52-121">Opis</span><span class="sxs-lookup"><span data-stu-id="b1a52-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1a52-122">\<element > schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="b1a52-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b1a52-123">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="b1a52-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a52-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1a52-124">Remarks</span></span>  
 <span data-ttu-id="b1a52-125">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b1a52-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="b1a52-126">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="b1a52-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b1a52-127">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="b1a52-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="b1a52-128">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasie najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b1a52-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="b1a52-129">W wyniku przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy wyniki mają następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="b1a52-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b1a52-130">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="b1a52-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1a52-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b1a52-131">Configuration Files</span></span>  
 <span data-ttu-id="b1a52-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b1a52-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1a52-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="b1a52-133">Example</span></span>  
 <span data-ttu-id="b1a52-134">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri>, która usuwa wszystkie ustawienia schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="b1a52-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b1a52-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1a52-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="b1a52-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b1a52-136">Network Settings Schema</span></span>](index.md)
