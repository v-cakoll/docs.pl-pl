---
title: Organizowanie domyślne dotyczące ciągów
ms.date: 03/20/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c07747c5100f6f7b7ee80b2e7e39d22362698e4
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807829"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="49966-102">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="49966-102">Default Marshaling for Strings</span></span>

<span data-ttu-id="49966-103">Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy mają podobne zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="49966-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>

<span data-ttu-id="49966-104">Parametry są przekazywane jako styl modelu COM `BSTR` typu lub jako ciąg zakończony znakiem null (tablicy znaków zakończony znakiem null).</span><span class="sxs-lookup"><span data-stu-id="49966-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="49966-105">Znaki ciągu może być organizowany jako Unicode (domyślnie w systemach Windows) lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="49966-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="49966-106">Ciągi używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="49966-106">Strings Used in Interfaces</span></span>

<span data-ttu-id="49966-107">W poniższej tabeli przedstawiono opcje kierowania dla typu danych string podczas przekazywania jako argumentu metody do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="49966-107">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="49966-108"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów COM interfejsy wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="49966-108">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>

|<span data-ttu-id="49966-109">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="49966-109">Enumeration type</span></span>|<span data-ttu-id="49966-110">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="49966-110">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|<span data-ttu-id="49966-111">`UnmanagedType.BStr` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="49966-111">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="49966-112">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="49966-112">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|`UnmanagedType.LPStr`|<span data-ttu-id="49966-113">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="49966-113">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="49966-114">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="49966-114">A pointer to a null-terminated array of Unicode characters.</span></span>|

<span data-ttu-id="49966-115">Ta tabela ma zastosowanie do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49966-115">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="49966-116">Aby uzyskać <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="49966-116">For <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>

<span data-ttu-id="49966-117">W poniższym przykładzie pokazano ciągów, zadeklarowanej w `IStringWorker` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="49966-117">The following example shows strings declared in the `IStringWorker` interface.</span></span>

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

<span data-ttu-id="49966-118">Poniższy przykład pokazuje odpowiedniego interfejsu opisanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="49966-118">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="49966-119">Wywoływanie ciągów używanych w platformy</span><span class="sxs-lookup"><span data-stu-id="49966-119">Strings Used in Platform Invoke</span></span>

<span data-ttu-id="49966-120">Argumenty typu string kopii, konwertowania z formatu .NET Framework (Unicode) do formatu niezarządzanych platformy wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-120">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="49966-121">Ciągów są niezmienne i nie są kopiowane z niezarządzanej pamięci zarządzanej pamięci podczas to wywołanie zwraca.</span><span class="sxs-lookup"><span data-stu-id="49966-121">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>

<span data-ttu-id="49966-122">Poniższa tabela zawiera opcje marshaling dla ciągów, gdy organizowany jako argumentu metody platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="49966-122">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="49966-123"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="49966-123">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>

|<span data-ttu-id="49966-124">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="49966-124">Enumeration type</span></span>|<span data-ttu-id="49966-125">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="49966-125">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="49966-126">Styl modelu COM `BSTR` z prefiksem długości i znaki ANSI.</span><span class="sxs-lookup"><span data-stu-id="49966-126">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|
|`UnmanagedType.BStr`|<span data-ttu-id="49966-127">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="49966-127">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="49966-128">`UnmanagedType.LPStr` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="49966-128">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="49966-129">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="49966-129">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="49966-130">Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-130">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="49966-131">Wskaźnik do tablicą zakończoną znakiem null UTF-8 zakodowanych znaków.</span><span class="sxs-lookup"><span data-stu-id="49966-131">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="49966-132">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="49966-132">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.TBStr`|<span data-ttu-id="49966-133">Styl modelu COM `BSTR` z prefiksem długości i znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-133">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|
|`VBByRefStr`|<span data-ttu-id="49966-134">Wartość, która umożliwia Visual Basic .NET zmienić parametry w kod niezarządzany i mieć wyniki zostaną uwzględnione w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="49966-134">A value that enables Visual Basic .NET to change a string in unmanaged code and have the results reflected in managed code.</span></span> <span data-ttu-id="49966-135">Ta wartość jest obsługiwana tylko w przypadku wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-135">This value is supported only for platform invoke.</span></span> <span data-ttu-id="49966-136">Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.</span><span class="sxs-lookup"><span data-stu-id="49966-136">This is the default value in Visual Basic for `ByVal` strings.</span></span>|

<span data-ttu-id="49966-137">Ta tabela ma zastosowanie do <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49966-137">This table applies to <xref:System.String>.</span></span> <span data-ttu-id="49966-138">Aby uzyskać <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `LPStr`, `LPTStr`, i `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="49966-138">For <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>

<span data-ttu-id="49966-139">Następująca definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="49966-139">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>

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

## <a name="strings-used-in-structures"></a><span data-ttu-id="49966-140">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="49966-140">Strings Used in Structures</span></span>

<span data-ttu-id="49966-141">Ciągi są prawidłowe elementy członkowskie struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach.</span><span class="sxs-lookup"><span data-stu-id="49966-141">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="49966-142">W poniższej tabeli przedstawiono opcje kierowania <xref:System.String> typ danych, gdy typ jest organizowana jako pole.</span><span class="sxs-lookup"><span data-stu-id="49966-142">The following table shows the marshaling options for the <xref:System.String> data type when the type is marshaled as a field.</span></span> <span data-ttu-id="49966-143"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów do pola wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="49966-143">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>

|<span data-ttu-id="49966-144">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="49966-144">Enumeration type</span></span>|<span data-ttu-id="49966-145">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="49966-145">Description of unmanaged format</span></span>|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|<span data-ttu-id="49966-146">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="49966-146">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|
|<span data-ttu-id="49966-147">`UnmanagedType.LPStr` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="49966-147">`UnmanagedType.LPStr` (default)</span></span>|<span data-ttu-id="49966-148">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="49966-148">A pointer to a null-terminated array of ANSI characters.</span></span>|
|`UnmanagedType.LPTStr`|<span data-ttu-id="49966-149">Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-149">A pointer to a null-terminated array of platform-dependent characters.</span></span>|
|`UnmanagedType.LPUTF8Str`|<span data-ttu-id="49966-150">Wskaźnik do tablicą zakończoną znakiem null UTF-8 zakodowanych znaków.</span><span class="sxs-lookup"><span data-stu-id="49966-150">A pointer to a null-terminated array of UTF-8 encoded characters.</span></span>|
|`UnmanagedType.LPWStr`|<span data-ttu-id="49966-151">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="49966-151">A pointer to a null-terminated array of Unicode characters.</span></span>|
|`UnmanagedType.ByValTStr`|<span data-ttu-id="49966-152">Tablica o stałej długości, znaków; Typ tablicy jest ustalany przez zestaw znaków zawierającą strukturę.</span><span class="sxs-lookup"><span data-stu-id="49966-152">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|

<span data-ttu-id="49966-153">`ByValTStr` Typ jest używany do wbudowanych tablic znaków o stałej długości, które pojawiają się w ramach struktury.</span><span class="sxs-lookup"><span data-stu-id="49966-153">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="49966-154">Inne typy mają zastosowanie do odwołania ciągu zawarte w obrębie struktury, które zawierają wskaźnikami do ciągów.</span><span class="sxs-lookup"><span data-stu-id="49966-154">Other types apply to string references contained within structures that contain pointers to strings.</span></span>

<span data-ttu-id="49966-155">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> mający zastosowanie do zawierający struktury Określa format znaków z ciągów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="49966-155">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="49966-156">Następujące przykładowe struktury zawierają ciąg odwołania i ciągi wbudowane, a także ANSI, Unicode i znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="49966-156">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span> <span data-ttu-id="49966-157">Reprezentacja tych struktur w bibliotece typów przedstawiono w następującym C++ kodu:</span><span class="sxs-lookup"><span data-stu-id="49966-157">The representation of these structures in a type library is shown in the following C++ code:</span></span>

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

<span data-ttu-id="49966-158">Poniższy przykład pokazuje, jak używać <xref:System.Runtime.InteropServices.MarshalAsAttribute> zdefiniować tę samą strukturę w różnych formatach.</span><span class="sxs-lookup"><span data-stu-id="49966-158">The following example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> to define the same structure in different formats.</span></span>

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

## <a name="fixed-length-string-buffers"></a><span data-ttu-id="49966-159">Bufory o stałej długości ciągu</span><span class="sxs-lookup"><span data-stu-id="49966-159">Fixed-Length String Buffers</span></span>

<span data-ttu-id="49966-160">W pewnych okolicznościach buforu znaków o stałej długości muszą być przekazywane do kodu niezarządzanego, aby być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="49966-160">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="49966-161">Po prostu przekazując ciąg nie działa w tym przypadku, ponieważ obiekt wywoływany nie można zmodyfikować zawartość przekazanego buforu.</span><span class="sxs-lookup"><span data-stu-id="49966-161">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="49966-162">Nawet jeśli ten ciąg jest przekazywany przez odwołanie, nie ma możliwości zainicjować buforu na dany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="49966-162">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>

<span data-ttu-id="49966-163">To rozwiązanie służy do przekazywania <xref:System.Text.StringBuilder> buforu jako argument zamiast <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="49966-163">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a <xref:System.String>.</span></span> <span data-ttu-id="49966-164">A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="49966-164">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="49966-165">Ponadto może zostać zainicjowane do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="49966-165">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="49966-166">Na przykład, jeśli należy zainicjować `StringBuilder` buforu na pojemność `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków.</span><span class="sxs-lookup"><span data-stu-id="49966-166">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="49966-167">Konta + 1 fakt, że niezarządzanego ciągu ma terminatora null podczas `StringBuilder` nie.</span><span class="sxs-lookup"><span data-stu-id="49966-167">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>

<span data-ttu-id="49966-168">Na przykład Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) funkcji interfejsu API (zdefiniowane w *Windows.h*) wymaga, że obiekt wywołujący przekazywać buforu znaków o stałej długości, do której funkcja zapisuje tekst okna.</span><span class="sxs-lookup"><span data-stu-id="49966-168">For example, the Windows [`GetWindowText`](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) API function (defined in *Windows.h*) requires that the caller pass a fixed-length character buffer to which the function writes the window's text.</span></span> <span data-ttu-id="49966-169">`LpString` Wskazuje przydzielonej przez obiekt wywołujący bufor o rozmiarze `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="49966-169">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="49966-170">Obiekt wywołujący oczekuje się, aby przydzielić bufor i ustawić `nMaxCount` argumentu rozmiaru przydzielonego buforu.</span><span class="sxs-lookup"><span data-stu-id="49966-170">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="49966-171">W poniższym przykładzie przedstawiono `GetWindowText` deklaracji funkcji, zgodnie z definicją w *Windows.h*.</span><span class="sxs-lookup"><span data-stu-id="49966-171">The following example shows the `GetWindowText` function declaration as defined in *Windows.h*.</span></span>

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

<span data-ttu-id="49966-172">A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="49966-172">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="49966-173">Poniższy przykład kodu demonstruje sposób `StringBuilder` może być inicjowany do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="49966-173">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>

```csharp
internal static class WindowsAPI
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
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1);
        return sb.ToString();
    }
}
```

```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetWindowText Lib "User32.dll" _
        (hWnd As IntPtr, lpString As StringBuilder, nMaxCount As Integer)
End Class

Public Class Window
    Friend h As IntPtr ' Friend handle to Window.
    Public Function GetText() As String
        Dim sb As New StringBuilder(256)
        WindowsAPI.GetWindowText(h, sb, sb.Capacity + 1)
        Return sb.ToString()
   End Function
End Class
```

## <a name="see-also"></a><span data-ttu-id="49966-174">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="49966-174">See also</span></span>

- [<span data-ttu-id="49966-175">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="49966-175">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="49966-176">Marshaling ciągów</span><span class="sxs-lookup"><span data-stu-id="49966-176">Marshaling Strings</span></span>](marshaling-strings.md)
- [<span data-ttu-id="49966-177">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="49966-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="49966-178">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="49966-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="49966-179">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="49966-179">Copying and Pinning</span></span>](copying-and-pinning.md)
