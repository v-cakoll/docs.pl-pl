---
title: Wywoływana otoka COM
description: Gdy klient COM wywołuje obiekt .NET, środowisko CLR tworzy obiekt zarządzany i otokę COM wywołującą dla niego. Klienci modelu COM wywołują otokę dla obiektu.
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
ms.openlocfilehash: c42ea0b5ba4cb01304ceae4ba2d2fc91b629a9b3
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420529"
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="73f16-104">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="73f16-104">COM Callable Wrapper</span></span>

<span data-ttu-id="73f16-105">Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="73f16-105">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="73f16-106">Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="73f16-106">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>

<span data-ttu-id="73f16-107">Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług.</span><span class="sxs-lookup"><span data-stu-id="73f16-107">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="73f16-108">Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew.</span><span class="sxs-lookup"><span data-stu-id="73f16-108">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="73f16-109">Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="73f16-109">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="73f16-110">Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.</span><span class="sxs-lookup"><span data-stu-id="73f16-110">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>

![Wielu klientów COM przechowujących odwołanie do CCW, które uwidacznia INew.](./media/com-callable-wrapper/com-callable-wrapper-clients.gif)

<span data-ttu-id="73f16-112">Wywoływane otoki COM są niewidoczne dla innych klas uruchomionych w środowisku uruchomieniowym .NET.</span><span class="sxs-lookup"><span data-stu-id="73f16-112">COM callable wrappers are invisible to other classes running within the .NET runtime.</span></span> <span data-ttu-id="73f16-113">Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.</span><span class="sxs-lookup"><span data-stu-id="73f16-113">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>

## <a name="object-identity"></a><span data-ttu-id="73f16-114">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="73f16-114">Object Identity</span></span>

<span data-ttu-id="73f16-115">Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="73f16-115">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="73f16-116">Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.</span><span class="sxs-lookup"><span data-stu-id="73f16-116">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>

## <a name="object-lifetime"></a><span data-ttu-id="73f16-117">Okres istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="73f16-117">Object Lifetime</span></span>

<span data-ttu-id="73f16-118">W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="73f16-118">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="73f16-119">Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="73f16-119">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="73f16-120">Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="73f16-120">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>

## <a name="simulating-com-interfaces"></a><span data-ttu-id="73f16-121">Symulowanie interfejsów COM</span><span class="sxs-lookup"><span data-stu-id="73f16-121">Simulating COM interfaces</span></span>

<span data-ttu-id="73f16-122">CCW udostępnia wszystkie publiczne, widoczne dla modelu COM interfejsy, typy danych i zwraca wartości do klientów COM w sposób, który jest zgodny z wymuszeniem interakcji opartej na interfejsie COM.</span><span class="sxs-lookup"><span data-stu-id="73f16-122">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="73f16-123">W przypadku klienta COM wywoływanie metod w obiekcie .NET jest identyczne z wywoływaniem metod obiektu COM.</span><span class="sxs-lookup"><span data-stu-id="73f16-123">For a COM client, invoking methods on a .NET object is identical to invoking methods on a COM object.</span></span>

<span data-ttu-id="73f16-124">Aby utworzyć to bezproblemowe podejście, CCW produkuje tradycyjne interfejsy COM, takie jak **IUnknown** i **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="73f16-124">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="73f16-125">Jak widać na poniższej ilustracji, CCW zachowuje pojedyncze odwołanie do obiektu platformy .NET, który go otacza.</span><span class="sxs-lookup"><span data-stu-id="73f16-125">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="73f16-126">Zarówno klient COM, jak i obiekt .NET współpracują ze sobą za pomocą serwera proxy i klasy zastępczej CCW.</span><span class="sxs-lookup"><span data-stu-id="73f16-126">Both the COM client and the .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>

![Diagram przedstawiający sposób, w jaki CCW produkuje interfejsy COM.](./media/com-callable-wrapper/com-callable-wrapper-interfaces.gif)

<span data-ttu-id="73f16-128">Oprócz ujawniania interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, środowisko uruchomieniowe platformy .NET dostarcza implementacje interfejsów COM wymienionych w poniższej tabeli w imieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="73f16-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET runtime supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="73f16-129">Klasa platformy .NET może zastąpić domyślne zachowanie, dostarczając własną implementację tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="73f16-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="73f16-130">Jednak środowisko uruchomieniowe zawsze zapewnia implementację interfejsów **IUnknown** i **IDispatch** .</span><span class="sxs-lookup"><span data-stu-id="73f16-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>

|<span data-ttu-id="73f16-131">Interfejs</span><span class="sxs-lookup"><span data-stu-id="73f16-131">Interface</span></span>|<span data-ttu-id="73f16-132">Opis</span><span class="sxs-lookup"><span data-stu-id="73f16-132">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="73f16-133">**IDispatch**</span><span class="sxs-lookup"><span data-stu-id="73f16-133">**IDispatch**</span></span>|<span data-ttu-id="73f16-134">Udostępnia mechanizm późnego wiązania do typu.</span><span class="sxs-lookup"><span data-stu-id="73f16-134">Provides a mechanism for late binding to type.</span></span>|
|<span data-ttu-id="73f16-135">**IErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="73f16-135">**IErrorInfo**</span></span>|<span data-ttu-id="73f16-136">Zawiera tekstowy opis błędu, jego źródło, plik pomocy, kontekst pomocy oraz identyfikator GUID interfejsu, który definiuje błąd (zawsze **GUID_NULL** dla klas .NET).</span><span class="sxs-lookup"><span data-stu-id="73f16-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|
|<span data-ttu-id="73f16-137">**IProvideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="73f16-137">**IProvideClassInfo**</span></span>|<span data-ttu-id="73f16-138">Umożliwia klientom COM uzyskiwanie dostępu do interfejsu **Metoda ITypeInfo** zaimplementowanego przez klasę zarządzaną.</span><span class="sxs-lookup"><span data-stu-id="73f16-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span> <span data-ttu-id="73f16-139">Zwraca `COR_E_NOTSUPPORTED` na platformie .NET Core dla typów, które nie zostały zaimportowane z modelu com.</span><span class="sxs-lookup"><span data-stu-id="73f16-139">Returns `COR_E_NOTSUPPORTED` on .NET Core for types not imported from COM.</span></span> |
|<span data-ttu-id="73f16-140">**ISupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="73f16-140">**ISupportErrorInfo**</span></span>|<span data-ttu-id="73f16-141">Umożliwia klientowi COM określenie, czy zarządzany obiekt obsługuje interfejs **IErrorInfo** .</span><span class="sxs-lookup"><span data-stu-id="73f16-141">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="73f16-142">Jeśli tak, program umożliwia klientowi uzyskanie wskaźnika do ostatniego obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="73f16-142">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="73f16-143">Wszystkie typy zarządzane obsługują interfejs **IErrorInfo** .</span><span class="sxs-lookup"><span data-stu-id="73f16-143">All managed types support the **IErrorInfo** interface.</span></span>|
|<span data-ttu-id="73f16-144">**Metoda ITypeInfo** (tylko .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="73f16-144">**ITypeInfo** (.NET Framework Only)</span></span>|<span data-ttu-id="73f16-145">Zapewnia informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie wytwarzane przez Tlbexp. exe.</span><span class="sxs-lookup"><span data-stu-id="73f16-145">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|
|<span data-ttu-id="73f16-146">**IUnknown**</span><span class="sxs-lookup"><span data-stu-id="73f16-146">**IUnknown**</span></span>|<span data-ttu-id="73f16-147">Zapewnia standardową implementację interfejsu **IUnknown** , za pomocą którego klient com zarządza okresem istnienia CCW i zapewnia przekształcenie typu.</span><span class="sxs-lookup"><span data-stu-id="73f16-147">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|

 <span data-ttu-id="73f16-148">Zarządzana Klasa może również udostępniać interfejsy COM opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="73f16-148">A managed class can also provide the COM interfaces described in the following table.</span></span>

|<span data-ttu-id="73f16-149">Interfejs</span><span class="sxs-lookup"><span data-stu-id="73f16-149">Interface</span></span>|<span data-ttu-id="73f16-150">Opis</span><span class="sxs-lookup"><span data-stu-id="73f16-150">Description</span></span>|
|---------------|-----------------|
|<span data-ttu-id="73f16-151">\_Interfejs klasy (*ClassName*)</span><span class="sxs-lookup"><span data-stu-id="73f16-151">The (\_*classname*) class interface</span></span>|<span data-ttu-id="73f16-152">Interfejs, uwidoczniony przez środowisko uruchomieniowe i niejawnie zdefiniowany, który uwidacznia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie uwidocznione w zarządzanym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="73f16-152">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|
|<span data-ttu-id="73f16-153">**IConnectionPoint** i **IConnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="73f16-153">**IConnectionPoint** and **IConnectionPointContainer**</span></span>|<span data-ttu-id="73f16-154">Interfejs dla obiektów, które są źródłem zdarzeń opartych na delegatach (interfejs do rejestrowania subskrybentów zdarzeń).</span><span class="sxs-lookup"><span data-stu-id="73f16-154">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|
|<span data-ttu-id="73f16-155">**IDispatchEx** (tylko .NET Framework)</span><span class="sxs-lookup"><span data-stu-id="73f16-155">**IDispatchEx** (.NET Framework Only)</span></span>|<span data-ttu-id="73f16-156">Interfejs dostarczony przez środowisko uruchomieniowe, jeśli klasa implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="73f16-156">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="73f16-157">Interfejs **IDispatchEx** jest rozszerzeniem interfejsu **IDispatch** , który, w przeciwieństwie do **IDispatch**, włącza Wyliczenie, Dodawanie, usuwanie i uwzględnianie wielkości liter dla elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="73f16-157">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|
|<span data-ttu-id="73f16-158">**IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="73f16-158">**IEnumVARIANT**</span></span>|<span data-ttu-id="73f16-159">Interfejs dla klas typu kolekcji, który wylicza obiekty w kolekcji, jeśli klasa implementuje **interfejs IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="73f16-159">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|

## <a name="introducing-the-class-interface"></a><span data-ttu-id="73f16-160">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="73f16-160">Introducing the class interface</span></span>

<span data-ttu-id="73f16-161">Interfejs klasy, który nie jest jawnie zdefiniowany w kodzie zarządzanym, jest interfejsem, który uwidacznia wszystkie metody publiczne, właściwości, pola i zdarzenia, które są jawnie uwidocznione w obiekcie .NET.</span><span class="sxs-lookup"><span data-stu-id="73f16-161">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="73f16-162">Ten interfejs może być interfejsem o podwójnym lub tylko do wysyłania.</span><span class="sxs-lookup"><span data-stu-id="73f16-162">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="73f16-163">Interfejs klasy odbiera nazwę samej klasy .NET, poprzedzoną podkreśleniem.</span><span class="sxs-lookup"><span data-stu-id="73f16-163">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="73f16-164">Na przykład dla ssaków klasy, interfejs klasy to \_ ssak.</span><span class="sxs-lookup"><span data-stu-id="73f16-164">For example, for class Mammal, the class interface is \_Mammal.</span></span>

<span data-ttu-id="73f16-165">W przypadku klas pochodnych interfejs klasy udostępnia również wszystkie metody publiczne, właściwości i pola klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="73f16-165">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="73f16-166">Klasa pochodna również udostępnia interfejs klasy dla każdej klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="73f16-166">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="73f16-167">Na przykład, jeśli ssak klas rozszerza klasę MammalSuperclass, która sama stanowi rozszerzenie elementu System. Object, obiekt .NET uwidacznia klientom COM trzy interfejsy klasy o nazwie \_ ssak, \_ MammalSuperclass i \_ Object.</span><span class="sxs-lookup"><span data-stu-id="73f16-167">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>

<span data-ttu-id="73f16-168">Rozważmy na przykład następujące klasy .NET:</span><span class="sxs-lookup"><span data-stu-id="73f16-168">For example, consider the following .NET class:</span></span>

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

<span data-ttu-id="73f16-169">Klient COM może uzyskać wskaźnik do interfejsu klasy o nazwie `_Mammal` .</span><span class="sxs-lookup"><span data-stu-id="73f16-169">The COM client can obtain a pointer to a class interface named `_Mammal`.</span></span> <span data-ttu-id="73f16-170">Na .NET Framework można użyć narzędzia [eksportu biblioteki typów (Tlbexp. exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) w celu wygenerowania biblioteki typów zawierającej `_Mammal` definicję interfejsu.</span><span class="sxs-lookup"><span data-stu-id="73f16-170">On .NET Framework, you can use the [Type Library Exporter (Tlbexp.exe)](../../framework/tools/tlbexp-exe-type-library-exporter.md) tool to generate a type library containing the `_Mammal` interface definition.</span></span> <span data-ttu-id="73f16-171">Eksporter biblioteki typów nie jest obsługiwany w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="73f16-171">The Type Library Exporter is not supported on .NET Core.</span></span> <span data-ttu-id="73f16-172">Jeśli `Mammal` Klasa implementuje jeden lub więcej interfejsów, interfejsy pojawią się pod klasą coclass.</span><span class="sxs-lookup"><span data-stu-id="73f16-172">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>

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

<span data-ttu-id="73f16-173">Generowanie interfejsu klasy jest opcjonalne.</span><span class="sxs-lookup"><span data-stu-id="73f16-173">Generating the class interface is optional.</span></span> <span data-ttu-id="73f16-174">Domyślnie usługa międzyoperacyjna modelu COM generuje interfejs tylko do wysyłania dla każdej klasy, która jest eksportowana do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="73f16-174">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="73f16-175">Można zapobiec lub zmodyfikować automatyczne tworzenie tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do klasy.</span><span class="sxs-lookup"><span data-stu-id="73f16-175">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="73f16-176">Chociaż interfejs klasy może ułatwić zadanie udostępniania klas zarządzanych do modelu COM, jego użycie jest ograniczone.</span><span class="sxs-lookup"><span data-stu-id="73f16-176">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>

> [!CAUTION]
> <span data-ttu-id="73f16-177">Przy użyciu interfejsu klasy, zamiast jawnie definiować własne, program może zaskomplikowanić przyszłą wersję klasy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="73f16-177">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="73f16-178">Przed rozpoczęciem korzystania z interfejsu klasy zapoznaj się z poniższymi wskazówkami.</span><span class="sxs-lookup"><span data-stu-id="73f16-178">Please read the following guidelines before using the class interface.</span></span>

### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="73f16-179">Zdefiniuj jawny interfejs do użycia przez klientów COM zamiast generowania interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="73f16-179">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>

<span data-ttu-id="73f16-180">Ponieważ usługa międzyoperacyjna modelu COM generuje interfejs klasy automatycznie, zmiany po wersji klasy mogą zmieniać układ interfejsu klasy udostępnianego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="73f16-180">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="73f16-181">Ponieważ klienci COM są zwykle Niegotowi do obsługi zmian w układzie interfejsu, są przerywane, jeśli zmienisz układ elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="73f16-181">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>

<span data-ttu-id="73f16-182">Te wytyczne wzmacniają, że interfejsy udostępniane klientom COM muszą pozostać niezmienione.</span><span class="sxs-lookup"><span data-stu-id="73f16-182">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="73f16-183">Aby zmniejszyć ryzyko przerwania klientów COM przez przypadkowe zmianę kolejności układu interfejsu, Izoluj wszystkie zmiany do klasy z układu interfejsu, jawnie definiując interfejsy.</span><span class="sxs-lookup"><span data-stu-id="73f16-183">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>

<span data-ttu-id="73f16-184">Użyj **ClassInterfaceAttribute** , aby rozprowadzić automatyczne generowanie interfejsu klasy i zaimplementować jawny interfejs dla klasy, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="73f16-184">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>

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

<span data-ttu-id="73f16-185">Wartość **ClassInterfaceType. None** uniemożliwia generowanie interfejsu klasy, gdy metadane klasy są eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="73f16-185">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="73f16-186">W poprzednim przykładzie klienci COM mogą uzyskać dostęp do `LoanApp` klasy tylko za pomocą `IExplicit` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="73f16-186">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>

### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="73f16-187">Unikaj buforowania identyfikatorów wysyłania (identyfikatory spId)</span><span class="sxs-lookup"><span data-stu-id="73f16-187">Avoid caching dispatch identifiers (DispIds)</span></span>

<span data-ttu-id="73f16-188">Korzystanie z interfejsu klasy jest akceptowalną opcją dla klientów obsługujących skrypty, klienci Microsoft Visual Basic 6,0 lub dowolny klient z późnym wiązaniem, który nie buforuje identyfikatorów spId elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="73f16-188">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="73f16-189">Identyfikatory spId identyfikują elementy członkowskie interfejsu, aby umożliwić późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="73f16-189">DispIds identify interface members to enable late binding.</span></span>

<span data-ttu-id="73f16-190">Dla interfejsu klasy generowanie identyfikatorów spId opiera się na pozycji elementu członkowskiego w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="73f16-190">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="73f16-191">Jeśli zmienisz kolejność elementu członkowskiego i wyeksportusz klasę do biblioteki typów, zmienisz identyfikatory spId wygenerowane w interfejsie klasy.</span><span class="sxs-lookup"><span data-stu-id="73f16-191">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>

<span data-ttu-id="73f16-192">Aby uniknąć przerywania klientów z późnym wiązaniem modelu COM podczas korzystania z interfejsu klasy, Zastosuj **ClassInterfaceAttribute** z wartością **ClassInterfaceType. autowysyłania** .</span><span class="sxs-lookup"><span data-stu-id="73f16-192">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="73f16-193">Ta wartość implementuje interfejs klasy tylko do wysyłania, ale pomija opis interfejsu z biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="73f16-193">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="73f16-194">Bez opisu interfejsu klienci nie mogą buforować identyfikatorów spId w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="73f16-194">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="73f16-195">Chociaż jest to domyślny typ interfejsu dla interfejsu klasy, można zastosować wartość atrybutu jawnie.</span><span class="sxs-lookup"><span data-stu-id="73f16-195">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>

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

<span data-ttu-id="73f16-196">Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, klienci COM mogą wywołać metodę **IDispatch. GetIDsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="73f16-196">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="73f16-197">Aby wywołać metodę w interfejsie, Przekaż zwracany identyfikator DispId jako argument do elementu **IDispatch. Invoke**.</span><span class="sxs-lookup"><span data-stu-id="73f16-197">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>

### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="73f16-198">Ogranicz przy użyciu opcji podwójnego interfejsu dla interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="73f16-198">Restrict using the dual interface option for the class interface.</span></span>

<span data-ttu-id="73f16-199">Podwójne interfejsy umożliwiają wczesne i późne wiązanie do członków interfejsu przez klientów COM.</span><span class="sxs-lookup"><span data-stu-id="73f16-199">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="73f16-200">W czasie projektowania i podczas testowania może okazać się przydatne, aby ustawić interfejs klasy na podwójny.</span><span class="sxs-lookup"><span data-stu-id="73f16-200">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="73f16-201">W przypadku klasy zarządzanej (i jej klas podstawowych), które nigdy nie będą modyfikowane, ta opcja jest również akceptowalna.</span><span class="sxs-lookup"><span data-stu-id="73f16-201">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="73f16-202">We wszystkich innych przypadkach należy unikać ustawiania interfejsu klasy na podwójny.</span><span class="sxs-lookup"><span data-stu-id="73f16-202">In all other cases, avoid setting the class interface to dual.</span></span>

<span data-ttu-id="73f16-203">Automatycznie wygenerowany podwójny interfejs może być odpowiedni w rzadkich przypadkach; jednak często tworzy złożoność związaną z wersją.</span><span class="sxs-lookup"><span data-stu-id="73f16-203">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="73f16-204">Na przykład klienci COM korzystający z interfejsu klasy klasy pochodnej mogą łatwo przerwać od zmian w klasie bazowej.</span><span class="sxs-lookup"><span data-stu-id="73f16-204">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="73f16-205">Gdy strona trzecia udostępnia klasę bazową, układ interfejsu klasy jest poza formantem.</span><span class="sxs-lookup"><span data-stu-id="73f16-205">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="73f16-206">W przeciwieństwie do interfejsu tylko do wysyłania, podwójny interfejs (**ClassInterfaceType. AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="73f16-206">Further, unlike a dispatch-only interface, a dual interface (**ClassInterfaceType.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="73f16-207">Ten opis zachęca klientów z późnym wiązaniem do buforowania identyfikatorów spId w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="73f16-207">Such a description encourages late-bound clients to cache DispIds at compile time.</span></span>

### <a name="ensure-that-all-com-event-notifications-are-late-bound"></a><span data-ttu-id="73f16-208">Upewnij się, że wszystkie powiadomienia o zdarzeniach COM są opóźnione.</span><span class="sxs-lookup"><span data-stu-id="73f16-208">Ensure that all COM event notifications are late-bound.</span></span>

<span data-ttu-id="73f16-209">Domyślnie informacje o typie COM są osadzone bezpośrednio w zarządzanych zestawach, co eliminuje konieczność stosowania podstawowych zestawów międzyoperacyjnych (zestawów PIA).</span><span class="sxs-lookup"><span data-stu-id="73f16-209">By default, COM type information is embedded directly into managed assemblies, which eliminates the need for primary interop assemblies (PIAs).</span></span> <span data-ttu-id="73f16-210">Jednak jedno z ograniczeń informacji o typie osadzonym polega na tym, że nie obsługuje on dostarczania powiadomień o zdarzeniach COM przez wczesne wywołania tablic wirtualnych, ale obsługuje tylko wywołania z późnym wiązaniem `IDispatch::Invoke` .</span><span class="sxs-lookup"><span data-stu-id="73f16-210">However, one of the limitations of embedded type information is that it does not support delivery of COM event notifications by early-bound vtable calls, but only supports late-bound `IDispatch::Invoke` calls.</span></span>

<span data-ttu-id="73f16-211">Jeśli aplikacja wymaga wczesnych wywołań metod interfejsu zdarzenia COM, można ustawić właściwość **Osadź typy** współdziałania w programie Visual Studio do `true` , lub dołączyć następujący element w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="73f16-211">If your application requires early-bound calls to COM event interface methods, you can set the **Embed Interop Types** property in Visual Studio to `true`, or include the following element in your project file:</span></span>

```xml
<EmbedInteropTypes>True</EmbedInteropTypes>
```

## <a name="see-also"></a><span data-ttu-id="73f16-212">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73f16-212">See also</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>
- [<span data-ttu-id="73f16-213">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="73f16-213">COM Wrappers</span></span>](com-wrappers.md)
- [<span data-ttu-id="73f16-214">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="73f16-214">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="73f16-215">Udostępnianie składników .NET Core modelowi COM</span><span class="sxs-lookup"><span data-stu-id="73f16-215">Exposing .NET Core Components to COM</span></span>](../../core/native-interop/expose-components-to-com.md)
- [<span data-ttu-id="73f16-216">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="73f16-216">Qualifying .NET Types for Interoperation</span></span>](qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="73f16-217">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="73f16-217">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)
