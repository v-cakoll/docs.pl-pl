---
title: Organizowanie danych w wywołaniu platformy
ms.date: 03/20/2019
dev_langs:
- cpp
helpviewer_keywords:
- platform invoke, marshaling data
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: dc5c76cf-7b12-406f-b79c-d1a023ec245d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 396dc1dec60a6a984f9ddd0b8a8753b7293a5ab9
ms.sourcegitcommit: 77854e8704b9689b73103d691db34d71c2bf1dad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58307866"
---
# <a name="marshaling-data-with-platform-invoke"></a>Organizowanie danych w wywołaniu platformy

Aby wywołać funkcje wyeksportowane z biblioteką niezarządzaną, aplikacji programu .NET Framework wymaga prototypu funkcji w kodzie zarządzanym, reprezentujący funkcji niezarządzanej. Aby utworzyć prototypu, który umożliwia platformie wywołania do organizowania danych poprawnie, należy wykonać następujące czynności:

- Zastosuj <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu statycznej funkcji lub metody w kodzie zarządzanym.

- Zastąp typy zarządzanych danych dla niezarządzane typy danych.

Dokumentacja dostarczona z niezarządzanej funkcji służy do konstruowania równoważne prototypu zarządzanych przez stosowanie tego atrybutu z jej pól opcjonalnych i zastępując typy zarządzanych danych w przypadku niezarządzanych typów. Aby uzyskać instrukcje dotyczące sposobu stosowania **DllImportAttribute**, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).

Ta sekcja zawiera przykłady pokazujące, jak utworzyć prototypy funkcji zarządzanej przekazywanie argumentów do i odbierania wartości zwracanych z funkcji eksportowanych przez niezarządzanych bibliotek. Przykłady pokazują również użycie <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu i <xref:System.Runtime.InteropServices.Marshal> klasy, aby jawnie organizowania danych.

## <a name="platform-invoke-data-types"></a>Typy danych w wywołaniu platformy

Poniższa tabela zawiera listę typów danych używanych w funkcji stylu C i Win32 API (wymienione w Wtypes.h). Wiele niezarządzanych bibliotek zawierają funkcje, które przekazać te typy danych jako parametry i zwracane wartości. Trzecia kolumna wyświetla odpowiednie .NET Framework wbudowanym typie wartości lub klasy, których używasz w kodzie zarządzanym. W niektórych przypadkach można zastąpić typu tej samej wielkości dla typu wymienione w tabeli.

|Niezarządzany typ w Wtypes.h|Niezarządzany typ języka C|Nazwa typu zarządzanego|Opis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|**VOID**|**void**|<xref:System.Void?displayProperty=nameWithType>|Stosowane do funkcji, która nie zwraca wartości.|
|**UCHWYT**|**Void \***|<xref:System.IntPtr?displayProperty=nameWithType> lub <xref:System.UIntPtr?displayProperty=nameWithType>|32-bitowy na 32-bitowych systemach operacyjnych Windows, 64-bitowy na 64-bitowych systemach operacyjnych Windows.|
|**BAJTÓW**|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|
|**KRÓTKA**|**short**|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|
|**WORD**|**short bez znaku**|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|
|**INT**|**int**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|**UINT**|**unsigned int**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|**LONG**|**long**|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|**BOOL**|**long**|<xref:System.Boolean?displayProperty=nameWithType> lub <xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|**DWORD**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|**ULONG**|**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|**CHAR**|**char**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z ANSI.|
|**WCHAR**|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|**LPSTR**|**Char &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|
|**LPCSTR**|**Const char &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|
|**LPWSTR**|**wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|**LPCWSTR**|**Const wchar_t &ast;**|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|**FLOAT**|**float**|<xref:System.Single?displayProperty=nameWithType>|32-bitowy|
|**PODWÓJNE**|**double**|<xref:System.Double?displayProperty=nameWithType>|64-bitowy|

Dla odpowiednich typów w pakietach [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++, zobacz [wprowadzenie do biblioteki klas programu .NET Framework](../../../docs/standard/class-library-overview.md).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Poniższy kod definiuje dostępne Pinvoke.dll funkcje biblioteki. Wiele przykładów opisane w tym wywołaniu sekcji tej biblioteki.

### <a name="example"></a>Przykład

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
