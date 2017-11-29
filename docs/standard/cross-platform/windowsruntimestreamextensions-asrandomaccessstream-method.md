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
# <a name="windowsruntimestreamextensionsasrandomaccessstreamsystemiostream-method"></a>WindowsRuntimeStreamExtensions.AsRandomAccessStream(System.IO.Stream) — Metoda
[Obsługiwane w programie .NET Framework 4.5.1 i nowszych wersjach]  
  
 Konwertuje określony strumień na strumień o dostępie losowym.  
  
 **Namespace:**<xref:System.IO?displayProperty=nameWithType>  
 **Zestaw:** System.Runtime.WindowsRuntime (w System.Runtime.WindowsRuntime.dll)  
  
## <a name="syntax"></a>Składnia  
  
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
  
#### <a name="parameters"></a>Parametry  
 `stream`  
  
 Typ:<xref:System.IO.Stream?displayProperty=nameWithType>  
Strumień do przekonwertowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 Typ: [Windows.Storage.Streams.RandomAccessStream](http://msdn.microsoft.com/library/windows/apps/windows.storage.streams.randomaccessstream.aspx)  
A [!INCLUDE[wrt](../../../includes/wrt-md.md)] dostępie swobodnym strumienia, reprezentujący skonwertowany strumienia.  
  
## <a name="exceptions"></a>Wyjątki  
  
|Wyjątek|Warunek|  
|---------------|---------------|  
|<xref:System.NotSupportedException>|Strumień, który ma zostać przekonwertowany, nie obsługuje wyszukiwania.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda rozszerzenia jest dostępna tylko podczas projektowania aplikacji do Sklepu Windows. Ta metoda oferuje wygodny sposób pracy ze strumieniami w aplikacjach do Sklepu Windows. W strumieniu .NET Framework, który ma zostać przekonwertowany musi obsługiwać operacji wyszukiwania. Aby uzyskać więcej informacji, zobacz <xref:System.IO.Stream.Seek%2A?displayProperty=nameWithType> metody.  
  
> [!IMPORTANT]
>  Ten interfejs API jest obsługiwany w .NET Framework 4.5.1 lub nowszy, ale nie w wersji 4.5.  
  
## <a name="version-information"></a>Informacje o wersji  
 **Platforma .NET dla aplikacji ze Sklepu Windows**  
  
 Obsługiwane w: Windows 8.1  
  
## <a name="see-also"></a>Zobacz też  
 <!--zz <xref:System.IO.WindowsRuntimeStreamExtensions>--> `System.IO.WindowsRuntimeStreamExtensions`  
 [Porady: konwertowanie między .NET Framework i strumieni środowiska wykonawczego systemu Windows](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)
