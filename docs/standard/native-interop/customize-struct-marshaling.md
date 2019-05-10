---
title: Dostosowywanie struktury marshaling — .NET
description: Dowiedz się, jak dostosować, jak .NET organizuje Twoje struktur natywną reprezentację.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
dev_langs:
- csharp
- cpp
ms.openlocfilehash: da36f2a703fe817c171e192b9c94e473c93447a3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2019
ms.locfileid: "65065472"
---
# <a name="customizing-structure-marshaling"></a><span data-ttu-id="2db0c-103">Dostosowywanie struktury organizacyjne</span><span class="sxs-lookup"><span data-stu-id="2db0c-103">Customizing structure marshaling</span></span>

<span data-ttu-id="2db0c-104">Czasami organizowania reguły domyślne w strukturach nie są dokładnie potrzebnych składników.</span><span class="sxs-lookup"><span data-stu-id="2db0c-104">Sometimes the default marshaling rules for structures aren't exactly what you need.</span></span> <span data-ttu-id="2db0c-105">Środowiska uruchomieniowe platformy .NET zawierają kilka punktów rozszerzeń, którą można dostosować układ i jak pola są przekazywane do struktury.</span><span class="sxs-lookup"><span data-stu-id="2db0c-105">The .NET runtimes provide a few extension points for you to customize your structure's layout and how fields are marshaled.</span></span>

## <a name="customizing-structure-layout"></a><span data-ttu-id="2db0c-106">Dostosowywanie układu struktury</span><span class="sxs-lookup"><span data-stu-id="2db0c-106">Customizing structure layout</span></span>

<span data-ttu-id="2db0c-107">.NET zapewnia <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> atrybutu i <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> wyliczenie, aby możliwe było dostosować jak pola są umieszczane w pamięci.</span><span class="sxs-lookup"><span data-stu-id="2db0c-107">.NET provides the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType> attribute and the <xref:System.Runtime.InteropServices.LayoutKind?displayProperty=nameWithType> enumeration to allow you to customize how fields are placed in memory.</span></span> <span data-ttu-id="2db0c-108">Poniższe wskazówki pomogą pozwala uniknąć typowych problemów.</span><span class="sxs-lookup"><span data-stu-id="2db0c-108">The following guidance will help you avoid common issues.</span></span>

<span data-ttu-id="2db0c-109">**ROZWAŻ ✔️** przy użyciu `LayoutKind.Sequential` zawsze, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="2db0c-109">**✔️ CONSIDER** using `LayoutKind.Sequential` whenever possible.</span></span>

<span data-ttu-id="2db0c-110">**CZY ✔️** składać się tylko `LayoutKind.Explicit` marshaling po swojej natywnej struktury jest również ma układ jawny, na przykład Unii.</span><span class="sxs-lookup"><span data-stu-id="2db0c-110">**✔️ DO** only use `LayoutKind.Explicit` in marshaling when your native struct is also has an explicit layout, such as a union.</span></span>

<span data-ttu-id="2db0c-111">**Należy UNIKAĆ ❌** przy użyciu `LayoutKind.Explicit` podczas przekazywania struktur na platformach innych niż Windows.</span><span class="sxs-lookup"><span data-stu-id="2db0c-111">**❌ AVOID** using `LayoutKind.Explicit` when marshaling structures on non-Windows platforms.</span></span> <span data-ttu-id="2db0c-112">Środowisko uruchomieniowe platformy .NET Core nie obsługuje przekazywanie struktury jawnej przez wartość do funkcji natywnych w systemach Intel lub AMD 64-bitowych inne niż Windows.</span><span class="sxs-lookup"><span data-stu-id="2db0c-112">The .NET Core runtime doesn't support passing explicit structures by value to native functions on Intel or AMD 64-bit non-Windows systems.</span></span> <span data-ttu-id="2db0c-113">Środowisko wykonawcze obsługuje jednak jawne przekazywanie struktury przez odniesienie na wszystkich platformach.</span><span class="sxs-lookup"><span data-stu-id="2db0c-113">However, the runtime supports passing explicit structures by reference on all platforms.</span></span>

## <a name="customizing-boolean-field-marshaling"></a><span data-ttu-id="2db0c-114">Dostosowywanie pola logicznych marshalingu</span><span class="sxs-lookup"><span data-stu-id="2db0c-114">Customizing boolean field marshaling</span></span>

<span data-ttu-id="2db0c-115">Kod natywny ma wiele różnych reprezentacji boolean.</span><span class="sxs-lookup"><span data-stu-id="2db0c-115">Native code has many different boolean representations.</span></span> <span data-ttu-id="2db0c-116">Na Windows samodzielnie istnieją trzy sposoby do reprezentowania wartości logiczne.</span><span class="sxs-lookup"><span data-stu-id="2db0c-116">On Windows alone, there are three ways to represent boolean values.</span></span> <span data-ttu-id="2db0c-117">Środowisko wykonawcze nie wiedzieć natywnych definicji struktury, dlatego najlepiej, co można zrobić zgadnąć na temat sposobu organizowania z wartościami logicznymi.</span><span class="sxs-lookup"><span data-stu-id="2db0c-117">The runtime doesn't know the native definition of your structure, so the best it can do is make a guess on how to marshal your boolean values.</span></span> <span data-ttu-id="2db0c-118">Środowisko uruchomieniowe platformy .NET zapewnia sposób, aby wskazać sposób organizowania pola logicznych.</span><span class="sxs-lookup"><span data-stu-id="2db0c-118">The .NET runtime provides a way to indicate how to marshal your boolean field.</span></span> <span data-ttu-id="2db0c-119">W poniższych przykładach pokazano, jak kierować .NET `bool` na różnych typach boolean natywnych.</span><span class="sxs-lookup"><span data-stu-id="2db0c-119">The following examples show how to marshal .NET `bool` to different native boolean types.</span></span>

<span data-ttu-id="2db0c-120">Atrybut typu wartość logiczna wartości domyślne kierowanie jako natywny Win32 4-bajtowych [ `BOOL` ](/windows/desktop/winprog/windows-data-types#BOOL) wartość, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2db0c-120">Boolean values default to marshaling as a native 4-byte Win32 [`BOOL`](/windows/desktop/winprog/windows-data-types#BOOL) value as shown in the following example:</span></span>

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

<span data-ttu-id="2db0c-121">Jeśli chcesz mieć jawne, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> wartości, aby uzyskać takie samo zachowanie, jak powyżej:</span><span class="sxs-lookup"><span data-stu-id="2db0c-121">If you want to be explicit, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.Bool?displayProperty=nameWithType> value to get the same behavior as above:</span></span>

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

<span data-ttu-id="2db0c-122">Za pomocą `UnmanagedType.U1` lub `UnmanagedType.I1` poniższych wartości, możesz poinformować środowiska uruchomieniowego, aby zorganizować `b` pola jako natywny 1-bajtowe `bool` typu.</span><span class="sxs-lookup"><span data-stu-id="2db0c-122">Using the `UnmanagedType.U1` or `UnmanagedType.I1` values below, you can tell the runtime to marshal the `b` field as a 1-byte native `bool` type.</span></span>

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

<span data-ttu-id="2db0c-123">Windows, mogą używać <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> wartość, aby poinformować środowiska uruchomieniowego do organizowania 2-bajtowych wartości logicznych `VARIANT_BOOL` wartość:</span><span class="sxs-lookup"><span data-stu-id="2db0c-123">On Windows, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.VariantBool?displayProperty=nameWithType> value to tell the runtime to marshal your boolean value to a 2-byte `VARIANT_BOOL` value:</span></span>

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
> <span data-ttu-id="2db0c-124">`VARIANT_BOOL` różni się od większości typów bool, w tym `VARIANT_TRUE = -1` i `VARIANT_FALSE = 0`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-124">`VARIANT_BOOL` is different than most bool types in that `VARIANT_TRUE = -1` and `VARIANT_FALSE = 0`.</span></span> <span data-ttu-id="2db0c-125">Ponadto wszystkie wartości, które nie są równe `VARIANT_TRUE` są traktowane jako wartość false.</span><span class="sxs-lookup"><span data-stu-id="2db0c-125">Additionally, all values that aren't equal to `VARIANT_TRUE` are considered false.</span></span>

## <a name="customizing-array-field-marshaling"></a><span data-ttu-id="2db0c-126">Dostosowywanie marshaling pola tablicy</span><span class="sxs-lookup"><span data-stu-id="2db0c-126">Customizing array field marshaling</span></span>

<span data-ttu-id="2db0c-127">.NET zawiera także kilka sposobów dostosowywania, organizowanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="2db0c-127">.NET also includes a few ways to customize array marshaling.</span></span>

<span data-ttu-id="2db0c-128">Domyślnie .NET kieruje tablic jako wskaźnik do listy sąsiadujących elementów:</span><span class="sxs-lookup"><span data-stu-id="2db0c-128">By default, .NET marshals arrays as a pointer to a contiguous list of the elements:</span></span>

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

<span data-ttu-id="2db0c-129">Jeśli masz komunikowanie się z interfejsów API modelu COM, może być konieczne przeprowadzanie marshalingu tablic jako `SAFEARRAY*` obiektów.</span><span class="sxs-lookup"><span data-stu-id="2db0c-129">If you're interfacing with COM APIs, you may have to marshal arrays as `SAFEARRAY*` objects.</span></span> <span data-ttu-id="2db0c-130">Możesz użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> wartość, aby poinformować środowiska uruchomieniowego, aby zorganizować tablicę jako `SAFEARRAY*`:</span><span class="sxs-lookup"><span data-stu-id="2db0c-130">You can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> and the <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> value to tell the runtime to marshal an array as a `SAFEARRAY*`:</span></span>

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

<span data-ttu-id="2db0c-131">Jeśli chcesz dostosować, jakiego rodzaju elementu jest w `SAFEARRAY`, wówczas można użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> i <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> typu pola, aby dostosować element dokładnie `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-131">If you need to customize what type of element is in the `SAFEARRAY`, then you can use the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> fields to customize the exact element type of the `SAFEARRAY`.</span></span>

<span data-ttu-id="2db0c-132">Jeśli musisz kierować tablicy w miejscu, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> wartość, aby poinformować Organizator, aby zorganizować tablicę w miejscu.</span><span class="sxs-lookup"><span data-stu-id="2db0c-132">If you need to marshal the array in-place, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> value to tell the marshaler to marshal the array in-place.</span></span> <span data-ttu-id="2db0c-133">Podczas korzystania z tego organizowanie, również należy podać wartość <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pole Liczba elementów w tablicy, dzięki czemu środowisko uruchomieniowe poprawnie można przydzielić miejsca w strukturze.</span><span class="sxs-lookup"><span data-stu-id="2db0c-133">When you're using this marshaling, you also must supply a value to the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field  for the number of elements in the array so the runtime can correctly allocate space for the structure.</span></span>

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
> <span data-ttu-id="2db0c-134">.NET nie obsługuje organizowanie pole o zmiennej długości tablicy jako składowej tablicowej z elastycznych C99.</span><span class="sxs-lookup"><span data-stu-id="2db0c-134">.NET doesn't support marshaling a variable length array field as a C99 Flexible Array Member.</span></span>

## <a name="customizing-string-field-marshaling"></a><span data-ttu-id="2db0c-135">Dostosowywanie marshaling pola ciągu</span><span class="sxs-lookup"><span data-stu-id="2db0c-135">Customizing string field marshaling</span></span>

<span data-ttu-id="2db0c-136">.NET zapewnia także szeroką gamę dostosowania marshaling pól ciągów.</span><span class="sxs-lookup"><span data-stu-id="2db0c-136">.NET also provides a wide variety of customizations for marshaling string fields.</span></span>

<span data-ttu-id="2db0c-137">Domyślnie .NET kieruje ciąg jako wskaźnik na ciąg zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="2db0c-137">By default, .NET marshals a string as a pointer to a null-terminated string.</span></span> <span data-ttu-id="2db0c-138">Kodowanie jest zależne od wartości <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> pole <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2db0c-138">The encoding depends on the value of the <xref:System.Runtime.InteropServices.StructLayoutAttribute.CharSet?displayProperty=nameWithType> field in the <xref:System.Runtime.InteropServices.StructLayoutAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2db0c-139">Jeśli atrybut nie zostanie określony, kodowanie, wartość domyślna to kodowania ANSI.</span><span class="sxs-lookup"><span data-stu-id="2db0c-139">If no attribute is specified, the encoding defaults to an ANSI encoding.</span></span>

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

<span data-ttu-id="2db0c-140">Jeśli musisz używać różnych kodowań dla różnych pól lub po prostu chcesz być dokładniejsze w definicji struktury, można użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> wartości na <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2db0c-140">If you need to use different encodings for different fields or just prefer to be more explicit in your struct definition, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPStr?displayProperty=nameWithType> or <xref:System.Runtime.InteropServices.UnmanagedType.LPWStr?displayProperty=nameWithType> values on a <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> attribute.</span></span>

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

<span data-ttu-id="2db0c-141">Jeśli chcesz kierować swoje ciągi przy użyciu kodowania UTF-8, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wartość w swojej <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2db0c-141">If you want to marshal your strings using the UTF-8 encoding, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> value in your <xref:System.Runtime.InteropServices.MarshalAsAttribute>.</span></span>

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
> <span data-ttu-id="2db0c-142">Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> wymaga programu .NET Framework 4.7 (lub nowszy) lub .NET Core 1.1 (lub nowszy).</span><span class="sxs-lookup"><span data-stu-id="2db0c-142">Using <xref:System.Runtime.InteropServices.UnmanagedType.LPUTF8Str?displayProperty=nameWithType> requires either .NET Framework 4.7 (or later versions) or .NET Core 1.1 (or later versions).</span></span> <span data-ttu-id="2db0c-143">Nie jest dostępne w programie .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="2db0c-143">It isn't available in .NET Standard 2.0.</span></span>

<span data-ttu-id="2db0c-144">Jeśli pracujesz z interfejsów API modelu COM, może być konieczne kierować ciąg w kodowaniu `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-144">If you're working with COM APIs, you may need to marshal a string as a `BSTR`.</span></span> <span data-ttu-id="2db0c-145">Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> wartości, można kierować ciąg jako `BSTR`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-145">Using the <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> value, you can marshal a string as a `BSTR`.</span></span>

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

<span data-ttu-id="2db0c-146">Korzystając z interfejsu API opartego na WinRT, konieczne może być kierować ciąg w kodowaniu `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-146">When using a WinRT-based API, you may need to marshal a string as an `HSTRING`.</span></span>  <span data-ttu-id="2db0c-147">Za pomocą <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> wartości, można kierować ciąg jako `HSTRING`.</span><span class="sxs-lookup"><span data-stu-id="2db0c-147">Using the <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> value, you can marshal a string as a `HSTRING`.</span></span>

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

<span data-ttu-id="2db0c-148">Jeśli Twój interfejs API wymaga przekazania parametrów w miejscu w strukturze, możesz użyć <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> wartość.</span><span class="sxs-lookup"><span data-stu-id="2db0c-148">If your API requires you to pass the string in-place in the structure, you can use the <xref:System.Runtime.InteropServices.UnmanagedType.ByValTStr?displayProperty=nameWithType> value.</span></span> <span data-ttu-id="2db0c-149">Należy pamiętać, że kodowanie ciągu organizowane przez `ByValTStr` jest określana na podstawie `CharSet` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="2db0c-149">Do note that the encoding for a string marshaled by `ByValTStr` is determined from the `CharSet` attribute.</span></span> <span data-ttu-id="2db0c-150">Ponadto wymaga ona, że długość ciągu jest przekazywany przez <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> pola.</span><span class="sxs-lookup"><span data-stu-id="2db0c-150">Additionally, it requires that a string length is passed by the <xref:System.Runtime.InteropServices.MarshalAsAttribute.SizeConst?displayProperty=nameWithType> field.</span></span>

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

## <a name="customizing-decimal-field-marshaling"></a><span data-ttu-id="2db0c-151">Dostosowywanie marshaling pola wartości dziesiętnej</span><span class="sxs-lookup"><span data-stu-id="2db0c-151">Customizing decimal field marshaling</span></span>

<span data-ttu-id="2db0c-152">Jeśli pracujesz w Windows, mogą wystąpić niektóre interfejsy API, używanego przez natywnych [ `CY` lub `CURRENCY` ](/windows/desktop/api/wtypes/ns-wtypes-tagcy) struktury.</span><span class="sxs-lookup"><span data-stu-id="2db0c-152">If you're working on Windows, you might encounter some APIs that use the native [`CY` or `CURRENCY`](/windows/desktop/api/wtypes/ns-wtypes-tagcy) structure.</span></span> <span data-ttu-id="2db0c-153">Domyślnie .NET `decimal` wpisz marshals do natywnych [ `DECIMAL` ](/windows/desktop/api/wtypes/ns-wtypes-tagdec) struktury.</span><span class="sxs-lookup"><span data-stu-id="2db0c-153">By default, the .NET `decimal` type marshals to the native [`DECIMAL`](/windows/desktop/api/wtypes/ns-wtypes-tagdec) structure.</span></span> <span data-ttu-id="2db0c-154">Można jednak użyć <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> wartość, aby nakazać Organizator, aby przekonwertować `decimal` wartość do macierzystej `CY` wartość.</span><span class="sxs-lookup"><span data-stu-id="2db0c-154">However, you can use a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=nameWithType> value to instruct the marshaler to convert a `decimal` value to a native `CY` value.</span></span>

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

## <a name="marshaling-systemobjects"></a><span data-ttu-id="2db0c-155">Marshaling `System.Object`s</span><span class="sxs-lookup"><span data-stu-id="2db0c-155">Marshaling `System.Object`s</span></span>

<span data-ttu-id="2db0c-156">W Windows, może kierować element `object`-wpisane pola do kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="2db0c-156">On Windows, you can marshal `object`-typed fields to native code.</span></span> <span data-ttu-id="2db0c-157">Można kierować te pola do jednego z trzech typów:</span><span class="sxs-lookup"><span data-stu-id="2db0c-157">You can marshal these fields to one of three types:</span></span>
- [`VARIANT`](/windows/desktop/api/oaidl/ns-oaidl-tagvariant)
- [`IUnknown*`](/windows/desktop/api/unknwn/nn-unknwn-iunknown)
- [`IDispatch*`](/windows/desktop/api/oaidl/nn-oaidl-idispatch)

<span data-ttu-id="2db0c-158">Domyślnie `object`— będzie można zorganizować wpisane pola `IUnknown*` która otacza obiekt.</span><span class="sxs-lookup"><span data-stu-id="2db0c-158">By default, an `object`-typed field will be marshaled to an `IUnknown*` that wraps the object.</span></span>

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

<span data-ttu-id="2db0c-159">Jeśli chcesz kierować pola obiektu do `IDispatch*`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> wartości.</span><span class="sxs-lookup"><span data-stu-id="2db0c-159">If you want to marshal an object field to an `IDispatch*`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="2db0c-160">Jeśli chcesz kierować go jako `VARIANT`, Dodaj <xref:System.Runtime.InteropServices.MarshalAsAttribute> z <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> wartości.</span><span class="sxs-lookup"><span data-stu-id="2db0c-160">If you want to marshal it as a `VARIANT`, add a <xref:System.Runtime.InteropServices.MarshalAsAttribute> with the <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> value.</span></span>

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

<span data-ttu-id="2db0c-161">W poniższej tabeli opisano, jak różne typy środowiska uruchomieniowego `obj` mapowania pól do różnych typów, które są przechowywane w `VARIANT`:</span><span class="sxs-lookup"><span data-stu-id="2db0c-161">The following table describes how different runtime types of the `obj` field map to the various types stored in a `VARIANT`:</span></span>

| <span data-ttu-id="2db0c-162">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="2db0c-162">.NET Type</span></span> | <span data-ttu-id="2db0c-163">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="2db0c-163">VARIANT Type</span></span> | | <span data-ttu-id="2db0c-164">Typ architektury .NET</span><span class="sxs-lookup"><span data-stu-id="2db0c-164">.NET Type</span></span> | <span data-ttu-id="2db0c-165">Typ VARIANT</span><span class="sxs-lookup"><span data-stu-id="2db0c-165">VARIANT Type</span></span> |
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
