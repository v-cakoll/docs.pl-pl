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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921319"
---
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda

[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]

Konwertuje określony strumień na strumień o dostępie losowym.

**Namespace:** <xref:System.IO?displayProperty=nameWithType>
**Zestaw:** System.Runtime.WindowsRuntime (in System.Runtime.WindowsRuntime.dll)

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

Obsługują: Windows 8.1

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Konwertowanie między .NET Framework i strumieni środowiska wykonawczego Windows](../io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
