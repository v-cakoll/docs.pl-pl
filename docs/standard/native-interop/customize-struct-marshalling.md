---
title: Dostosowywanie struktury kierowania — .NET
description: Dowiedz się, jak dostosować, jak .NET organizuje Twoje struktur natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b07851a0d26f5bfe7edc2115d7276a8e96ba0917
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973561"
---
# <a name="customizing-structure-marshalling"></a>Dostosowywanie struktury kierowania

Czasami kierujące reguły domyślne w strukturach nie są dokładnie potrzebnych składników. Środowiska uruchomieniowe platformy .NET zawierają kilka punktów rozszerzeń, którą można dostosować układ i jak pola są przekazywane do struktury.

## <a name="customizing-structure-layout"></a>Dostosowywanie układu struktury

.NET zapewnia <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atrybutu i <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> wyliczenie, aby możliwe było dostosować jak pola są umieszczane w pamięci. Poniższe wskazówki pomogą pozwala uniknąć typowych problemów.

**ROZWAŻ ✔️** przy użyciu `LayoutKind.Sequential` zawsze, gdy jest to możliwe.

**CZY ✔️** składać się tylko `LayoutKind.Explicit` organizowana po swojej natywnej struktury jest również ma układ jawny, na przykład Unii.

**Należy UNIKAĆ ❌** przy użyciu `LayoutKind.Explicit` podczas kierowania struktury na platformach innych niż Windows. Środowisko uruchomieniowe platformy .NET Core nie obsługuje przekazywanie struktury jawnej przez wartość do funkcji natywnych w systemach Intel lub AMD 64-bitowych inne niż Windows. Środowisko wykonawcze obsługuje jednak jawne przekazywanie struktury przez odniesienie na wszystkich platformach.

## <a name="customizing-boolean-field-marshalling"></a>Dostosowywanie pola logicznych kierowania

Kod natywny ma wiele różnych reprezentacji boolean. Na Windows samodzielnie istnieją trzy sposoby do reprezentowania wartości logiczne. Środowisko wykonawcze nie wiedzieć natywnych definicji struktury, dlatego najlepiej, co można zrobić zgadnąć na temat sposobu organizowania z wartościami logicznymi. Środowisko uruchomieniowe platformy .NET zapewnia sposób, aby wskazać sposób organizowania pola logicznych. W poniższych przykładach pokazano, jak kierować .NET `bool` na różnych typach boolean natywnych.

Atrybut typu wartość logiczna wartości domyślne do kierowania jako natywny Win32 4-bajtowych [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) wartość, jak pokazano w poniższym przykładzie:

```csharp
public struct WinBool
{
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

Jeśli chcesz mieć jawne, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> wartości, aby uzyskać takie samo zachowanie, jak powyżej:

```csharp
public struct WinBool
{
    [MarshalAs(UnmanagedType.Bool)]
    public bool b;
}
```

```cpp
struct WinBool
{
    public BOOL b;
};
```

Za pomocą `UnmanagedType.U1` lub `UnmanagedType.I1` poniższych wartości, możesz poinformować środowiska uruchomieniowego, aby zorganizować `b` pola jako natywny 1-bajtowe `bool` typu.

```csharp
public struct CBool
{
    [MarshalAs(UnmanagedType.U1)]
    public bool b;
}
```

```cpp
struct CBool
{
    public bool b;
};
```

Windows, mogą używać <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> wartość, aby poinformować środowiska uruchomieniowego do organizowania 2-bajtowych wartości logicznych `VARIANT_BOOL` wartość:

```csharp
public struct VariantBool
{
    [MarshalAs(UnmanagedType.VariantBool)]
    public bool b;
}
```

```cpp
struct VariantBool
{
    public VARIANT_BOOL b;
};
```

> [!NOTE]
> `VARIANT_BOOL` różni się od większości typów bool, w tym `VARIANT_TRUE = -1` i `VARIANT_FALSE = 0`. Ponadto wszystkie wartości, które nie są równe `VARIANT_TRUE` są traktowane jako wartość false.

## <a name="customizing-array-field-marshalling"></a>Dostosowywanie kierowania pola tablicy

.NET zawiera także kilka sposobów, aby dostosować kierowania tablicy.

Domyślnie .NET kieruje tablic jako wskaźnik do listy sąsiadujących elementów:

```csharp
public struct DefaultArray
{
    public int[] values;
}
```

```cpp
struct DefaultArray
{
    int* values;
};
```

Jeśli masz komunikowanie się z interfejsów API modelu COM, może być konieczne przeprowadzanie marshalingu tablic jako `SAFEARRAY*` obiektów. Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> wartość, aby poinformować środowiska uruchomieniowego, aby zorganizować tablicę jako `SAFEARRAY*`:

```csharp
public struct SafeArrayExample
{
    [MarshalAs(UnmanagedType.SafeArray)]
    public int[] values;
}
```

```cpp
struct SafeArrayExample
{
    SAFEARRAY* values;
};
```

Jeśli chcesz dostosować, jakiego rodzaju elementu jest w `SAFEARRAY`, wówczas można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> typu pola, aby dostosować element dokładnie `SAFEARRAY`.

Jeśli musisz kierować tablicy w miejscu, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> wartość, aby poinformować Organizator, aby zorganizować tablicę w miejscu. Podczas korzystania z tego kierowania, również należy podać wartość <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole Liczba elementów w tablicy, dzięki czemu środowisko uruchomieniowe poprawnie można przydzielić miejsca w strukturze.

```csharp
public struct InPlaceArray
{
    [MarshalAs(UnmanagedType.ByValArray, SizeConst = 4)]
    public int[] values;
}
```

```cpp
struct InPlaceArray
{
    int values[4];
};
```

> [!NOTE]
> .NET nie obsługuje kierowania pole o zmiennej długości tablicy jako składowej tablicowej z elastycznych C99.

## <a name="customizing-string-field-marshalling"></a>Dostosowywanie kierowania pola ciągu

.NET zapewnia także szeroką gamę dostosowania kierowania pól ciągów.

Domyślnie .NET kieruje ciąg jako wskaźnik na ciąg zakończony znakiem null. Kodowanie jest zależne od wartości <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>. Jeśli atrybut nie zostanie określony, kodowanie, wartość domyślna to kodowania ANSI.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char* str;
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Jeśli musisz używać różnych kodowań dla różnych pól lub po prostu chcesz być dokładniejsze w definicji struktury, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> wartości na <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu.

```csharp
public struct AnsiString
{
    [MarshalAs(UnmanagedType.LPStr)]
    public string str;
}
```

```cpp
struct AnsiString
{
    char* str;
};
```

```csharp
public struct UnicodeString
{
    [MarshalAs(UnmanagedType.LPWStr)]
    public string str;
}
```

```cpp
struct UnicodeString
{
    char16_t* str; // Could also be wchar_t* on Windows.
};
```

Jeśli chcesz kierować swoje ciągi przy użyciu kodowania UTF-8, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wartość w swojej <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

```csharp
public struct UTF8String
{
    [MarshalAs(UnmanagedType.LPUTF8Str)]
    public string str;
}
```

```cpp
struct UTF8String
{
    char* str;
};
```

> [!NOTE]
> Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga programu .NET Framework 4.7 (lub nowszy) lub .NET Core 1.1 (lub nowszy). Nie jest dostępne w programie .NET Standard 2.0.

Jeśli pracujesz z interfejsów API modelu COM, może być konieczne kierować ciąg w kodowaniu `BSTR`. Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> wartości, można kierować ciąg jako `BSTR`.

```csharp
public struct BString
{
    [MarshalAs(UnmanagedType.BStr)]
    public string str;
}
```

```cpp
struct BString
{
    BSTR str;
};
```

Korzystając z interfejsu API opartego na WinRT, konieczne może być kierować ciąg w kodowaniu `HSTRING`.  Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> wartości, można kierować ciąg jako `HSTRING`.

```csharp
public struct HString
{
    [MarshalAs(UnmanagedType.HString)]
    public string str;
}
```

```cpp
struct BString
{
    HSTRING str;
};
```

Jeśli Twój interfejs API wymaga przekazania parametrów w miejscu w strukturze, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> wartość. Należy pamiętać, że kodowanie ciągu skierowany przez `ByValTStr` jest określana na podstawie `CharSet` atrybutu. Ponadto wymaga ona, że długość ciągu jest przekazywany przez <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pola.

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char str[4];
};
```

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct DefaultString
{
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 4)]
    public string str;
}
```

```cpp
struct DefaultString
{
    char16_t str[4]; // Could also be wchar_t[4] on Windows.
};
```

## <a name="customizing-decimal-field-marshalling"></a>Dostosowywanie kierowania pola wartości dziesiętnej

Jeśli pracujesz w Windows, mogą wystąpić niektóre interfejsy API, używanego przez natywnych [ `CY` lub `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) struktury. Domyślnie .NET `decimal` wpisz marshals do natywnych [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) struktury. Można jednak użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> wartość, aby nakazać Organizator, aby przekonwertować `decimal` wartość do macierzystej `CY` wartość.

```csharp
public struct Currency
{
    [MarshalAs(UnmanagedType.Currency)]
    public decimal dec;
}
```

```cpp
struct Currency
{
    CY dec;
};
```

## <a name="marshalling-systemobjects"></a>Kierowania `System.Object`s

W Windows, może kierować element `object`-wpisane pola do kodu macierzystego. Można kierować te pola do jednego z trzech typów:
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Domyślnie `object`— pole wpisane, zostanie skierowany do `IUnknown*` która otacza obiekt.

```csharp
public struct ObjectDefault
{
    public object obj;
}
```

```cpp
struct ObjectDefault
{
    IUnknown* obj;
};
```

Jeśli chcesz kierować pola obiektu do `IDispatch*`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> wartości.

```csharp
public struct ObjectDispatch
{
    [MarshalAs(UnmanagedType.IDispatch)]
    public object obj;
}
```

```cpp
struct ObjectDispatch
{
    IDispatch* obj;
};
```

Jeśli chcesz kierować go jako `VARIANT`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> wartości.

```csharp
public struct ObjectVariant
{
    [MarshalAs(UnmanagedType.Struct)]
    public object obj;
}
```

```cpp
struct ObjectVariant
{
    VARIANT obj;
};
```

W poniższej tabeli opisano, jak różne typy środowiska uruchomieniowego `obj` mapowania pól do różnych typów, które są przechowywane w `VARIANT`:

| Typ architektury .NET | Typ VARIANT | | Typ architektury .NET | Typ VARIANT |
|------------|--------------|-|----------|--------------|
|  `byte`  | `VT_UI1` |     | `System.Runtime.InteropServices.BStrWrapper` | `VT_BSTR` |
| `sbyte`  | `VT_I1`  |     | `object`  | `VT_DISPATCH` |
| `short`  | `VT_I2`  |     | `System.Runtime.InteropServices.UnknownWrapper` | `VT_UNKNOWN` |
| `ushort` | `VT_UI2` |     | `System.Runtime.InteropServices.DispatchWrapper` | `VT_DISPATCH` |
| `int`    | `VT_I4`  |     | `System.Reflection.Missing` | `VT_ERROR` |
| `uint`   | `VT_UI4` |     | `(object)null` | `VT_EMPTY` |
| `long`   | `VT_I8`  |     | `bool` | `VT_BOOL` |
| `ulong`  | `VT_UI8` |     | `System.DateTime` | `VT_DATE` |
| `float`  | `VT_R4`  |     | `decimal` | `VT_DECIMAL` |
| `double` | `VT_R8`  |     | `System.Runtime.InteropServices.CurrencyWrapper` | `VT_CURRENCY` |
| `char`   | `VT_UI2` |     | `System.DBNull` | `VT_NULL` |
| `string` | `VT_BSTR`|
