---
title: Marshaling danych w wywołaniu platformy
ms.date: 07/31/2018
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae8fbb47986e5baaecb919ce79ae384a8427737a
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45646301"
---
# <a name="marshaling-data-with-platform-invoke"></a>Marshaling danych w wywołaniu platformy
Aby wywołać funkcje wyeksportowane z biblioteką niezarządzaną, aplikacji programu .NET Framework wymaga prototypu funkcji w kodzie zarządzanym, reprezentujący funkcji niezarządzanej. Aby utworzyć prototypu, który umożliwia platformie wywołania do organizowania danych poprawnie, należy wykonać następujące czynności:  
  
-   Zastosuj <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu statycznej funkcji lub metody w kodzie zarządzanym.  
  
-   Zastąp typy zarządzanych danych dla niezarządzane typy danych.  
  
 Dokumentacja dostarczona z niezarządzanej funkcji służy do konstruowania równoważne prototypu zarządzanych przez stosowanie tego atrybutu z jej pól opcjonalnych i zastępując typy zarządzanych danych w przypadku niezarządzanych typów. Aby uzyskać instrukcje dotyczące sposobu stosowania **DllImportAttribute**, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).  
  
 Ta sekcja zawiera przykłady pokazujące, jak utworzyć prototypy funkcji zarządzanej przekazywanie argumentów do i odbierania wartości zwracanych z funkcji eksportowanych przez niezarządzanych bibliotek. Przykłady pokazują również użycie <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu i <xref:System.Runtime.InteropServices.Marshal> klasy, aby jawnie organizowania danych.  
  
## <a name="platform-invoke-data-types"></a>Typy danych w wywołaniu platformy  
 Poniższa tabela zawiera listę typów danych używanych w funkcji stylu C i Win32 API (wymienione w Wtypes.h). Wiele niezarządzanych bibliotek zawierają funkcje, które przekazać te typy danych jako parametry i zwracane wartości. Trzecia kolumna wyświetla odpowiednie .NET Framework wbudowanym typie wartości lub klasy, których używasz w kodzie zarządzanym. W niektórych przypadkach można zastąpić typu tej samej wielkości dla typu wymienione w tabeli.  
  
|Niezarządzany typ w Wtypes.h|Niezarządzany typ języka C|Nazwa klasy zarządzanej|Opis|  
|--------------------------------|-------------------------------|------------------------|-----------------|  
|**VOID**|**void**|<xref:System.Void?displayProperty=nameWithType>|Stosowane do funkcji, która nie zwraca wartości.|
|**UCHWYT**|**Void \***|<xref:System.IntPtr?displayProperty=nameWithType>|32-bitowy na 32-bitowych systemach operacyjnych Windows, 64-bitowy na 64-bitowych systemach operacyjnych Windows.|  
|**BAJTÓW**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|  
|**KRÓTKA**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|  
|**WORD**|**short bez znaku**|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|  
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|  
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**DŁUGI**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|  
|**BOOL**|**long**|<xref:System.Byte>|32-bitowy|  
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|  
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|  
|**LPSTR**|**Char &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**LPCSTR**|**Const char &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|  
|**LPWSTR**|**wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|  
|**LPCWSTR**|**Const wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|  
|**FLOAT**|**float**|<xref:System.Single?displayProperty=nameWithType>|32-bitowy|  
|**PODWÓJNE**|**Double**|<xref:System.Double?displayProperty=nameWithType>|64-bitowy|  
  
 Dla odpowiednich typów w pakietach [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++, zobacz [wprowadzenie do biblioteki klas programu .NET Framework](../../../docs/standard/class-library-overview.md).  
  
## <a name="pinvokelibdll"></a>PinvokeLib.dll  
 Poniższy kod definiuje dostępne Pinvoke.dll funkcje biblioteki. Wiele przykładów opisane w tym wywołaniu sekcji tej biblioteki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]  
  
 [!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
