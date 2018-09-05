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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aedc7b1941268184b71713d31913dbfbd8b74643
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504262"
---
# <a name="default-marshaling-behavior"></a>Domyślne zachowanie marshalingu
Marshaling międzyoperacyjny działa w regułach tego dyktować, jak dane skojarzone z parametrami metody zachowuje się jak przekazuje między zarządzanymi i niezarządzanymi pamięci. Te wbudowane reguły kontrolować takie kierowania działań jako przekształcenia typu danych, / / wywoływany można zmienić danych przekazanych do niego i zwracają te zmiany do obiektu wywołującego, a w ramach której okolicznościach Organizator udostępnia optymalizację wydajności.  
  
 W tej sekcji wymieniono domyślnych parametrów zachowań interop marshaling usługi. Przedstawia ona szczegółowe informacje na temat organizowanie tablic, typów logicznych, typu char, delegatów, klas, obiektów, ciągi i struktur.  
  
> [!NOTE]
>  Marshaling typów ogólnych nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [współpracy za pomocą typów ogólnych](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Zarządzanie pamięcią za pomocą organizatora międzyoperacyjnego  
 Organizator międzyoperacyjny zawsze spróbuje zwolnić pamięć przydzielana przez kod niezarządzany. To zachowanie jest zgodne z zasadami zarządzania pamięci COM, ale różni się od reguły rządzące natywnych języka C++.  
  
 Błąd może wystąpić, jeśli przewidujesz natywnych zachowania C++ (nie pamięci zwalnianie) podczas używania platformy wywołać, który automatycznie zwalnia pamięć dla wskaźników. Na przykład wywołanie następujące metody niezarządzanego z biblioteki DLL w języku C++ nie automatycznie zwolni wszystkie pamięci.  
  
### <a name="unmanaged-signature"></a>Niezarządzane podpisu  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Jednakże, jeśli zdefiniujesz metody jako prototyp wywołania platformy, Zastąp każde **BSTR** to typ <xref:System.String> typu, a następnie wywołaj `MethodOne`, środowisko uruchomieniowe języka wspólnego spróbuje zwolnić `b` dwa razy. Można zmienić zachowanie organizowania za pomocą <xref:System.IntPtr> typy zamiast **ciąg** typów.  
  
 Środowisko uruchomieniowe zawsze używa **CoTaskMemFree** metodę, aby zwolnić pamięć. Jeśli pamięci, w którym pracujesz, nie została przydzielona za pomocą **CoTaskMemAlloc** metody, należy użyć **IntPtr** i zwalniają pamięć ręcznie przy użyciu odpowiedniej metody. Podobnie, można uniknąć pamięcią automatyczną zwalnianie w sytuacjach, w których nigdy nie powinna być zwolniona pamięć, tak jak w przypadku **GetCommandLine** funkcji z modułu Kernel32.dll, która zwraca wskaźnik do pamięci jądra. Aby uzyskać szczegółowe informacje dotyczące ręcznego zwalniania pamięci, zobacz [przykłady buforów](https://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Organizowanie domyślne dotyczące klas  
 Klasy mogą być organizowane wyłącznie przez współdziałania z modelem COM i zawsze są przekazywane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy jest nazywane interfejsu klasy. Aby dowiedzieć się, jak zastępowanie interfejsu klasy za pomocą ulubionego interfejsu, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Przekazywanie klas dla modelu COM  
 Gdy zarządzanej klasy jest przekazywany do modelu COM, organizator międzyoperacyjny automatycznie opakowuje klasy przy użyciu serwera proxy modelu COM i przekazuje interfejsu klasy generowane przez serwer proxy, aby wywołanie metody COM. Serwer proxy następnie deleguje wszystkie wywołania interfejsu klasy z powrotem do obiektu zarządzanego. Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowane przez klasy. Serwer proxy takich jak automatycznie implementuje interfejsy **IUnknown** i **IDispatch** imieniu klasy.  
  
### <a name="passing-classes-to-net-code"></a>Przekazywanie klas kodu platformy .NET  
 Klasy coclass nie są zwykle używane jako argumenty tej metody w modelu COM. Zamiast tego domyślnego interfejsu jest zwykle przekazywany zamiast wspólna.  
  
 Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyoperacyjny jest odpowiedzialny za zawijanie interfejsu z otoką właściwe i przekazanie otoki do zarządzanej metody. Określanie, które otoki, aby użyć może być trudne. Każde wystąpienie obiektu COM ma otokę pojedynczy, unikatowy niezależnie od tego, jak wiele interfejsów obiekt implementuje. Na przykład pojedynczy obiekt COM, który implementuje pięć różnych interfejsów ma tylko jedną otokę. Ten sam otoki udostępnia wszystkie pięć interfejsów. Jeśli dwa wystąpienia obiektu COM są tworzone, są tworzone dwa wystąpienia otoki.  
  
 Dla otoki zachować ten sam typ w okresie swojego istnienia Organizator międzyoperacyjny musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępnianych przez obiekt jest przekazywany za pomocą organizatora. Organizator identyfikuje obiekt, patrząc na jeden z interfejsów, który implementuje obiekt.  
  
 Na przykład Organizator Określa, że klasy otoki powinien być używany do opakowywania interfejsu, który został przekazany do kodu zarządzanego. Po interfejsie najpierw jest przekazywany za pomocą organizatora, organizator sprawdza, czy interfejs pochodzi z znany obiekt. To sprawdzanie jest wykonywane w dwóch sytuacjach:  
  
-   Interfejs jest jest implementowany przez inny obiekt zarządzany, który został przekazany do modelu COM, gdzie indziej. Organizator można łatwo zidentyfikować interfejsów udostępnianych przez zarządzane obiekty i jest możliwość dopasowania interfejs z zarządzanego obiektu, który dostarcza implementację. Zarządzany obiekt jest następnie przekazywany do metody i nie otoki jest wymagana.  
  
-   Obiekt, który jest już opakowana implementuje interfejs. Aby ustalić, czy jest to możliwe, organizator zapytania obiektu dla jego **IUnknown** interfejs i porównuje zwrócony interfejs służący do interfejsów inne obiekty, które są już opakowana. Jeśli interfejs jest taki sam jak inny otoki, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywany do metody.  
  
 Jeśli interfejs nie jest od znanych obiektu, organizator wykonuje następujące czynności:  
  
1.  Organizator wysyła zapytanie do obiektu **IProvideClassInfo2** interfejsu. Jeśli nie dostarczono, organizator używa CLSID zwróciło **IProvideClassInfo2.GetGUID** do identyfikowania coclass, zapewniając interfejs. O identyfikatorze CLSID Organizator można zlokalizować otoki z rejestru, jeśli zestaw został wcześniej zarejestrowany.  
  
2.  Organizator zapytania dla interfejsu **IProvideClassInfo** interfejsu. Jeśli nie dostarczono, organizator używa **ITypeInfo** zwróciło **IProvideClassInfo.GetClassinfo** ustalenie, identyfikator CLSID klasy uwidaczniania interfejsu. Organizator można użyć identyfikatora CLSID, do lokalizowania metadane dla otoki.  
  
3.  Jeśli organizator nadal nie można określić klasę, opakowuje interfejs za pomocą klasy otoki ogólnych o nazwie **.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Organizowanie domyślne dotyczące delegatów  
 Zarządzane delegata jest organizowana jako interfejsem COM lub wskaźnika funkcji jest oparte na mechanizmie wywołania:  
  
-   Dla platformy, należy wywołać, obiekt delegowany jest organizowana jako wskaźnik funkcji niezarządzanej domyślnie.  
  
-   Dla współdziałania z modelem COM, obiekt delegowany jest organizowana jako interfejsu COM typu **_Delegate** domyślnie. **_Delegate** interfejsu jest zdefiniowany w bibliotece typów Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metody, która umożliwia wywoływanie metody, która odwołuje się do obiektu delegowanego.  
  
 W poniższej tabeli przedstawiono organizowania opcji dla typu danych zarządzanych delegata. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> delegatów marshal wartości wyliczenia.  
  
|Typ wyliczeniowy|Opis formatu niezarządzanych|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Wskaźnik funkcji niezarządzanej.|  
|**UnmanagedType.Interface**|Interfejs typu **_Delegate**, zgodnie z definicją w Mscorlib.tlb.|  
  
 Należy wziąć pod uwagę poniższy przykład kodu, w której metody `DelegateTestInterface` są eksportowane do biblioteki typów COM. Należy zauważyć, że tylko deleguje oznaczone **ref** (lub **ByRef**) — słowo kluczowe są przekazywane jako we/wy parametrów.  
  
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
  
```  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 Wskaźnik funkcji może zostać wyłuskany tak samo, jak może zostać wyłuskany, drugi wskaźnik funkcji niezarządzanej.  

W tym przykładzie, jeśli dwa obiekty delegowane są przekazywane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, wynik jest `int` i wskaźnik `int`. Ponieważ typy delegatów są są organizowane, `int` w tym miejscu reprezentuje wskaźnik do void (`void*`), czyli adres delegata w pamięci. Innymi słowy, ten wynik zależy od 32-bitowych systemach Windows, ponieważ `int` w tym miejscu reprezentuje rozmiar wskaźnika funkcji.

> [!NOTE]
>  Odwołanie do wskaźnika funkcji do delegata zarządzanego kodu niezarządzanego w posiadaniu nie uniemożliwia środowiska uruchomieniowego języka wspólnego przeprowadzania wyrzucania elementów bezużytecznych obiektów zarządzanych.  
  
 Na przykład, poniższy kod jest nieprawidłowy ponieważ odwołanie do `cb` przekazanego do obiektu `SetChangeHandler` metody nie przechowuje `cb` podtrzymywania połączenia po przekroczeniu cyklu życia `Test` metody. Gdy `cb` obiektu są bezużyteczne, wskaźnik funkcji jest przekazywany do `SetChangeHandler` nie jest już prawidłowy.  
  
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
  
 Aby zrekompensować nieoczekiwany wyrzucania elementów bezużytecznych, obiekt wywołujący musi zapewnić, że `cb` obiektu jest życiu tak długo, jak funkcja niezarządzany wskaźnik jest w użyciu. Opcjonalnie może mieć kod niezarządzany, powiadom kodu zarządzanego, gdy wskaźnik funkcji nie jest już potrzebny, co ilustruje poniższy przykład.  
  
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
  
## <a name="default-marshaling-for-value-types"></a>Organizowanie domyślne dotyczące typów wartości  
 Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe są [danych kopiowalnych](blittable-and-non-blittable-types.md) i nie wymagają szeregowanie. Inne [niekopiowalnych](blittable-and-non-blittable-types.md) typy mają różne reprezentacje w pamięci zarządzanych i niezarządzanych i wymagają szeregowanie. Nadal innych typów wymaga jawnego formatowanie wewnątrz międzyoperacyjnej granicy.  
  
 Ten temat zawiera informacje poniżej, dla typów wartości sformatowane:  
  
-   [Typy wartości używane na platformie wywołania](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [Typy wartości używane w modelu COM](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 Oprócz zawierająca opis typów sformatowane, ten temat zawiera informacje o [System typów wartości](#cpcondefaultmarshalingforvaluetypesanchor1) , które mają nietypowe zachowanie organizowania.  
  
 Sformatowana typ to typ złożony, który zawiera informacje, które jawnie kontroluje układ składowych w pamięci. Informacje o układzie składowej jest realizowane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu. Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:  
  
-   **LayoutKind.Automatic**  
  
     Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatna zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności. Jednak gdy typ wartości jest przekazywany do kodu niezarządzanego, układ elementów członkowskich jest przewidywalne. Podjęto próbę automatycznie kierować takie struktury, powoduje wyjątek.  
  
-   **LayoutKind.Sequential**  
  
     Wskazuje, że elementy członkowskie tego typu mają być rozmieszczone w niezarządzanej pamięci w tej samej kolejności, w jakiej są wyświetlane w definicji typu zarządzanego.  
  
-   **LayoutKind.Explicit**  
  
     Wskazuje, czy członkowie są ułożone zgodnie z opisem w <xref:System.Runtime.InteropServices.FieldOffsetAttribute> dostarczony z każdym polem.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a>Typy wartości używane na platformie wywołania  
 W poniższym przykładzie `Point` i `Rect` typy zapewniają elementu członkowskiego informacji o układzie przy użyciu **structlayoutattribute —**.  
  
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
  
 Podczas przekazywania do kodu niezarządzanego, te typy sformatowane jest organizowana jako struktury stylu C. Zapewnia to prosty sposób wywoływania niezarządzanego interfejsu API, która przyjmuje argumenty struktury. Na przykład `POINT` i `RECT` struktury mogą być przekazywane do firmy Microsoft Win32 API **PtInRect** funkcji w następujący sposób:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Można przekazać struktury za pomocą platformy następujące wywołania definicji:  
  
```vb  
Class Win32API      
   Declare Auto Function PtInRect Lib "User32.dll" _  
    (ByRef r As Rect, p As Point) As Boolean  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("User32.dll")]  
   public static extern Bool PtInRect(ref Rect r, Point p);  
}  
```  
  
 `Rect` Typ wartości muszą być przekazywane przez odwołanie, ponieważ niezarządzany API oczekuje wskaźnika do `RECT` mają być przekazane do funkcji. `Point` Typ wartości jest przekazywany przez wartość, ponieważ oczekuje niezarządzany interfejs API `POINT` przekazywane na stosie. Bardzo ważne jest to niewielka różnica. Odwołania są przekazywane do kodu niezarządzanego jako wskaźniki. Wartości są przekazywane do kodu niezarządzanego na stosie.  
  
> [!NOTE]
>  Gdy typem sformatowane jest organizowana jako struktury, tylko pola w typie są dostępne. Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z niezarządzanego kodu.  
  
 Klasy może również być przekazywania do kodu niezarządzanego jako struktury stylu C pod warunkiem naprawili układ składowych. Informacje o układzie składowej klasy, również jest dostarczana z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu. Główna różnica między typami wartości przy użyciu stałej układ i klas o stałym układzie jest sposób, w którym są przekazywania do kodu niezarządzanego. Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszelkie zmiany wprowadzone do elementów członkowskich typu przez obiekt wywoływany nie są widoczne przez obiekt wywołujący. Typy odwołań są przekazywane przez odwołanie (odwołania do typu jest przekazywane na stosie). w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu przez obiekt wywoływany są widoczne przez obiekt wywołujący.  
  
> [!NOTE]
>  Jeśli typ odwołania ma składowe typów niekopiowalnych, wymagana jest konwersja dwa razy: podczas pierwszego, gdy argument jest przekazywany niezarządzanym, a drugi raz na powrót z wywołania. Ze względu na to dodatkowe obciążenie/Ściemnianie parametry muszą być jawnie stosowana do argumentu Jeśli obiekt wywołujący chce, aby zobaczyć zmiany wprowadzone przez obiekt wywoływany.  
  
 W poniższym przykładzie `SystemTime` klasa ma układ składowych sekwencyjne i mogą być przekazywane do interfejsu API Win32 **GetSystemTime** funkcji.  
  
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
  
 **GetSystemTime** funkcja jest zdefiniowana w następujący sposób:  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 Definicja wywołanie równoważnej platformy **GetSystemTime** jest następująca:  
  
```vb  
Public Class Win32  
   Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (ByVal sysTime _  
   As SystemTime)  
End Class  
```  
  
```csharp  
class Win32API {  
   [DllImport("Kernel32.dll", CharSet=CharSet.Auto)]  
   public static extern void GetSystemTime(SystemTime st);  
}  
```  
  
 Należy zauważyć, że `SystemTime` argument nie jest typu jako argument odwołania, ponieważ `SystemTime` jest klasą nie jest typem wartości. Inaczej niż w przypadku typów wartości klasy zawsze są przekazywane przez odwołanie.  
  
 Poniższy przykład kodu pokazuje inną `Point` klasy, która ma metodę o nazwie `SetXY`. Ponieważ typ ma sekwencyjne układ, można przekazany do kodu niezarządzanego i organizowane w strukturze. Jednak `SetXY` elementu członkowskiego nie jest wywoływane z niezarządzanego kodu, nawet jeśli obiekt jest przekazywany przez odwołanie.  
  
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
  
<a name="cpcondefaultmarshalingforvaluetypesanchor3"></a>   
### <a name="value-types-used-in-com-interop"></a>Typy wartości używane w modelu COM  
 Typy sformatowane również mogą być przekazywane do wywołania metody międzyoperacyjnego modelu COM. W rzeczywistości podczas eksportowania do biblioteki typów, typy wartości są automatycznie konwertowane do struktur. Jak pokazano na poniższym przykładzie, `Point` typ wartości staje się definicję typu (typedef) o nazwie `Point`. Wszystkie odwołania do `Point` typu wartości w innym miejscu w bibliotece typów są zastępowane `Point` typedef.  
  
 **Reprezentacja biblioteki typów**  
  
```  
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
  
 Te same zasady, które są używane do organizowania wartości i odwołań pozwalającą na platformie wywołania są używane w przypadku kierowania za pośrednictwem interfejsów COM. Na przykład, jeśli wystąpienie `Point` typ wartości jest przekazywany z programu .NET Framework modelowi COM, `Point` jest przekazywany przez wartość. Jeśli `Point` typ wartości jest przekazywany przez odwołanie, wskaźnik do `Point` jest przekazywane na stosie. Organizator międzyoperacyjny nie obsługuje wyższego poziomu pośredniego (**punktu** \* \*) w dowolnym kierunku.  
  
> [!NOTE]
>  Struktury o <xref:System.Runtime.InteropServices.LayoutKind> równa wartości wyliczenia **jawne** nie można używać w modelu COM, ponieważ wyeksportowanej biblioteki typów nie express jawnego układu.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>System typów wartości  
 <xref:System> Przestrzeń nazw ma kilka typów wartości, które reprezentują formy opakowanej typów pierwotnych w czasie wykonywania. Na przykład typ wartości <xref:System.Int32?displayProperty=nameWithType> struktury reprezentuje spakowany formie **ELEMENT_TYPE_I4**. Zamiast kierowania tych typów jako struktury, jak inne typy sformatowane, można kierować je w taki sam sposób, jak typy pierwotne, które one polu. **System.Int32** w związku z tym jest organizowana jako **ELEMENT_TYPE_I4** zamiast w strukturze zawierający pojedynczy element członkowski typu **długie**. Poniższa tabela zawiera listę typów wartości w **systemu** obszar nazw, który jest spakowany reprezentacje typów pierwotnych.  
  
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
  
 Wpisuje inną wartość **systemu** przestrzeni nazw są obsługiwane w inny sposób. Ponieważ kod niezarządzany już dobrze udokumentowana formatów dla tych typów, organizator ma specjalne reguły organizowanie ich. Poniższa tabela zawiera listę typów specjalna wartość **systemu** przestrzeni nazw, a także typu niezarządzanego, są one przekazywane do.  
  
|Typ wartości systemu|Typ pliku IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATA**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DECIMAL**|  
|<xref:System.Guid?displayProperty=nameWithType>|**IDENTYFIKATOR GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Poniższy kod przedstawia definicję typy niezarządzanwe **data**, **GUID**, **dziesiętna**, i **OLE_COLOR** w typie Stdole2 Biblioteka.  
  
#### <a name="type-library-representation"></a>Reprezentacja biblioteki typów  
  
```  
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
  
 Poniższy kod przedstawia odpowiadające im definicje w zarządzanej `IValueTypes` interfejsu.  
  
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
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)  
 [Kopiowanie i przypinanie](copying-and-pinning.md)  
 [Domyślny marshaling dla tablic](default-marshaling-for-arrays.md)  
 [Domyślny marshaling dla obiektów](default-marshaling-for-objects.md)  
 [Domyślny marshaling dla ciągów](default-marshaling-for-strings.md)
