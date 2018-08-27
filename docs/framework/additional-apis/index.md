---
title: Dodatkowe biblioteki klas i interfejsów API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 049268c29946e95ca7bb194f6cae38baf8f060f6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933533"
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="5e8d1-102">Dodatkowe biblioteki klas i interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5e8d1-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="5e8d1-103">Jest stale rozwijana i .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-103">The .NET Framework is constantly evolving.</span></span> <span data-ttu-id="5e8d1-104">Aby poprawić programowanie dla wielu platform i wprowadzać nowe funkcjonalności wcześnie, nowe funkcje są wydawane poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="5e8d1-104">To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB).</span></span> <span data-ttu-id="5e8d1-105">Ten temat zawiera listę projektów OOB, które firma Microsoft zapewnia dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-105">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="5e8d1-106">Ponadto niektóre biblioteki kierować konkretnych platform lub implementacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-106">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="5e8d1-107">Na przykład <xref:System.Text.CodePagesEncodingProvider> klasy sprawia, że stron kodowych są dostępne dla aplikacji platformy uniwersalnej systemu Windows, opracowane przy użyciu programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-107">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="5e8d1-108">Ten temat zawiera również tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-108">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="5e8d1-109">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="5e8d1-109">OOB projects</span></span>
  
| <span data-ttu-id="5e8d1-110">Projekt</span><span class="sxs-lookup"><span data-stu-id="5e8d1-110">Project</span></span> | <span data-ttu-id="5e8d1-111">Opis</span><span class="sxs-lookup"><span data-stu-id="5e8d1-111">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="5e8d1-112">Zawiera kolekcje, które są wątkowo bezpieczne i gwarancji nigdy nie zmieni się ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-112">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="5e8d1-113">Udostępnia program obsługi komunikatów dla <xref:System.Net.Http.HttpClient> oparte na interfejsie WinHTTP Windows.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-113">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="5e8d1-114">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="5e8d1-114">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="5e8d1-115">Zawiera bibliotekę typy wektorowe, które mogą korzystać SIMD przyspieszanie sprzętowe.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-115">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="5e8d1-116">Biblioteka przepływu danych TPL zapewnia składników przepływu danych, aby zwiększyć niezawodność aplikacji obsługujących współbieżności.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-116">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="5e8d1-117">Biblioteki charakterystyczne dla platformy</span><span class="sxs-lookup"><span data-stu-id="5e8d1-117">Platform-specific libraries</span></span>
  
| <span data-ttu-id="5e8d1-118">Projekt</span><span class="sxs-lookup"><span data-stu-id="5e8d1-118">Project</span></span> | <span data-ttu-id="5e8d1-119">Opis</span><span class="sxs-lookup"><span data-stu-id="5e8d1-119">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="5e8d1-120">Rozszerza <xref:System.Text.EncodingProvider> klasy w celu udostępnienia aplikacji przeznaczonych dla platformy uniwersalnej Windows stron kodowych.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-120">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="5e8d1-121">Interfejsy API z prywatnym</span><span class="sxs-lookup"><span data-stu-id="5e8d1-121">Private APIs</span></span>  

<span data-ttu-id="5e8d1-122">Te interfejsy API obsługuje infrastrukturę produktu i nie/obsługiwanych przeznaczonych do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="5e8d1-122">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="5e8d1-123">Nazwa interfejsu API</span><span class="sxs-lookup"><span data-stu-id="5e8d1-123">API Name</span></span> |
| -------- |
| [<span data-ttu-id="5e8d1-124">System.Net.Connection Class</span><span class="sxs-lookup"><span data-stu-id="5e8d1-124">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="5e8d1-125">System.Net.Connection.m\_WriteList Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-125">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="5e8d1-126">System.Net.ConnectionGroup Class</span><span class="sxs-lookup"><span data-stu-id="5e8d1-126">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="5e8d1-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-127">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="5e8d1-128">System.Net.CoreResponseData Class</span><span class="sxs-lookup"><span data-stu-id="5e8d1-128">System.Net.CoreResponseData Class</span></span>](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [<span data-ttu-id="5e8d1-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-129">System.Net.CoreResponseData.m\_ResponseHeaders Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [<span data-ttu-id="5e8d1-130">System.Net.CoreResponseData.m\_StatusCode Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-130">System.Net.CoreResponseData.m\_StatusCode Field</span></span>](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [<span data-ttu-id="5e8d1-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-131">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="5e8d1-132">System.Net.HttpWebRequest.\_CoreResponse Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-132">System.Net.HttpWebRequest.\_CoreResponse Field</span></span>](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [<span data-ttu-id="5e8d1-133">System.Net.HttpWebRequest.\_HttpResponse Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-133">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="5e8d1-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-134">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="5e8d1-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-135">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="5e8d1-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span><span class="sxs-lookup"><span data-stu-id="5e8d1-136">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="5e8d1-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span><span class="sxs-lookup"><span data-stu-id="5e8d1-137">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="5e8d1-138">System.Windows.Forms.Design.DataMemberListEditor Class</span><span class="sxs-lookup"><span data-stu-id="5e8d1-138">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="5e8d1-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e8d1-139">See also</span></span>

[<span data-ttu-id="5e8d1-140">Program .NET Framework i wydania poza harmonogramem (OOB)</span><span class="sxs-lookup"><span data-stu-id="5e8d1-140">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
