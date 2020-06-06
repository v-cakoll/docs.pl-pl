---
title: <schemeSettings>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154650"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="2e62c-102">\<schemeSettings>, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="2e62c-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="2e62c-103">Określa, w jaki sposób <xref:System.Uri> będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="2e62c-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="2e62c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e62c-104">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e62c-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2e62c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2e62c-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2e62c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e62c-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2e62c-107">Attributes</span></span>  
 <span data-ttu-id="2e62c-108">Brak</span><span class="sxs-lookup"><span data-stu-id="2e62c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2e62c-109">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2e62c-109">Child Elements</span></span>  
  
|<span data-ttu-id="2e62c-110">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="2e62c-110">**Element**</span></span>|<span data-ttu-id="2e62c-111">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2e62c-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2e62c-112">add</span><span class="sxs-lookup"><span data-stu-id="2e62c-112">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2e62c-113">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="2e62c-113">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="2e62c-114">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="2e62c-114">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2e62c-115">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="2e62c-115">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="2e62c-116">usuwa</span><span class="sxs-lookup"><span data-stu-id="2e62c-116">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="2e62c-117">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="2e62c-117">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2e62c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2e62c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2e62c-119">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="2e62c-119">**Element**</span></span>|<span data-ttu-id="2e62c-120">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2e62c-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2e62c-121">adresu</span><span class="sxs-lookup"><span data-stu-id="2e62c-121">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="2e62c-122">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="2e62c-122">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e62c-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2e62c-123">Remarks</span></span>  
 <span data-ttu-id="2e62c-124">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2e62c-124">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="2e62c-125">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="2e62c-125">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2e62c-126">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="2e62c-126">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="2e62c-127">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="2e62c-127">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="2e62c-128">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="2e62c-128">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="2e62c-129">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="2e62c-129">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2e62c-130">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2e62c-130">Configuration Files</span></span>  
 <span data-ttu-id="2e62c-131">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2e62c-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e62c-132">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e62c-132">Example</span></span>  
 <span data-ttu-id="2e62c-133">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="2e62c-133">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="2e62c-134">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="2e62c-134">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="2e62c-135">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="2e62c-135">Namespace</span></span>|<span data-ttu-id="2e62c-136">System</span><span class="sxs-lookup"><span data-stu-id="2e62c-136">System</span></span>|  
|<span data-ttu-id="2e62c-137">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="2e62c-137">Schema Name</span></span>||  
|<span data-ttu-id="2e62c-138">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="2e62c-138">Validation File</span></span>||  
|<span data-ttu-id="2e62c-139">Może być puste</span><span class="sxs-lookup"><span data-stu-id="2e62c-139">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="2e62c-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e62c-140">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="2e62c-141">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2e62c-141">Network Settings Schema</span></span>](index.md)
