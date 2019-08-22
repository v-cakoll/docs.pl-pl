---
title: <schemeSettings>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: 46012b15d41422fb3357e57438e320136809ef41
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664009"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="43ded-102">\<schemeSettings >, element (ustawienia identyfikatora URI)</span><span class="sxs-lookup"><span data-stu-id="43ded-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="43ded-103">Określa, w <xref:System.Uri> jaki sposób będzie analizowana dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="43ded-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
 <span data-ttu-id="43ded-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43ded-104">\<configuration></span></span>  
<span data-ttu-id="43ded-105">\<> identyfikatora URI</span><span class="sxs-lookup"><span data-stu-id="43ded-105">\<uri></span></span>  
<span data-ttu-id="43ded-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="43ded-106">\<schemeSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ded-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="43ded-107">Syntax</span></span>  
  
```xml  
<schemeSettings>   
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43ded-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="43ded-108">Attributes and Elements</span></span>  
 <span data-ttu-id="43ded-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="43ded-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43ded-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="43ded-110">Attributes</span></span>  
 <span data-ttu-id="43ded-111">Brak</span><span class="sxs-lookup"><span data-stu-id="43ded-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="43ded-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="43ded-112">Child Elements</span></span>  
  
|<span data-ttu-id="43ded-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="43ded-113">**Element**</span></span>|<span data-ttu-id="43ded-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="43ded-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43ded-115">add</span><span class="sxs-lookup"><span data-stu-id="43ded-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="43ded-116">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="43ded-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="43ded-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="43ded-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="43ded-118">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="43ded-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="43ded-119">remove</span><span class="sxs-lookup"><span data-stu-id="43ded-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="43ded-120">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="43ded-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="43ded-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="43ded-121">Parent Elements</span></span>  
  
|<span data-ttu-id="43ded-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="43ded-122">**Element**</span></span>|<span data-ttu-id="43ded-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="43ded-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="43ded-124">uri</span><span class="sxs-lookup"><span data-stu-id="43ded-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="43ded-125">Zawiera ustawienia, które określają, w jaki sposób .NET Framework obsługuje adresy sieci Web wyrażone przy użyciu Uniform Resource Identifier (URI).</span><span class="sxs-lookup"><span data-stu-id="43ded-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43ded-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43ded-126">Remarks</span></span>  
 <span data-ttu-id="43ded-127">Domyślnie <xref:System.Uri?displayProperty=nameWithType> Klasa cofa ograniczniki ścieżki kodowanej procentowo przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="43ded-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="43ded-128">Ta implementacja została zaimplementowana jako mechanizm zabezpieczeń przed atakami podobnymi do następujących:</span><span class="sxs-lookup"><span data-stu-id="43ded-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="43ded-129">Jeśli ten identyfikator URI zostanie przesłany do modułów, które nie obsługują poprawnie znaków zakodowanych procentowo, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="43ded-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="43ded-130">Z <xref:System.Uri?displayProperty=nameWithType> tego powodu Klasa najpierw cofa ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="43ded-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="43ded-131">Wynikiem przekazania złośliwego adresu URL powyżej do <xref:System.Uri?displayProperty=nameWithType> konstruktora klasy są następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="43ded-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="43ded-132">To zachowanie domyślne można zmodyfikować, aby nie wycofać ograniczników ścieżki zakodowanej procentowo przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="43ded-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="43ded-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="43ded-133">Configuration Files</span></span>  
 <span data-ttu-id="43ded-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="43ded-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43ded-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="43ded-135">Example</span></span>  
 <span data-ttu-id="43ded-136">W poniższym przykładzie przedstawiono konfigurację używaną przez <xref:System.Uri> klasę do obsługi nieprawidłowych ograniczników ścieżki w kodzie procentowym dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="43ded-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="43ded-137">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="43ded-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="43ded-138">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="43ded-138">Namespace</span></span>|<span data-ttu-id="43ded-139">System</span><span class="sxs-lookup"><span data-stu-id="43ded-139">System</span></span>|  
|<span data-ttu-id="43ded-140">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="43ded-140">Schema Name</span></span>||  
|<span data-ttu-id="43ded-141">Plik walidacji</span><span class="sxs-lookup"><span data-stu-id="43ded-141">Validation File</span></span>||  
|<span data-ttu-id="43ded-142">Może być puste</span><span class="sxs-lookup"><span data-stu-id="43ded-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="43ded-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43ded-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="43ded-144">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="43ded-144">Network Settings Schema</span></span>](index.md)
