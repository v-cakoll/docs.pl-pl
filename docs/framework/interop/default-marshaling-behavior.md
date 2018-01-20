---
title: "Domyślne zachowanie marshalingu"
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
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e66caf800fd49b4822ee22326b8a5cf712d99bb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="default-marshaling-behavior"></a>Domyślne zachowanie marshalingu
Przekazywanie międzyoperacyjne działa w regułach tego dyktować zachowania danych skojarzonych z parametrami metody przesyłanych między zarządzanymi i niezarządzanymi pamięci. Te wbudowane reguły kontrolowania takich kierowania działań jako przekształcenia typu danych, czy wywoływany można zmienić przekazywania danych i zwracany do obiektu wywołującego te zmiany i w której okolicznościach organizatora zapewnia optymalizacji wydajności.  
  
 W tej sekcji wymieniono domyślnych parametrów behawioralnej interop organizowanie usługi. Stanowi szczegółowe informacje na temat przekazywanie tablic, typów logicznych typu char, delegatów, klas, obiektów, ciągi i struktury.  
  
> [!NOTE]
>  Organizowanie typów ogólnych nie jest obsługiwane. Aby uzyskać więcej informacji, zobacz [współpracy przy użyciu typów ogólnych](http://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58).  
  
## <a name="memory-management-with-the-interop-marshaler"></a>Zarządzanie pamięcią z organizatora międzyoperacyjne  
 Organizator międzyoperacyjnego zawsze próbuje zwolnić pamięci przydzielonej przez kod niezarządzany. To zachowanie jest zgodne z zasadami zarządzania pamięci COM, ale różni się od zasad rządzących natywnych języka C++.  
  
 Pomyłek mogą wystąpić, jeśli przewidujesz natywnego zachowania C++ (nie pamięci zwalnianie) gdy przy użyciu platformy wywołania, które automatycznie zwalnia pamięć dla wskaźników. Na przykład wywołanie następującej metody niezarządzane z biblioteki DLL języka C++ nie automatycznie zwolnienia wszystkie pamięci.  
  
### <a name="unmanaged-signature"></a>Niezarządzanego podpisu  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 Jednak w przypadku definiowania metodę jako prototyp wywołanie platformy, Zastąp każdego **BSTR** to typ <xref:System.String> wpisz i Wywołaj `MethodOne`, środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy. Zachowanie marshalingu można zmienić za pomocą <xref:System.IntPtr> typy zamiast **ciąg** typów.  
  
 Środowisko uruchomieniowe zawsze używa **CoTaskMemFree** metodę, aby zwolnić pamięć. Jeśli pracujesz z pamięci nie została przydzielona z **CoTaskMemAlloc** metody, należy użyć **IntPtr** i zwolnić pamięć, ręcznie przy użyciu odpowiedniej metody. Podobnie można uniknąć automatycznego pamięci zwalnianie w sytuacjach, gdy pamięć nigdy nie powinien zwolniona, takie jak w przypadku **GetCommandLine** funkcji Kernel32.dll, która zwraca wskaźnik do pamięci jądra. Aby uzyskać więcej informacji o zwalnianiu ręcznie pamięci, zobacz [próbki buforów](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5).  
  
## <a name="default-marshaling-for-classes"></a>Organizowanie domyślne dotyczące klas  
 Klasy mogą być organizowany tylko przy użyciu współdziałanie z COM i zawsze są przekazywane jako interfejsy. W niektórych przypadkach interfejs używany do organizowania klasy nosi nazwę interfejsu klasy. Aby dowiedzieć się, jak zastępowanie interfejsu klasy przy użyciu interfejsu wybranych przez użytkownika, zobacz [wprowadzenie interfejsu klasy](http://msdn.microsoft.com/library/733c0dd2-12e5-46e6-8de1-39d5b25df024).  
  
### <a name="passing-classes-to-com"></a>Przekazywanie klas modelowi COM  
 Po klasie zarządzanej jest przekazywana do modelu COM, międzyoperacyjnego organizatora automatycznie zawijany klasy z serwera proxy modelu COM i przekazuje interfejsu klasy utworzonej przez serwer proxy do wywołania metody COM. Serwer proxy następnie deleguje wszystkie wywołania interfejsu klasy do obiektu zarządzanego. Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowana przez klasę. Serwer proxy takich jak automatycznie implementuje interfejsy **IUnknown** i **IDispatch** imieniu klasy.  
  
### <a name="passing-classes-to-net-code"></a>Przekazywanie klas kodu platformy .NET  
 Klasy coclass nie są zwykle używane jako argumenty metody w modelu COM. Zamiast tego domyślnego interfejsu jest zwykle przekazywany zamiast klasy coclass.  
  
 Jeśli interfejs zostanie przekazany do kodu zarządzanego, międzyoperacyjnego organizatora jest odpowiedzialny za zawijanie interfejsu z właściwego otoki i przekazywanie otoka zarządzanych metody. Określanie, które otoki do użycia, może być trudne. Każde wystąpienie obiektu COM ma otoki jedną, unikatową, niezależnie od tego, jak wiele interfejsów, które implementuje obiektu. Na przykład pojedynczy obiekt COM, który implementuje pięciu różnych interfejsów ma tylko jedną otoki. Tym samym otoki przedstawia wszystkie interfejsy pięć. Jeśli są tworzone dwa wystąpienia obiektu COM, są tworzone dwa wystąpienia otoki.  
  
 Dla otoki do obsługi tego samego typu w całym cyklu eksploatacji międzyoperacyjnego organizatora musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępniany przez obiekt jest przekazywana organizatora. Organizator określa obiekt, analizując jednego z interfejsów, które implementuje obiektu.  
  
 Na przykład organizatora Określa, że klasy otoki powinien być używany do opakowywania interfejs, który został przekazany do kodu zarządzanego. Po interfejsie najpierw są przekazywane za pośrednictwem organizatora, organizatora sprawdza, czy interfejs pochodzi ze znanego obiektu. To sprawdzanie jest wykonywane w dwóch sytuacjach:  
  
-   Interfejs jest implementowana przez inny obiekt zarządzany, który został przekazany do modelu COM w innym miejscu. Organizator można łatwo zidentyfikować interfejsach udostępnionych przez zarządzanych obiektów i może być zgodna z zarządzanego obiektu, który udostępnia implementację interfejsu. Zarządzanego obiektu są następnie przekazywane do metody i nie jest wymagane nie otoki.  
  
-   Obiekt, który jest już opakowana implementuje interfejs. Aby ustalić, czy jest to możliwe, organizator odpytuje obiekt dla jego **IUnknown** interfejsu i porównuje zwrócony interfejs do interfejsów inne obiekty, które są już opakowana. Jeśli interfejs jest taki sam jak inny otoki, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywany do metody.  
  
 Jeśli interfejs nie pochodzi z obiektu znane, organizator wykonuje następujące czynności:  
  
1.  Organizator wysyła zapytanie do obiektu **IProvideClassInfo2** interfejsu. Jeśli zostanie podana, organizator używa identyfikatora CLSID zwrócony z **IProvideClassInfo2.GetGUID** do identyfikowania coclass udostępnia interfejs. O identyfikatorze CLSID Organizator mogą znaleźć otoki z rejestru, jeśli zestaw został wcześniej zarejestrowany.  
  
2.  Organizator zapytania dla interfejsu **IProvideClassInfo** interfejsu. Jeśli zostanie podana, używa organizatora **ITypeInfo** zwrócony z **IProvideClassInfo.GetClassinfo** ustalenie CLSID udostępnianie interfejsu klasy. Organizator można użyć identyfikatora CLSID można znaleźć metadanych dla otoki.  
  
3.  Jeśli organizator nadal nie można zidentyfikować klasę, opakowuje interfejsu z klasy otoki ogólnego o nazwie **System.__ComObject**.  
  
## <a name="default-marshaling-for-delegates"></a>Organizowanie domyślne dotyczące obiektów delegowanych  
 Delegat zarządzanych jest przekazywane jako interfejsu COM lub wskaźnik funkcji, oparte na mechanizmie wywołania:  
  
-   Dla platformy invoke, delegat jest przekazywane jako wskaźnik funkcji niezarządzanej domyślnie.  
  
-   Dla międzyoperacyjności z modelem COM, delegat jest przekazywane jako interfejs COM typu **_Delegate** domyślnie. **_Delegate** interfejsu jest zdefiniowany w bibliotece typów Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metody, dzięki czemu można wywołać metodę, która odwołuje się do obiektu delegowanego.  
  
 W poniższej tabeli przedstawiono opcje organizowania dla typu danych zarządzanych delegata. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie delegatów.  
  
|Typ wyliczenia|Opis formatu niezarządzane|  
|----------------------|-------------------------------------|  
|**UnmanagedType.FunctionPtr**|Wskaźnik funkcji niezarządzanej.|  
|**UnmanagedType.Interface**|Interfejs typu **_Delegate**, zgodnie z definicją w Mscorlib.tlb.|  
  
 Należy wziąć pod uwagę Poniższy przykładowy kod, w którym metody `DelegateTestInterface` zostaną wyeksportowane do biblioteki typów COM. Należy zauważyć, że tylko deleguje oznaczonych **ref** (lub **ByRef**) — słowo kluczowe są przekazywane jako we/wy parametrów.  
  
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
  
### <a name="type-library-representation"></a>Reprezentacja typu biblioteki  
  
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
  
 Wskaźnik funkcji jest wyłuskiwany, tak samo, jak można usunąć odwołania innych wskaźnika funkcji niezarządzanej.  
  
> [!NOTE]
>  Odwołanie do wskaźnika funkcji do delegata zarządzanych przez kod niezarządzany nie zapobiega środowisko uruchomieniowe języka wspólnego wykonywania wyrzucanie elementów bezużytecznych do zarządzanego obiektu.  
  
 Na przykład następujący kod jest nieprawidłowy ponieważ odwołanie do `cb` obiekt przekazany do `SetChangeHandler` metody, nie przechowuje `cb` aktywności poza czas życia `Test` metody. Raz `cb` obiekt jest bezużytecznych, wskaźnik funkcji przekazany do `SetChangeHandler` nie jest już prawidłowy.  
  
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
  
 Kompensacji nieoczekiwany wyrzucanie elementów bezużytecznych, wywołujący musi zapewnić, że `cb` obiektu jest aktywne tak długo, jak funkcja niezarządzany wskaźnik jest w użyciu. Opcjonalnie może mieć kodu niezarządzanego, powiadom kodu zarządzanego, gdy wskaźnik funkcji nie jest już potrzebne, jak przedstawiono na poniższym przykładzie.  
  
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
  
## <a name="default-marshaling-for-value-types"></a>Domyślny marshaling dla typów wartości  
 Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe są [kopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md) i nie wymagają przekazywanie. Inne [niekopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md) typy niepodobnych reprezentacje w pamięci zarządzane i niezarządzane, wymagane jest przekazywanie. Nadal innych typów wymaga jawnego formatowania granicy współdziałanie.  
  
 Ten temat zawiera informacje wykonaj w typach wartości sformatowane:  
  
-   [Typy wartości używane na platformie wywołania](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [Typy wartości używane w modelu COM Interop](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 Oprócz opisujące sformatowany typów, w tym temacie identyfikuje [System typów wartości](#cpcondefaultmarshalingforvaluetypesanchor1) zawierających nietypowe zachowanie marshalingu.  
  
 Sformatowany typem jest typ złożony, który zawiera informacje, które jawnie określa układ jej elementów członkowskich w pamięci. Informacje o układzie elementu członkowskiego jest realizowane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu. Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:  
  
-   **LayoutKind.Automatic**  
  
     Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatne zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności. Jednak gdy typem wartości są przekazywane do kodu niezarządzanego, układ elementów członkowskich jest atrybutem wartości prognozowanych. Próba zorganizowania taka struktura automatycznie powoduje zgłoszenie wyjątku.  
  
-   **LayoutKind.Sequential**  
  
     Wskazuje, że mają zostać uwzględnione w pamięci niezarządzanej w tej samej kolejności, w jakiej występują w definicji typu zarządzanego elementy członkowskie tego typu.  
  
-   **LayoutKind.Explicit**  
  
     Określa układ elementów członkowskich według <xref:System.Runtime.InteropServices.FieldOffsetAttribute> dostarczony wraz z każdego pola.  
  
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
  
 Podczas przekazywane do kodu niezarządzanego, te typy sformatowany są przekazywane jako struktury w stylu języka C. To zapewnia prosty sposób wywoływania niezarządzanego API, która przyjmuje argumenty struktury. Na przykład `POINT` i `RECT` struktury mogą zostać przekazane do interfejsu API Win32 Microsoft **PtInRect** działają w następujący sposób:  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 Można przekazać struktur za pomocą następujących platform wywołania definicji:  
  
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
  
 `Rect` Typ wartości muszą być przekazywane przez odwołanie, ponieważ oczekiwana jest wskaźnik do niezarządzanego API `RECT` mają być przekazane do funkcji. `Point` Typ wartości jest przekazywany przez wartość, ponieważ oczekuje niezarządzanego API `POINT` do przekazania na stosie. Ta różnica jest bardzo ważne. Odwołania są przekazywane do kodu niezarządzanego jako wskaźników. Wartości są przekazywane do kodu niezarządzanego na stosie.  
  
> [!NOTE]
>  Gdy typem sformatowany jest przekazywane jako struktura, tylko pola w ramach typu są dostępne. Jeśli typ ma metody, właściwości lub zdarzeń, są niedostępne z kodem niezarządzanym.  
  
 Klasy można również być przekazywane do kodu niezarządzanego jako struktur w stylu języka C, pod warunkiem rozwiązaniu układu elementu członkowskiego. Dostępne są również informacje o układzie elementu członkowskiego klasy z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu. Główną różnicą między typami wartości o stałej układ i klasy z układem stałej jest sposób, w którym są przekazywane do kodu niezarządzanego. Typy wartości są przekazywane przez wartość (stos) i w związku z tym zmiany wprowadzone przez funkcję wywołującą elementy członkowskie tego typu nie są widoczne dla obiekt wywołujący. Typy odwołań są przekazywane przez odwołanie (odwołanie do typu jest przekazywany na stosie). w rezultacie wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu wywoływany są widoczne przez obiekt wywołujący.  
  
> [!NOTE]
>  Jeśli typ referencyjny ma elementów członkowskich typu niekopiowalne, konwersja nie jest wymagana dwa razy: raz pierwszy, gdy argument jest przekazywany stronie niezarządzane, a drugi raz na powrót z wywołania. Ze względu na to obciążenie dodane lub Brak parametrów musi jawnie odnosić się do argumentu, jeśli element wywołujący chce wyświetlać zmiany wprowadzone przez funkcję wywołującą.  
  
 W poniższym przykładzie `SystemTime` klasa ma układ sekwencyjny elementu członkowskiego i mogą zostać przekazane do interfejsu API Win32 **GetSystemTime** funkcji.  
  
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
  
 Platforma równoważne wywołanie definicji **GetSystemTime** wygląda następująco:  
  
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
  
 Zwróć uwagę, że `SystemTime` argument nie jest typu jako argument odwołania, ponieważ `SystemTime` jest klasa, nie jest typem wartości. W przeciwieństwie do typów wartości klasy zawsze są przekazywane przez odwołanie.  
  
 Poniższy przykład kodu pokazuje innej `Point` klasy, która ma metodę o nazwie `SetXY`. Ponieważ typ ma układ sekwencyjny, można przekazany do kodu niezarządzanego i organizowane w strukturze. Jednak `SetXY` element członkowski nie jest można wywołać za pomocą kodu niezarządzanego, nawet jeśli obiekt jest przekazywana przez odwołanie.  
  
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
### <a name="value-types-used-in-com-interop"></a>Typy wartości używane w modelu COM Interop  
 Typy sformatowany również mogą być przekazywane do wywołania metody międzyoperacyjnego COM. W rzeczywistości podczas eksportowania do biblioteki typów, typów wartości są automatycznie konwertowane na struktury. Jak pokazano na poniższym przykładzie, `Point` typ wartości staje się definicja typu (typedef) o nazwie `Point`. Wszystkie odwołania do `Point` są zamieniane na typ wartości w innym miejscu w bibliotece typów `Point` typedef.  
  
 **Reprezentacja typu biblioteki**  
  
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
  
 Te same zasady używany do organizowania wartości i odwołań pozwalającą na platformie wywołania wywołania są używane podczas organizowania za pośrednictwem interfejsów COM. Na przykład, gdy wystąpienie klasy `Point` typ wartości jest przekazywany z programu .NET Framework modelowi COM, `Point` jest przekazywany przez wartość. Jeśli `Point` typ wartości jest przekazywana przez odwołanie, wskaźnik do `Point` jest przekazywany na stosie. Organizator międzyoperacyjne nie obsługuje wyższego poziomu pośredni (**punktu \* \*** ) w żadnym kierunku.  
  
> [!NOTE]
>  Struktury o <xref:System.Runtime.InteropServices.LayoutKind> ustawioną wartość wyliczenia **Explicit** nie można używać w modelu COM interop, ponieważ wyeksportowanej biblioteki typów nie express jawny układ.  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a>System typów wartości  
 <xref:System> Przestrzeń nazw ma kilka typów wartości, które reprezentują formy opakowanej typu pierwotnego środowiska wykonawczego. Na przykład typ wartości <xref:System.Int32?displayProperty=nameWithType> struktury reprezentuje formy opakowanej z **ELEMENT_TYPE_I4**. Zamiast przekazywanie tych typów jako struktury, są inne typy sformatowane, należy kierować je w taki sam sposób jak typy pierwotne, które one polu. **System.Int32** w związku z tym jest przekazywane jako **ELEMENT_TYPE_I4** zamiast struktury zawierający pojedynczy element członkowski typu **długi**. Poniższa tabela zawiera listę typów wartości w **systemu** przestrzeni nazw, która to opakowanego reprezentacje typów pierwotnych.  
  
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
  
 Wartość typów w **systemu** przestrzeni nazw są obsługiwane w inny sposób. Organizator, ponieważ kodu niezarządzanego już ustalonym formaty dla tych typów, ma specjalne zasady przekazywanie ich. W poniższej tabeli przedstawiono typy specjalna wartość w **systemu** przestrzeni nazw, a także typ niezarządzany, są one przekazywane do.  
  
|Typ wartości systemu|Typ IDL|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|**DATA**|  
|<xref:System.Decimal?displayProperty=nameWithType>|**DECIMAL**|  
|<xref:System.Guid?displayProperty=nameWithType>|**IDENTYFIKATOR GUID**|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|**OLE_COLOR**|  
  
 Poniższy kod przedstawia definicję typu niezarządzanego **data**, **GUID**, **DZIESIĘTNĄ**, i **OLE_COLOR** w typie Stdole2 Biblioteka.  
  
#### <a name="type-library-representation"></a>Reprezentacja typu biblioteki  
  
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
  
#### <a name="type-library-representation"></a>Reprezentacja typu biblioteki  
  
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
 [Typy kopiowalne i niekopiowalne](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [Kopiowanie i przypinanie](../../../docs/framework/interop/copying-and-pinning.md)  
 [Domyślny marshaling dla tablic](../../../docs/framework/interop/default-marshaling-for-arrays.md)  
 [Domyślny marshaling dla obiektów](../../../docs/framework/interop/default-marshaling-for-objects.md)  
 [Domyślny marshaling dla ciągów](../../../docs/framework/interop/default-marshaling-for-strings.md)
