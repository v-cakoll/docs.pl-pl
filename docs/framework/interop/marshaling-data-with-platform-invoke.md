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
ms.openlocfilehash: 3cb310dc6d786c3c7711f4c194c6623324c777dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642870"
---
# <a name="marshaling-data-with-platform-invoke"></a>Organizowanie danych w wywołaniu platformy

Aby wywołać funkcje wyeksportowane z biblioteką niezarządzaną, aplikacji programu .NET Framework wymaga prototypu funkcji w kodzie zarządzanym, reprezentujący funkcji niezarządzanej. Aby utworzyć prototypu, który umożliwia platformie wywołania do organizowania danych poprawnie, należy wykonać następujące czynności:

- Zastosuj <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu statycznej funkcji lub metody w kodzie zarządzanym.

- Zastąp typy zarządzanych danych dla niezarządzane typy danych.

Dokumentacja dostarczona z niezarządzanej funkcji służy do konstruowania równoważne prototypu zarządzanych przez stosowanie tego atrybutu z jej pól opcjonalnych i zastępując typy zarządzanych danych w przypadku niezarządzanych typów. Aby uzyskać instrukcje dotyczące sposobu stosowania <xref:System.Runtime.InteropServices.DllImportAttribute>, zobacz [wykorzystywanie niezarządzanych funkcji DLL](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md).

Ta sekcja zawiera przykłady pokazujące, jak utworzyć prototypy funkcji zarządzanej przekazywanie argumentów do i odbierania wartości zwracanych z funkcji eksportowanych przez niezarządzanych bibliotek. Przykłady pokazują również użycie <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu i <xref:System.Runtime.InteropServices.Marshal> klasy, aby jawnie organizowania danych.

## <a name="platform-invoke-data-types"></a>Typy danych w wywołaniu platformy

W poniższej tabeli wymieniono typy danych używany w funkcji stylu C i interfejsów API Windows. Wiele niezarządzanych bibliotek zawierają funkcje, które przekazać te typy danych jako parametry i zwracane wartości. Trzecia kolumna wyświetla odpowiednie .NET Framework wbudowanym typie wartości lub klasy, których używasz w kodzie zarządzanym. W niektórych przypadkach można zastąpić typu tej samej wielkości dla typu wymienione w tabeli.

|Niezarządzany typ w interfejsach API Windows|Niezarządzany typ języka C|Typ zarządzany|Opis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Stosowane do funkcji, która nie zwraca wartości.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> lub <xref:System.UIntPtr?displayProperty=nameWithType>|32-bitowy na 32-bitowych systemach operacyjnych Windows, 64-bitowy na 64-bitowych systemach operacyjnych Windows.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> lub <xref:System.Int32?displayProperty=nameWithType>|32-bitowy|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32-bitowy|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Dekoracji z użyciem standardu Unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32-bitowy|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64-bitowy|

Dla odpowiadające typy w języku Visual Basic C#i C++, zobacz [wprowadzenie do biblioteki klas programu .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Poniższy kod definiuje dostępne Pinvoke.dll funkcje biblioteki. Wiele przykładów opisane w tym wywołaniu sekcji tej biblioteki.

### <a name="example"></a>Przykład

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
