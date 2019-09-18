---
title: Dodatkowe biblioteki klas i interfejsy API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053244"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="a2f42-102">Dodatkowe biblioteki klas i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="a2f42-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="a2f42-103">.NET Framework ciągle się zmienia.</span><span class="sxs-lookup"><span data-stu-id="a2f42-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="a2f42-104">Aby ulepszyć Programowanie dla wielu platform i wprowadzić nowe funkcje wczesne, nowe funkcje są uwalniane poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="a2f42-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="a2f42-105">W tym temacie wymieniono projekty OOB, dla których dostarczamy dokumentację.</span><span class="sxs-lookup"><span data-stu-id="a2f42-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="a2f42-106">Ponadto niektóre biblioteki są przeznaczone dla określonych platform lub implementacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2f42-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="a2f42-107">Na przykład Klasa sprawia <xref:System.Text.CodePagesEncodingProvider> , że kodowanie strony kodowej jest dostępne dla aplikacji platformy UWP utworzonych przy użyciu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2f42-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="a2f42-108">W tym temacie wymieniono również te biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a2f42-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="a2f42-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="a2f42-109">OOB projects</span></span>
  
| <span data-ttu-id="a2f42-110">Projekt</span><span class="sxs-lookup"><span data-stu-id="a2f42-110">Project</span></span> | <span data-ttu-id="a2f42-111">Opis</span><span class="sxs-lookup"><span data-stu-id="a2f42-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="a2f42-112">Zapewnia kolekcje, które są bezpieczne dla wątków i gwarantują, że nigdy nie zmieniają ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="a2f42-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="a2f42-113">Zapewnia obsługę komunikatów dla <xref:System.Net.Http.HttpClient> programu na podstawie interfejsu WinHTTP systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a2f42-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| <xref:System.Numerics> | <span data-ttu-id="a2f42-114">Udostępnia bibliotekę typów wektorów, które mogą korzystać z przyspieszania sprzętowego SIMD.</span><span class="sxs-lookup"><span data-stu-id="a2f42-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="a2f42-115">Biblioteka TPL przepływu danych zawiera składniki przepływu danych, które ułatwiają zwiększenie niezawodności aplikacji z obsługą współbieżności.</span><span class="sxs-lookup"><span data-stu-id="a2f42-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="a2f42-116">Biblioteki charakterystyczne dla platformy</span><span class="sxs-lookup"><span data-stu-id="a2f42-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="a2f42-117">Projekt</span><span class="sxs-lookup"><span data-stu-id="a2f42-117">Project</span></span> | <span data-ttu-id="a2f42-118">Opis</span><span class="sxs-lookup"><span data-stu-id="a2f42-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="a2f42-119"><xref:System.Text.EncodingProvider> Rozszerza klasę, aby umożliwić dostęp do kodowania stron kodowych aplikacjom przeznaczonym dla platforma uniwersalna systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a2f42-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="a2f42-120">Prywatne interfejsy API</span><span class="sxs-lookup"><span data-stu-id="a2f42-120">Private APIs</span></span>  

<span data-ttu-id="a2f42-121">Te interfejsy API obsługują infrastrukturę produktu i nie są przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a2f42-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="a2f42-122">Nazwa interfejsu API</span><span class="sxs-lookup"><span data-stu-id="a2f42-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="a2f42-123">System.Net.Connection Class</span><span class="sxs-lookup"><span data-stu-id="a2f42-123">System.Net.Connection Class</span></span>](connection.md) |
| [<span data-ttu-id="a2f42-124">System.Net.Connection.m\_WriteList Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-124">System.Net.Connection.m\_WriteList Field</span></span>](m_writelist.md) |
| [<span data-ttu-id="a2f42-125">System.Net.ConnectionGroup Class</span><span class="sxs-lookup"><span data-stu-id="a2f42-125">System.Net.ConnectionGroup Class</span></span>](connectiongroup.md) |
| [<span data-ttu-id="a2f42-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](m_connectionlist.md) |
| [<span data-ttu-id="a2f42-127">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="a2f42-127">System.Net.CoreResponseData Class</span></span>](coreresponsedata.md) |
| [<span data-ttu-id="a2f42-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-128">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="a2f42-129">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-129">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="a2f42-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-130">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](_autoredirects.md) |
| [<span data-ttu-id="a2f42-131">System.Net.HttpWebRequest.\_CoreResponse Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-131">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="a2f42-132">System.Net.HttpWebRequest.\_HttpResponse Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-132">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](_httpresponse.md) |
| [<span data-ttu-id="a2f42-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-133">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](m_connectiongrouplist.md) |
| [<span data-ttu-id="a2f42-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-134">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](s_servicepointtable.md) |
| [<span data-ttu-id="a2f42-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="a2f42-135">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="a2f42-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="a2f42-136">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](datamemberfieldeditor-class.md) |
| [<span data-ttu-id="a2f42-137">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="a2f42-137">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="a2f42-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a2f42-138">See also</span></span>

- [<span data-ttu-id="a2f42-139">Program .NET Framework i wydania poza harmonogramem (OOB)</span><span class="sxs-lookup"><span data-stu-id="a2f42-139">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
