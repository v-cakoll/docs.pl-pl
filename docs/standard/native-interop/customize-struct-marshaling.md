---
title: Dostosowywanie organizowania struktury — .NET
description: Dowiedz się, jak dostosować platformę .NET do organizowania struktur w natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: b174a817e82f9a9f123c79581656cc8e7179b435
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929038"
---
# <a name="customizing-structure-marshaling"></a>Dostosowywanie marshalingu struktur

Czasami domyślne reguły organizowania dla struktur nie są dokładnie tym, czego potrzebujesz. Środowiska uruchomieniowe platformy .NET udostępniają kilka punktów rozszerzenia, które umożliwiają dostosowanie układu struktury i sposobu organizowania pól.

## <a name="customizing-structure-layout"></a>Dostosowywanie układu struktury

Platforma .NET udostępnia <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atrybut <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> i Wyliczenie umożliwiające dostosowanie sposobu umieszczania pól w pamięci. Poniższe wskazówki pomogą uniknąć typowych problemów.

**✔️ rozważyć** użycie `LayoutKind.Sequential` wszędzie tam, gdzie to możliwe.

**✔️ są** używane `LayoutKind.Explicit` tylko podczas organizowania, gdy struktura natywna ma również jawny układ, taki jak Unia.

**❌ Unikać** `LayoutKind.Explicit` tworzenia struktur na platformach innych niż Windows. Środowisko uruchomieniowe platformy .NET Core nie obsługuje przekazywania jawnych struktur przez wartość do funkcji natywnych w systemach Intel lub AMD 64-bitowych systemów innych niż Windows. Jednak środowisko uruchomieniowe obsługuje przekazywanie jawnych struktur przez odwołanie na wszystkich platformach.

## <a name="customizing-boolean-field-marshaling"></a>Dostosowywanie kierowania pola logicznego

Kod natywny ma wiele różnych reprezentacji wartości logicznych. W systemie Windows, istnieją trzy sposoby reprezentowania wartości logicznych. Środowisko uruchomieniowe nie zna natywnej definicji struktury, dlatego najlepszym rozwiązaniem jest przypuszczenie metody organizowania wartości logicznych. Środowisko uruchomieniowe platformy .NET zapewnia sposób organizowania pola wartości logicznej. W poniższych przykładach pokazano, jak skierować `bool` platformę .NET do różnych natywnych typów logicznych.

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

Jeśli chcesz być jawnie, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> wartości, aby uzyskać takie samo zachowanie jak powyżej:

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

Korzystając z `UnmanagedType.U1` wartości `UnmanagedType.I1` lub poniżej, można powiedzieć środowisko uruchomieniowe, aby zorganizować `b` pole jako 1-bajtowy typ `bool` natywny.

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

W systemie Windows można użyć <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> wartości, aby poinformować środowisko uruchomieniowe o kierowaniu wartości logicznej do wartości 2-bajtowej: `VARIANT_BOOL`

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
> `VARIANT_BOOL`jest inna niż większość typów bool w tym `VARIANT_TRUE = -1` i `VARIANT_FALSE = 0`. Ponadto wszystkie wartości, które nie `VARIANT_TRUE` są równe, są uważane za fałszywe.

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

Jeśli korzystasz z interfejsów API modelu COM, może być konieczne kierowanie tablic jako `SAFEARRAY*` obiektów. Można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> i wartości, aby określić, że środowisko uruchomieniowe ma `SAFEARRAY*`zorganizować tablicę jako:

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

Jeśli musisz dostosować `SAFEARRAY`typ elementu w, możesz <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> użyć pól i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> , `SAFEARRAY`aby dostosować dokładny typ elementu.

Jeśli trzeba zorganizować tablicę w miejscu, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> wartości, aby poinformować organizatora, aby zorganizować tablicę w miejscu. W przypadku korzystania z tego organizowania należy również podać wartość <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pola dla liczby elementów w tablicy, aby środowisko uruchomieniowe prawidłowo przydzielić miejsce dla struktury.

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

Domyślnie program .NET kierujący ciąg jako wskaźnik do ciągu zakończonego wartością null. Kodowanie zależy od wartości <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>w. Jeśli żaden atrybut nie jest określony, kodowanie jest domyślnie zgodne z kodowaniem ANSI.

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

Jeśli potrzebujesz użyć innych kodowań dla różnych pól lub wolisz bardziej jawnie w definicji struktury, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> wartości lub <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> dla <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu.

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

Jeśli chcesz zorganizować ciągi przy użyciu kodowania UTF-8, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wartości <xref:System.Runtime.InteropServices.MarshalAsAttribute>w.

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
> Użycie <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga .NET Framework 4,7 (lub nowszych) lub .NET Core 1,1 (lub nowszych). Nie jest on dostępny w .NET Standard 2,0.

Jeśli pracujesz z interfejsami API modelu COM, może być konieczne przekierowanie ciągu `BSTR`jako. Korzystając z <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> wartości, można zorganizować ciąg `BSTR`jako.

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

W przypadku korzystania z interfejsu API opartego na WinRT może być konieczne zorganizowanie ciągu jako `HSTRING`.  Korzystając z <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> wartości, można zorganizować ciąg `HSTRING`jako.

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

Jeśli interfejs API wymaga przekazania ciągu w strukturze, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> wartości. Należy pamiętać, że kodowanie dla ciągu organizowanego przez `ByValTStr` jest określane `CharSet` na podstawie atrybutu. Ponadto wymaga, aby długość ciągu była przenoszona przez <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole.

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

Jeśli pracujesz w systemie Windows, możesz napotkać niektóre interfejsy API, które używają natywnego [ `CY` lub `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) struktury. Domyślnie typ .NET `decimal` ma kierowanie do struktury natywnej [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) . Można jednak użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> wartości z wartością, <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> aby nakazać `decimal` Organizatorowi przekonwertowanie wartości na wartość natywną `CY` .

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

W systemie Windows można skierować `object`pola do kodu natywnego. Można kierować te pola do jednego z trzech typów:

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

Domyślnie `object`pole z określonym typem zostanie zorganizowane `IUnknown*` do obiektu, który otacza obiekt.

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

Jeśli chcesz zorganizować pole obiektu do `IDispatch*`, Dodaj element <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> wartością.

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

Jeśli chcesz zorganizować ją jako `VARIANT`, Dodaj element <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> wartością.

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

W poniższej tabeli opisano, jak różne typy środowiska uruchomieniowego są `obj` mapowane na różne typy przechowywane `VARIANT`w:

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
