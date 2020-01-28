---
title: Dostosowywanie organizowania struktury — .NET
description: Dowiedz się, jak dostosować platformę .NET do organizowania struktur w natywną reprezentację.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741535"
---
# <a name="customizing-structure-marshaling"></a>Dostosowywanie marshalingu struktur

Czasami domyślne reguły organizowania dla struktur nie są dokładnie tym, czego potrzebujesz. Środowiska uruchomieniowe platformy .NET udostępniają kilka punktów rozszerzenia, które umożliwiają dostosowanie układu struktury i sposobu organizowania pól.

## <a name="customizing-structure-layout"></a>Dostosowywanie układu struktury

Platforma .NET udostępnia atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> i Wyliczenie <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType>, aby umożliwić dostosowywanie sposobu umieszczania pól w pamięci. Poniższe wskazówki pomogą uniknąć typowych problemów.

✔️ ROZWAŻYĆ użycie `LayoutKind.Sequential`, gdy jest to możliwe.

✔️ używać `LayoutKind.Explicit` podczas organizowania, gdy struktura natywna również ma jawny układ, taki jak Unia.

❌ UNIKAj używania `LayoutKind.Explicit` podczas organizowania struktur na platformach innych niż Windows, jeśli chcesz, aby docelowe środowiska uruchomieniowe przed platformą .NET Core 3,0. Środowisko uruchomieniowe platformy .NET Core przed 3,0 nie obsługuje przekazywania jawnych struktur przez wartość do funkcji natywnych w systemach Intel lub AMD 64-bitowym z systemem innym niż Windows. Jednak środowisko uruchomieniowe obsługuje przekazywanie jawnych struktur przez odwołanie na wszystkich platformach.

## <a name="customizing-boolean-field-marshaling"></a>Dostosowywanie kierowania pola logicznego

Kod natywny ma wiele różnych reprezentacji wartości logicznych. W systemie Windows, istnieją trzy sposoby reprezentowania wartości logicznych. Środowisko uruchomieniowe nie zna natywnej definicji struktury, dlatego najlepszym rozwiązaniem jest przypuszczenie metody organizowania wartości logicznych. Środowisko uruchomieniowe platformy .NET zapewnia sposób organizowania pola wartości logicznej. W poniższych przykładach pokazano, jak zorganizować platformę .NET `bool` do różnych natywnych typów logicznych.

Wartości logiczne są domyślnie organizowane jako natywne 4-bajtowe wartości [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) Win32, jak pokazano w następującym przykładzie:

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

Jeśli chcesz być jawnie, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType>, aby uzyskać takie samo zachowanie jak powyżej:

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

Korzystając z `UnmanagedType.U1` lub `UnmanagedType.I1` wartości poniżej, można poinstruować środowisko uruchomieniowe, aby zorganizować pole `b` jako typ 1-bajtowy `bool` natywny.

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

W systemie Windows można użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType>, aby określić, że środowisko uruchomieniowe ma kierować wartość logiczną do 2-bajtowej `VARIANT_BOOL` wartości:

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
> `VARIANT_BOOL` jest inna niż większość typów bool w tym `VARIANT_TRUE = -1` i `VARIANT_FALSE = 0`. Ponadto wszystkie wartości, które nie są równe `VARIANT_TRUE` są uważane za fałszywe.

## <a name="customizing-array-field-marshaling"></a>Dostosowywanie organizowania pól tablicy

Platforma .NET zawiera również kilka sposobów dostosowywania organizowania tablic.

Domyślnie program .NET kierowanie tablic jako wskaźnika do ciągłej listy elementów:

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

Jeśli korzystasz z interfejsów API modelu COM, może być konieczne kierowanie tablic jako obiektów `SAFEARRAY*`. Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> i wartości <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>, aby określić, że środowisko uruchomieniowe ma zorganizować tablicę jako `SAFEARRAY*`:

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

Jeśli musisz dostosować typ elementu do `SAFEARRAY`, możesz użyć pól <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> do dostosowania dokładnego typu elementu `SAFEARRAY`.

Jeśli musisz zorganizować tablicę w miejscu, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>, aby poinformować organizatora, aby zorganizować tablicę w miejscu. W przypadku korzystania z tego organizowania należy również podać wartość pola <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> dla liczby elementów w tablicy, aby środowisko uruchomieniowe prawidłowo przydzielić miejsce dla struktury.

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
> Platforma .NET nie obsługuje organizowania pola tablicy o zmiennej długości jako C99 elastycznej składowej tablicy.

## <a name="customizing-string-field-marshaling"></a>Dostosowywanie organizowania pól ciągów

Platforma .NET udostępnia również szeroką gamę dostosowań do organizowania pól ciągów.

Domyślnie program .NET kierujący ciąg jako wskaźnik do ciągu zakończonego wartością null. Kodowanie zależy od wartości pola <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>. Jeśli żaden atrybut nie jest określony, kodowanie jest domyślnie zgodne z kodowaniem ANSI.

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

Jeśli potrzebujesz użyć innych kodowań dla różnych pól lub wolisz bardziej jawnie w definicji struktury, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> w atrybucie <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.

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

Jeśli chcesz zorganizować ciągi przy użyciu kodowania UTF-8, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.MarshalAsAttribute>.

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
> Używanie <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga .NET Framework 4,7 (lub nowszych) lub .NET Core 1,1 (lub nowszych). Nie jest on dostępny w .NET Standard 2,0.

Jeśli pracujesz z interfejsami API modelu COM, może być konieczne przekierowanie ciągu jako `BSTR`. Korzystając z wartości <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, można zorganizować ciąg jako `BSTR`.

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

W przypadku korzystania z interfejsu API opartego na WinRT może być konieczne skierowanie ciągu jako `HSTRING`.  Korzystając z wartości <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, można zorganizować ciąg jako `HSTRING`.

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

Jeśli interfejs API wymaga przekazania ciągu w strukturze, można użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>. Należy pamiętać, że kodowanie dla ciągu organizowanego przez `ByValTStr` jest określane na podstawie atrybutu `CharSet`. Ponadto wymaga, aby długość ciągu była przenoszona przez pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.

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

## <a name="customizing-decimal-field-marshaling"></a>Dostosowywanie organizowania pól dziesiętnych

Jeśli pracujesz w systemie Windows, możesz napotkać niektóre interfejsy API, które używają natywnej struktury [`CY` lub `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) . Domyślnie typ `decimal` .NET kierowanie do struktury [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) natywnej. Można jednak użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType>, aby nakazać Organizatorowi przekonwertowanie wartości `decimal` na natywną wartość `CY`.

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

## <a name="marshaling-systemobjects"></a>Kierowanie `System.Object`s

W systemie Windows można organizować pola wpisywane `object`na kod natywny. Można kierować te pola do jednego z trzech typów:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Domyślnie pole o typie `object`będzie organizowane w `IUnknown*`, który zawija obiekt.

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

Jeśli chcesz zorganizować pole obiektu do `IDispatch*`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.

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

Jeśli chcesz zorganizować ją jako `VARIANT`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.

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

W poniższej tabeli opisano, jak różne typy środowiska uruchomieniowego `obj` mapowane na różne typy przechowywane w `VARIANT`:

| Typ .NET | Typ VARIANT | | Typ .NET | Typ VARIANT |
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
