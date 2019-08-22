---
title: <httpWebRequest>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: de5672e5c6762b1e0742e717a3d499a4f93ee8ec
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659341"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="79395-102">\<httpWebRequest >, element (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="79395-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="79395-103">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="79395-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="79395-104">\<> konfiguracji</span><span class="sxs-lookup"><span data-stu-id="79395-104">\<configuration></span></span>  
<span data-ttu-id="79395-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="79395-105">\<system.net></span></span>  
<span data-ttu-id="79395-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="79395-106">\<settings></span></span>  
<span data-ttu-id="79395-107">\<httpWebRequest></span><span class="sxs-lookup"><span data-stu-id="79395-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79395-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="79395-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="79395-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="79395-109">Attributes and Elements</span></span>  
 <span data-ttu-id="79395-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="79395-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="79395-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="79395-111">Attributes</span></span>  
  
|<span data-ttu-id="79395-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="79395-112">**Attribute**</span></span>|<span data-ttu-id="79395-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="79395-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="79395-114">Określa maksymalną długość nagłówka odpowiedzi w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="79395-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="79395-115">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="79395-115">The default is 64.</span></span> <span data-ttu-id="79395-116">Wartość-1 oznacza, że w nagłówkach odpowiedzi nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="79395-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="79395-117">Określa maksymalną długość odpowiedzi na błąd w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="79395-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="79395-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="79395-118">The default is 64.</span></span> <span data-ttu-id="79395-119">Wartość-1 oznacza, że w odpowiedzi na błąd nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="79395-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="79395-120">Określa maksymalną długość przekazywania w odpowiedzi na nieautoryzowany kod błędu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="79395-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="79395-121">Wartość domyślna to-1.</span><span class="sxs-lookup"><span data-stu-id="79395-121">The default is -1.</span></span> <span data-ttu-id="79395-122">Wartość-1 oznacza, że żaden limit rozmiaru nie zostanie nałożony na przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="79395-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="79395-123">Określa, czy jest włączone analizowanie niebezpiecznego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="79395-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="79395-124">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="79395-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="79395-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="79395-125">Child Elements</span></span>  
 <span data-ttu-id="79395-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="79395-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="79395-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="79395-127">Parent Elements</span></span>  
  
|<span data-ttu-id="79395-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="79395-128">**Element**</span></span>|<span data-ttu-id="79395-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="79395-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="79395-130">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="79395-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="79395-131">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="79395-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79395-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="79395-132">Remarks</span></span>  
 <span data-ttu-id="79395-133">Domyślnie .NET Framework ściśle wymusza analizowanie identyfikatorów URI w dokumencie RFC 2616.</span><span class="sxs-lookup"><span data-stu-id="79395-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="79395-134">Niektóre odpowiedzi serwera mogą zawierać znaki kontrolne w zabronionych polach, co spowoduje <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> , że metoda <xref:System.Net.WebException>wygeneruje.</span><span class="sxs-lookup"><span data-stu-id="79395-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="79395-135">Jeśli **UseUnsafeHeaderParsing** ma **wartość true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> program nie będzie zgłaszany w tym przypadku, jednak aplikacja będzie narażona na kilka form ataków dotyczących analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="79395-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="79395-136">Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawierała znaków kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="79395-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="79395-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="79395-137">Configuration Files</span></span>  
 <span data-ttu-id="79395-138">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="79395-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79395-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="79395-139">Example</span></span>  
 <span data-ttu-id="79395-140">Poniższy przykład pokazuje, jak określić większą niż normalną maksymalną długość nagłówka.</span><span class="sxs-lookup"><span data-stu-id="79395-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="79395-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79395-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="79395-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="79395-142">Network Settings Schema</span></span>](index.md)
