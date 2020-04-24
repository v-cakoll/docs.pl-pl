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

![Wielu klientów COM przechowujących odwołanie do CCW, które uwidacznia INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

Wywoływane otoki COM są niewidoczne dla innych klas uruchomionych w środowisku uruchomieniowym .NET. Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.

## <a name="object-identity"></a>Tożsamość obiektu

Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami. Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.

## <a name="object-lifetime"></a>Okres istnienia obiektu

W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM. Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu. Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.

## <a name="simulating-com-interfaces"></a>Symulowanie interfejsów COM

CCW udostępnia wszystkie publiczne, widoczne dla modelu COM interfejsy, typy danych i zwraca wartości do klientów COM w sposób, który jest zgodny z wymuszeniem interakcji opartej na interfejsie COM. W przypadku klienta COM wywoływanie metod w obiekcie .NET jest identyczne z wywoływaniem metod obiektu COM.

Aby utworzyć to bezproblemowe podejście, CCW produkuje tradycyjne interfejsy COM, takie jak **IUnknown** i **IDispatch**. Jak widać na poniższej ilustracji, CCW zachowuje pojedyncze odwołanie do obiektu platformy .NET, który go otacza. Zarówno klient COM, jak i obiekt .NET współpracują ze sobą za pomocą serwera proxy i klasy zastępczej CCW.

![Diagram przedstawiający sposób, w jaki CCW produkuje interfejsy COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

Oprócz ujawniania interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, środowisko uruchomieniowe platformy .NET dostarcza implementacje interfejsów COM wymienionych w poniższej tabeli w imieniu obiektu. Klasa platformy .NET może zastąpić domyślne zachowanie, dostarczając własną implementację tych interfejsów. Jednak środowisko uruchomieniowe zawsze zapewnia implementację interfejsów **IUnknown** i **IDispatch** .

|Interface|Opis|
|---------------|-----------------|
|**IDispatch**|Udostępnia mechanizm późnego wiązania do typu.|
|**IErrorInfo**|Zawiera tekstowy opis błędu, jego źródło, plik pomocy, kontekst pomocy oraz identyfikator GUID interfejsu, który definiuje błąd (zawsze **GUID_NULL** dla klas .NET).|
|**IProvideClassInfo**|Umożliwia klientom COM uzyskiwanie dostępu do interfejsu **Metoda ITypeInfo** zaimplementowanego przez klasę zarządzaną. Zwraca `COR_E_NOTSUPPORTED` na platformie .NET Core dla typów, które nie zostały zaimportowane z modelu com. |
|**ISupportErrorInfo**|Umożliwia klientowi COM określenie, czy zarządzany obiekt obsługuje interfejs **IErrorInfo** . Jeśli tak, program umożliwia klientowi uzyskanie wskaźnika do ostatniego obiektu wyjątku. Wszystkie typy zarządzane obsługują interfejs **IErrorInfo** .|
|**Metoda ITypeInfo** (tylko .NET Framework)|Zapewnia informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie wytwarzane przez Tlbexp. exe.|
|**IUnknown**|Zapewnia standardową implementację interfejsu **IUnknown** , za pomocą którego klient com zarządza okresem istnienia CCW i zapewnia przekształcenie typu.|

 Zarządzana Klasa może również udostępniać interfejsy COM opisane w poniższej tabeli.

|Interface|Opis|
|---------------|-----------------|
|Interfejs klasy\_(*ClassName*)|Interfejs, uwidoczniony przez środowisko uruchomieniowe i niejawnie zdefiniowany, który uwidacznia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie uwidocznione w zarządzanym obiekcie.|
|**IConnectionPoint** i **IConnectionPointContainer**|Interfejs dla obiektów, które są źródłem zdarzeń opartych na delegatach (interfejs do rejestrowania subskrybentów zdarzeń).|
|**IDispatchEx** (tylko .NET Framework)|Interfejs dostarczony przez środowisko uruchomieniowe, jeśli klasa implementuje **IExpando**. Interfejs **IDispatchEx** jest rozszerzeniem interfejsu **IDispatch** , który, w przeciwieństwie do **IDispatch**, włącza Wyliczenie, Dodawanie, usuwanie i uwzględnianie wielkości liter dla elementów członkowskich.|
|**IEnumVARIANT**|Interfejs dla klas typu kolekcji, który wylicza obiekty w kolekcji, jeśli klasa implementuje **interfejs IEnumerable**.|

## <a name="introducing-the-class-interface"></a>Wprowadzenie do interfejsu klasy

Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, jest interfejsem, który uwidacznia wszystkie metody publiczne, właściwości, pola i zdarzenia, które są jawnie uwidocznione w obiekcie .NET. Ten interfejs może być interfejsem o podwójnym lub tylko do wysyłania. Interfejs klasy odbiera nazwę samej klasy .NET, poprzedzoną podkreśleniem. Na przykład dla ssaków klasy, interfejs klasy to \_ssak.

W przypadku klas pochodnych interfejs klasy udostępnia również wszystkie metody publiczne, właściwości i pola klasy podstawowej. Klasa pochodna również udostępnia interfejs klasy dla każdej klasy bazowej. Na przykład, jeśli ssak klas rozszerza klasę MammalSuperclass, która sama stanowi rozszerzenie elementu System. Object, obiekt .NET uwidacznia klientom COM trzy interfejsy klasy o \_nazwie ssak \_, MammalSuperclass i \_Object.

Rozważmy na przykład następujące klasy .NET:

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

Klient COM może uzyskać wskaźnik do interfejsu klasy o nazwie `_Mammal`. Na .NET Framework można użyć narzędzia [eksportu biblioteki typów (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) w celu wygenerowania biblioteki typów zawierającej definicję `_Mammal` interfejsu. Eksporter biblioteki typów nie jest obsługiwany w programie .NET Core. Jeśli `Mammal` Klasa implementuje jeden lub więcej interfejsów, interfejsy pojawią się pod klasą coclass.

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

Generowanie interfejsu klasy jest opcjonalne. Domyślnie usługa międzyoperacyjna modelu COM generuje interfejs tylko do wysyłania dla każdej klasy, która jest eksportowana do biblioteki typów. Można zapobiec lub zmodyfikować automatyczne tworzenie tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do klasy. Chociaż interfejs klasy może ułatwić zadanie udostępniania klas zarządzanych do modelu COM, jego użycie jest ograniczone.

> [!CAUTION]
> Przy użyciu interfejsu klasy, zamiast jawnie definiować własne, program może zaskomplikowanić przyszłą wersję klasy zarządzanej. Przed rozpoczęciem korzystania z interfejsu klasy zapoznaj się z poniższymi wskazówkami.

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a>Zdefiniuj jawny interfejs do użycia przez klientów COM zamiast generowania interfejsu klasy.

Ponieważ usługa międzyoperacyjna modelu COM generuje interfejs klasy automatycznie, zmiany po wersji klasy mogą zmieniać układ interfejsu klasy udostępnianego przez środowisko uruchomieniowe języka wspólnego. Ponieważ klienci COM są zwykle Niegotowi do obsługi zmian w układzie interfejsu, są przerywane, jeśli zmienisz układ elementu członkowskiego klasy.

Te wytyczne wzmacniają, że interfejsy udostępniane klientom COM muszą pozostać niezmienione. Aby zmniejszyć ryzyko przerwania klientów COM przez przypadkowe zmianę kolejności układu interfejsu, Izoluj wszystkie zmiany do klasy z układu interfejsu, jawnie definiując interfejsy.

Użyj **ClassInterfaceAttribute** , aby rozprowadzić automatyczne generowanie interfejsu klasy i zaimplementować jawny interfejs dla klasy, jak pokazano w poniższym fragmencie kodu:

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

Wartość **ClassInterfaceType. None** uniemożliwia generowanie interfejsu klasy, gdy metadane klasy są eksportowane do biblioteki typów. W poprzednim przykładzie klienci COM mogą uzyskać dostęp do `LoanApp` klasy tylko za pomocą `IExplicit` interfejsu.

### <a name="avoid-caching-dispatch-identifiers-dispids"></a>Unikaj buforowania identyfikatorów wysyłania (identyfikatory spId)

Korzystanie z interfejsu klasy jest akceptowalną opcją dla klientów obsługujących skrypty, klienci Microsoft Visual Basic 6,0 lub dowolny klient z późnym wiązaniem, który nie buforuje identyfikatorów spId elementów członkowskich interfejsu. Identyfikatory spId identyfikują elementy członkowskie interfejsu, aby umożliwić późne wiązanie.

Dla interfejsu klasy generowanie identyfikatorów spId opiera się na pozycji elementu członkowskiego w interfejsie. Jeśli zmienisz kolejność elementu członkowskiego i wyeksportusz klasę do biblioteki typów, zmienisz identyfikatory spId wygenerowane w interfejsie klasy.

Aby uniknąć przerywania klientów z późnym wiązaniem modelu COM podczas korzystania z interfejsu klasy, Zastosuj **ClassInterfaceAttribute** z wartością **ClassInterfaceType. autowysyłania** . Ta wartość implementuje interfejs klasy tylko do wysyłania, ale pomija opis interfejsu z biblioteki typów. Bez opisu interfejsu klienci nie mogą buforować identyfikatorów spId w czasie kompilacji. Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartość atrybutu jawnie.

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

Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, klienci COM mogą wywołać metodę **IDispatch. GetIDsOfNames**. Aby wywołać metodę w interfejsie, Przekaż zwracany identyfikator DispId jako argument do elementu **IDispatch. Invoke**.

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a>Ogranicz przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.

Podwójne interfejsy umożliwiają wczesne i późne wiązanie do członków interfejsu przez klientów COM. W czasie projektowania i podczas testowania może okazać się przydatne, aby ustawić interfejs klasy na podwójny. W przypadku klasy zarządzanej (i jej klas podstawowych), które nigdy nie będą modyfikowane, ta opcja jest również akceptowalna. We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójny.

Automatycznie wygenerowany podwójny interfejs może być odpowiedni w rzadkich przypadkach; jednak często tworzy złożoność związaną z wersją. Na przykład klienci COM korzystający z interfejsu klasy klasy pochodnej mogą łatwo przerwać od zmian w klasie bazowej. Gdy strona trzecia udostępnia klasę bazową, układ interfejsu klasy jest poza formantem. W przeciwieństwie do interfejsu tylko do wysyłania, podwójny interfejs (**ClassInterfaceType. AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej bibliotece typów. Ten opis zachęca klientów z późnym wiązaniem do buforowania identyfikatorów spId w czasie kompilacji.

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a>Upewnij się, że wszystkie powiadomienia o zdarzeniach COM są opóźnione.

Domyślnie informacje o typie COM są osadzone bezpośrednio w zarządzanych zestawach, co eliminuje konieczność stosowania podstawowych zestawów międzyoperacyjnych (zestawów PIA). Jednak jedno z ograniczeń informacji o typie osadzonym polega na tym, że nie obsługuje on dostarczania powiadomień o zdarzeniach COM przez wczesne wywołania tablic wirtualnych, ale obsługuje tylko wywołania `IDispatch::Invoke` z późnym wiązaniem.

Jeśli aplikacja wymaga wczesnych wywołań metod interfejsu zdarzenia COM, można ustawić właściwość **Osadź typy** współdziałania w programie Visual Studio do `true`, lub dołączyć następujący element w pliku projektu:

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
