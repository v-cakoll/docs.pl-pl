---
title: <clear>, element dla schemeSettings (ustawienia identyfikatora URI)
ms.date: 03/30/2017
ms.assetid: 65098332-ce61-4542-ab8d-e7dc0257d31f
ms.openlocfilehash: 132506dc15335b738fcdb026f4d31429bc45a228
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674691"
---
# <a name="clear-element-for-schemesettings-uri-settings"></a><span data-ttu-id="ec2d1-102">\<Wyczyść >, Element dla schemeSettings (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="ec2d1-102">\<clear> Element for schemeSettings (Uri Settings)</span></span>
<span data-ttu-id="ec2d1-103">Usuwa wszystkie istniejące ustawienia schematu.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-103">Clears all existing scheme settings.</span></span>  
  
 <span data-ttu-id="ec2d1-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="ec2d1-104">\<configuration></span></span>  
<span data-ttu-id="ec2d1-105">\<Identyfikator URI ></span><span class="sxs-lookup"><span data-stu-id="ec2d1-105">\<uri></span></span>  
<span data-ttu-id="ec2d1-106">\<schemeSettings></span><span class="sxs-lookup"><span data-stu-id="ec2d1-106">\<schemeSettings></span></span>  
<span data-ttu-id="ec2d1-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="ec2d1-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec2d1-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec2d1-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec2d1-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="ec2d1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ec2d1-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec2d1-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="ec2d1-111">Attributes</span></span>  
 <span data-ttu-id="ec2d1-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec2d1-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="ec2d1-113">Child Elements</span></span>  
 <span data-ttu-id="ec2d1-114">Brak.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ec2d1-115">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="ec2d1-115">Parent Elements</span></span>  
  
|<span data-ttu-id="ec2d1-116">Element</span><span class="sxs-lookup"><span data-stu-id="ec2d1-116">Element</span></span>|<span data-ttu-id="ec2d1-117">Opis</span><span class="sxs-lookup"><span data-stu-id="ec2d1-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ec2d1-118">\<schemeSettings >, Element (ustawienia identyfikatora Uri)</span><span class="sxs-lookup"><span data-stu-id="ec2d1-118">\<schemeSettings> Element (Uri Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|<span data-ttu-id="ec2d1-119">Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-119">Specifies how a <xref:System.Uri> will be parsed for specific schemes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec2d1-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec2d1-120">Remarks</span></span>  
 <span data-ttu-id="ec2d1-121">Domyślnie <xref:System.Uri?displayProperty=nameWithType> procent un wyprowadza klasy zakodowane ograniczniki ścieżka przed wykonaniem kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-121">By default, the <xref:System.Uri?displayProperty=nameWithType> class un-escapes percent encoded path delimiters before executing path compression.</span></span> <span data-ttu-id="ec2d1-122">Było to wdrożone jako mechanizm zabezpieczeń przed atakami, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="ec2d1-122">This was implemented as a security mechanism against attacks like the following:</span></span>  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ec2d1-123">Jeśli ten identyfikator URI zostanie przekazany do modułów braku obsługi procent zakodowane znaków prawidłowo, może to spowodować następujące polecenie, które są wykonywane przez serwer:</span><span class="sxs-lookup"><span data-stu-id="ec2d1-123">If this URI gets passed down to modules not handling percent encoded characters correctly, it could result in the following command being executed by the server:</span></span>  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 <span data-ttu-id="ec2d1-124">Z tego powodu <xref:System.Uri?displayProperty=nameWithType> pierwszy ograniczniki ścieżki un wyprowadza klasy, a następnie stosuje kompresji ścieżki.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-124">For this reason, <xref:System.Uri?displayProperty=nameWithType> class first un-escapes path delimiters and then applies path compression.</span></span> <span data-ttu-id="ec2d1-125">Wynik przekazania złośliwy adres URL powyżej <xref:System.Uri?displayProperty=nameWithType> klasy Konstruktor skutkuje następujący identyfikator URI:</span><span class="sxs-lookup"><span data-stu-id="ec2d1-125">The result of passing the malicious URL above to <xref:System.Uri?displayProperty=nameWithType> class constructor results in the following URI:</span></span>  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 <span data-ttu-id="ec2d1-126">To zachowanie domyślne można zmodyfikować w taki sposób, aby nie procent ścieżki zakodowany un ucieczki ograniczniki za pomocą opcji konfiguracji schemeSettings dla określonego schematu.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-126">This default behavior can be modified to not un-escape percent encoded path delimiters using the schemeSettings configuration option for a specific scheme.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ec2d1-127">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="ec2d1-127">Configuration Files</span></span>  
 <span data-ttu-id="ec2d1-128">Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="ec2d1-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ec2d1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="ec2d1-129">Example</span></span>  
 <span data-ttu-id="ec2d1-130">W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasę, która usuwa wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.</span><span class="sxs-lookup"><span data-stu-id="ec2d1-130">The following example shows a configuration used by the <xref:System.Uri> class that clears all scheme settings and then adds support for not escaping percent-encoded path delimiters for the http scheme.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ec2d1-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec2d1-131">See also</span></span>

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [<span data-ttu-id="ec2d1-132">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="ec2d1-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
