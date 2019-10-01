---
title: <add>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: efd52557ea8b617a39e685ff8ad69bab01322a7a
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699594"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="98a6a-102">\<add > elementu schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="98a6a-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="98a6a-103">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="98a6a-103">Adds a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="98a6a-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="98a6a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="98a6a-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98a6a-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="98a6a-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98a6a-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="98a6a-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="98a6a-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a6a-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="98a6a-108">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98a6a-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="98a6a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="98a6a-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="98a6a-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98a6a-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="98a6a-111">Attributes</span></span>  
  
|<span data-ttu-id="98a6a-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="98a6a-112">Attribute</span></span>|<span data-ttu-id="98a6a-113">Opis</span><span class="sxs-lookup"><span data-stu-id="98a6a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98a6a-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="98a6a-114">name</span></span>|<span data-ttu-id="98a6a-115">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="98a6a-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="98a6a-116">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="98a6a-116">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="98a6a-117">{Nazwa atrybutu} Przypisane</span><span class="sxs-lookup"><span data-stu-id="98a6a-117">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="98a6a-118">Wartość</span><span class="sxs-lookup"><span data-stu-id="98a6a-118">Value</span></span>|<span data-ttu-id="98a6a-119">Opis</span><span class="sxs-lookup"><span data-stu-id="98a6a-119">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="98a6a-120">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="98a6a-120">genericUriParserOptions</span></span>|<span data-ttu-id="98a6a-121">Opcje parsera dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="98a6a-121">The parser options for this scheme.</span></span> <span data-ttu-id="98a6a-122">Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="98a6a-122">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98a6a-123">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="98a6a-123">Child Elements</span></span>  
 <span data-ttu-id="98a6a-124">Brak</span><span class="sxs-lookup"><span data-stu-id="98a6a-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98a6a-125">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="98a6a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="98a6a-126">Element</span><span class="sxs-lookup"><span data-stu-id="98a6a-126">Element</span></span>|<span data-ttu-id="98a6a-127">Opis</span><span class="sxs-lookup"><span data-stu-id="98a6a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98a6a-128">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="98a6a-128">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="98a6a-129">Określa sposób, w jaki <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="98a6a-129">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98a6a-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98a6a-130">Remarks</span></span>  
 <span data-ttu-id="98a6a-131">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="98a6a-131">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="98a6a-132">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="98a6a-132">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="98a6a-133">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="98a6a-133">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="98a6a-134">Z tego powodu Klasa <xref:System.Uri?displayProperty=nameWithType> najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="98a6a-134">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="98a6a-135">Wynikiem przekazania złośliwego adresu URL powyżej do konstruktora klasy <xref:System.Uri?displayProperty=nameWithType> skutkuje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="98a6a-135">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="98a6a-136">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="98a6a-136">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="98a6a-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="98a6a-137">Configuration Files</span></span>  
 <span data-ttu-id="98a6a-138">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="98a6a-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98a6a-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="98a6a-139">Example</span></span>  
 <span data-ttu-id="98a6a-140">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="98a6a-140">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="98a6a-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98a6a-141">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="98a6a-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="98a6a-142">Network Settings Schema</span></span>](index.md)
