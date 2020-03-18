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
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="bdad0-103">Dostosowywanie marshalingu struktur</span><span class="sxs-lookup"><span data-stu-id="bdad0-103">Customizing structure marshaling</span></span>

<span data-ttu-id="bdad0-104">Czasami domyślne reguły organizowania struktur nie są dokładnie tym, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="bdad0-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="bdad0-105">Środowiska uruchomieniowe .NET zapewniają kilka punktów rozszerzenia, aby dostosować układ struktury i sposób organizowania pól.</span><span class="sxs-lookup"><span data-stu-id="bdad0-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="bdad0-106">Dostosowywanie układu struktury</span><span class="sxs-lookup"><span data-stu-id="bdad0-106">Customizing structure layout</span></span>

<span data-ttu-id="bdad0-107">.NET udostępnia <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atrybut <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> i wyliczenie, aby umożliwić dostosowanie sposobu umieszczania pól w pamięci.</span><span class="sxs-lookup"><span data-stu-id="bdad0-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="bdad0-108">Poniższe wskazówki pomogą Ci uniknąć typowych problemów.</span><span class="sxs-lookup"><span data-stu-id="bdad0-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="bdad0-109">✔️ ROZWAŻ `LayoutKind.Sequential` UŻYCIE, gdy tylko jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="bdad0-109">✔️ CONSIDER using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="bdad0-110">✔️ do `LayoutKind.Explicit` tylko używać w organizowaniu, gdy natywna struktura ma również jawny układ, takich jak unii.</span><span class="sxs-lookup"><span data-stu-id="bdad0-110">✔️ DO only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="bdad0-111">❌Unikaj `LayoutKind.Explicit` używania podczas organizowania struktur na platformach innych niż Windows, jeśli trzeba kierować środowiska uruchomieniowe przed .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bdad0-111">❌ AVOID using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="bdad0-112">Środowisko uruchomieniowe .NET Core przed 3.0 nie obsługuje przekazywania jawnych struktur według wartości do funkcji natywnych w 64-bitowych systemach innych niż Windows firmy Intel lub AMD.</span><span class="sxs-lookup"><span data-stu-id="bdad0-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="bdad0-113">Jednak czas wykonywania obsługuje przekazywanie jawne struktury przez odwołanie na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="bdad0-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="bdad0-114">Dostosowywanie kierowanie pól logicznych</span><span class="sxs-lookup"><span data-stu-id="bdad0-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="bdad0-115">Kod macierzysty ma wiele różnych reprezentacji logicznych.</span><span class="sxs-lookup"><span data-stu-id="bdad0-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="bdad0-116">W samym systemie Windows istnieją trzy sposoby reprezentowania wartości logicznych.</span><span class="sxs-lookup"><span data-stu-id="bdad0-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="bdad0-117">Czas wykonywania nie zna natywnej definicji struktury, więc najlepiej można zrobić, to odgadnąć, jak zorganizować wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="bdad0-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="bdad0-118">Program runtime .NET umożliwia wskazanie sposobu organizowania pola logicznego.</span><span class="sxs-lookup"><span data-stu-id="bdad0-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="bdad0-119">W poniższych przykładach przedstawiono `bool` sposób organizowania .NET do różnych typów natywnych logicznych.</span><span class="sxs-lookup"><span data-stu-id="bdad0-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="bdad0-120">Wartości logiczne domyślnie do organizowania jako natywna 4-bajtowa wartość Win32, [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bdad0-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="bdad0-121">Jeśli chcesz mieć jawne, można <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> użyć wartości, aby uzyskać takie samo zachowanie jak powyżej:</span><span class="sxs-lookup"><span data-stu-id="bdad0-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="bdad0-122">Za `UnmanagedType.U1` pomocą `UnmanagedType.I1` lub wartości poniżej, można powiedzieć, `b` w czasie wykonywania `bool` do organizowania pola jako typ macierzysty 1-bajtowy.</span><span class="sxs-lookup"><span data-stu-id="bdad0-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="bdad0-123">W systemie Windows można <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> użyć tej wartości, aby poinformować środowisko uruchomieniowe, aby zorganizować wartość logiczną do wartości 2-bajtowej: `VARIANT_BOOL`</span><span class="sxs-lookup"><span data-stu-id="bdad0-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="bdad0-124">`VARIANT_BOOL`różni się od większości typów `VARIANT_TRUE = -1` `VARIANT_FALSE = 0`bool w tym i .</span><span class="sxs-lookup"><span data-stu-id="bdad0-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="bdad0-125">Ponadto wszystkie wartości, które nie `VARIANT_TRUE` są równe są uważane za false.</span><span class="sxs-lookup"><span data-stu-id="bdad0-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="bdad0-126">Dostosowywanie organizowania pól tablicy</span><span class="sxs-lookup"><span data-stu-id="bdad0-126">Customizing array field marshaling</span></span>

<span data-ttu-id="bdad0-127">.NET zawiera również kilka sposobów dostosowywania organizowania tablicy.</span><span class="sxs-lookup"><span data-stu-id="bdad0-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="bdad0-128">Domyślnie .NET organizuje tablice jako wskaźnik do ciągłej listy elementów:</span><span class="sxs-lookup"><span data-stu-id="bdad0-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="bdad0-129">Jeśli łączysz się z interfejsami API COM, `SAFEARRAY*` może być trzeba zorganizować tablice jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="bdad0-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="bdad0-130">Można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> i wartość, aby poinformować program runtime `SAFEARRAY*`do organizowania tablicy jako:</span><span class="sxs-lookup"><span data-stu-id="bdad0-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="bdad0-131">Jeśli chcesz dostosować typ elementu w `SAFEARRAY`, następnie można <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> i pola, aby dostosować `SAFEARRAY`dokładny typ elementu .</span><span class="sxs-lookup"><span data-stu-id="bdad0-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="bdad0-132">Jeśli trzeba zorganizować tablicy w miejscu, można <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> użyć wartości, aby poinformować organizatora do organizowania tablicy w miejscu.</span><span class="sxs-lookup"><span data-stu-id="bdad0-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="bdad0-133">Korzystając z tego organizowania, należy również podać <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> wartość do pola dla liczby elementów w tablicy, dzięki czemu czas wykonywania można poprawnie przydzielić miejsce dla struktury.</span><span class="sxs-lookup"><span data-stu-id="bdad0-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="bdad0-134">.NET nie obsługuje organizowania pola tablicy o zmiennej długości jako członka tablicy elastycznej C99.</span><span class="sxs-lookup"><span data-stu-id="bdad0-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="bdad0-135">Dostosowywanie organizowania pól ciągów</span><span class="sxs-lookup"><span data-stu-id="bdad0-135">Customizing string field marshaling</span></span>

<span data-ttu-id="bdad0-136">.NET udostępnia również szeroką gamę dostosowań dla organizowania pól ciągów.</span><span class="sxs-lookup"><span data-stu-id="bdad0-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="bdad0-137">Domyślnie .NET organizuje ciąg jako wskaźnik do ciągu zakończonego zerem.</span><span class="sxs-lookup"><span data-stu-id="bdad0-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="bdad0-138">Kodowanie zależy od wartości <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pola w <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>pliku .</span><span class="sxs-lookup"><span data-stu-id="bdad0-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bdad0-139">Jeśli nie określono żadnego atrybutu, kodowanie domyślnie koduje ANSI.</span><span class="sxs-lookup"><span data-stu-id="bdad0-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="bdad0-140">Jeśli chcesz użyć różnych kodowania dla różnych pól lub po prostu wolą być bardziej jawne <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> definicji struktury, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub wartości na atrybut.</span><span class="sxs-lookup"><span data-stu-id="bdad0-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="bdad0-141">Jeśli chcesz zorganizować ciągi przy użyciu kodowania UTF-8, <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute>wartości w pliku .</span><span class="sxs-lookup"><span data-stu-id="bdad0-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="bdad0-142">Korzystanie <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga .NET Framework 4.7 (lub nowszych wersji) lub .NET Core 1.1 (lub nowszych wersjach).</span><span class="sxs-lookup"><span data-stu-id="bdad0-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="bdad0-143">Nie jest dostępna w .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="bdad0-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="bdad0-144">Jeśli pracujesz z interfejsami API COM, może `BSTR`być konieczne zorganizowanie ciągu jako pliku .</span><span class="sxs-lookup"><span data-stu-id="bdad0-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="bdad0-145">Za <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> pomocą wartości można zorganizować ciąg `BSTR`jako .</span><span class="sxs-lookup"><span data-stu-id="bdad0-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="bdad0-146">Korzystając z interfejsu API opartego na winrt, może `HSTRING`być konieczne zorganizowanie ciągu jako .</span><span class="sxs-lookup"><span data-stu-id="bdad0-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="bdad0-147">Za <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> pomocą wartości można zorganizować ciąg `HSTRING`jako .</span><span class="sxs-lookup"><span data-stu-id="bdad0-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="bdad0-148">Jeśli interfejs API wymaga przekazania ciągu w miejscu w strukturze, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> wartości.</span><span class="sxs-lookup"><span data-stu-id="bdad0-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="bdad0-149">Należy pamiętać, że kodowanie ciągu `ByValTStr` organizowane przez `CharSet` jest określana na podstawie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="bdad0-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="bdad0-150">Ponadto wymaga, aby długość ciągu jest <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> przekazywana przez pole.</span><span class="sxs-lookup"><span data-stu-id="bdad0-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="bdad0-151">Dostosowywanie organizowania pól dziesiętnych</span><span class="sxs-lookup"><span data-stu-id="bdad0-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="bdad0-152">Jeśli pracujesz w systemie Windows, może wystąpić niektóre [ `CY` `CURRENCY` ](/windows/win32/api/wtypes/ns-wtypes-cy~r1) interfejsy API, które używają natywnych lub struktury.</span><span class="sxs-lookup"><span data-stu-id="bdad0-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="bdad0-153">Domyślnie typ .NET `decimal` organizuje do [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) struktury macierzystej.</span><span class="sxs-lookup"><span data-stu-id="bdad0-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="bdad0-154">Jednak można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> a <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> z wartością, aby poinstruować organizatora, aby przekonwertować `decimal` wartość na wartość natywną. `CY`</span><span class="sxs-lookup"><span data-stu-id="bdad0-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="bdad0-155">Kierowanie `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="bdad0-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="bdad0-156">W systemie Windows `object`można zorganizować pola wpisane do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="bdad0-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="bdad0-157">Te pola można zorganizować na jeden z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="bdad0-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="bdad0-158">Domyślnie pole `object`wpisane na maszynę `IUnknown*` będzie organizowane w obiekcie, które otacza obiekt.</span><span class="sxs-lookup"><span data-stu-id="bdad0-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="bdad0-159">Jeśli chcesz zorganizować pole obiektu `IDispatch*`do , <xref:System.Runtime.InteropServices.MarshalAsAttribute> dodaj <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> a z wartością.</span><span class="sxs-lookup"><span data-stu-id="bdad0-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="bdad0-160">Jeśli chcesz zorganizować go `VARIANT`jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> dodaj <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> a z wartością.</span><span class="sxs-lookup"><span data-stu-id="bdad0-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="bdad0-161">W poniższej tabeli opisano, `obj` jak różne typy czasu wykonywania mapy pola do różnych typów przechowywanych `VARIANT`w:</span><span class="sxs-lookup"><span data-stu-id="bdad0-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="bdad0-162">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="bdad0-162">.NET Type</span></span> | <span data-ttu-id="bdad0-163">Typ WARIANTU</span><span class="sxs-lookup"><span data-stu-id="bdad0-163">VARIANT Type</span></span> | | <span data-ttu-id="bdad0-164">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="bdad0-164">.NET Type</span></span> | <span data-ttu-id="bdad0-165">Typ WARIANTU</span><span class="sxs-lookup"><span data-stu-id="bdad0-165">VARIANT Type</span></span> |
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
