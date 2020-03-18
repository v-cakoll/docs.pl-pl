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
ms.openlocfilehash: 6f2f4055a95dbcea8d7872b5c5fa3ccede8c2c8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400380"
---
# <a name="com-callable-wrapper"></a>Wywoływana otoka COM

Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu. Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.

Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług. Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew. Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci. Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.

![Wielu klientów COM posiadających odwołanie do CCW, który udostępnia INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Otoki wywoływane przez COM są niewidoczne dla innych klas działających w czasie wykonywania .NET. Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.

## <a name="object-identity"></a>Tożsamość obiektu

Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami. Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.

## <a name="object-lifetime"></a>Okres istnienia obiektu

W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM. Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu. Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.

## <a name="simulating-com-interfaces"></a>Symulowanie interfejsów COM

CCW udostępnia wszystkie publiczne, widoczne dla modelu COM interfejsy, typy danych i zwracanie wartości klientom COM w sposób zgodny z wymuszaniem interakcji opartych na interfejsie przez COM. Dla klienta COM wywoływanie metod na obiekcie .NET jest identyczne z wywoływanie m.in.

Aby utworzyć to podejście bez szwu, CCW produkuje tradycyjne interfejsy COM, takie jak **IUnknown** i **IDispatch**. Jak pokazano na poniższej ilustracji, CCW utrzymuje pojedyncze odwołanie na .NET obiektu, który jest zawijany. Zarówno klient COM, jak i obiekt .NET współdziałają ze sobą za pośrednictwem serwera proxy i konstrukcji skrótowej CCW.

![Diagram, który pokazuje, jak CCW produkuje interfejsy COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Oprócz ujawniania interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, środowisko wykonawcze .NET dostarcza implementacje interfejsów COM wymienionych w poniższej tabeli w imieniu obiektu. Klasa .NET można zastąpić zachowanie domyślne, zapewniając własną implementację tych interfejsów. Jednak czas wykonywania zawsze zapewnia implementację dla **interfejsów IUnknown** i **IDispatch.**

|Interface|Opis|
|---------------|-----------------|
|**Idispatch**|Zapewnia mechanizm późnego wiązania typu.|
|**Ierrorinfo**|Zawiera tekstowy opis błędu, jego źródła, pliku Pomocy, kontekstu Pomocy i identyfikatora GUID interfejsu, który zdefiniował błąd (zawsze **GUID_NULL** dla klas .NET).|
|**IProvideClassInfo (IProvideClassInfo)**|Umożliwia klientom COM uzyskanie dostępu do interfejsu **ITypeInfo** zaimplementowanego przez klasę zarządzaną. Zwraca `COR_E_NOTSUPPORTED` wartość programu .NET Core dla typów, które nie są importowane z com. |
|**Isupporterrorinfo**|Umożliwia klientowi COM określenie, czy obiekt zarządzany obsługuje interfejs **IErrorInfo.** Jeśli tak, umożliwia klientowi uzyskanie wskaźnika do najnowszego obiektu wyjątku. Wszystkie typy zarządzane obsługują interfejs **IErrorInfo.**|
|**ITypeInfo** (tylko struktura.NET)|Zawiera informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie produkowane przez Tlbexp.exe.|
|**IUnknown**|Zapewnia standardową implementację interfejsu **IUnknown,** z którym klient COM zarządza okresem istnienia CCW i zapewnia typ przymusu.|

 Klasa zarządzana może również zapewnić interfejsy COM opisane w poniższej tabeli.

|Interface|Opis|
|---------------|-----------------|
|Interfejs\_klasy *(classname)*|Interfejs, udostępniane przez program runtime i nie jawnie zdefiniowane, który udostępnia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie widoczne na obiekcie zarządzanym.|
|**IConnectionPoint** i **IConnectionPointContainer**|Interfejs dla obiektów, które źródło zdarzeń opartych na delegowaniu (interfejs do rejestrowania subskrybentów zdarzeń).|
|**IDispatchEx** (tylko platforma.NET)|Interfejs dostarczany przez program runtime, jeśli klasa implementuje **IExpando**. Interfejs **IDispatchEx** jest rozszerzeniem interfejsu **IDispatch,** które w przeciwieństwie do **IDispatch**umożliwia wyliczanie, dodawanie, usuwanie i wywoływanie elementów członkowskich.|
|**Ienumvariant**|Interfejs dla klas typu kolekcji, który wylicza obiekty w kolekcji, jeśli klasa implementuje **IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Przedstawiamy interfejs klasy

Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, jest interfejsem, który udostępnia wszystkie metody publiczne, właściwości, pola i zdarzenia, które są jawnie widoczne w obiekcie .NET. Ten interfejs może być interfejsem dual lub dispatch-only. Interfejs klasy odbiera nazwę samej klasy .NET, poprzedzoną podkreśleniem. Na przykład dla klasy Ssak, \_interfejs klasy jest Ssak.

Dla klas pochodnych interfejs klasy udostępnia również wszystkie metody publiczne, właściwości i pola klasy podstawowej. Klasa pochodna udostępnia również interfejs klasy dla każdej klasy podstawowej. Na przykład jeśli klasa MammalSuperclass, która sama rozszerza System.Object, obiekt .NET udostępnia klientom COM trzy \_interfejsy \_klas o nazwie \_Mammal, MammalSuperclass i Object.

Rozważmy na przykład następującą klasę .NET:

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

Klient COM może uzyskać wskaźnik do `_Mammal`interfejsu klasy o nazwie . W platformie .NET Framework można użyć narzędzia [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) do wygenerowania biblioteki typów zawierającej definicję `_Mammal` interfejsu. Eksporter biblioteki typów nie jest obsługiwany w usłudze .NET Core. Jeśli `Mammal` klasa zaimplementowana jeden lub więcej interfejsów, interfejsy będą wyświetlane w ramach koklasy.

```console
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

Generowanie interfejsu klasy jest opcjonalne. Domyślnie współdziałania COM generuje interfejs tylko do wysyłki dla każdej klasy eksportowane do biblioteki typów. Można zapobiec lub zmodyfikować automatyczne tworzenie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> tego interfejsu, stosując do swojej klasy. Mimo że interfejs klasy może ułatwić zadanie ujawniania zarządzanych klas do com, jego zastosowania są ograniczone.

> [!CAUTION]
> Przy użyciu interfejsu klasy, zamiast jawnie definiowania własnych, może skomplikować przyszłe przechowywanie wersji klasy zarządzanej. Przed użyciem interfejsu klasy należy zapoznać się z poniższymi wskazówkami.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Zdefiniuj jawny interfejs dla klientów COM do użycia, a nie generowania interfejsu klasy.

Ponieważ com interop generuje interfejs klasy automatycznie, zmiany po wersji do klasy można zmienić układ interfejsu klasy udostępniane przez wspólny język w czasie wykonywania. Ponieważ klienci COM są zazwyczaj nieprzygotowani do obsługi zmian w układzie interfejsu, przerywają, jeśli zmienisz układ elementu członkowskiego klasy.

Ta wytyczna wzmacnia przekonanie, że interfejsy udostępniane klientom COM muszą pozostać niezmienne. Aby zmniejszyć ryzyko przerwania klientów COM przez nieumyślne zmianę kolejności układu interfejsu, wyizoluj wszystkie zmiany w klasie od układu interfejsu, jawnie definiując interfejsy.

Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy i zaimplementować jawny interfejs dla klasy, jak pokazano następujący fragment kodu:

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

**ClassInterfaceType.None** wartość uniemożliwia interfejs klasy są generowane, gdy metadane klasy jest eksportowany do biblioteki typów. W poprzednim przykładzie klienci COM mogą `LoanApp` uzyskać dostęp `IExplicit` do klasy tylko za pośrednictwem interfejsu.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Unikaj buforowania identyfikatorów wysyłki (DispIds)

Korzystanie z interfejsu klasy jest akceptowalną opcją dla klientów skryptowych, klientów programu Microsoft Visual Basic 6.0 lub dowolnego klienta z późnym wiązaniem, który nie buforuje identyfikatorów identyfikatorów członkowskich interfejsu. Identyfikatory dispIds zidentyfikować elementy członkowskie interfejsu, aby włączyć późne wiązanie.

Dla interfejsu klasy generacji DispIds opiera się na pozycji elementu członkowskiego w interfejsie. Jeśli zmienisz kolejność elementu członkowskiego i wyeksportujesz klasę do biblioteki typów, zmienisz identyfikatory DispIds wygenerowane w interfejsie klasy.

Aby uniknąć przerywania klientów COM z późnym wiązaniem podczas korzystania z interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartość. Ta wartość implementuje interfejs klasy tylko do wysyłki, ale pomija opis interfejsu z biblioteki typów. Bez opisu interfejsu klienci nie mogą buforować identyfikatorów DispIds w czasie kompilacji. Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartość atrybutu jawnie.

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

Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, klienci COM można wywołać **IDispatch.GetIdsOfNames**. Aby wywołać metodę w interfejsie, przekazać zwrócony DispId jako argument **do IDispatch.Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Ogranicz przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.

Dwa interfejsy umożliwiają wczesne i późne wiązanie z członkami interfejsu przez klientów COM. W czasie projektowania i podczas testowania może okazać się przydatne, aby ustawić interfejs klasy na podwójny. Dla klasy zarządzanej (i jej klas podstawowych), które nigdy nie zostaną zmodyfikowane, ta opcja jest również dopuszczalne. We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójny.

Automatycznie generowany podwójny interfejs może być odpowiedni w rzadkich przypadkach; jednak częściej tworzy złożoność związaną z wersją. Na przykład klienci COM przy użyciu interfejsu klasy klasy pochodnej można łatwo przerwać ze zmianami do klasy podstawowej. Gdy strona trzecia zapewnia klasę podstawową, układ interfejsu klasy jest poza kontrolą. Ponadto, w przeciwieństwie do interfejsu tylko do wysyłki, podwójny interfejs (**ClassInterfaceType.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej bibliotece typów. Taki opis zachęca klientów z późnym wiązaniem do buforowania identyfikatorów DispIds w czasie kompilacji.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Upewnij się, że wszystkie powiadomienia o zdarzeniach COM są późne.

Domyślnie informacje o typie COM są osadzone bezpośrednio w zestawach zarządzanych, co eliminuje konieczność stosowania podstawowych zestawów międzyop (PIA). Jednak jednym z ograniczeń informacji o typie osadzonym jest to, że nie obsługuje dostarczania powiadomień o `IDispatch::Invoke` zdarzeniach COM przez wywołania vtable na początku, ale obsługuje tylko wywołania z późnym wiązaniem.

Jeśli aplikacja wymaga wywołań na wczesnym etapie do metod interfejsu zdarzenia COM, można ustawić `true` **Embed Interop Types** właściwość w programie Visual Studio do lub dołączyć następujący element w pliku projektu:

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [Otoki COM](com-wrappers.md)
- [Udostępnianie składników .NET Framework modelowi COM](../../framework/interop/exposing-dotnet-components-to-com.md)
- [Udostępnianie składników .NET Core modelowi COM](../../core/native-interop/expose-components-to-com.md)
- [Kwalifikowanie typów .NET do międzyoperacyjności](qualify-net-types-for-interoperation.md)
- [Wywoływana otoka środowiska uruchomieniowego](runtime-callable-wrapper.md)
