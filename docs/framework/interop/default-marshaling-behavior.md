---
title: Domyślne zachowanie marshalingu
ms.date: 06/26/2018
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
ms.openlocfilehash: fe1d35f091eb98ca0080a73283d7e158e2ae26eb
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409448"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="d5af2-102">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="d5af2-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="d5af2-103">Marshaling międzyoperacyjny działa w regułach tego dyktować, jak dane skojarzone z parametrami metody zachowuje się jak przekazuje między zarządzanymi i niezarządzanymi pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5af2-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="d5af2-104">Te wbudowane reguły kontrolować takie kierowania działań jako przekształcenia typu danych, / / wywoływany można zmienić danych przekazanych do niego i zwracają te zmiany do obiektu wywołującego, a w ramach której okolicznościach Organizator udostępnia optymalizację wydajności.</span><span class="sxs-lookup"><span data-stu-id="d5af2-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="d5af2-105">W tej sekcji wymieniono domyślnych parametrów zachowań interop marshaling usługi.</span><span class="sxs-lookup"><span data-stu-id="d5af2-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="d5af2-106">Przedstawia ona szczegółowe informacje na temat organizowanie tablic, typów logicznych, typu char, delegatów, klas, obiektów, ciągi i struktur.</span><span class="sxs-lookup"><span data-stu-id="d5af2-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5af2-107">Marshaling typów ogólnych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="d5af2-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="d5af2-108">Aby uzyskać więcej informacji, zobacz [współpracy za pomocą typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d5af2-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="d5af2-109">Zarządzanie pamięcią za pomocą organizatora międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="d5af2-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="d5af2-110">Organizator międzyoperacyjny zawsze spróbuje zwolnić pamięć przydzielana przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="d5af2-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="d5af2-111">To zachowanie jest zgodne z zasadami zarządzania pamięci COM, ale różni się od reguły rządzące natywnych języka C++.</span><span class="sxs-lookup"><span data-stu-id="d5af2-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="d5af2-112">Błąd może wystąpić, jeśli przewidujesz natywnych zachowania C++ (nie pamięci zwalnianie) podczas używania platformy wywołać, który automatycznie zwalnia pamięć dla wskaźników.</span><span class="sxs-lookup"><span data-stu-id="d5af2-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="d5af2-113">Na przykład wywołanie następujące metody niezarządzanego z biblioteki DLL w języku C++ nie automatycznie zwolni wszystkie pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5af2-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="d5af2-114">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="d5af2-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="d5af2-115">Jednakże, jeśli zdefiniujesz metody jako prototyp wywołania platformy, Zastąp każde **BSTR** to typ <xref:System.String> typu, a następnie wywołaj `MethodOne`, środowisko uruchomieniowe języka wspólnego spróbuje zwolnić `b` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="d5af2-116">Można zmienić zachowanie organizowania za pomocą <xref:System.IntPtr> typy zamiast **ciąg** typów.</span><span class="sxs-lookup"><span data-stu-id="d5af2-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="d5af2-117">Środowisko uruchomieniowe zawsze używa **CoTaskMemFree** metodę, aby zwolnić pamięć.</span><span class="sxs-lookup"><span data-stu-id="d5af2-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="d5af2-118">Jeśli pamięci, w którym pracujesz, nie została przydzielona za pomocą **CoTaskMemAlloc** metody, należy użyć **IntPtr** i zwalniają pamięć ręcznie przy użyciu odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="d5af2-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="d5af2-119">Podobnie, można uniknąć pamięcią automatyczną zwalnianie w sytuacjach, w których nigdy nie powinna być zwolniona pamięć, tak jak w przypadku **GetCommandLine** funkcji z modułu Kernel32.dll, która zwraca wskaźnik do pamięci jądra.</span><span class="sxs-lookup"><span data-stu-id="d5af2-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="d5af2-120">Aby uzyskać szczegółowe informacje dotyczące ręcznego zwalniania pamięci, zobacz [przykłady buforów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d5af2-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="d5af2-121">Organizowanie domyślne dotyczące klas</span><span class="sxs-lookup"><span data-stu-id="d5af2-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="d5af2-122">Klasy mogą być organizowane wyłącznie przez współdziałania z modelem COM i zawsze są przekazywane jako interfejsy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="d5af2-123">W niektórych przypadkach interfejs używany do organizowania klasy jest nazywane interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="d5af2-124">Aby dowiedzieć się, jak zastępowanie interfejsu klasy za pomocą ulubionego interfejsu, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="d5af2-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="d5af2-125">Przekazywanie klas dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="d5af2-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="d5af2-126">Gdy zarządzanej klasy jest przekazywany do modelu COM, organizator międzyoperacyjny automatycznie opakowuje klasy przy użyciu serwera proxy modelu COM i przekazuje interfejsu klasy generowane przez serwer proxy, aby wywołanie metody COM.</span><span class="sxs-lookup"><span data-stu-id="d5af2-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="d5af2-127">Serwer proxy następnie deleguje wszystkie wywołania interfejsu klasy z powrotem do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d5af2-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="d5af2-128">Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowane przez klasy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="d5af2-129">Serwer proxy takich jak automatycznie implementuje interfejsy **IUnknown** i **IDispatch** imieniu klasy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="d5af2-130">Przekazywanie klas kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="d5af2-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="d5af2-131">Klasy coclass nie są zwykle używane jako argumenty tej metody w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d5af2-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="d5af2-132">Zamiast tego domyślnego interfejsu jest zwykle przekazywany zamiast wspólna.</span><span class="sxs-lookup"><span data-stu-id="d5af2-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="d5af2-133">Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyoperacyjny jest odpowiedzialny za zawijanie interfejsu z otoką właściwe i przekazanie otoki do zarządzanej metody.</span><span class="sxs-lookup"><span data-stu-id="d5af2-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="d5af2-134">Określanie, które otoki, aby użyć może być trudne.</span><span class="sxs-lookup"><span data-stu-id="d5af2-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="d5af2-135">Każde wystąpienie obiektu COM ma otokę pojedynczy, unikatowy niezależnie od tego, jak wiele interfejsów obiekt implementuje.</span><span class="sxs-lookup"><span data-stu-id="d5af2-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="d5af2-136">Na przykład pojedynczy obiekt COM, który implementuje pięć różnych interfejsów ma tylko jedną otokę.</span><span class="sxs-lookup"><span data-stu-id="d5af2-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="d5af2-137">Ten sam otoki udostępnia wszystkie pięć interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d5af2-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="d5af2-138">Jeśli dwa wystąpienia obiektu COM są tworzone, są tworzone dwa wystąpienia otoki.</span><span class="sxs-lookup"><span data-stu-id="d5af2-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="d5af2-139">Dla otoki zachować ten sam typ w okresie swojego istnienia Organizator międzyoperacyjny musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępnianych przez obiekt jest przekazywany za pomocą organizatora.</span><span class="sxs-lookup"><span data-stu-id="d5af2-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="d5af2-140">Organizator identyfikuje obiekt, patrząc na jeden z interfejsów, który implementuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="d5af2-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="d5af2-141">Na przykład Organizator Określa, że klasy otoki powinien być używany do opakowywania interfejsu, który został przekazany do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d5af2-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="d5af2-142">Po interfejsie najpierw jest przekazywany za pomocą organizatora, organizator sprawdza, czy interfejs pochodzi z znany obiekt.</span><span class="sxs-lookup"><span data-stu-id="d5af2-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="d5af2-143">To sprawdzanie jest wykonywane w dwóch sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="d5af2-143">This check occurs in two situations:</span></span>  
  
-   <span data-ttu-id="d5af2-144">Interfejs jest jest implementowany przez inny obiekt zarządzany, który został przekazany do modelu COM, gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="d5af2-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="d5af2-145">Organizator można łatwo zidentyfikować interfejsów udostępnianych przez zarządzane obiekty i jest możliwość dopasowania interfejs z zarządzanego obiektu, który dostarcza implementację.</span><span class="sxs-lookup"><span data-stu-id="d5af2-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="d5af2-146">Zarządzany obiekt jest następnie przekazywany do metody i nie otoki jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="d5af2-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
-   <span data-ttu-id="d5af2-147">Obiekt, który jest już opakowana implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="d5af2-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="d5af2-148">Aby ustalić, czy jest to możliwe, organizator zapytania obiektu dla jego **IUnknown** interfejs i porównuje zwrócony interfejs służący do interfejsów inne obiekty, które są już opakowana.</span><span class="sxs-lookup"><span data-stu-id="d5af2-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="d5af2-149">Jeśli interfejs jest taki sam jak inny otoki, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywany do metody.</span><span class="sxs-lookup"><span data-stu-id="d5af2-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="d5af2-150">Jeśli interfejs nie jest od znanych obiektu, organizator wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="d5af2-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1.  <span data-ttu-id="d5af2-151">Organizator wysyła zapytanie do obiektu **IProvideClassInfo2** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="d5af2-152">Jeśli nie dostarczono, organizator używa CLSID zwróciło **IProvideClassInfo2.GetGUID** do identyfikowania coclass, zapewniając interfejs.</span><span class="sxs-lookup"><span data-stu-id="d5af2-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="d5af2-153">O identyfikatorze CLSID Organizator można zlokalizować otoki z rejestru, jeśli zestaw został wcześniej zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="d5af2-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2.  <span data-ttu-id="d5af2-154">Organizator zapytania dla interfejsu **IProvideClassInfo** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="d5af2-155">Jeśli nie dostarczono, organizator używa **ITypeInfo** zwróciło **IProvideClassInfo.GetClassinfo** ustalenie, identyfikator CLSID klasy uwidaczniania interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="d5af2-156">Organizator można użyć identyfikatora CLSID, do lokalizowania metadane dla otoki.</span><span class="sxs-lookup"><span data-stu-id="d5af2-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3.  <span data-ttu-id="d5af2-157">Jeśli organizator nadal nie można określić klasę, opakowuje interfejs za pomocą klasy otoki ogólnych o nazwie **.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="d5af2-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="d5af2-158">Organizowanie domyślne dotyczące delegatów</span><span class="sxs-lookup"><span data-stu-id="d5af2-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="d5af2-159">Zarządzane delegata jest organizowana jako interfejsem COM lub wskaźnika funkcji jest oparte na mechanizmie wywołania:</span><span class="sxs-lookup"><span data-stu-id="d5af2-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
-   <span data-ttu-id="d5af2-160">Dla platformy, należy wywołać, obiekt delegowany jest organizowana jako wskaźnik funkcji niezarządzanej domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
-   <span data-ttu-id="d5af2-161">Dla współdziałania z modelem COM, obiekt delegowany jest organizowana jako interfejsu COM typu **_Delegate** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="d5af2-162">**_Delegate** interfejsu jest zdefiniowany w bibliotece typów Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metody, która umożliwia wywoływanie metody, która odwołuje się do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="d5af2-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="d5af2-163">W poniższej tabeli przedstawiono organizowania opcji dla typu danych zarządzanych delegata.</span><span class="sxs-lookup"><span data-stu-id="d5af2-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="d5af2-164"><xref:System.Runtime.InteropServices.MarshalAsAttribute> Atrybut udostępnia wiele <xref:System.Runtime.InteropServices.UnmanagedType> delegatów marshal wartości wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d5af2-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="d5af2-165">Typ wyliczeniowy</span><span class="sxs-lookup"><span data-stu-id="d5af2-165">Enumeration type</span></span>|<span data-ttu-id="d5af2-166">Opis formatu niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="d5af2-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="d5af2-167">**UnmanagedType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="d5af2-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="d5af2-168">Wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d5af2-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="d5af2-169">**UnmanagedType.Interface**</span><span class="sxs-lookup"><span data-stu-id="d5af2-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="d5af2-170">Interfejs typu **_Delegate**, zgodnie z definicją w Mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="d5af2-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="d5af2-171">Należy wziąć pod uwagę poniższy przykład kodu, w której metody `DelegateTestInterface` są eksportowane do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="d5af2-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="d5af2-172">Należy zauważyć, że tylko deleguje oznaczone **ref** (lub **ByRef**) — słowo kluczowe są przekazywane jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="d5af2-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="d5af2-173">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d5af2-173">Type library representation</span></span>  
  
```cpp  
importlib("mscorlib.tlb");  
interface DelegateTest : IDispatch {  
[id(…)] HRESULT m1([in] _Delegate* d);  
[id(…)] HRESULT m2([in] _Delegate* d);  
[id(…)] HRESULT m3([in, out] _Delegate** d);  
[id()] HRESULT m4([in] int d);  
[id()] HRESULT m5([in, out] int *d);  
   };  
```  
  
 <span data-ttu-id="d5af2-174">Wskaźnik funkcji może zostać wyłuskany tak samo, jak może zostać wyłuskany, drugi wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d5af2-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="d5af2-175">W tym przykładzie, jeśli dwa obiekty delegowane są przekazywane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, wynik jest `int` i wskaźnik `int`.</span><span class="sxs-lookup"><span data-stu-id="d5af2-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="d5af2-176">Ponieważ typy delegatów są są organizowane, `int` w tym miejscu reprezentuje wskaźnik do void (`void*`), czyli adres delegata w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5af2-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="d5af2-177">Innymi słowy, ten wynik zależy od 32-bitowych systemach Windows, ponieważ `int` w tym miejscu reprezentuje rozmiar wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5af2-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
>  <span data-ttu-id="d5af2-178">Odwołanie do wskaźnika funkcji do delegata zarządzanego kodu niezarządzanego w posiadaniu nie uniemożliwia środowiska uruchomieniowego języka wspólnego przeprowadzania wyrzucania elementów bezużytecznych obiektów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d5af2-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="d5af2-179">Na przykład, poniższy kod jest nieprawidłowy ponieważ odwołanie do `cb` przekazanego do obiektu `SetChangeHandler` metody nie przechowuje `cb` podtrzymywania połączenia po przekroczeniu cyklu życia `Test` metody.</span><span class="sxs-lookup"><span data-stu-id="d5af2-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="d5af2-180">Gdy `cb` obiektu są bezużyteczne, wskaźnik funkcji jest przekazywany do `SetChangeHandler` nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="d5af2-181">Aby zrekompensować nieoczekiwany wyrzucania elementów bezużytecznych, obiekt wywołujący musi zapewnić, że `cb` obiektu jest życiu tak długo, jak funkcja niezarządzany wskaźnik jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="d5af2-182">Opcjonalnie może mieć kod niezarządzany, powiadom kodu zarządzanego, gdy wskaźnik funkcji nie jest już potrzebny, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="d5af2-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="d5af2-183">Organizowanie domyślne dotyczące typów wartości</span><span class="sxs-lookup"><span data-stu-id="d5af2-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="d5af2-184">Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe są [danych kopiowalnych](blittable-and-non-blittable-types.md) i nie wymagają szeregowanie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="d5af2-185">Inne [niekopiowalnych](blittable-and-non-blittable-types.md) typy mają różne reprezentacje w pamięci zarządzanych i niezarządzanych i wymagają szeregowanie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="d5af2-186">Nadal innych typów wymaga jawnego formatowanie wewnątrz międzyoperacyjnej granicy.</span><span class="sxs-lookup"><span data-stu-id="d5af2-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="d5af2-187">Ta sekcja zawiera informacje na następujących typach sformatowaną wartość:</span><span class="sxs-lookup"><span data-stu-id="d5af2-187">This section provides information on the following formatted value types:</span></span>  
  
-   [<span data-ttu-id="d5af2-188">Typy wartości używane na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="d5af2-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
-   [<span data-ttu-id="d5af2-189">Typy wartości używane w modelu COM</span><span class="sxs-lookup"><span data-stu-id="d5af2-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="d5af2-190">Oprócz zawierająca opis typów sformatowane, ten temat zawiera informacje o [System typów wartości](#system-value-types) , które mają nietypowe zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="d5af2-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="d5af2-191">Sformatowana typ to typ złożony, który zawiera informacje, które jawnie kontroluje układ składowych w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d5af2-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="d5af2-192">Informacje o układzie składowej jest realizowane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="d5af2-193">Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="d5af2-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
-   <span data-ttu-id="d5af2-194">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="d5af2-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="d5af2-195">Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatna zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="d5af2-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="d5af2-196">Jednak gdy typ wartości jest przekazywany do kodu niezarządzanego, układ elementów członkowskich jest przewidywalne.</span><span class="sxs-lookup"><span data-stu-id="d5af2-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="d5af2-197">Podjęto próbę automatycznie kierować takie struktury, powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d5af2-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
-   <span data-ttu-id="d5af2-198">**LayoutKind.Sequential**</span><span class="sxs-lookup"><span data-stu-id="d5af2-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="d5af2-199">Wskazuje, że elementy członkowskie tego typu mają być rozmieszczone w niezarządzanej pamięci w tej samej kolejności, w jakiej są wyświetlane w definicji typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d5af2-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
-   <span data-ttu-id="d5af2-200">**LayoutKind.Explicit**</span><span class="sxs-lookup"><span data-stu-id="d5af2-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="d5af2-201">Wskazuje, czy członkowie są ułożone zgodnie z opisem w <xref:System.Runtime.InteropServices.FieldOffsetAttribute> dostarczony z każdym polem.</span><span class="sxs-lookup"><span data-stu-id="d5af2-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="d5af2-202">Typy wartości używane na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="d5af2-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="d5af2-203">W poniższym przykładzie `Point` i `Rect` typy zapewniają elementu członkowskiego informacji o układzie przy użyciu **structlayoutattribute —**.</span><span class="sxs-lookup"><span data-stu-id="d5af2-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="d5af2-204">Podczas przekazywania do kodu niezarządzanego, te typy sformatowane jest organizowana jako struktury stylu C.</span><span class="sxs-lookup"><span data-stu-id="d5af2-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="d5af2-205">Zapewnia to prosty sposób wywoływania niezarządzanego interfejsu API, która przyjmuje argumenty struktury.</span><span class="sxs-lookup"><span data-stu-id="d5af2-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="d5af2-206">Na przykład `POINT` i `RECT` struktury mogą być przekazywane do interfejsu API programu Microsoft Windows **PtInRect** funkcji w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d5af2-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="d5af2-207">Można przekazać struktury za pomocą platformy następujące wywołania definicji:</span><span class="sxs-lookup"><span data-stu-id="d5af2-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="d5af2-208">`Rect` Typ wartości muszą być przekazywane przez odwołanie, ponieważ niezarządzany API oczekuje wskaźnika do `RECT` mają być przekazane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5af2-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="d5af2-209">`Point` Typ wartości jest przekazywany przez wartość, ponieważ oczekuje niezarządzany interfejs API `POINT` przekazywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="d5af2-210">Bardzo ważne jest to niewielka różnica.</span><span class="sxs-lookup"><span data-stu-id="d5af2-210">This subtle difference is very important.</span></span> <span data-ttu-id="d5af2-211">Odwołania są przekazywane do kodu niezarządzanego jako wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="d5af2-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="d5af2-212">Wartości są przekazywane do kodu niezarządzanego na stosie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5af2-213">Gdy typem sformatowane jest organizowana jako struktury, tylko pola w typie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="d5af2-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="d5af2-214">Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z niezarządzanego kodu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="d5af2-215">Klasy może również być przekazywania do kodu niezarządzanego jako struktury stylu C pod warunkiem naprawili układ składowych.</span><span class="sxs-lookup"><span data-stu-id="d5af2-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="d5af2-216">Informacje o układzie składowej klasy, również jest dostarczana z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="d5af2-217">Główna różnica między typami wartości przy użyciu stałej układ i klas o stałym układzie jest sposób, w którym są przekazywania do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d5af2-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="d5af2-218">Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszelkie zmiany wprowadzone do elementów członkowskich typu przez obiekt wywoływany nie są widoczne przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d5af2-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="d5af2-219">Typy odwołań są przekazywane przez odwołanie (odwołania do typu jest przekazywane na stosie). w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu przez obiekt wywoływany są widoczne przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="d5af2-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5af2-220">Jeśli typ odwołania ma składowe typów niekopiowalnych, wymagana jest konwersja dwa razy: podczas pierwszego, gdy argument jest przekazywany niezarządzanym, a drugi raz na powrót z wywołania.</span><span class="sxs-lookup"><span data-stu-id="d5af2-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="d5af2-221">Ze względu na to dodatkowe obciążenie/Ściemnianie parametry muszą być jawnie stosowana do argumentu Jeśli obiekt wywołujący chce, aby zobaczyć zmiany wprowadzone przez obiekt wywoływany.</span><span class="sxs-lookup"><span data-stu-id="d5af2-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="d5af2-222">W poniższym przykładzie `SystemTime` klasa ma układ składowych sekwencyjne i mogą być przekazywane do interfejsu API Windows **GetSystemTime** funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5af2-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="d5af2-223">**GetSystemTime** funkcja jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d5af2-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="d5af2-224">Definicja wywołanie równoważnej platformy **GetSystemTime** jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d5af2-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class WindowsAPI
    Friend Shared Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class WindowsAPI
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="d5af2-225">Należy zauważyć, że `SystemTime` argument nie jest typu jako argument odwołania, ponieważ `SystemTime` jest klasą nie jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="d5af2-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="d5af2-226">Inaczej niż w przypadku typów wartości klasy zawsze są przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="d5af2-227">Poniższy przykład kodu pokazuje inną `Point` klasy, która ma metodę o nazwie `SetXY`.</span><span class="sxs-lookup"><span data-stu-id="d5af2-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="d5af2-228">Ponieważ typ ma sekwencyjne układ, można przekazany do kodu niezarządzanego i organizowane w strukturze.</span><span class="sxs-lookup"><span data-stu-id="d5af2-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="d5af2-229">Jednak `SetXY` elementu członkowskiego nie jest wywoływane z niezarządzanego kodu, nawet jeśli obiekt jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="d5af2-230">Typy wartości używane w modelu COM</span><span class="sxs-lookup"><span data-stu-id="d5af2-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="d5af2-231">Typy sformatowane również mogą być przekazywane do wywołania metody międzyoperacyjnego modelu COM.</span><span class="sxs-lookup"><span data-stu-id="d5af2-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="d5af2-232">W rzeczywistości podczas eksportowania do biblioteki typów, typy wartości są automatycznie konwertowane do struktur.</span><span class="sxs-lookup"><span data-stu-id="d5af2-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="d5af2-233">Jak pokazano na poniższym przykładzie, `Point` typ wartości staje się definicję typu (typedef) o nazwie `Point`.</span><span class="sxs-lookup"><span data-stu-id="d5af2-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="d5af2-234">Wszystkie odwołania do `Point` typu wartości w innym miejscu w bibliotece typów są zastępowane `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="d5af2-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="d5af2-235">**Reprezentacja biblioteki typów**</span><span class="sxs-lookup"><span data-stu-id="d5af2-235">**Type library representation**</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="d5af2-236">Te same zasady, które są używane do organizowania wartości i odwołań pozwalającą na platformie wywołania są używane w przypadku kierowania za pośrednictwem interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="d5af2-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="d5af2-237">Na przykład, jeśli wystąpienie `Point` typ wartości jest przekazywany z programu .NET Framework modelowi COM, `Point` jest przekazywany przez wartość.</span><span class="sxs-lookup"><span data-stu-id="d5af2-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="d5af2-238">Jeśli `Point` typ wartości jest przekazywany przez odwołanie, wskaźnik do `Point` jest przekazywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="d5af2-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="d5af2-239">Organizator międzyoperacyjny nie obsługuje wyższego poziomu pośredniego (**punktu** \* \*) w dowolnym kierunku.</span><span class="sxs-lookup"><span data-stu-id="d5af2-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5af2-240">Struktury o <xref:System.Runtime.InteropServices.LayoutKind> równa wartości wyliczenia **jawne** nie można używać w modelu COM, ponieważ wyeksportowanej biblioteki typów nie express jawnego układu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="d5af2-241">System typów wartości</span><span class="sxs-lookup"><span data-stu-id="d5af2-241">System Value Types</span></span>  
 <span data-ttu-id="d5af2-242"><xref:System> Przestrzeń nazw ma kilka typów wartości, które reprezentują formy opakowanej typów pierwotnych w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d5af2-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="d5af2-243">Na przykład typ wartości <xref:System.Int32?displayProperty=nameWithType> struktury reprezentuje spakowany formie **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="d5af2-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="d5af2-244">Zamiast kierowania tych typów jako struktury, jak inne typy sformatowane, można kierować je w taki sam sposób, jak typy pierwotne, które one polu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="d5af2-245">**System.Int32** w związku z tym jest organizowana jako **ELEMENT_TYPE_I4** zamiast w strukturze zawierający pojedynczy element członkowski typu **długie**.</span><span class="sxs-lookup"><span data-stu-id="d5af2-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="d5af2-246">Poniższa tabela zawiera listę typów wartości w **systemu** obszar nazw, który jest spakowany reprezentacje typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="d5af2-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="d5af2-247">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="d5af2-247">System value type</span></span>|<span data-ttu-id="d5af2-248">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="d5af2-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="d5af2-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="d5af2-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="d5af2-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="d5af2-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="d5af2-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="d5af2-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="d5af2-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="d5af2-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="d5af2-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="d5af2-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="d5af2-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="d5af2-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="d5af2-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="d5af2-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="d5af2-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="d5af2-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="d5af2-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="d5af2-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="d5af2-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="d5af2-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="d5af2-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="d5af2-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="d5af2-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="d5af2-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="d5af2-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="d5af2-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="d5af2-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="d5af2-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="d5af2-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="d5af2-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="d5af2-264">Wpisuje inną wartość **systemu** przestrzeni nazw są obsługiwane w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="d5af2-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="d5af2-265">Ponieważ kod niezarządzany już dobrze udokumentowana formatów dla tych typów, organizator ma specjalne reguły organizowanie ich.</span><span class="sxs-lookup"><span data-stu-id="d5af2-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="d5af2-266">Poniższa tabela zawiera listę typów specjalna wartość **systemu** przestrzeni nazw, a także typu niezarządzanego, są one przekazywane do.</span><span class="sxs-lookup"><span data-stu-id="d5af2-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="d5af2-267">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="d5af2-267">System value type</span></span>|<span data-ttu-id="d5af2-268">Typ pliku IDL</span><span class="sxs-lookup"><span data-stu-id="d5af2-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="d5af2-269">**DATA**</span><span class="sxs-lookup"><span data-stu-id="d5af2-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="d5af2-270">**DECIMAL**</span><span class="sxs-lookup"><span data-stu-id="d5af2-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="d5af2-271">**GUID**</span><span class="sxs-lookup"><span data-stu-id="d5af2-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="d5af2-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="d5af2-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="d5af2-273">Poniższy kod przedstawia definicję typy niezarządzanwe **data**, **GUID**, **dziesiętna**, i **OLE_COLOR** w typie Stdole2 Biblioteka.</span><span class="sxs-lookup"><span data-stu-id="d5af2-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="d5af2-274">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d5af2-274">Type library representation</span></span>  
  
```cpp  
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
  
 <span data-ttu-id="d5af2-275">Poniższy kod przedstawia odpowiadające im definicje w zarządzanej `IValueTypes` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d5af2-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="d5af2-276">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d5af2-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5af2-277">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5af2-277">See also</span></span>
- [<span data-ttu-id="d5af2-278">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="d5af2-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="d5af2-279">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="d5af2-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="d5af2-280">Domyślny marshaling dla tablic</span><span class="sxs-lookup"><span data-stu-id="d5af2-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="d5af2-281">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="d5af2-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="d5af2-282">Domyślny marshaling dla ciągów</span><span class="sxs-lookup"><span data-stu-id="d5af2-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
