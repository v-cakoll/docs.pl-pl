---
title: <schemeSettings>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 498aef77a1dfd8cffcac73b704b8d1bb6df5d165
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697771"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="0599b-102">\<element > schemeSettings (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="0599b-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="0599b-103">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="0599b-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="0599b-104"> **> konfiguracji \<** </span><span class="sxs-lookup"><span data-stu-id="0599b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="0599b-105">&nbsp;&nbsp;[ **\<URI >** ](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0599b-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="0599b-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<schemeSettings >**</span><span class="sxs-lookup"><span data-stu-id="0599b-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0599b-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="0599b-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0599b-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="0599b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0599b-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="0599b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0599b-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="0599b-110">Attributes</span></span>  
 <span data-ttu-id="0599b-111">Brak</span><span class="sxs-lookup"><span data-stu-id="0599b-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0599b-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="0599b-112">Child Elements</span></span>  
  
|<span data-ttu-id="0599b-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="0599b-113">**Element**</span></span>|<span data-ttu-id="0599b-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0599b-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0599b-115">add</span><span class="sxs-lookup"><span data-stu-id="0599b-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0599b-116">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="0599b-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="0599b-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="0599b-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0599b-118">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="0599b-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="0599b-119">remove</span><span class="sxs-lookup"><span data-stu-id="0599b-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="0599b-120">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="0599b-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0599b-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="0599b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0599b-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="0599b-122">**Element**</span></span>|<span data-ttu-id="0599b-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="0599b-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0599b-124">uri</span><span class="sxs-lookup"><span data-stu-id="0599b-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="0599b-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="0599b-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0599b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0599b-126">Remarks</span></span>  
 <span data-ttu-id="0599b-127">Domyślnie Klasa <xref:System.Uri?displayProperty=nameWithType> cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="0599b-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="0599b-128">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="0599b-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0599b-129">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="0599b-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="0599b-130">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> klasie najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="0599b-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="0599b-131">W wyniku przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy wyniki mają następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="0599b-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="0599b-132">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="0599b-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0599b-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0599b-133">Configuration Files</span></span>  
 <span data-ttu-id="0599b-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0599b-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0599b-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="0599b-135">Example</span></span>  
 <span data-ttu-id="0599b-136">W poniższym przykładzie przedstawiono konfigurację używaną przez klasę <xref:System.Uri> do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="0599b-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="0599b-137">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="0599b-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="0599b-138">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="0599b-138">Namespace</span></span>|<span data-ttu-id="0599b-139">System</span><span class="sxs-lookup"><span data-stu-id="0599b-139">System</span></span>|  
|<span data-ttu-id="0599b-140">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="0599b-140">Schema Name</span></span>||  
|<span data-ttu-id="0599b-141">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="0599b-141">Validation File</span></span>||  
|<span data-ttu-id="0599b-142">Może być puste</span><span class="sxs-lookup"><span data-stu-id="0599b-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="0599b-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0599b-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="0599b-144">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="0599b-144">Network Settings Schema</span></span>](index.md)
