---
title: Organizowanie domyślne dotyczące ciągów
description: Zapoznaj się z domyślnym zachowaniem organizowania ciągów w interfejsach, wywołaniu platformy, strukturach, & buforów ciągów o stałej długości w programie .NET.
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
ms.openlocfilehash: 440a49730f351b820cd68a741e79f94434f585c8
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904120"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="f7651-103">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="f7651-103">Default Marshaling for Strings</span></span>

<span data-ttu-id="f7651-104">Obie <xref:System.String?displayProperty=nameWithType> klasy i <xref:System.Text.StringBuilder?displayProperty=nameWithType> mają podobne zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="f7651-104">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="f7651-105">Ciągi są organizowane jako typ stylu COM `BSTR` lub jako ciąg zakończony znakiem null (tablica znaków, która kończy się znakiem null).</span><span class="sxs-lookup"><span data-stu-id="f7651-105">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="f7651-106">Znaki w ciągu mogą być organizowane jako Unicode (domyślnie w systemach Windows) lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="f7651-106">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="f7651-107">Ciągi używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="f7651-107">Strings Used in Interfaces</span></span>

<span data-ttu-id="f7651-108">W poniższej tabeli przedstawiono opcje kierowania dla typu danych ciągu, które są organizowane jako argumenty metody do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f7651-108">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="f7651-109">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia, które umożliwiają kierowanie ciągów do interfejsów com.</span><span class="sxs-lookup"><span data-stu-id="f7651-109">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="f7651-110">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f7651-110">Enumeration type</span></span>|<span data-ttu-id="f7651-111">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="f7651-111">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="f7651-112">`UnmanagedType.BStr`wartooć</span><span class="sxs-lookup"><span data-stu-id="f7651-112">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="f7651-113">Styl COM `BSTR` o stałej długości i znakach Unicode.</span><span class="sxs-lookup"><span data-stu-id="f7651-113">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="f7651-114">Wskaźnik do tablicy znaków ANSI zakończonych znakiem null.</span><span class="sxs-lookup"><span data-stu-id="f7651-114">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="f7651-115">Wskaźnik do tablicy znaków Unicode zakończonych wartością null.</span><span class="sxs-lookup"><span data-stu-id="f7651-115">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="f7651-116">Ta tabela ma zastosowanie do <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="f7651-116">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="f7651-117">W przypadku <xref:System.Text.StringBuilder> opcji Jedynymi dozwolonymi opcjami są `UnmanagedType.LPStr` i `UnmanagedType.LPWStr` .</span><span class="sxs-lookup"><span data-stu-id="f7651-117">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="f7651-118">Poniższy przykład przedstawia ciągi zadeklarowane w `IStringWorker` interfejsie.</span><span class="sxs-lookup"><span data-stu-id="f7651-118">The following example shows strings declared in the `IStringWorker` interface.</span></span>

```csharp
public interface IStringWorker
{
    void PassString1(string s);
    void PassString2([MarshalAs(UnmanagedType.BStr)] string s);
    void PassString3([MarshalAs(UnmanagedType.LPStr)] string s);
    void PassString4([MarshalAs(UnmanagedType.LPWStr)] string s);
    void PassStringRef1(ref string s);
    void PassStringRef2([MarshalAs(UnmanagedType.BStr)] ref string s);
    void PassStringRef3([MarshalAs(UnmanagedType.LPStr)] ref string s);
    void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)] ref string s);
}
```

```vb
Public Interface IStringWorker
    Sub PassString1(s As String)
    Sub PassString2(<MarshalAs(UnmanagedType.BStr)> s As String)
    Sub PassString3(<MarshalAs(UnmanagedType.LPStr)> s As String)
    Sub PassString4(<MarshalAs(UnmanagedType.LPWStr)> s As String)
    Sub PassStringRef1(ByRef s As String)
    Sub PassStringRef2(<MarshalAs(UnmanagedType.BStr)> ByRef s As String)
    Sub PassStringRef3(<MarshalAs(UnmanagedType.LPStr)> ByRef s As String)
    Sub PassStringRef4(<MarshalAs(UnmanagedType.LPWStr)> ByRef s As String)
End Interface
```

<span data-ttu-id="f7651-119">Poniższy przykład pokazuje odpowiedni interfejs opisany w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="f7651-119">The following example shows the corresponding interface described in a type library.</span></span>

```cpp
interface IStringWorker : IDispatch
{
    HRESULT PassString1([in] BSTR s);
    HRESULT PassString2([in] BSTR s);
    HRESULT PassString3([in] LPStr s);
    HRESULT PassString4([in] LPWStr s);
    HRESULT PassStringRef1([in, out] BSTR *s);
    HRESULT PassStringRef2([in, out] BSTR *s);
    HRESULT PassStringRef3([in, out] LPStr *s);
    HRESULT PassStringRef4([in, out] LPWStr *s);
};
```

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="f7651-120">Ciągi używane w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="f7651-120">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="f7651-121">Wywołanie platformy kopiuje argumenty ciągu, konwertując z formatu .NET Framework (Unicode) na format niezarządzany platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-121">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="f7651-122">Ciągi są niezmienne i nie są kopiowane z pamięci niezarządzanej do pamięci zarządzanej, gdy wywołanie zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="f7651-122">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="f7651-123">W poniższej tabeli wymieniono opcje kierowania dla ciągów, które są organizowane jako argumenty metody wywołania wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-123">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="f7651-124">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania ciągów.</span><span class="sxs-lookup"><span data-stu-id="f7651-124">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="f7651-125">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f7651-125">Enumeration type</span></span>|<span data-ttu-id="f7651-126">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="f7651-126">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="f7651-127">Styl COM `BSTR` z prefiksem o stałej długości i znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="f7651-127">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="f7651-128">Styl COM `BSTR` o stałej długości i znakach Unicode.</span><span class="sxs-lookup"><span data-stu-id="f7651-128">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="f7651-129">`UnmanagedType.LPStr`wartooć</span><span class="sxs-lookup"><span data-stu-id="f7651-129">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="f7651-130">Wskaźnik do tablicy znaków ANSI zakończonych znakiem null.</span><span class="sxs-lookup"><span data-stu-id="f7651-130">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="f7651-131">Wskaźnik do tablicy zakończonych znakiem NULL znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-131">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="f7651-132">Wskaźnik do tablicy kodowanej za pomocą wartości NULL znaków zakodowanych w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f7651-132">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="f7651-133">Wskaźnik do tablicy znaków Unicode zakończonych wartością null.</span><span class="sxs-lookup"><span data-stu-id="f7651-133">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="f7651-134">Styl COM ze wstępnie `BSTR` ustaloną długością i znakami zależnymi od platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-134">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="f7651-135">Wartość, która umożliwia Visual Basic .NET, aby zmienić ciąg w kodzie niezarządzanym i mieć wyniki odzwierciedlone w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="f7651-135">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="f7651-136">Ta wartość jest obsługiwana tylko w przypadku wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-136">This value is supported only for platform invoke.</span></span> <span data-ttu-id="f7651-137">Jest to wartość domyślna w Visual Basic dla `ByVal` ciągów.</span><span class="sxs-lookup"><span data-stu-id="f7651-137">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="f7651-138">Ta tabela ma zastosowanie do <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="f7651-138">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="f7651-139">W przypadku <xref:System.Text.StringBuilder> opcji Jedynymi dozwolonymi opcjami są `LPStr` , `LPTStr` , i `LPWStr` .</span><span class="sxs-lookup"><span data-stu-id="f7651-139">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="f7651-140">W poniższej definicji typu przedstawiono poprawne użycie wywołań wywołania `MarshalAsAttribute` wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-140">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

```csharp
class StringLibAPI
{
    [DllImport("StringLib.dll")]
    public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPWStr([MarshalAs(UnmanagedType.LPWStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPTStr([MarshalAs(UnmanagedType.LPTStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassLPUTF8Str([MarshalAs(UnmanagedType.LPUTF8Str)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)] string s);
    [DllImport("StringLib.dll")]
    public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)] string s);
}
```

```vb
Class StringLibAPI
    Public Declare Auto Sub PassLPStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPStr)> s As String)
    Public Declare Auto Sub PassLPWStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPWStr)> s As String)
    Public Declare Auto Sub PassLPTStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPTStr)> s As String)
    Public Declare Auto Sub PassLPUTF8Str Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.LPUTF8Str)> s As String)
    Public Declare Auto Sub PassBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.BStr)> s As String)
    Public Declare Auto Sub PassAnsiBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.AnsiBStr)> s As String)
    Public Declare Auto Sub PassTBStr Lib "StringLib.dll" (
        <MarshalAs(UnmanagedType.TBStr)> s As String)
End Class
```

## <a name="strings-used-in-structures"></a><span data-ttu-id="f7651-141">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="f7651-141">Strings Used in Structures</span></span>

<span data-ttu-id="f7651-142">Ciągi są prawidłowymi elementami członkowskimi struktur; jednak <xref:System.Text.StringBuilder> bufory są nieprawidłowe w strukturach.</span><span class="sxs-lookup"><span data-stu-id="f7651-142">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="f7651-143">W poniższej tabeli przedstawiono opcje kierowania dla <xref:System.String> typu danych, gdy typ jest zorganizowany jako pole.</span><span class="sxs-lookup"><span data-stu-id="f7651-143">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="f7651-144">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia, które umożliwiają kierowanie ciągów do pola.</span><span class="sxs-lookup"><span data-stu-id="f7651-144">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="f7651-145">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f7651-145">Enumeration type</span></span>|<span data-ttu-id="f7651-146">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="f7651-146">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="f7651-147">Styl COM `BSTR` o stałej długości i znakach Unicode.</span><span class="sxs-lookup"><span data-stu-id="f7651-147">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="f7651-148">`UnmanagedType.LPStr`wartooć</span><span class="sxs-lookup"><span data-stu-id="f7651-148">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="f7651-149">Wskaźnik do tablicy znaków ANSI zakończonych znakiem null.</span><span class="sxs-lookup"><span data-stu-id="f7651-149">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="f7651-150">Wskaźnik do tablicy zakończonych znakiem NULL znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="f7651-150">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="f7651-151">Wskaźnik do tablicy kodowanej za pomocą wartości NULL znaków zakodowanych w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f7651-151">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="f7651-152">Wskaźnik do tablicy znaków Unicode zakończonych wartością null.</span><span class="sxs-lookup"><span data-stu-id="f7651-152">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="f7651-153">Tablica znaków o stałej długości; typ tablicy jest określany przez zestaw znaków struktury zawierającej.</span><span class="sxs-lookup"><span data-stu-id="f7651-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="f7651-154">`ByValTStr`Typ jest używany w przypadku wbudowanych tablic znaków o stałej długości, które pojawiają się w obrębie struktury.</span><span class="sxs-lookup"><span data-stu-id="f7651-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="f7651-155">Inne typy są stosowane do odwołań do ciągów zawartych w strukturach, które zawierają wskaźniki do ciągów.</span><span class="sxs-lookup"><span data-stu-id="f7651-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="f7651-156">`CharSet`Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> , który jest stosowany do struktury zawierającej, określa format znaków ciągów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="f7651-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="f7651-157">Następujące przykładowe struktury zawierają odwołania do ciągów i ciągi śródwierszowe oraz znaki ANSI, Unicode i.</span><span class="sxs-lookup"><span data-stu-id="f7651-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="f7651-158">Reprezentacja tych struktur w bibliotece typów jest pokazana w następującym kodzie języka C++:</span><span class="sxs-lookup"><span data-stu-id="f7651-158">The representation of these structures in a type library is shown in the following C++ code:</span></span>

```cpp
struct StringInfoA
{
    char *  f1;
    char    f2[256];
};

struct StringInfoW
{
    WCHAR * f1;
    WCHAR   f2[256];
    BSTR    f3;
};

struct StringInfoT
{
    TCHAR * f1;
    TCHAR   f2[256];
};
```

<span data-ttu-id="f7651-159">Poniższy przykład pokazuje, jak używać <xref:System.Runtime.InteropServices.MarshalAsAttribute> do definiowania tej samej struktury w różnych formatach.</span><span class="sxs-lookup"><span data-stu-id="f7651-159">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Ansi)]
struct StringInfoA
{
    [MarshalAs(UnmanagedType.LPStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
struct StringInfoW
{
    [MarshalAs(UnmanagedType.LPWStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
    [MarshalAs(UnmanagedType.BStr)] public string f3;
}

[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Auto)]
struct StringInfoT
{
    [MarshalAs(UnmanagedType.LPTStr)] public string f1;
    [MarshalAs(UnmanagedType.ByValTStr, SizeConst = 256)] public string f2;
}
```

```vb
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _
Structure StringInfoA
    <MarshalAs(UnmanagedType.LPStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _
Structure StringInfoW
    <MarshalAs(UnmanagedType.LPWStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
<MarshalAs(UnmanagedType.BStr)> Public f3 As String
End Structure

<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _
Structure StringInfoT
    <MarshalAs(UnmanagedType.LPTStr)> Public f1 As String
    <MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _
    Public f2 As String
End Structure
```

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="f7651-160">Bufory ciągów o stałej długości</span><span class="sxs-lookup"><span data-stu-id="f7651-160">Fixed-Length String Buffers</span></span>

<span data-ttu-id="f7651-161">W pewnych okolicznościach bufor znaków o stałej długości musi być przekazywać do kodu niezarządzanego w celu manipulowania.</span><span class="sxs-lookup"><span data-stu-id="f7651-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="f7651-162">Po prostu przekazanie ciągu nie działa w tym przypadku, ponieważ element wywoływany nie może modyfikować zawartości przekazywanego buforu.</span><span class="sxs-lookup"><span data-stu-id="f7651-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="f7651-163">Nawet jeśli ciąg jest przekazywane przez odwołanie, nie ma możliwości zainicjowania buforu do danego rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="f7651-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="f7651-164">Rozwiązaniem jest przekazanie <xref:System.Text.StringBuilder> buforu jako argumentu zamiast <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="f7651-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="f7651-165">`StringBuilder`Można wycofać odwołanie i zmodyfikować go przez wywoływany, pod warunkiem, że nie przekracza on pojemności `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="f7651-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="f7651-166">Można go również zainicjować na stałą długość.</span><span class="sxs-lookup"><span data-stu-id="f7651-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="f7651-167">Na przykład, jeśli zainicjujesz `StringBuilder` bufor do pojemności `N` , organizator udostępnia bufor o rozmiarze ( `N` + 1).</span><span class="sxs-lookup"><span data-stu-id="f7651-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="f7651-168">Konta + 1 dla faktu, że niezarządzany ciąg ma terminator o wartości null, a nie `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="f7651-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="f7651-169">Na przykład [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) Funkcja Windows API (zdefiniowana w *Winuser. h*) wymaga, aby obiekt wywołujący przeszedł bufor znaków o stałej długości, do którego funkcja zapisuje tekst okna.</span><span class="sxs-lookup"><span data-stu-id="f7651-169">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *winuser.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="f7651-170">`LpString`wskazuje bufor rozmiaru przydzieloną przez wywołującego `nMaxCount` .</span><span class="sxs-lookup"><span data-stu-id="f7651-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="f7651-171">Obiekt wywołujący oczekuje na przydzielenie buforu i ustawienie `nMaxCount` argumentu na rozmiar przydzielonego buforu.</span><span class="sxs-lookup"><span data-stu-id="f7651-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="f7651-172">W poniższym przykładzie pokazano `GetWindowText` deklarację funkcji, zgodnie z definicją w *Winuser. h*.</span><span class="sxs-lookup"><span data-stu-id="f7651-172">The following example shows the `GetWindowText` function declaration as defined in *winuser.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="f7651-173">`StringBuilder`Można wycofać odwołanie i zmodyfikować go przez wywoływany, pod warunkiem, że nie przekracza on pojemności `StringBuilder` .</span><span class="sxs-lookup"><span data-stu-id="f7651-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="f7651-174">Poniższy przykład kodu demonstruje, jak `StringBuilder` można zainicjować o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="f7651-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;
using System.Text;

internal static class NativeMethods
{
    [DllImport("User32.dll")]
    internal static extern void GetWindowText(IntPtr hWnd, StringBuilder lpString, int nMaxCount);
}

public class Window
{
    internal IntPtr h;        // Internal handle to Window.
    public String GetText()
    {
        StringBuilder sb = new StringBuilder(256);
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Imports System.Text

Friend Class NativeMethods
    Friend Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        NativeMethods.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="f7651-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7651-175">See also</span></span>

- [<span data-ttu-id="f7651-176">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="f7651-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="f7651-177">Organizowanie ciągów</span><span class="sxs-lookup"><span data-stu-id="f7651-177">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="f7651-178">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="f7651-178">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="f7651-179">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f7651-179">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="f7651-180">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="f7651-180">Copying and Pinning</span></span>](copying-and-pinning.md)
