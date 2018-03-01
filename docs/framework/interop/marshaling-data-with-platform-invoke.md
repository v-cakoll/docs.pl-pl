---
title: "Marshaling danych w wywołaniu platformy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 24ae6da0b32cf15ee9104bd10ba5fe6bb03a9763
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-data-with-platform-invoke"></a>Marshaling danych w wywołaniu platformy
Aby wywoływać funkcje wyeksportowane z biblioteki niezarządzane, aplikacji programu .NET Framework wymaga prototypu funkcji w kodzie zarządzanym, który reprezentuje niezarządzanej funkcji. Aby utworzyć prototyp, który umożliwia platformie wywołania do organizowania danych prawidłowo, należy wykonać następujące czynności:  
  
-   Zastosuj <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu statycznej funkcji lub metody w kodzie zarządzanym.  
  
-   Zastąp typy zarządzanych danych dla typów danych niezarządzane.  
  
 Dokumentacja dostarczona z niezarządzanej funkcji służy do utworzenia równoważne prototypu zarządzanych przez zastosowanie atrybutu o swoich pól opcjonalnych i podstawiając typy zarządzanych danych dla typów niezarządzane. Aby uzyskać instrukcje dotyczące sposobu stosowania **elementu DllImportAttribute**, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Ta sekcja zawiera przykłady, które pokazują, jak utworzyć prototypy funkcji zarządzanego przekazywanie argumentów i odbierania wartości zwracanych z funkcje wyeksportowane przez niezarządzanych bibliotek. Przykłady pokazują także kiedy należy używać <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu i <xref:System.Runtime.InteropServices.Marshal> klasy do jawnie organizowania danych.  
  
## <a name="platform-invoke-data-types"></a>Typy danych wywołanie platformy  
 W poniższej tabeli wymieniono typy danych używanych do interfejsu API systemu Win32 (wymienione w Wtypes.h) i funkcje w stylu języka C. Wiele niezarządzanych bibliotek zawiera funkcje, które są przekazywane jako parametry te typy danych i wartości zwracane. Trzecia kolumna zawiera listę odpowiedni typ wartości wbudowanych .NET Framework lub klasy używanej w kodzie zarządzanym. W niektórych przypadkach można zastąpić typu tego samego rozmiaru dla typu wymienione w tabeli.  
  
|Typ niezarządzany w Wtypes.h|Niezarządzany typ języka C|Nazwa klasy zarządzane|Opis|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**DOJŚCIE**|**void\***|<xref:System.IntPtr?displayProperty=nameWithType>|32-bitowy na 32-bitowego systemu operacyjnego, 64-bitowy na 64-bitowych systemach operacyjnych Windows.|  
|**BAJTÓW**|**char bez znaku**|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|  
|**KRÓTKI**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|  
|**WORD**|**short bez znaku**|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**DŁUGA**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|  
|**WARTOŚĆ LOGICZNA**|**long**|<xref:System.Byte>|32-bitowy|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji ze standardem Unicode.|  
|**LPSTR**|**char\***|<xref:System.String?displayProperty=nameWithType>lub<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**LPCSTR**|**Const char\***|<xref:System.String?displayProperty=nameWithType>lub<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**LPWSTR**|**wchar_t\***|<xref:System.String?displayProperty=nameWithType>lub<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji ze standardem Unicode.|  
|**LPCWSTR**|**Const wchar_t\***|<xref:System.String?displayProperty=nameWithType>lub<xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji ze standardem Unicode.|  
|**FLOAT**|**Float**|<xref:System.Single?displayProperty=nameWithType>|32-bitowy|  
|**O PODWÓJNEJ PRECYZJI**|**O podwójnej precyzji**|<xref:System.Double?displayProperty=nameWithType>|64-bitowy|  
  
 Dla odpowiednich typów w [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++, zobacz [wprowadzenie do Biblioteka klas programu .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Poniższy kod definiuje dostępne Pinvoke.dll funkcje biblioteki. Wiele próbek opisane w tej sekcji wywołania tej biblioteki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
