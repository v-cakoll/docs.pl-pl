---
title: Biblioteki dodatkowe klasy i interfejsy API
ms.custom: 
ms.date: 04/12/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c22de3ed401e0be10b155649395da43cedb35e6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="additional-class-libraries-and-apis"></a><span data-ttu-id="8c11b-102">Biblioteki dodatkowe klasy i interfejsy API</span><span class="sxs-lookup"><span data-stu-id="8c11b-102">Additional class libraries and APIs</span></span>

<span data-ttu-id="8c11b-103">Stale ewoluuje programu .NET Framework i wydania w celu ulepszania wiele platform lub wprowadzenie nowych funkcji wcześniej dla naszych klientów, nowych funkcji poza pasmem (OOB).</span><span class="sxs-lookup"><span data-stu-id="8c11b-103">The .NET Framework is constantly evolving and in order to improve cross-platform development or to introduce new functionality early to our customers, we release new features out of band (OOB).</span></span> <span data-ttu-id="8c11b-104">Ten temat zawiera listę projektów OOB, które firma Microsoft udostępnia w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="8c11b-104">This topic lists the OOB projects that we provide documentation for.</span></span>  
  
<span data-ttu-id="8c11b-105">Ponadto niektóre biblioteki docelowych określonych platform lub implementacji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c11b-105">In addition, some libraries target specific platforms or implementations of the .NET Framework.</span></span> <span data-ttu-id="8c11b-106">Na przykład <xref:System.Text.CodePagesEncodingProvider> klasy udostępnia kodowania strony kodu do aplikacji platformy uniwersalnej systemu Windows opracowana za pomocą programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c11b-106">For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework.</span></span> <span data-ttu-id="8c11b-107">W tym temacie wymieniono także tych bibliotek.</span><span class="sxs-lookup"><span data-stu-id="8c11b-107">This topic lists these libraries as well.</span></span>  
  
## <a name="oob-projects"></a><span data-ttu-id="8c11b-108">Projekty OOB</span><span class="sxs-lookup"><span data-stu-id="8c11b-108">OOB projects</span></span>
  
| <span data-ttu-id="8c11b-109">Projekt</span><span class="sxs-lookup"><span data-stu-id="8c11b-109">Project</span></span> | <span data-ttu-id="8c11b-110">Opis</span><span class="sxs-lookup"><span data-stu-id="8c11b-110">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | <span data-ttu-id="8c11b-111">Zawiera kolekcje, które są wątkowo bezpieczne i zagwarantowanie odpowiednich nigdy nie ulegną zmianie ich zawartość.</span><span class="sxs-lookup"><span data-stu-id="8c11b-111">Provides collections that are thread safe and guaranteed to never change their contents.</span></span> |
| <xref:System.Net.Http.WinHttpHandler> | <span data-ttu-id="8c11b-112">Udostępnia program obsługi komunikatów dla <xref:System.Net.Http.HttpClient> oparte na interfejsie WinHTTP systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8c11b-112">Provides a message handler for <xref:System.Net.Http.HttpClient> based on the WinHTTP interface of Windows.</span></span> |
| [<span data-ttu-id="8c11b-113">System.Numerics.Vectors</span><span class="sxs-lookup"><span data-stu-id="8c11b-113">System.Numerics.Vectors</span></span>](https://msdn.microsoft.com/library/mt452176.aspx) | <span data-ttu-id="8c11b-114">Udostępnia bibliotekę typów wektora, które można wykorzystać SIMD przyspieszanie sprzętowe.</span><span class="sxs-lookup"><span data-stu-id="8c11b-114">Provides a library of vector types that can take advantage of SIMD hardware-based acceleration.</span></span>| 
| <xref:System.Threading.Tasks.Dataflow> | <span data-ttu-id="8c11b-115">Biblioteka przepływu danych tpl zawiera składniki przepływu danych, aby zwiększyć niezawodność aplikacji z obsługą współbieżności.</span><span class="sxs-lookup"><span data-stu-id="8c11b-115">The TPL Dataflow Library provides dataflow components to help increase the robustness of concurrency-enabled applications.</span></span> |  

## <a name="platform-specific-libraries"></a><span data-ttu-id="8c11b-116">Biblioteki specyficzne dla platformy</span><span class="sxs-lookup"><span data-stu-id="8c11b-116">Platform-specific libraries</span></span>
  
| <span data-ttu-id="8c11b-117">Projekt</span><span class="sxs-lookup"><span data-stu-id="8c11b-117">Project</span></span> | <span data-ttu-id="8c11b-118">Opis</span><span class="sxs-lookup"><span data-stu-id="8c11b-118">Description</span></span> |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | <span data-ttu-id="8c11b-119">Rozszerza <xref:System.Text.EncodingProvider> klasy, aby udostępnić kodowania strony kodu aplikacji przeznaczonych dla platformy uniwersalnej systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="8c11b-119">Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform.</span></span> |  
  
## <a name="private-apis"></a><span data-ttu-id="8c11b-120">Interfejsy API prywatnych</span><span class="sxs-lookup"><span data-stu-id="8c11b-120">Private APIs</span></span>  

<span data-ttu-id="8c11b-121">Te interfejsy API obsługuje infrastrukturę programu produktu i nie są/obsługiwane przeznaczonych do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8c11b-121">These APIs support the product infrastructure and are not intended/supported to be used directly from your code.</span></span>  
  
| <span data-ttu-id="8c11b-122">Nazwa interfejsu API</span><span class="sxs-lookup"><span data-stu-id="8c11b-122">API Name</span></span> |
| -------- |
| [<span data-ttu-id="8c11b-123">Klasa System.Net.Connection</span><span class="sxs-lookup"><span data-stu-id="8c11b-123">System.Net.Connection Class</span></span>](../../../docs/framework/additional-apis/connection.md) |
| [<span data-ttu-id="8c11b-124">System.Net.Connection.m\_WriteList pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-124">System.Net.Connection.m\_WriteList Field</span></span>](../../../docs/framework/additional-apis/m_writelist.md) |
| [<span data-ttu-id="8c11b-125">Klasa System.Net.ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="8c11b-125">System.Net.ConnectionGroup Class</span></span>](../../../docs/framework/additional-apis/connectiongroup.md) |
| [<span data-ttu-id="8c11b-126">System.Net.ConnectionGroup.m\_ConnectionList pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-126">System.Net.ConnectionGroup.m\_ConnectionList Field</span></span>](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [<span data-ttu-id="8c11b-127">System.Net.HttpWebRequest. \_HttpResponse pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-127">System.Net.HttpWebRequest.\_HttpResponse Field</span></span>](../../../docs/framework/additional-apis/_httpresponse.md) |
| [<span data-ttu-id="8c11b-128">System.Net.HttpWebRequest. \_AutoRedirects pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-128">System.Net.HttpWebRequest.\_AutoRedirects Field</span></span>](../../../docs/framework/additional-apis/_autoredirects.md) |
| [<span data-ttu-id="8c11b-129">System.Net.ServicePoint.m\_ConnectionGroupList pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-129">System.Net.ServicePoint.m\_ConnectionGroupList Field</span></span>](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [<span data-ttu-id="8c11b-130">System.Net.ServicePointManager.s\_ServicePointTable pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-130">System.Net.ServicePointManager.s\_ServicePointTable Field</span></span>](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [<span data-ttu-id="8c11b-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes pola</span><span class="sxs-lookup"><span data-stu-id="8c11b-131">System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field</span></span>](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [<span data-ttu-id="8c11b-132">Klasa System.Windows.Forms.Design.DataMemberFieldEditor</span><span class="sxs-lookup"><span data-stu-id="8c11b-132">System.Windows.Forms.Design.DataMemberFieldEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [<span data-ttu-id="8c11b-133">Klasa System.Windows.Forms.Design.DataMemberListEditor</span><span class="sxs-lookup"><span data-stu-id="8c11b-133">System.Windows.Forms.Design.DataMemberListEditor Class</span></span>](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a><span data-ttu-id="8c11b-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c11b-134">See also</span></span>

[<span data-ttu-id="8c11b-135">Program .NET Framework i wydania poza harmonogramem (OOB)</span><span class="sxs-lookup"><span data-stu-id="8c11b-135">The .NET Framework and Out-of-Band Releases</span></span>](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
