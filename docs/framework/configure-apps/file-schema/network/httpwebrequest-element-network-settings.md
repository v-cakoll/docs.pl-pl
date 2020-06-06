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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087454"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="380ca-102">\<httpWebRequest>, element (ustawienia sieci)</span><span class="sxs-lookup"><span data-stu-id="380ca-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="380ca-103">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="380ca-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="380ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="380ca-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="380ca-105">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="380ca-105">Attributes and Elements</span></span>  
 <span data-ttu-id="380ca-106">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="380ca-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="380ca-107">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="380ca-107">Attributes</span></span>  
  
|<span data-ttu-id="380ca-108">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="380ca-108">**Attribute**</span></span>|<span data-ttu-id="380ca-109">**Opis**</span><span class="sxs-lookup"><span data-stu-id="380ca-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="380ca-110">Określa maksymalną długość nagłówka odpowiedzi w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="380ca-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="380ca-111">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="380ca-111">The default is 64.</span></span> <span data-ttu-id="380ca-112">Wartość-1 oznacza, że w nagłówkach odpowiedzi nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="380ca-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="380ca-113">Określa maksymalną długość odpowiedzi na błąd w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="380ca-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="380ca-114">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="380ca-114">The default is 64.</span></span> <span data-ttu-id="380ca-115">Wartość-1 oznacza, że w odpowiedzi na błąd nie zostanie wprowadzony limit rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="380ca-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="380ca-116">Określa maksymalną długość przekazywania w odpowiedzi na nieautoryzowany kod błędu w bajtach.</span><span class="sxs-lookup"><span data-stu-id="380ca-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="380ca-117">Wartość domyślna to-1.</span><span class="sxs-lookup"><span data-stu-id="380ca-117">The default is -1.</span></span> <span data-ttu-id="380ca-118">Wartość-1 oznacza, że żaden limit rozmiaru nie zostanie nałożony na przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="380ca-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="380ca-119">Określa, czy jest włączone analizowanie niebezpiecznego nagłówka.</span><span class="sxs-lookup"><span data-stu-id="380ca-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="380ca-120">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="380ca-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="380ca-121">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="380ca-121">Child Elements</span></span>  
 <span data-ttu-id="380ca-122">Brak.</span><span class="sxs-lookup"><span data-stu-id="380ca-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="380ca-123">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="380ca-123">Parent Elements</span></span>  
  
|<span data-ttu-id="380ca-124">**Postaci**</span><span class="sxs-lookup"><span data-stu-id="380ca-124">**Element**</span></span>|<span data-ttu-id="380ca-125">**Opis**</span><span class="sxs-lookup"><span data-stu-id="380ca-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="380ca-126">ustawienia</span><span class="sxs-lookup"><span data-stu-id="380ca-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="380ca-127">Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="380ca-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="380ca-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="380ca-128">Remarks</span></span>  
 <span data-ttu-id="380ca-129">Domyślnie .NET Framework ściśle wymusza analizowanie identyfikatorów URI w dokumencie RFC 2616.</span><span class="sxs-lookup"><span data-stu-id="380ca-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="380ca-130">Niektóre odpowiedzi serwera mogą zawierać znaki kontrolne w zabronionych polach, co spowoduje, że <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda wygeneruje <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="380ca-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="380ca-131">Jeśli **UseUnsafeHeaderParsing** ma **wartość true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> program nie będzie zgłaszany w tym przypadku, jednak aplikacja będzie narażona na kilka form ataków dotyczących analizy identyfikatorów URI.</span><span class="sxs-lookup"><span data-stu-id="380ca-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="380ca-132">Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawierała znaków kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="380ca-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="380ca-133">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="380ca-133">Configuration Files</span></span>  
 <span data-ttu-id="380ca-134">Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="380ca-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="380ca-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="380ca-135">Example</span></span>  
 <span data-ttu-id="380ca-136">Poniższy przykład pokazuje, jak określić większą niż normalną maksymalną długość nagłówka.</span><span class="sxs-lookup"><span data-stu-id="380ca-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="380ca-137">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="380ca-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="380ca-138">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="380ca-138">Network Settings Schema</span></span>](index.md)
