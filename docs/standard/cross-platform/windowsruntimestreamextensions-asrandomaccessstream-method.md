---
title: WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
api_name:
- System.IO.WindowsRuntimeStreamExtensions.AsRandomAccessStream
api_location:
- System.Runtime.WindowsRuntime.dll
ms.assetid: dcc72283-caed-49ee-b45d-ccaf94e97129
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d5dd2829a9a00f869af3d7f370f99361979b8106
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/06/2019
ms.locfileid: "55758797"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="bb3fc-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb3fc-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="bb3fc-103">[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="bb3fc-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="bb3fc-104">Konwertuje określony strumień na strumień o dostępie losowym.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="bb3fc-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Zestaw:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="bb3fc-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="bb3fc-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb3fc-106">Syntax</span></span>

```csharp
[CLSCompliantAttribute(false)]
public static IRandomAccessStream AsRandomAccessStream(Stream stream)
```

```vb
'Declaration
<ExtensionAttribute> _
<CLSCompliantAttribute(False)> _
Public Shared Function AsRandomAccessStream ( _
        stream As Stream) As IRandomAccessStream
```

## <a name="parameters"></a><span data-ttu-id="bb3fc-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb3fc-107">Parameters</span></span>

`stream`

<span data-ttu-id="bb3fc-108">Typ: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="bb3fc-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="bb3fc-109">Strumień do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="bb3fc-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bb3fc-110">Return Value</span></span>

<span data-ttu-id="bb3fc-111">Typ: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="bb3fc-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="bb3fc-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] strumienia dostępu losowego, który reprezentujący przekonwertowany strumień.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="bb3fc-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="bb3fc-113">Exceptions</span></span>

|<span data-ttu-id="bb3fc-114">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="bb3fc-114">Exception</span></span>|<span data-ttu-id="bb3fc-115">Warunek</span><span class="sxs-lookup"><span data-stu-id="bb3fc-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="bb3fc-116">Strumień, który ma zostać przekonwertowany, nie obsługuje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bb3fc-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bb3fc-117">Remarks</span></span>

<span data-ttu-id="bb3fc-118">Ta metoda rozszerzenia jest dostępna tylko podczas projektowania aplikacji do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="bb3fc-119">Ta metoda oferuje wygodny sposób pracy ze strumieniami w aplikacjach do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="bb3fc-120">Strumień programu .NET Framework, który ma zostać przekonwertowany, musi obsługiwać wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="bb3fc-121">Aby uzyskać więcej informacji, zobacz <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bb3fc-122">Ten interfejs API jest obsługiwany w .NET Framework 4.5.1 i nowszymi wersjami, ale nie w wersji 4.5.</span><span class="sxs-lookup"><span data-stu-id="bb3fc-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="bb3fc-123">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="bb3fc-123">Version Information</span></span>

<span data-ttu-id="bb3fc-124">**Platforma .NET dla aplikacji Windows Store**</span><span class="sxs-lookup"><span data-stu-id="bb3fc-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="bb3fc-125">Obsługują: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="bb3fc-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="bb3fc-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb3fc-126">See also</span></span>

- [<span data-ttu-id="bb3fc-127">Instrukcje: Konwertowanie między .NET Framework i strumieni środowiska wykonawczego Windows</span><span class="sxs-lookup"><span data-stu-id="bb3fc-127">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
