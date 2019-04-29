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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3eb5c9686f54bcaacef8d593f0ace4804d4ae60
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643442"
---
# <a name="default-marshaling-for-arrays"></a>Organizowanie domyślne dotyczące tablic
W aplikacji składających się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako we/wy parametrów. Z kolei Organizator międzyoperacyjny przekazuje tablicę, tak jak parametry domyślne.  
  
 Za pomocą [przypinania optymalizacji](copying-and-pinning.md), tablicy danych kopiowalnych może okazać się działać jako In/Out parametru podczas interakcji z obiektów w tej samej typu apartment. Jeśli później wyeksportować kod na bibliotekę typów, używany do generowania serwera proxy między komputerami oraz biblioteki jest używany do organizowania wywołania w apartamentach wywołania można przywrócić na wartość true w zachowaniu parametru.  
  
 Tablice są skomplikowane ze względu na charakter, a różnice między zarządzanymi i niezarządzanymi macierzami oświadcza informacji od innych typów niekopiowalnych.  
  
## <a name="managed-arrays"></a>Zarządzane tablice  
 Zarządzane tablicy, która może się różnić typów; jednak <xref:System.Array?displayProperty=nameWithType> klasy jest klasą bazową wszystkich typów tablicowych. **System.Array** klasa posiada właściwości, określając rangę, długość i dolną i górną granicę, tablica, a także metody uzyskiwania dostępu do, sortowanie, wyszukiwanie, kopiowanie i tworzenie tablic.  
  
 Te typy tablic są dynamiczne i nie ma odpowiedniego typu statycznego zdefiniowane w bibliotece klas podstawowych. Jest to dobrze jest myśleć o każdej kombinacji typ elementu i rangi jako typ samodzielny tablicy. Dlatego Jednowymiarowa tablica liczb całkowitych jest innego typu niż Jednowymiarowa tablica typu double. Podobnie tablicę dwuwymiarową liczb całkowitych różni się od Jednowymiarowa tablica liczb całkowitych. Granice tablicy nie są uwzględniane podczas porównywania typów.  
  
 Jak pokazano w poniższej tabeli, dowolne wystąpienie tablicy zarządzanej musi być typu określonego elementu, rangę i dolną granicę.  
  
|Zarządzany typ tablicy|Typ elementu|Ranga|Dolna granica|Notacja podpisu|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Określony według typu.|Określony według rangi.|Opcjonalnie określone przez granice.|*Typ* **[** *n*,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Nieznany|Nieznany|Nieznany|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|Określony według typu.|1|0|*Typ* **[** *n* **]**|  
  
## <a name="unmanaged-arrays"></a>Tablice niezarządzanych  
 Niezarządzane tablice są tablic bezpiecznych styl modelu COM lub tablice stylu C o długości stałą lub zmienną. Tablice bezpieczne są samoopisujące tablic, wykonujących typu, rangę i granice skojarzonych danych. Tablice stylu C są jednowymiarowe tablice o określonym typie ze stałym dolną granicę równą 0. Usługa kierowania ma ograniczoną obsługę oba typy tablic.  
  
## <a name="passing-array-parameters-to-net-code"></a>Przekazywanie parametrów tablicy do kodu platformy .NET  
 Tablice stylu C i tablic bezpiecznych programu mogą być przekazywane do kodu platformy .NET z niezarządzanego kodu jako bezpiecznego tablicy lub tablicy stylu C. W poniższej tabeli przedstawiono wartości typu niezarządzanego i zaimportowanym typem.  
  
|Typ niezarządzany|Typu importowanego|  
|--------------------|-------------------|  
|**SafeArray (** *typu* **)**|**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znane tylko wtedy, gdy jest podawany jako zarządzanego podpisu. Bezpieczne tablic, które nie są rangi = 1 lub dolna granica = 0 nie mogą być przekazywane jako **SZARRAY**.|  
|*Typ***]** |**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znane tylko wtedy, gdy jest podawany jako zarządzanego podpisu.|  
  
### <a name="safe-arrays"></a>Tablic bezpiecznych programu  
 Po zaimportowaniu bezpieczną tablicą z biblioteki typów na zestaw .NET tablica jest konwertowana na tablicę jednowymiarową znanego typu (takie jak **int**). Tych samych zasad konwersji typów, które są stosowane do parametrów dotyczą również elementy tablicy. Na przykład, bezpieczną tablicą o **BSTR** typy staje się zarządzanych tablicę ciągów i bezpieczną tablicą wariantów staje się tablicy obiektów. **SAFEARRAY** typ elementu jest przechwytywane z biblioteki typów i zapisane w **SAFEARRAY** wartość <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia.  
  
 Ponieważ nie można ustalić rangi i granice tablicy bezpieczne z biblioteki typów, rangę zakłada, że jest równa 1, a dolna granica zakłada, że jest równa 0. Ranga i granice muszą być zdefiniowane w zarządzanego podpisu produkowane przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md). Jeśli różni się rangę przekazywany do metody w czasie wykonywania, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> zgłaszany. Jeśli typ tablicy przekazany w czasie wykonywania jest inny, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> zgłaszany. Poniższy przykład pokazuje tablic bezpiecznych w kodzie zarządzanym i niezarządzanym.  
  
 **Niezarządzane podpisu**  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 **Zarządzanego podpisu**  
  
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
  
 Wielowymiarowym lub różną od zera powiązane z tablic bezpiecznych, może być organizowany wywołanie kodu zarządzanego, jeśli podpis metody generowane przez Tlbimp.exe jest modyfikowany, aby wskazać typ elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_ TYPE_SZARRAY**. Alternatywnie, można użyć **/sysarray** Przełącz przy użyciu Tlbimp.exe do importowania wszystkich tablic jako <xref:System.Array?displayProperty=nameWithType> obiektów. W przypadkach, w którym tablicy przekazywana jest znany jako wielowymiarowe można edytować utworzony kod intermediate language (MSIL) firmy Microsoft przez Tlbimp.exe i skompiluj go ponownie. Aby uzyskać szczegółowe informacje dotyczące sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).  
  
### <a name="c-style-arrays"></a>Tablice stylu C  
 Po zaimportowaniu tablicy stylu C z biblioteki typów na zestaw .NET tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ elementu tablicy jest określana na podstawie biblioteki typów i zachowywane podczas importowania. Te same reguły konwersji, które są stosowane do parametrów dotyczą również elementy tablicy. Na przykład tablica **LPStr** typy staje się tablica **ciąg** typów. Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu do parametru.  
  
 Ranga tablicy, przyjmowana jest wartość 1. Jeśli pozycja jest większa niż 1, tablica jest organizowana jako Jednowymiarowa tablica, w kolejności kolumn. Dolna granica jest zawsze równa 0.  
  
 Biblioteki typów mogą zawierać tablic o długości stałą lub zmienną. Tlbimp.exe można importować tylko o stałej długości tablic z bibliotek typów, ponieważ biblioteki typów brakuje informacji potrzebnych do organizowania tablice o zmiennej długości. W przypadku tablic o stałej długości, rozmiar zaimportowano z biblioteki typów i przechwycone w **MarshalAsAttribute** który został zastosowany do parametru.  
  
 Trzeba ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.  
  
 **Niezarządzane podpisu**  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 **Zarządzanego podpisu**  
  
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
  
 Chociaż można stosować **size_is** lub **length_is —** atrybuty do tablicy w źródle języka definicji interfejsu (IDL) w celu przekazania rozmiaru na kliencie Microsoft Interface Definition Language (MIDL) Kompilator nie propaguje tych informacji do biblioteki typów. Nie wiedząc o tym rozmiar, współdziałanie marshaling usługi nie można zorganizować elementów tablicy. W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania. Na przykład:  
  
 **Niezarządzane podpisu**  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 **Zarządzanego podpisu**  
  
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
  
 Możesz zapewnić Organizator rozmiar tablicy generowany kod intermediate language (MSIL) firmy Microsoft przez Tlbimp.exe do edycji, a następnie ponownego kompilowania. Aby uzyskać szczegółowe informacje dotyczące sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)). Wskaż liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ parametru tablicy definicji metody zarządzanego w jednym z następujących sposobów:  
  
- Określ inny parametr, który zawiera liczbę elementów w tablicy. Parametry są identyfikowane według położenia, rozpoczynając od pierwszego parametru jako numer 0.     
  
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
  
- Zdefiniować rozmiar tablicy jako stała. Na przykład:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Podczas przekazywania tablic z niezarządzanego kodu do kodu zarządzanego, organizator sprawdza **MarshalAsAttribute** skojarzone z parametru, aby określić rozmiar tablicy. Jeśli rozmiar tablicy nie jest określona, tylko jeden element jest organizowany.  
  
> [!NOTE]
>  **MarshalAsAttribute** nie wpływa na przekazywanie zarządzane macierze do kodu niezarządzanego. W tym kierunku rozmiar tablicy jest określana przez badanie. Nie ma możliwości marshalingu podzbiór tablicy zarządzanej.  
  
 Organizator międzyoperacyjny używa **CoTaskMemAlloc** i **CoTaskMemFree** metody przydzielania i pobrać pamięci. Alokacja pamięci wykonywane przez kod niezarządzany, należy również użyć tych metod.  
  
## <a name="passing-arrays-to-com"></a>Przekazywanie tablic modelowi COM  
 Wszystkie typy tablic zarządzanych mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego. W zależności od typu zarządzanego i atrybuty stosowane do niego tablicy może zostać oceniony jako bezpiecznej tablicy lub tablicy stylu C, jak pokazano w poniższej tabeli.  
  
|Zarządzany typ tablicy|Wyeksportowany jako|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**|<xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ jest dostarczany w podpisie. Ranga ma zawsze numer 1, dolna granica jest zawsze 0. Rozmiar zawsze jest znany w czasie wykonywania.|  
|**ELEMENT_TYPE_ARRAY** **\<** *typu* **>** **\<** *ranga* **>**[**\<** *granice* **>**]|**UnmanagedType.SafeArray(** *type* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Granice rangę, typ, znajdują się w podpisie. Rozmiar zawsze jest znany w czasie wykonywania.|  
|**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray(** *type* **)**<br /><br /> Typ, rangę, granice i rozmiar zawsze są znane w czasie wykonywania.|  
  
 Brak ograniczeń w automatyzacji OLE odnoszących się do tablic struktur, które zawierają LPSTR lub LPWSTR.  W związku z tym **ciąg** pola muszą być przekazywane jako **UnmanagedType.BSTR**. W przeciwnym razie zostanie zgłoszony wyjątek.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 Gdy metoda zawiera **ELEMENT_TYPE_SZARRAY** parametru (jednowymiarową) są eksportowane z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu. Zastosuj te same reguły konwersji do typów elementów tablicy. Zawartość tablicy zarządzanej są automatycznie kopiowane z pamięci zarządzanej do **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga tablic bezpiecznych ma zawsze numer 1 i dolna granica jest zawsze 0. Rozmiar jest określany w czasie wykonywania przez rozmiar tablicy zarządzanej przekazywana.  
  
 Tablica również może być organizowany jako tablicy stylu C za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Mimo że organizator ma długość potrzebnych do organizowania tablicy, długość tablicy zwykle jest przekazywany jako osobne argument przekazuję długość obiekt wywoływany.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 Gdy metoda zawiera **ELEMENT_TYPE_ARRAY** parametru została wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu. Zawartość tablicy zarządzanej są automatycznie kopiowane z pamięci zarządzanej do **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Rangę, rozmiar i granice tablic bezpiecznych są określane w czasie wykonywania przez właściwości tablicy zarządzanej.  
  
 Tablicy również może być organizowany jako tablicy stylu C, stosując <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Tablice zagnieżdżone nie mogą być przekazywane. Na przykład, następujący podpis generuje błąd podczas eksportowania z [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>ELEMENT_TYPE_CLASS \<System.Array>  
 Gdy metoda zawiera <xref:System.Array?displayProperty=nameWithType> parametru została wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **_Array** interfejsu. Zawartość tablicy zarządzanej jest dostępna tylko za pośrednictwem metody i właściwości **_Array** interfejsu. **System.Array** również może być organizowany jako **SAFEARRAY** przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Podczas przekazywania jako bezpieczną tablicą, elementy tablicy są organizowana jako wariantów. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Tablice w ramach struktury  
 Niezarządzane struktury mogą zawierać osadzonych tablic. Domyślnie te pola osadzoną tablicę są przekazywane jako obiektu SAFEARRAY. W poniższym przykładzie `s1` jest osadzoną tablicę, która została przydzielona bezpośrednio w samej strukturze.  
  
#### <a name="unmanaged-representation"></a>Reprezentacji niezarządzanej  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Tablice mogą być organizowane poza jako <xref:System.Runtime.InteropServices.UnmanagedType>, musisz ustawić <xref:System.Runtime.InteropServices.MarshalAsAttribute> pola. Rozmiar można ustawić tylko jako stała. Poniższy kod przedstawia definicję odpowiedniego zarządzanego `MyStruct`.  
  
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
