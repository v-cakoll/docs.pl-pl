---
title: Domyślne zachowanie marshalingu
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: f7df323dacfbee3361fe75d831f1e87df328b194
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989223"
---
# <a name="default-marshaling-behavior"></a>Domyślne zachowanie marshalingu
Międzyoperacyjne organizowanie działa na reguły, które określają, jak dane skojarzone z parametrami metody zachowuje się, jak przechodzi między pamięcią zarządzaną i niezarządzaną. Te wbudowane reguły kontrolują takie działania organizowania jak przekształcenia typu danych, czy wywoływany może zmieniać dane przekazywane do niego i zwracać te zmiany do obiektu wywołującego i w jakich okolicznościach organizator zapewnia optymalizacje wydajności.  
  
 W tej sekcji identyfikuje domyślne cechy behawioralne usługi międzyoperacyjnej. Przedstawia szczegółowe informacje na temat organizowania tablic, typów logicznych, typów znaków, delegatów, klas, obiektów, ciągów i struktur.  
  
> [!NOTE]
> Kierowanie typów ogólnych nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Zarządzanie pamięcią za pomocą organizatora międzyoperacyjnego  
 Organizator międzyoperacyjny zawsze próbuje zwolnić pamięć przydzieloną przez kod niezarządzany. To zachowanie jest zgodne z regułami zarządzania pamięcią COM, ale różni się od reguł, które regulują natywne C++.  
  
 Zamieszanie może wystąpić, jeśli przewidujesz natywne zachowanie języka C++ (bez zwalniania pamięci) podczas korzystania z platformy wywołania, która automatycznie zwalnia pamięć dla wskaźników. Na przykład wywołanie następującej metody niezarządzane z biblioteki DLL języka C++ nie zwalnia automatycznie pamięci.  
  
### <a name="unmanaged-signature"></a>Podpis niezarządzany  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Jeśli jednak zdefiniujesz metodę jako prototyp wywołania platformy, zastąp `MethodOne`każdy typ **BSTR** typem <xref:System.String> i wywołaj , środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy. Zachowanie organizowania można zmienić <xref:System.IntPtr> przy użyciu typów, a nie **string** typów.  
  
 Środowisko wykonawcze zawsze używa **CoTaskMemFree** metody do zwolnienia pamięci. Jeśli pamięć, z którą pracujesz, nie została przydzielona za pomocą metody **CoTaskMemAlloc,** należy użyć **IntPtr** i zwolnić pamięć ręcznie przy użyciu odpowiedniej metody. Podobnie można uniknąć automatycznego zwalniania pamięci w sytuacjach, w których pamięć nigdy nie powinna być zwalniana, na przykład podczas korzystania z funkcji **GetCommandLine** z pliku Kernel32.dll, która zwraca wskaźnik do pamięci jądra. Aby uzyskać szczegółowe informacje na temat ręcznego zwalniania pamięci, zobacz [przykład buforów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Domyślne kierowanie dla klas  
 Klasy mogą być organizowane tylko przez com interop i są zawsze organizowane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy jest znany jako interfejs klasy. Aby uzyskać informacje na temat zastępowania interfejsu klasy za pomocą wybranego interfejsu, zobacz [Przedstawianie interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Przekazywanie klas do com  
 Gdy klasa zarządzana jest przekazywana do com, międzyoperacyjny organizator automatycznie zawija klasę z serwerem proxy COM i przekazuje interfejs klasy wytwarzany przez serwer proxy do wywołania metody COM. Następnie serwer proxy deleguje wszystkie wywołania interfejsu klasy z powrotem do obiektu zarządzanego. Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowane przez klasę. Serwer proxy automatycznie implementuje interfejsy, takie jak **IUnknown** i **IDispatch** w imieniu klasy.  
  
### <a name="passing-classes-to-net-code"></a>Przekazywanie klas do kodu .NET  
 Coclasses nie są zwykle używane jako argumenty metody w COM. Zamiast tego domyślny interfejs jest zwykle przekazywany zamiast coclass.  
  
 Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyop jest odpowiedzialny za zawijanie interfejsu z właściwą otoką i przekazywanie otoki do metody zarządzanej. Określenie, które opakowanie do użycia może być trudne. Każde wystąpienie obiektu COM ma pojedyncze, unikatowe otoki, bez względu na to, ile interfejsów implementuje obiekt. Na przykład pojedynczy obiekt COM, który implementuje pięć różnych interfejsów ma tylko jedną otokę. Ta sama otoka udostępnia wszystkie pięć interfejsów. Jeśli zostaną utworzone dwa wystąpienia obiektu COM, zostaną utworzone dwa wystąpienia otoki.  
  
 Dla otoki, aby zachować ten sam typ przez cały okres jego istnienia, międzyopranieżator musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępniane przez obiekt jest przekazywany przez organizatora. Organizator identyfikuje obiekt, patrząc na jeden z interfejsów implementuje obiekt.  
  
 Na przykład organizator określa, że otoka klasy powinna służyć do zawijania interfejsu, który został przekazany do kodu zarządzanego. Gdy interfejs jest po raz pierwszy przekazywane przez organizatora, organizator sprawdza, czy interfejs pochodzi ze znanego obiektu. Kontrola ta występuje w dwóch sytuacjach:  
  
- Interfejs jest implementowany przez inny obiekt zarządzany, który został przekazany do com gdzie indziej. Organizator może łatwo zidentyfikować interfejsy udostępniane przez obiekty zarządzane i jest w stanie dopasować interfejs do obiektu zarządzanego, który zapewnia implementację. Obiekt zarządzany jest następnie przekazywany do metody i nie jest potrzebne otoki.  
  
- Obiekt, który został już opakowany implementuje interfejs. Aby ustalić, czy tak jest, organizator zapytania obiektu dla jego **interfejsu IUnknown** i porównuje zwrócony interfejs do interfejsów innych obiektów, które są już opakowane. Jeśli interfejs jest taki sam jak w innym otoce, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywana do metody.  
  
 Jeśli interfejs nie pochodzi ze znanego obiektu, organizator wykonuje następujące czynności:  
  
1. Organizator zapytania obiektu dla interfejsu **IProvideClassInfo2.** Jeśli pod warunkiem, organizator używa CLSID zwrócony z **IProvideClassInfo2.GetGUID** do identyfikowania coclass dostarczanie interfejsu. Za pomocą identyfikatora CLSID organizator może zlokalizować otokę z rejestru, jeśli zestaw został wcześniej zarejestrowany.  
  
2. Organizator wysyła zapytanie do interfejsu **interfejsu IProvideClassInfo.** Jeśli pod warunkiem, organizator używa **ITypeInfo** zwrócone z **IProvideClassInfo.GetClassinfo** do określenia CLSID klasy uwidaczniania interfejsu. Organizator może użyć identyfikatora CLSID, aby zlokalizować metadane otoki.  
  
3. Jeśli organizator nadal nie może zidentyfikować klasy, zawija interfejs z klasą otoki ogólnej o nazwie **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Domyślne kierowanie dla delegatów  
 Zarządzany delegat jest organizowany jako interfejs COM lub jako wskaźnik funkcji, na podstawie mechanizmu wywołującego:  
  
- W przypadku wywołania platformy pełnomocnik jest domyślnie organizowany jako wskaźnik funkcji niezarządzanej.  
  
- W przypadku interop COM delegat jest organizowany jako interfejs COM typu **_Delegate** domyślnie. Interfejs **_Delegate** jest zdefiniowany w bibliotece typu Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodę, która umożliwia wywołanie metody, do której odwołuje się delegat.  
  
 W poniższej tabeli przedstawiono opcje organizowania dla typu danych zarządzanych delegatów. Atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do delegatów marshal.  
  
|Typ wyliczenia|Opis formatu niezarządzanego|  
|----------------------|-------------------------------------|  
|**NiezarządzaneType.FunctionPtr**|Wskaźnik funkcji niezarządzanej.|  
|**Niezarządzany typ.interfejs**|Interfejs typu **_Delegate**, zgodnie z definicją w mscorlib.tlb.|  
  
 Należy wziąć pod uwagę poniższy `DelegateTestInterface` przykładowy kod, w którym metody są eksportowane do biblioteki typów COM. Należy zauważyć, że tylko delegatów **oznaczonych ref** (lub **ByRef**) słowo kluczowe są przekazywane jako in/out parametry.  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public interface DelegateTest {  
void m1(Delegate d);  
void m2([MarshalAs(UnmanagedType.Interface)] Delegate d);
void m3([MarshalAs(UnmanagedType.Interface)] ref Delegate d);
void m4([MarshalAs(UnmanagedType.FunctionPtr)] Delegate d);
void m5([MarshalAs(UnmanagedType.FunctionPtr)] ref Delegate d);
}  
```  
  
### <a name="type-library-representation"></a>Reprezentacja biblioteki typów  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Wskaźnik funkcji może być wyłuskiwane, podobnie jak każdy inny wskaźnik funkcji niezarządzane mogą być wyłuskiwane.  

W tym przykładzie, gdy dwóch delegatów są organizowane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, wynik jest `int` i wskaźnik do . `int` Ponieważ typy delegata `int` są organizowane, w`void*`tym miejscu reprezentuje wskaźnik do void ( ), który jest adres delegata w pamięci. Innymi słowy ten wynik jest specyficzne dla 32-bitowych systemów Windows, ponieważ `int` w tym miejscu reprezentuje rozmiar wskaźnika funkcji.

> [!NOTE]
> Odwołanie do wskaźnika funkcji do zarządzanego delegata przechowywanego przez kod niezarządzany nie uniemożliwia wykonywania środowiska wykonawczego języka wspólnego w obiekcie zarządzanym.  
  
 Na przykład poniższy kod jest niepoprawna, ponieważ `cb` odwołanie `SetChangeHandler` do obiektu, `cb` przekazane do metody, nie utrzymuje przy życiu poza okresem `Test` życia metody. Gdy `cb` obiekt jest zbierane śmieci, wskaźnik `SetChangeHandler` funkcji przekazany do nie jest już prawidłowy.  
  
```csharp  
public class ExternalAPI {  
   [DllImport("External.dll")]  
   public static extern void SetChangeHandler(  
      [MarshalAs(UnmanagedType.FunctionPtr)]ChangeDelegate d);  
}  
public delegate bool ChangeDelegate([MarshalAs(UnmanagedType.LPWStr) string S);  
public class CallBackClass {  
   public bool OnChange(string S){ return true;}  
}  
internal class DelegateTest {  
   public static void Test() {  
      CallBackClass cb = new CallBackClass();  
      // Caution: The following reference on the cb object does not keep the
      // object from being garbage collected after the Main method
      // executes.  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));
   }  
}  
```  
  
 Aby zrekompensować nieoczekiwane wyrzucania elementów `cb` bezużytecznych, obiekt wywołujący musi upewnić się, że obiekt jest utrzymywany przy życiu tak długo, jak wskaźnik funkcji niezarządzane jest w użyciu. Opcjonalnie można mieć kod niezarządzany powiadamiać kod zarządzany, gdy wskaźnik funkcji nie jest już potrzebne, jak pokazano w poniższym przykładzie.  
  
```csharp  
internal class DelegateTest {  
   CallBackClass cb;  
   // Called before ever using the callback function.  
   public static void SetChangeHandler() {  
      cb = new CallBackClass();  
      ExternalAPI.SetChangeHandler(new ChangeDelegate(cb.OnChange));  
   }  
   // Called after using the callback function for the last time.  
   public static void RemoveChangeHandler() {  
      // The cb object can be collected now. The unmanaged code is
      // finished with the callback function.  
      cb = null;  
   }  
}  
```  
  
## <a name="default-marshaling-for-value-types"></a>Domyślne kierowanie dla typów wartości  
 Większość typów wartości, takich jak liczby całkowite i numery zmiennoprzecinkowe, są [blittable](blittable-and-non-blittable-types.md) i nie wymagają organizowania. Inne [typy niedlażne](blittable-and-non-blittable-types.md) mają różne reprezentacje w pamięci zarządzanej i niezarządzanej i wymagają organizowania. Nadal inne typy wymagają jawnego formatowania w granicach współdziałania.  
  
 Ta sekcja zawiera informacje na temat następujących sformatowanych typów wartości:  
  
- [Typy wartości używane w wywoływaniu platformy](#value-types-used-in-platform-invoke)  
  
- [Typy wartości używane w com interop](#value-types-used-in-com-interop)  
  
 Oprócz opisywania sformatowanych typów w tym temacie identyfikowane [są typy wartości systemowej,](#system-value-types) które mają nietypowe zachowanie organizowania.  
  
 Sformatowany typ jest typem złożonym, który zawiera informacje, które jawnie kontroluje układ jego członków w pamięci. Informacje o układzie elementu <xref:System.Runtime.InteropServices.StructLayoutAttribute> członkowskiego są dostarczane przy użyciu atrybutu. Układ może być jedną <xref:System.Runtime.InteropServices.LayoutKind> z następujących wartości wyliczenia:  
  
- **UkładKind.Auto**  
  
     Wskazuje, że środowisko uruchomieniowe języka wspólnego jest wolne do ponownego zamówenia elementów członkowskich typu dla wydajności. Jednak gdy typ wartości jest przekazywany do kodu niezarządzanego, układ elementów członkowskich jest przewidywalny. Próba zorganizowania takiej struktury automatycznie powoduje wyjątek.  
  
- **Layoutkind.sequential**  
  
     Wskazuje, że elementy członkowskie typu mają być określone w pamięci niezarządzanej w tej samej kolejności, w jakiej pojawiają się w definicji typu zarządzanego.  
  
- **Layoutkind.explicit**  
  
     Wskazuje, że elementy członkowskie są <xref:System.Runtime.InteropServices.FieldOffsetAttribute> rozmieszczone zgodnie z dostarczonymi z każdym polem.  
  
### <a name="value-types-used-in-platform-invoke"></a>Typy wartości używane w wywoływaniu platformy  
 W poniższym `Point` przykładzie i `Rect` typy zawierają informacje o układzie elementu członkowskiego przy użyciu **StructLayoutAttribute**.  
  
```vb  
Imports System.Runtime.InteropServices  
<StructLayout(LayoutKind.Sequential)> Public Structure Point  
   Public x As Integer  
   Public y As Integer  
End Structure  
<StructLayout(LayoutKind.Explicit)> Public Structure Rect  
   <FieldOffset(0)> Public left As Integer  
   <FieldOffset(4)> Public top As Integer  
   <FieldOffset(8)> Public right As Integer  
   <FieldOffset(12)> Public bottom As Integer  
End Structure  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[StructLayout(LayoutKind.Sequential)]  
public struct Point {  
   public int x;  
   public int y;  
}
  
[StructLayout(LayoutKind.Explicit)]  
public struct Rect {  
   [FieldOffset(0)] public int left;  
   [FieldOffset(4)] public int top;  
   [FieldOffset(8)] public int right;  
   [FieldOffset(12)] public int bottom;  
}  
```  
  
 Gdy kierowane do kodu niezarządzanego, te sformatowane typy są organizowane jako struktury w stylu C. Zapewnia to łatwy sposób wywoływania niezarządzanego interfejsu API, który ma argumenty struktury. Na przykład `POINT` struktury `RECT` i mogą być przekazywane do funkcji **PtInRect** interfejsu API systemu Microsoft Windows w następujący sposób:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Struktury można przekazać przy użyciu następującej definicji wywołania platformy:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 Typ `Rect` wartości musi być przekazywany przez odwołanie, ponieważ niezarządzany interfejs API oczekuje `RECT` wskaźnika do przekazania do funkcji. Typ `Point` wartości jest przekazywany przez wartość, ponieważ `POINT` niezarządzany interfejs API oczekuje, że mają być przekazywane na stosie. Ta subtelna różnica jest bardzo ważna. Odwołania są przekazywane do kodu niezarządzanego jako wskaźniki. Wartości są przekazywane do kodu niezarządzanego na stosie.  
  
> [!NOTE]
> Gdy sformatowany typ jest zorganizowany jako struktura, tylko pola w typie są dostępne. Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z kodu niezarządzanego.  
  
 Klasy mogą być również kierowane do kodu niezarządzanego jako struktury w stylu C, pod warunkiem, że mają stały układ elementu członkowskiego. Informacje o układzie członkowskim dla klasy <xref:System.Runtime.InteropServices.StructLayoutAttribute> są również dostarczane z atrybutem. Główną różnicą między typami wartości o stałym układzie i klas o stałym układzie jest sposób, w jaki są one kierowane do kodu niezarządzanego. Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszelkie zmiany wprowadzone do elementów członkowskich typu przez wywoływanego nie są widoczne przez wywołującego. Typy odwołań są przekazywane przez odwołanie (odwołanie do typu jest przekazywana na stosie); w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu blittable typu typu przez wywoływanego są widoczne przez wywołującego.  
  
> [!NOTE]
> Jeśli typ odwołania ma członków typów nieblittable, konwersja jest wymagana dwa razy: po raz pierwszy, gdy argument jest przekazywany do strony niezarządzanej i po raz drugi po powrocie z wywołania. Ze względu na to dodatkowe obciążenie, in/out parametry muszą być jawnie stosowane do argumentu, jeśli wywołujący chce zobaczyć zmiany wprowadzone przez wywoływanego.  
  
 W poniższym przykładzie `SystemTime` klasa ma sekwencyjny układ elementu członkowskiego i może być przekazywana do funkcji **GetSystemTime** interfejsu API systemu Windows.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class SystemTime  
   Public wYear As System.UInt16  
   Public wMonth As System.UInt16  
   Public wDayOfWeek As System.UInt16  
   Public wDay As System.UInt16  
   Public wHour As System.UInt16  
   Public wMinute As System.UInt16  
   Public wSecond As System.UInt16  
   Public wMilliseconds As System.UInt16  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
   public class SystemTime {  
   public ushort wYear;
   public ushort wMonth;  
   public ushort wDayOfWeek;
   public ushort wDay;
   public ushort wHour;
   public ushort wMinute;
   public ushort wSecond;
   public ushort wMilliseconds;
}  
```  
  
 Funkcja **GetSystemTime** jest zdefiniowana w następujący sposób:  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Równoważna definicja wywołania platformy dla **Systemu GetSystemTime** jest następująca:  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 Należy zauważyć, że `SystemTime` argument nie jest `SystemTime` wpisywany jako argument odwołania, ponieważ jest klasą, a nie typem wartości. W przeciwieństwie do typów wartości klasy są zawsze przekazywane przez odwołanie.  
  
 Poniższy przykład kodu `Point` pokazuje inną klasę, `SetXY`która ma metodę o nazwie . Ponieważ typ ma układ sekwencyjny, może być przekazywana do kodu niezarządzanego i kierowane jako struktura. Jednak element `SetXY` członkowski nie jest wywoływany z kodu niezarządzanego, nawet jeśli obiekt jest przekazywany przez odwołanie.  
  
```vb  
<StructLayout(LayoutKind.Sequential)> Public Class Point  
   Private x, y As Integer  
   Public Sub SetXY(x As Integer, y As Integer)  
      Me.x = x  
      Me.y = y  
   End Sub  
End Class  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public class Point {  
   int x, y;  
   public void SetXY(int x, int y){
      this.x = x;  
      this.y = y;  
   }  
}  
```  
  
### <a name="value-types-used-in-com-interop"></a>Typy wartości używane w com interop  
 Sformatowane typy mogą być również przekazywane do wywołań metody współdziałać COM. W rzeczywistości po wyeksportowaniu do biblioteki typów typów wartości są automatycznie konwertowane na struktury. Jak pokazano w poniższym `Point` przykładzie, typ wartości staje się `Point`definicją typu (typedef) o nazwie . Wszystkie odwołania do `Point` typu wartości w innym miejscu `Point` w bibliotece typów są zastępowane typedef.  
  
 **Reprezentacja biblioteki typów**  
  
```cpp  
typedef struct tagPoint {  
   int x;  
   int y;  
} Point;  
interface _Graphics {  
   …  
   HRESULT SetPoint ([in] Point p)  
   HRESULT SetPointRef ([in,out] Point *p)  
   HRESULT GetPoint ([out,retval] Point *p)  
}  
```  
  
 Te same reguły używane do organizowania wartości i odwołania do wywołania platformy są używane podczas organizowania za pośrednictwem interfejsów COM. Na przykład gdy wystąpienie `Point` typu wartości jest przekazywana z `Point` programu .NET Framework do COM, jest przekazywana przez wartość. Jeśli `Point` typ wartości jest przekazywany przez `Point` odwołanie, wskaźnik do a jest przekazywany na stosie. Organizator międzyoperacyjny nie obsługuje wyższych poziomów pośrednich (**Punkt** \* \*) w obu kierunkach.  
  
> [!NOTE]
> Struktury o <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia ustawionej **na Jawne** nie można używać w współdziałanie COM, ponieważ eksportowana biblioteka typów nie może wyrazić jawnego układu.  
  
### <a name="system-value-types"></a>Typy wartości systemowych  
 Obszar <xref:System> nazw ma kilka typów wartości, które reprezentują formę pudełkową typów pierwotnych środowiska wykonawczego. Na przykład struktura <xref:System.Int32?displayProperty=nameWithType> typu wartości reprezentuje formę ELEMENT_TYPE_I4 **.** Zamiast organizowania tych typów jako struktur, jak inne typy sformatowane są, kierunkować je w taki sam sposób jak typy pierwotne, które polu. **System.Int32** jest zatem organizowany jako **ELEMENT_TYPE_I4,** a nie jako struktura zawierająca pojedynczy element członkowski typu **long**. Poniższa tabela zawiera listę typów wartości w obszarze nazw **system,** które są pudełkowymi reprezentacjami typów pierwotnych.  
  
|Typ wartości systemu|Typ elementu|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|**ELEMENT_TYPE_BOOLEAN**|  
|<xref:System.SByte?displayProperty=nameWithType>|**ELEMENT_TYPE_I1**|  
|<xref:System.Byte?displayProperty=nameWithType>|**ELEMENT_TYPE_UI1**|  
|<xref:System.Char?displayProperty=nameWithType>|**ELEMENT_TYPE_CHAR**|  
|<xref:System.Int16?displayProperty=nameWithType>|**ELEMENT_TYPE_I2**|  
|<xref:System.UInt16?displayProperty=nameWithType>|**ELEMENT_TYPE_U2**|  
|<xref:System.Int32?displayProperty=nameWithType>|**ELEMENT_TYPE_I4**|  
|<xref:System.UInt32?displayProperty=nameWithType>|**ELEMENT_TYPE_U4**|  
|<xref:System.Int64?displayProperty=nameWithType>|**ELEMENT_TYPE_I8**|  
|<xref:System.UInt64?displayProperty=nameWithType>|**ELEMENT_TYPE_U8**|  
|<xref:System.Single?displayProperty=nameWithType>|**ELEMENT_TYPE_R4**|  
|<xref:System.Double?displayProperty=nameWithType>|**ELEMENT_TYPE_R8**|  
|<xref:System.String?displayProperty=nameWithType>|**ELEMENT_TYPE_STRING**|  
|<xref:System.IntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_I**|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|**ELEMENT_TYPE_U**|  
  
 Niektóre inne typy wartości w obszarze nazw **systemu** są obsługiwane inaczej. Ponieważ kod niezarządzany ma już ugruntowane formaty dla tych typów, organizator ma specjalne reguły dotyczące organizowania ich. W poniższej tabeli wymieniono specjalne typy wartości w obszarze nazw **systemu,** a także typ niezarządzany, do których są organizowane.  
  
|Typ wartości systemu|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**Data**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**Dziesiętnych**|  
|<xref:System.Guid?displayProperty=nameWithType>|**Identyfikator guid**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Poniższy kod przedstawia definicję niezarządzanych typów **DATE,** **GUID,** **DECIMAL**i **OLE_COLOR** w bibliotece typów Stdole2.  
  
#### <a name="type-library-representation"></a>Reprezentacja biblioteki typów  
  
```cpp  
typedef double DATE;  
typedef DWORD OLE_COLOR;  
  
typedef struct tagDEC {  
    USHORT    wReserved;  
    BYTE      scale;  
    BYTE      sign;  
    ULONG     Hi32;  
    ULONGLONG Lo64;  
} DECIMAL;  
  
typedef struct tagGUID {  
    DWORD Data1;  
    WORD  Data2;  
    WORD  Data3;  
    BYTE  Data4[ 8 ];  
} GUID;  
```  
  
 Poniższy kod przedstawia odpowiednie definicje `IValueTypes` w interfejsie zarządzanym.  
  
```vb  
Public Interface IValueTypes  
   Sub M1(d As System.DateTime)  
   Sub M2(d As System.Guid)  
   Sub M3(d As System.Decimal)  
   Sub M4(d As System.Drawing.Color)  
End Interface  
```  
  
```csharp  
public interface IValueTypes {  
   void M1(System.DateTime d);  
   void M2(System.Guid d);  
   void M3(System.Decimal d);  
   void M4(System.Drawing.Color d);  
}  
```  
  
#### <a name="type-library-representation"></a>Reprezentacja biblioteki typów  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Zobacz też

- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Kopiowanie i przypinanie](copying-and-pinning.md)
- [Organizowanie domyślne dotyczące tablic](default-marshaling-for-arrays.md)
- [Domyślny marshaling dla obiektów](default-marshaling-for-objects.md)
- [Organizowanie domyślne dotyczące ciągów](default-marshaling-for-strings.md)
