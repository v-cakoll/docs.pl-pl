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
ms.openlocfilehash: 8505f4c742fb002be249ab069708f7f768c672df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123579"
---
# <a name="default-marshaling-for-arrays"></a>Organizowanie domyślne dotyczące tablic
W aplikacji składającej się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablicy jako parametry wejściowe/out. W przeciwieństwie do organizatora międzyoperacyjności domyślnie przekazuje tablicę w postaci parametrów.  
  
 Dzięki [przypinaniu optymalizacji](copying-and-pinning.md)Tablica danych kopiowalnych może być wyświetlana jako parametr in/out podczas korzystania z obiektów w tym samym elemencie Apartment. Jednak w przypadku późniejszego wyeksportowania kodu do biblioteki typów użytej do wygenerowania serwera proxy międzymaszynowego, a ta biblioteka jest używana do organizowania wywołań w ramach apartamentach, wywołania mogą przywrócić wartość true w zachowaniu parametrów.  
  
 Tablice są złożone z natury, a różnice między zarządzanymi i niezarządzanymi tablicami gwarantują więcej informacji niż w przypadku innych typów innych niż danych kopiowalnych.  
  
## <a name="managed-arrays"></a>Zarządzane tablice  
 Zarządzane typy tablic mogą się różnić; jednak Klasa <xref:System.Array?displayProperty=nameWithType> jest klasą bazową wszystkich typów tablicowych. Klasa **System. Array** ma właściwości do określania rangi, długości i dolnych i górnych granic tablicy, a także metod uzyskiwania dostępu do, sortowania, wyszukiwania, kopiowania i tworzenia tablic.  
  
 Te typy tablic są dynamiczne i nie mają odpowiedniego typu statycznego zdefiniowanego w bibliotece klas bazowych. Wygodnie jest myśleć o każdej kombinacji typu elementu i rangi jako odrębny typ tablicy. W związku z tym, Jednowymiarowa tablica liczb całkowitych jest innego typu niż Jednowymiarowa tablica podwójnych typów. Podobnie Dwuwymiarowa tablica liczb całkowitych różni się od jednowymiarowej tablicy liczb całkowitych. Granice tablicy nie są brane pod uwagę podczas porównywania typów.  
  
 Jak przedstawiono w poniższej tabeli, każde wystąpienie tablicy zarządzanej musi mieć określony typ elementu, rangę i dolną granicę.  
  
|Typ tablicy zarządzanej|Typ elementu|Stopni|Dolna granica|Notacja podpisu|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Określony przez typ.|Określone przez rangę.|Opcjonalnie określone przez granice.|*Typ* **[** *n*,*m* **]**|  
|**PODPIS**|Nieznany|Nieznany|Nieznany|**System. Array**|  
|**ELEMENT_TYPE_SZARRAY**|Określony przez typ.|1|0|*Typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Tablice niezarządzane  
 Tablice niezarządzane są tablicami bezpiecznymi w stylu COM lub tablicami w stylu C ze stałą lub zmienną długością. Bezpieczne tablice to samoopisujące się tablice, które zawierają typ, rangę i granice skojarzonych danych tablicy. Tablice w stylu C to jednowymiarowe tablice z ustaloną dolną granicą 0. Usługa Marshaling ma ograniczoną obsługę obu typów tablic.  
  
## <a name="passing-array-parameters-to-net-code"></a>Przekazywanie parametrów tablicy do kodu platformy .NET  
 Zarówno tablice w stylu C, jak i bezpieczne tablice można przesłać do kodu platformy .NET z niezarządzanego kodu jako tablicę bezpieczną lub tablicę w stylu języka C. W poniższej tabeli przedstawiono wartość typu niezarządzanego i typ zaimportowany.  
  
|Typ niezarządzany|Typ zaimportowany|  
|--------------------|-------------------|  
|**SAFEARRAY (** *Typ* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *przekonwertowane* **>**<br /><br /> Ranga = 1, Dolna granica = 0. Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym. Tablic bezpiecznych, które nie mają rangi = 1 lub dolnego powiązania = 0, nie mogą być organizowane jako **SZARRAY**.|  
|*Typ*  **[]**|**ELEMENT_TYPE_SZARRAY** **\<** *przekonwertowane* **>**<br /><br /> Ranga = 1, Dolna granica = 0. Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.|  
  
### <a name="safe-arrays"></a>Bezpieczne tablice  
 Gdy bezpieczna tablica jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na tablicę jednowymiarową znanego typu (na przykład **int**). Te same reguły konwersji typów, które mają zastosowanie do parametrów, mają zastosowanie także do elementów tablicy. Na przykład bezpieczna tablica typów **BSTR** jest zarządzaną tablicą ciągów, a bezpieczna tablica wariantów jest zarządzaną tablicą obiektów. Typ elementu **SAFEARRAY** jest przechwytywany z biblioteki typów i zapisywany w wartości **SAFEARRAY** wyliczenia <xref:System.Runtime.InteropServices.UnmanagedType>.  
  
 Ponieważ ranga i granice tablicy bezpiecznej nie można ustalić na podstawie biblioteki typów, przyjmuje się, że ranga jest równa 1, a dolna granica jest przyjmowana jako równa 0. Ranga i granice muszą być zdefiniowane w zarządzanym podpisie wygenerowanym przez [importera biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md). Jeśli ranga przeniesiona do metody w czasie wykonywania różni się, zostanie zgłoszony <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException>. Jeśli typ tablicy przeszedł w czasie wykonywania różni się, zostanie zgłoszony <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException>. W poniższym przykładzie przedstawiono bezpieczne tablice w kodzie zarządzanym i niezarządzanym.  
  
 **Niezarządzany podpis**  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Sygnatura zarządzana**  
  
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
  
 Wielowymiarowe lub niezerowe powiązane tablice mogą być organizowane w kodzie zarządzanym, jeśli sygnatura metody utworzona przez Tlbimp. exe została zmodyfikowana w celu wskazania typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_TYPE_SZARRAY**. Alternatywnie można użyć przełącznika **/sysarray** z Tlbimp. exe, aby zaimportować wszystkie tablice jako obiekty <xref:System.Array?displayProperty=nameWithType>. W przypadku, gdy przenoszona tablica jest nazywana wielowymiarową, można edytować kod języka pośredniego firmy Microsoft (MSIL) utworzony przez Tlbimp. exe, a następnie ponownie go skompilować. Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz Dostosowywanie wywoływanych [otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>Tablice w stylu języka C  
 Gdy tablica w stylu C jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ elementu tablicy jest określany na podstawie biblioteki typów i zachowywany podczas importowania. Te same reguły konwersji, które mają zastosowanie do parametrów, mają zastosowanie także do elementów tablicy. Na przykład Tablica typów **LPSTR** jest tablicą typów **ciągów** . Tlbimp. exe przechwytuje typ elementu tablicy i stosuje atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> do parametru.  
  
 Przyjmuje się, że ranga tablicy jest równa 1. Jeśli ranga jest większa niż 1, tablica jest organizowana jako tablica Jednowymiarowa w kolejności kolumny — główna. Dolna granica zawsze jest równa 0.  
  
 Biblioteki typów mogą zawierać tablice o stałej lub zmiennej długości. Tlbimp. exe może importować tylko tablice o stałej długości z bibliotek typów, ponieważ biblioteki typów nie zawierają informacji wymaganych do organizowania tablic o zmiennej długości. W przypadku tablic o stałej długości rozmiar jest zaimportowany z biblioteki typów i przechwytywany w elemencie **MarshalAsAttribute** , który jest stosowany do parametru.  
  
 Należy ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.  
  
 **Niezarządzany podpis**  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Sygnatura zarządzana**  
  
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
  
 Chociaż atrybuty **size_is** lub **length_is** można zastosować do tablicy źródła w języku definicji interfejsu (IDL), aby przekazać rozmiar do klienta, kompilator Microsoft Interface Definition Language (MIDL) nie propaguje tego informacje do biblioteki typów. Bez znajomości rozmiaru usługa Marshaling Interop nie może zorganizować elementów tablicy. W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania. Na przykład:  
  
 **Niezarządzany podpis**  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Sygnatura zarządzana**  
  
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
  
 Można przekazać Organizatorowi rozmiar tablicy, edytując kod języka pośredniego firmy Microsoft (MSIL) utworzony przez Tlbimp. exe, a następnie ponownie go skompilować. Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz Dostosowywanie wywoływanych [otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Aby wskazać liczbę elementów w tablicy, Zastosuj typ <xref:System.Runtime.InteropServices.MarshalAsAttribute> do parametru array definicji metody zarządzanej w jeden z następujących sposobów:  
  
- Zidentyfikuj inny parametr zawierający liczbę elementów w tablicy. Parametry są identyfikowane według pozycji, rozpoczynając od pierwszego parametru jako numer 0.     
  
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
  
- Zdefiniuj rozmiar tablicy jako stałą. Na przykład:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Podczas organizowania tablic z niezarządzanego kodu do kodu zarządzanego Organizator sprawdza, czy atrybut **MarshalAsAttribute** skojarzony z parametrem, aby określić rozmiar tablicy. Jeśli rozmiar tablicy nie zostanie określony, tylko jeden element jest zorganizowany.  
  
> [!NOTE]
> Wartość **MarshalAsAttribute** nie ma wpływu na kierowanie tablic zarządzanych do kodu niezarządzanego. W tym kierunku rozmiar tablicy jest określany przez badanie. Nie istnieje sposób organizowania podzestawu zarządzanej tablicy.  
  
 Organizator międzyoperacyjny używa metod **CoTaskMemAlloc** i **CoTaskMemFree** do przydzielania i pobierania pamięci. Alokacja pamięci wykonywana przez kod niezarządzany również musi używać tych metod.  
  
## <a name="passing-arrays-to-com"></a>Przekazywanie tablic do modelu COM  
 Wszystkie typy tablicy zarządzanej mogą być przesyłane do niezarządzanego kodu z kodu zarządzanego. W zależności od typu zarządzanego i zastosowanych do niego atrybutów tablica może być dostępna jako bezpieczna tablica lub tablica w stylu C, jak pokazano w poniższej tabeli.  
  
|Typ tablicy zarządzanej|Wyeksportowany jako|  
|------------------------|-----------------|  
|*Typ* **\<** **ELEMENT_TYPE_SZARRAY** **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **. SafeArray (** *Typ* **)**<br /><br /> **UnmanagedType. LPArray**<br /><br /> Typ jest podany w podpisie. Ranga jest zawsze 1, Dolna granica jest zawsze równa 0. Rozmiar jest zawsze znany w czasie wykonywania.|  
|*Typ* **\<** **ELEMENT_TYPE_ARRAY** **>** **\<** *rangi* **>** [ **\<** *granice* **>** ]|**UnmanagedType. SAFEARRAY (** *Typ* **)**<br /><br /> **UnmanagedType. LPArray**<br /><br /> Typ, ranga, granice są podane w podpisie. Rozmiar jest zawsze znany w czasie wykonywania.|  
|**\<** ELEMENT_TYPE_CLASS<xref:System.Array?displayProperty=nameWithType> **>**|**UT_Interface**<br /><br /> **UnmanagedType. SAFEARRAY (** *Typ* **)**<br /><br /> Typ, ranga, granice i rozmiar są zawsze znane w czasie wykonywania.|  
  
 Istnieje ograniczenie dotyczące automatyzacji OLE odnoszące się do tablic struktur, które zawierają LPSTR lub LPWSTR.  W związku z tym pola **String** muszą być organizowane jako **UnmanagedType. BSTR**. W przeciwnym razie zostanie zgłoszony wyjątek.  
  
### <a name="element_type_szarray"></a>ELEMENT_TYPE_SZARRAY  
 Gdy metoda zawierająca parametr **ELEMENT_TYPE_SZARRAY** (tablica Jednowymiarowa) jest eksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na typ **SAFEARRAY** danego typu. Te same reguły konwersji mają zastosowanie do typów elementów tablicy. Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do elementu **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga tablic bezpiecznych jest zawsze 1, a dolna granica jest zawsze równa 0. Rozmiar jest określany w czasie wykonywania przez rozmiar przesyłanej tablicy zarządzanej.  
  
 Tablica może być również organizowana jako tablica w stylu C przy użyciu atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>. Na przykład:  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Chociaż Organizator ma informacje o długości wymaganej do zorganizowania tablicy, Długość tablicy jest zwykle przekazywany jako oddzielny argument, aby przekazać długość do elementu wywoływanego.  
  
### <a name="element_type_array"></a>ELEMENT_TYPE_ARRAY  
 Gdy metoda zawierająca parametr **ELEMENT_TYPE_ARRAY** jest eksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na typ **SAFEARRAY** danego typu. Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do elementu **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga, rozmiar i granice bezpiecznych tablic są określane w czasie wykonywania przez charakterystykę zarządzanej tablicy.  
  
 Tablica może być również organizowana jako tablica w stylu C przez zastosowanie atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>. Na przykład:  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 Nie można zorganizować tablic zagnieżdżonych. Na przykład następujący podpis generuje błąd podczas eksportowania z [eksporterem biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a>ELEMENT_TYPE_CLASS \<system. Array >  
 Gdy metoda zawierająca parametr <xref:System.Array?displayProperty=nameWithType> zostanie wyeksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na interfejs **_Array** . Zawartość tablicy zarządzanej jest dostępna tylko za pomocą metod i właściwości interfejsu **_Array** . Element **System. Array** może być również zorganizowany jako **SAFEARRAY** przy użyciu atrybutu <xref:System.Runtime.InteropServices.MarshalAsAttribute>. Gdy jest zorganizowany jako bezpieczna tablica, elementy tablicy są organizowane jako warianty. Na przykład:  
  
#### <a name="managed-signature"></a>Sygnatura zarządzana  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Tablice w strukturach  
 Struktury niezarządzane mogą zawierać osadzone tablice. Domyślnie te osadzone pola tablicy są organizowane jako SAFEARRAY. W poniższym przykładzie `s1` jest osadzoną tablicą przydzieloną bezpośrednio w samej strukturze.  
  
#### <a name="unmanaged-representation"></a>Reprezentacja niezarządzana  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Tablice można zorganizować jako <xref:System.Runtime.InteropServices.UnmanagedType>, co wymaga ustawienia pola <xref:System.Runtime.InteropServices.MarshalAsAttribute>. Rozmiar można ustawić tylko jako stała. Poniższy kod przedstawia odpowiadającą zarządzane definicje `MyStruct`.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Domyślne zachowanie marshalingu](default-marshaling-behavior.md)
- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [Kopiowanie i przypinanie](copying-and-pinning.md)
