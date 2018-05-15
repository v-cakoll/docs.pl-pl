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
---
# <a name="com-callable-wrapper"></a><span data-ttu-id="933c3-102">Wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="933c3-102">COM Callable Wrapper</span></span>
<span data-ttu-id="933c3-103">Gdy klient modelu COM wywołuje obiekt środowiska .NET, środowisko uruchomieniowe języka wspólnego tworzy zarządzany obiekt oraz otokę wywoływaną z modelu COM (CCW) dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="933c3-103">When a COM client calls a .NET object, the common language runtime creates the managed object and a COM callable wrapper (CCW) for the object.</span></span> <span data-ttu-id="933c3-104">Klienci modelu COM nie potrafią się odwoływać bezpośrednio do obiektu środowiska .NET, dlatego używają otoki CCW jako pośrednika umożliwiającego dostęp do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="933c3-104">Unable to reference a .NET object directly, COM clients use the CCW as a proxy for the managed object.</span></span>  
  
 <span data-ttu-id="933c3-105">Środowisko uruchomieniowe tworzy dla obiektu zarządzanego dokładnie jedną otokę CCW, niezależnie od liczby klientów modelu COM żądających jego usług.</span><span class="sxs-lookup"><span data-stu-id="933c3-105">The runtime creates exactly one CCW for a managed object, regardless of the number of COM clients requesting its services.</span></span> <span data-ttu-id="933c3-106">Jak pokazano na poniższej ilustracji, wielu klientów modelu COM może zawierać odwołanie do otoki CCW, która udostępnia interfejs INew.</span><span class="sxs-lookup"><span data-stu-id="933c3-106">As the following illustration shows, multiple COM clients can hold a reference to the CCW that exposes the INew interface.</span></span> <span data-ttu-id="933c3-107">Z kolei otoka CCW zawiera jedno odwołanie do obiektu zarządzanego, który implementuje interfejs i podlega działaniu modułu odśmiecania pamięci.</span><span class="sxs-lookup"><span data-stu-id="933c3-107">The CCW, in turn, holds a single reference to the managed object that implements the interface and is garbage collected.</span></span> <span data-ttu-id="933c3-108">Klienci modelu COM i środowiska .NET mogą wykonywać żądania do tego samego zarządzanego obiektu równocześnie.</span><span class="sxs-lookup"><span data-stu-id="933c3-108">Both COM and .NET clients can make requests on the same managed object simultaneously.</span></span>  
  
 <span data-ttu-id="933c3-109">![Wywoływana otoka COM](./media/ccw.gif "w lewo")</span><span class="sxs-lookup"><span data-stu-id="933c3-109">![COM callable wrapper](./media/ccw.gif "ccw")</span></span>  
<span data-ttu-id="933c3-110">Uzyskiwanie dostępu do obiektów środowiska .NET przez otokę wywoływaną z modelu COM</span><span class="sxs-lookup"><span data-stu-id="933c3-110">Accessing .NET objects through COM callable wrapper</span></span>  
  
 <span data-ttu-id="933c3-111">Otoki wywoływane z modelu COM są niewidoczne dla innych klas uruchomionych w środowisku .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="933c3-111">COM callable wrappers are invisible to other classes running within the .NET Framework.</span></span> <span data-ttu-id="933c3-112">Ich głównym celem jest kierowanie wywołań między kodem zarządzanym i niezarządzanym. Otoki CCW mogą jednak również zarządzać tożsamościami i okresem istnienia zarządzanych obiektów, które opakowują.</span><span class="sxs-lookup"><span data-stu-id="933c3-112">Their primary purpose is to marshal calls between managed and unmanaged code; however, CCWs also manage the object identity and object lifetime of the managed objects they wrap.</span></span>  
  
## <a name="object-identity"></a><span data-ttu-id="933c3-113">Tożsamość obiektu</span><span class="sxs-lookup"><span data-stu-id="933c3-113">Object Identity</span></span>  
 <span data-ttu-id="933c3-114">Środowisko uruchomieniowe przydziela pamięć obiektowi środowiska .NET ze swojego stosu odśmieconej pamięci, co umożliwia przenoszenie obiektu w pamięci zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="933c3-114">The runtime allocates memory for the .NET object from its garbage-collected heap, which enables the runtime to move the object around in memory as necessary.</span></span> <span data-ttu-id="933c3-115">Natomiast otoce CCW środowisko uruchomieniowe przydziela pamięć ze stosu niepodlegającego odśmiecaniu pamięci, dzięki czemu klienci COM mogą się odwoływać bezpośrednio do otoki.</span><span class="sxs-lookup"><span data-stu-id="933c3-115">In contrast, the runtime allocates memory for the CCW from a noncollected heap, making it possible for COM clients to reference the wrapper directly.</span></span>  
  
## <a name="object-lifetime"></a><span data-ttu-id="933c3-116">Okres istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="933c3-116">Object Lifetime</span></span>  
 <span data-ttu-id="933c3-117">W odróżnieniu od klienta środowiska .NET, którego opakowuje, otoka CCW podlega zliczaniu odwołań w sposób tradycyjny dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="933c3-117">Unlike the .NET client it wraps, the CCW is reference-counted in traditional COM fashion.</span></span> <span data-ttu-id="933c3-118">Gdy liczba odwołań do otoki CCW osiągnie zero, otoka zwalnia swoje odwołanie do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="933c3-118">When the reference count on the CCW reaches zero, the wrapper releases its reference on the managed object.</span></span> <span data-ttu-id="933c3-119">Pamięć zajmowana przez zarządzany obiekt, do którego już nie ma żadnych odwołań, jest odzyskiwana podczas następnego cyklu wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="933c3-119">A managed object with no remaining references is collected during the next garbage-collection cycle.</span></span>  
  
## <a name="simulating-com-interfaces"></a><span data-ttu-id="933c3-120">Symuluje interfejsy modelu COM</span><span class="sxs-lookup"><span data-stu-id="933c3-120">Simulating COM interfaces</span></span>

<span data-ttu-id="933c3-121">CCW przedstawia wszystkie publiczne, interfejsach widocznych dla modelu COM, typy danych i wartości zwracanych do klientów modelu COM w sposób zgodny z modelu COM wymuszania interakcji z interfejsu.</span><span class="sxs-lookup"><span data-stu-id="933c3-121">CCW exposes all public, COM-visible interfaces, data types, and return values to COM clients in a manner that is consistent with COM's enforcement of interface-based interaction.</span></span> <span data-ttu-id="933c3-122">Klient modelu COM wywoływanie metod dla obiektu .NET Framework jest taki sam jak wywoływanie metod obiektów COM.</span><span class="sxs-lookup"><span data-stu-id="933c3-122">For a COM client, invoking methods on a .NET Framework object is identical to invoking methods on a COM object.</span></span>  
  
 <span data-ttu-id="933c3-123">Aby utworzyć takie podejście bezproblemowe, CCW wytwarza tradycyjnych interfejsy modelu COM, takie jak **IUnknown** i **IDispatch**.</span><span class="sxs-lookup"><span data-stu-id="933c3-123">To create this seamless approach, the CCW manufactures traditional COM interfaces, such as **IUnknown** and **IDispatch**.</span></span> <span data-ttu-id="933c3-124">Jak pokazano na poniższej ilustracji, CCW obsługuje jedno odwołanie dla obiektu .NET, który jest zawijany.</span><span class="sxs-lookup"><span data-stu-id="933c3-124">As the following illustration shows, the CCW maintains a single reference on the .NET object that it wraps.</span></span> <span data-ttu-id="933c3-125">Zarówno klient modelu COM i .NET obiektu współdziałać ze sobą za pośrednictwem serwera proxy i stub konstrukcja CCW.</span><span class="sxs-lookup"><span data-stu-id="933c3-125">Both the COM client and .NET object interact with each other through the proxy and stub construction of the CCW.</span></span>  
  
 <span data-ttu-id="933c3-126">![Interfejsy modelu COM](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span><span class="sxs-lookup"><span data-stu-id="933c3-126">![COM interfaces](./media/ccwwithinterfaces.gif "ccwwithinterfaces")</span></span>  
<span data-ttu-id="933c3-127">Interfejsy modelu COM i wywoływana otoka COM</span><span class="sxs-lookup"><span data-stu-id="933c3-127">COM interfaces and the COM callable wrapper</span></span>  
  
 <span data-ttu-id="933c3-128">Oprócz udostępnianie interfejsów, które są jawnie implementowane przez klasę w środowisku zarządzanym, .NET Framework dostarcza implementacji interfejsów COM wymienione w poniższej tabeli w imieniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="933c3-128">In addition to exposing the interfaces that are explicitly implemented by a class in the managed environment, the .NET Framework supplies implementations of the COM interfaces listed in the following table on behalf of the object.</span></span> <span data-ttu-id="933c3-129">Klasy .NET można zastąpić domyślne zachowanie, zapewniając własną implementację tych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="933c3-129">A .NET class can override the default behavior by providing its own implementation of these interfaces.</span></span> <span data-ttu-id="933c3-130">Jednak środowiska uruchomieniowego zawsze udostępnia implementację dla **IUnknown** i **IDispatch** interfejsów.</span><span class="sxs-lookup"><span data-stu-id="933c3-130">However, the runtime always provides the implementation for the **IUnknown** and **IDispatch** interfaces.</span></span>  
  
|<span data-ttu-id="933c3-131">Interface</span><span class="sxs-lookup"><span data-stu-id="933c3-131">Interface</span></span>|<span data-ttu-id="933c3-132">Opis</span><span class="sxs-lookup"><span data-stu-id="933c3-132">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="933c3-133">**Idispatch**</span><span class="sxs-lookup"><span data-stu-id="933c3-133">**Idispatch**</span></span>|<span data-ttu-id="933c3-134">Udostępnia mechanizm późne powiązania do typu.</span><span class="sxs-lookup"><span data-stu-id="933c3-134">Provides a mechanism for late binding to type.</span></span>|  
|<span data-ttu-id="933c3-135">**IerrorInfo**</span><span class="sxs-lookup"><span data-stu-id="933c3-135">**IerrorInfo**</span></span>|<span data-ttu-id="933c3-136">Dostarcza opis tekstowy błąd, źródła pliku pomocy, kontekst pomocy i identyfikator GUID interfejsu, który zdefiniowano błędu (zawsze **GUID_NULL** dla klas .NET).</span><span class="sxs-lookup"><span data-stu-id="933c3-136">Provides a textual description of the error, its source, a Help file, Help context, and the GUID of the interface that defined the error (always **GUID_NULL** for .NET classes).</span></span>|  
|<span data-ttu-id="933c3-137">**IprovideClassInfo**</span><span class="sxs-lookup"><span data-stu-id="933c3-137">**IprovideClassInfo**</span></span>|<span data-ttu-id="933c3-138">Umożliwia klientom uzyskanie dostępu do modelu COM **ITypeInfo** interfejsu implementowanego przez zarządzanej klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-138">Enables COM clients to gain access to the **ITypeInfo** interface implemented by a managed class.</span></span>|  
|<span data-ttu-id="933c3-139">**IsupportErrorInfo**</span><span class="sxs-lookup"><span data-stu-id="933c3-139">**IsupportErrorInfo**</span></span>|<span data-ttu-id="933c3-140">Umożliwia klientowi COM ustalić, czy obiekt zarządzany obsługuje **IErrorInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="933c3-140">Enables a COM client to determine whether the managed object supports the **IErrorInfo** interface.</span></span> <span data-ttu-id="933c3-141">Jeśli tak, umożliwia klientowi uzyskać wskaźnik do najnowszej obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="933c3-141">If so, enables the client to obtain a pointer to the latest exception object.</span></span> <span data-ttu-id="933c3-142">Wszystkie typy Obsługa zarządzanego **IErrorInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="933c3-142">All managed types support the **IErrorInfo** interface.</span></span>|  
|<span data-ttu-id="933c3-143">**ItypeInfo**</span><span class="sxs-lookup"><span data-stu-id="933c3-143">**ItypeInfo**</span></span>|<span data-ttu-id="933c3-144">Zawiera informacje o typie dla klasy, która jest dokładnie taka sama jak informacje o typie utworzonego przez Tlbexp.exe.</span><span class="sxs-lookup"><span data-stu-id="933c3-144">Provides type information for a class that is exactly the same as the type information produced by Tlbexp.exe.</span></span>|  
|<span data-ttu-id="933c3-145">**Iunknown**</span><span class="sxs-lookup"><span data-stu-id="933c3-145">**Iunknown**</span></span>|<span data-ttu-id="933c3-146">Udostępnia implementację standardowe **IUnknown** interfejs, z którym klient modelu COM zarządza czasem istnienia CCW i udostępnia koercja typu.</span><span class="sxs-lookup"><span data-stu-id="933c3-146">Provides the standard implementation of the **IUnknown** interface with which the COM client manages the lifetime of the CCW and provides type coercion.</span></span>|  
  
 <span data-ttu-id="933c3-147">Zarządzanej klasy oferuje również interfejsy modelu COM, opisane w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="933c3-147">A managed class can also provide the COM interfaces described in the following table.</span></span>  
  
|<span data-ttu-id="933c3-148">Interface</span><span class="sxs-lookup"><span data-stu-id="933c3-148">Interface</span></span>|<span data-ttu-id="933c3-149">Opis</span><span class="sxs-lookup"><span data-stu-id="933c3-149">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="933c3-150">(\_*Classname*) interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="933c3-150">The (\_*classname*) class interface</span></span>|<span data-ttu-id="933c3-151">Interfejs, udostępniane przez środowisko uruchomieniowe i nie są jawnie zdefiniowane, która udostępnia wszystkie interfejsy publiczne, metody, właściwości i pola, które są jawnie widoczne obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="933c3-151">Interface, exposed by the runtime and not explicitly defined, that exposes all public interfaces, methods, properties, and fields that are explicitly exposed on a managed object.</span></span>|  
|<span data-ttu-id="933c3-152">**IConnectionPoint** i **IconnectionPointContainer**</span><span class="sxs-lookup"><span data-stu-id="933c3-152">**IConnectionPoint** and **IconnectionPointContainer**</span></span>|<span data-ttu-id="933c3-153">Interfejs dla obiektów, które źródła na podstawie delegata zdarzenia (interfejs do rejestrowania zdarzeń subskrybentów).</span><span class="sxs-lookup"><span data-stu-id="933c3-153">Interface for objects that source delegate-based events (an interface for registering event subscribers).</span></span>|  
|<span data-ttu-id="933c3-154">**IdispatchEx**</span><span class="sxs-lookup"><span data-stu-id="933c3-154">**IdispatchEx**</span></span>|<span data-ttu-id="933c3-155">Interfejs dostarczony przez środowisko uruchomieniowe, jeśli klasa implementuje **IExpando**.</span><span class="sxs-lookup"><span data-stu-id="933c3-155">Interface supplied by the runtime if the class implements **IExpando**.</span></span> <span data-ttu-id="933c3-156">**IDispatchEx** interfejsu jest rozszerzeniem **IDispatch** interfejsu, w odróżnieniu od **IDispatch**, umożliwia wyliczania, dodawania, usuwania i z uwzględnieniem wielkości liter wywoływanie elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="933c3-156">The **IDispatchEx** interface is an extension of the **IDispatch** interface that, unlike **IDispatch**, enables enumeration, addition, deletion, and case-sensitive calling of members.</span></span>|  
|<span data-ttu-id="933c3-157">**Interfejsu IEnumVARIANT**</span><span class="sxs-lookup"><span data-stu-id="933c3-157">**IEnumVARIANT**</span></span>|<span data-ttu-id="933c3-158">Interfejs dla klasy typ kolekcji, która wylicza obiektów w kolekcji, jeśli klasa implementuje **IEnumerable**.</span><span class="sxs-lookup"><span data-stu-id="933c3-158">Interface for collection-type classes, which enumerates the objects in the collection if the class implements **IEnumerable**.</span></span>|  
  
## <a name="introducing-the-class-interface"></a><span data-ttu-id="933c3-159">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="933c3-159">Introducing the class interface</span></span>  
 <span data-ttu-id="933c3-160">Interfejs klasy, która nie jest jawnie zdefiniowany w zarządzanym kodzie, to interfejs, który udostępnia wszystkie metody publiczne, właściwości pola i zdarzenia, które jawnie są dostępne dla obiektu .NET.</span><span class="sxs-lookup"><span data-stu-id="933c3-160">The class interface, which is not explicitly defined in managed code, is an interface that exposes all public methods, properties, fields, and events that are explicitly exposed on the .NET object.</span></span> <span data-ttu-id="933c3-161">Ten interfejs może być interfejsem podwójną lub w trybie tylko do wysyłania.</span><span class="sxs-lookup"><span data-stu-id="933c3-161">This interface can be a dual or dispatch-only interface.</span></span> <span data-ttu-id="933c3-162">Interfejs klasy uzyskuje nazwę klasy .NET, poprzedzone znaku podkreślenia.</span><span class="sxs-lookup"><span data-stu-id="933c3-162">The class interface receives the name of the .NET class itself, preceded by an underscore.</span></span> <span data-ttu-id="933c3-163">Na przykład dla klasy ssak interfejsu klasy jest \_ssak.</span><span class="sxs-lookup"><span data-stu-id="933c3-163">For example, for class Mammal, the class interface is \_Mammal.</span></span>  
  
 <span data-ttu-id="933c3-164">Dla klas pochodnych interfejsu klasy udostępnia również metody publiczne, właściwości i pola klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="933c3-164">For derived classes, the class interface also exposes all public methods, properties, and fields of the base class.</span></span> <span data-ttu-id="933c3-165">Klasy pochodnej udostępnia również interfejs klasy dla każdej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="933c3-165">The derived class also exposes a class interface for each base class.</span></span> <span data-ttu-id="933c3-166">Na przykład, jeśli klasa ssak rozszerza klasę MammalSuperclass, które stanowi rozszerzenie elementu System.Object, ujawnia obiektu .NET dla klientów modelu COM. trzy klasy o nazwie interfejsów \_ssak, \_MammalSuperclass, i \_obiektu.</span><span class="sxs-lookup"><span data-stu-id="933c3-166">For example, if class Mammal extends class MammalSuperclass, which itself extends System.Object, the .NET object exposes to COM clients three class interfaces named \_Mammal, \_MammalSuperclass, and \_Object.</span></span>  
  
 <span data-ttu-id="933c3-167">Na przykład wziąć pod uwagę następujące klasy .NET:</span><span class="sxs-lookup"><span data-stu-id="933c3-167">For example, consider the following .NET class:</span></span>  
  
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
  
 <span data-ttu-id="933c3-168">Klient COM może pobrać wskaźnik do interfejsu klasy o nazwie `_Mammal`, opisanym w bibliotece typów który [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) narzędzie.</span><span class="sxs-lookup"><span data-stu-id="933c3-168">The COM client can obtain a pointer to a class interface named `_Mammal`, which is described in the type library that the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) tool generates.</span></span> <span data-ttu-id="933c3-169">Jeśli `Mammal` klasy zaimplementowane interfejsy co najmniej jednego, interfejsy pojawią się w obszarze klasy coclass.</span><span class="sxs-lookup"><span data-stu-id="933c3-169">If the `Mammal` class implemented one or more interfaces, the interfaces would appear under the coclass.</span></span>  
  
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
  
 <span data-ttu-id="933c3-170">Generowanie interfejsu klasy jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="933c3-170">Generating the class interface is optional.</span></span> <span data-ttu-id="933c3-171">Domyślnie usługa międzyoperacyjna modelu COM generuje tylko do wysyłania interfejs dla każdej klasy wyeksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="933c3-171">By default, COM interop generates a dispatch-only interface for each class you export to a type library.</span></span> <span data-ttu-id="933c3-172">Można zapobiec lub zmodyfikować automatycznego tworzenia tego interfejsu, stosując <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> do swojej klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-172">You can prevent or modify the automatic creation of this interface by applying the <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> to your class.</span></span> <span data-ttu-id="933c3-173">Mimo że interfejsu klasy może ułatwić zadań ujawnienia zarządzanej klasy COM, jego zastosowań są ograniczone.</span><span class="sxs-lookup"><span data-stu-id="933c3-173">Although the class interface can ease the task of exposing managed classes to COM, its uses are limited.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="933c3-174">Za pomocą interfejsu klasy zamiast jawnie definiować własne, skomplikować przyszłych wersji zarządzanej klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-174">Using the class interface, instead of explicitly defining your own, can complicate the future versioning of your managed class.</span></span> <span data-ttu-id="933c3-175">Przeczytaj poniższe wskazówki przed rozpoczęciem korzystania z interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-175">Please read the following guidelines before using the class interface.</span></span>  
  
### <a name="define-an-explicit-interface-for-com-clients-to-use-rather-than-generating-the-class-interface"></a><span data-ttu-id="933c3-176">Zdefiniuj jawnego interfejsu dla klientów modelu COM można użyć zamiast generowania interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-176">Define an explicit interface for COM clients to use rather than generating the class interface.</span></span>  
 <span data-ttu-id="933c3-177">Ponieważ usługa międzyoperacyjna modelu COM, które automatycznie generuje interfejsu klasy, po wersji zmiany do swojej klasy można zmienić układ interfejsu klasy udostępniane przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="933c3-177">Because COM interop generates a class interface automatically, post-version changes to your class can alter the layout of the class interface exposed by the common language runtime.</span></span> <span data-ttu-id="933c3-178">Ponieważ klienci COM są zwykle nieprzygotowany obsługiwać zmiany w układzie interfejs, Przerwij w przypadku zmiany układu elementu członkowskiego klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-178">Since COM clients are typically unprepared to handle changes in the layout of an interface, they break if you change the member layout of the class.</span></span>  
  
 <span data-ttu-id="933c3-179">Niniejsze wytyczne wzmacnia pojęcia, że interfejsy widoczne dla klientów modelu COM musi pozostać niezmienne.</span><span class="sxs-lookup"><span data-stu-id="933c3-179">This guideline reinforces the notion that interfaces exposed to COM clients must remain unchangeable.</span></span> <span data-ttu-id="933c3-180">Aby zmniejszyć ryzyko złamanie klientów modelu COM. przypadkowo zmiana kolejności układ interfejsu, wyizolować wszystkie zmiany do klasy z układu interfejsu przez jawne zdefiniowanie interfejsów.</span><span class="sxs-lookup"><span data-stu-id="933c3-180">To reduce the risk of breaking COM clients by inadvertently reordering the interface layout, isolate all changes to the class from the interface layout by explicitly defining interfaces.</span></span>  
  
 <span data-ttu-id="933c3-181">Użyj **ClassInterfaceAttribute** odłączyć automatyczne generowanie interfejsu klasy i zaimplementować jawnego interfejsu klasy, jak przedstawiono na poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="933c3-181">Use the **ClassInterfaceAttribute** to disengage the automatic generation of the class interface and implement an explicit interface for the class, as the following code fragment shows:</span></span>  
  
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
  
 <span data-ttu-id="933c3-182">**ClassInterfaceType.None** wartość zapobiega interfejsu klasy generowane podczas eksportowania metadanych klasy do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="933c3-182">The **ClassInterfaceType.None** value prevents the class interface from being generated when the class metadata is exported to a type library.</span></span> <span data-ttu-id="933c3-183">W poprzednim przykładzie, mogą uzyskać dostęp klienci COM `LoanApp` tylko za pomocą klasy `IExplicit` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="933c3-183">In the preceding example, COM clients can access the `LoanApp` class only through the `IExplicit` interface.</span></span>  
  
### <a name="avoid-caching-dispatch-identifiers-dispids"></a><span data-ttu-id="933c3-184">Unikaj buforowanie wysyłania identyfikatorów (identyfikator DISPID)</span><span class="sxs-lookup"><span data-stu-id="933c3-184">Avoid caching dispatch identifiers (DispIds)</span></span>
 <span data-ttu-id="933c3-185">Przy użyciu interfejsu klasy jest dopuszczalne opcją klientów przy użyciu skryptu, Microsoft Visual Basic 6.0 lub późnym wiązaniem klienta, który nie będzie buforować identyfikatory DISPID członków interfejsu.</span><span class="sxs-lookup"><span data-stu-id="933c3-185">Using the class interface is an acceptable option for scripted clients, Microsoft Visual Basic 6.0 clients, or any late-bound client that does not cache the DispIds of interface members.</span></span> <span data-ttu-id="933c3-186">Identyfikator DISPID Identyfikowanie członków interfejsu, aby umożliwić późne wiązanie.</span><span class="sxs-lookup"><span data-stu-id="933c3-186">DispIds identify interface members to enable late binding.</span></span>  
  
 <span data-ttu-id="933c3-187">Dla interfejsu klasy generowania identyfikator DISPID opiera się na pozycji elementu członkowskiego w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="933c3-187">For the class interface, generation of DispIds is based on the position of the member in the interface.</span></span> <span data-ttu-id="933c3-188">Jeśli zmiana kolejności elementu członkowskiego i wyeksportować klasie do biblioteki typów, zmieni identyfikator DISPID, generowane w interfejsie klasa.</span><span class="sxs-lookup"><span data-stu-id="933c3-188">If you change the order of the member and export the class to a type library, you will alter the DispIds generated in the class interface.</span></span>  
  
 <span data-ttu-id="933c3-189">Aby uniknąć dzielenia klientów modelu COM. z późnym wiązaniem, korzystając z interfejsu klasy, należy zastosować **ClassInterfaceAttribute** z **ClassInterfaceType.AutoDispatch** wartości.</span><span class="sxs-lookup"><span data-stu-id="933c3-189">To avoid breaking late-bound COM clients when using the class interface, apply the **ClassInterfaceAttribute** with the **ClassInterfaceType.AutoDispatch** value.</span></span> <span data-ttu-id="933c3-190">Ta wartość implementuje interfejs klasy tylko do wysyłania, ale pominięto opis interfejsu z biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="933c3-190">This value implements a dispatch-only class interface, but omits the interface description from the type library.</span></span> <span data-ttu-id="933c3-191">Opis interfejsu — bez klientów występują problemy dotyczące czas kompilacji identyfikator DISPID w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="933c3-191">Without an interface description, clients are unable to cache DispIds at compile time.</span></span> <span data-ttu-id="933c3-192">Jest to domyślny typ interfejsu dla interfejsu klasy, należy zastosować jawnie wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="933c3-192">Although this is the default interface type for the class interface, you can apply the attribute value explicitly.</span></span>  
  
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
  
 <span data-ttu-id="933c3-193">Aby uzyskać identyfikator DispId elementu członkowskiego interfejsu w czasie wykonywania, można wywołać klientów modelu COM. **IDispatch.GetIdsOfNames**.</span><span class="sxs-lookup"><span data-stu-id="933c3-193">To get the DispId of an interface member at run time, COM clients can call **IDispatch.GetIdsOfNames**.</span></span> <span data-ttu-id="933c3-194">Aby wywołać metody w interfejsie, Przekaż DispId zwrócony jako argument do **IDispatch.Invoke**.</span><span class="sxs-lookup"><span data-stu-id="933c3-194">To invoke a method on the interface, pass the returned DispId as an argument to **IDispatch.Invoke**.</span></span>  
  
### <a name="restrict-using-the-dual-interface-option-for-the-class-interface"></a><span data-ttu-id="933c3-195">Ogranicz przy użyciu opcji podwójną interfejsu dla interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-195">Restrict using the dual interface option for the class interface.</span></span>  
 <span data-ttu-id="933c3-196">Podwójne interfejsy Włącz wczesne i późne powiązania elementów członkowskich interfejsu COM klientów.</span><span class="sxs-lookup"><span data-stu-id="933c3-196">Dual interfaces enable early and late binding to interface members by COM clients.</span></span> <span data-ttu-id="933c3-197">W czasie projektowania i podczas testowania może być przydatne go ustawić dwa interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-197">At design time and during testing, you might find it useful to set the class interface to dual.</span></span> <span data-ttu-id="933c3-198">Zarządzanej klasy (i jej klas podstawowych) który nigdy nie będą zmodyfikowane, ta opcja jest również akceptowane.</span><span class="sxs-lookup"><span data-stu-id="933c3-198">For a managed class (and its base classes) that will never be modified, this option is also acceptable.</span></span> <span data-ttu-id="933c3-199">We wszystkich innych przypadkach uniknąć ustawienie podwójnego interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="933c3-199">In all other cases, avoid setting the class interface to dual.</span></span>  
  
 <span data-ttu-id="933c3-200">Interfejs podwójną automatycznie generowanych może być dobrym rozwiązaniem w rzadkich przypadkach; jednak częściej tworzy związanych z wersji złożoności.</span><span class="sxs-lookup"><span data-stu-id="933c3-200">An automatically generated dual interface might be appropriate in rare cases; however, more often it creates version-related complexity.</span></span> <span data-ttu-id="933c3-201">Na przykład klientów modelu COM przy użyciu interfejsu klasy pochodnej klasy łatwo można przerwać ze zmianami do klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="933c3-201">For example, COM clients using the class interface of a derived class can easily break with changes to the base class.</span></span> <span data-ttu-id="933c3-202">W przypadku innych firm udostępnia klasę podstawową, układ interfejsu klasy jest poza formantu.</span><span class="sxs-lookup"><span data-stu-id="933c3-202">When a third party provides the base class, the layout of the class interface is out of your control.</span></span> <span data-ttu-id="933c3-203">Bardziej szczegółowo w przeciwieństwie do interfejsu tylko do wysyłania podwójną interfejsu (**ClassInterface.AutoDual**) zawiera opis interfejsu klasy w wyeksportowanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="933c3-203">Further, unlike a dispatch-only interface, a dual interface (**ClassInterface.AutoDual**) provides a description of the class interface in the exported type library.</span></span> <span data-ttu-id="933c3-204">Opis taki zachęca klientów z późnym wiązaniem do pamięci podręcznej identyfikator DISPID w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="933c3-204">Such a description encourages late-bound clients to cache DispIds at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933c3-205">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="933c3-205">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute>  
 [<span data-ttu-id="933c3-206">Otoki COM</span><span class="sxs-lookup"><span data-stu-id="933c3-206">COM Wrappers</span></span>](com-wrappers.md)  
 [<span data-ttu-id="933c3-207">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="933c3-207">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="933c3-208">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="933c3-208">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="933c3-209">Wywoływana otoka środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="933c3-209">Runtime Callable Wrapper</span></span>](runtime-callable-wrapper.md)