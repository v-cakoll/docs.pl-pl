---
title: Wywoływana otoka COM
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CCW
- COM interop, COM wrappers
- COM wrappers
- callable wrappers
- interoperation with unmanaged code, COM wrappers
- COM callable wrappers
ms.assetid: d04be3b5-27b9-4f5b-8469-a44149fabf78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21f7b0d56a788b4161fb7e99899b4dd15a434152
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394969"
---
# <a name="com-callable-wrapper"></a>Wywoływana otoka COM
Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu. Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.  
  
 Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług. Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew. Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci. Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.  
  
 ![Wywoływana otoka COM](./media/ccw.gif "w lewo")  
Uzyskiwanie dostępu do obiektów środowiska .NET przez otokę wywoływaną z modelu COM  
  
 Otoki wywoływane z modelu COM są niewidoczne dla innych klas uruchomionych w środowisku .NET Framework. Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.  
  
## <a name="object-identity"></a>Tożsamość obiektu  
 Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami. Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.  
  
## <a name="object-lifetime"></a>Okres istnienia obiektu  
 W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM. Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu. Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.  
  
## <a name="simulating-com-interfaces"></a>Symuluje interfejsy modelu COM

CCW przedstawia wszystkie publiczne, interfejsach widocznych dla modelu COM, typy danych i wartości zwracanych do klientów modelu COM w sposób zgodny z modelu COM wymuszania interakcji z interfejsu. Klient modelu COM wywoływanie metod dla obiektu .NET Framework jest taki sam jak wywoływanie metod obiektów COM.  
  
 Aby utworzyć takie podejście bezproblemowe, CCW wytwarza tradycyjnych interfejsy modelu COM, takie jak **IUnknown** i **IDispatch**. Jak pokazano na poniższej ilustracji, CCW obsługuje jedno odwołanie dla obiektu .NET, który jest zawijany. Zarówno klient modelu COM i .NET obiektu współdziałać ze sobą za pośrednictwem serwera proxy i stub konstrukcja CCW.  
  
 ![Interfejsy modelu COM](./media/ccwwithinterfaces.gif "ccwwithinterfaces")  
Interfejsy modelu COM i wywoływana otoka COM  
  
 Oprócz udostępnianie interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, .NET Framework dostarcza implementacji interfejsów COM wymienione w poniższej tabeli w imieniu obiektu. Klasy .NET można zastąpić domyślne zachowanie, zapewniając własną implementację tych interfejsów. Jednak środowiska uruchomieniowego zawsze udostępnia implementację dla **IUnknown** i **IDispatch** interfejsów.  
  
|Interface|Opis|  
|---------------|-----------------|  
|**Idispatch**|Udostępnia mechanizm późne powiązania do typu.|  
|**IerrorInfo**|Dostarcza opis tekstowy błąd, źródła pliku pomocy, kontekst pomocy i identyfikator GUID interfejsu, który zdefiniowano błędu (zawsze **GUID_NULL** dla klas .NET).|  
|**IprovideClassInfo**|Umożliwia klientom uzyskanie dostępu do modelu COM **ITypeInfo** interfejsu implementowanego przez zarządzanej klasy.|  
|**IsupportErrorInfo**|Umożliwia klientowi COM ustalić, czy obiekt zarządzany obsługuje **IErrorInfo** interfejsu. Jeśli tak, umożliwia klientowi uzyskać wskaźnik do najnowszej obiekt wyjątku. Wszystkie typy Obsługa zarządzanego **IErrorInfo** interfejsu.|  
|**ItypeInfo**|Zawiera informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie utworzonego przez Tlbexp.exe.|  
|**Iunknown**|Udostępnia implementację standardowe **IUnknown** interfejs, z którym klient modelu COM zarządza czasem istnienia CCW i udostępnia koercja typu.|  
  
 Zarządzanej klasy oferuje również interfejsy modelu COM, opisane w poniższej tabeli.  
  
|Interface|Opis|  
|---------------|-----------------|  
|(\_*Classname*) interfejsu klasy|Interfejs, udostępniane przez środowisko uruchomieniowe i nie są jawnie zdefiniowane, która udostępnia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie widoczne obiektu zarządzanego.|  
|**IConnectionPoint** i **IconnectionPointContainer**|Interfejs dla obiektów, które źródła na podstawie delegata zdarzenia (interfejs do rejestrowania zdarzeń subskrybentów).|  
|**IdispatchEx**|Interfejs dostarczony przez środowisko uruchomieniowe, jeśli klasa implementuje **IExpando**. **IDispatchEx** interfejsu jest rozszerzeniem **IDispatch** interfejsu, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania i z uwzględnieniem wielkości liter wywoływanie elementów członkowskich.|  
|**Interfejsu IEnumVARIANT**|Interfejs dla klasy typ kolekcji, która wylicza obiektów w kolekcji, jeśli klasa implementuje **IEnumerable**.|  
  
## <a name="introducing-the-class-interface"></a>Wprowadzenie do interfejsu klasy  
 Interfejs klasy, która nie jest jawnie zdefiniowany w zarządzanym kodzie, to interfejs, który udostępnia wszystkie metody publiczne, właściwości pola i zdarzenia, które jawnie są dostępne dla obiektu .NET. Ten interfejs może być interfejsem podwójną lub w trybie tylko do wysyłania. Interfejs klasy uzyskuje nazwę klasy .NET, poprzedzone znaku podkreślenia. Na przykład dla klasy ssak interfejsu klasy jest \_ssak.  
  
 Dla klas pochodnych interfejsu klasy udostępnia również metody publiczne, właściwości i pola klasy podstawowej. Klasy pochodnej udostępnia również interfejs klasy dla każdej klasy podstawowej. Na przykład, jeśli klasa ssak rozszerza klasę MammalSuperclass, które stanowi rozszerzenie elementu System.Object, ujawnia obiektu .NET dla klientów modelu COM. trzy klasy o nazwie interfejsów \_ssak, \_MammalSuperclass, i \_obiektu.  
  
 Na przykład wziąć pod uwagę następujące klasy .NET:  
  
```vb  
' Applies the ClassInterfaceAttribute to set the interface to dual.  
<ClassInterface(ClassInterfaceType.AutoDual)> _  
' Implicitly extends System.Object.  
Public Class Mammal  
    Sub Eat()  
    Sub Breathe()  
    Sub Sleep()  
End Class  
```  
  
```csharp  
// Applies the ClassInterfaceAttribute to set the interface to dual.  
[ClassInterface(ClassInterfaceType.AutoDual)]  
// Implicitly extends System.Object.  
public class Mammal  
{  
    void  Eat();  
    void  Breathe():  
    void  Sleep();  
}  
```  
  
 Klient COM może pobrać wskaźnik do interfejsu klasy o nazwie `_Mammal`, opisanym w bibliotece typów który [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) narzędzie. Jeśli `Mammal` klasy zaimplementowane interfejsy co najmniej jednego, interfejsy pojawią się w obszarze klasy coclass.  
  
```  
[odl, uuid(…), hidden, dual, nonextensible, oleautomation]  
interface _Mammal : IDispatch  
{  
    [id(0x00000000), propget] HRESULT ToString([out, retval] BSTR*  
        pRetVal);  
    [id(0x60020001)] HRESULT Equals([in] VARIANT obj, [out, retval]  
        VARIANT_BOOL* pRetVal);  
    [id(0x60020002)] HRESULT GetHashCode([out, retval] short* pRetVal);  
    [id(0x60020003)] HRESULT GetType([out, retval] _Type** pRetVal);  
    [id(0x6002000d)] HRESULT Eat();  
    [id(0x6002000e)] HRESULT Breathe();  
    [id(0x6002000f)] HRESULT Sleep();  
}  
[uuid(…)]  
coclass Mammal   
{  
    [default] interface _Mammal;  
}  
```  
  
 Generowanie interfejsu klasy jest opcjonalna. Domyślnie usługa międzyoperacyjna modelu COM generuje tylko do wysyłania interfejs dla każdej klasy wyeksportowane do biblioteki typów. Można zapobiec lub zmodyfikować automatycznego tworzenia tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do swojej klasy. Mimo że interfejsu klasy może ułatwić zadań ujawnienia zarządzanej klasy COM, jego zastosowań są ograniczone.  
  
> [!CAUTION]
>  Za pomocą interfejsu klasy zamiast jawnie definiować własne, skomplikować przyszłych wersji zarządzanej klasy. Przeczytaj poniższe wskazówki przed rozpoczęciem korzystania z interfejsu klasy.  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Zdefiniuj jawnego interfejsu dla klientów modelu COM można użyć zamiast generowania interfejsu klasy.  
 Ponieważ usługa międzyoperacyjna modelu COM, które automatycznie generuje interfejsu klasy, po wersji zmiany do swojej klasy można zmienić układ interfejsu klasy udostępniane przez środowisko uruchomieniowe języka wspólnego. Ponieważ klienci COM są zwykle nieprzygotowany obsługiwać zmiany w układzie interfejs, Przerwij w przypadku zmiany układu elementu członkowskiego klasy.  
  
 Niniejsze wytyczne wzmacnia pojęcia, że interfejsy widoczne dla klientów modelu COM musi pozostać niezmienne. Aby zmniejszyć ryzyko złamanie klientów modelu COM. przypadkowo zmiana kolejności układ interfejsu, wyizolować wszystkie zmiany do klasy z układu interfejsu przez jawne zdefiniowanie interfejsów.  
  
 Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy i zaimplementować jawnego interfejsu klasy, jak przedstawiono na poniższym fragmencie kodu:  
  
```vb  
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp  
    Implements IExplicit  
    Sub M() Implements IExplicit.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.None)]  
public class LoanApp : IExplicit {  
    void M();  
}  
```  
  
 **ClassInterfaceType.None** wartość zapobiega interfejsu klasy generowane podczas eksportowania metadanych klasy do biblioteki typów. W poprzednim przykładzie, mogą uzyskać dostęp klienci COM `LoanApp` tylko za pomocą klasy `IExplicit` interfejsu.  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Unikaj buforowanie wysyłania identyfikatorów (identyfikator DISPID)
 Przy użyciu interfejsu klasy jest dopuszczalne opcją klientów przy użyciu skryptu, Microsoft Visual Basic 6.0 lub późnym wiązaniem klienta, który nie będzie buforować identyfikatory DISPID członków interfejsu. Identyfikator DISPID Identyfikowanie członków interfejsu, aby umożliwić późne wiązanie.  
  
 Dla interfejsu klasy generowania identyfikator DISPID opiera się na pozycji elementu członkowskiego w interfejsie. Jeśli zmiana kolejności elementu członkowskiego i wyeksportować klasie do biblioteki typów, zmieni identyfikator DISPID, generowane w interfejsie klasa.  
  
 Aby uniknąć dzielenia klientów modelu COM. z późnym wiązaniem, korzystając z interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartości. Ta wartość implementuje interfejs klasy tylko do wysyłania, ale pominięto opis interfejsu z biblioteki typów. Opis interfejsu — bez klientów występują problemy dotyczące czas kompilacji identyfikator DISPID w pamięci podręcznej. Jest to domyślny typ interfejsu dla interfejsu klasy, należy zastosować jawnie wartość atrybutu.  
  
```vb  
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp  
    Implements IAnother  
    Sub M() Implements IAnother.M  
…  
End Class  
```  
  
```csharp  
[ClassInterface(ClassInterfaceType.AutoDispatch]  
public class LoanApp : IAnother {  
    void M();  
}  
```  
  
 Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, można wywołać klientów modelu COM. **IDispatch.GetIdsOfNames**. Aby wywołać metody w interfejsie, Przekaż DispId zwrócony jako argument do **IDispatch.Invoke**.  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Ogranicz przy użyciu opcji podwójną interfejsu dla interfejsu klasy.  
 Podwójne interfejsy Włącz wczesne i późne powiązania elementów członkowskich interfejsu COM klientów. W czasie projektowania i podczas testowania może być przydatne go ustawić dwa interfejsu klasy. Zarządzanej klasy (i jej klas podstawowych) który nigdy nie będą zmodyfikowane, ta opcja jest również akceptowane. We wszystkich innych przypadkach uniknąć ustawienie podwójnego interfejsu klasy.  
  
 Interfejs podwójną automatycznie generowanych może być dobrym rozwiązaniem w rzadkich przypadkach; jednak częściej tworzy związanych z wersji złożoności. Na przykład klientów modelu COM przy użyciu interfejsu klasy pochodnej klasy łatwo można przerwać ze zmianami do klasy podstawowej. W przypadku innych firm udostępnia klasę podstawową, układ interfejsu klasy jest poza formantu. Bardziej szczegółowo w przeciwieństwie do interfejsu tylko do wysyłania podwójną interfejsu (**ClassInterface.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej biblioteki typów. Opis taki zachęca klientów z późnym wiązaniem do pamięci podręcznej identyfikator DISPID w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [Otoki COM](com-wrappers.md)  
 [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)  
 [Kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md)  
 [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)