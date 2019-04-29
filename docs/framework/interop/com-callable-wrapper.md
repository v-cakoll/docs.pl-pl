---
title: Wywoływana otoka COM
ms.date: 10/23/2018
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
ms.openlocfilehash: 942ba933126da291e072270318a5657953ddcdb8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61643624"
---
# <a name="com-callable-wrapper"></a>Wywoływana otoka COM

Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu. Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.

Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług. Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew. Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci. Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.

![Wielu klientów modelu COM, zawierający odwołanie do otoki CCW, która udostępnia INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Otoki wywoływane z modelu COM są niewidoczne dla innych klas uruchomionych w środowisku .NET Framework. Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.

## <a name="object-identity"></a>Tożsamość obiektu

Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami. Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.

## <a name="object-lifetime"></a>Okres istnienia obiektu

W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM. Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu. Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.

## <a name="simulating-com-interfaces"></a>Symulowanie interfejsów COM

CCW uwidacznia wszystkie publiczne, interfejsach widocznych dla modelu COM, typy danych i wartości zwracane do klientów modelu COM w sposób, który jest zgodny z modelu COM wymuszania interakcji z interfejsu. Klient modelu COM wywoływanie metod dla obiektu .NET Framework jest taka sama jak wywoływanie metod na obiekt COM.

Aby utworzyć to bezproblemowe podejście, CCW są produkowane tradycyjnych interfejsów COM, takich jak **IUnknown** i **IDispatch**. Jak pokazano na poniższej ilustracji, CCW zachowuje jedno odwołanie obiektu platformy .NET, która je otacza. Zarówno klient modelu COM, jak i obiektu .NET ze sobą współdziałać za pośrednictwem serwera proxy i klasy zastępczej konstrukcja CCW.

![Diagram, który pokazuje, jak CCW produkuje interfejsy COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Oprócz udostępnianie interfejsów, które są jawnie implementowane przez klasy w środowisku zarządzanym, .NET Framework dostarcza implementacji interfejsów COM, wymienione w poniższej tabeli w imieniu obiektu. Klasa platformy .NET można zastąpić domyślne zachowanie, podając własną implementację tych interfejsów. Środowisko uruchomieniowe zawsze zapewnia jednak wykonania na **IUnknown** i **IDispatch** interfejsów.

|Interface|Opis|
|---------------|-----------------|
|**IDispatch**|Udostępnia mechanizm późnym wiązaniem do typu.|
|**IErrorInfo**|Zawiera opis tekstowy błędu, źródło, pliku pomocy, Pomoc kontekstowa i identyfikator GUID interfejs który jest zdefiniowany błędu (zawsze **GUID_NULL** dla klas platformy .NET).|
|**IProvideClassInfo**|Umożliwia klientom COM uzyskać dostęp do **ITypeInfo** interfejs implementowany przez klasy zarządzanej.|
|**Interfejs ISupportErrorInfo**|Umożliwia klientowi COM ustalić, czy obsługuje obiektu zarządzanego **IErrorInfo** interfejsu. Jeśli tak, ta umożliwia uzyskiwanie wskaźnika do najnowszych obiekt wyjątku. Wszystkie zarządzane typy obsługi **IErrorInfo** interfejsu.|
|**ITypeInfo**|Zawiera informacje o typie dla klasy, w którym są dokładnie takie same jak informacje o typie utworzony przez Tlbexp.exe.|
|**IUnknown**|Dostarcza implementację standardowa **IUnknown** interfejs, za pomocą którego klient modelu COM zarządza czasem istnienia CCW i umożliwia wymuszanie typów.|

 Klasa zarządzana oferuje również interfejsów COM, opisanego w poniższej tabeli.

|Interface|Opis|
|---------------|-----------------|
|(\_*Classname*) interfejs klasy|Interfejs, udostępniane przez środowisko uruchomieniowe i nie zostały jawnie określone, który przedstawia wszystkich interfejsów publicznych, metod, właściwości i pola, które są jawnie widoczne zarządzanego obiektu.|
|**IConnectionPoint** i **interfejsy IConnectionPointContainer**|Interfejs dla obiektów, które źródeł zdarzeń opartych na delegacie (interfejs rejestracji subskrybentów zdarzeń).|
|**IDispatchEx**|Interfejs dostarczony przez środowisko wykonawcze, jeśli klasa implementuje **IExpando**. **IDispatchEx** interfejs jest rozszerzeniem **IDispatch** interfejs, który, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania oraz wielkość liter wywoływanie elementów członkowskich.|
|**Interfejs IEnumVARIANT**|Interfejs dla klasy typ kolekcji, która wylicza obiektów w kolekcji, jeśli klasa implementuje **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Wprowadzenie interfejsu klasy

Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, to interfejs, który udostępnia wszystkie metody publiczne, właściwości, pola i zdarzenia, które jawnie są widoczne dla obiektu .NET. Ten interfejs może być interfejsem podwójna lub tylko do wysyłania. Interfejs klasy uzyskuje nazwę klasy .NET, poprzedzonej podkreśleniem. Na przykład dla klasy ssak interfejsu klasy jest \_ssak.

Dla klas pochodnych interfejsu klasy udostępnia również metody publiczne, właściwości i pola klasy bazowej. W klasie pochodnej udostępnia również interfejs klasy dla każdej klasy bazowej. Na przykład, jeśli klasa ssak rozszerza klasę MammalSuperclass, która sama rozszerza System.Object, udostępnia obiekt .NET do klientów modelu COM, trzy klasy interfejsów o nazwie \_ssak, \_MammalSuperclass, i \_obiektu.

Na przykład rozważmy następujące klasy .NET:

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
    public void Eat() {}
    public void Breathe() {}
    public void Sleep() {}
}
```

Klient COM może pobrać wskaźnik do interfejsu klasy o nazwie `_Mammal`, który jest opisany w bibliotece typów, [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) narzędzie generuje. Jeśli `Mammal` klasy zaimplementować jeden lub więcej interfejsów, interfejsy, zostanie wyświetlony w obszarze wspólna.

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

Generowanie interfejsu klasy jest opcjonalne. Domyślnie usługa międzyoperacyjna modelu COM generuje tylko do wysyłania interfejs dla każdej klasy, które są eksportowane do biblioteki typów. Możesz uniemożliwić lub zmodyfikować automatyczne tworzenie tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do swojej klasy. Chociaż interfejs klasy może ułatwić zadań ujawnienia klas zarządzanych dla modelu COM, jego zastosowania są ograniczone.

> [!CAUTION]
> Za pomocą interfejsu klasy zamiast jawnie definiować własne, skomplikować przyszłych wersji klasy zarządzanej. Przeczytaj poniższe wskazówki przed rozpoczęciem korzystania z interfejsu klasy.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Definicja jawnego interfejsu dla klientów modelu COM do użycia, zamiast generować interfejsu klasy.

Ponieważ usługa międzyoperacyjna modelu COM, które automatycznie generuje interfejs klasy, zmiany po wydaniu wersji do klasy można zmienić układ interfejsu klasy udostępnianych przez środowisko uruchomieniowe języka wspólnego. Ponieważ klientów modelu COM są zazwyczaj Nieprzygotowane do obsługi zmian w układzie interfejs, dzielą one, jeśli zmienisz układ składowych klasy.

Ta wytyczna wzmacnia pojęcia, że interfejsy ujawnione klientom modelu COM musi pozostać nie będzie zmieniana. Aby zmniejszyć ryzyko przerwanie klientów modelu COM przypadkowo zmiana kolejności układów interfejsu, wyizolować wszystkie zmiany do klasy w układzie interfejsu przez jawne określenie interfejsów.

Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy do implementacji interfejsu jawnego dla tej klasy, co ilustruje poniższy fragment kodu:

```vb
<ClassInterface(ClassInterfaceType.None)>Public Class LoanApp
    Implements IExplicit
    Sub M() Implements IExplicit.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.None)]
public class LoanApp : IExplicit
{
    int IExplicit.M() { return 0; }
}
```

**ClassInterfaceType.None** wartość zapobiega interfejsu klasy są generowane, gdy metadanych klas są eksportowane do biblioteki typów. W powyższym przykładzie klienci COM mogą uzyskiwać dostęp `LoanApp` tylko przez klasy `IExplicit` interfejsu.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Należy unikać buforowania identyfikatory wysyłania (DISPID)

Przy użyciu interfejsu klasy. czy dopuszczalne rozwiązanie dla klientów przy użyciu skryptu, Microsoft Visual Basic 6.0 lub klienta z późnym wiązaniem, który nie będzie buforować DISPID członków interfejsów. DISPID zidentyfikować składowych interfejsu, aby umożliwić późnego wiązania.

Dla interfejsu klasy generowania DISPID opiera się na pozycji elementu członkowskiego w interfejsie. Jeśli zmiana kolejności elementu członkowskiego i wyeksportować klasy do biblioteki typów, powodują zmianę DISPID, wygenerowane za pomocą interfejsu klasy.

Aby uniknąć przerwanie klientów modelu COM z późnym wiązaniem przy użyciu interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartości. Ta wartość implementuje interfejs klasy jako tylko do wysyłki, ale pomija opis interfejsu z biblioteki typów. Bez opisu interfejsu klientów są do pamięci podręcznej DISPID na czas kompilacji. Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartości atrybutu jawnie.

```vb
<ClassInterface(ClassInterfaceType.AutoDispatch)> Public Class LoanApp
    Implements IAnother
    Sub M() Implements IAnother.M
…
End Class
```

```csharp
[ClassInterface(ClassInterfaceType.AutoDispatch)]
public class LoanApp
{
    public int M() { return 0; }
}
```

Aby uzyskać identyfikator DispId składowej interfejsu w czasie wykonywania, można wywołać klientów modelu COM **IDispatch.GetIdsOfNames**. Aby wywołać metodę interfejsu, należy przekazać zwrócony identyfikator DispId jako argument do **IDispatch.Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Ograniczenia przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.

Podwójne interfejsy umożliwiają wczesne i późne powiązania do składowych interfejsu klienci COM. W czasie projektowania i podczas testowania może być przydatne go ustawić podwójnego interfejsu klasy. Klasa zarządzana (i jej klasy bazowe), nigdy nie będą modyfikowane, ta opcja jest również dopuszczalne. We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójne.

Odpowiednie w rzadkich przypadkach; może być automatycznie generowane podwójnego interfejsu jednak częściej tworzy złożoności związane z wersją. Na przykład Klienci COM za pomocą interfejsu klasy pochodnej klasy łatwo może przerwać ze zmianami do klasy bazowej. Jeśli strona trzecia udostępnia klasę bazową, układ interfejsu klasy jest poza Twoją kontrolą. Bardziej szczegółowo, w przeciwieństwie do interfejsu tylko do wysyłania podwójnego interfejsu (**ClassInterfaceType.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej biblioteki typów. Opis taki zachęca klientów z późnym wiązaniem do pamięci podręcznej DISPID na czas kompilacji.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Upewnij się, że wszystkie powiadomienia o zdarzeniach modelu COM z późnym wiązaniem.

Domyślnie informacje o typie modelu COM jest osadzony bezpośrednio do zestawów zarządzanych, która eliminuje potrzebę stosowania podstawowych zestawów międzyoperacyjnych (PIA). Jednak jedną z ograniczenia informacje o typie osadzony jest ona nieobsługiwana dostarczania powiadomień o zdarzeniach COM przez wywołania z wczesnym wiązaniem vtable, ale obsługuje tylko z późnym wiązaniem `IDispatch::Invoke` wywołania.

Jeśli aplikacja wymaga wywołania wczesnym wiązaniem do metody interfejsu zdarzeń COM, możesz ustawić **Osadź typy współdziałania** właściwości w programie Visual Studio do `true`, lub Uwzględnij następujący element w pliku projektu:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Otoki COM](com-wrappers.md)
- [Udostępnianie składników .NET Framework modelowi COM](exposing-dotnet-components-to-com.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md)
- [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)
