---
title: Organizowanie domyślne dotyczące ciągów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df65f54a9a7408a22f8b558f99ab42d6c37ae55b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221072"
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="17975-102">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="17975-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="17975-103">Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy mają podobne zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="17975-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="17975-104">Parametry są przekazywane jako styl modelu COM `BSTR` typu lub jako ciąg zakończony znakiem null (tablicy znaków zakończony znakiem null).</span><span class="sxs-lookup"><span data-stu-id="17975-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="17975-105">Znaki ciągu może być organizowany jako Unicode (domyślnie w systemach Windows) lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="17975-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="17975-106">Ten temat zawiera następujące informacje dotyczące marshaling typów ciągów:</span><span class="sxs-lookup"><span data-stu-id="17975-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="17975-107">Ciągi używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="17975-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="17975-108">Wywoływanie ciągów używanych w platformy</span><span class="sxs-lookup"><span data-stu-id="17975-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="17975-109">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="17975-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="17975-110">Bufory o stałej długości ciągu</span><span class="sxs-lookup"><span data-stu-id="17975-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="17975-111">Ciągi używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="17975-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="17975-112">W poniższej tabeli przedstawiono opcje kierowania dla typu danych string podczas przekazywania jako argumentu metody do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="17975-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="17975-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów COM interfejsy wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="17975-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="17975-114">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="17975-114">Enumeration type</span></span>|<span data-ttu-id="17975-115">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="17975-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="17975-116">`UnmanagedType.BStr` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="17975-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="17975-117">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="17975-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="17975-118">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="17975-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="17975-119">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="17975-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="17975-120">Ta tabela ma zastosowanie do ciągów.</span><span class="sxs-lookup"><span data-stu-id="17975-120">This table applies to strings.</span></span> <span data-ttu-id="17975-121">Jednak w przypadku <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="17975-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="17975-122">W poniższym przykładzie pokazano ciągów, zadeklarowanej w `IStringWorker` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="17975-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);
```

<span data-ttu-id="17975-123">Poniższy przykład pokazuje odpowiedniego interfejsu opisanych w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="17975-123">The following example shows the corresponding interface described in a type library.</span></span>

```
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);
```

<a name="cpcondefaultmarshalingforstringsanchor5"></a>

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="17975-124">Wywoływanie ciągów używanych w platformy</span><span class="sxs-lookup"><span data-stu-id="17975-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="17975-125">Argumenty typu string kopii, konwertowania z formatu .NET Framework (Unicode) do formatu niezarządzanych platformy wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="17975-126">Ciągów są niezmienne i nie są kopiowane z niezarządzanej pamięci zarządzanej pamięci podczas to wywołanie zwraca.</span><span class="sxs-lookup"><span data-stu-id="17975-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="17975-127">Poniższa tabela zawiera opcje marshaling dla ciągów, gdy organizowany jako argumentu metody platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="17975-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="17975-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="17975-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="17975-129">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="17975-129">Enumeration type</span></span>|<span data-ttu-id="17975-130">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="17975-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="17975-131">Styl modelu COM `BSTR` z prefiksem długości i znaki ANSI.</span><span class="sxs-lookup"><span data-stu-id="17975-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="17975-132">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="17975-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="17975-133">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="17975-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="17975-134">Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="17975-135">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="17975-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="17975-136">Styl modelu COM `BSTR` z prefiksem długości i znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="17975-137">Wartość, która umożliwia Visual Basic .NET zmienić parametry w kod niezarządzany, a masz wyniki zostaną uwzględnione w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="17975-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="17975-138">Ta wartość jest obsługiwana tylko w przypadku wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="17975-139">Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.</span><span class="sxs-lookup"><span data-stu-id="17975-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="17975-140">Ta tabela ma zastosowanie do ciągów.</span><span class="sxs-lookup"><span data-stu-id="17975-140">This table applies to strings.</span></span> <span data-ttu-id="17975-141">Jednak w przypadku <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `LPStr`, `LPTStr`, i `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="17975-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="17975-142">Następująca definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania.</span><span class="sxs-lookup"><span data-stu-id="17975-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```

```csharp
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a><span data-ttu-id="17975-143">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="17975-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="17975-144">Ciągi są prawidłowe elementy członkowskie struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach.</span><span class="sxs-lookup"><span data-stu-id="17975-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="17975-145">W poniższej tabeli przedstawiono opcje kierowania string — typ danych, gdy typ jest organizowana jako pole.</span><span class="sxs-lookup"><span data-stu-id="17975-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="17975-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów do pola wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="17975-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="17975-147">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="17975-147">Enumeration type</span></span>|<span data-ttu-id="17975-148">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="17975-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="17975-149">Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="17975-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="17975-150">Wskaźnik do tablicy znaków ANSI zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="17975-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="17975-151">Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="17975-152">Wskaźnik do tablicy znaków Unicode zakończony wartością null.</span><span class="sxs-lookup"><span data-stu-id="17975-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="17975-153">Tablica o stałej długości, znaków; Typ tablicy jest ustalany przez zestaw znaków zawierającą strukturę.</span><span class="sxs-lookup"><span data-stu-id="17975-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="17975-154">`ByValTStr` Typ jest używany do wbudowanych tablic znaków o stałej długości, które pojawiają się w ramach struktury.</span><span class="sxs-lookup"><span data-stu-id="17975-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="17975-155">Inne typy mają zastosowanie do odwołania ciągu zawarte w obrębie struktury, które zawierają wskaźnikami do ciągów.</span><span class="sxs-lookup"><span data-stu-id="17975-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="17975-156">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który jest stosowany do struktury zawierającej Określa format znaków z ciągów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="17975-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="17975-157">Następujące przykładowe struktury zawierają ciąg odwołania i ciągi wbudowane, a także ANSI, Unicode i znaków zależnych od platformy.</span><span class="sxs-lookup"><span data-stu-id="17975-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="17975-158">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="17975-158">Type Library Representation</span></span>  
  
```
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 <span data-ttu-id="17975-159">Poniższy przykład kodu pokazuje sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do definiowania tę samą strukturę w różnych formatach.</span><span class="sxs-lookup"><span data-stu-id="17975-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
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
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="17975-160">Bufory o stałej długości ciągu</span><span class="sxs-lookup"><span data-stu-id="17975-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="17975-161">W pewnych okolicznościach buforu znaków o stałej długości muszą być przekazywane do kodu niezarządzanego, aby być zmieniane.</span><span class="sxs-lookup"><span data-stu-id="17975-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="17975-162">Po prostu przekazując ciąg nie działa w tym przypadku, ponieważ obiekt wywoływany nie można zmodyfikować zawartość przekazanego buforu.</span><span class="sxs-lookup"><span data-stu-id="17975-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="17975-163">Nawet jeśli ten ciąg jest przekazywany przez odwołanie, nie ma możliwości zainicjować buforu na dany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="17975-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="17975-164">To rozwiązanie służy do przekazywania <xref:System.Text.StringBuilder> buforu jako argument zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="17975-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="17975-165">A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="17975-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="17975-166">Ponadto może zostać zainicjowane do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="17975-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="17975-167">Na przykład, jeśli należy zainicjować `StringBuilder` buforu na pojemność `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków.</span><span class="sxs-lookup"><span data-stu-id="17975-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="17975-168">Konta + 1 fakt, że niezarządzanego ciągu ma terminatora null podczas `StringBuilder` nie.</span><span class="sxs-lookup"><span data-stu-id="17975-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="17975-169">Na przykład Microsoft Win32 API `GetWindowText` — funkcja (zdefiniowanymi w Windows.h) to muszą być przekazywane do kodu niezarządzanego ustawianych bufor znaków o stałej długości.</span><span class="sxs-lookup"><span data-stu-id="17975-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="17975-170">`LpString` Wskazuje przydzielonej przez obiekt wywołujący bufor o rozmiarze `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="17975-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="17975-171">Obiekt wywołujący oczekuje się, aby przydzielić bufor i ustawić `nMaxCount` argumentu rozmiaru przydzielonego buforu.</span><span class="sxs-lookup"><span data-stu-id="17975-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="17975-172">Poniższy kod przedstawia `GetWindowText` deklaracji funkcji, zgodnie z definicją w Windows.h.</span><span class="sxs-lookup"><span data-stu-id="17975-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="17975-173">A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="17975-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="17975-174">Poniższy przykład kodu demonstruje sposób `StringBuilder` może być inicjowany do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="17975-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="17975-175">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17975-175">See also</span></span>
- [<span data-ttu-id="17975-176">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="17975-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="17975-177">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="17975-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="17975-178">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="17975-178">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="17975-179">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="17975-179">Copying and Pinning</span></span>](copying-and-pinning.md)
