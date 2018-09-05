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
ms.openlocfilehash: a712414163446606cbc93154bc821d3b1166fe8f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561799"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda

[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]

Konwertuje określony strumień na strumień o dostępie losowym.

**Namespace:** <xref:System.IO?displayProperty=nameWithType> 
 **zestawu:** System.Runtime.WindowsRuntime (w pliku System.Runtime.WindowsRuntime.dll)

## <a name="syntax"></a>Składnia

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

## <a name="parameters"></a>Parametry

`stream`

Typ: <xref:System.IO.Stream?displayProperty=nameWithType>  
Strumień do przekonwertowania.

## <a name="return-value"></a>Wartość zwracana

Typ: <xref:Windows.Storage.Streams.RandomAccessStream>  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] strumienia dostępu losowego, który reprezentujący przekonwertowany strumień.

## <a name="exceptions"></a>Wyjątki

|Wyjątek|Warunek|
|---------------|---------------|
|<xref:System.NotSupportedException>|Strumień, który ma zostać przekonwertowany, nie obsługuje wyszukiwania.|

## <a name="remarks"></a>Uwagi

Ta metoda rozszerzenia jest dostępna tylko podczas projektowania aplikacji do Sklepu Windows. Ta metoda oferuje wygodny sposób pracy ze strumieniami w aplikacjach do Sklepu Windows. Strumień programu .NET Framework, który ma zostać przekonwertowany, musi obsługiwać wyszukiwanie. Aby uzyskać więcej informacji, zobacz <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.

> [!IMPORTANT]
> Ten interfejs API jest obsługiwany w .NET Framework 4.5.1 i nowszymi wersjami, ale nie w wersji 4.5.

## <a name="version-information"></a>Informacje o wersji

**Platforma .NET dla aplikacji Windows Store**

Obsługiwane w: Windows 8.1

## <a name="see-also"></a>Zobacz też

[System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions(v=vs.110).aspx)  
[Instrukcje: konwersja strumieni platformy .NET Framework i strumieni środowiska wykonawczego systemu Windows](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  