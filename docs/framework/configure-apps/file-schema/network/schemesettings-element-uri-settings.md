---
title: <schemeSettings>, element (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154650"
---
# <a name="schemesettings-element-uri-settings"></a><span data-ttu-id="05627-102">\<schemeSettings> Element (Ustawienia Uri)</span><span class="sxs-lookup"><span data-stu-id="05627-102">\<schemeSettings> Element (Uri Settings)</span></span>
<span data-ttu-id="05627-103">Określa sposób <xref:System.Uri> analizacji dla określonych schematów.</span><span class="sxs-lookup"><span data-stu-id="05627-103">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>  
  
[<span data-ttu-id="05627-104">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="05627-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="05627-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span><span class="sxs-lookup"><span data-stu-id="05627-105">&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)</span></span>  
<span data-ttu-id="05627-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<systemyRozstawy>**</span><span class="sxs-lookup"><span data-stu-id="05627-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<schemeSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05627-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="05627-107">Syntax</span></span>  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05627-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="05627-108">Attributes and Elements</span></span>  
 <span data-ttu-id="05627-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="05627-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05627-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="05627-110">Attributes</span></span>  
 <span data-ttu-id="05627-111">Brak</span><span class="sxs-lookup"><span data-stu-id="05627-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05627-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="05627-112">Child Elements</span></span>  
  
|<span data-ttu-id="05627-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="05627-113">**Element**</span></span>|<span data-ttu-id="05627-114">**Opis**</span><span class="sxs-lookup"><span data-stu-id="05627-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05627-115">Dodaj</span><span class="sxs-lookup"><span data-stu-id="05627-115">add</span></span>](add-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="05627-116">Dodaje ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="05627-116">Adds a scheme setting for a scheme name.</span></span>|  
|[<span data-ttu-id="05627-117">Wyczyść</span><span class="sxs-lookup"><span data-stu-id="05627-117">clear</span></span>](clear-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="05627-118">Czyści wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="05627-118">Clears all existing scheme settings.</span></span>|  
|[<span data-ttu-id="05627-119">Usunąć</span><span class="sxs-lookup"><span data-stu-id="05627-119">remove</span></span>](remove-element-for-schemesettings-uri-settings.md)|<span data-ttu-id="05627-120">Usuwa ustawienie schematu dla nazwy schematu.</span><span class="sxs-lookup"><span data-stu-id="05627-120">Removes a scheme setting for a scheme name.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05627-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="05627-121">Parent Elements</span></span>  
  
|<span data-ttu-id="05627-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="05627-122">**Element**</span></span>|<span data-ttu-id="05627-123">**Opis**</span><span class="sxs-lookup"><span data-stu-id="05627-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05627-124">Identyfikator uri</span><span class="sxs-lookup"><span data-stu-id="05627-124">uri</span></span>](uri-element-uri-settings.md)|<span data-ttu-id="05627-125">Zawiera ustawienia określające sposób obsługi adresów internetowych .NET Framework wyrażonych przy użyciu jednolitych identyfikatorów zasobów (URI).</span><span class="sxs-lookup"><span data-stu-id="05627-125">Contains settings that specify how the .NET Framework handles web addresses expressed using uniform resource identifiers (URIs).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05627-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05627-126">Remarks</span></span>  
 <span data-ttu-id="05627-127">Domyślnie <xref:System.Uri?displayProperty=nameWithType> klasa un-escapes procent zakodowane ograniczniki ścieżki przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="05627-127">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="05627-128">Zostało to zaimplementowane jako mechanizm zabezpieczeń przed atakami, takimi jak następujące:</span><span class="sxs-lookup"><span data-stu-id="05627-128">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="05627-129">Jeśli ten identyfikator URI zostanie przekazany do modułów, które nie obsługują poprawnie procentowych znaków zakodowanych, może to spowodować wykonanie następującego polecenia przez serwer:</span><span class="sxs-lookup"><span data-stu-id="05627-129">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="05627-130">Z tego <xref:System.Uri?displayProperty=nameWithType> powodu klasa najpierw un-escapes ograniczniki ścieżki, a następnie stosuje kompresję ścieżki.</span><span class="sxs-lookup"><span data-stu-id="05627-130">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="05627-131">Wynik przekazania złośliwego adresu <xref:System.Uri?displayProperty=nameWithType> URL powyżej do konstruktora klasy powoduje następujące identyfikatory URI:</span><span class="sxs-lookup"><span data-stu-id="05627-131">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="05627-132">To domyślne zachowanie można zmodyfikować tak, aby nie odkodowywało procentów przy użyciu opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="05627-132">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05627-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="05627-133">Configuration Files</span></span>  
 <span data-ttu-id="05627-134">Ten element może być używany w pliku konfiguracyjnym aplikacji lub pliku konfiguracyjnym komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="05627-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05627-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="05627-135">Example</span></span>  
 <span data-ttu-id="05627-136">Poniższy przykład przedstawia konfigurację <xref:System.Uri> używaną przez klasę do obsługi nie uciekających ograniczników ścieżki zakodowanych w procentach dla schematu http.</span><span class="sxs-lookup"><span data-stu-id="05627-136">The following example shows a configuration used by the <xref:System.Uri> class to support not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="05627-137">Informacje o elementach</span><span class="sxs-lookup"><span data-stu-id="05627-137">Element Information</span></span>  
  
|||
|-|-|  
|<span data-ttu-id="05627-138">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="05627-138">Namespace</span></span>|<span data-ttu-id="05627-139">System</span><span class="sxs-lookup"><span data-stu-id="05627-139">System</span></span>|  
|<span data-ttu-id="05627-140">Nazwa schematu</span><span class="sxs-lookup"><span data-stu-id="05627-140">Schema Name</span></span>||  
|<span data-ttu-id="05627-141">Plik sprawdzania poprawności</span><span class="sxs-lookup"><span data-stu-id="05627-141">Validation File</span></span>||  
|<span data-ttu-id="05627-142">Może być pusty</span><span class="sxs-lookup"><span data-stu-id="05627-142">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="05627-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05627-143">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="05627-144">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="05627-144">Network Settings Schema</span></span>](index.md)
