---
title: Dostosowywanie organizowania struktury — .NET
description: Dowiedz się, jak dostosować platformę .NET do organizowania struktur w natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: f4b8402413f4d2f558d8e61ad4f10490dece9835
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423988"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="19804-103">Dostosowywanie marshalingu struktur</span><span class="sxs-lookup"><span data-stu-id="19804-103">Customizing structure marshaling</span></span>

<span data-ttu-id="19804-104">Czasami domyślne reguły organizowania dla struktur nie są dokładnie tym, czego potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="19804-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="19804-105">Środowiska uruchomieniowe platformy .NET udostępniają kilka punktów rozszerzenia, które umożliwiają dostosowanie układu struktury i sposobu organizowania pól.</span><span class="sxs-lookup"><span data-stu-id="19804-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="19804-106">Dostosowywanie układu struktury</span><span class="sxs-lookup"><span data-stu-id="19804-106">Customizing structure layout</span></span>

<span data-ttu-id="19804-107">Platforma .NET udostępnia atrybut <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> i Wyliczenie <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType>, aby umożliwić dostosowywanie sposobu umieszczania pól w pamięci.</span><span class="sxs-lookup"><span data-stu-id="19804-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="19804-108">Poniższe wskazówki pomogą uniknąć typowych problemów.</span><span class="sxs-lookup"><span data-stu-id="19804-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="19804-109">**✔️ rozważyć** użycie `LayoutKind.Sequential`, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="19804-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="19804-110">**✔️** używać `LayoutKind.Explicit` podczas organizowania, gdy struktura natywna również ma jawny układ, taki jak Unia.</span><span class="sxs-lookup"><span data-stu-id="19804-110">**✔️ DO** only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="19804-111">**❌ Unikaj** używania `LayoutKind.Explicit` podczas organizowania struktur na platformach innych niż Windows, jeśli chcesz, aby docelowe środowiska uruchomieniowe przed platformą .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="19804-111">**❌ AVOID** using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms if you need to target runtimes before .NET Core 3.0.</span></span> <span data-ttu-id="19804-112">Środowisko uruchomieniowe platformy .NET Core przed 3,0 nie obsługuje przekazywania jawnych struktur przez wartość do funkcji natywnych w systemach Intel lub AMD 64-bitowym z systemem innym niż Windows.</span><span class="sxs-lookup"><span data-stu-id="19804-112">The .NET Core runtime before 3.0 doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="19804-113">Jednak środowisko uruchomieniowe obsługuje przekazywanie jawnych struktur przez odwołanie na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="19804-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="19804-114">Dostosowywanie kierowania pola logicznego</span><span class="sxs-lookup"><span data-stu-id="19804-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="19804-115">Kod natywny ma wiele różnych reprezentacji wartości logicznych.</span><span class="sxs-lookup"><span data-stu-id="19804-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="19804-116">W systemie Windows, istnieją trzy sposoby reprezentowania wartości logicznych.</span><span class="sxs-lookup"><span data-stu-id="19804-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="19804-117">Środowisko uruchomieniowe nie zna natywnej definicji struktury, dlatego najlepszym rozwiązaniem jest przypuszczenie metody organizowania wartości logicznych.</span><span class="sxs-lookup"><span data-stu-id="19804-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="19804-118">Środowisko uruchomieniowe platformy .NET zapewnia sposób organizowania pola wartości logicznej.</span><span class="sxs-lookup"><span data-stu-id="19804-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="19804-119">W poniższych przykładach pokazano, jak zorganizować platformę .NET `bool` do różnych natywnych typów logicznych.</span><span class="sxs-lookup"><span data-stu-id="19804-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="19804-120">Wartości logiczne są domyślnie organizowane jako natywne 4-bajtowe wartości [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) Win32, jak pokazano w następującym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="19804-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="19804-121">Jeśli chcesz być jawnie, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType>, aby uzyskać takie samo zachowanie jak powyżej:</span><span class="sxs-lookup"><span data-stu-id="19804-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="19804-122">Korzystając z `UnmanagedType.U1` lub `UnmanagedType.I1` wartości poniżej, można poinstruować środowisko uruchomieniowe, aby zorganizować pole `b` jako typ 1-bajtowy `bool` natywny.</span><span class="sxs-lookup"><span data-stu-id="19804-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="19804-123">W systemie Windows można użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType>, aby określić, że środowisko uruchomieniowe ma kierować wartość logiczną do 2-bajtowej `VARIANT_BOOL` wartości:</span><span class="sxs-lookup"><span data-stu-id="19804-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="19804-124">`VARIANT_BOOL` jest inna niż większość typów bool w tym `VARIANT_TRUE = -1` i `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="19804-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="19804-125">Ponadto wszystkie wartości, które nie są równe `VARIANT_TRUE` są uważane za fałszywe.</span><span class="sxs-lookup"><span data-stu-id="19804-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="19804-126">Dostosowywanie organizowania pól tablicy</span><span class="sxs-lookup"><span data-stu-id="19804-126">Customizing array field marshaling</span></span>

<span data-ttu-id="19804-127">Platforma .NET zawiera również kilka sposobów dostosowywania organizowania tablic.</span><span class="sxs-lookup"><span data-stu-id="19804-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="19804-128">Domyślnie program .NET kierowanie tablic jako wskaźnika do ciągłej listy elementów:</span><span class="sxs-lookup"><span data-stu-id="19804-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="19804-129">Jeśli korzystasz z interfejsów API modelu COM, może być konieczne kierowanie tablic jako obiektów `SAFEARRAY*`.</span><span class="sxs-lookup"><span data-stu-id="19804-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="19804-130">Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> i wartości <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>, aby określić, że środowisko uruchomieniowe ma zorganizować tablicę jako `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="19804-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="19804-131">Jeśli musisz dostosować typ elementu do `SAFEARRAY`, możesz użyć pól <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> do dostosowania dokładnego typu elementu `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="19804-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="19804-132">Jeśli musisz zorganizować tablicę w miejscu, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>, aby poinformować organizatora, aby zorganizować tablicę w miejscu.</span><span class="sxs-lookup"><span data-stu-id="19804-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="19804-133">W przypadku korzystania z tego organizowania należy również podać wartość pola <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> dla liczby elementów w tablicy, aby środowisko uruchomieniowe prawidłowo przydzielić miejsce dla struktury.</span><span class="sxs-lookup"><span data-stu-id="19804-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="19804-134">Platforma .NET nie obsługuje organizowania pola tablicy o zmiennej długości jako C99 elastycznej składowej tablicy.</span><span class="sxs-lookup"><span data-stu-id="19804-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="19804-135">Dostosowywanie organizowania pól ciągów</span><span class="sxs-lookup"><span data-stu-id="19804-135">Customizing string field marshaling</span></span>

<span data-ttu-id="19804-136">Platforma .NET udostępnia również szeroką gamę dostosowań do organizowania pól ciągów.</span><span class="sxs-lookup"><span data-stu-id="19804-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="19804-137">Domyślnie program .NET kierujący ciąg jako wskaźnik do ciągu zakończonego wartością null.</span><span class="sxs-lookup"><span data-stu-id="19804-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="19804-138">Kodowanie zależy od wartości pola <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="19804-139">Jeśli żaden atrybut nie jest określony, kodowanie jest domyślnie zgodne z kodowaniem ANSI.</span><span class="sxs-lookup"><span data-stu-id="19804-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="19804-140">Jeśli potrzebujesz użyć innych kodowań dla różnych pól lub wolisz bardziej jawnie w definicji struktury, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> w atrybucie <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="19804-141">Jeśli chcesz zorganizować ciągi przy użyciu kodowania UTF-8, możesz użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> w <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="19804-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="19804-142">Używanie <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga .NET Framework 4,7 (lub nowszych) lub .NET Core 1,1 (lub nowszych).</span><span class="sxs-lookup"><span data-stu-id="19804-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="19804-143">Nie jest on dostępny w .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="19804-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="19804-144">Jeśli pracujesz z interfejsami API modelu COM, może być konieczne przekierowanie ciągu jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="19804-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="19804-145">Korzystając z wartości <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType>, można zorganizować ciąg jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="19804-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="19804-146">W przypadku korzystania z interfejsu API opartego na WinRT może być konieczne skierowanie ciągu jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="19804-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="19804-147">Korzystając z wartości <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType>, można zorganizować ciąg jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="19804-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="19804-148">Jeśli interfejs API wymaga przekazania ciągu w strukturze, można użyć wartości <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="19804-149">Należy pamiętać, że kodowanie dla ciągu organizowanego przez `ByValTStr` jest określane na podstawie atrybutu `CharSet`.</span><span class="sxs-lookup"><span data-stu-id="19804-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="19804-150">Ponadto wymaga, aby długość ciągu była przenoszona przez pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="19804-151">Dostosowywanie organizowania pól dziesiętnych</span><span class="sxs-lookup"><span data-stu-id="19804-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="19804-152">Jeśli pracujesz w systemie Windows, możesz napotkać niektóre interfejsy API, które używają natywnej struktury [`CY` lub `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) .</span><span class="sxs-lookup"><span data-stu-id="19804-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/win32/api/wtypes/ns-wtypes-cy~r1) structure.</span></span> <span data-ttu-id="19804-153">Domyślnie typ `decimal` .NET kierowanie do struktury [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) natywnej.</span><span class="sxs-lookup"><span data-stu-id="19804-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/win32/api/wtypes/ns-wtypes-decimal~r1) structure.</span></span> <span data-ttu-id="19804-154">Można jednak użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType>, aby nakazać Organizatorowi przekonwertowanie wartości `decimal` na natywną wartość `CY`.</span><span class="sxs-lookup"><span data-stu-id="19804-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="19804-155">Kierowanie `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="19804-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="19804-156">W systemie Windows można organizować pola wpisywane `object`na kod natywny.</span><span class="sxs-lookup"><span data-stu-id="19804-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="19804-157">Można kierować te pola do jednego z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="19804-157">You can marshal these fields to one of three types:</span></span>

- [`VARIANT`](/windows/win32/api/oaidl/ns-oaidl-variant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="19804-158">Domyślnie pole o typie `object`będzie organizowane w `IUnknown*`, który zawija obiekt.</span><span class="sxs-lookup"><span data-stu-id="19804-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="19804-159">Jeśli chcesz zorganizować pole obiektu do `IDispatch*`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="19804-160">Jeśli chcesz zorganizować ją jako `VARIANT`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z wartością <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19804-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="19804-161">W poniższej tabeli opisano, jak różne typy środowiska uruchomieniowego `obj` mapowane na różne typy przechowywane w `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="19804-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="19804-162">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="19804-162">.NET Type</span></span> | <span data-ttu-id="19804-163">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="19804-163">VARIANT Type</span></span> | | <span data-ttu-id="19804-164">Typ .NET</span><span class="sxs-lookup"><span data-stu-id="19804-164">.NET Type</span></span> | <span data-ttu-id="19804-165">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="19804-165">VARIANT Type</span></span> |
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
