---
title: "Organizowanie domyślne dotyczące tablic"
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
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 91df17448a57f7495dc95fb2b4ab1fa63dd8a27f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-for-arrays"></a>Domyślny marshaling dla tablic
W aplikacji, składające się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako we/wy parametrów. Z kolei międzyoperacyjnego organizatora przekazuje tablicy, tak jak parametry domyślnie.  
  
 Z [przypinania optymalizacji](../../../docs/framework/interop/copying-and-pinning.md), tablicy kopiowalne może występować działanie jako In/Out parametru podczas interakcji z obiektów w tym samym apartamencie. Jeśli później wyeksportować kod do biblioteki typów, używany do generowania proxy między komputerami, a biblioteki jest używany do organizowania wywołania w apartamentach, wywołania można przywrócić na wartość true w zachowaniu parametru.  
  
 Tablice są skomplikowane natury, a różnice między zarządzanymi i niezarządzanymi macierzami gwarantuje więcej informacji od innych typów niekopiowalne. Ten temat zawiera następujące informacje na przekazywanie tablic:  
  
-   [Tablice zarządzane](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [Tablice niezarządzane](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [Przekazywanie parametrów tablicy do kodu platformy .NET](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [Przekazywanie tablic w modelu COM](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a>Tablice zarządzane  
 Zarządzane tablicy, która może różnić się typy; jednak <xref:System.Array?displayProperty=nameWithType> klasa jest klasą bazową dla wszystkich typów tablicy. **System.Array** klasa ma właściwości określające rangę, długość i dolną i górną granicę tablicy, a także metod do uzyskiwania dostępu do, sortowanie, wyszukiwanie, kopiowanie i tworzenia tablic.  
  
 Typy tablicy są dynamiczne i nie mają odpowiednich typu statycznego zdefiniowany w klasie podstawowej biblioteki. Jest wygodną Rozważmy każdej kombinacji typ elementu i rangę jako różne typu tablicy. W związku z tym jest tablicą jednowymiarową liczb całkowitych jest innego typu niż tablicą jednowymiarową typu double. Podobnie jest tablicą dwuwymiarową liczb całkowitych różni się od Jednowymiarowa tablica liczb całkowitych. Granice tablicy nie są uwzględniane podczas porównywania typów.  
  
 Jak pokazano na poniższej tabeli, wszystkie wystąpienia tablicy musi być typ określonego elementu, Ranking i dolną granicę.  
  
|Typ tablicy zarządzanego|Typ elementu|Ranga|Dolna granica|Notacja podpisu|  
|------------------------|------------------|----------|-----------------|------------------------|  
|**ELEMENT_TYPE_ARRAY**|Określony przez typ.|Określony przez rangę.|Opcjonalnie określony przez granice.|*Typ* **[**  *n* ,*m* **]**|  
|**ELEMENT_TYPE_CLASS**|Nieznany|Nieznany|Nieznany|**System.Array**|  
|**ELEMENT_TYPE_SZARRAY**|Określony przez typ.|1|0|*Typ* **[**  *n*  **]**|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a>Tablice niezarządzane  
 Tablice niezarządzane są tablice bezpieczne styl modelu COM lub stylu języka C tablice o stałym rozmiarze lub zmiennej długości. Tablice bezpieczne są samoopisujące tablic zawierających typu, Ranking i granice danych skojarzonej macierzy. Tablice w stylu języka C są jednowymiarowe tablice o określonym typie ze stałym dolna granica 0. Usługa kierowania ma ograniczony pomocy technicznej dla obu typów tablic.  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a>Przekazywanie parametrów tablicy do kodu platformy .NET  
 Zarówno tablic w stylu języka C i bezpieczne tablice mogą być przekazywane do kodu platformy .NET z kodem niezarządzanym jako bezpiecznej tablicy lub tablica stylu języka C. W poniższej tabeli przedstawiono wartości typu niezarządzanego i typu zaimportowanego.  
  
|Typ niezarządzany|Zaimportowany typ|  
|--------------------|-------------------|  
|**SafeArray (** *typu* **)**|**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znany, tylko jeśli są dostępne w zarządzanego podpisu. Tablice bezpieczne, które nie są rangi = 1 lub dolna granica = 0, nie mogą być przekazywane jako **SZARRAY**.|  
|*Typ***]** |**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**<br /><br /> Ranga = 1, dolna granica = 0. Rozmiar jest znany, tylko jeśli są dostępne w zarządzanego podpisu.|  
  
### <a name="safe-arrays"></a>Tablice bezpieczne  
 Po zaimportowaniu bezpiecznej tablicy z biblioteki typów na zestaw .NET tablicy jest konwertowana na tablicą jednowymiarową znanego typu (takich jak **int**). Tej samej reguły konwersji typów, które są stosowane do parametrów dotyczą również elementów tablicy. Na przykład bezpieczną tablicą o **BSTR** typy staje się tablicy ciągów i bezpieczną tablicą typu Variant staje się zarządzanych Tablica obiektów. **SAFEARRAY** typ elementu zostaną zebrane z biblioteki typów i zapisywane w **SAFEARRAY** wartość <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia.  
  
 Ponieważ ranga i granice bezpiecznej tablicy nie można określić z biblioteki typów, rangę zakłada, że jest równa 1 oraz dolną granicę zakłada, że jest równa 0. Ranga i zakresem, musi być zdefiniowana w zarządzanego podpisu utworzonego przez [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md). Jeśli różni się rangę przekazywany do metody w czasie wykonywania, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> jest generowany. Jeśli typ tablicy został przekazany w czasie wykonywania jest inny, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> jest generowany. Poniższy przykład przedstawia tablice bezpieczne, zarządzane i niezarządzane kodu.  
  
 **Niezarządzanego podpisu**  
  
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
  
 Wielowymiarowym lub niezerowe granica tablic bezpieczne, można zorganizować kodu zarządzanego, jeśli podpis metody generowane przez Tlbimp.exe są modyfikowane w celu wskazywać typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_ TYPE_SZARRAY**. Alternatywnie można użyć **/sysarray** przełącznik z Tlbimp.exe Aby zaimportować wszystkie tablice jako <xref:System.Array?displayProperty=nameWithType> obiektów. W przypadkach, gdy tablica przekazywany jest znany jako wielowymiarowych możesz edytować wyprodukowanych kod języka pośredniego (MSIL) firmy Microsoft przez Tlbimp.exe i ponownie go skompilować. Aby uzyskać szczegółowe informacje na temat sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływane otoki środowiska uruchomieniowego](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be).  
  
### <a name="c-style-arrays"></a>Tablice w stylu języka C  
 Po zaimportowaniu tablicy stylu języka C z biblioteki typów na zestaw .NET tablicy jest konwertowana na **ELEMENT_TYPE_SZARRAY**.  
  
 Typ elementu tablicy jest określana na podstawie biblioteki typów i zachowane podczas importowania. Tej samej reguły konwersji, które są stosowane do parametrów dotyczą również elementów tablicy. Na przykład tablicę **LPStr** typy staje się tablicę **ciąg** typów. Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu parametru.  
  
 Ranga tablicy zakłada się, że równa 1. Jeśli pozycja jest większa niż 1, tablicy jest przekazywane jako tablica jednowymiarowa w kolejności kolumn. Dolna granica jest zawsze równa 0.  
  
 Biblioteki typów mogą zawierać tablic o stałej lub zmiennej długości. Tlbimp.exe można importować tylko o stałej długości tablic z biblioteki typów, ponieważ informacje wymagane do organizowania tablice o zmiennej długości brakuje biblioteki typów. O stałej długości tablic, rozmiar jest zaimportowany z biblioteki typów i przechwytywane **atrybut MarshalAsAttribute** do parametru zastosowano.  
  
 Trzeba ręcznie zdefiniować typu biblioteki zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.  
  
 **Niezarządzanego podpisu**  
  
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
  
 Mimo że można zastosować **size_is** lub **length_is —** atrybutów do tablicy w źródle języka definicji interfejsu (IDL) w celu przedstawienia rozmiar do klienta, języka definicji interfejsu firmy Microsoft (MIDL) Kompilator nie są propagowane tych informacji do biblioteki typów. Bez wiedzy o rozmiar, interop organizowanie usługi nie można zorganizować elementów tablicy. W rezultacie tablice o zmiennej długości są importowane jako argumenty odwołania. Na przykład:  
  
 **Niezarządzanego podpisu**  
  
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
  
 Organizator można udostępnić w rozmiar tablicy, edytując kod języka pośredniego (MSIL) wyprodukowanych firmy Microsoft przez Tlbimp.exe i następnie ponownej kompilacji. Aby uzyskać szczegółowe informacje na temat sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływane otoki środowiska uruchomieniowego](http://msdn.microsoft.com/library/4652beaf-77d0-4f37-9687-ca193288c0be). Wskaż liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> typu parametru tablicy definicji metody zarządzanego w jednym z następujących sposobów:  
  
-   Określ inny parametr, który zawiera liczbę elementów w tablicy. Parametry są identyfikowane za pomocą pozycji, począwszy od pierwszego parametru jako liczba 0.     
  
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
  
-   Zdefiniuj rozmiar tablicy jako stała. Na przykład:  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 Podczas organizowania tablic z kodem niezarządzanym do kodu zarządzanego, sprawdza organizatora **atrybut MarshalAsAttribute** skojarzonych z parametrem, aby określić rozmiar tablicy. Jeśli nie określono rozmiaru tablicy, zorganizować jest tylko jeden element.  
  
> [!NOTE]
>  **Atrybut MarshalAsAttribute** nie wpływa na przekazywanie zarządza tablic do kodu niezarządzanego. W tym kierunku rozmiaru tablicy jest określana przez badania. Nie istnieje sposób do organizowania podzbiór tablicy.  
  
 Organizator międzyoperacyjnego używa **CoTaskMemAlloc** i **CoTaskMemFree** metod można przydzielić i pobrać pamięci. Alokacja pamięci wykonywane przez kod niezarządzany również użyć tych metod.  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a>Przekazywanie tablic w modelu COM  
 Wszystkie typy tablicy mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego. W zależności od typu zarządzanego i atrybuty tablicy są dostępne jako bezpiecznej tablicy lub tablica stylu języka C, jak pokazano w poniższej tabeli.  
  
|Typ tablicy zarządzanego|Wyeksportowany jako|  
|------------------------|-----------------|  
|**ELEMENT_TYPE_SZARRAY**  **\<**  *typu***>**|<xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *typu* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Typ jest dostępne w podpisie. Pozycja ma zawsze numer 1, dolna granica jest zawsze 0. Rozmiar zawsze jest znany w czasie wykonywania.|  
|**ELEMENT_TYPE_ARRAY**  **\<**  *typu*  **>**   **\<**  *rangę*  **>** [ **\<**  *granice*  **>** ]|**UnmanagedType.SafeArray (** *typu* **)**<br /><br /> **UnmanagedType.LPArray**<br /><br /> Granice rangi, typ, znajdują się w podpisie. Rozmiar zawsze jest znany w czasie wykonywania.|  
|**PO ELEMENCIE ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**|**UT_Interface**<br /><br /> **UnmanagedType.SafeArray (** *typu* **)**<br /><br /> Typ, pozycja, granice i rozmiar zawsze są określane w czasie wykonywania.|  
  
 Istnieje ograniczenie w automatyzacji OLE odnoszących się do tablic struktury zawierające LPSTR lub LPWSTR.  W związku z tym **ciąg** pola muszą być przekazywane jako **UnmanagedType.BSTR**. W przeciwnym razie zostanie wygenerowany wyjątek.  
  
### <a name="elementtypeszarray"></a>ELEMENT_TYPE_SZARRAY  
 Gdy metoda zawiera **ELEMENT_TYPE_SZARRAY** parametr (jednowymiarową) jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **SAFEARRAY** danego typu. Te same reguły konwersji dotyczą typ elementu tablicy. Zawartość tablicy zarządzanej automatycznie są kopiowane z pamięci zarządzanej do **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Pozycja tablice bezpieczne ma zawsze numer 1 i dolną granicą jest zawsze 0. Rozmiar jest określany w czasie wykonywania przez rozmiar tablicy zarządzanej przekazywany.  
  
 Tablica można również zorganizować jako tablica stylu języka C za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Na przykład:  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Mimo że organizator ma długość potrzebnych do organizowania tablicy, długość tablicy zwykle jest przekazywany jako osobne argumentu o długości do wywoływany.  
  
### <a name="elementtypearray"></a>ELEMENT_TYPE_ARRAY  
 Gdy metoda zawiera **ELEMENT_TYPE_ARRAY** parametru jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **SAFEARRAY** danego typu. Zawartość tablicy zarządzanej automatycznie są kopiowane z pamięci zarządzanej do **SAFEARRAY**. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 Ranga, rozmiar i granice tablice bezpieczne są określane w czasie wykonywania przez właściwości tablicy zarządzanej.  
  
 Tablica można również zorganizować jako tablica stylu języka C, stosując <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Na przykład:  
  
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
  
#### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 Tablice zagnieżdżone nie mogą być przekazywane. Na przykład następująca sygnatura generuje błąd podczas eksportowania z [Eksporter biblioteki typów (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a>Po elemencie ELEMENT_TYPE_CLASS \<System.Array >  
 Gdy metoda zawiera <xref:System.Array?displayProperty=nameWithType> parametru jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **_Array** interfejsu. Zawartość tablicy zarządzanej są dostępne tylko za pośrednictwem metody i właściwości **_Array** interfejsu. **System.Array** również mogą być przekazywane jako **SAFEARRAY** przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu. Gdy przekazywane jako Tablica bezpieczna, elementy tablicy są przekazywane jako wariantów. Na przykład:  
  
#### <a name="managed-signature"></a>Zarządzanego podpisu  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a>Tablice w strukturach  
 Niezarządzane struktury może zawierać osadzone tablic. Domyślnie te pola osadzonej tablicy są przekazywane jako obiektu SAFEARRAY. W poniższym przykładzie `s1` jest osadzoną tablicę, która jest przydzielane bezpośrednio w strukturze samej siebie.  
  
#### <a name="unmanaged-representation"></a>Reprezentacja niezarządzane  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 Tablice mogą być przekazywane jako <xref:System.Runtime.InteropServices.UnmanagedType>, który wymaga ustawienia <xref:System.Runtime.InteropServices.MarshalAsAttribute> pola. Rozmiar można ustawić tylko jako stała. Poniższy kod przedstawia odpowiedniego zarządzanej definicji `MyStruct`.  
  
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
 [Domyślne zachowanie marshalingu](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [Typy kopiowalne i niekopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Atrybuty kierunkową](http://msdn.microsoft.com/library/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [Kopiowanie i przypinanie](../../../docs/framework/interop/copying-and-pinning.md)
