---
title: "Organizowanie domyślne dotyczące ciągów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 34cd8194f5f36c2f9c93517403aa27f6bbbcb698
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-marshaling-for-strings"></a>Domyślny marshaling dla ciągów
Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy zachowują się podobnie kierowania.  
  
 Parametry są przekazywane jako styl modelu COM `BSTR` typu lub w postaci ciągu zakończonego wartością null (znak tablica, która kończy się znakiem null). Znaki w ciągu mogą być przekazywane jako Unicode (domyślnie w systemach Windows) lub ANSI.  
  
 Ten temat zawiera następujące informacje na przekazywanie typów ciąg:  
  
-   [Parametry używane w interfejsach](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Wywołanie ciągów używanych na platformie](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Ciągi używane w strukturach](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Bufory o stałej długości ciągu](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>   
## <a name="strings-used-in-interfaces"></a>Parametry używane w interfejsach  
 W poniższej tabeli przedstawiono opcje organizowania dla typu danych string podczas organizowane jako argument metody do kodu niezarządzanego. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> kierowanie ciągów do interfejsów modelu COM wartości wyliczenia.  
  
|Typ wyliczenia|Opis formatu niezarządzane|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`(ustawienie domyślne)|Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zerem.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.|  
  
 Ta tabela odnosi się do ciągów. Niemniej jednak w przypadku <xref:System.Text.StringBuilder>, czy można używać wyłącznie opcji `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.  
  
 W poniższym przykładzie przedstawiono ciągi zadeklarowany w `IStringWorker` interfejsu.  
  
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
  
 W poniższym przykładzie przedstawiono odpowiedniego interfejsu opisanego w bibliotece typów.  
  
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
## <a name="strings-used-in-platform-invoke"></a>Wywołanie ciągów używanych na platformie  
 Wywołanie platformy argumenty typu string kopie, konwersji z formatu .NET Framework (Unicode) do formatu niezarządzane platformy. Ciągi są niezmienne i nie są kopiowane z niezarządzanej pamięci do pamięci zarządzanej po powrocie z wywołania.  
  
 W poniższej tabeli wymieniono opcje organizowania ciągów, gdy organizowane jako argument metody platformy wywołania wywołania. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie ciągów.  
  
|Typ wyliczenia|Opis formatu niezarządzane|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|Styl modelu COM `BSTR` z prefiksem długość i znaków ANSI.|  
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zerem.|  
|`UnmanagedType.LPTStr`|Wskaźnik do tablicy znaków zależny od platformy zerem.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.|  
|`UnmanagedType.TBStr`|Styl modelu COM `BSTR` z prefiksem długość i znaki zależny od platformy.|  
|`VBByRefStr`|Wartość, która umożliwia Visual Basic .NET zmienić parametry w niezarządzanych kodu, a wyniki odzwierciedla w kodzie zarządzanym. Ta wartość jest obsługiwana tylko przez wywołanie platformy. Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.|  
  
 Ta tabela odnosi się do ciągów. Niemniej jednak w przypadku <xref:System.Text.StringBuilder>, czy można używać wyłącznie opcji `LPStr`, `LPTStr`, i `LPWStr`.  
  
 Następujące definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania wywołania.  
  
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
## <a name="strings-used-in-structures"></a>Ciągi używane w strukturach  
 Parametry są prawidłowe członków struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach. W poniższej tabeli przedstawiono opcje organizowania string — typ danych, gdy typ jest przekazywane jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie ciągów do pola.  
  
|Typ wyliczenia|Opis formatu niezarządzane|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długość i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zerem.|  
|`UnmanagedType.LPTStr`|Wskaźnik do tablicy znaków zależny od platformy zerem.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończonym znakiem null.|  
|`UnmanagedType.ByValTStr`|O stałej długości tablicy znaków; Typ tablicy jest określana przez struktury zawierającej zestaw znaków.|  
  
 `ByValTStr` Typ jest używany dla wbudowanego, tablice o stałej długości znaków, które pojawiają się w ramach struktury. Inne typy są stosowane do odwołania ciągu zawartych wewnątrz struktur, które zawierają wskaźniki do ciągów.  
  
 `CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który jest stosowany do struktury zawierające Określa format znaków ciągów w strukturach. Następujące struktury przykład zawiera odwołania do ciągu i ciągi wbudowany, a także ANSI, Unicode i znaków zależny od platformy.  
  
### <a name="type-library-representation"></a>Reprezentacja typu biblioteki  
  
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
  
 Poniższy przykładowy kod przedstawia sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do definiowania tej samej struktury w różnych formatach.  
  
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
## <a name="fixed-length-string-buffers"></a>Bufory o stałej długości ciągu  
 W niektórych sytuacjach buforu o stałej długości znaków muszą być przekazywane do kodu niezarządzanego można manipulować. Po prostu przekazywanie ciągu nie działa, w tym przypadku ponieważ wywoływany nie można zmodyfikować zawartości buforu przekazany. Nawet jeśli ciąg jest przekazywana przez odwołanie, nie istnieje sposób Inicjowanie buforu na dany rozmiar.  
  
 Rozwiązanie jest przekazanie <xref:System.Text.StringBuilder> buforu jako argument zamiast ciągu. A `StringBuilder` wyłuskiwany i zmodyfikowane przez wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Ponadto może zostać zainicjowane do stałej długości. Na przykład, jeśli należy zainicjować `StringBuilder` bufor do pojemności `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków. Konta + 1 dla fakt, że ciąg niezarządzane zawiera terminatorem null podczas `StringBuilder` nie.  
  
 Na przykład Microsoft Win32 API `GetWindowText` funkcji (zdefiniowanej w Windows.h) jest znak o stałej długości buforu, który muszą być przekazywane do kodu niezarządzanego można manipulować. `LpString`Wskazuje bufor przydzielony wywołującego rozmiaru `nMaxCount`. Obiekt wywołujący powinien alokacji buforu i ustaw `nMaxCount` argument rozmiarowi przydzielonego buforu. Poniższy kod przedstawia `GetWindowText` deklaracji funkcji, zgodnie z definicją w Windows.h.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` wyłuskiwany i zmodyfikowane przez wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Poniższy przykład kodu pokazuje sposób `StringBuilder` mogą być inicjowane do stałej długości.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Domyślne zachowanie Marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Typy Kopiowalne i niekopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Atrybuty kierunkową](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopiowanie i przypinanie](../../../docs/framework/interop/copying-and-pinning.md)
