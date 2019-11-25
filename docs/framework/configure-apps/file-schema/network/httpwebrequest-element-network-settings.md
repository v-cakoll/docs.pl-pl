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
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087454"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="3299e-102">\<element > httpWebRequest (Ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="3299e-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="3299e-103">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="3299e-103">Customizes Web request parameters.</span></span>  

<span data-ttu-id="3299e-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="3299e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3299e-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="3299e-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="3299e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) ></span><span class="sxs-lookup"><span data-stu-id="3299e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\</span></span>
<span data-ttu-id="3299e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpWebRequest >**</span><span class="sxs-lookup"><span data-stu-id="3299e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**</span></span>

## <a name="syntax"></a><span data-ttu-id="3299e-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3299e-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3299e-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3299e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3299e-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3299e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3299e-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3299e-111">Attributes</span></span>  
  
|<span data-ttu-id="3299e-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="3299e-112">**Attribute**</span></span>|<span data-ttu-id="3299e-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3299e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="3299e-114">Określa maksymalną długość nagłówka odpowiedzi w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="3299e-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="3299e-115">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="3299e-115">The default is 64.</span></span> <span data-ttu-id="3299e-116">Wartość-1 oznacza, że w nagłówkach odpowiedzi nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="3299e-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="3299e-117">Określa maksymalną długość odpowiedzi na błąd w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="3299e-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="3299e-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="3299e-118">The default is 64.</span></span> <span data-ttu-id="3299e-119">Wartość-1 oznacza, że w odpowiedzi na błąd nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="3299e-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="3299e-120">Określa maksymalną długość przekazywania w odpowiedzi na nieautoryzowany kod błędu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="3299e-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="3299e-121">Wartość domyślna to-1.</span><span class="sxs-lookup"><span data-stu-id="3299e-121">The default is -1.</span></span> <span data-ttu-id="3299e-122">Wartość-1 oznacza, że żaden limit rozmiaru nie zostanie nałożony na przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="3299e-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="3299e-123">Określa, czy jest włączone analizowanie niebezpiecznego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="3299e-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="3299e-124">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="3299e-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3299e-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3299e-125">Child Elements</span></span>  
 <span data-ttu-id="3299e-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="3299e-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3299e-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3299e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3299e-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="3299e-128">**Element**</span></span>|<span data-ttu-id="3299e-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="3299e-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="3299e-130">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="3299e-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="3299e-131">Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="3299e-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3299e-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3299e-132">Remarks</span></span>  
 <span data-ttu-id="3299e-133">Domyślnie .NET Framework ściśle wymusza analizowanie identyfikatorów URI w dokumencie RFC 2616.</span><span class="sxs-lookup"><span data-stu-id="3299e-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="3299e-134">Niektóre odpowiedzi serwera mogą zawierać znaki kontrolne w zabronionych polach, co spowoduje wygenerowanie <xref:System.Net.WebException>przez metodę <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3299e-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="3299e-135">Jeśli **UseUnsafeHeaderParsing** ma **wartość true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> w tym przypadku nie zostanie zgłoszony; Jednak aplikacja będzie narażona na kilka form ataków z analizowaniem identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="3299e-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="3299e-136">Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawierała znaków kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="3299e-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="3299e-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3299e-137">Configuration Files</span></span>  
 <span data-ttu-id="3299e-138">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="3299e-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3299e-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="3299e-139">Example</span></span>  
 <span data-ttu-id="3299e-140">Poniższy przykład pokazuje, jak określić większą niż normalną maksymalną długość nagłówka.</span><span class="sxs-lookup"><span data-stu-id="3299e-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3299e-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3299e-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="3299e-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="3299e-142">Network Settings Schema</span></span>](index.md)
