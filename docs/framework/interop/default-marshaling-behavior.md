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
ms.openlocfilehash: 18282d14540027e4fae4fe152d3867ad8c223c37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181478"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="14406-102">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="14406-102">Default Marshaling Behavior</span></span>
<span data-ttu-id="14406-103">Międzyoperacyjne organizowanie działa na reguły, które określają, jak dane skojarzone z parametrami metody zachowuje się, jak przechodzi między pamięcią zarządzaną i niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="14406-103">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="14406-104">Te wbudowane reguły kontrolują takie działania organizowania jak przekształcenia typu danych, czy wywoływany może zmieniać dane przekazywane do niego i zwracać te zmiany do obiektu wywołującego i w jakich okolicznościach organizator zapewnia optymalizacje wydajności.</span><span class="sxs-lookup"><span data-stu-id="14406-104">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="14406-105">W tej sekcji identyfikuje domyślne cechy behawioralne usługi międzyoperacyjnej.</span><span class="sxs-lookup"><span data-stu-id="14406-105">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="14406-106">Przedstawia szczegółowe informacje na temat organizowania tablic, typów logicznych, typów znaków, delegatów, klas, obiektów, ciągów i struktur.</span><span class="sxs-lookup"><span data-stu-id="14406-106">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14406-107">Kierowanie typów ogólnych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="14406-107">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="14406-108">Aby uzyskać więcej informacji, zobacz [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14406-108">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="14406-109">Zarządzanie pamięcią za pomocą organizatora międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="14406-109">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="14406-110">Organizator międzyoperacyjny zawsze próbuje zwolnić pamięć przydzieloną przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="14406-110">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="14406-111">To zachowanie jest zgodne z regułami zarządzania pamięcią COM, ale różni się od reguł, które regulują natywne C++.</span><span class="sxs-lookup"><span data-stu-id="14406-111">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="14406-112">Zamieszanie może wystąpić, jeśli przewidujesz natywne zachowanie języka C++ (bez zwalniania pamięci) podczas korzystania z platformy wywołania, która automatycznie zwalnia pamięć dla wskaźników.</span><span class="sxs-lookup"><span data-stu-id="14406-112">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="14406-113">Na przykład wywołanie następującej metody niezarządzane z biblioteki DLL języka C++ nie zwalnia automatycznie pamięci.</span><span class="sxs-lookup"><span data-stu-id="14406-113">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="14406-114">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="14406-114">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="14406-115">Jeśli jednak zdefiniujesz metodę jako prototyp wywołania platformy, zastąp `MethodOne`każdy typ **BSTR** typem <xref:System.String> i wywołaj , środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="14406-115">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="14406-116">Zachowanie organizowania można zmienić <xref:System.IntPtr> przy użyciu typów, a nie **string** typów.</span><span class="sxs-lookup"><span data-stu-id="14406-116">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="14406-117">Środowisko wykonawcze zawsze używa **CoTaskMemFree** metody do zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="14406-117">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="14406-118">Jeśli pamięć, z którą pracujesz, nie została przydzielona za pomocą metody **CoTaskMemAlloc,** należy użyć **IntPtr** i zwolnić pamięć ręcznie przy użyciu odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="14406-118">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="14406-119">Podobnie można uniknąć automatycznego zwalniania pamięci w sytuacjach, w których pamięć nigdy nie powinna być zwalniana, na przykład podczas korzystania z funkcji **GetCommandLine** z pliku Kernel32.dll, która zwraca wskaźnik do pamięci jądra.</span><span class="sxs-lookup"><span data-stu-id="14406-119">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="14406-120">Aby uzyskać szczegółowe informacje na temat ręcznego zwalniania pamięci, zobacz [przykład buforów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="14406-120">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="14406-121">Domyślne kierowanie dla klas</span><span class="sxs-lookup"><span data-stu-id="14406-121">Default marshaling for classes</span></span>  
 <span data-ttu-id="14406-122">Klasy mogą być organizowane tylko przez com interop i są zawsze organizowane jako interfejsy.</span><span class="sxs-lookup"><span data-stu-id="14406-122">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="14406-123">W niektórych przypadkach interfejs używany do organizowania klasy jest znany jako interfejs klasy.</span><span class="sxs-lookup"><span data-stu-id="14406-123">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="14406-124">Aby uzyskać informacje na temat zastępowania interfejsu klasy za pomocą wybranego interfejsu, zobacz [Przedstawianie interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="14406-124">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="14406-125">Przekazywanie klas do com</span><span class="sxs-lookup"><span data-stu-id="14406-125">Passing Classes to COM</span></span>  
 <span data-ttu-id="14406-126">Gdy klasa zarządzana jest przekazywana do com, międzyoperacyjny organizator automatycznie zawija klasę z serwerem proxy COM i przekazuje interfejs klasy wytwarzany przez serwer proxy do wywołania metody COM.</span><span class="sxs-lookup"><span data-stu-id="14406-126">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="14406-127">Następnie serwer proxy deleguje wszystkie wywołania interfejsu klasy z powrotem do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="14406-127">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="14406-128">Serwer proxy udostępnia również inne interfejsy, które nie są jawnie implementowane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="14406-128">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="14406-129">Serwer proxy automatycznie implementuje interfejsy, takie jak **IUnknown** i **IDispatch** w imieniu klasy.</span><span class="sxs-lookup"><span data-stu-id="14406-129">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="14406-130">Przekazywanie klas do kodu .NET</span><span class="sxs-lookup"><span data-stu-id="14406-130">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="14406-131">Coclasses nie są zwykle używane jako argumenty metody w COM.</span><span class="sxs-lookup"><span data-stu-id="14406-131">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="14406-132">Zamiast tego domyślny interfejs jest zwykle przekazywany zamiast coclass.</span><span class="sxs-lookup"><span data-stu-id="14406-132">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="14406-133">Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyop jest odpowiedzialny za zawijanie interfejsu z właściwą otoką i przekazywanie otoki do metody zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="14406-133">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="14406-134">Określenie, które opakowanie do użycia może być trudne.</span><span class="sxs-lookup"><span data-stu-id="14406-134">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="14406-135">Każde wystąpienie obiektu COM ma pojedyncze, unikatowe otoki, bez względu na to, ile interfejsów implementuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="14406-135">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="14406-136">Na przykład pojedynczy obiekt COM, który implementuje pięć różnych interfejsów ma tylko jedną otokę.</span><span class="sxs-lookup"><span data-stu-id="14406-136">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="14406-137">Ta sama otoka udostępnia wszystkie pięć interfejsów.</span><span class="sxs-lookup"><span data-stu-id="14406-137">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="14406-138">Jeśli zostaną utworzone dwa wystąpienia obiektu COM, zostaną utworzone dwa wystąpienia otoki.</span><span class="sxs-lookup"><span data-stu-id="14406-138">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="14406-139">Dla otoki, aby zachować ten sam typ przez cały okres jego istnienia, międzyopranieżator musi zidentyfikować poprawne otoki po raz pierwszy interfejs udostępniane przez obiekt jest przekazywany przez organizatora.</span><span class="sxs-lookup"><span data-stu-id="14406-139">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="14406-140">Organizator identyfikuje obiekt, patrząc na jeden z interfejsów implementuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="14406-140">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="14406-141">Na przykład organizator określa, że otoka klasy powinna służyć do zawijania interfejsu, który został przekazany do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="14406-141">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="14406-142">Gdy interfejs jest po raz pierwszy przekazywane przez organizatora, organizator sprawdza, czy interfejs pochodzi ze znanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="14406-142">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="14406-143">Kontrola ta występuje w dwóch sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="14406-143">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="14406-144">Interfejs jest implementowany przez inny obiekt zarządzany, który został przekazany do com gdzie indziej.</span><span class="sxs-lookup"><span data-stu-id="14406-144">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="14406-145">Organizator może łatwo zidentyfikować interfejsy udostępniane przez obiekty zarządzane i jest w stanie dopasować interfejs do obiektu zarządzanego, który zapewnia implementację.</span><span class="sxs-lookup"><span data-stu-id="14406-145">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="14406-146">Obiekt zarządzany jest następnie przekazywany do metody i nie jest potrzebne otoki.</span><span class="sxs-lookup"><span data-stu-id="14406-146">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="14406-147">Obiekt, który został już opakowany implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="14406-147">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="14406-148">Aby ustalić, czy tak jest, organizator zapytania obiektu dla jego **interfejsu IUnknown** i porównuje zwrócony interfejs do interfejsów innych obiektów, które są już opakowane.</span><span class="sxs-lookup"><span data-stu-id="14406-148">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="14406-149">Jeśli interfejs jest taki sam jak w innym otoce, obiekty mają taką samą tożsamość i istniejące otoki jest przekazywana do metody.</span><span class="sxs-lookup"><span data-stu-id="14406-149">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="14406-150">Jeśli interfejs nie pochodzi ze znanego obiektu, organizator wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="14406-150">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="14406-151">Organizator zapytania obiektu dla interfejsu **IProvideClassInfo2.**</span><span class="sxs-lookup"><span data-stu-id="14406-151">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="14406-152">Jeśli pod warunkiem, organizator używa CLSID zwrócony z **IProvideClassInfo2.GetGUID** do identyfikowania coclass dostarczanie interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14406-152">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="14406-153">Za pomocą identyfikatora CLSID organizator może zlokalizować otokę z rejestru, jeśli zestaw został wcześniej zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="14406-153">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="14406-154">Organizator wysyła zapytanie do interfejsu **interfejsu IProvideClassInfo.**</span><span class="sxs-lookup"><span data-stu-id="14406-154">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="14406-155">Jeśli pod warunkiem, organizator używa **ITypeInfo** zwrócone z **IProvideClassInfo.GetClassinfo** do określenia CLSID klasy uwidaczniania interfejsu.</span><span class="sxs-lookup"><span data-stu-id="14406-155">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="14406-156">Organizator może użyć identyfikatora CLSID, aby zlokalizować metadane otoki.</span><span class="sxs-lookup"><span data-stu-id="14406-156">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="14406-157">Jeśli organizator nadal nie może zidentyfikować klasy, zawija interfejs z klasą otoki ogólnej o nazwie **System.__ComObject**.</span><span class="sxs-lookup"><span data-stu-id="14406-157">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="14406-158">Domyślne kierowanie dla delegatów</span><span class="sxs-lookup"><span data-stu-id="14406-158">Default marshaling for delegates</span></span>  
 <span data-ttu-id="14406-159">Zarządzany delegat jest organizowany jako interfejs COM lub jako wskaźnik funkcji, na podstawie mechanizmu wywołującego:</span><span class="sxs-lookup"><span data-stu-id="14406-159">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="14406-160">W przypadku wywołania platformy pełnomocnik jest domyślnie organizowany jako wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="14406-160">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="14406-161">W przypadku interop COM delegat jest organizowany jako interfejs COM typu **_Delegate** domyślnie.</span><span class="sxs-lookup"><span data-stu-id="14406-161">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="14406-162">Interfejs **_Delegate** jest zdefiniowany w bibliotece typu Mscorlib.tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodę, która umożliwia wywołanie metody, do której odwołuje się delegat.</span><span class="sxs-lookup"><span data-stu-id="14406-162">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="14406-163">W poniższej tabeli przedstawiono opcje organizowania dla typu danych zarządzanych delegatów.</span><span class="sxs-lookup"><span data-stu-id="14406-163">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="14406-164">Atrybut <xref:System.Runtime.InteropServices.MarshalAsAttribute> zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do delegatów marshal.</span><span class="sxs-lookup"><span data-stu-id="14406-164">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="14406-165">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="14406-165">Enumeration type</span></span>|<span data-ttu-id="14406-166">Opis formatu niezarządzanego</span><span class="sxs-lookup"><span data-stu-id="14406-166">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="14406-167">**NiezarządzaneType.FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="14406-167">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="14406-168">Wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="14406-168">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="14406-169">**Niezarządzany typ.interfejs**</span><span class="sxs-lookup"><span data-stu-id="14406-169">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="14406-170">Interfejs typu **_Delegate**, zgodnie z definicją w mscorlib.tlb.</span><span class="sxs-lookup"><span data-stu-id="14406-170">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="14406-171">Należy wziąć pod uwagę poniższy `DelegateTestInterface` przykładowy kod, w którym metody są eksportowane do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="14406-171">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="14406-172">Należy zauważyć, że tylko delegatów **oznaczonych ref** (lub **ByRef**) słowo kluczowe są przekazywane jako in/out parametry.</span><span class="sxs-lookup"><span data-stu-id="14406-172">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="14406-173">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="14406-173">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="14406-174">Wskaźnik funkcji może być wyłuskiwane, podobnie jak każdy inny wskaźnik funkcji niezarządzane mogą być wyłuskiwane.</span><span class="sxs-lookup"><span data-stu-id="14406-174">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="14406-175">W tym przykładzie, gdy dwóch delegatów są organizowane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, wynik jest `int` i wskaźnik do . `int`</span><span class="sxs-lookup"><span data-stu-id="14406-175">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="14406-176">Ponieważ typy delegata `int` są organizowane, w`void*`tym miejscu reprezentuje wskaźnik do void ( ), który jest adres delegata w pamięci.</span><span class="sxs-lookup"><span data-stu-id="14406-176">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="14406-177">Innymi słowy ten wynik jest specyficzne dla 32-bitowych systemów Windows, ponieważ `int` w tym miejscu reprezentuje rozmiar wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="14406-177">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="14406-178">Odwołanie do wskaźnika funkcji do zarządzanego delegata przechowywanego przez kod niezarządzany nie uniemożliwia wykonywania środowiska wykonawczego języka wspólnego w obiekcie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="14406-178">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="14406-179">Na przykład poniższy kod jest niepoprawna, ponieważ `cb` odwołanie `SetChangeHandler` do obiektu, `cb` przekazane do metody, nie utrzymuje przy życiu poza okresem `Test` życia metody.</span><span class="sxs-lookup"><span data-stu-id="14406-179">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="14406-180">Gdy `cb` obiekt jest zbierane śmieci, wskaźnik `SetChangeHandler` funkcji przekazany do nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="14406-180">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="14406-181">Aby zrekompensować nieoczekiwane wyrzucania elementów `cb` bezużytecznych, obiekt wywołujący musi upewnić się, że obiekt jest utrzymywany przy życiu tak długo, jak wskaźnik funkcji niezarządzane jest w użyciu.</span><span class="sxs-lookup"><span data-stu-id="14406-181">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="14406-182">Opcjonalnie można mieć kod niezarządzany powiadamiać kod zarządzany, gdy wskaźnik funkcji nie jest już potrzebne, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="14406-182">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="14406-183">Domyślne kierowanie dla typów wartości</span><span class="sxs-lookup"><span data-stu-id="14406-183">Default marshaling for value types</span></span>  
 <span data-ttu-id="14406-184">Większość typów wartości, takich jak liczby całkowite i numery zmiennoprzecinkowe, są [blittable](blittable-and-non-blittable-types.md) i nie wymagają organizowania.</span><span class="sxs-lookup"><span data-stu-id="14406-184">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="14406-185">Inne [typy niedlażne](blittable-and-non-blittable-types.md) mają różne reprezentacje w pamięci zarządzanej i niezarządzanej i wymagają organizowania.</span><span class="sxs-lookup"><span data-stu-id="14406-185">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="14406-186">Nadal inne typy wymagają jawnego formatowania w granicach współdziałania.</span><span class="sxs-lookup"><span data-stu-id="14406-186">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="14406-187">Ta sekcja zawiera informacje na temat następujących sformatowanych typów wartości:</span><span class="sxs-lookup"><span data-stu-id="14406-187">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="14406-188">Typy wartości używane w wywoływaniu platformy</span><span class="sxs-lookup"><span data-stu-id="14406-188">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="14406-189">Typy wartości używane w com interop</span><span class="sxs-lookup"><span data-stu-id="14406-189">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="14406-190">Oprócz opisywania sformatowanych typów w tym temacie identyfikowane [są typy wartości systemowej,](#system-value-types) które mają nietypowe zachowanie organizowania.</span><span class="sxs-lookup"><span data-stu-id="14406-190">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="14406-191">Sformatowany typ jest typem złożonym, który zawiera informacje, które jawnie kontroluje układ jego członków w pamięci.</span><span class="sxs-lookup"><span data-stu-id="14406-191">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="14406-192">Informacje o układzie elementu <xref:System.Runtime.InteropServices.StructLayoutAttribute> członkowskiego są dostarczane przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="14406-192">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="14406-193">Układ może być jedną <xref:System.Runtime.InteropServices.LayoutKind> z następujących wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="14406-193">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="14406-194">**LayoutKind.Automatic**</span><span class="sxs-lookup"><span data-stu-id="14406-194">**LayoutKind.Automatic**</span></span>  
  
     <span data-ttu-id="14406-195">Wskazuje, że środowisko uruchomieniowe języka wspólnego jest wolne do ponownego zamówenia elementów członkowskich typu dla wydajności.</span><span class="sxs-lookup"><span data-stu-id="14406-195">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="14406-196">Jednak gdy typ wartości jest przekazywany do kodu niezarządzanego, układ elementów członkowskich jest przewidywalny.</span><span class="sxs-lookup"><span data-stu-id="14406-196">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="14406-197">Próba zorganizowania takiej struktury automatycznie powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="14406-197">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="14406-198">**Layoutkind.sequential**</span><span class="sxs-lookup"><span data-stu-id="14406-198">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="14406-199">Wskazuje, że elementy członkowskie typu mają być określone w pamięci niezarządzanej w tej samej kolejności, w jakiej pojawiają się w definicji typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="14406-199">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="14406-200">**Layoutkind.explicit**</span><span class="sxs-lookup"><span data-stu-id="14406-200">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="14406-201">Wskazuje, że elementy członkowskie są <xref:System.Runtime.InteropServices.FieldOffsetAttribute> rozmieszczone zgodnie z dostarczonymi z każdym polem.</span><span class="sxs-lookup"><span data-stu-id="14406-201">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="14406-202">Typy wartości używane w wywoływaniu platformy</span><span class="sxs-lookup"><span data-stu-id="14406-202">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="14406-203">W poniższym `Point` przykładzie i `Rect` typy zawierają informacje o układzie elementu członkowskiego przy użyciu **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="14406-203">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="14406-204">Gdy kierowane do kodu niezarządzanego, te sformatowane typy są organizowane jako struktury w stylu C.</span><span class="sxs-lookup"><span data-stu-id="14406-204">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="14406-205">Zapewnia to łatwy sposób wywoływania niezarządzanego interfejsu API, który ma argumenty struktury.</span><span class="sxs-lookup"><span data-stu-id="14406-205">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="14406-206">Na przykład `POINT` struktury `RECT` i mogą być przekazywane do funkcji **PtInRect** interfejsu API systemu Microsoft Windows w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14406-206">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="14406-207">Struktury można przekazać przy użyciu następującej definicji wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="14406-207">You can pass structures using the following platform invoke definition:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function PtInRect Lib "User32.dll" (
        ByRef r As Rect, p As Point) As Boolean
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("User32.dll")]
   internal static extern bool PtInRect(ref Rect r, Point p);
}
```
  
 <span data-ttu-id="14406-208">Typ `Rect` wartości musi być przekazywany przez odwołanie, ponieważ niezarządzany interfejs API oczekuje `RECT` wskaźnika do przekazania do funkcji.</span><span class="sxs-lookup"><span data-stu-id="14406-208">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="14406-209">Typ `Point` wartości jest przekazywany przez wartość, ponieważ `POINT` niezarządzany interfejs API oczekuje, że mają być przekazywane na stosie.</span><span class="sxs-lookup"><span data-stu-id="14406-209">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="14406-210">Ta subtelna różnica jest bardzo ważna.</span><span class="sxs-lookup"><span data-stu-id="14406-210">This subtle difference is very important.</span></span> <span data-ttu-id="14406-211">Odwołania są przekazywane do kodu niezarządzanego jako wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="14406-211">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="14406-212">Wartości są przekazywane do kodu niezarządzanego na stosie.</span><span class="sxs-lookup"><span data-stu-id="14406-212">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14406-213">Gdy sformatowany typ jest zorganizowany jako struktura, tylko pola w typie są dostępne.</span><span class="sxs-lookup"><span data-stu-id="14406-213">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="14406-214">Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="14406-214">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="14406-215">Klasy mogą być również kierowane do kodu niezarządzanego jako struktury w stylu C, pod warunkiem, że mają stały układ elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="14406-215">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="14406-216">Informacje o układzie członkowskim dla klasy <xref:System.Runtime.InteropServices.StructLayoutAttribute> są również dostarczane z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="14406-216">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="14406-217">Główną różnicą między typami wartości o stałym układzie i klas o stałym układzie jest sposób, w jaki są one kierowane do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="14406-217">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="14406-218">Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszelkie zmiany wprowadzone do elementów członkowskich typu przez wywoływanego nie są widoczne przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="14406-218">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="14406-219">Typy odwołań są przekazywane przez odwołanie (odwołanie do typu jest przekazywana na stosie); w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu blittable typu typu przez wywoływanego są widoczne przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="14406-219">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14406-220">Jeśli typ odwołania ma członków typów nieblittable, konwersja jest wymagana dwa razy: po raz pierwszy, gdy argument jest przekazywany do strony niezarządzanej i po raz drugi po powrocie z wywołania.</span><span class="sxs-lookup"><span data-stu-id="14406-220">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="14406-221">Ze względu na to dodatkowe obciążenie, in/out parametry muszą być jawnie stosowane do argumentu, jeśli wywołujący chce zobaczyć zmiany wprowadzone przez wywoływanego.</span><span class="sxs-lookup"><span data-stu-id="14406-221">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="14406-222">W poniższym przykładzie `SystemTime` klasa ma sekwencyjny układ elementu członkowskiego i może być przekazywana do funkcji **GetSystemTime** interfejsu API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="14406-222">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="14406-223">Funkcja **GetSystemTime** jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="14406-223">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="14406-224">Równoważna definicja wywołania platformy dla **Systemu GetSystemTime** jest następująca:</span><span class="sxs-lookup"><span data-stu-id="14406-224">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Sub GetSystemTime Lib "Kernel32.dll" (
        ByVal sysTime As SystemTime)
End Class
```
  
```csharp
internal static class NativeMethods
{
   [DllImport("Kernel32.dll", CharSet = CharSet.Auto)]
   internal static extern void GetSystemTime(SystemTime st);
}
```
  
 <span data-ttu-id="14406-225">Należy zauważyć, że `SystemTime` argument nie jest `SystemTime` wpisywany jako argument odwołania, ponieważ jest klasą, a nie typem wartości.</span><span class="sxs-lookup"><span data-stu-id="14406-225">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="14406-226">W przeciwieństwie do typów wartości klasy są zawsze przekazywane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="14406-226">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="14406-227">Poniższy przykład kodu `Point` pokazuje inną klasę, `SetXY`która ma metodę o nazwie .</span><span class="sxs-lookup"><span data-stu-id="14406-227">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="14406-228">Ponieważ typ ma układ sekwencyjny, może być przekazywana do kodu niezarządzanego i kierowane jako struktura.</span><span class="sxs-lookup"><span data-stu-id="14406-228">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="14406-229">Jednak element `SetXY` członkowski nie jest wywoływany z kodu niezarządzanego, nawet jeśli obiekt jest przekazywany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="14406-229">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="14406-230">Typy wartości używane w com interop</span><span class="sxs-lookup"><span data-stu-id="14406-230">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="14406-231">Sformatowane typy mogą być również przekazywane do wywołań metody współdziałać COM.</span><span class="sxs-lookup"><span data-stu-id="14406-231">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="14406-232">W rzeczywistości po wyeksportowaniu do biblioteki typów typów wartości są automatycznie konwertowane na struktury.</span><span class="sxs-lookup"><span data-stu-id="14406-232">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="14406-233">Jak pokazano w poniższym `Point` przykładzie, typ wartości staje się `Point`definicją typu (typedef) o nazwie .</span><span class="sxs-lookup"><span data-stu-id="14406-233">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="14406-234">Wszystkie odwołania do `Point` typu wartości w innym miejscu `Point` w bibliotece typów są zastępowane typedef.</span><span class="sxs-lookup"><span data-stu-id="14406-234">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="14406-235">**Reprezentacja biblioteki typów**</span><span class="sxs-lookup"><span data-stu-id="14406-235">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="14406-236">Te same reguły używane do organizowania wartości i odwołania do wywołania platformy są używane podczas organizowania za pośrednictwem interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="14406-236">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="14406-237">Na przykład gdy wystąpienie `Point` typu wartości jest przekazywana z `Point` programu .NET Framework do COM, jest przekazywana przez wartość.</span><span class="sxs-lookup"><span data-stu-id="14406-237">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="14406-238">Jeśli `Point` typ wartości jest przekazywany przez `Point` odwołanie, wskaźnik do a jest przekazywany na stosie.</span><span class="sxs-lookup"><span data-stu-id="14406-238">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="14406-239">Organizator międzyoperacyjny nie obsługuje wyższych poziomów pośrednich (**Punkt** \* \*) w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="14406-239">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="14406-240">Struktury o <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia ustawionej **na Jawne** nie można używać w współdziałanie COM, ponieważ eksportowana biblioteka typów nie może wyrazić jawnego układu.</span><span class="sxs-lookup"><span data-stu-id="14406-240">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="14406-241">Typy wartości systemowych</span><span class="sxs-lookup"><span data-stu-id="14406-241">System Value Types</span></span>  
 <span data-ttu-id="14406-242">Obszar <xref:System> nazw ma kilka typów wartości, które reprezentują formę pudełkową typów pierwotnych środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="14406-242">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="14406-243">Na przykład struktura <xref:System.Int32?displayProperty=nameWithType> typu wartości reprezentuje formę ELEMENT_TYPE_I4 **.**</span><span class="sxs-lookup"><span data-stu-id="14406-243">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="14406-244">Zamiast organizowania tych typów jako struktur, jak inne typy sformatowane są, kierunkować je w taki sam sposób jak typy pierwotne, które polu.</span><span class="sxs-lookup"><span data-stu-id="14406-244">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="14406-245">**System.Int32** jest zatem organizowany jako **ELEMENT_TYPE_I4,** a nie jako struktura zawierająca pojedynczy element członkowski typu **long**.</span><span class="sxs-lookup"><span data-stu-id="14406-245">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="14406-246">Poniższa tabela zawiera listę typów wartości w obszarze nazw **system,** które są pudełkowymi reprezentacjami typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="14406-246">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="14406-247">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="14406-247">System value type</span></span>|<span data-ttu-id="14406-248">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="14406-248">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="14406-249">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="14406-249">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="14406-250">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="14406-250">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="14406-251">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="14406-251">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="14406-252">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="14406-252">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="14406-253">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="14406-253">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="14406-254">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="14406-254">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="14406-255">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="14406-255">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="14406-256">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="14406-256">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="14406-257">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="14406-257">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="14406-258">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="14406-258">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="14406-259">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="14406-259">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="14406-260">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="14406-260">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="14406-261">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="14406-261">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="14406-262">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="14406-262">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="14406-263">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="14406-263">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="14406-264">Niektóre inne typy wartości w obszarze nazw **systemu** są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="14406-264">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="14406-265">Ponieważ kod niezarządzany ma już ugruntowane formaty dla tych typów, organizator ma specjalne reguły dotyczące organizowania ich.</span><span class="sxs-lookup"><span data-stu-id="14406-265">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="14406-266">W poniższej tabeli wymieniono specjalne typy wartości w obszarze nazw **systemu,** a także typ niezarządzany, do których są organizowane.</span><span class="sxs-lookup"><span data-stu-id="14406-266">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="14406-267">Typ wartości systemu</span><span class="sxs-lookup"><span data-stu-id="14406-267">System value type</span></span>|<span data-ttu-id="14406-268">Typ IDL</span><span class="sxs-lookup"><span data-stu-id="14406-268">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="14406-269">**Data**</span><span class="sxs-lookup"><span data-stu-id="14406-269">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="14406-270">**Dziesiętnych**</span><span class="sxs-lookup"><span data-stu-id="14406-270">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="14406-271">**Identyfikator guid**</span><span class="sxs-lookup"><span data-stu-id="14406-271">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="14406-272">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="14406-272">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="14406-273">Poniższy kod przedstawia definicję niezarządzanych typów **DATE,** **GUID,** **DECIMAL**i **OLE_COLOR** w bibliotece typów Stdole2.</span><span class="sxs-lookup"><span data-stu-id="14406-273">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="14406-274">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="14406-274">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="14406-275">Poniższy kod przedstawia odpowiednie definicje `IValueTypes` w interfejsie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="14406-275">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="14406-276">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="14406-276">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="14406-277">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="14406-277">See also</span></span>

- [<span data-ttu-id="14406-278">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="14406-278">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="14406-279">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="14406-279">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="14406-280">Organizowanie domyślne dotyczące tablic</span><span class="sxs-lookup"><span data-stu-id="14406-280">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="14406-281">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="14406-281">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="14406-282">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="14406-282">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
