---
title: Organizowanie domyślne dotyczące tablic
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181452"
---
# <a name="default-marshaling-for-arrays"></a>Organizowanie domyślne dotyczące tablic
W aplikacji składającej się w całości z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako parametry W/Out. Z drugiej strony organizator międzypłeczny przekazuje tablicy jako w parametrach domyślnie.  
  
 Dzięki [optymalizacji przypinania](copying-and-pinning.md)tablica blittable może działać jako parametr In/Out podczas interakcji z obiektami w tym samym mieszkaniu. Jednak jeśli później wyeksportować kod do biblioteki typów używane do generowania serwera proxy między komputerami i tej biblioteki jest używany do organizowania wywołań w apartamentach, wywołania można przywrócić true w zachowanie parametru.  
  
 Tablice są złożone z natury, a różnice między tablicami zarządzanymi i niezarządzanymi wymagają więcej informacji niż inne typy, których nie można uzyskać.  
  
## <a name="managed-arrays"></a>Tablice zarządzane  
 Typy tablic zarządzanych mogą się różnić; jednak <xref:System.Array?displayProperty=nameWithType> klasa jest klasą podstawową wszystkich typów tablic. **Klasa System.Array** ma właściwości określania rangi, długości oraz dolnej i górnej granicy tablicy, a także metody uzyskiwania dostępu, sortowania, wyszukiwania, kopiowania i tworzenia tablic.  
  
 Te typy tablic są dynamiczne i nie mają odpowiedniego typu statycznego zdefiniowanego w bibliotece klas podstawowych. Jest to wygodne, aby myśleć o każdej kombinacji typu elementu i rangi jako odrębny typ tablicy. W związku z tym jednowymiarowa tablica liczby całkowitej jest innego typu niż jednowymiarowa tablica typów podwójnych. Podobnie dwuwymiarowa tablica liczby całkowitych różni się od jednowymiarowej tablicy liczby całkowitej. Granice tablicy nie są brane pod uwagę podczas porównywania typów.  
  
 Jak pokazano w poniższej tabeli, każde wystąpienie tablicy zarządzanej musi mieć określony typ elementu, rangę i dolną granicę.  
  
|Typ tablicy zarządzanej|Typ elementu|Ranga|Dolna granica|Notacja podpisu|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Określony przez typ.|Określona według rangi.|Opcjonalnie określone przez granice.|*typ* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Nieznane|Nieznane|Nieznane|**System.array**|  
|**Element_type_szarray**|Określony przez typ.|1|0|*typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Tablice niezarządzane  
 Tablice niezarządzane są tablicami bezpiecznymi w stylu COM lub tablicami w stylu C o stałej lub zmiennej długości. Bezpieczne tablice są samookryczające tablice, które zawierają typ, rangę i granice skojarzonych danych tablicy. Tablice w stylu C są jednowymiarowymi tablicami wpisanych o stałej dolnej granicy 0. Usługa organizowania ma ograniczoną obsługę dla obu typów tablic.  
  
## <a name="passing-array-parameters-to-net-code"></a>Przekazywanie parametrów tablicy do kodu NET  
 Zarówno tablice w stylu C, jak i bezpieczne tablice mogą być przekazywane do kodu .NET z kodu niezarządzanego jako tablica bezpieczna lub tablica w stylu C. W poniższej tabeli przedstawiono wartość typu niezarządzanego i typ zaimportowany.  
  
|Typ niezarządzany|Typ zaimportowany|  
|--------------------|-------------------|  
|**SafeArray(** *Typ* **)**|**\<** **ELEMENT_TYPE_SZARRAY** *ConvertedType***>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym. Bezpieczne tablice, które nie są rangą = 1 lub dolna granica = 0 nie mogą być organizowane jako **SZARRAY**.|  
|*Typ*  **[]**|**\<** **ELEMENT_TYPE_SZARRAY** *ConvertedType***>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.|  
  
### <a name="safe-arrays"></a>Bezpieczne tablice  
 Gdy bezpieczna tablica jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na tablicę jednowymiarową znanego typu (na przykład **int).** Te same reguły konwersji typu, które mają zastosowanie do parametrów, mają również zastosowanie do elementów tablicy. Na przykład bezpieczna tablica typów **BSTR** staje się zarządzaną tablicą ciągów, a bezpieczna tablica wariantów staje się zarządzaną tablicą obiektów. Typ elementu **SAFEARRAY** jest przechwytywany z biblioteki typów i <xref:System.Runtime.InteropServices.UnmanagedType> zapisywany w wartości **SAFEARRAY** wyliczenia.  
  
 Ponieważ rangi i granice tablicy bezpieczne nie można określić z biblioteki typów, ranga zakłada się, że równa 1 i dolnej granicy zakłada się równe 0. Ranga i granice muszą być zdefiniowane w podpisie zarządzanym sporządzonym przez [importera biblioteki typów (Tlbimp.exe).](../tools/tlbimp-exe-type-library-importer.md) Jeśli ranga przeszedł do metody w czasie <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> wykonywania różni się, a jest wyrzucany. Jeśli typ tablicy przekazywane w czasie wykonywania <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> różni się, a jest generowany. Poniższy przykład przedstawia bezpieczne tablice w kodzie zarządzanym i niezarządzanym.  
  
 **Podpis niezarządzany**  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Podpis zarządzany**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 Tablice wielowymiarowe lub niezerowe mogą być kierowane do kodu zarządzanego, jeśli podpis metody wyprodukowany przez Tlbimp.exe zostanie zmodyfikowany w celu wskazania typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_TYPE_SZARRAY**. Alternatywnie można użyć **przełącznika /sysarray** z Tlbimp.exe, <xref:System.Array?displayProperty=nameWithType> aby zaimportować wszystkie tablice jako obiekty. W przypadkach, gdy tablica przekazywana jest znana jako wielowymiarowa, można edytować kod języka pośredniego firmy Microsoft (MSIL) wyprodukowany przez Tlbimp.exe, a następnie ponownie go skompilować. Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz [Dostosowywanie otoki wywoławcze środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>Tablice w stylu C  
 Gdy tablica w stylu C jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ elementu tablicy jest określany z biblioteki typów i zachowywany podczas importowania. Te same reguły konwersji, które mają zastosowanie do parametrów, mają również zastosowanie do elementów tablicy. Na przykład tablica typów **LPStr** staje się tablicą typów **string.** Program Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do parametru.  
  
 Przyjmuje się, że ranga tablicy jest równa 1. Jeśli ranga jest większa niż 1, tablica jest organizowana jako tablica jednowymiarowa w kolejności głównej kolumny. Dolna granica zawsze jest równa 0.  
  
 Biblioteki typów mogą zawierać tablice o stałej lub zmiennej długości. Program Tlbimp.exe może importować tylko tablice o stałej długości z bibliotek typów, ponieważ biblioteki typów nie są w stanie zorganizować tablic o zmiennej długości. W przypadku tablic o stałej długości rozmiar jest importowany z biblioteki typów i przechwytywany w naliczanym pliku **MarshalAsAttribute,** który jest stosowany do parametru.  
  
 Należy ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.  
  
 **Podpis niezarządzany**  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Podpis zarządzany**  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 Chociaż można zastosować **size_is** lub **length_is** atrybuty do tablicy w źródle języka IDL (Interface Definition Language) w celu przekazania rozmiaru do klienta, kompilator języka MIDL (Microsoft Interface Definition Language) nie propaguje tych informacji do biblioteki typów. Nie znając rozmiaru usługi międzyoperacyjnej marshaling nie można marshal elementów tablicy. W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania. Przykład:  
  
 **Podpis niezarządzany**  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Podpis zarządzany**  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 Organizatora można podać rozmiar tablicy, edytując kod języka pośredniego firmy Microsoft (MSIL) wyprodukowany przez program Tlbimp.exe, a następnie ponownie go kompilując. Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz [Dostosowywanie otoki wywoławcze środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Aby wskazać liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> ten typ do parametru tablicy definicji metody zarządzanej w jeden z następujących sposobów:  
  
- Zidentyfikuj inny parametr, który zawiera liczbę elementów w tablicy. Parametry są identyfikowane przez położenie, począwszy od pierwszego parametru jako liczba 0.
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- Zdefiniuj rozmiar tablicy jako stałą. Przykład:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Podczas organizowania tablic z kodu niezarządzanego do kodu zarządzanego, organizator sprawdza **MarshalAsAttribute skojarzone** z parametrem, aby określić rozmiar tablicy. Jeśli rozmiar tablicy nie jest określony, tylko jeden element jest organizowane.  
  
> [!NOTE]
> **MarshalAsAttribute** nie ma wpływu na kierowanie tablice zarządzane do kodu niezarządzanego. W tym kierunku rozmiar tablicy jest określany przez badanie. Nie ma sposobu, aby zorganizować podzbiór tablicy zarządzanej.  
  
 Organizator interop używa **CoTaskMemAlloc** i **CoTaskMemFree** metody alokacji i pobierania pamięci. Alokacja pamięci wykonywane przez kod niezarządzany musi również korzystać z tych metod.  
  
## <a name="passing-arrays-to-com"></a>Przekazywanie tablic do com  
 Wszystkie typy tablic zarządzanych mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego. W zależności od typu zarządzanego i atrybutów zastosowanych do niego, tablica jest dostępna jako tablica bezpieczna lub tablica w stylu C, jak pokazano w poniższej tabeli.  
  
|Typ tablicy zarządzanej|Wywiezione jako|  
|------------------------|-----------------|  
|**\<** *type* Typ **ELEMENT_TYPE_SZARRAY****>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *typ* **)**<br /><br /> **NiezarządzaneType.LPArray**<br /><br /> Typ znajduje się w podpisie. Ranga jest zawsze 1, dolna granica jest zawsze 0. Rozmiar jest zawsze znany w czasie wykonywania.|  
|**\<** **ELEMENT_TYPE_ARRAY** **\<** **>** **\<** *ranga* *type* **>** typu [ *granice* **>**]|**NiezarządzaneType.SafeArray(** *typ* **)**<br /><br /> **NiezarządzaneType.LPArray**<br /><br /> Typ, ranga, granice są podane w podpisie. Rozmiar jest zawsze znany w czasie wykonywania.|  
|**ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **NiezarządzaneType.SafeArray(** *typ* **)**<br /><br /> Typ, ranga, granice i rozmiar są zawsze znane w czasie wykonywania.|  
  
 Istnieje ograniczenie w automatyzacji OLE odnoszące się do tablic struktur, które zawierają LPSTR lub LPWSTR.  W związku z tym pola **ciąg** musi być zorganizowany jako **UnmanagedType.BSTR**. W przeciwnym razie zostanie zgłoszony wyjątek.  
  
### <a name="element_type_szarray"></a>Element_type_szarray  
 Gdy metoda zawierająca parametr **ELEMENT_TYPE_SZARRAY** (tablica jednowymiarowa) jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu. Te same reguły konwersji mają zastosowanie do typów elementów tablicy. Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do **safearray**. Przykład:  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga bezpiecznych tablic jest zawsze 1, a dolna granica jest zawsze 0. Rozmiar jest określany w czasie wykonywania przez rozmiar zarządzanej tablicy przekazywanych.  
  
 Tablica może być również organizowane jako tablicy <xref:System.Runtime.InteropServices.MarshalAsAttribute> w stylu C przy użyciu atrybutu. Przykład:  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Chociaż organizator ma informacje o długości potrzebne do organizowania tablicy, długość tablicy jest zwykle przekazywana jako oddzielny argument do przekazywania długości do wywoływanego.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 Gdy metoda zawierająca parametr **ELEMENT_TYPE_ARRAY** jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu. Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do **safearray**. Przykład:  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga, rozmiar i granice tablic bezpieczeństwa są określane w czasie wykonywania przez właściwości tablicy zarządzanej.  
  
 Tablica może być również organizowane jako tablicy <xref:System.Runtime.InteropServices.MarshalAsAttribute> w stylu C, stosując atrybut. Przykład:  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Tablice zagnieżdżone nie mogą być organizowane. Na przykład następujący podpis generuje błąd podczas eksportowania z [eksporterem biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>> \<ELEMENT_TYPE_CLASS System.Array  
 Gdy metoda zawierająca <xref:System.Array?displayProperty=nameWithType> parametr jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na interfejs **_Array.** Zawartość tablicy zarządzanej są dostępne tylko za pośrednictwem metod i właściwości interfejsu **_Array.** **System.Array** może być również organizowane jako **SAFEARRAY** przy użyciu atrybutu. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Gdy organizowane jako bezpieczne tablicy, elementy tablicy są organizowane jako warianty. Przykład:  
  
#### <a name="managed-signature"></a>Podpis zarządzany  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Tablice w strukturach  
 Struktury niezarządzane mogą zawierać tablice osadzone. Domyślnie te osadzone pola tablicy są organizowane jako SAFEARRAY. W poniższym `s1` przykładzie jest osadzona tablica, która jest przydzielana bezpośrednio w samej strukturze.  
  
#### <a name="unmanaged-representation"></a>Reprezentacja niezarządzana  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Tablice mogą być <xref:System.Runtime.InteropServices.UnmanagedType>organizowane jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> co wymaga, aby ustawić pole. Rozmiar można ustawić tylko jako stałą. Poniższy kod przedstawia odpowiednią `MyStruct`zarządzał definicję .  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
