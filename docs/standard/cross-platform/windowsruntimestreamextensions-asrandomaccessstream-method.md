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
ms.openlocfilehash: 8935a8c282bbe812ad76ac6d4228c38ab12626a4
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44193591"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a><span data-ttu-id="cf27b-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda</span><span class="sxs-lookup"><span data-stu-id="cf27b-102">WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) Method</span></span>

<span data-ttu-id="cf27b-103">[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="cf27b-103">[Supported in the .NET Framework 4.5.1 and later versions]</span></span>

<span data-ttu-id="cf27b-104">Konwertuje określony strumień na strumień o dostępie losowym.</span><span class="sxs-lookup"><span data-stu-id="cf27b-104">Converts the specified stream to a random access stream.</span></span>

<span data-ttu-id="cf27b-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **zestawu:** System.Runtime.WindowsRuntime (w pliku System.Runtime.WindowsRuntime.dll)</span><span class="sxs-lookup"><span data-stu-id="cf27b-105">**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Assembly:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)</span></span>

## <a name="syntax"></a><span data-ttu-id="cf27b-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="cf27b-106">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="cf27b-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="cf27b-107">Parameters</span></span>

`stream`

<span data-ttu-id="cf27b-108">Typ: <xref:System.IO.Stream?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cf27b-108">Type: <xref:System.IO.Stream?displayProperty=nameWithType></span></span>  
<span data-ttu-id="cf27b-109">Strumień do przekonwertowania.</span><span class="sxs-lookup"><span data-stu-id="cf27b-109">The stream to convert.</span></span>

## <a name="return-value"></a><span data-ttu-id="cf27b-110">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="cf27b-110">Return Value</span></span>

<span data-ttu-id="cf27b-111">Typ: <xref:Windows.Storage.Streams.RandomAccessStream></span><span class="sxs-lookup"><span data-stu-id="cf27b-111">Type: <xref:Windows.Storage.Streams.RandomAccessStream></span></span>  
<span data-ttu-id="cf27b-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] strumienia dostępu losowego, który reprezentujący przekonwertowany strumień.</span><span class="sxs-lookup"><span data-stu-id="cf27b-112">A [!INCLUDE[wrt](../../../includes/wrt-md.md)] random access stream, which represents the converted stream.</span></span>

## <a name="exceptions"></a><span data-ttu-id="cf27b-113">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cf27b-113">Exceptions</span></span>

|<span data-ttu-id="cf27b-114">Wyjątek</span><span class="sxs-lookup"><span data-stu-id="cf27b-114">Exception</span></span>|<span data-ttu-id="cf27b-115">Warunek</span><span class="sxs-lookup"><span data-stu-id="cf27b-115">Condition</span></span>|
|---------------|---------------|
|<xref:System.NotSupportedException>|<span data-ttu-id="cf27b-116">Strumień, który ma zostać przekonwertowany, nie obsługuje wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="cf27b-116">The stream to convert does not support seeking.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cf27b-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cf27b-117">Remarks</span></span>

<span data-ttu-id="cf27b-118">Ta metoda rozszerzenia jest dostępna tylko podczas projektowania aplikacji do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="cf27b-118">This extension method is available only when you develop Windows Store apps.</span></span> <span data-ttu-id="cf27b-119">Ta metoda oferuje wygodny sposób pracy ze strumieniami w aplikacjach do Sklepu Windows.</span><span class="sxs-lookup"><span data-stu-id="cf27b-119">This method provides a convenient way of working with streams in Windows Store apps.</span></span> <span data-ttu-id="cf27b-120">Strumień programu .NET Framework, który ma zostać przekonwertowany, musi obsługiwać wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="cf27b-120">The .NET Framework stream you want to convert must support seeking.</span></span> <span data-ttu-id="cf27b-121">Aby uzyskać więcej informacji, zobacz <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cf27b-121">For more information, see the <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cf27b-122">Ten interfejs API jest obsługiwany w .NET Framework 4.5.1 i nowszymi wersjami, ale nie w wersji 4.5.</span><span class="sxs-lookup"><span data-stu-id="cf27b-122">This API is supported in the .NET Framework 4.5.1 and later versions, but not in version 4.5.</span></span>

## <a name="version-information"></a><span data-ttu-id="cf27b-123">Informacje o wersji</span><span class="sxs-lookup"><span data-stu-id="cf27b-123">Version Information</span></span>

<span data-ttu-id="cf27b-124">**Platforma .NET dla aplikacji Windows Store**</span><span class="sxs-lookup"><span data-stu-id="cf27b-124">**.NET for Windows Store apps**</span></span>

<span data-ttu-id="cf27b-125">Obsługiwane w: Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="cf27b-125">Supported in: Windows 8.1</span></span>

## <a name="see-also"></a><span data-ttu-id="cf27b-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf27b-126">See also</span></span>

<span data-ttu-id="cf27b-127">-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[porady: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego Windows](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span><span class="sxs-lookup"><span data-stu-id="cf27b-127">-[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)
-[How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)</span></span>
