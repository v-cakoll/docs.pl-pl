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
ms.openlocfilehash: d3167abd0c263a0a27573778d6f243bc824306a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71051684"
---
# <a name="marshaling-data-with-platform-invoke"></a>Organizowanie danych w wywołaniu platformy

Aby wywoływać funkcje wyeksportowane z biblioteki niezarządzanej, aplikacja .NET Framework wymaga prototypu funkcji w zarządzanym kodzie, który reprezentuje niezarządzaną funkcję. Aby utworzyć prototyp umożliwiający poprawne kierowanie danych przez wywołanie platformy, należy wykonać następujące czynności:

- <xref:System.Runtime.InteropServices.DllImportAttribute> Zastosuj atrybut do statycznej funkcji lub metody w kodzie zarządzanym.

- Podstawianie typów danych zarządzanych dla niezarządzanych typów danych.

Korzystając z dokumentacji dostarczonej z niezarządzaną funkcją, można utworzyć odpowiedni prototyp zarządzany przez zastosowanie atrybutu z opcjonalnymi polami i podstawianie typów danych zarządzanych dla typów niezarządzanych. Aby uzyskać instrukcje dotyczące sposobu zastosowania, <xref:System.Runtime.InteropServices.DllImportAttribute>zobacz Korzystanie z [niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md).

Ta sekcja zawiera przykłady, które pokazują, jak utworzyć prototypy funkcji zarządzanych do przekazywania argumentów do i otrzymywania wartości zwracanych z funkcji wyeksportowanych przez biblioteki niezarządzane. Przykłady pokazują również, kiedy używać <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu <xref:System.Runtime.InteropServices.Marshal> i klasy, aby jawnie zorganizować dane.

## <a name="platform-invoke-data-types"></a>Typy danych wywołania platformy

Poniższa tabela zawiera listę typów danych używanych w interfejsach API systemu Windows i w funkcjach w stylu języka C. Wiele bibliotek niezarządzanych zawiera funkcje, które przekazują te typy danych jako parametry i wartości zwracane. Trzecia kolumna zawiera listę odpowiednich .NET Framework wbudowanego typu wartości lub klasy, które są używane w kodzie zarządzanym. W niektórych przypadkach można zastąpić typ o takim samym rozmiarze dla typu wymienionego w tabeli.

|Typ niezarządzany w interfejsach API systemu Windows|Niezarządzany typ języka C|Typ zarządzany|Opis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Zastosowano do funkcji, która nie zwraca wartości.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> lub <xref:System.UIntPtr?displayProperty=nameWithType>|32 bitów w 32-bitowych systemach operacyjnych Windows, 64 BITS w systemach operacyjnych Windows w 64-bitowym.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bitów|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitów|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bitów|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> lub <xref:System.Int32?displayProperty=nameWithType>|32 bitów|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitów|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bitów|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Dekorować z ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Dekorować z kodowaniem Unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekorować z ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekorować z ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekorować z kodowaniem Unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekorować z kodowaniem Unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bitów|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bitów|

Dla odpowiednich typów w Visual Basic, C#i C++, zobacz [wprowadzenie do biblioteki klas .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Poniższy kod definiuje funkcje biblioteki udostępniane przez PInvoke. dll. Wiele przykładów opisanych w tej sekcji wywołuje tę bibliotekę.

### <a name="example"></a>Przykład

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
