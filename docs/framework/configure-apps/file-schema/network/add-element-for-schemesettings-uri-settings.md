---
title: <add>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087718"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="984f7-102">\<dodać elementu > dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="984f7-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="984f7-103">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="984f7-103">Adds a scheme setting for a scheme name.</span></span>  

<span data-ttu-id="984f7-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="984f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="984f7-105">&nbsp;&nbsp;[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="984f7-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="984f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="984f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="984f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**</span><span class="sxs-lookup"><span data-stu-id="984f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>

## <a name="syntax"></a><span data-ttu-id="984f7-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="984f7-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="984f7-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="984f7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="984f7-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="984f7-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="984f7-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="984f7-111">Attributes</span></span>  
  
|<span data-ttu-id="984f7-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="984f7-112">Attribute</span></span>|<span data-ttu-id="984f7-113">Opis</span><span class="sxs-lookup"><span data-stu-id="984f7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="984f7-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="984f7-114">name</span></span>|<span data-ttu-id="984f7-115">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="984f7-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="984f7-116">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="984f7-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="984f7-117">{Nazwa atrybutu} Przypisane</span><span class="sxs-lookup"><span data-stu-id="984f7-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="984f7-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="984f7-118">Value</span></span>|<span data-ttu-id="984f7-119">Opis</span><span class="sxs-lookup"><span data-stu-id="984f7-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="984f7-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="984f7-120">genericUriParserOptions</span></span>|<span data-ttu-id="984f7-121">Opcje parsera dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="984f7-121">The parser options for this scheme.</span></span> <span data-ttu-id="984f7-122">Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="984f7-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="984f7-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="984f7-123">Child Elements</span></span>  
 <span data-ttu-id="984f7-124">Brak</span><span class="sxs-lookup"><span data-stu-id="984f7-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="984f7-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="984f7-125">Parent Elements</span></span>  
  
|<span data-ttu-id="984f7-126">Element</span><span class="sxs-lookup"><span data-stu-id="984f7-126">Element</span></span>|<span data-ttu-id="984f7-127">Opis</span><span class="sxs-lookup"><span data-stu-id="984f7-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="984f7-128">\<element > schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="984f7-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="984f7-129">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="984f7-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="984f7-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="984f7-130">Remarks</span></span>  
 <span data-ttu-id="984f7-131">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="984f7-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="984f7-132">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="984f7-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="984f7-133">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="984f7-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="984f7-134">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasie najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="984f7-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="984f7-135">W wyniku przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy wyniki mają następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="984f7-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="984f7-136">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="984f7-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="984f7-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="984f7-137">Configuration Files</span></span>  
 <span data-ttu-id="984f7-138">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="984f7-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="984f7-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="984f7-139">Example</span></span>  
 <span data-ttu-id="984f7-140">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="984f7-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="984f7-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="984f7-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="984f7-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="984f7-142">Network Settings Schema</span></span>](index.md)
