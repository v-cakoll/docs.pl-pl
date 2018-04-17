---
title: Organizowanie domyślne dotyczące ciągów
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 10f2c0e0e61190f571ae5bd4998f54d128448296
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="default-marshaling-for-strings"></a><span data-ttu-id="26071-102">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="26071-102">Default Marshaling for Strings</span></span>
<span data-ttu-id="26071-103">Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy zachowują się podobnie kierowania.</span><span class="sxs-lookup"><span data-stu-id="26071-103">Both the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes have similar marshaling behavior.</span></span>  
  
 <span data-ttu-id="26071-104">Parametry są przekazywane jako styl modelu COM `BSTR` typu lub w postaci ciągu zakończonego wartością null (znak tablica, która kończy się znakiem null).</span><span class="sxs-lookup"><span data-stu-id="26071-104">Strings are marshaled as a COM-style `BSTR` type or as a null-terminated string (a character array that ends with a null character).</span></span> <span data-ttu-id="26071-105">Znaki w ciągu mogą być przekazywane jako Unicode (domyślnie w systemach Windows) lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="26071-105">The characters within the string can be marshaled as Unicode (the default on Windows systems) or ANSI.</span></span>  
  
 <span data-ttu-id="26071-106">Ten temat zawiera następujące informacje na przekazywanie typów ciąg:</span><span class="sxs-lookup"><span data-stu-id="26071-106">This topic provides the following information on marshaling string types:</span></span>  
  
-   [<span data-ttu-id="26071-107">Parametry używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="26071-107">Strings Used in Interfaces</span></span>](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [<span data-ttu-id="26071-108">Wywołanie ciągów używanych na platformie</span><span class="sxs-lookup"><span data-stu-id="26071-108">Strings Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [<span data-ttu-id="26071-109">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="26071-109">Strings Used in Structures</span></span>](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [<span data-ttu-id="26071-110">Bufory o stałej długości ciągu</span><span class="sxs-lookup"><span data-stu-id="26071-110">Fixed-Length String Buffers</span></span>](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a><span data-ttu-id="26071-111">Parametry używane w interfejsach</span><span class="sxs-lookup"><span data-stu-id="26071-111">Strings Used in Interfaces</span></span>  
 <span data-ttu-id="26071-112">W poniższej tabeli przedstawiono opcje organizowania dla typu danych string podczas organizowane jako argument metody do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="26071-112">The following table shows the marshaling options for the string data type when marshaled as a method argument to unmanaged code.</span></span> <span data-ttu-id="26071-113"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> kierowanie ciągów do interfejsów modelu COM wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="26071-113">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to COM interfaces.</span></span>  
  
|<span data-ttu-id="26071-114">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="26071-114">Enumeration type</span></span>|<span data-ttu-id="26071-115">Opis formatu niezarządzane</span><span class="sxs-lookup"><span data-stu-id="26071-115">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="26071-116">`UnmanagedType.BStr` (ustawienie domyślne)</span><span class="sxs-lookup"><span data-stu-id="26071-116">`UnmanagedType.BStr` (default)</span></span>|<span data-ttu-id="26071-117">Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="26071-117">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="26071-118">Wskaźnik do tablicy znaków ANSI zerem.</span><span class="sxs-lookup"><span data-stu-id="26071-118">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="26071-119">Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.</span><span class="sxs-lookup"><span data-stu-id="26071-119">A pointer to a null-terminated array of Unicode characters.</span></span>|  
  
 <span data-ttu-id="26071-120">Ta tabela odnosi się do ciągów.</span><span class="sxs-lookup"><span data-stu-id="26071-120">This table applies to strings.</span></span> <span data-ttu-id="26071-121">Niemniej jednak w przypadku <xref:System.Text.StringBuilder>, czy można używać wyłącznie opcji `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="26071-121">However, for <xref:System.Text.StringBuilder>, the only options allowed are `UnmanagedType.LPStr` and `UnmanagedType.LPWStr`.</span></span>  
  
 <span data-ttu-id="26071-122">W poniższym przykładzie przedstawiono ciągi zadeklarowany w `IStringWorker` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="26071-122">The following example shows strings declared in the `IStringWorker` interface.</span></span>  
  
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

<span data-ttu-id="26071-123">W poniższym przykładzie przedstawiono odpowiedniego interfejsu opisanego w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="26071-123">The following example shows the corresponding interface described in a type library.</span></span>

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

## <a name="strings-used-in-platform-invoke"></a><span data-ttu-id="26071-124">Wywołanie ciągów używanych na platformie</span><span class="sxs-lookup"><span data-stu-id="26071-124">Strings Used in Platform Invoke</span></span>  
 <span data-ttu-id="26071-125">Wywołanie platformy argumenty typu string kopie, konwersji z formatu .NET Framework (Unicode) do formatu niezarządzane platformy.</span><span class="sxs-lookup"><span data-stu-id="26071-125">Platform invoke copies string arguments, converting from the .NET Framework format (Unicode) to the platform unmanaged format.</span></span> <span data-ttu-id="26071-126">Ciągi są niezmienne i nie są kopiowane z niezarządzanej pamięci do pamięci zarządzanej po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="26071-126">Strings are immutable and are not copied back from unmanaged memory to managed memory when the call returns.</span></span>  
  
 <span data-ttu-id="26071-127">W poniższej tabeli wymieniono opcje organizowania ciągów, gdy organizowane jako argument metody platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="26071-127">The following table lists the marshaling options for strings when marshaled as a method argument of a platform invoke call.</span></span> <span data-ttu-id="26071-128"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie ciągów.</span><span class="sxs-lookup"><span data-stu-id="26071-128">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings.</span></span>  
  
|<span data-ttu-id="26071-129">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="26071-129">Enumeration type</span></span>|<span data-ttu-id="26071-130">Opis formatu niezarządzane</span><span class="sxs-lookup"><span data-stu-id="26071-130">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|<span data-ttu-id="26071-131">Styl modelu COM `BSTR` z prefiksem długość i znaków ANSI.</span><span class="sxs-lookup"><span data-stu-id="26071-131">A COM-style `BSTR` with a prefixed length and ANSI characters.</span></span>|  
|`UnmanagedType.BStr`|<span data-ttu-id="26071-132">Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="26071-132">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="26071-133">Wskaźnik do tablicy znaków ANSI zerem.</span><span class="sxs-lookup"><span data-stu-id="26071-133">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="26071-134">Wskaźnik do tablicy znaków zależny od platformy zerem.</span><span class="sxs-lookup"><span data-stu-id="26071-134">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="26071-135">Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.</span><span class="sxs-lookup"><span data-stu-id="26071-135">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.TBStr`|<span data-ttu-id="26071-136">Styl modelu COM `BSTR` z prefiksem długość i znaki zależny od platformy.</span><span class="sxs-lookup"><span data-stu-id="26071-136">A COM-style `BSTR` with a prefixed length and platform-dependent characters.</span></span>|  
|`VBByRefStr`|<span data-ttu-id="26071-137">Wartość, która umożliwia Visual Basic .NET zmienić parametry w niezarządzanych kodu, a wyniki odzwierciedla w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="26071-137">A value that enables Visual Basic .NET to change a string in unmanaged code, and have the results reflected in managed code.</span></span> <span data-ttu-id="26071-138">Ta wartość jest obsługiwana tylko przez wywołanie platformy.</span><span class="sxs-lookup"><span data-stu-id="26071-138">This value is supported only for platform invoke.</span></span> <span data-ttu-id="26071-139">Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.</span><span class="sxs-lookup"><span data-stu-id="26071-139">This is default value in Visual Basic for `ByVal` strings.</span></span>|  
  
 <span data-ttu-id="26071-140">Ta tabela odnosi się do ciągów.</span><span class="sxs-lookup"><span data-stu-id="26071-140">This table applies to strings.</span></span> <span data-ttu-id="26071-141">Niemniej jednak w przypadku <xref:System.Text.StringBuilder>, czy można używać wyłącznie opcji `LPStr`, `LPTStr`, i `LPWStr`.</span><span class="sxs-lookup"><span data-stu-id="26071-141">However, for <xref:System.Text.StringBuilder>, the only options allowed are `LPStr`, `LPTStr`, and `LPWStr`.</span></span>  
  
 <span data-ttu-id="26071-142">Następujące definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="26071-142">The following type definition shows the correct use of `MarshalAsAttribute` for platform invoke calls.</span></span>  
  
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
## <a name="strings-used-in-structures"></a><span data-ttu-id="26071-143">Ciągi używane w strukturach</span><span class="sxs-lookup"><span data-stu-id="26071-143">Strings Used in Structures</span></span>  
 <span data-ttu-id="26071-144">Parametry są prawidłowe członków struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach.</span><span class="sxs-lookup"><span data-stu-id="26071-144">Strings are valid members of structures; however, <xref:System.Text.StringBuilder> buffers are invalid in structures.</span></span> <span data-ttu-id="26071-145">W poniższej tabeli przedstawiono opcje organizowania string — typ danych, gdy typ jest przekazywane jako pole.</span><span class="sxs-lookup"><span data-stu-id="26071-145">The following table shows the marshaling options for the string data type when the type is marshaled as a field.</span></span> <span data-ttu-id="26071-146"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie ciągów do pola.</span><span class="sxs-lookup"><span data-stu-id="26071-146">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal strings to a field.</span></span>  
  
|<span data-ttu-id="26071-147">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="26071-147">Enumeration type</span></span>|<span data-ttu-id="26071-148">Opis formatu niezarządzane</span><span class="sxs-lookup"><span data-stu-id="26071-148">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|<span data-ttu-id="26071-149">Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.</span><span class="sxs-lookup"><span data-stu-id="26071-149">A COM-style `BSTR` with a prefixed length and Unicode characters.</span></span>|  
|`UnmanagedType.LPStr`|<span data-ttu-id="26071-150">Wskaźnik do tablicy znaków ANSI zerem.</span><span class="sxs-lookup"><span data-stu-id="26071-150">A pointer to a null-terminated array of ANSI characters.</span></span>|  
|`UnmanagedType.LPTStr`|<span data-ttu-id="26071-151">Wskaźnik do tablicy znaków zależny od platformy zerem.</span><span class="sxs-lookup"><span data-stu-id="26071-151">A pointer to a null-terminated array of platform-dependent characters.</span></span>|  
|`UnmanagedType.LPWStr`|<span data-ttu-id="26071-152">Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.</span><span class="sxs-lookup"><span data-stu-id="26071-152">A pointer to a null-terminated array of Unicode characters.</span></span>|  
|`UnmanagedType.ByValTStr`|<span data-ttu-id="26071-153">O stałej długości tablicy znaków; Typ tablicy jest określana przez struktury zawierającej zestaw znaków.</span><span class="sxs-lookup"><span data-stu-id="26071-153">A fixed-length array of characters; the array's type is determined by the character set of the containing structure.</span></span>|  
  
 <span data-ttu-id="26071-154">`ByValTStr` Typ jest używany dla wbudowanego, tablice o stałej długości znaków, które pojawiają się w ramach struktury.</span><span class="sxs-lookup"><span data-stu-id="26071-154">The `ByValTStr` type is used for inline, fixed-length character arrays that appear within a structure.</span></span> <span data-ttu-id="26071-155">Inne typy są stosowane do odwołania ciągu zawartych wewnątrz struktur, które zawierają wskaźniki do ciągów.</span><span class="sxs-lookup"><span data-stu-id="26071-155">Other types apply to string references contained within structures that contain pointers to strings.</span></span>  
  
 <span data-ttu-id="26071-156">`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który jest stosowany do struktury zawierające Określa format znaków ciągów w strukturach.</span><span class="sxs-lookup"><span data-stu-id="26071-156">The `CharSet` argument of the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute that is applied to the containing structure determines the character format of strings in structures.</span></span> <span data-ttu-id="26071-157">Następujące struktury przykład zawiera odwołania do ciągu i ciągi wbudowany, a także ANSI, Unicode i znaków zależny od platformy.</span><span class="sxs-lookup"><span data-stu-id="26071-157">The following example structures contain string references and inline strings, as well as ANSI, Unicode, and platform-dependent characters.</span></span>  
  
### <a name="type-library-representation"></a><span data-ttu-id="26071-158">Reprezentacja typu biblioteki</span><span class="sxs-lookup"><span data-stu-id="26071-158">Type Library Representation</span></span>  
  
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
  
 <span data-ttu-id="26071-159">Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do definiowania tej samej struktury w różnych formatach.</span><span class="sxs-lookup"><span data-stu-id="26071-159">The following code example shows how to use the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to define the same structure in different formats.</span></span>  
  
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
## <a name="fixed-length-string-buffers"></a><span data-ttu-id="26071-160">Bufory o stałej długości ciągu</span><span class="sxs-lookup"><span data-stu-id="26071-160">Fixed-Length String Buffers</span></span>  
 <span data-ttu-id="26071-161">W niektórych sytuacjach buforu o stałej długości znaków muszą być przekazywane do kodu niezarządzanego można manipulować.</span><span class="sxs-lookup"><span data-stu-id="26071-161">In some circumstances, a fixed-length character buffer must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="26071-162">Po prostu przekazywanie ciągu nie działa, w tym przypadku ponieważ wywoływany nie można zmodyfikować zawartości buforu przekazany.</span><span class="sxs-lookup"><span data-stu-id="26071-162">Simply passing a string does not work in this case because the callee cannot modify the contents of the passed buffer.</span></span> <span data-ttu-id="26071-163">Nawet jeśli ciąg jest przekazywana przez odwołanie, nie istnieje sposób Inicjowanie buforu na dany rozmiar.</span><span class="sxs-lookup"><span data-stu-id="26071-163">Even if the string is passed by reference, there is no way to initialize the buffer to a given size.</span></span>  
  
 <span data-ttu-id="26071-164">Rozwiązanie jest przekazanie <xref:System.Text.StringBuilder> buforu jako argument zamiast ciągu.</span><span class="sxs-lookup"><span data-stu-id="26071-164">The solution is to pass a <xref:System.Text.StringBuilder> buffer as the argument instead of a string.</span></span> <span data-ttu-id="26071-165">A `StringBuilder` wyłuskiwany i zmodyfikowane przez wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="26071-165">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="26071-166">Ponadto może zostać zainicjowane do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="26071-166">It can also be initialized to a fixed length.</span></span> <span data-ttu-id="26071-167">Na przykład, jeśli należy zainicjować `StringBuilder` bufor do pojemności `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków.</span><span class="sxs-lookup"><span data-stu-id="26071-167">For example, if you initialize a `StringBuilder` buffer to a capacity of `N`, the marshaler provides a buffer of size (`N`+1) characters.</span></span> <span data-ttu-id="26071-168">Konta + 1 dla fakt, że ciąg niezarządzane zawiera terminatorem null podczas `StringBuilder` nie.</span><span class="sxs-lookup"><span data-stu-id="26071-168">The +1 accounts for the fact that the unmanaged string has a null terminator while `StringBuilder` does not.</span></span>  
  
 <span data-ttu-id="26071-169">Na przykład Microsoft Win32 API `GetWindowText` funkcji (zdefiniowanej w Windows.h) jest znak o stałej długości buforu, który muszą być przekazywane do kodu niezarządzanego można manipulować.</span><span class="sxs-lookup"><span data-stu-id="26071-169">For example, the Microsoft Win32 API `GetWindowText` function (defined in Windows.h) is a fixed-length character buffer that must be passed into unmanaged code to be manipulated.</span></span> <span data-ttu-id="26071-170">`LpString` Wskazuje bufor przydzielony wywołującego rozmiaru `nMaxCount`.</span><span class="sxs-lookup"><span data-stu-id="26071-170">`LpString` points to a caller-allocated buffer of size `nMaxCount`.</span></span> <span data-ttu-id="26071-171">Obiekt wywołujący powinien alokacji buforu i ustaw `nMaxCount` argument rozmiarowi przydzielonego buforu.</span><span class="sxs-lookup"><span data-stu-id="26071-171">The caller is expected to allocate the buffer and set the `nMaxCount` argument to the size of the allocated buffer.</span></span> <span data-ttu-id="26071-172">Poniższy kod przedstawia `GetWindowText` deklaracji funkcji, zgodnie z definicją w Windows.h.</span><span class="sxs-lookup"><span data-stu-id="26071-172">The following code shows the `GetWindowText` function declaration as defined in Windows.h.</span></span>  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 <span data-ttu-id="26071-173">A `StringBuilder` wyłuskiwany i zmodyfikowane przez wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="26071-173">A `StringBuilder` can be dereferenced and modified by the callee, provided it does not exceed the capacity of the `StringBuilder`.</span></span> <span data-ttu-id="26071-174">Poniższy przykład kodu pokazuje sposób `StringBuilder` mogą być inicjowane do stałej długości.</span><span class="sxs-lookup"><span data-stu-id="26071-174">The following code example demonstrates how `StringBuilder` can be initialized to a fixed length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="26071-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="26071-175">See Also</span></span>  
 [<span data-ttu-id="26071-176">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="26071-176">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)  
 [<span data-ttu-id="26071-177">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="26071-177">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 <span data-ttu-id="26071-178">[Atrybuty kierunkową](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="26071-178">[Directional Attributes](https://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2(v=vs.100))</span></span>  
 [<span data-ttu-id="26071-179">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="26071-179">Copying and Pinning</span></span>](copying-and-pinning.md)
