---
title: <remove>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 4095ba51-de20-4f87-b562-018abe422c91
ms.openlocfilehash: 0dc8c6111157ba1f23d4a0449bee8f6626027e23
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697859"
---
# <a name="remove-element-for-schemesettings-uri-settings"></a><span data-ttu-id="42c9f-102">\<remove > elementu schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="42c9f-102">\<remove> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="42c9f-103">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="42c9f-103">Removes a scheme setting for a scheme name.</span></span>  
  
[<span data-ttu-id="42c9f-104"> **@no__t — 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="42c9f-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="42c9f-105">&nbsp; @ no__t-1[ **\<uri >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="42c9f-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="42c9f-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<schemeSettings >** ](schemesettings-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="42c9f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<schemeSettings>**](schemesettings-element-uri-settings.md)</span></span>  
<span data-ttu-id="42c9f-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<remove >**</span><span class="sxs-lookup"><span data-stu-id="42c9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c9f-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="42c9f-108">Syntax</span></span>  
  
```xml  
<remove
  name="http|https"
/>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42c9f-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="42c9f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="42c9f-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="42c9f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42c9f-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="42c9f-111">Attributes</span></span>  
  
|<span data-ttu-id="42c9f-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="42c9f-112">Attribute</span></span>|<span data-ttu-id="42c9f-113">Opis</span><span class="sxs-lookup"><span data-stu-id="42c9f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="42c9f-114">nazwa</span><span class="sxs-lookup"><span data-stu-id="42c9f-114">name</span></span>|<span data-ttu-id="42c9f-115">Nazwa schematu, dla którego jest stosowane to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="42c9f-115">The scheme name for which this setting applies.</span></span> <span data-ttu-id="42c9f-116">Jedyne obsługiwane wartości to Name = "http" i Name = "https".</span><span class="sxs-lookup"><span data-stu-id="42c9f-116">The only supported values are name="http" and name="https".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42c9f-117">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="42c9f-117">Child Elements</span></span>  
 <span data-ttu-id="42c9f-118">Brak.</span><span class="sxs-lookup"><span data-stu-id="42c9f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42c9f-119">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="42c9f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="42c9f-120">Element</span><span class="sxs-lookup"><span data-stu-id="42c9f-120">Element</span></span>|<span data-ttu-id="42c9f-121">Opis</span><span class="sxs-lookup"><span data-stu-id="42c9f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="42c9f-122">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="42c9f-122">\<schemeSettings> Element (Uri Settings)</span></span>](schemesettings-element-uri-settings.md)|<span data-ttu-id="42c9f-123">Określa sposób, w jaki <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="42c9f-123">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42c9f-124">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42c9f-124">Remarks</span></span>  
 <span data-ttu-id="42c9f-125">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="42c9f-125">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="42c9f-126">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="42c9f-126">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="42c9f-127">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="42c9f-127">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="42c9f-128">Z tego powodu Klasa <xref:System.Uri?displayProperty=nameWithType> najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="42c9f-128">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="42c9f-129">Wynikiem przekazania złośliwego adresu URL powyżej do konstruktora klasy <xref:System.Uri?displayProperty=nameWithType> skutkuje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="42c9f-129">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="42c9f-130">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="42c9f-130">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="42c9f-131">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="42c9f-131">Configuration Files</span></span>  
 <span data-ttu-id="42c9f-132">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="42c9f-132">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c9f-133">Przykład</span><span class="sxs-lookup"><span data-stu-id="42c9f-133">Example</span></span>  
 <span data-ttu-id="42c9f-134">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri>, która usuwa wszystkie ustawienia schematu dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="42c9f-134">The following example shows a configuration used by the <xref:System.Uri> class that removes any scheme settings for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <remove name="http"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="42c9f-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="42c9f-135">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="42c9f-136">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="42c9f-136">Network Settings Schema</span></span>](index.md)
