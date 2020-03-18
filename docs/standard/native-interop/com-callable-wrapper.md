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
# <a name="com-callable-wrapper"></a><span data-ttu-id="a35df-102">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="a35df-102">COM Callable Wrapper</span></span>

<span data-ttu-id="a35df-103">Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a35df-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="a35df-104">Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a35df-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="a35df-105">Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług.</span><span class="sxs-lookup"><span data-stu-id="a35df-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="a35df-106">Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew.</span><span class="sxs-lookup"><span data-stu-id="a35df-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="a35df-107">Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a35df-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="a35df-108">Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.</span><span class="sxs-lookup"><span data-stu-id="a35df-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Wielu klientów COM posiadających odwołanie do CCW, który udostępnia INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="a35df-110">Otoki wywoływane przez COM są niewidoczne dla innych klas działających w czasie wykonywania .NET.</span><span class="sxs-lookup"><span data-stu-id="a35df-110">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="a35df-111">Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.</span><span class="sxs-lookup"><span data-stu-id="a35df-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="a35df-112">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="a35df-112">Object Identity</span></span>

<span data-ttu-id="a35df-113">Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="a35df-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="a35df-114">Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.</span><span class="sxs-lookup"><span data-stu-id="a35df-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="a35df-115">Okres istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="a35df-115">Object Lifetime</span></span>

<span data-ttu-id="a35df-116">W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="a35df-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="a35df-117">Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="a35df-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="a35df-118">Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a35df-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="a35df-119">Symulowanie interfejsów COM</span><span class="sxs-lookup"><span data-stu-id="a35df-119">Simulating COM interfaces</span></span>

<span data-ttu-id="a35df-120">CCW udostępnia wszystkie publiczne, widoczne dla modelu COM interfejsy, typy danych i zwracanie wartości klientom COM w sposób zgodny z wymuszaniem interakcji opartych na interfejsie przez COM.</span><span class="sxs-lookup"><span data-stu-id="a35df-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="a35df-121">Dla klienta COM wywoływanie metod na obiekcie .NET jest identyczne z wywoływanie m.in.</span><span class="sxs-lookup"><span data-stu-id="a35df-121">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="a35df-122">Aby utworzyć to podejście bez szwu, CCW produkuje tradycyjne interfejsy COM, takie jak **IUnknown** i **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="a35df-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="a35df-123">Jak pokazano na poniższej ilustracji, CCW utrzymuje pojedyncze odwołanie na .NET obiektu, który jest zawijany.</span><span class="sxs-lookup"><span data-stu-id="a35df-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="a35df-124">Zarówno klient COM, jak i obiekt .NET współdziałają ze sobą za pośrednictwem serwera proxy i konstrukcji skrótowej CCW.</span><span class="sxs-lookup"><span data-stu-id="a35df-124">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagram, który pokazuje, jak CCW produkuje interfejsy COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="a35df-126">Oprócz ujawniania interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, środowisko wykonawcze .NET dostarcza implementacje interfejsów COM wymienionych w poniższej tabeli w imieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="a35df-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="a35df-127">Klasa .NET można zastąpić zachowanie domyślne, zapewniając własną implementację tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="a35df-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="a35df-128">Jednak czas wykonywania zawsze zapewnia implementację dla **interfejsów IUnknown** i **IDispatch.**</span><span class="sxs-lookup"><span data-stu-id="a35df-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="a35df-129">Interface</span><span class="sxs-lookup"><span data-stu-id="a35df-129">Interface</span></span>|<span data-ttu-id="a35df-130">Opis</span><span class="sxs-lookup"><span data-stu-id="a35df-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a35df-131">**Idispatch**</span><span class="sxs-lookup"><span data-stu-id="a35df-131">**IDispatch**</span></span>|<span data-ttu-id="a35df-132">Zapewnia mechanizm późnego wiązania typu.</span><span class="sxs-lookup"><span data-stu-id="a35df-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="a35df-133">**Ierrorinfo**</span><span class="sxs-lookup"><span data-stu-id="a35df-133">**IErrorInfo**</span></span>|<span data-ttu-id="a35df-134">Zawiera tekstowy opis błędu, jego źródła, pliku Pomocy, kontekstu Pomocy i identyfikatora GUID interfejsu, który zdefiniował błąd (zawsze **GUID_NULL** dla klas .NET).</span><span class="sxs-lookup"><span data-stu-id="a35df-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="a35df-135">**IProvideClassInfo (IProvideClassInfo)**</span><span class="sxs-lookup"><span data-stu-id="a35df-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="a35df-136">Umożliwia klientom COM uzyskanie dostępu do interfejsu **ITypeInfo** zaimplementowanego przez klasę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="a35df-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="a35df-137">Zwraca `COR_E_NOTSUPPORTED` wartość programu .NET Core dla typów, które nie są importowane z com.</span><span class="sxs-lookup"><span data-stu-id="a35df-137">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="a35df-138">**Isupporterrorinfo**</span><span class="sxs-lookup"><span data-stu-id="a35df-138">**ISupportErrorInfo**</span></span>|<span data-ttu-id="a35df-139">Umożliwia klientowi COM określenie, czy obiekt zarządzany obsługuje interfejs **IErrorInfo.**</span><span class="sxs-lookup"><span data-stu-id="a35df-139">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="a35df-140">Jeśli tak, umożliwia klientowi uzyskanie wskaźnika do najnowszego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a35df-140">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="a35df-141">Wszystkie typy zarządzane obsługują interfejs **IErrorInfo.**</span><span class="sxs-lookup"><span data-stu-id="a35df-141">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="a35df-142">**ITypeInfo** (tylko struktura.NET)</span><span class="sxs-lookup"><span data-stu-id="a35df-142">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="a35df-143">Zawiera informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie produkowane przez Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="a35df-143">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="a35df-144">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="a35df-144">**IUnknown**</span></span>|<span data-ttu-id="a35df-145">Zapewnia standardową implementację interfejsu **IUnknown,** z którym klient COM zarządza okresem istnienia CCW i zapewnia typ przymusu.</span><span class="sxs-lookup"><span data-stu-id="a35df-145">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="a35df-146">Klasa zarządzana może również zapewnić interfejsy COM opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a35df-146">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="a35df-147">Interface</span><span class="sxs-lookup"><span data-stu-id="a35df-147">Interface</span></span>|<span data-ttu-id="a35df-148">Opis</span><span class="sxs-lookup"><span data-stu-id="a35df-148">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="a35df-149">Interfejs\_klasy *(classname)*</span><span class="sxs-lookup"><span data-stu-id="a35df-149">The (\_*classname*) class interface</span></span>|<span data-ttu-id="a35df-150">Interfejs, udostępniane przez program runtime i nie jawnie zdefiniowane, który udostępnia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie widoczne na obiekcie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="a35df-150">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="a35df-151">**IConnectionPoint** i **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="a35df-151">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="a35df-152">Interfejs dla obiektów, które źródło zdarzeń opartych na delegowaniu (interfejs do rejestrowania subskrybentów zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="a35df-152">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="a35df-153">**IDispatchEx** (tylko platforma.NET)</span><span class="sxs-lookup"><span data-stu-id="a35df-153">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="a35df-154">Interfejs dostarczany przez program runtime, jeśli klasa implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="a35df-154">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="a35df-155">Interfejs **IDispatchEx** jest rozszerzeniem interfejsu **IDispatch,** które w przeciwieństwie do **IDispatch**umożliwia wyliczanie, dodawanie, usuwanie i wywoływanie elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="a35df-155">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="a35df-156">**Ienumvariant**</span><span class="sxs-lookup"><span data-stu-id="a35df-156">**IEnumVARIANT**</span></span>|<span data-ttu-id="a35df-157">Interfejs dla klas typu kolekcji, który wylicza obiekty w kolekcji, jeśli klasa implementuje **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="a35df-157">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="a35df-158">Przedstawiamy interfejs klasy</span><span class="sxs-lookup"><span data-stu-id="a35df-158">Introducing the class interface</span></span>

<span data-ttu-id="a35df-159">Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, jest interfejsem, który udostępnia wszystkie metody publiczne, właściwości, pola i zdarzenia, które są jawnie widoczne w obiekcie .NET.</span><span class="sxs-lookup"><span data-stu-id="a35df-159">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="a35df-160">Ten interfejs może być interfejsem dual lub dispatch-only.</span><span class="sxs-lookup"><span data-stu-id="a35df-160">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="a35df-161">Interfejs klasy odbiera nazwę samej klasy .NET, poprzedzoną podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="a35df-161">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="a35df-162">Na przykład dla klasy Ssak, \_interfejs klasy jest Ssak.</span><span class="sxs-lookup"><span data-stu-id="a35df-162">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="a35df-163">Dla klas pochodnych interfejs klasy udostępnia również wszystkie metody publiczne, właściwości i pola klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a35df-163">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="a35df-164">Klasa pochodna udostępnia również interfejs klasy dla każdej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a35df-164">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="a35df-165">Na przykład jeśli klasa MammalSuperclass, która sama rozszerza System.Object, obiekt .NET udostępnia klientom COM trzy \_interfejsy \_klas o nazwie \_Mammal, MammalSuperclass i Object.</span><span class="sxs-lookup"><span data-stu-id="a35df-165">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="a35df-166">Rozważmy na przykład następującą klasę .NET:</span><span class="sxs-lookup"><span data-stu-id="a35df-166">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="a35df-167">Klient COM może uzyskać wskaźnik do `_Mammal`interfejsu klasy o nazwie .</span><span class="sxs-lookup"><span data-stu-id="a35df-167">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="a35df-168">W platformie .NET Framework można użyć narzędzia [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) do wygenerowania biblioteki typów zawierającej definicję `_Mammal` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a35df-168">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="a35df-169">Eksporter biblioteki typów nie jest obsługiwany w usłudze .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a35df-169">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="a35df-170">Jeśli `Mammal` klasa zaimplementowana jeden lub więcej interfejsów, interfejsy będą wyświetlane w ramach koklasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-170">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="a35df-171">Generowanie interfejsu klasy jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="a35df-171">Generating the class interface is optional.</span></span> <span data-ttu-id="a35df-172">Domyślnie współdziałania COM generuje interfejs tylko do wysyłki dla każdej klasy eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a35df-172">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="a35df-173">Można zapobiec lub zmodyfikować automatyczne tworzenie <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> tego interfejsu, stosując do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-173">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="a35df-174">Mimo że interfejs klasy może ułatwić zadanie ujawniania zarządzanych klas do com, jego zastosowania są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="a35df-174">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="a35df-175">Przy użyciu interfejsu klasy, zamiast jawnie definiowania własnych, może skomplikować przyszłe przechowywanie wersji klasy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="a35df-175">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="a35df-176">Przed użyciem interfejsu klasy należy zapoznać się z poniższymi wskazówkami.</span><span class="sxs-lookup"><span data-stu-id="a35df-176">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="a35df-177">Zdefiniuj jawny interfejs dla klientów COM do użycia, a nie generowania interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-177">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="a35df-178">Ponieważ com interop generuje interfejs klasy automatycznie, zmiany po wersji do klasy można zmienić układ interfejsu klasy udostępniane przez wspólny język w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a35df-178">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="a35df-179">Ponieważ klienci COM są zazwyczaj nieprzygotowani do obsługi zmian w układzie interfejsu, przerywają, jeśli zmienisz układ elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-179">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="a35df-180">Ta wytyczna wzmacnia przekonanie, że interfejsy udostępniane klientom COM muszą pozostać niezmienne.</span><span class="sxs-lookup"><span data-stu-id="a35df-180">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="a35df-181">Aby zmniejszyć ryzyko przerwania klientów COM przez nieumyślne zmianę kolejności układu interfejsu, wyizoluj wszystkie zmiany w klasie od układu interfejsu, jawnie definiując interfejsy.</span><span class="sxs-lookup"><span data-stu-id="a35df-181">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="a35df-182">Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy i zaimplementować jawny interfejs dla klasy, jak pokazano następujący fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="a35df-182">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="a35df-183">**ClassInterfaceType.None** wartość uniemożliwia interfejs klasy są generowane, gdy metadane klasy jest eksportowany do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a35df-183">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="a35df-184">W poprzednim przykładzie klienci COM mogą `LoanApp` uzyskać dostęp `IExplicit` do klasy tylko za pośrednictwem interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a35df-184">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="a35df-185">Unikaj buforowania identyfikatorów wysyłki (DispIds)</span><span class="sxs-lookup"><span data-stu-id="a35df-185">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="a35df-186">Korzystanie z interfejsu klasy jest akceptowalną opcją dla klientów skryptowych, klientów programu Microsoft Visual Basic 6.0 lub dowolnego klienta z późnym wiązaniem, który nie buforuje identyfikatorów identyfikatorów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a35df-186">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="a35df-187">Identyfikatory dispIds zidentyfikować elementy członkowskie interfejsu, aby włączyć późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="a35df-187">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="a35df-188">Dla interfejsu klasy generacji DispIds opiera się na pozycji elementu członkowskiego w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="a35df-188">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="a35df-189">Jeśli zmienisz kolejność elementu członkowskiego i wyeksportujesz klasę do biblioteki typów, zmienisz identyfikatory DispIds wygenerowane w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-189">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="a35df-190">Aby uniknąć przerywania klientów COM z późnym wiązaniem podczas korzystania z interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartość.</span><span class="sxs-lookup"><span data-stu-id="a35df-190">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="a35df-191">Ta wartość implementuje interfejs klasy tylko do wysyłki, ale pomija opis interfejsu z biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="a35df-191">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="a35df-192">Bez opisu interfejsu klienci nie mogą buforować identyfikatorów DispIds w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a35df-192">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="a35df-193">Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartość atrybutu jawnie.</span><span class="sxs-lookup"><span data-stu-id="a35df-193">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="a35df-194">Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, klienci COM można wywołać **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="a35df-194">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="a35df-195">Aby wywołać metodę w interfejsie, przekazać zwrócony DispId jako argument **do IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="a35df-195">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="a35df-196">Ogranicz przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="a35df-196">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="a35df-197">Dwa interfejsy umożliwiają wczesne i późne wiązanie z członkami interfejsu przez klientów COM.</span><span class="sxs-lookup"><span data-stu-id="a35df-197">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="a35df-198">W czasie projektowania i podczas testowania może okazać się przydatne, aby ustawić interfejs klasy na podwójny.</span><span class="sxs-lookup"><span data-stu-id="a35df-198">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="a35df-199">Dla klasy zarządzanej (i jej klas podstawowych), które nigdy nie zostaną zmodyfikowane, ta opcja jest również dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="a35df-199">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="a35df-200">We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójny.</span><span class="sxs-lookup"><span data-stu-id="a35df-200">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="a35df-201">Automatycznie generowany podwójny interfejs może być odpowiedni w rzadkich przypadkach; jednak częściej tworzy złożoność związaną z wersją.</span><span class="sxs-lookup"><span data-stu-id="a35df-201">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="a35df-202">Na przykład klienci COM przy użyciu interfejsu klasy klasy pochodnej można łatwo przerwać ze zmianami do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="a35df-202">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="a35df-203">Gdy strona trzecia zapewnia klasę podstawową, układ interfejsu klasy jest poza kontrolą.</span><span class="sxs-lookup"><span data-stu-id="a35df-203">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="a35df-204">Ponadto, w przeciwieństwie do interfejsu tylko do wysyłki, podwójny interfejs (**ClassInterfaceType.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="a35df-204">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="a35df-205">Taki opis zachęca klientów z późnym wiązaniem do buforowania identyfikatorów DispIds w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a35df-205">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="a35df-206">Upewnij się, że wszystkie powiadomienia o zdarzeniach COM są późne.</span><span class="sxs-lookup"><span data-stu-id="a35df-206">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="a35df-207">Domyślnie informacje o typie COM są osadzone bezpośrednio w zestawach zarządzanych, co eliminuje konieczność stosowania podstawowych zestawów międzyop (PIA).</span><span class="sxs-lookup"><span data-stu-id="a35df-207">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="a35df-208">Jednak jednym z ograniczeń informacji o typie osadzonym jest to, że nie obsługuje dostarczania powiadomień o `IDispatch::Invoke` zdarzeniach COM przez wywołania vtable na początku, ale obsługuje tylko wywołania z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="a35df-208">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="a35df-209">Jeśli aplikacja wymaga wywołań na wczesnym etapie do metod interfejsu zdarzenia COM, można ustawić `true` **Embed Interop Types** właściwość w programie Visual Studio do lub dołączyć następujący element w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="a35df-209">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="a35df-210">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a35df-210">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="a35df-211">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="a35df-211">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="a35df-212">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="a35df-212">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="a35df-213">Udostępnianie składników .NET Core modelowi COM</span><span class="sxs-lookup"><span data-stu-id="a35df-213">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="a35df-214">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="a35df-214">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="a35df-215">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a35df-215">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
