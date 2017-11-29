---
title: "WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
api_name: System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location: System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: be93ddc0f3bf0a5079f31bfa0ff5caa882342c37
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="64717-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda</span><span class="sxs-lookup"><span data-stu-id="64717-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>
<span data-ttu-id="64717-103">[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="64717-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>  
  
 <span data-ttu-id="64717-104">Konwertuje określony strumień na strumień o dostępie losowym.</span><span class="sxs-lookup"><span data-stu-id="64717-104">Converts the specified stream to a random access stream.</span></span>  
  
 <span data-ttu-id="64717-105">**Namespace:**<xref:System.IO?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64717-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType></span></span>  
 <span data-ttu-id="64717-106">**Zestaw:** System.Runtime.WindowsRuntime (w System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="64717-106">**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64717-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="64717-107">Syntax</span></span>  
  
```csharp  
[CLSCompliantAttribute(false)]  
public static  IRandomAccessStream AsRandomAccessStream(Stream stream)  
```  
  
```vb  
'Declaration  
<ExtensionAttribute> _  
<CLSCompliantAttribute(False)> _  
Public Shared Function AsRandomAccessStream ( _  
        stream As Stream) As IRandomAccessStream  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64717-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="64717-108">Parameters</span></span>  
 `stream`  
  
 <span data-ttu-id="64717-109">Typ:<xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="64717-109">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="64717-110">Strumień do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="64717-110">The stream to convert.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64717-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="64717-111">Return Value</span></span>  
 <span data-ttu-id="64717-112">Typ: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span><span class="sxs-lookup"><span data-stu-id="64717-112">Type: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)</span></span>  
<span data-ttu-id="64717-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dostępie swobodnym strumienia, reprezentujący skonwertowany strumienia.</span><span class="sxs-lookup"><span data-stu-id="64717-113">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="64717-114">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="64717-114">Exceptions</span></span>  
  
|<span data-ttu-id="64717-115">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="64717-115">Exception</span></span>|<span data-ttu-id="64717-116">Warunek</span><span class="sxs-lookup"><span data-stu-id="64717-116">Condition</span></span>|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|<span data-ttu-id="64717-117">Strumień, który ma zostać przekonwertowany, nie obsługuje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="64717-117">The stream to convert does not support seeking.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="64717-118">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64717-118">Remarks</span></span>  
 <span data-ttu-id="64717-119">Ta metoda rozszerzenia jest dostępna tylko podczas projektowania aplikacji do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="64717-119">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="64717-120">Ta metoda oferuje wygodny sposób pracy ze strumieniami w aplikacjach do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="64717-120">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="64717-121">W strumieniu .NET Framework, który ma zostać przekonwertowany musi obsługiwać operacji wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="64717-121">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="64717-122">Aby uzyskać więcej informacji, zobacz <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="64717-122">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="64717-123">Ten interfejs API jest obsługiwany w .NET Framework 4.5.1 lub nowszy, ale nie w wersji 4.5.</span><span class="sxs-lookup"><span data-stu-id="64717-123">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="64717-124">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="64717-124">Version Information</span></span>  
 <span data-ttu-id="64717-125">**Platforma .NET dla aplikacji ze Sklepu Windows**</span><span class="sxs-lookup"><span data-stu-id="64717-125">**.NET for Windows Store apps**</span></span>  
  
 <span data-ttu-id="64717-126">Obsługiwane w: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="64717-126">Supported in: Windows 8.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64717-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64717-127">See Also</span></span>  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [<span data-ttu-id="64717-128">Porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows</span><span class="sxs-lookup"><span data-stu-id="64717-128">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
