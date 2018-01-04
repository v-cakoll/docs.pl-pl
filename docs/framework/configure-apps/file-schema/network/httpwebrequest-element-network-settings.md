---
title: '&lt;httpWebRequest&gt; elementu (ustawienia sieciowe)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
caps.latest.revision: "18"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: dadb2d7635f132b44d6fca8c56f53b847ffb1ff9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="lthttpwebrequestgt-element-network-settings"></a><span data-ttu-id="2d92b-102">&lt;httpWebRequest&gt; elementu (ustawienia sieciowe)</span><span class="sxs-lookup"><span data-stu-id="2d92b-102">&lt;httpWebRequest&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2d92b-103">Dostosowuje parametry żądania sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2d92b-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="2d92b-104">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="2d92b-104">\<configuration></span></span>  
<span data-ttu-id="2d92b-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="2d92b-105">\<system.net></span></span>  
<span data-ttu-id="2d92b-106">\<Ustawienia ></span><span class="sxs-lookup"><span data-stu-id="2d92b-106">\<settings></span></span>  
<span data-ttu-id="2d92b-107">\<httpWebRequest ></span><span class="sxs-lookup"><span data-stu-id="2d92b-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d92b-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d92b-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d92b-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="2d92b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2d92b-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="2d92b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d92b-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="2d92b-111">Attributes</span></span>  
  
|<span data-ttu-id="2d92b-112">**Atrybut**</span><span class="sxs-lookup"><span data-stu-id="2d92b-112">**Attribute**</span></span>|<span data-ttu-id="2d92b-113">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2d92b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="2d92b-114">Określa maksymalną długość nagłówka odpowiedzi w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="2d92b-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="2d92b-115">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="2d92b-115">The default is 64.</span></span> <span data-ttu-id="2d92b-116">Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na nagłówków odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="2d92b-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="2d92b-117">Określa maksymalną długość odpowiedzi błędu, w kilobajtach.</span><span class="sxs-lookup"><span data-stu-id="2d92b-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="2d92b-118">Wartość domyślna to 64.</span><span class="sxs-lookup"><span data-stu-id="2d92b-118">The default is 64.</span></span> <span data-ttu-id="2d92b-119">Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na odpowiedzi na błąd.</span><span class="sxs-lookup"><span data-stu-id="2d92b-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="2d92b-120">Określa maksymalną długość przekazywania w odpowiedzi na kod błędu nieautoryzowanego, w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2d92b-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="2d92b-121">Wartość domyślna to -1.</span><span class="sxs-lookup"><span data-stu-id="2d92b-121">The default is -1.</span></span> <span data-ttu-id="2d92b-122">Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="2d92b-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="2d92b-123">Określa, czy włączone jest niebezpieczne nagłówka podczas analizowania.</span><span class="sxs-lookup"><span data-stu-id="2d92b-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="2d92b-124">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="2d92b-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d92b-125">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="2d92b-125">Child Elements</span></span>  
 <span data-ttu-id="2d92b-126">Brak.</span><span class="sxs-lookup"><span data-stu-id="2d92b-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d92b-127">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="2d92b-127">Parent Elements</span></span>  
  
|<span data-ttu-id="2d92b-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="2d92b-128">**Element**</span></span>|<span data-ttu-id="2d92b-129">**Opis**</span><span class="sxs-lookup"><span data-stu-id="2d92b-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d92b-130">Ustawienia</span><span class="sxs-lookup"><span data-stu-id="2d92b-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="2d92b-131">Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2d92b-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d92b-132">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d92b-132">Remarks</span></span>  
 <span data-ttu-id="2d92b-133">Domyślnie program .NET Framework ściśle wymusza RFC 2616 podczas analizowania identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="2d92b-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="2d92b-134">Niektóre odpowiedzi serwera może zawierać znaków kontrolnych w polach zabronione, co spowoduje <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metodę, aby zgłosić <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="2d92b-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="2d92b-135">Jeśli **useUnsafeHeaderParsing** ustawiono **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nie zgłosi wyjątku w takim przypadku; jednak, aplikacja będzie narażony na kilka rodzajów ataków analizy identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="2d92b-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="2d92b-136">Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawiera znaków kontrolnych.</span><span class="sxs-lookup"><span data-stu-id="2d92b-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2d92b-137">Pliki konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2d92b-137">Configuration Files</span></span>  
 <span data-ttu-id="2d92b-138">Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2d92b-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d92b-139">Przykład</span><span class="sxs-lookup"><span data-stu-id="2d92b-139">Example</span></span>  
 <span data-ttu-id="2d92b-140">Poniższy przykład przedstawia sposób określ większy niż normalne nagłówka maksymalną długość.</span><span class="sxs-lookup"><span data-stu-id="2d92b-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d92b-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d92b-141">See Also</span></span>  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [<span data-ttu-id="2d92b-142">Schemat ustawień sieci</span><span class="sxs-lookup"><span data-stu-id="2d92b-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
