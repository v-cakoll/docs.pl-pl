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
# <a name="default-marshaling-for-strings"></a>Organizowanie domyślne dotyczące ciągów
Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy mają podobne zachowanie organizowania.  
  
 Parametry są przekazywane jako styl modelu COM `BSTR` typu lub jako ciąg zakończony znakiem null (tablicy znaków zakończony znakiem null). Znaki ciągu może być organizowany jako Unicode (domyślnie w systemach Windows) lub ANSI.  
  
 Ten temat zawiera następujące informacje dotyczące marshaling typów ciągów:  
  
-   [Ciągi używane w interfejsach](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [Wywoływanie ciągów używanych w platformy](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [Ciągi używane w strukturach](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [Bufory o stałej długości ciągu](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>Ciągi używane w interfejsach  
 W poniższej tabeli przedstawiono opcje kierowania dla typu danych string podczas przekazywania jako argumentu metody do kodu niezarządzanego. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów COM interfejsy wartości wyliczenia.  
  
|Typ wyliczeniowy|Opis formatu niezarządzanych|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (ustawienie domyślne)|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|  
  
 Ta tabela ma zastosowanie do ciągów. Jednak w przypadku <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.  
  
 W poniższym przykładzie pokazano ciągów, zadeklarowanej w `IStringWorker` interfejsu.  
  
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

Poniższy przykład pokazuje odpowiedniego interfejsu opisanych w bibliotece typów.

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

## <a name="strings-used-in-platform-invoke"></a>Wywoływanie ciągów używanych w platformy  
 Argumenty typu string kopii, konwertowania z formatu .NET Framework (Unicode) do formatu niezarządzanych platformy wywołania platformy. Ciągów są niezmienne i nie są kopiowane z niezarządzanej pamięci zarządzanej pamięci podczas to wywołanie zwraca.  
  
 Poniższa tabela zawiera opcje marshaling dla ciągów, gdy organizowany jako argumentu metody platformy wywołania wywołania. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów wartości wyliczenia.  
  
|Typ wyliczeniowy|Opis formatu niezarządzanych|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|Styl modelu COM `BSTR` z prefiksem długości i znaki ANSI.|  
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|  
|`UnmanagedType.LPTStr`|Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|  
|`UnmanagedType.TBStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków zależnych od platformy.|  
|`VBByRefStr`|Wartość, która umożliwia Visual Basic .NET zmienić parametry w kod niezarządzany, a masz wyniki zostaną uwzględnione w kodzie zarządzanym. Ta wartość jest obsługiwana tylko w przypadku wywołania platformy. Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.|  
  
 Ta tabela ma zastosowanie do ciągów. Jednak w przypadku <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `LPStr`, `LPTStr`, i `LPWStr`.  
  
 Następująca definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania.  
  
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
 Ciągi są prawidłowe elementy członkowskie struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach. W poniższej tabeli przedstawiono opcje kierowania string — typ danych, gdy typ jest organizowana jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów do pola wartości wyliczenia.  
  
|Typ wyliczeniowy|Opis formatu niezarządzanych|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|  
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|  
|`UnmanagedType.LPTStr`|Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.|  
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|  
|`UnmanagedType.ByValTStr`|Tablica o stałej długości, znaków; Typ tablicy jest ustalany przez zestaw znaków zawierającą strukturę.|  
  
 `ByValTStr` Typ jest używany do wbudowanych tablic znaków o stałej długości, które pojawiają się w ramach struktury. Inne typy mają zastosowanie do odwołania ciągu zawarte w obrębie struktury, które zawierają wskaźnikami do ciągów.  
  
 `CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybut, który jest stosowany do struktury zawierającej Określa format znaków z ciągów w strukturach. Następujące przykładowe struktury zawierają ciąg odwołania i ciągi wbudowane, a także ANSI, Unicode i znaków zależnych od platformy.  
  
### <a name="type-library-representation"></a>Reprezentacja biblioteki typów  
  
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
  
 Poniższy przykład kodu pokazuje sposób użycia <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do definiowania tę samą strukturę w różnych formatach.  
  
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
 W pewnych okolicznościach buforu znaków o stałej długości muszą być przekazywane do kodu niezarządzanego, aby być zmieniane. Po prostu przekazując ciąg nie działa w tym przypadku, ponieważ obiekt wywoływany nie można zmodyfikować zawartość przekazanego buforu. Nawet jeśli ten ciąg jest przekazywany przez odwołanie, nie ma możliwości zainicjować buforu na dany rozmiar.  
  
 To rozwiązanie służy do przekazywania <xref:System.Text.StringBuilder> buforu jako argument zamiast ciągu. A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Ponadto może zostać zainicjowane do stałej długości. Na przykład, jeśli należy zainicjować `StringBuilder` buforu na pojemność `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków. Konta + 1 fakt, że niezarządzanego ciągu ma terminatora null podczas `StringBuilder` nie.  
  
 Na przykład Microsoft Win32 API `GetWindowText` — funkcja (zdefiniowanymi w Windows.h) to muszą być przekazywane do kodu niezarządzanego ustawianych bufor znaków o stałej długości. `LpString` Wskazuje przydzielonej przez obiekt wywołujący bufor o rozmiarze `nMaxCount`. Obiekt wywołujący oczekuje się, aby przydzielić bufor i ustawić `nMaxCount` argumentu rozmiaru przydzielonego buforu. Poniższy kod przedstawia `GetWindowText` deklaracji funkcji, zgodnie z definicją w Windows.h.  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Poniższy przykład kodu demonstruje sposób `StringBuilder` może być inicjowany do stałej długości.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
