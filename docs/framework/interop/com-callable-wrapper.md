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
ms.openlocfilehash: b8e2cab36c1dd990a1bf848067e7ae81baeb9ed8
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57355054"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="141dd-102">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="141dd-102">COM Callable Wrapper</span></span>

<span data-ttu-id="141dd-103">Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="141dd-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="141dd-104">Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="141dd-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="141dd-105">Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług.</span><span class="sxs-lookup"><span data-stu-id="141dd-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="141dd-106">Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew.</span><span class="sxs-lookup"><span data-stu-id="141dd-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="141dd-107">Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="141dd-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="141dd-108">Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.</span><span class="sxs-lookup"><span data-stu-id="141dd-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

<span data-ttu-id="141dd-109">![Wywoływana otoka COM](./media/ccw.gif "ccw") uzyskiwania dostępu do obiektów platformy .NET za pomocą wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="141dd-109">![COM callable wrapper](./media/ccw.gif "ccw") Accessing .NET objects through COM callable wrapper</span></span>

<span data-ttu-id="141dd-110">Otoki wywoływane z modelu COM są niewidoczne dla innych klas uruchomionych w środowisku .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="141dd-110">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="141dd-111">Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.</span><span class="sxs-lookup"><span data-stu-id="141dd-111">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="141dd-112">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="141dd-112">Object Identity</span></span>

<span data-ttu-id="141dd-113">Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="141dd-113">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="141dd-114">Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.</span><span class="sxs-lookup"><span data-stu-id="141dd-114">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="141dd-115">Okres istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="141dd-115">Object Lifetime</span></span>

<span data-ttu-id="141dd-116">W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="141dd-116">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="141dd-117">Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="141dd-117">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="141dd-118">Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="141dd-118">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="141dd-119">Symulowanie interfejsów COM</span><span class="sxs-lookup"><span data-stu-id="141dd-119">Simulating COM interfaces</span></span>

<span data-ttu-id="141dd-120">CCW uwidacznia wszystkie publiczne, interfejsach widocznych dla modelu COM, typy danych i wartości zwracane do klientów modelu COM w sposób, który jest zgodny z modelu COM wymuszania interakcji z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="141dd-120">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="141dd-121">Klient modelu COM wywoływanie metod dla obiektu .NET Framework jest taka sama jak wywoływanie metod na obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="141dd-121">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="141dd-122">Aby utworzyć to bezproblemowe podejście, CCW są produkowane tradycyjnych interfejsów COM, takich jak **IUnknown** i **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="141dd-122">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="141dd-123">Jak pokazano na poniższej ilustracji, CCW zachowuje jedno odwołanie obiektu platformy .NET, która je otacza.</span><span class="sxs-lookup"><span data-stu-id="141dd-123">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="141dd-124">Zarówno klient modelu COM, jak i obiektu platformy .NET ze sobą współdziałać za pośrednictwem serwera proxy i klasy zastępczej konstrukcja CCW.</span><span class="sxs-lookup"><span data-stu-id="141dd-124">Both the COM client and .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

<span data-ttu-id="141dd-125">![Interfejsy modelu COM](./media/ccwwithinterfaces.gif "ccwwithinterfaces") interfejsów COM i wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="141dd-125">![COM interfaces](./media/ccwwithinterfaces.gif "ccwwithinterfaces") COM interfaces and the COM callable wrapper</span></span>

<span data-ttu-id="141dd-126">Oprócz udostępnianie interfejsów, które są jawnie implementowane przez klasy w środowisku zarządzanym, .NET Framework dostarcza implementacji interfejsów COM, wymienione w poniższej tabeli w imieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="141dd-126">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="141dd-127">Klasa platformy .NET można zastąpić domyślne zachowanie, podając własną implementację tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="141dd-127">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="141dd-128">Środowisko uruchomieniowe zawsze zapewnia jednak wykonania na **IUnknown** i **IDispatch** interfejsów.</span><span class="sxs-lookup"><span data-stu-id="141dd-128">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="141dd-129">Interface</span><span class="sxs-lookup"><span data-stu-id="141dd-129">Interface</span></span>|<span data-ttu-id="141dd-130">Opis</span><span class="sxs-lookup"><span data-stu-id="141dd-130">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="141dd-131">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="141dd-131">**IDispatch**</span></span>|<span data-ttu-id="141dd-132">Udostępnia mechanizm późnym wiązaniem do typu.</span><span class="sxs-lookup"><span data-stu-id="141dd-132">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="141dd-133">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="141dd-133">**IErrorInfo**</span></span>|<span data-ttu-id="141dd-134">Zawiera opis tekstowy błędu, źródło, pliku pomocy, Pomoc kontekstowa i identyfikator GUID interfejs który jest zdefiniowany błędu (zawsze **GUID_NULL** dla klas platformy .NET).</span><span class="sxs-lookup"><span data-stu-id="141dd-134">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="141dd-135">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="141dd-135">**IProvideClassInfo**</span></span>|<span data-ttu-id="141dd-136">Umożliwia klientom COM uzyskać dostęp do **ITypeInfo** interfejs implementowany przez klasy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="141dd-136">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|
|<span data-ttu-id="141dd-137">**Interfejs ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="141dd-137">**ISupportErrorInfo**</span></span>|<span data-ttu-id="141dd-138">Umożliwia klientowi COM ustalić, czy obsługuje obiektu zarządzanego **IErrorInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="141dd-138">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="141dd-139">Jeśli tak, ta umożliwia uzyskiwanie wskaźnika do najnowszych obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="141dd-139">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="141dd-140">Wszystkie zarządzane typy obsługi **IErrorInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="141dd-140">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="141dd-141">**ITypeInfo**</span><span class="sxs-lookup"><span data-stu-id="141dd-141">**ITypeInfo**</span></span>|<span data-ttu-id="141dd-142">Zawiera informacje o typie dla klasy, w którym są dokładnie takie same jak informacje o typie utworzony przez Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="141dd-142">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="141dd-143">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="141dd-143">**IUnknown**</span></span>|<span data-ttu-id="141dd-144">Dostarcza implementację standardowa **IUnknown** interfejs, za pomocą którego klient modelu COM zarządza czasem istnienia CCW i umożliwia wymuszanie typów.</span><span class="sxs-lookup"><span data-stu-id="141dd-144">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="141dd-145">Klasa zarządzana oferuje również interfejsów COM, opisanego w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="141dd-145">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="141dd-146">Interface</span><span class="sxs-lookup"><span data-stu-id="141dd-146">Interface</span></span>|<span data-ttu-id="141dd-147">Opis</span><span class="sxs-lookup"><span data-stu-id="141dd-147">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="141dd-148">(\_*Classname*) interfejs klasy</span><span class="sxs-lookup"><span data-stu-id="141dd-148">The (\_*classname*) class interface</span></span>|<span data-ttu-id="141dd-149">Interfejs, udostępniane przez środowisko uruchomieniowe i nie zostały jawnie określone, który przedstawia wszystkich interfejsów publicznych, metod, właściwości i pola, które są jawnie widoczne zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="141dd-149">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="141dd-150">**IConnectionPoint** i **interfejsy IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="141dd-150">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="141dd-151">Interfejs dla obiektów, które źródeł zdarzeń opartych na delegacie (interfejs rejestracji subskrybentów zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="141dd-151">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="141dd-152">**IDispatchEx**</span><span class="sxs-lookup"><span data-stu-id="141dd-152">**IDispatchEx**</span></span>|<span data-ttu-id="141dd-153">Interfejs dostarczony przez środowisko wykonawcze, jeśli klasa implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="141dd-153">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="141dd-154">**IDispatchEx** interfejs jest rozszerzeniem **IDispatch** interfejs, który, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania oraz wielkość liter wywoływanie elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="141dd-154">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="141dd-155">**Interfejs IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="141dd-155">**IEnumVARIANT**</span></span>|<span data-ttu-id="141dd-156">Interfejs dla klasy typ kolekcji, która wylicza obiektów w kolekcji, jeśli klasa implementuje **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="141dd-156">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="141dd-157">Wprowadzenie interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="141dd-157">Introducing the class interface</span></span>

<span data-ttu-id="141dd-158">Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, to interfejs, który udostępnia wszystkie metody publiczne, właściwości, pola i zdarzenia, które jawnie są widoczne dla obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="141dd-158">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="141dd-159">Ten interfejs może być interfejsem podwójna lub tylko do wysyłania.</span><span class="sxs-lookup"><span data-stu-id="141dd-159">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="141dd-160">Interfejs klasy uzyskuje nazwę klasy .NET, poprzedzonej podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="141dd-160">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="141dd-161">Na przykład dla klasy ssak interfejsu klasy jest \_ssak.</span><span class="sxs-lookup"><span data-stu-id="141dd-161">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="141dd-162">Dla klas pochodnych interfejsu klasy udostępnia również metody publiczne, właściwości i pola klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="141dd-162">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="141dd-163">W klasie pochodnej udostępnia również interfejs klasy dla każdej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="141dd-163">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="141dd-164">Na przykład, jeśli klasa ssak rozszerza klasę MammalSuperclass, która sama rozszerza System.Object, udostępnia obiekt .NET do klientów modelu COM, trzy klasy interfejsów o nazwie \_ssak, \_MammalSuperclass, i \_obiektu.</span><span class="sxs-lookup"><span data-stu-id="141dd-164">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="141dd-165">Na przykład rozważmy następujące klasy .NET:</span><span class="sxs-lookup"><span data-stu-id="141dd-165">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="141dd-166">Klient COM może pobrać wskaźnik do interfejsu klasy o nazwie `_Mammal`, który jest opisany w bibliotece typów, [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) narzędzie generuje.</span><span class="sxs-lookup"><span data-stu-id="141dd-166">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="141dd-167">Jeśli `Mammal` klasy zaimplementować jeden lub więcej interfejsów, interfejsy, zostanie wyświetlony w obszarze wspólna.</span><span class="sxs-lookup"><span data-stu-id="141dd-167">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="141dd-168">Generowanie interfejsu klasy jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="141dd-168">Generating the class interface is optional.</span></span> <span data-ttu-id="141dd-169">Domyślnie usługa międzyoperacyjna modelu COM generuje tylko do wysyłania interfejs dla każdej klasy, które są eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="141dd-169">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="141dd-170">Możesz uniemożliwić lub zmodyfikować automatyczne tworzenie tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-170">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="141dd-171">Chociaż interfejs klasy może ułatwić zadań ujawnienia klas zarządzanych dla modelu COM, jego zastosowania są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="141dd-171">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="141dd-172">Za pomocą interfejsu klasy zamiast jawnie definiować własne, skomplikować przyszłych wersji klasy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="141dd-172">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="141dd-173">Przeczytaj poniższe wskazówki przed rozpoczęciem korzystania z interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-173">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="141dd-174">Definicja jawnego interfejsu dla klientów modelu COM do użycia, zamiast generować interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-174">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="141dd-175">Ponieważ usługa międzyoperacyjna modelu COM, które automatycznie generuje interfejs klasy, zmiany po wydaniu wersji do klasy można zmienić układ interfejsu klasy udostępnianych przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="141dd-175">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="141dd-176">Ponieważ klientów modelu COM są zazwyczaj Nieprzygotowane do obsługi zmian w układzie interfejs, dzielą one, jeśli zmienisz układ składowych klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-176">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="141dd-177">Ta wytyczna wzmacnia pojęcia, że interfejsy ujawnione klientom modelu COM musi pozostać nie będzie zmieniana.</span><span class="sxs-lookup"><span data-stu-id="141dd-177">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="141dd-178">Aby zmniejszyć ryzyko przerwanie klientów modelu COM przypadkowo zmiana kolejności układów interfejsu, wyizolować wszystkie zmiany do klasy w układzie interfejsu przez jawne określenie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="141dd-178">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="141dd-179">Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy do implementacji interfejsu jawnego dla tej klasy, co ilustruje poniższy fragment kodu:</span><span class="sxs-lookup"><span data-stu-id="141dd-179">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="141dd-180">**ClassInterfaceType.None** wartość zapobiega interfejsu klasy są generowane, gdy metadanych klas są eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="141dd-180">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="141dd-181">W powyższym przykładzie klienci COM mogą uzyskiwać dostęp `LoanApp` tylko przez klasy `IExplicit` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="141dd-181">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="141dd-182">Należy unikać buforowania identyfikatory wysyłania (DISPID)</span><span class="sxs-lookup"><span data-stu-id="141dd-182">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="141dd-183">Przy użyciu interfejsu klasy. czy dopuszczalne rozwiązanie dla klientów przy użyciu skryptu, Microsoft Visual Basic 6.0 lub klienta z późnym wiązaniem, który nie będzie buforować DISPID członków interfejsów.</span><span class="sxs-lookup"><span data-stu-id="141dd-183">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="141dd-184">DISPID zidentyfikować składowych interfejsu, aby umożliwić późnego wiązania.</span><span class="sxs-lookup"><span data-stu-id="141dd-184">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="141dd-185">Dla interfejsu klasy generowania DISPID opiera się na pozycji elementu członkowskiego w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="141dd-185">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="141dd-186">Jeśli zmiana kolejności elementu członkowskiego i wyeksportować klasy do biblioteki typów, powodują zmianę DISPID, wygenerowane za pomocą interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-186">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="141dd-187">Aby uniknąć przerwanie klientów modelu COM z późnym wiązaniem przy użyciu interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartości.</span><span class="sxs-lookup"><span data-stu-id="141dd-187">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="141dd-188">Ta wartość implementuje interfejs klasy jako tylko do wysyłki, ale pomija opis interfejsu z biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="141dd-188">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="141dd-189">Bez opisu interfejsu klientów są do pamięci podręcznej DISPID na czas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="141dd-189">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="141dd-190">Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartości atrybutu jawnie.</span><span class="sxs-lookup"><span data-stu-id="141dd-190">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="141dd-191">Aby uzyskać identyfikator DispId składowej interfejsu w czasie wykonywania, można wywołać klientów modelu COM **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="141dd-191">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="141dd-192">Aby wywołać metodę interfejsu, należy przekazać zwrócony identyfikator DispId jako argument do **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="141dd-192">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="141dd-193">Ograniczenia przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-193">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="141dd-194">Podwójne interfejsy umożliwiają wczesne i późne powiązania do składowych interfejsu klienci COM.</span><span class="sxs-lookup"><span data-stu-id="141dd-194">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="141dd-195">W czasie projektowania i podczas testowania może być przydatne go ustawić podwójnego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="141dd-195">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="141dd-196">Klasa zarządzana (i jej klasy bazowe), nigdy nie będą modyfikowane, ta opcja jest również dopuszczalne.</span><span class="sxs-lookup"><span data-stu-id="141dd-196">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="141dd-197">We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójne.</span><span class="sxs-lookup"><span data-stu-id="141dd-197">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="141dd-198">Odpowiednie w rzadkich przypadkach; może być automatycznie generowane podwójnego interfejsu jednak częściej tworzy złożoności związane z wersją.</span><span class="sxs-lookup"><span data-stu-id="141dd-198">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="141dd-199">Na przykład Klienci COM za pomocą interfejsu klasy pochodnej klasy łatwo może przerwać ze zmianami do klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="141dd-199">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="141dd-200">Jeśli strona trzecia udostępnia klasę bazową, układ interfejsu klasy jest poza Twoją kontrolą.</span><span class="sxs-lookup"><span data-stu-id="141dd-200">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="141dd-201">Bardziej szczegółowo, w przeciwieństwie do interfejsu tylko do wysyłania podwójnego interfejsu (**ClassInterfaceType.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="141dd-201">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="141dd-202">Opis taki zachęca klientów z późnym wiązaniem do pamięci podręcznej DISPID w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="141dd-202">Such a description encourages late-bound clients to cache DispIds at run time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="141dd-203">Upewnij się, że wszystkie powiadomienia o zdarzeniach modelu COM z późnym wiązaniem.</span><span class="sxs-lookup"><span data-stu-id="141dd-203">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="141dd-204">Domyślnie informacje o typie modelu COM jest osadzony bezpośrednio do zestawów zarządzanych, która eliminuje potrzebę stosowania podstawowych zestawów międzyoperacyjnych (PIA).</span><span class="sxs-lookup"><span data-stu-id="141dd-204">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="141dd-205">Jednak jedną z ograniczenia informacje o typie osadzony jest ona nieobsługiwana dostarczania powiadomień o zdarzeniach COM przez wywołania z wczesnym wiązaniem vtable, ale obsługuje tylko z późnym wiązaniem `IDispatch::Invoke` wywołania.</span><span class="sxs-lookup"><span data-stu-id="141dd-205">However, one of the limitations of embedded type information is that it does not supported delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="141dd-206">Jeśli aplikacja wymaga wywołania wczesnym wiązaniem do metody interfejsu zdarzeń COM, możesz ustawić **Osadź typy współdziałania** właściwości w programie Visual Studio do `true`, lub Uwzględnij następujący element w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="141dd-206">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="141dd-207">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="141dd-207">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="141dd-208">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="141dd-208">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="141dd-209">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="141dd-209">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="141dd-210">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="141dd-210">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="141dd-211">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="141dd-211">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
