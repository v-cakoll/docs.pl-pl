---
title: Domyślne zachowanie marshalingu
description: Poznaj domyślne zachowanie organizowania w programie .NET. Przejrzyj zarządzanie pamięcią za pomocą organizowania międzyoperacyjności i zobacz domyślne kierowanie dla klas, delegatów i typów wartości.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 0469874d016725eb6423bb8453e9657b2be923d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618574"
---
# <a name="default-marshaling-behavior"></a>Domyślne zachowanie marshalingu
Kierowanie międzyoperacyjności operuje na regułach, które określają sposób, w jaki dane skojarzone z parametrami metod działają w miarę przekazywania między pamięcią zarządzaną i niezarządzaną. Te wbudowane reguły kontrolują takie działania kierujące jako przekształcenia typu danych, niezależnie od tego, czy wywoływany może zmienić dane przekazywane do niego, i zwrócić te zmiany do obiektu wywołującego, i w jakich okolicznościach Organizator zapewnia optymalizację wydajności.  
  
 W tej sekcji opisano domyślne właściwości behawioralne usługi organizowania międzyoperacyjnego. Przedstawia szczegółowe informacje na temat organizowania tablic, typów logicznych, typów znaków, delegatów, klas, obiektów, ciągów i struktur.  
  
> [!NOTE]
> Kierowanie typów ogólnych nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Zarządzanie pamięcią za pomocą Organizatora międzyoperacyjnego  
 Organizator międzyoperacyjny zawsze próbuje zwolnić pamięć przydzieloną przez kod niezarządzany. To zachowanie jest zgodne z regułami zarządzania pamięcią COM, ale różni się od zasad, które regulują natywne C++.  
  
 Może wystąpić sytuacja, w której przewidywane jest zachowanie natywnego języka C++ (bez zwalniania pamięci) podczas korzystania z funkcji wywołania platformy, która automatycznie zwalnia pamięć dla wskaźników. Na przykład, wywołanie następującej niezarządzanej metody z biblioteki C++ DLL nie zwalnia automatycznie żadnej pamięci.  
  
### <a name="unmanaged-signature"></a>Niezarządzany podpis  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Jednakże w przypadku zdefiniowania metody jako prototypu wywołania platformy Zastąp każdy typ **BSTR** typem <xref:System.String> , a wywołanie `MethodOne` , środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy. Zachowanie organizowania można zmienić przy użyciu <xref:System.IntPtr> typów, a nie typów **ciągów** .  
  
 Środowisko uruchomieniowe zawsze używa metody **CoTaskMemFree** do zwolnienia pamięci. Jeśli pamięć, z którą pracujesz, nie została przypisana przy użyciu metody **CoTaskMemAlloc** , należy użyć elementu **IntPtr** i zwolnić pamięć ręcznie przy użyciu odpowiedniej metody. Podobnie można uniknąć automatycznej zwalniania pamięci w sytuacjach, w których pamięć nigdy nie powinna zostać zwolniona, na przykład przy użyciu funkcji **GetCommandLine** z Kernel32.dll, która zwraca wskaźnik do pamięci jądra. Aby uzyskać szczegółowe informacje na temat ręcznego zwalniania pamięci, zobacz [przykładowe bufory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).  
  
## <a name="default-marshaling-for-classes"></a>Kierowanie domyślne dla klas  
 Klasy mogą być organizowane tylko przez międzyoperacyjność modelu COM i są zawsze organizowane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy jest nazywany interfejsem klasy. Aby uzyskać informacje na temat przesłaniania interfejsu klasy z wybranym interfejsem, zobacz [wprowadzenie do interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).  
  
### <a name="passing-classes-to-com"></a>Przekazywanie klas do modelu COM  
 Gdy zarządzana Klasa jest przekazywana do modelu COM, organizator międzyoperacyjny automatycznie zawija klasę z serwerem proxy modelu COM i przekazuje interfejs klasy utworzony przez serwer proxy do wywołania metody COM. Następnie serwer proxy deleguje wszystkie wywołania w interfejsie klasy z powrotem do obiektu zarządzanego. Serwer proxy ujawnia również inne interfejsy, które nie są jawnie zaimplementowane przez klasę. Serwer proxy automatycznie implementuje interfejsy, takie jak **IUnknown** i **IDispatch** w imieniu klasy.  
  
### <a name="passing-classes-to-net-code"></a>Przekazywanie klas do kodu platformy .NET  
 Klasy coclass nie są zwykle używane jako argumenty metod w modelu COM. Zamiast tego, domyślnym interfejsem jest zwykle przekazanie zamiast klasy coclass.  
  
 Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyoperacyjny jest odpowiedzialny za pakowanie interfejsu z odpowiednią otoką i przekazanie otoki do metody zarządzanej. Określanie otoki, która ma być używana, może być trudne. Każde wystąpienie obiektu COM ma pojedynczą, unikatową otokę, niezależnie od liczby interfejsów implementujących obiekt. Na przykład pojedynczy obiekt COM, który implementuje pięć odrębnych interfejsów, ma tylko jedną otokę. Ta sama otoka uwidacznia wszystkie pięć interfejsów. Jeśli tworzone są dwa wystąpienia obiektu COM, tworzone są dwa wystąpienia otoki.  
  
 Aby otoka mogła obsługiwać ten sam typ w całym okresie istnienia, organizator międzyoperacyjny musi identyfikować poprawną otokę, gdy interfejs uwidoczniony przez obiekt jest przekazywany przez organizatora. Organizator identyfikuje obiekt, przeglądając jeden z interfejsów implementujących obiekt.  
  
 Na przykład Organizator określa, że otoka klasy ma być używana do zawijania interfejsu, który został przekazano do kodu zarządzanego. Gdy interfejs jest po raz pierwszy przekazywany przez organizatora, organizator sprawdza, czy interfejs pochodzi z znanego obiektu. To sprawdzenie odbywa się w dwóch sytuacjach:  
  
- Interfejs jest implementowany przez inny zarządzany obiekt, który został przekazano do modelu COM w innym miejscu. Organizator może łatwo identyfikować interfejsy udostępniane przez zarządzane obiekty i jest w stanie dopasować interfejs z zarządzanym obiektem, który udostępnia implementację. Obiekt zarządzany jest następnie przekazywać do metody, a otoka nie jest wymagana.  
  
- Obiekt, który został już opakowany, implementuje interfejs. Aby określić, czy tak jest, organizator wysyła zapytanie do obiektu w interfejsie **IUnknown** i porównuje zwracany interfejs do interfejsów innych obiektów, które zostały już opakowane. Jeśli interfejs jest taki sam jak w przypadku innych otok, obiekty mają taką samą tożsamość, a istniejąca otoka jest przenoszona do metody.  
  
 Jeśli interfejs nie pochodzi z znanego obiektu, organizator wykonuje następujące czynności:  
  
1. Organizator wysyła zapytanie do obiektu dla interfejsu **IProvideClassInfo2** . Jeśli jest podany, organizator używa identyfikatora CLSID zwróconego z **IProvideClassInfo2. GetGuid** do identyfikowania klasy coclass dostarczającej interfejs. Przy użyciu identyfikatora CLSID Organizator może zlokalizować otokę z rejestru, jeśli zestaw został wcześniej zarejestrowany.  
  
2. Organizator wysyła zapytanie do interfejsu dla interfejsu **IProvideClassInfo** . Jeśli jest podany, organizator używa **Metoda ITypeInfo** zwrócone z **IProvideClassInfo. GetClassInfo** , aby określić identyfikator CLSID klasy, która uwidacznia interfejs. Organizator może użyć identyfikatora CLSID, aby zlokalizować metadane dla otoki.  
  
3. Jeśli organizator nadal nie może zidentyfikować klasy, zawija interfejs z klasą otoki ogólnej o nazwie **System. __ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Kierowanie domyślne dla delegatów  
 Zarządzany delegat jest zorganizowany jako interfejs COM lub jako wskaźnik funkcji, na podstawie mechanizmu wywołującego:  
  
- W przypadku wywołania platformy delegat jest domyślnie zorganizowany jako niezarządzany wskaźnik funkcji.  
  
- W przypadku międzyoperacyjności modelu COM delegat jest domyślnie zorganizowany jako interfejs COM typu **_Delegate** . Interfejs **_Delegate** jest zdefiniowany w bibliotece typów mscorlib. tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodę, która umożliwia wywołanie metody, która odwołuje się do obiektu delegowanego.  
  
 W poniższej tabeli przedstawiono opcje kierowania dla zarządzanego typu danych delegata. Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania delegatów.  
  
|Typ wyliczenia|Opis niezarządzanego formatu|  
|----------------------|-------------------------------------|  
|**UnmanagedType. elementem FunctionPtr**|Wskaźnik funkcji niezarządzanej.|  
|**UnmanagedType. Interface**|Interfejs typu **_Delegate**, zgodnie z definicją w pliku mscorlib. tlb.|  
  
 Rozważmy następujący przykładowy kod, w którym metody `DelegateTestInterface` są eksportowane do biblioteki typów com. Należy zauważyć, że tylko delegatów oznaczonych za pomocą słowa kluczowego **ref** (lub **ByRef**) są przesyłane jako parametry wejściowe/out.  
  
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
  
 Wskaźnik funkcji może zostać wywoływany, tak jak każdy inny niezarządzany wskaźnik funkcji może zostać odwołujący się.  

W tym przykładzie, gdy dwa Delegaty są organizowane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> , wynik jest `int` i wskaźnikiem do `int` . Ponieważ typy delegatów są organizowane, `int` w tym miejscu reprezentuje wskaźnik do typu void ( `void*` ), który jest adresem delegata w pamięci. Innymi słowy, ten wynik jest specyficzny dla 32-bitowych systemów Windows, ponieważ w `int` tym miejscu reprezentuje rozmiar wskaźnika funkcji.

> [!NOTE]
> Odwołanie do wskaźnika funkcji do zarządzanego delegata przechowywanego przez kod niezarządzany nie zapobiega występowaniu elementów bezużytecznych w zarządzanym obiekcie przez środowisko uruchomieniowe języka wspólnego.  
  
 Na przykład następujący kod jest niepoprawny, ponieważ odwołanie do `cb` obiektu, do `SetChangeHandler` metody, nie utrzymuje `cb` aktywności poza cyklem życia `Test` metody. Gdy `cb` obiekt zostanie odrzucony, wskaźnik funkcji przeszedł do `SetChangeHandler` nie jest już prawidłowy.  
  
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
  
 Aby skompensować nieoczekiwane wyrzucanie elementów bezużytecznych, obiekt wywołujący musi upewnić się, że jest on aktywny, o ile `cb` niezarządzany wskaźnik funkcji jest używany. Opcjonalnie kod niezarządzany powiadamia kod zarządzany, gdy wskaźnik funkcji nie jest już wymagany, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="default-marshaling-for-value-types"></a>Kierowanie domyślne dla typów wartości  
 Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe, są [danych kopiowalnych](blittable-and-non-blittable-types.md) i nie wymaga organizowania. Inne typy inne [niż danych kopiowalnych](blittable-and-non-blittable-types.md) mają podobne reprezentacje w pamięci zarządzanej i niezarządzanej oraz wymagają organizowania. Nadal inne typy wymagają jawnego formatowania w granicach międzyoperacyjnych.  
  
 Ta sekcja zawiera informacje o następujących sformatowanych typach wartości:  
  
- [Typy wartości używane w wywołaniu platformy](#value-types-used-in-platform-invoke)  
  
- [Typy wartości używane w międzyoperacyjności modelu COM](#value-types-used-in-com-interop)  
  
 Oprócz opisywania sformatowanych typów, ten temat identyfikuje [typy wartości systemowych](#system-value-types) , które mają nietypowe zachowanie podczas organizowania.  
  
 Sformatowany typ to typ złożony, który zawiera informacje, które jawnie kontrolują układ elementów członkowskich w pamięci. Informacje o układzie elementu członkowskiego są udostępniane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu. Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:  
  
- **LayoutKind.**  
  
     Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatne, aby zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności. Jednak gdy typ wartości jest przenoszona do kodu niezarządzanego, układ elementów członkowskich jest przewidywalny. Próba zorganizowania takiej struktury automatycznie powoduje wyjątek.  
  
- **LayoutKind. sekwencyjny**  
  
     Wskazuje, że elementy członkowskie typu muszą zostać ustanowione w pamięci niezarządzanej w takiej samej kolejności, w jakiej występują w definicji typu zarządzanego.  
  
- **LayoutKind. Explicit**  
  
     Wskazuje, że elementy członkowskie są określane zgodnie z <xref:System.Runtime.InteropServices.FieldOffsetAttribute> podanymi dla każdego pola.  
  
### <a name="value-types-used-in-platform-invoke"></a>Typy wartości używane w wywołaniu platformy  
 W poniższym przykładzie `Point` `Rect` typy i zapewniają informacje o układzie elementu członkowskiego przy użyciu **StructLayoutAttribute**.  
  
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
  
 W przypadku kierowania do niezarządzanego kodu te sformatowane typy są organizowane jako struktury w stylu C. Zapewnia to prosty sposób wywoływania niezarządzanego interfejsu API, który ma argumenty struktury. Na przykład `POINT` `RECT` struktury i mogą być przesyłane do funkcji **PtInRect** interfejsu API systemu Microsoft Windows w następujący sposób:  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Można przekazać struktury przy użyciu następującej definicji wywołania platformy:  
  
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
  
 `Rect`Typ wartości musi być przesyłany przez odwołanie, ponieważ niezarządzany interfejs API oczekuje na `RECT` przekazanie wskaźnika do funkcji. `Point`Typ wartości jest przenoszona przez wartość, ponieważ niezarządzany interfejs API oczekuje na `POINT` przekazanie na stosie. Ta delikatna różnica jest bardzo ważna. Odwołania są przesyłane do niezarządzanego kodu jako wskaźniki. Wartości są przesyłane do kodu niezarządzanego na stosie.  
  
> [!NOTE]
> Gdy sformatowany typ jest zorganizowany jako struktura, dostępne są tylko pola należące do tego typu. Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z kodu niezarządzanego.  
  
 Klasy mogą być również organizowane w kodzie niezarządzanym jako struktury w stylu C, pod warunkiem, że mają stały układ elementu członkowskiego. Informacje o układzie elementu członkowskiego klasy są również udostępniane z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutem. Główna różnica między typami wartości ze stałym układem i klasami ze stałym układem jest sposobem, w jaki są one organizowane do kodu niezarządzanego. Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu przez wywoływany nie są widoczne dla obiektu wywołującego. Typy odwołań są przesyłane przez odwołanie (odwołanie do typu jest przesyłane na stosie); w związku z tym, wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu przez wywoływany przez obiekt wywołujący są widoczne dla obiektu dzwoniącego.  
  
> [!NOTE]
> Jeśli typ referencyjny składa się z typów innych niż danych kopiowalnych, konwersja jest wymagana dwukrotnie: pierwszy raz, gdy argument jest przenoszona do niezarządzanej strony, a drugi czas powrotu z wywołania. W związku z tym dodatkowymi kosztami parametry wejściowe/out muszą być jawnie stosowane do argumentu, jeśli obiekt wywołujący chce zobaczyć zmiany wprowadzone przez wywoływany element.  
  
 W poniższym przykładzie `SystemTime` Klasa ma sekwencyjny układ elementów członkowskich i może być przenoszona do funkcji **GetSystemTime** interfejsu API systemu Windows.  
  
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
  
 Odpowiednik definicji wywołania platformy dla **GetSystemTime** jest następujący:  
  
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
  
 Zwróć uwagę, że `SystemTime` argument nie jest wpisywany jako argument odwołania `SystemTime` , ponieważ jest klasą, a nie typem wartości. W przeciwieństwie do typów wartości, klasy są zawsze przesyłane przez odwołanie.  
  
 Poniższy przykład kodu przedstawia inną `Point` klasę, która ma metodę o nazwie `SetXY` . Ponieważ typ ma sekwencyjny układ, może być przekazywany do kodu niezarządzanego i zorganizowany jako struktura. Jednak `SetXY` element członkowski nie jest wywoływany z kodu niezarządzanego, nawet jeśli obiekt jest przesyłany przez odwołanie.  
  
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
  
### <a name="value-types-used-in-com-interop"></a>Typy wartości używane w międzyoperacyjności modelu COM  
 Sformatowane typy mogą być również przesyłane do wywołań metod międzyoperacyjnych modelu COM. W rzeczywistości, gdy eksportowane do biblioteki typów, typy wartości są automatycznie konwertowane na struktury. Jak pokazano na poniższym przykładzie, `Point` Typ wartości jest definicją typu (TypeDef) o nazwie `Point` . Wszystkie odwołania do `Point` typu wartości w innym miejscu w bibliotece typów są zastępowane `Point` typedef.  
  
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
  
 Te same reguły służące do organizowania wartości i odwołań do wywołań wywołania platformy są używane podczas organizowania interfejsów COM. Na przykład, gdy wystąpienie `Point` typu wartości jest przesyłane z .NET Framework do modelu COM, `Point` wartość jest przenoszona przez wartości. Jeśli `Point` Typ wartości jest przesyłany przez odwołanie, wskaźnik do elementu `Point` jest przesyłany na stosie. Organizator międzyoperacyjny nie obsługuje wyższych poziomów pośrednich (**punkt** \* \* ) w dowolnym kierunku.  
  
> [!NOTE]
> Struktury z <xref:System.Runtime.InteropServices.LayoutKind> wartością wyliczenia ustawioną na wartość **Explicit** nie mogą być używane w międzyoperacyjności modelu COM, ponieważ eksportowana biblioteka typów nie może wyrazić jawnego układu.  
  
### <a name="system-value-types"></a>Typy wartości systemu  
 <xref:System>Przestrzeń nazw ma kilka typów wartości, które reprezentują postać opakowaną typów pierwotnych środowiska uruchomieniowego. Na przykład struktura typu wartości <xref:System.Int32?displayProperty=nameWithType> reprezentuje opakowaną postać **ELEMENT_TYPE_I4**. Zamiast organizować te typy jako struktury, tak jak inne sformatowane typy, są organizowane w taki sam sposób, jak w przypadku typów pierwotnych. W związku z tym obiekt **System. Int32** jest zorganizowany jako **ELEMENT_TYPE_I4** zamiast struktury zawierającej pojedynczy element członkowski typu **Long**. Poniższa tabela zawiera listę typów wartości w przestrzeni nazw **systemu** , które są opakowane na typy pierwotne.  
  
|Typ wartości systemowej|Typ elementu|  
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
  
 Niektóre inne typy wartości w przestrzeni nazw **system** są obsługiwane inaczej. Ponieważ kod niezarządzany ma już dobrze ustalone formaty dla tych typów, Organizator ma specjalne reguły do organizowania. W poniższej tabeli wymieniono specjalne typy wartości w przestrzeni nazw **systemu** , a także niezarządzany typ, do którego są organizowane.  
  
|Typ wartości systemowej|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DNIU**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DOKŁADNOŚCI**|  
|<xref:System.Guid?displayProperty=nameWithType>|**IDENT**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Poniższy kod przedstawia definicję niezarządzanych typów **Date**, **GUID**, **Decimal**i **OLE_COLOR** w bibliotece typów Stdole2.  
  
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
  
 Poniższy kod przedstawia odpowiednie definicje w zarządzanym `IValueTypes` interfejsie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Typy kopiowalne i niekopiowalne](blittable-and-non-blittable-types.md)
- [Kopiowanie i przypinanie](copying-and-pinning.md)
- [Organizowanie domyślne dotyczące tablic](default-marshaling-for-arrays.md)
- [Domyślny marshaling dla obiektów](default-marshaling-for-objects.md)
- [Organizowanie domyślne dotyczące ciągów](default-marshaling-for-strings.md)
