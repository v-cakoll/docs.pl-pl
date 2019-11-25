---
title: <clear>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 90035c1c9ccdb8ac888aec84e506ccde41748c9f
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087444"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="b16bd-102">\<Wyczyść element > dla schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="b16bd-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="b16bd-103">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="b16bd-103">Clears all existing scheme settings.</span></span>  

<span data-ttu-id="b16bd-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b16bd-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b16bd-105">&nbsp;&nbsp;[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b16bd-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>\
<span data-ttu-id="b16bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="b16bd-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>\
<span data-ttu-id="b16bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="b16bd-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="b16bd-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="b16bd-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b16bd-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="b16bd-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b16bd-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="b16bd-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b16bd-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="b16bd-111">Attributes</span></span>  
 <span data-ttu-id="b16bd-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="b16bd-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b16bd-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="b16bd-113">Child Elements</span></span>  
 <span data-ttu-id="b16bd-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="b16bd-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b16bd-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="b16bd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b16bd-116">Element</span><span class="sxs-lookup"><span data-stu-id="b16bd-116">Element</span></span>|<span data-ttu-id="b16bd-117">Opis</span><span class="sxs-lookup"><span data-stu-id="b16bd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b16bd-118">\<element > schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="b16bd-118">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="b16bd-119">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="b16bd-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b16bd-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b16bd-120">Remarks</span></span>  
 <span data-ttu-id="b16bd-121">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b16bd-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="b16bd-122">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="b16bd-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b16bd-123">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="b16bd-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="b16bd-124">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasie najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="b16bd-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="b16bd-125">W wyniku przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy wyniki mają następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="b16bd-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="b16bd-126">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="b16bd-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b16bd-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b16bd-127">Configuration Files</span></span>  
 <span data-ttu-id="b16bd-128">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b16bd-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b16bd-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="b16bd-129">Example</span></span>  
 <span data-ttu-id="b16bd-130">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri>, która czyści wszystkie ustawienia schematu, a następnie dodaje obsługę nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="b16bd-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b16bd-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b16bd-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="b16bd-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="b16bd-132">Network Settings Schema</span></span>](index.md)
