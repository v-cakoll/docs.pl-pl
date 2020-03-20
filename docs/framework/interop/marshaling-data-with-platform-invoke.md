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
ms.openlocfilehash: b8c4e9d835db044912d1cbed92a14dd05e7de658
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399939"
---
# <a name="marshaling-data-with-platform-invoke"></a>Organizowanie danych w wywołaniu platformy

Aby wywołać funkcje eksportowane z biblioteki niezarządzanej, aplikacja .NET Framework wymaga prototypu funkcji w kodzie zarządzanym, który reprezentuje funkcję niezarządzaną. Aby utworzyć prototyp, który umożliwia platformie wywołać do danych marshal poprawnie, należy wykonać następujące czynności:

- Zastosuj <xref:System.Runtime.InteropServices.DllImportAttribute> atrybut do funkcji statycznej lub metody w kodzie zarządzanym.

- Zastąp typy danych zarządzanych dla niezarządzanych typów danych.

Można użyć dokumentacji dostarczonej z funkcją niezarządzaną do konstruowania równoważnego zarządzanego prototypu przez zastosowanie atrybutu z jego opcjonalnymi polami i zastąpienie typów danych zarządzanych dla typów niezarządzanych. Aby uzyskać instrukcje dotyczące <xref:System.Runtime.InteropServices.DllImportAttribute>stosowania funkcji DLL w sposób , zobacz [Korzystanie z funkcji biblioteki DLL niezarządzanej](consuming-unmanaged-dll-functions.md).

Ta sekcja zawiera przykłady, które pokazują, jak utworzyć prototypy funkcji zarządzanych do przekazywania argumentów do i odbierania wartości zwracanych z funkcji eksportowanych przez biblioteki niezarządzane. Przykłady również wykazać, kiedy <xref:System.Runtime.InteropServices.MarshalAsAttribute> należy użyć <xref:System.Runtime.InteropServices.Marshal> atrybutu i klasy jawnie marshal danych.

## <a name="platform-invoke-data-types"></a>Platforma wywołuje typy danych

W poniższej tabeli wymieniono typy danych używane w interfejsach API systemu Windows i funkcjach w stylu C. Wiele bibliotek niezarządzanych zawiera funkcje, które przekazują te typy danych jako parametry i zwracają wartości. Trzecia kolumna zawiera listę odpowiedniego typu wartości wbudowanej programu .NET Framework lub klasy używanej w kodzie zarządzanym. W niektórych przypadkach można zastąpić typ tego samego rozmiaru typem wymienionym w tabeli.

|Typ niezarządzany w interfejsach API systemu Windows|Niezarządzany typ języka C|Typ zarządzany|Opis|
|--------------------------------|-------------------------------|------------------------|-----------------|
|`VOID`|`void`|<xref:System.Void?displayProperty=nameWithType>|Zastosowane do funkcji, która nie zwraca wartości.|
|`HANDLE`|`void *`|<xref:System.IntPtr?displayProperty=nameWithType> lub <xref:System.UIntPtr?displayProperty=nameWithType>|32 bity na 32-bitowych systemach operacyjnych Windows, 64 bity w 64-bitowych systemach operacyjnych Windows.|
|`BYTE`|`unsigned char`|<xref:System.Byte?displayProperty=nameWithType>|8 bitów|
|`SHORT`|`short`|<xref:System.Int16?displayProperty=nameWithType>|16 bitów|
|`WORD`|`unsigned short`|<xref:System.UInt16?displayProperty=nameWithType>|16 bitów|
|`INT`|`int`|<xref:System.Int32?displayProperty=nameWithType>|32 bity|
|`UINT`|`unsigned int`|<xref:System.UInt32?displayProperty=nameWithType>|32 bity|
|`LONG`|`long`|<xref:System.Int32?displayProperty=nameWithType>|32 bity|
|`BOOL`|`long`|<xref:System.Boolean?displayProperty=nameWithType> lub <xref:System.Int32?displayProperty=nameWithType>|32 bity|
|`DWORD`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bity|
|`ULONG`|`unsigned long`|<xref:System.UInt32?displayProperty=nameWithType>|32 bity|
|`CHAR`|`char`|<xref:System.Char?displayProperty=nameWithType>|Udekoruj ANSI.|
|`WCHAR`|`wchar_t`|<xref:System.Char?displayProperty=nameWithType>|Udekoruj unicode.|
|`LPSTR`|`char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Udekoruj ANSI.|
|`LPCSTR`|`const char *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Udekoruj ANSI.|
|`LPWSTR`|`wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Udekoruj unicode.|
|`LPCWSTR`|`const wchar_t *`|<xref:System.String?displayProperty=nameWithType> lub <xref:System.Text.StringBuilder?displayProperty=nameWithType>|Udekoruj unicode.|
|`FLOAT`|`float`|<xref:System.Single?displayProperty=nameWithType>|32 bity|
|`DOUBLE`|`double`|<xref:System.Double?displayProperty=nameWithType>|64 bity|

Dla odpowiednich typów w językach Visual Basic, C#i C++, zobacz [wprowadzenie do biblioteki klas .NET Framework](../../standard/class-library-overview.md#system-namespace).

## <a name="pinvokelibdll"></a>PinvokeLib.dll

Poniższy kod definiuje funkcje biblioteki dostarczone przez pinvoke.dll. Wiele przykładów opisanych w tej sekcji wywołać tej biblioteki.

### <a name="example"></a>Przykład

[!code-cpp[PInvokeLib#1](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.cpp#1)]

[!code-cpp[PInvokeLib#2](../../../samples/snippets/cpp/VS_Snippets_CLR/pinvokelib/cpp/pinvokelib.h#2)]
