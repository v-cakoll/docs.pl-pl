---
title: Domyślne zachowanie marshalingu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ed306098852e93d43a4055fd1d9b8cf97a01766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="30e1d-102">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="30e1d-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="30e1d-103">Przekazywanie międzyoperacyjne działa w regułach tego dyktować zachowania danych skojarzonych z parametrami metody przesyłanych między zarządzanymi i niezarządzanymi pamięci.</span><span class="sxs-lookup"><span data-stu-id="30e1d-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="30e1d-104">Te wbudowane reguły kontrolowania takich kierowania działań jako przekształcenia typu danych, czy wywoływany można zmienić przekazywania danych i zwracany do obiektu wywołującego te zmiany i w której okolicznościach organizatora zapewnia optymalizacji wydajności.</span><span class="sxs-lookup"><span data-stu-id="30e1d-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="30e1d-105">W tej sekcji wymieniono domyślnych parametrów behawioralnej interop organizowanie usługi.</span><span class="sxs-lookup"><span data-stu-id="30e1d-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="30e1d-106">Stanowi szczegółowe informacje na temat przekazywanie tablic, typów logicznych typu char, delegatów, klas, obiektów, ciągi i struktury.</span><span class="sxs-lookup"><span data-stu-id="30e1d-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e1d-107">Organizowanie typów ogólnych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="30e1d-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="30e1d-108">Aby uzyskać więcej informacji, zobacz [współpracy przy użyciu typów ogólnych](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="30e1d-108">For more information see, [Interoperating Using Generic Types](https://msdn.microsoft.com/library/26b88e03-085b-4b53-94ba-a5a9c709ce58(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="30e1d-109">Zarządzanie pamięcią z organizatora międzyoperacyjne</span><span class="sxs-lookup"><span data-stu-id="30e1d-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="30e1d-110">Organizator międzyoperacyjnego zawsze próbuje zwolnić pamięci przydzielonej przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="30e1d-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="30e1d-111">To zachowanie jest zgodne z zasadami zarządzania pamięci COM, ale różni się od zasad rządzących natywnych języka C++.</span><span class="sxs-lookup"><span data-stu-id="30e1d-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="30e1d-112">Pomyłek mogą wystąpić, jeśli przewidujesz natywnego zachowania C++ (nie pamięci zwalnianie) gdy przy użyciu platformy wywołania, które automatycznie zwalnia pamięć dla wskaźników.</span><span class="sxs-lookup"><span data-stu-id="30e1d-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="30e1d-113">Na przykład wywołanie następującej metody niezarządzane z biblioteki DLL języka C++ nie automatycznie zwolnienia wszystkie pamięci.</span><span class="sxs-lookup"><span data-stu-id="30e1d-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="30e1d-114">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="30e1d-114">Unmanaged signature</span></span>  
  
```  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="30e1d-115">Jednak w przypadku definiowania metodę jako prototyp wywołanie platformy, Zastąp każdego **BSTR** to typ <xref:System.String> wpisz i Wywołaj `MethodOne`, środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="30e1d-116">Zachowanie marshalingu można zmienić za pomocą <xref:System.IntPtr> typy zamiast **ciąg** typów.</span><span class="sxs-lookup"><span data-stu-id="30e1d-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="30e1d-117">Środowisko uruchomieniowe zawsze używa **CoTaskMemFree** metodę, aby zwolnić pamięć.</span><span class="sxs-lookup"><span data-stu-id="30e1d-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="30e1d-118">Jeśli pracujesz z pamięci nie została przydzielona z **CoTaskMemAlloc** metody, należy użyć **IntPtr** i zwolnić pamięć, ręcznie przy użyciu odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="30e1d-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="30e1d-119">Podobnie można uniknąć automatycznego pamięci zwalnianie w sytuacjach, gdy pamięć nigdy nie powinien zwolniona, takie jak w przypadku **GetCommandLine** funkcji Kernel32.dll, która zwraca wskaźnik do pamięci jądra.</span><span class="sxs-lookup"><span data-stu-id="30e1d-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="30e1d-120">Aby uzyskać więcej informacji o zwalnianiu ręcznie pamięci, zobacz [próbki buforów](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="30e1d-120">For details on manually freeing memory, see the [Buffers Sample](http://msdn.microsoft.com/library/e30d36e8-d7c4-4936-916a-8fdbe4d9ffd5(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="30e1d-121">Organizowanie domyślne dotyczące klas</span><span class="sxs-lookup"><span data-stu-id="30e1d-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="30e1d-122">Klasy mogą być organizowany tylko przy użyciu współdziałanie z COM i zawsze są przekazywane jako interfejsy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="30e1d-123">W niektórych przypadkach interfejs używany do organizowania klasy nosi nazwę interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="30e1d-124">Aby dowiedzieć się, jak zastępowanie interfejsu klasy przy użyciu interfejsu wybranych przez użytkownika, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="30e1d-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="30e1d-125">Przekazywanie klas modelowi COM</span><span class="sxs-lookup"><span data-stu-id="30e1d-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="30e1d-126">Po klasie zarządzanej jest przekazywana do modelu COM, międzyoperacyjnego organizatora automatycznie zawijany klasy z serwera proxy modelu COM i przekazuje interfejsu klasy utworzonej przez serwer proxy do wywołania metody COM.</span><span class="sxs-lookup"><span data-stu-id="30e1d-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="30e1d-127">Serwer proxy następnie deleguje wszystkie wywołania interfejsu klasy do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="30e1d-128">Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowana przez klasę.</span><span class="sxs-lookup"><span data-stu-id="30e1d-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="30e1d-129">Serwer proxy takich jak automatycznie implementuje interfejsy **IUnknown** i **IDispatch** imieniu klasy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="30e1d-130">Przekazywanie klas kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="30e1d-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="30e1d-131">Klasy coclass nie są zwykle używane jako argumenty metody w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="30e1d-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="30e1d-132">Zamiast tego domyślnego interfejsu jest zwykle przekazywany zamiast klasy coclass.</span><span class="sxs-lookup"><span data-stu-id="30e1d-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="30e1d-133">Jeśli interfejs zostanie przekazany do kodu zarządzanego, międzyoperacyjnego organizatora jest odpowiedzialny za zawijanie interfejsu z właściwego otoki i przekazywanie otoka zarządzanych metody.</span><span class="sxs-lookup"><span data-stu-id="30e1d-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="30e1d-134">Określanie, które otoki do użycia, może być trudne.</span><span class="sxs-lookup"><span data-stu-id="30e1d-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="30e1d-135">Każde wystąpienie obiektu COM ma otoki jedną, unikatową, niezależnie od tego, jak wiele interfejsów, które implementuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="30e1d-136">Na przykład pojedynczy obiekt COM, który implementuje pięciu różnych interfejsów ma tylko jedną otoki.</span><span class="sxs-lookup"><span data-stu-id="30e1d-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="30e1d-137">Tym samym otoki przedstawia wszystkie interfejsy pięć.</span><span class="sxs-lookup"><span data-stu-id="30e1d-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="30e1d-138">Jeśli są tworzone dwa wystąpienia obiektu COM, są tworzone dwa wystąpienia otoki.</span><span class="sxs-lookup"><span data-stu-id="30e1d-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="30e1d-139">Dla otoki do obsługi tego samego typu w całym cyklu eksploatacji międzyoperacyjnego organizatora musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępniany przez obiekt jest przekazywana organizatora.</span><span class="sxs-lookup"><span data-stu-id="30e1d-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="30e1d-140">Organizator określa obiekt, analizując jednego z interfejsów, które implementuje obiektu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="30e1d-141">Na przykład organizatora Określa, że klasy otoki powinien być używany do opakowywania interfejs, który został przekazany do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="30e1d-142">Po interfejsie najpierw są przekazywane za pośrednictwem organizatora, organizatora sprawdza, czy interfejs pochodzi ze znanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="30e1d-143">To sprawdzanie jest wykonywane w dwóch sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="30e1d-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="30e1d-144">Interfejs jest implementowana przez inny obiekt zarządzany, który został przekazany do modelu COM w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="30e1d-145">Organizator można łatwo zidentyfikować interfejsach udostępnionych przez zarządzanych obiektów i może być zgodna z zarządzanego obiektu, który udostępnia implementację interfejsu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="30e1d-146">Zarządzanego obiektu są następnie przekazywane do metody i nie jest wymagane nie otoki.</span><span class="sxs-lookup"><span data-stu-id="30e1d-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="30e1d-147">Obiekt, który jest już opakowana implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="30e1d-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="30e1d-148">Aby ustalić, czy jest to możliwe, organizator odpytuje obiekt dla jego **IUnknown** interfejsu i porównuje zwrócony interfejs do interfejsów inne obiekty, które są już opakowana.</span><span class="sxs-lookup"><span data-stu-id="30e1d-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="30e1d-149">Jeśli interfejs jest taki sam jak inny otoki, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywany do metody.</span><span class="sxs-lookup"><span data-stu-id="30e1d-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="30e1d-150">Jeśli interfejs nie pochodzi z obiektu znane, organizator wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="30e1d-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="30e1d-151">Organizator wysyła zapytanie do obiektu **IProvideClassInfo2** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="30e1d-152">Jeśli zostanie podana, organizator używa identyfikatora CLSID zwrócony z **IProvideClassInfo2.GetGUID** do identyfikowania coclass udostępnia interfejs.</span><span class="sxs-lookup"><span data-stu-id="30e1d-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="30e1d-153">O identyfikatorze CLSID Organizator mogą znaleźć otoki z rejestru, jeśli zestaw został wcześniej zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="30e1d-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="30e1d-154">Organizator zapytania dla interfejsu **IProvideClassInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="30e1d-155">Jeśli zostanie podana, używa organizatora **ITypeInfo** zwrócony z **IProvideClassInfo.GetClassinfo** ustalenie CLSID udostępnianie interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="30e1d-156">Organizator można użyć identyfikatora CLSID można znaleźć metadanych dla otoki.</span><span class="sxs-lookup"><span data-stu-id="30e1d-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="30e1d-157">Jeśli organizator nadal nie można zidentyfikować klasę, opakowuje interfejsu z klasy otoki ogólnego o nazwie **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="30e1d-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="30e1d-158">Organizowanie domyślne dotyczące obiektów delegowanych</span><span class="sxs-lookup"><span data-stu-id="30e1d-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="30e1d-159">Delegat zarządzanych jest przekazywane jako interfejsu COM lub wskaźnik funkcji, oparte na mechanizmie wywołania:</span><span class="sxs-lookup"><span data-stu-id="30e1d-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="30e1d-160">Dla platformy invoke, delegat jest przekazywane jako wskaźnik funkcji niezarządzanej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="30e1d-161">Dla międzyoperacyjności z modelem COM, delegat jest przekazywane jako interfejs COM typu **_Delegate** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="30e1d-162">**_Delegate** interfejsu jest zdefiniowany w bibliotece typów Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metody, dzięki czemu można wywołać metodę, która odwołuje się do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="30e1d-163">W poniższej tabeli przedstawiono opcje organizowania dla typu danych zarządzanych delegata.</span><span class="sxs-lookup"><span data-stu-id="30e1d-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="30e1d-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybutu udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia wartości do kierowanie delegatów.</span><span class="sxs-lookup"><span data-stu-id="30e1d-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="30e1d-165">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="30e1d-165">Enumeration type</span></span>|<span data-ttu-id="30e1d-166">Opis formatu niezarządzane</span><span class="sxs-lookup"><span data-stu-id="30e1d-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="30e1d-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="30e1d-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="30e1d-168">Wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="30e1d-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="30e1d-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="30e1d-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="30e1d-170">Interfejs typu **_Delegate**, zgodnie z definicją w Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="30e1d-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="30e1d-171">Należy wziąć pod uwagę Poniższy przykładowy kod, w którym metody `DelegateTestInterface` zostaną wyeksportowane do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="30e1d-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="30e1d-172">Należy zauważyć, że tylko deleguje oznaczonych **ref** (lub **ByRef**) — słowo kluczowe są przekazywane jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="30e1d-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="30e1d-173">Reprezentacja typu biblioteki</span><span class="sxs-lookup"><span data-stu-id="30e1d-173">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="30e1d-174">Wskaźnik funkcji jest wyłuskiwany, tak samo, jak można usunąć odwołania innych wskaźnika funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="30e1d-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e1d-175">Odwołanie do wskaźnika funkcji do delegata zarządzanych przez kod niezarządzany nie zapobiega środowisko uruchomieniowe języka wspólnego wykonywania wyrzucanie elementów bezużytecznych do zarządzanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-175">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="30e1d-176">Na przykład następujący kod jest nieprawidłowy ponieważ odwołanie do `cb` obiekt przekazany do `SetChangeHandler` metody, nie przechowuje `cb` aktywności poza czas życia `Test` metody.</span><span class="sxs-lookup"><span data-stu-id="30e1d-176">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="30e1d-177">Raz `cb` obiekt jest bezużytecznych, wskaźnik funkcji przekazany do `SetChangeHandler` nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="30e1d-177">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="30e1d-178">Kompensacji nieoczekiwany wyrzucanie elementów bezużytecznych, wywołujący musi zapewnić, że `cb` obiektu jest aktywne tak długo, jak funkcja niezarządzany wskaźnik jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-178">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="30e1d-179">Opcjonalnie może mieć kodu niezarządzanego, powiadom kodu zarządzanego, gdy wskaźnik funkcji nie jest już potrzebne, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-179">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="30e1d-180">Domyślny marshaling dla typów wartości</span><span class="sxs-lookup"><span data-stu-id="30e1d-180">Default marshaling for value types</span></span>  
 <span data-ttu-id="30e1d-181">Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe są [kopiowalne](blittable-and-non-blittable-types.md) i nie wymagają przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-181">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="30e1d-182">Inne [niekopiowalne](blittable-and-non-blittable-types.md) typy niepodobnych reprezentacje w pamięci zarządzane i niezarządzane, wymagane jest przekazywanie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-182">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="30e1d-183">Nadal innych typów wymaga jawnego formatowania granicy współdziałanie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-183">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="30e1d-184">Ten temat zawiera informacje wykonaj w typach wartości sformatowane:</span><span class="sxs-lookup"><span data-stu-id="30e1d-184">This topic provides the follow information on formatted value types:</span></span>  
  
-   [<span data-ttu-id="30e1d-185">Typy wartości używane na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="30e1d-185">Value Types Used in Platform Invoke</span></span>](#cpcondefaultmarshalingforvaluetypesanchor2)  
  
-   [<span data-ttu-id="30e1d-186">Typy wartości używane w modelu COM Interop</span><span class="sxs-lookup"><span data-stu-id="30e1d-186">Value Types Used in COM Interop</span></span>](#cpcondefaultmarshalingforvaluetypesanchor3)  
  
 <span data-ttu-id="30e1d-187">Oprócz opisujące sformatowany typów, w tym temacie identyfikuje [System typów wartości](#cpcondefaultmarshalingforvaluetypesanchor1) zawierających nietypowe zachowanie marshalingu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-187">In addition to describing formatted types, this topic identifies [System Value Types](#cpcondefaultmarshalingforvaluetypesanchor1) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="30e1d-188">Sformatowany typem jest typ złożony, który zawiera informacje, które jawnie określa układ jej elementów członkowskich w pamięci.</span><span class="sxs-lookup"><span data-stu-id="30e1d-188">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="30e1d-189">Informacje o układzie elementu członkowskiego jest realizowane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-189">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="30e1d-190">Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="30e1d-190">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="30e1d-191">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="30e1d-191">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="30e1d-192">Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatne zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="30e1d-192">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="30e1d-193">Jednak gdy typem wartości są przekazywane do kodu niezarządzanego, układ elementów członkowskich jest atrybutem wartości prognozowanych.</span><span class="sxs-lookup"><span data-stu-id="30e1d-193">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="30e1d-194">Próba zorganizowania taka struktura automatycznie powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="30e1d-194">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="30e1d-195">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="30e1d-195">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="30e1d-196">Wskazuje, że mają zostać uwzględnione w pamięci niezarządzanej w tej samej kolejności, w jakiej występują w definicji typu zarządzanego elementy członkowskie tego typu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-196">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="30e1d-197">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="30e1d-197">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="30e1d-198">Określa układ elementów członkowskich według <xref:System.Runtime.InteropServices.FieldOffsetAttribute> dostarczony wraz z każdego pola.</span><span class="sxs-lookup"><span data-stu-id="30e1d-198">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor2"></a>   
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="30e1d-199">Typy wartości używane na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="30e1d-199">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="30e1d-200">W poniższym przykładzie `Point` i `Rect` typy zapewniają elementu członkowskiego informacji o układzie przy użyciu **structlayoutattribute —**.</span><span class="sxs-lookup"><span data-stu-id="30e1d-200">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="30e1d-201">Podczas przekazywane do kodu niezarządzanego, te typy sformatowany są przekazywane jako struktury w stylu języka C.</span><span class="sxs-lookup"><span data-stu-id="30e1d-201">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="30e1d-202">To zapewnia prosty sposób wywoływania niezarządzanego API, która przyjmuje argumenty struktury.</span><span class="sxs-lookup"><span data-stu-id="30e1d-202">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="30e1d-203">Na przykład `POINT` i `RECT` struktury mogą zostać przekazane do interfejsu API Win32 Microsoft **PtInRect** działają w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="30e1d-203">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Win32 API **PtInRect** function as follows:</span></span>  
  
```  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="30e1d-204">Można przekazać struktur za pomocą następujących platform wywołania definicji:</span><span class="sxs-lookup"><span data-stu-id="30e1d-204">You can pass structures using the following platform invoke definition:</span></span>  
  
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
  
 <span data-ttu-id="30e1d-205">`Rect` Typ wartości muszą być przekazywane przez odwołanie, ponieważ oczekiwana jest wskaźnik do niezarządzanego API `RECT` mają być przekazane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="30e1d-205">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="30e1d-206">`Point` Typ wartości jest przekazywany przez wartość, ponieważ oczekuje niezarządzanego API `POINT` do przekazania na stosie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-206">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="30e1d-207">Ta różnica jest bardzo ważne.</span><span class="sxs-lookup"><span data-stu-id="30e1d-207">This subtle difference is very important.</span></span> <span data-ttu-id="30e1d-208">Odwołania są przekazywane do kodu niezarządzanego jako wskaźników.</span><span class="sxs-lookup"><span data-stu-id="30e1d-208">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="30e1d-209">Wartości są przekazywane do kodu niezarządzanego na stosie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-209">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e1d-210">Gdy typem sformatowany jest przekazywane jako struktura, tylko pola w ramach typu są dostępne.</span><span class="sxs-lookup"><span data-stu-id="30e1d-210">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="30e1d-211">Jeśli typ ma metody, właściwości lub zdarzeń, są niedostępne z kodem niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="30e1d-211">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="30e1d-212">Klasy można również być przekazywane do kodu niezarządzanego jako struktur w stylu języka C, pod warunkiem rozwiązaniu układu elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-212">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="30e1d-213">Dostępne są również informacje o układzie elementu członkowskiego klasy z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-213">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="30e1d-214">Główną różnicą między typami wartości o stałej układ i klasy z układem stałej jest sposób, w którym są przekazywane do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-214">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="30e1d-215">Typy wartości są przekazywane przez wartość (stos) i w związku z tym zmiany wprowadzone przez funkcję wywołującą elementy członkowskie tego typu nie są widoczne dla obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="30e1d-215">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="30e1d-216">Typy odwołań są przekazywane przez odwołanie (odwołanie do typu jest przekazywany na stosie). w rezultacie wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu wywoływany są widoczne przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="30e1d-216">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e1d-217">Jeśli typ referencyjny ma elementów członkowskich typu niekopiowalne, konwersja nie jest wymagana dwa razy: raz pierwszy, gdy argument jest przekazywany stronie niezarządzane, a drugi raz na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="30e1d-217">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="30e1d-218">Ze względu na to obciążenie dodane lub Brak parametrów musi jawnie odnosić się do argumentu, jeśli element wywołujący chce wyświetlać zmiany wprowadzone przez funkcję wywołującą.</span><span class="sxs-lookup"><span data-stu-id="30e1d-218">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="30e1d-219">W poniższym przykładzie `SystemTime` klasa ma układ sekwencyjny elementu członkowskiego i mogą zostać przekazane do interfejsu API Win32 **GetSystemTime** funkcji.</span><span class="sxs-lookup"><span data-stu-id="30e1d-219">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Win32 API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="30e1d-220">**GetSystemTime** funkcja jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="30e1d-220">The **GetSystemTime** function is defined as follows:</span></span>  
  
```  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="30e1d-221">Platforma równoważne wywołanie definicji **GetSystemTime** wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="30e1d-221">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
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
  
 <span data-ttu-id="30e1d-222">Zwróć uwagę, że `SystemTime` argument nie jest typu jako argument odwołania, ponieważ `SystemTime` jest klasa, nie jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="30e1d-222">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="30e1d-223">W przeciwieństwie do typów wartości klasy zawsze są przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-223">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="30e1d-224">Poniższy przykład kodu pokazuje innej `Point` klasy, która ma metodę o nazwie `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="30e1d-224">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="30e1d-225">Ponieważ typ ma układ sekwencyjny, można przekazany do kodu niezarządzanego i organizowane w strukturze.</span><span class="sxs-lookup"><span data-stu-id="30e1d-225">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="30e1d-226">Jednak `SetXY` element członkowski nie jest można wywołać za pomocą kodu niezarządzanego, nawet jeśli obiekt jest przekazywana przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-226">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="30e1d-227">Typy wartości używane w modelu COM Interop</span><span class="sxs-lookup"><span data-stu-id="30e1d-227">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="30e1d-228">Typy sformatowany również mogą być przekazywane do wywołania metody międzyoperacyjnego COM.</span><span class="sxs-lookup"><span data-stu-id="30e1d-228">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="30e1d-229">W rzeczywistości podczas eksportowania do biblioteki typów, typów wartości są automatycznie konwertowane na struktury.</span><span class="sxs-lookup"><span data-stu-id="30e1d-229">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="30e1d-230">Jak pokazano na poniższym przykładzie, `Point` typ wartości staje się definicja typu (typedef) o nazwie `Point`.</span><span class="sxs-lookup"><span data-stu-id="30e1d-230">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="30e1d-231">Wszystkie odwołania do `Point` są zamieniane na typ wartości w innym miejscu w bibliotece typów `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="30e1d-231">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="30e1d-232">**Reprezentacja typu biblioteki**</span><span class="sxs-lookup"><span data-stu-id="30e1d-232">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="30e1d-233">Te same zasady używany do organizowania wartości i odwołań pozwalającą na platformie wywołania wywołania są używane podczas organizowania za pośrednictwem interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="30e1d-233">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="30e1d-234">Na przykład, gdy wystąpienie klasy `Point` typ wartości jest przekazywany z programu .NET Framework modelowi COM, `Point` jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="30e1d-234">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="30e1d-235">Jeśli `Point` typ wartości jest przekazywana przez odwołanie, wskaźnik do `Point` jest przekazywany na stosie.</span><span class="sxs-lookup"><span data-stu-id="30e1d-235">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="30e1d-236">Organizator międzyoperacyjne nie obsługuje wyższego poziomu pośredni (**punktu \* \*** ) w żadnym kierunku.</span><span class="sxs-lookup"><span data-stu-id="30e1d-236">The interop marshaler does not support higher levels of indirection (**Point \*\***) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30e1d-237">Struktury o <xref:System.Runtime.InteropServices.LayoutKind> ustawioną wartość wyliczenia **Explicit** nie można używać w modelu COM interop, ponieważ wyeksportowanej biblioteki typów nie express jawny układ.</span><span class="sxs-lookup"><span data-stu-id="30e1d-237">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
<a name="cpcondefaultmarshalingforvaluetypesanchor1"></a>   
### <a name="system-value-types"></a><span data-ttu-id="30e1d-238">System typów wartości</span><span class="sxs-lookup"><span data-stu-id="30e1d-238">System Value Types</span></span>  
 <span data-ttu-id="30e1d-239"><xref:System> Przestrzeń nazw ma kilka typów wartości, które reprezentują formy opakowanej typu pierwotnego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="30e1d-239">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="30e1d-240">Na przykład typ wartości <xref:System.Int32?displayProperty=nameWithType> struktury reprezentuje formy opakowanej z **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="30e1d-240">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="30e1d-241">Zamiast przekazywanie tych typów jako struktury, są inne typy sformatowane, należy kierować je w taki sam sposób jak typy pierwotne, które one polu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-241">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="30e1d-242">**System.Int32** w związku z tym jest przekazywane jako **ELEMENT_TYPE_I4** zamiast struktury zawierający pojedynczy element członkowski typu **długi**.</span><span class="sxs-lookup"><span data-stu-id="30e1d-242">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="30e1d-243">Poniższa tabela zawiera listę typów wartości w **systemu** przestrzeni nazw, która to opakowanego reprezentacje typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="30e1d-243">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="30e1d-244">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="30e1d-244">System value type</span></span>|<span data-ttu-id="30e1d-245">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="30e1d-245">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="30e1d-246">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="30e1d-246">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="30e1d-247">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="30e1d-247">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="30e1d-248">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="30e1d-248">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="30e1d-249">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="30e1d-249">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="30e1d-250">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="30e1d-250">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="30e1d-251">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="30e1d-251">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="30e1d-252">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="30e1d-252">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="30e1d-253">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="30e1d-253">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="30e1d-254">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="30e1d-254">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="30e1d-255">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="30e1d-255">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="30e1d-256">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="30e1d-256">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="30e1d-257">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="30e1d-257">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="30e1d-258">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="30e1d-258">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="30e1d-259">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="30e1d-259">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="30e1d-260">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="30e1d-260">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="30e1d-261">Wartość typów w **systemu** przestrzeni nazw są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="30e1d-261">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="30e1d-262">Organizator, ponieważ kodu niezarządzanego już ustalonym formaty dla tych typów, ma specjalne zasady przekazywanie ich.</span><span class="sxs-lookup"><span data-stu-id="30e1d-262">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="30e1d-263">W poniższej tabeli przedstawiono typy specjalna wartość w **systemu** przestrzeni nazw, a także typ niezarządzany, są one przekazywane do.</span><span class="sxs-lookup"><span data-stu-id="30e1d-263">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="30e1d-264">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="30e1d-264">System value type</span></span>|<span data-ttu-id="30e1d-265">Typ IDL</span><span class="sxs-lookup"><span data-stu-id="30e1d-265">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="30e1d-266">**DATA**</span><span class="sxs-lookup"><span data-stu-id="30e1d-266">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="30e1d-267">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="30e1d-267">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="30e1d-268">**IDENTYFIKATOR GUID**</span><span class="sxs-lookup"><span data-stu-id="30e1d-268">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="30e1d-269">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="30e1d-269">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="30e1d-270">Poniższy kod przedstawia definicję typu niezarządzanego **data**, **GUID**, **DZIESIĘTNĄ**, i **OLE_COLOR** w typie Stdole2 Biblioteka.</span><span class="sxs-lookup"><span data-stu-id="30e1d-270">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="30e1d-271">Reprezentacja typu biblioteki</span><span class="sxs-lookup"><span data-stu-id="30e1d-271">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="30e1d-272">Poniższy kod przedstawia odpowiadające im definicje w zarządzanej `IValueTypes` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="30e1d-272">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="30e1d-273">Reprezentacja typu biblioteki</span><span class="sxs-lookup"><span data-stu-id="30e1d-273">Type library representation</span></span>  
  
```  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="30e1d-274">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="30e1d-274">See Also</span></span>  
 [<span data-ttu-id="30e1d-275">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="30e1d-275">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="30e1d-276">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="30e1d-276">Copying and Pinning</span></span>](copying-and-pinning.md)  
 [<span data-ttu-id="30e1d-277">Domyślny marshaling dla tablic</span><span class="sxs-lookup"><span data-stu-id="30e1d-277">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)  
 [<span data-ttu-id="30e1d-278">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="30e1d-278">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)  
 [<span data-ttu-id="30e1d-279">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="30e1d-279">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
