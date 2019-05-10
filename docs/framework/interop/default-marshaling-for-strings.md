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
ms.openlocfilehash: d39d4dfd5413b95300b70f27437bd27ca2d67a20
ms.sourcegitcommit: 4c10802ad003374641a2c2373b8a92e3c88babc8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65452384"
---
# <a name="default-marshaling-for-strings"></a>Organizowanie domyślne dotyczące ciągów

Zarówno <xref:System.String?displayProperty=nameWithType> i <xref:System.Text.StringBuilder?displayProperty=nameWithType> klasy mają podobne zachowanie organizowania.

Parametry są przekazywane jako styl modelu COM `BSTR` typu lub jako ciąg zakończony znakiem null (tablicy znaków zakończony znakiem null). Znaki ciągu może być organizowany jako Unicode (domyślnie w systemach Windows) lub ANSI.

## <a name="strings-used-in-interfaces"></a>Ciągi używane w interfejsach

W poniższej tabeli przedstawiono opcje kierowania dla typu danych string podczas przekazywania jako argumentu metody do kodu niezarządzanego. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów COM interfejsy wartości wyliczenia.

|Typ wyliczeniowy|Opis formatu niezarządzanych|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr` (ustawienie domyślne)|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|
|`UnmanagedType.LPStr`|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|

Ta tabela ma zastosowanie do <xref:System.String>. Aby uzyskać <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `UnmanagedType.LPStr` i `UnmanagedType.LPWStr`.

W poniższym przykładzie pokazano ciągów, zadeklarowanej w `IStringWorker` interfejsu.

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

Poniższy przykład pokazuje odpowiedniego interfejsu opisanych w bibliotece typów.

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

## <a name="strings-used-in-platform-invoke"></a>Wywoływanie ciągów używanych w platformy

Argumenty typu string kopii, konwertowania z formatu .NET Framework (Unicode) do formatu niezarządzanych platformy wywołania platformy. Ciągów są niezmienne i nie są kopiowane z niezarządzanej pamięci zarządzanej pamięci podczas to wywołanie zwraca.

Poniższa tabela zawiera opcje marshaling dla ciągów, gdy organizowany jako argumentu metody platformy wywołania wywołania. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów wartości wyliczenia.

|Typ wyliczeniowy|Opis formatu niezarządzanych|
|----------------------|-------------------------------------|
|`UnmanagedType.AnsiBStr`|Styl modelu COM `BSTR` z prefiksem długości i znaki ANSI.|
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|
|`UnmanagedType.LPStr` (ustawienie domyślne)|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|
|`UnmanagedType.LPTStr`|Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.|
|`UnmanagedType.LPUTF8Str`|Wskaźnik do tablicą zakończoną znakiem null UTF-8 zakodowanych znaków.|
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|
|`UnmanagedType.TBStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków zależnych od platformy.|
|`VBByRefStr`|Wartość, która umożliwia Visual Basic .NET zmienić parametry w kod niezarządzany i mieć wyniki zostaną uwzględnione w kodzie zarządzanym. Ta wartość jest obsługiwana tylko w przypadku wywołania platformy. Jest to wartość domyślna w języku Visual Basic dla `ByVal` ciągów.|

Ta tabela ma zastosowanie do <xref:System.String>. Aby uzyskać <xref:System.Text.StringBuilder>, są tylko opcje dozwolone `LPStr`, `LPTStr`, i `LPWStr`.

Następująca definicja typu zawiera prawidłowe użycie `MarshalAsAttribute` platformy wywołania.

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

## <a name="strings-used-in-structures"></a>Ciągi używane w strukturach

Ciągi są prawidłowe elementy członkowskie struktur; jednak <xref:System.Text.StringBuilder> buforów są nieprawidłowe w strukturach. W poniższej tabeli przedstawiono opcje kierowania <xref:System.String> typ danych, gdy typ jest organizowana jako pole. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> przeprowadzanie marshalingu ciągów do pola wartości wyliczenia.

|Typ wyliczeniowy|Opis formatu niezarządzanych|
|----------------------|-------------------------------------|
|`UnmanagedType.BStr`|Styl modelu COM `BSTR` z prefiksem długości i znaków Unicode.|
|`UnmanagedType.LPStr` (ustawienie domyślne)|Wskaźnik do tablicy znaków ANSI zakończony znakiem null.|
|`UnmanagedType.LPTStr`|Wskaźnik do tablicą zakończoną znakiem null znaków zależnych od platformy.|
|`UnmanagedType.LPUTF8Str`|Wskaźnik do tablicą zakończoną znakiem null UTF-8 zakodowanych znaków.|
|`UnmanagedType.LPWStr`|Wskaźnik do tablicy znaków Unicode zakończony wartością null.|
|`UnmanagedType.ByValTStr`|Tablica o stałej długości, znaków; Typ tablicy jest ustalany przez zestaw znaków zawierającą strukturę.|

`ByValTStr` Typ jest używany do wbudowanych tablic znaków o stałej długości, które pojawiają się w ramach struktury. Inne typy mają zastosowanie do odwołania ciągu zawarte w obrębie struktury, które zawierają wskaźnikami do ciągów.

`CharSet` Argument <xref:System.Runtime.InteropServices.StructLayoutAttribute> mający zastosowanie do zawierający struktury Określa format znaków z ciągów w strukturach. Następujące przykładowe struktury zawierają ciąg odwołania i ciągi wbudowane, a także ANSI, Unicode i znaków zależnych od platformy. Reprezentacja tych struktur w bibliotece typów przedstawiono w następującym C++ kodu:

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

Poniższy przykład pokazuje, jak używać <xref:System.Runtime.InteropServices.MarshalAsAttribute> zdefiniować tę samą strukturę w różnych formatach.

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

## <a name="fixed-length-string-buffers"></a>Bufory o stałej długości ciągu

W pewnych okolicznościach buforu znaków o stałej długości muszą być przekazywane do kodu niezarządzanego, aby być zmieniane. Po prostu przekazując ciąg nie działa w tym przypadku, ponieważ obiekt wywoływany nie można zmodyfikować zawartość przekazanego buforu. Nawet jeśli ten ciąg jest przekazywany przez odwołanie, nie ma możliwości zainicjować buforu na dany rozmiar.

To rozwiązanie służy do przekazywania <xref:System.Text.StringBuilder> buforu jako argument zamiast <xref:System.String>. A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Ponadto może zostać zainicjowane do stałej długości. Na przykład, jeśli należy zainicjować `StringBuilder` buforu na pojemność `N`, organizator udostępnia bufor o rozmiarze (`N`+ 1) znaków. Konta + 1 fakt, że niezarządzanego ciągu ma terminatora null podczas `StringBuilder` nie.

Na przykład Windows [ `GetWindowText` ](/windows/desktop/api/winuser/nf-winuser-getwindowtextw) funkcji interfejsu API (zdefiniowane w *winuser.h*) wymaga, że obiekt wywołujący przekazywać buforu znaków o stałej długości, do której funkcja zapisuje tekst okna. `LpString` Wskazuje przydzielonej przez obiekt wywołujący bufor o rozmiarze `nMaxCount`. Obiekt wywołujący oczekuje się, aby przydzielić bufor i ustawić `nMaxCount` argumentu rozmiaru przydzielonego buforu. W poniższym przykładzie przedstawiono `GetWindowText` deklaracji funkcji, zgodnie z definicją w *winuser.h*.

```cpp
int GetWindowText(
    HWND hWnd,        // Handle to window or control.
    LPTStr lpString,  // Text buffer.
    int nMaxCount     // Maximum number of characters to copy.
);
```

A `StringBuilder` wyłuskiwany i zmodyfikowane przez obiekt wywoływany, pod warunkiem nie przekracza pojemność `StringBuilder`. Poniższy przykład kodu demonstruje sposób `StringBuilder` może być inicjowany do stałej długości.

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

## <a name="see-also"></a>Zobacz także

- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Marshaling ciągów](marshaling-strings.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
