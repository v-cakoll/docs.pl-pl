---
title: Dostosowywanie organizowania struktury — .NET
description: Dowiedz się, jak dostosować sposób organizowania struktur przez platformę .NET do reprezentacji macierzystej.
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 7f8d1ad93633d6feef9c3c6f5d19aad52105968c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400373"
---
# <a name="customizing-structure-marshaling"></a>Dostosowywanie marshalingu struktur

Czasami domyślne reguły organizowania struktur nie są dokładnie tym, czego potrzebujesz. Środowiska uruchomieniowe .NET zapewniają kilka punktów rozszerzenia, aby dostosować układ struktury i sposób organizowania pól.

## <a name="customizing-structure-layout"></a>Dostosowywanie układu struktury

.NET udostępnia <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atrybut <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> i wyliczenie, aby umożliwić dostosowanie sposobu umieszczania pól w pamięci. Poniższe wskazówki pomogą Ci uniknąć typowych problemów.

✔️ ROZWAŻ `LayoutKind.Sequential` UŻYCIE, gdy tylko jest to możliwe.

✔️ do `LayoutKind.Explicit` tylko używać w organizowaniu, gdy natywna struktura ma również jawny układ, takich jak unii.

❌Unikaj `LayoutKind.Explicit` używania podczas organizowania struktur na platformach innych niż Windows, jeśli trzeba kierować środowiska uruchomieniowe przed .NET Core 3.0. Środowisko uruchomieniowe .NET Core przed 3.0 nie obsługuje przekazywania jawnych struktur według wartości do funkcji natywnych w 64-bitowych systemach innych niż Windows firmy Intel lub AMD. Jednak czas wykonywania obsługuje przekazywanie jawne struktury przez odwołanie na wszystkich platformach.

## <a name="customizing-boolean-field-marshaling"></a>Dostosowywanie kierowanie pól logicznych

Kod macierzysty ma wiele różnych reprezentacji logicznych. W samym systemie Windows istnieją trzy sposoby reprezentowania wartości logicznych. Czas wykonywania nie zna natywnej definicji struktury, więc najlepiej można zrobić, to odgadnąć, jak zorganizować wartości logiczne. Program runtime .NET umożliwia wskazanie sposobu organizowania pola logicznego. W poniższych przykładach przedstawiono `bool` sposób organizowania .NET do różnych typów natywnych logicznych.

Wartości logiczne domyślnie do organizowania jako natywna 4-bajtowa wartość Win32, [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) jak pokazano w poniższym przykładzie:

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

Jeśli chcesz mieć jawne, można <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> użyć wartości, aby uzyskać takie samo zachowanie jak powyżej:

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

Za `UnmanagedType.U1` pomocą `UnmanagedType.I1` lub wartości poniżej, można powiedzieć, `b` w czasie wykonywania `bool` do organizowania pola jako typ macierzysty 1-bajtowy.

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

W systemie Windows można <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> użyć tej wartości, aby poinformować środowisko uruchomieniowe, aby zorganizować wartość logiczną do wartości 2-bajtowej: `VARIANT_BOOL`

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
> `VARIANT_BOOL`różni się od większości typów `VARIANT_TRUE = -1` `VARIANT_FALSE = 0`bool w tym i . Ponadto wszystkie wartości, które nie `VARIANT_TRUE` są równe są uważane za false.

## <a name="customizing-array-field-marshaling"></a>Dostosowywanie organizowania pól tablicy

.NET zawiera również kilka sposobów dostosowywania organizowania tablicy.

Domyślnie .NET organizuje tablice jako wskaźnik do ciągłej listy elementów:

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

Jeśli łączysz się z interfejsami API COM, `SAFEARRAY*` może być trzeba zorganizować tablice jako obiekty. Można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> i wartość, aby poinformować program runtime `SAFEARRAY*`do organizowania tablicy jako:

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

Jeśli chcesz dostosować typ elementu w `SAFEARRAY`, następnie można <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> i pola, aby dostosować `SAFEARRAY`dokładny typ elementu .

Jeśli trzeba zorganizować tablicy w miejscu, można <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> użyć wartości, aby poinformować organizatora do organizowania tablicy w miejscu. Korzystając z tego organizowania, należy również podać <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> wartość do pola dla liczby elementów w tablicy, dzięki czemu czas wykonywania można poprawnie przydzielić miejsce dla struktury.

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
> .NET nie obsługuje organizowania pola tablicy o zmiennej długości jako członka tablicy elastycznej C99.

## <a name="customizing-string-field-marshaling"></a>Dostosowywanie organizowania pól ciągów

.NET udostępnia również szeroką gamę dostosowań dla organizowania pól ciągów.

Domyślnie .NET organizuje ciąg jako wskaźnik do ciągu zakończonego zerem. Kodowanie zależy od wartości <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>pliku . Jeśli nie określono żadnego atrybutu, kodowanie domyślnie koduje ANSI.

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

Jeśli chcesz użyć różnych kodowania dla różnych pól lub po prostu wolą być bardziej jawne <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> definicji struktury, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub wartości na atrybut.

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

Jeśli chcesz zorganizować ciągi przy użyciu kodowania UTF-8, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute>wartości w pliku .

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
> Korzystanie <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga .NET Framework 4.7 (lub nowszych wersji) lub .NET Core 1.1 (lub nowszych wersjach). Nie jest dostępna w .NET Standard 2.0.

Jeśli pracujesz z interfejsami API COM, może `BSTR`być konieczne zorganizowanie ciągu jako pliku . Za <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> pomocą wartości można zorganizować ciąg `BSTR`jako .

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

Korzystając z interfejsu API opartego na winrt, może `HSTRING`być konieczne zorganizowanie ciągu jako .  Za <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> pomocą wartości można zorganizować ciąg `HSTRING`jako .

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

Jeśli interfejs API wymaga przekazania ciągu w miejscu w strukturze, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> wartości. Należy pamiętać, że kodowanie ciągu `ByValTStr` organizowane przez `CharSet` jest określana na podstawie atrybutu. Ponadto wymaga, aby długość ciągu jest <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> przekazywana przez pole.

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

Jeśli pracujesz w systemie Windows, może wystąpić niektóre [ `CY` `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) interfejsy API, które używają natywnych lub struktury. Domyślnie typ .NET `decimal` organizuje do [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) struktury macierzystej. Jednak można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> a <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> z wartością, aby poinstruować organizatora, aby przekonwertować `decimal` wartość na wartość natywną. `CY`

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

W systemie Windows `object`można zorganizować pola wpisane do kodu macierzystego. Te pola można zorganizować na jeden z trzech typów:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Domyślnie pole `object`wpisane na maszynę `IUnknown*` będzie organizowane w obiekcie, które otacza obiekt.

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

Jeśli chcesz zorganizować pole obiektu `IDispatch*`do , <xref:System.Runtime.InteropServices.MarshalAsAttribute> dodaj <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> a z wartością.

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

Jeśli chcesz zorganizować go `VARIANT`jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> dodaj <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> a z wartością.

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

W poniższej tabeli opisano, `obj` jak różne typy czasu wykonywania mapy pola do różnych typów przechowywanych `VARIANT`w:

| Typ .NET | Typ WARIANTU | | Typ .NET | Typ WARIANTU |
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
