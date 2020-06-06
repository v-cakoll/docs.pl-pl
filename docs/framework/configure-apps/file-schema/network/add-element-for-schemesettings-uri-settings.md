---
title: <add>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: ed40098e8d4c2d1298771e67a618b8d04f59c912
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087718"
---
# <a name="add-element-for-schemesettings-uri-settings"></a><span data-ttu-id="6b184-102">\<add>, element dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="6b184-102">\<add> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="6b184-103">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="6b184-103">Adds a scheme setting for a scheme name.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="6b184-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b184-104">Syntax</span></span>  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b184-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="6b184-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6b184-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="6b184-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b184-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="6b184-107">Attributes</span></span>  
  
|<span data-ttu-id="6b184-108">Atrybut</span><span class="sxs-lookup"><span data-stu-id="6b184-108">Attribute</span></span>|<span data-ttu-id="6b184-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6b184-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b184-110">name</span><span class="sxs-lookup"><span data-stu-id="6b184-110">name</span></span>|<span data-ttu-id="6b184-111">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="6b184-111">The scheme name for which this setting applies.</span></span> <span data-ttu-id="6b184-112">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="6b184-112">The only supported values are name="http" and name="https".</span></span>|  
  
## <a name="attribute-name-attribute"></a><span data-ttu-id="6b184-113">{Nazwa atrybutu} Przypisane</span><span class="sxs-lookup"><span data-stu-id="6b184-113">{Attribute name} Attribute</span></span>  
  
|<span data-ttu-id="6b184-114">Wartość</span><span class="sxs-lookup"><span data-stu-id="6b184-114">Value</span></span>|<span data-ttu-id="6b184-115">Opis</span><span class="sxs-lookup"><span data-stu-id="6b184-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b184-116">genericUriParserOptions</span><span class="sxs-lookup"><span data-stu-id="6b184-116">genericUriParserOptions</span></span>|<span data-ttu-id="6b184-117">Opcje parsera dla tego schematu.</span><span class="sxs-lookup"><span data-stu-id="6b184-117">The parser options for this scheme.</span></span> <span data-ttu-id="6b184-118">Jedyna obsługiwana wartość to genericUriParserOptions = "DontUnescapePathDotsAndSlashes".</span><span class="sxs-lookup"><span data-stu-id="6b184-118">The only supported value is genericUriParserOptions= "DontUnescapePathDotsAndSlashes".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b184-119">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6b184-119">Child Elements</span></span>  
 <span data-ttu-id="6b184-120">Brak</span><span class="sxs-lookup"><span data-stu-id="6b184-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b184-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="6b184-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6b184-122">Element</span><span class="sxs-lookup"><span data-stu-id="6b184-122">Element</span></span>|<span data-ttu-id="6b184-123">Opis</span><span class="sxs-lookup"><span data-stu-id="6b184-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b184-124">\<schemeSettings>— Element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="6b184-124">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="6b184-125">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="6b184-125">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b184-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b184-126">Remarks</span></span>  
 <span data-ttu-id="6b184-127">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="6b184-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="6b184-128">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="6b184-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6b184-129">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="6b184-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="6b184-130">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="6b184-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="6b184-131">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="6b184-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="6b184-132">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="6b184-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6b184-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6b184-133">Configuration Files</span></span>  
 <span data-ttu-id="6b184-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="6b184-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b184-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="6b184-135">Example</span></span>  
 <span data-ttu-id="6b184-136">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="6b184-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b184-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b184-137">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="6b184-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="6b184-138">Network Settings Schema</span></span>](index.md)
