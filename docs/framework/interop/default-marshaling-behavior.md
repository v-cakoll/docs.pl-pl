---
title: Domyślne zachowanie marshalingu
description: Poznaj domyślne zachowanie organizowania w programie .NET. Przejrzyj zarządzanie pamięcią za pomocą organizowania międzyoperacyjności i zobacz domyślne kierowanie dla klas, delegatów i typów wartości.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, default
- interoperation with unmanaged code, marshaling
- marshaling behavior
ms.assetid: c0a9bcdf-3df8-4db3-b1b6-abbdb2af809a
ms.openlocfilehash: 0469874d016725eb6423bb8453e9657b2be923d4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618574"
---
# <a name="default-marshaling-behavior"></a><span data-ttu-id="e414e-104">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="e414e-104">Default Marshaling Behavior</span></span>
<span data-ttu-id="e414e-105">Kierowanie międzyoperacyjności operuje na regułach, które określają sposób, w jaki dane skojarzone z parametrami metod działają w miarę przekazywania między pamięcią zarządzaną i niezarządzaną.</span><span class="sxs-lookup"><span data-stu-id="e414e-105">Interop marshaling operates on rules that dictate how data associated with method parameters behaves as it passes between managed and unmanaged memory.</span></span> <span data-ttu-id="e414e-106">Te wbudowane reguły kontrolują takie działania kierujące jako przekształcenia typu danych, niezależnie od tego, czy wywoływany może zmienić dane przekazywane do niego, i zwrócić te zmiany do obiektu wywołującego, i w jakich okolicznościach Organizator zapewnia optymalizację wydajności.</span><span class="sxs-lookup"><span data-stu-id="e414e-106">These built-in rules control such marshaling activities as data type transformations, whether a callee can change data passed to it and return those changes to the caller, and under which circumstances the marshaler provides performance optimizations.</span></span>  
  
 <span data-ttu-id="e414e-107">W tej sekcji opisano domyślne właściwości behawioralne usługi organizowania międzyoperacyjnego.</span><span class="sxs-lookup"><span data-stu-id="e414e-107">This section identifies the default behavioral characteristics of the interop marshaling service.</span></span> <span data-ttu-id="e414e-108">Przedstawia szczegółowe informacje na temat organizowania tablic, typów logicznych, typów znaków, delegatów, klas, obiektów, ciągów i struktur.</span><span class="sxs-lookup"><span data-stu-id="e414e-108">It presents detailed information on marshaling arrays, Boolean types, char types, delegates, classes, objects, strings, and structures.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e414e-109">Kierowanie typów ogólnych nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="e414e-109">Marshaling of generic types is not supported.</span></span> <span data-ttu-id="e414e-110">Aby uzyskać więcej informacji, zobacz [współdziałanie przy użyciu typów ogólnych](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e414e-110">For more information see, [Interoperating Using Generic Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms229590(v=vs.100)).</span></span>  
  
## <a name="memory-management-with-the-interop-marshaler"></a><span data-ttu-id="e414e-111">Zarządzanie pamięcią za pomocą Organizatora międzyoperacyjnego</span><span class="sxs-lookup"><span data-stu-id="e414e-111">Memory management with the interop marshaler</span></span>  
 <span data-ttu-id="e414e-112">Organizator międzyoperacyjny zawsze próbuje zwolnić pamięć przydzieloną przez kod niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="e414e-112">The interop marshaler always attempts to free memory allocated by unmanaged code.</span></span> <span data-ttu-id="e414e-113">To zachowanie jest zgodne z regułami zarządzania pamięcią COM, ale różni się od zasad, które regulują natywne C++.</span><span class="sxs-lookup"><span data-stu-id="e414e-113">This behavior complies with COM memory management rules, but differs from the rules that govern native C++.</span></span>  
  
 <span data-ttu-id="e414e-114">Może wystąpić sytuacja, w której przewidywane jest zachowanie natywnego języka C++ (bez zwalniania pamięci) podczas korzystania z funkcji wywołania platformy, która automatycznie zwalnia pamięć dla wskaźników.</span><span class="sxs-lookup"><span data-stu-id="e414e-114">Confusion can arise if you anticipate native C++ behavior (no memory freeing) when using platform invoke, which automatically frees memory for pointers.</span></span> <span data-ttu-id="e414e-115">Na przykład, wywołanie następującej niezarządzanej metody z biblioteki C++ DLL nie zwalnia automatycznie żadnej pamięci.</span><span class="sxs-lookup"><span data-stu-id="e414e-115">For example, calling the following unmanaged method from a C++ DLL does not automatically free any memory.</span></span>  
  
### <a name="unmanaged-signature"></a><span data-ttu-id="e414e-116">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="e414e-116">Unmanaged signature</span></span>  
  
```cpp  
BSTR MethodOne (BSTR b) {  
     return b;  
}  
```  
  
 <span data-ttu-id="e414e-117">Jednakże w przypadku zdefiniowania metody jako prototypu wywołania platformy Zastąp każdy typ **BSTR** typem <xref:System.String> , a wywołanie `MethodOne` , środowisko uruchomieniowe języka wspólnego próbuje zwolnić `b` dwa razy.</span><span class="sxs-lookup"><span data-stu-id="e414e-117">However, if you define the method as a platform invoke prototype, replace each **BSTR** type with a <xref:System.String> type, and call `MethodOne`, the common language runtime attempts to free `b` twice.</span></span> <span data-ttu-id="e414e-118">Zachowanie organizowania można zmienić przy użyciu <xref:System.IntPtr> typów, a nie typów **ciągów** .</span><span class="sxs-lookup"><span data-stu-id="e414e-118">You can change the marshaling behavior by using <xref:System.IntPtr> types rather than **String** types.</span></span>  
  
 <span data-ttu-id="e414e-119">Środowisko uruchomieniowe zawsze używa metody **CoTaskMemFree** do zwolnienia pamięci.</span><span class="sxs-lookup"><span data-stu-id="e414e-119">The runtime always uses the **CoTaskMemFree** method to free memory.</span></span> <span data-ttu-id="e414e-120">Jeśli pamięć, z którą pracujesz, nie została przypisana przy użyciu metody **CoTaskMemAlloc** , należy użyć elementu **IntPtr** i zwolnić pamięć ręcznie przy użyciu odpowiedniej metody.</span><span class="sxs-lookup"><span data-stu-id="e414e-120">If the memory you are working with was not allocated with the **CoTaskMemAlloc** method, you must use an **IntPtr** and free the memory manually using the appropriate method.</span></span> <span data-ttu-id="e414e-121">Podobnie można uniknąć automatycznej zwalniania pamięci w sytuacjach, w których pamięć nigdy nie powinna zostać zwolniona, na przykład przy użyciu funkcji **GetCommandLine** z Kernel32.dll, która zwraca wskaźnik do pamięci jądra.</span><span class="sxs-lookup"><span data-stu-id="e414e-121">Similarly, you can avoid automatic memory freeing in situations where memory should never be freed, such as when using the **GetCommandLine** function from Kernel32.dll, which returns a pointer to kernel memory.</span></span> <span data-ttu-id="e414e-122">Aby uzyskać szczegółowe informacje na temat ręcznego zwalniania pamięci, zobacz [przykładowe bufory](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e414e-122">For details on manually freeing memory, see the [Buffers Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/x3txb6xc(v=vs.100)).</span></span>  
  
## <a name="default-marshaling-for-classes"></a><span data-ttu-id="e414e-123">Kierowanie domyślne dla klas</span><span class="sxs-lookup"><span data-stu-id="e414e-123">Default marshaling for classes</span></span>  
 <span data-ttu-id="e414e-124">Klasy mogą być organizowane tylko przez międzyoperacyjność modelu COM i są zawsze organizowane jako interfejsy.</span><span class="sxs-lookup"><span data-stu-id="e414e-124">Classes can be marshaled only by COM interop and are always marshaled as interfaces.</span></span> <span data-ttu-id="e414e-125">W niektórych przypadkach interfejs używany do organizowania klasy jest nazywany interfejsem klasy.</span><span class="sxs-lookup"><span data-stu-id="e414e-125">In some cases the interface used to marshal the class is known as the class interface.</span></span> <span data-ttu-id="e414e-126">Aby uzyskać informacje na temat przesłaniania interfejsu klasy z wybranym interfejsem, zobacz [wprowadzenie do interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="e414e-126">For information about overriding the class interface with an interface of your choice, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
### <a name="passing-classes-to-com"></a><span data-ttu-id="e414e-127">Przekazywanie klas do modelu COM</span><span class="sxs-lookup"><span data-stu-id="e414e-127">Passing Classes to COM</span></span>  
 <span data-ttu-id="e414e-128">Gdy zarządzana Klasa jest przekazywana do modelu COM, organizator międzyoperacyjny automatycznie zawija klasę z serwerem proxy modelu COM i przekazuje interfejs klasy utworzony przez serwer proxy do wywołania metody COM.</span><span class="sxs-lookup"><span data-stu-id="e414e-128">When a managed class is passed to COM, the interop marshaler automatically wraps the class with a COM proxy and passes the class interface produced by the proxy to the COM method call.</span></span> <span data-ttu-id="e414e-129">Następnie serwer proxy deleguje wszystkie wywołania w interfejsie klasy z powrotem do obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-129">The proxy then delegates all calls on the class interface back to the managed object.</span></span> <span data-ttu-id="e414e-130">Serwer proxy ujawnia również inne interfejsy, które nie są jawnie zaimplementowane przez klasę.</span><span class="sxs-lookup"><span data-stu-id="e414e-130">The proxy also exposes other interfaces that are not explicitly implemented by the class.</span></span> <span data-ttu-id="e414e-131">Serwer proxy automatycznie implementuje interfejsy, takie jak **IUnknown** i **IDispatch** w imieniu klasy.</span><span class="sxs-lookup"><span data-stu-id="e414e-131">The proxy automatically implements interfaces such as **IUnknown** and **IDispatch** on behalf of the class.</span></span>  
  
### <a name="passing-classes-to-net-code"></a><span data-ttu-id="e414e-132">Przekazywanie klas do kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="e414e-132">Passing Classes to .NET Code</span></span>  
 <span data-ttu-id="e414e-133">Klasy coclass nie są zwykle używane jako argumenty metod w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e414e-133">Coclasses are not typically used as method arguments in COM.</span></span> <span data-ttu-id="e414e-134">Zamiast tego, domyślnym interfejsem jest zwykle przekazanie zamiast klasy coclass.</span><span class="sxs-lookup"><span data-stu-id="e414e-134">Instead, a default interface is usually passed in place of the coclass.</span></span>  
  
 <span data-ttu-id="e414e-135">Gdy interfejs jest przekazywany do kodu zarządzanego, organizator międzyoperacyjny jest odpowiedzialny za pakowanie interfejsu z odpowiednią otoką i przekazanie otoki do metody zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="e414e-135">When an interface is passed into managed code, the interop marshaler is responsible for wrapping the interface with the proper wrapper and passing the wrapper to the managed method.</span></span> <span data-ttu-id="e414e-136">Określanie otoki, która ma być używana, może być trudne.</span><span class="sxs-lookup"><span data-stu-id="e414e-136">Determining which wrapper to use can be difficult.</span></span> <span data-ttu-id="e414e-137">Każde wystąpienie obiektu COM ma pojedynczą, unikatową otokę, niezależnie od liczby interfejsów implementujących obiekt.</span><span class="sxs-lookup"><span data-stu-id="e414e-137">Every instance of a COM object has a single, unique wrapper, no matter how many interfaces the object implements.</span></span> <span data-ttu-id="e414e-138">Na przykład pojedynczy obiekt COM, który implementuje pięć odrębnych interfejsów, ma tylko jedną otokę.</span><span class="sxs-lookup"><span data-stu-id="e414e-138">For example, a single COM object that implements five distinct interfaces has only one wrapper.</span></span> <span data-ttu-id="e414e-139">Ta sama otoka uwidacznia wszystkie pięć interfejsów.</span><span class="sxs-lookup"><span data-stu-id="e414e-139">The same wrapper exposes all five interfaces.</span></span> <span data-ttu-id="e414e-140">Jeśli tworzone są dwa wystąpienia obiektu COM, tworzone są dwa wystąpienia otoki.</span><span class="sxs-lookup"><span data-stu-id="e414e-140">If two instances of the COM object are created, then two instances of the wrapper are created.</span></span>  
  
 <span data-ttu-id="e414e-141">Aby otoka mogła obsługiwać ten sam typ w całym okresie istnienia, organizator międzyoperacyjny musi identyfikować poprawną otokę, gdy interfejs uwidoczniony przez obiekt jest przekazywany przez organizatora.</span><span class="sxs-lookup"><span data-stu-id="e414e-141">For the wrapper to maintain the same type throughout its lifetime, the interop marshaler must identify the correct wrapper the first time an interface exposed by the object is passed through the marshaler.</span></span> <span data-ttu-id="e414e-142">Organizator identyfikuje obiekt, przeglądając jeden z interfejsów implementujących obiekt.</span><span class="sxs-lookup"><span data-stu-id="e414e-142">The marshaler identifies the object by looking at one of the interfaces the object implements.</span></span>  
  
 <span data-ttu-id="e414e-143">Na przykład Organizator określa, że otoka klasy ma być używana do zawijania interfejsu, który został przekazano do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-143">For example, the marshaler determines that the class wrapper should be used to wrap the interface that was passed into managed code.</span></span> <span data-ttu-id="e414e-144">Gdy interfejs jest po raz pierwszy przekazywany przez organizatora, organizator sprawdza, czy interfejs pochodzi z znanego obiektu.</span><span class="sxs-lookup"><span data-stu-id="e414e-144">When the interface is first passed through the marshaler, the marshaler checks whether the interface is coming from a known object.</span></span> <span data-ttu-id="e414e-145">To sprawdzenie odbywa się w dwóch sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="e414e-145">This check occurs in two situations:</span></span>  
  
- <span data-ttu-id="e414e-146">Interfejs jest implementowany przez inny zarządzany obiekt, który został przekazano do modelu COM w innym miejscu.</span><span class="sxs-lookup"><span data-stu-id="e414e-146">An interface is being implemented by another managed object that was passed to COM elsewhere.</span></span> <span data-ttu-id="e414e-147">Organizator może łatwo identyfikować interfejsy udostępniane przez zarządzane obiekty i jest w stanie dopasować interfejs z zarządzanym obiektem, który udostępnia implementację.</span><span class="sxs-lookup"><span data-stu-id="e414e-147">The marshaler can readily identify interfaces exposed by managed objects and is able to match the interface with the managed object that provides the implementation.</span></span> <span data-ttu-id="e414e-148">Obiekt zarządzany jest następnie przekazywać do metody, a otoka nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="e414e-148">The managed object is then passed to the method and no wrapper is needed.</span></span>  
  
- <span data-ttu-id="e414e-149">Obiekt, który został już opakowany, implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="e414e-149">An object that has already been wrapped is implementing the interface.</span></span> <span data-ttu-id="e414e-150">Aby określić, czy tak jest, organizator wysyła zapytanie do obiektu w interfejsie **IUnknown** i porównuje zwracany interfejs do interfejsów innych obiektów, które zostały już opakowane.</span><span class="sxs-lookup"><span data-stu-id="e414e-150">To determine whether this is the case, the marshaler queries the object for its **IUnknown** interface and compares the returned interface to the interfaces of other objects that are already wrapped.</span></span> <span data-ttu-id="e414e-151">Jeśli interfejs jest taki sam jak w przypadku innych otok, obiekty mają taką samą tożsamość, a istniejąca otoka jest przenoszona do metody.</span><span class="sxs-lookup"><span data-stu-id="e414e-151">If the interface is the same as that of another wrapper, the objects have the same identity and the existing wrapper is passed to the method.</span></span>  
  
 <span data-ttu-id="e414e-152">Jeśli interfejs nie pochodzi z znanego obiektu, organizator wykonuje następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e414e-152">If an interface is not from a known object, the marshaler does the following:</span></span>  
  
1. <span data-ttu-id="e414e-153">Organizator wysyła zapytanie do obiektu dla interfejsu **IProvideClassInfo2** .</span><span class="sxs-lookup"><span data-stu-id="e414e-153">The marshaler queries the object for the **IProvideClassInfo2** interface.</span></span> <span data-ttu-id="e414e-154">Jeśli jest podany, organizator używa identyfikatora CLSID zwróconego z **IProvideClassInfo2. GetGuid** do identyfikowania klasy coclass dostarczającej interfejs.</span><span class="sxs-lookup"><span data-stu-id="e414e-154">If provided, the marshaler uses the CLSID returned from **IProvideClassInfo2.GetGUID** to identify the coclass providing the interface.</span></span> <span data-ttu-id="e414e-155">Przy użyciu identyfikatora CLSID Organizator może zlokalizować otokę z rejestru, jeśli zestaw został wcześniej zarejestrowany.</span><span class="sxs-lookup"><span data-stu-id="e414e-155">With the CLSID, the marshaler can locate the wrapper from the registry if the assembly has previously been registered.</span></span>  
  
2. <span data-ttu-id="e414e-156">Organizator wysyła zapytanie do interfejsu dla interfejsu **IProvideClassInfo** .</span><span class="sxs-lookup"><span data-stu-id="e414e-156">The marshaler queries the interface for the **IProvideClassInfo** interface.</span></span> <span data-ttu-id="e414e-157">Jeśli jest podany, organizator używa **Metoda ITypeInfo** zwrócone z **IProvideClassInfo. GetClassInfo** , aby określić identyfikator CLSID klasy, która uwidacznia interfejs.</span><span class="sxs-lookup"><span data-stu-id="e414e-157">If provided, the marshaler uses the **ITypeInfo** returned from **IProvideClassInfo.GetClassinfo** to determine the CLSID of the class exposing the interface.</span></span> <span data-ttu-id="e414e-158">Organizator może użyć identyfikatora CLSID, aby zlokalizować metadane dla otoki.</span><span class="sxs-lookup"><span data-stu-id="e414e-158">The marshaler can use the CLSID to locate the metadata for the wrapper.</span></span>  
  
3. <span data-ttu-id="e414e-159">Jeśli organizator nadal nie może zidentyfikować klasy, zawija interfejs z klasą otoki ogólnej o nazwie **System. __ComObject**.</span><span class="sxs-lookup"><span data-stu-id="e414e-159">If the marshaler still cannot identify the class, it wraps the interface with a generic wrapper class called **System.__ComObject**.</span></span>  
  
## <a name="default-marshaling-for-delegates"></a><span data-ttu-id="e414e-160">Kierowanie domyślne dla delegatów</span><span class="sxs-lookup"><span data-stu-id="e414e-160">Default marshaling for delegates</span></span>  
 <span data-ttu-id="e414e-161">Zarządzany delegat jest zorganizowany jako interfejs COM lub jako wskaźnik funkcji, na podstawie mechanizmu wywołującego:</span><span class="sxs-lookup"><span data-stu-id="e414e-161">A managed delegate is marshaled as a COM interface or as a function pointer, based on the calling mechanism:</span></span>  
  
- <span data-ttu-id="e414e-162">W przypadku wywołania platformy delegat jest domyślnie zorganizowany jako niezarządzany wskaźnik funkcji.</span><span class="sxs-lookup"><span data-stu-id="e414e-162">For platform invoke, a delegate is marshaled as an unmanaged function pointer by default.</span></span>  
  
- <span data-ttu-id="e414e-163">W przypadku międzyoperacyjności modelu COM delegat jest domyślnie zorganizowany jako interfejs COM typu **_Delegate** .</span><span class="sxs-lookup"><span data-stu-id="e414e-163">For COM interop, a delegate is marshaled as a COM interface of type **_Delegate** by default.</span></span> <span data-ttu-id="e414e-164">Interfejs **_Delegate** jest zdefiniowany w bibliotece typów mscorlib. tlb i zawiera <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> metodę, która umożliwia wywołanie metody, która odwołuje się do obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-164">The **_Delegate** interface is defined in the Mscorlib.tlb type library and contains the <xref:System.Delegate.DynamicInvoke%2A?displayProperty=nameWithType> method, which enables you to call the method that the delegate references.</span></span>  
  
 <span data-ttu-id="e414e-165">W poniższej tabeli przedstawiono opcje kierowania dla zarządzanego typu danych delegata.</span><span class="sxs-lookup"><span data-stu-id="e414e-165">The following table shows the marshaling options for the managed delegate data type.</span></span> <span data-ttu-id="e414e-166">Ten <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut zawiera kilka <xref:System.Runtime.InteropServices.UnmanagedType> wartości wyliczenia do organizowania delegatów.</span><span class="sxs-lookup"><span data-stu-id="e414e-166">The <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute provides several <xref:System.Runtime.InteropServices.UnmanagedType> enumeration values to marshal delegates.</span></span>  
  
|<span data-ttu-id="e414e-167">Typ wyliczenia</span><span class="sxs-lookup"><span data-stu-id="e414e-167">Enumeration type</span></span>|<span data-ttu-id="e414e-168">Opis niezarządzanego formatu</span><span class="sxs-lookup"><span data-stu-id="e414e-168">Description of unmanaged format</span></span>|  
|----------------------|-------------------------------------|  
|<span data-ttu-id="e414e-169">**UnmanagedType. elementem FunctionPtr**</span><span class="sxs-lookup"><span data-stu-id="e414e-169">**UnmanagedType.FunctionPtr**</span></span>|<span data-ttu-id="e414e-170">Wskaźnik funkcji niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="e414e-170">An unmanaged function pointer.</span></span>|  
|<span data-ttu-id="e414e-171">**UnmanagedType. Interface**</span><span class="sxs-lookup"><span data-stu-id="e414e-171">**UnmanagedType.Interface**</span></span>|<span data-ttu-id="e414e-172">Interfejs typu **_Delegate**, zgodnie z definicją w pliku mscorlib. tlb.</span><span class="sxs-lookup"><span data-stu-id="e414e-172">An interface of type **_Delegate**, as defined in Mscorlib.tlb.</span></span>|  
  
 <span data-ttu-id="e414e-173">Rozważmy następujący przykładowy kod, w którym metody `DelegateTestInterface` są eksportowane do biblioteki typów com.</span><span class="sxs-lookup"><span data-stu-id="e414e-173">Consider the following example code in which the methods of `DelegateTestInterface` are exported to a COM type library.</span></span> <span data-ttu-id="e414e-174">Należy zauważyć, że tylko delegatów oznaczonych za pomocą słowa kluczowego **ref** (lub **ByRef**) są przesyłane jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="e414e-174">Notice that only delegates marked with the **ref** (or **ByRef**) keyword are passed as In/Out parameters.</span></span>  
  
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
  
### <a name="type-library-representation"></a><span data-ttu-id="e414e-175">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e414e-175">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="e414e-176">Wskaźnik funkcji może zostać wywoływany, tak jak każdy inny niezarządzany wskaźnik funkcji może zostać odwołujący się.</span><span class="sxs-lookup"><span data-stu-id="e414e-176">A function pointer can be dereferenced, just as any other unmanaged function pointer can be dereferenced.</span></span>  

<span data-ttu-id="e414e-177">W tym przykładzie, gdy dwa Delegaty są organizowane jako <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType> , wynik jest `int` i wskaźnikiem do `int` .</span><span class="sxs-lookup"><span data-stu-id="e414e-177">In this example, when the two delegates are marshaled as <xref:System.Runtime.InteropServices.UnmanagedType.FunctionPtr?displayProperty=nameWithType>, the result is an `int` and a pointer to an `int`.</span></span> <span data-ttu-id="e414e-178">Ponieważ typy delegatów są organizowane, `int` w tym miejscu reprezentuje wskaźnik do typu void ( `void*` ), który jest adresem delegata w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e414e-178">Because delegate types are being marshaled, `int` here represents a pointer to a void (`void*`), which is the address of the delegate in memory.</span></span> <span data-ttu-id="e414e-179">Innymi słowy, ten wynik jest specyficzny dla 32-bitowych systemów Windows, ponieważ w `int` tym miejscu reprezentuje rozmiar wskaźnika funkcji.</span><span class="sxs-lookup"><span data-stu-id="e414e-179">In other words, this result is specific to 32-bit Windows systems, since `int` here represents the size of the function pointer.</span></span>

> [!NOTE]
> <span data-ttu-id="e414e-180">Odwołanie do wskaźnika funkcji do zarządzanego delegata przechowywanego przez kod niezarządzany nie zapobiega występowaniu elementów bezużytecznych w zarządzanym obiekcie przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e414e-180">A reference to the function pointer to a managed delegate held by unmanaged code does not prevent the common language runtime from performing garbage collection on the managed object.</span></span>  
  
 <span data-ttu-id="e414e-181">Na przykład następujący kod jest niepoprawny, ponieważ odwołanie do `cb` obiektu, do `SetChangeHandler` metody, nie utrzymuje `cb` aktywności poza cyklem życia `Test` metody.</span><span class="sxs-lookup"><span data-stu-id="e414e-181">For example, the following code is incorrect because the reference to the `cb` object, passed to the `SetChangeHandler` method, does not keep `cb` alive beyond the life of the `Test` method.</span></span> <span data-ttu-id="e414e-182">Gdy `cb` obiekt zostanie odrzucony, wskaźnik funkcji przeszedł do `SetChangeHandler` nie jest już prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="e414e-182">Once the `cb` object is garbage collected, the function pointer passed to `SetChangeHandler` is no longer valid.</span></span>  
  
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
  
 <span data-ttu-id="e414e-183">Aby skompensować nieoczekiwane wyrzucanie elementów bezużytecznych, obiekt wywołujący musi upewnić się, że jest on aktywny, o ile `cb` niezarządzany wskaźnik funkcji jest używany.</span><span class="sxs-lookup"><span data-stu-id="e414e-183">To compensate for unexpected garbage collection, the caller must ensure that the `cb` object is kept alive as long as the unmanaged function pointer is in use.</span></span> <span data-ttu-id="e414e-184">Opcjonalnie kod niezarządzany powiadamia kod zarządzany, gdy wskaźnik funkcji nie jest już wymagany, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e414e-184">Optionally, you can have the unmanaged code notify the managed code when the function pointer is no longer needed, as the following example shows.</span></span>  
  
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
  
## <a name="default-marshaling-for-value-types"></a><span data-ttu-id="e414e-185">Kierowanie domyślne dla typów wartości</span><span class="sxs-lookup"><span data-stu-id="e414e-185">Default marshaling for value types</span></span>  
 <span data-ttu-id="e414e-186">Większość typów wartości, takich jak liczby całkowite i liczby zmiennoprzecinkowe, są [danych kopiowalnych](blittable-and-non-blittable-types.md) i nie wymaga organizowania.</span><span class="sxs-lookup"><span data-stu-id="e414e-186">Most value types, such as integers and floating-point numbers, are [blittable](blittable-and-non-blittable-types.md) and do not require marshaling.</span></span> <span data-ttu-id="e414e-187">Inne typy inne [niż danych kopiowalnych](blittable-and-non-blittable-types.md) mają podobne reprezentacje w pamięci zarządzanej i niezarządzanej oraz wymagają organizowania.</span><span class="sxs-lookup"><span data-stu-id="e414e-187">Other [non-blittable](blittable-and-non-blittable-types.md) types have dissimilar representations in managed and unmanaged memory and do require marshaling.</span></span> <span data-ttu-id="e414e-188">Nadal inne typy wymagają jawnego formatowania w granicach międzyoperacyjnych.</span><span class="sxs-lookup"><span data-stu-id="e414e-188">Still other types require explicit formatting across the interoperation boundary.</span></span>  
  
 <span data-ttu-id="e414e-189">Ta sekcja zawiera informacje o następujących sformatowanych typach wartości:</span><span class="sxs-lookup"><span data-stu-id="e414e-189">This section provides information on the following formatted value types:</span></span>  
  
- [<span data-ttu-id="e414e-190">Typy wartości używane w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="e414e-190">Value Types Used in Platform Invoke</span></span>](#value-types-used-in-platform-invoke)  
  
- [<span data-ttu-id="e414e-191">Typy wartości używane w międzyoperacyjności modelu COM</span><span class="sxs-lookup"><span data-stu-id="e414e-191">Value Types Used in COM Interop</span></span>](#value-types-used-in-com-interop)  
  
 <span data-ttu-id="e414e-192">Oprócz opisywania sformatowanych typów, ten temat identyfikuje [typy wartości systemowych](#system-value-types) , które mają nietypowe zachowanie podczas organizowania.</span><span class="sxs-lookup"><span data-stu-id="e414e-192">In addition to describing formatted types, this topic identifies [System Value Types](#system-value-types) that have unusual marshaling behavior.</span></span>  
  
 <span data-ttu-id="e414e-193">Sformatowany typ to typ złożony, który zawiera informacje, które jawnie kontrolują układ elementów członkowskich w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e414e-193">A formatted type is a complex type that contains information that explicitly controls the layout of its members in memory.</span></span> <span data-ttu-id="e414e-194">Informacje o układzie elementu członkowskiego są udostępniane przy użyciu <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e414e-194">The member layout information is provided using the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="e414e-195">Układ może być jedną z następujących <xref:System.Runtime.InteropServices.LayoutKind> wartości wyliczenia:</span><span class="sxs-lookup"><span data-stu-id="e414e-195">The layout can be one of the following <xref:System.Runtime.InteropServices.LayoutKind> enumeration values:</span></span>  
  
- <span data-ttu-id="e414e-196">**LayoutKind.**</span><span class="sxs-lookup"><span data-stu-id="e414e-196">**LayoutKind.Auto**</span></span>  
  
     <span data-ttu-id="e414e-197">Wskazuje, że środowisko uruchomieniowe języka wspólnego jest bezpłatne, aby zmienić kolejność elementów członkowskich typu w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="e414e-197">Indicates that the common language runtime is free to reorder the members of the type for efficiency.</span></span> <span data-ttu-id="e414e-198">Jednak gdy typ wartości jest przenoszona do kodu niezarządzanego, układ elementów członkowskich jest przewidywalny.</span><span class="sxs-lookup"><span data-stu-id="e414e-198">However, when a value type is passed to unmanaged code, the layout of the members is predictable.</span></span> <span data-ttu-id="e414e-199">Próba zorganizowania takiej struktury automatycznie powoduje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e414e-199">An attempt to marshal such a structure automatically causes an exception.</span></span>  
  
- <span data-ttu-id="e414e-200">**LayoutKind. sekwencyjny**</span><span class="sxs-lookup"><span data-stu-id="e414e-200">**LayoutKind.Sequential**</span></span>  
  
     <span data-ttu-id="e414e-201">Wskazuje, że elementy członkowskie typu muszą zostać ustanowione w pamięci niezarządzanej w takiej samej kolejności, w jakiej występują w definicji typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-201">Indicates that the members of the type are to be laid out in unmanaged memory in the same order in which they appear in the managed type definition.</span></span>  
  
- <span data-ttu-id="e414e-202">**LayoutKind. Explicit**</span><span class="sxs-lookup"><span data-stu-id="e414e-202">**LayoutKind.Explicit**</span></span>  
  
     <span data-ttu-id="e414e-203">Wskazuje, że elementy członkowskie są określane zgodnie z <xref:System.Runtime.InteropServices.FieldOffsetAttribute> podanymi dla każdego pola.</span><span class="sxs-lookup"><span data-stu-id="e414e-203">Indicates that the members are laid out according to the <xref:System.Runtime.InteropServices.FieldOffsetAttribute> supplied with each field.</span></span>  
  
### <a name="value-types-used-in-platform-invoke"></a><span data-ttu-id="e414e-204">Typy wartości używane w wywołaniu platformy</span><span class="sxs-lookup"><span data-stu-id="e414e-204">Value Types Used in Platform Invoke</span></span>  
 <span data-ttu-id="e414e-205">W poniższym przykładzie `Point` `Rect` typy i zapewniają informacje o układzie elementu członkowskiego przy użyciu **StructLayoutAttribute**.</span><span class="sxs-lookup"><span data-stu-id="e414e-205">In the following example the `Point` and `Rect` types provide member layout information using the **StructLayoutAttribute**.</span></span>  
  
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
  
 <span data-ttu-id="e414e-206">W przypadku kierowania do niezarządzanego kodu te sformatowane typy są organizowane jako struktury w stylu C.</span><span class="sxs-lookup"><span data-stu-id="e414e-206">When marshaled to unmanaged code, these formatted types are marshaled as C-style structures.</span></span> <span data-ttu-id="e414e-207">Zapewnia to prosty sposób wywoływania niezarządzanego interfejsu API, który ma argumenty struktury.</span><span class="sxs-lookup"><span data-stu-id="e414e-207">This provides an easy way of calling an unmanaged API that has structure arguments.</span></span> <span data-ttu-id="e414e-208">Na przykład `POINT` `RECT` struktury i mogą być przesyłane do funkcji **PtInRect** interfejsu API systemu Microsoft Windows w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e414e-208">For example, the `POINT` and `RECT` structures can be passed to the Microsoft Windows API **PtInRect** function as follows:</span></span>  
  
```cpp  
BOOL PtInRect(const RECT *lprc, POINT pt);  
```  
  
 <span data-ttu-id="e414e-209">Można przekazać struktury przy użyciu następującej definicji wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="e414e-209">You can pass structures using the following platform invoke definition:</span></span>  
  
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
  
 <span data-ttu-id="e414e-210">`Rect`Typ wartości musi być przesyłany przez odwołanie, ponieważ niezarządzany interfejs API oczekuje na `RECT` przekazanie wskaźnika do funkcji.</span><span class="sxs-lookup"><span data-stu-id="e414e-210">The `Rect` value type must be passed by reference because the unmanaged API is expecting a pointer to a `RECT` to be passed to the function.</span></span> <span data-ttu-id="e414e-211">`Point`Typ wartości jest przenoszona przez wartość, ponieważ niezarządzany interfejs API oczekuje na `POINT` przekazanie na stosie.</span><span class="sxs-lookup"><span data-stu-id="e414e-211">The `Point` value type is passed by value because the unmanaged API expects the `POINT` to be passed on the stack.</span></span> <span data-ttu-id="e414e-212">Ta delikatna różnica jest bardzo ważna.</span><span class="sxs-lookup"><span data-stu-id="e414e-212">This subtle difference is very important.</span></span> <span data-ttu-id="e414e-213">Odwołania są przesyłane do niezarządzanego kodu jako wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="e414e-213">References are passed to unmanaged code as pointers.</span></span> <span data-ttu-id="e414e-214">Wartości są przesyłane do kodu niezarządzanego na stosie.</span><span class="sxs-lookup"><span data-stu-id="e414e-214">Values are passed to unmanaged code on the stack.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e414e-215">Gdy sformatowany typ jest zorganizowany jako struktura, dostępne są tylko pola należące do tego typu.</span><span class="sxs-lookup"><span data-stu-id="e414e-215">When a formatted type is marshaled as a structure, only the fields within the type are accessible.</span></span> <span data-ttu-id="e414e-216">Jeśli typ ma metody, właściwości lub zdarzenia, są one niedostępne z kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-216">If the type has methods, properties, or events, they are inaccessible from unmanaged code.</span></span>  
  
 <span data-ttu-id="e414e-217">Klasy mogą być również organizowane w kodzie niezarządzanym jako struktury w stylu C, pod warunkiem, że mają stały układ elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e414e-217">Classes can also be marshaled to unmanaged code as C-style structures, provided they have fixed member layout.</span></span> <span data-ttu-id="e414e-218">Informacje o układzie elementu członkowskiego klasy są również udostępniane z <xref:System.Runtime.InteropServices.StructLayoutAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="e414e-218">The member layout information for a class is also provided with the <xref:System.Runtime.InteropServices.StructLayoutAttribute> attribute.</span></span> <span data-ttu-id="e414e-219">Główna różnica między typami wartości ze stałym układem i klasami ze stałym układem jest sposobem, w jaki są one organizowane do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="e414e-219">The main difference between value types with fixed layout and classes with fixed layout is the way in which they are marshaled to unmanaged code.</span></span> <span data-ttu-id="e414e-220">Typy wartości są przekazywane przez wartość (na stosie) i w związku z tym wszystkie zmiany wprowadzone do elementów członkowskich typu przez wywoływany nie są widoczne dla obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="e414e-220">Value types are passed by value (on the stack) and consequently any changes made to the members of the type by the callee are not seen by the caller.</span></span> <span data-ttu-id="e414e-221">Typy odwołań są przesyłane przez odwołanie (odwołanie do typu jest przesyłane na stosie); w związku z tym, wszystkie zmiany wprowadzone do elementów członkowskich typu danych kopiowalnych typu przez wywoływany przez obiekt wywołujący są widoczne dla obiektu dzwoniącego.</span><span class="sxs-lookup"><span data-stu-id="e414e-221">Reference types are passed by reference (a reference to the type is passed on the stack); consequently, all changes made to blittable-type members of a type by the callee are seen by the caller.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e414e-222">Jeśli typ referencyjny składa się z typów innych niż danych kopiowalnych, konwersja jest wymagana dwukrotnie: pierwszy raz, gdy argument jest przenoszona do niezarządzanej strony, a drugi czas powrotu z wywołania.</span><span class="sxs-lookup"><span data-stu-id="e414e-222">If a reference type has members of non-blittable types, conversion is required twice: the first time when an argument is passed to the unmanaged side and the second time on return from the call.</span></span> <span data-ttu-id="e414e-223">W związku z tym dodatkowymi kosztami parametry wejściowe/out muszą być jawnie stosowane do argumentu, jeśli obiekt wywołujący chce zobaczyć zmiany wprowadzone przez wywoływany element.</span><span class="sxs-lookup"><span data-stu-id="e414e-223">Due to this added overhead, In/Out parameters must be explicitly applied to an argument if the caller wants to see changes made by the callee.</span></span>  
  
 <span data-ttu-id="e414e-224">W poniższym przykładzie `SystemTime` Klasa ma sekwencyjny układ elementów członkowskich i może być przenoszona do funkcji **GetSystemTime** interfejsu API systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e414e-224">In the following example, the `SystemTime` class has sequential member layout and can be passed to the Windows API **GetSystemTime** function.</span></span>  
  
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
  
 <span data-ttu-id="e414e-225">Funkcja **GetSystemTime** jest zdefiniowana w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e414e-225">The **GetSystemTime** function is defined as follows:</span></span>  
  
```cpp  
void GetSystemTime(SYSTEMTIME* SystemTime);  
```  
  
 <span data-ttu-id="e414e-226">Odpowiednik definicji wywołania platformy dla **GetSystemTime** jest następujący:</span><span class="sxs-lookup"><span data-stu-id="e414e-226">The equivalent platform invoke definition for **GetSystemTime** is as follows:</span></span>  
  
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
  
 <span data-ttu-id="e414e-227">Zwróć uwagę, że `SystemTime` argument nie jest wpisywany jako argument odwołania `SystemTime` , ponieważ jest klasą, a nie typem wartości.</span><span class="sxs-lookup"><span data-stu-id="e414e-227">Notice that the `SystemTime` argument is not typed as a reference argument because `SystemTime` is a class, not a value type.</span></span> <span data-ttu-id="e414e-228">W przeciwieństwie do typów wartości, klasy są zawsze przesyłane przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e414e-228">Unlike value types, classes are always passed by reference.</span></span>  
  
 <span data-ttu-id="e414e-229">Poniższy przykład kodu przedstawia inną `Point` klasę, która ma metodę o nazwie `SetXY` .</span><span class="sxs-lookup"><span data-stu-id="e414e-229">The following code example shows a different `Point` class that has a method called `SetXY`.</span></span> <span data-ttu-id="e414e-230">Ponieważ typ ma sekwencyjny układ, może być przekazywany do kodu niezarządzanego i zorganizowany jako struktura.</span><span class="sxs-lookup"><span data-stu-id="e414e-230">Because the type has sequential layout, it can be passed to unmanaged code and marshaled as a structure.</span></span> <span data-ttu-id="e414e-231">Jednak `SetXY` element członkowski nie jest wywoływany z kodu niezarządzanego, nawet jeśli obiekt jest przesyłany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="e414e-231">However, the `SetXY` member is not callable from unmanaged code, even though the object is passed by reference.</span></span>  
  
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
  
### <a name="value-types-used-in-com-interop"></a><span data-ttu-id="e414e-232">Typy wartości używane w międzyoperacyjności modelu COM</span><span class="sxs-lookup"><span data-stu-id="e414e-232">Value Types Used in COM Interop</span></span>  
 <span data-ttu-id="e414e-233">Sformatowane typy mogą być również przesyłane do wywołań metod międzyoperacyjnych modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e414e-233">Formatted types can also be passed to COM interop method calls.</span></span> <span data-ttu-id="e414e-234">W rzeczywistości, gdy eksportowane do biblioteki typów, typy wartości są automatycznie konwertowane na struktury.</span><span class="sxs-lookup"><span data-stu-id="e414e-234">In fact, when exported to a type library, value types are automatically converted to structures.</span></span> <span data-ttu-id="e414e-235">Jak pokazano na poniższym przykładzie, `Point` Typ wartości jest definicją typu (TypeDef) o nazwie `Point` .</span><span class="sxs-lookup"><span data-stu-id="e414e-235">As the following example shows, the `Point` value type becomes a type definition (typedef) with the name `Point`.</span></span> <span data-ttu-id="e414e-236">Wszystkie odwołania do `Point` typu wartości w innym miejscu w bibliotece typów są zastępowane `Point` typedef.</span><span class="sxs-lookup"><span data-stu-id="e414e-236">All references to the `Point` value type elsewhere in the type library are replaced with the `Point` typedef.</span></span>  
  
 <span data-ttu-id="e414e-237">**Reprezentacja biblioteki typów**</span><span class="sxs-lookup"><span data-stu-id="e414e-237">**Type library representation**</span></span>  
  
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
  
 <span data-ttu-id="e414e-238">Te same reguły służące do organizowania wartości i odwołań do wywołań wywołania platformy są używane podczas organizowania interfejsów COM.</span><span class="sxs-lookup"><span data-stu-id="e414e-238">The same rules used to marshal values and references to platform invoke calls are used when marshaling through COM interfaces.</span></span> <span data-ttu-id="e414e-239">Na przykład, gdy wystąpienie `Point` typu wartości jest przesyłane z .NET Framework do modelu COM, `Point` wartość jest przenoszona przez wartości.</span><span class="sxs-lookup"><span data-stu-id="e414e-239">For example, when an instance of the `Point` value type is passed from the .NET Framework to COM, the `Point` is passed by value.</span></span> <span data-ttu-id="e414e-240">Jeśli `Point` Typ wartości jest przesyłany przez odwołanie, wskaźnik do elementu `Point` jest przesyłany na stosie.</span><span class="sxs-lookup"><span data-stu-id="e414e-240">If the `Point` value type is passed by reference, a pointer to a `Point` is passed on the stack.</span></span> <span data-ttu-id="e414e-241">Organizator międzyoperacyjny nie obsługuje wyższych poziomów pośrednich (**punkt** \* \* ) w dowolnym kierunku.</span><span class="sxs-lookup"><span data-stu-id="e414e-241">The interop marshaler does not support higher levels of indirection (**Point** \*\*) in either direction.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e414e-242">Struktury z <xref:System.Runtime.InteropServices.LayoutKind> wartością wyliczenia ustawioną na wartość **Explicit** nie mogą być używane w międzyoperacyjności modelu COM, ponieważ eksportowana biblioteka typów nie może wyrazić jawnego układu.</span><span class="sxs-lookup"><span data-stu-id="e414e-242">Structures having the <xref:System.Runtime.InteropServices.LayoutKind> enumeration value set to **Explicit** cannot be used in COM interop because the exported type library cannot express an explicit layout.</span></span>  
  
### <a name="system-value-types"></a><span data-ttu-id="e414e-243">Typy wartości systemu</span><span class="sxs-lookup"><span data-stu-id="e414e-243">System Value Types</span></span>  
 <span data-ttu-id="e414e-244"><xref:System>Przestrzeń nazw ma kilka typów wartości, które reprezentują postać opakowaną typów pierwotnych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="e414e-244">The <xref:System> namespace has several value types that represent the boxed form of the runtime primitive types.</span></span> <span data-ttu-id="e414e-245">Na przykład struktura typu wartości <xref:System.Int32?displayProperty=nameWithType> reprezentuje opakowaną postać **ELEMENT_TYPE_I4**.</span><span class="sxs-lookup"><span data-stu-id="e414e-245">For example, the value type <xref:System.Int32?displayProperty=nameWithType> structure represents the boxed form of **ELEMENT_TYPE_I4**.</span></span> <span data-ttu-id="e414e-246">Zamiast organizować te typy jako struktury, tak jak inne sformatowane typy, są organizowane w taki sam sposób, jak w przypadku typów pierwotnych.</span><span class="sxs-lookup"><span data-stu-id="e414e-246">Instead of marshaling these types as structures, as other formatted types are, you marshal them in the same way as the primitive types they box.</span></span> <span data-ttu-id="e414e-247">W związku z tym obiekt **System. Int32** jest zorganizowany jako **ELEMENT_TYPE_I4** zamiast struktury zawierającej pojedynczy element członkowski typu **Long**.</span><span class="sxs-lookup"><span data-stu-id="e414e-247">**System.Int32** is therefore marshaled as **ELEMENT_TYPE_I4** instead of as a structure containing a single member of type **long**.</span></span> <span data-ttu-id="e414e-248">Poniższa tabela zawiera listę typów wartości w przestrzeni nazw **systemu** , które są opakowane na typy pierwotne.</span><span class="sxs-lookup"><span data-stu-id="e414e-248">The following table contains a list of the value types in the **System** namespace that are boxed representations of primitive types.</span></span>  
  
|<span data-ttu-id="e414e-249">Typ wartości systemowej</span><span class="sxs-lookup"><span data-stu-id="e414e-249">System value type</span></span>|<span data-ttu-id="e414e-250">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="e414e-250">Element type</span></span>|  
|-----------------------|------------------|  
|<xref:System.Boolean?displayProperty=nameWithType>|<span data-ttu-id="e414e-251">**ELEMENT_TYPE_BOOLEAN**</span><span class="sxs-lookup"><span data-stu-id="e414e-251">**ELEMENT_TYPE_BOOLEAN**</span></span>|  
|<xref:System.SByte?displayProperty=nameWithType>|<span data-ttu-id="e414e-252">**ELEMENT_TYPE_I1**</span><span class="sxs-lookup"><span data-stu-id="e414e-252">**ELEMENT_TYPE_I1**</span></span>|  
|<xref:System.Byte?displayProperty=nameWithType>|<span data-ttu-id="e414e-253">**ELEMENT_TYPE_UI1**</span><span class="sxs-lookup"><span data-stu-id="e414e-253">**ELEMENT_TYPE_UI1**</span></span>|  
|<xref:System.Char?displayProperty=nameWithType>|<span data-ttu-id="e414e-254">**ELEMENT_TYPE_CHAR**</span><span class="sxs-lookup"><span data-stu-id="e414e-254">**ELEMENT_TYPE_CHAR**</span></span>|  
|<xref:System.Int16?displayProperty=nameWithType>|<span data-ttu-id="e414e-255">**ELEMENT_TYPE_I2**</span><span class="sxs-lookup"><span data-stu-id="e414e-255">**ELEMENT_TYPE_I2**</span></span>|  
|<xref:System.UInt16?displayProperty=nameWithType>|<span data-ttu-id="e414e-256">**ELEMENT_TYPE_U2**</span><span class="sxs-lookup"><span data-stu-id="e414e-256">**ELEMENT_TYPE_U2**</span></span>|  
|<xref:System.Int32?displayProperty=nameWithType>|<span data-ttu-id="e414e-257">**ELEMENT_TYPE_I4**</span><span class="sxs-lookup"><span data-stu-id="e414e-257">**ELEMENT_TYPE_I4**</span></span>|  
|<xref:System.UInt32?displayProperty=nameWithType>|<span data-ttu-id="e414e-258">**ELEMENT_TYPE_U4**</span><span class="sxs-lookup"><span data-stu-id="e414e-258">**ELEMENT_TYPE_U4**</span></span>|  
|<xref:System.Int64?displayProperty=nameWithType>|<span data-ttu-id="e414e-259">**ELEMENT_TYPE_I8**</span><span class="sxs-lookup"><span data-stu-id="e414e-259">**ELEMENT_TYPE_I8**</span></span>|  
|<xref:System.UInt64?displayProperty=nameWithType>|<span data-ttu-id="e414e-260">**ELEMENT_TYPE_U8**</span><span class="sxs-lookup"><span data-stu-id="e414e-260">**ELEMENT_TYPE_U8**</span></span>|  
|<xref:System.Single?displayProperty=nameWithType>|<span data-ttu-id="e414e-261">**ELEMENT_TYPE_R4**</span><span class="sxs-lookup"><span data-stu-id="e414e-261">**ELEMENT_TYPE_R4**</span></span>|  
|<xref:System.Double?displayProperty=nameWithType>|<span data-ttu-id="e414e-262">**ELEMENT_TYPE_R8**</span><span class="sxs-lookup"><span data-stu-id="e414e-262">**ELEMENT_TYPE_R8**</span></span>|  
|<xref:System.String?displayProperty=nameWithType>|<span data-ttu-id="e414e-263">**ELEMENT_TYPE_STRING**</span><span class="sxs-lookup"><span data-stu-id="e414e-263">**ELEMENT_TYPE_STRING**</span></span>|  
|<xref:System.IntPtr?displayProperty=nameWithType>|<span data-ttu-id="e414e-264">**ELEMENT_TYPE_I**</span><span class="sxs-lookup"><span data-stu-id="e414e-264">**ELEMENT_TYPE_I**</span></span>|  
|<xref:System.UIntPtr?displayProperty=nameWithType>|<span data-ttu-id="e414e-265">**ELEMENT_TYPE_U**</span><span class="sxs-lookup"><span data-stu-id="e414e-265">**ELEMENT_TYPE_U**</span></span>|  
  
 <span data-ttu-id="e414e-266">Niektóre inne typy wartości w przestrzeni nazw **system** są obsługiwane inaczej.</span><span class="sxs-lookup"><span data-stu-id="e414e-266">Some other value types in the **System** namespace are handled differently.</span></span> <span data-ttu-id="e414e-267">Ponieważ kod niezarządzany ma już dobrze ustalone formaty dla tych typów, Organizator ma specjalne reguły do organizowania.</span><span class="sxs-lookup"><span data-stu-id="e414e-267">Because the unmanaged code already has well-established formats for these types, the marshaler has special rules for marshaling them.</span></span> <span data-ttu-id="e414e-268">W poniższej tabeli wymieniono specjalne typy wartości w przestrzeni nazw **systemu** , a także niezarządzany typ, do którego są organizowane.</span><span class="sxs-lookup"><span data-stu-id="e414e-268">The following table lists the special value types in the **System** namespace, as well as the unmanaged type they are marshaled to.</span></span>  
  
|<span data-ttu-id="e414e-269">Typ wartości systemowej</span><span class="sxs-lookup"><span data-stu-id="e414e-269">System value type</span></span>|<span data-ttu-id="e414e-270">Typ IDL</span><span class="sxs-lookup"><span data-stu-id="e414e-270">IDL type</span></span>|  
|-----------------------|--------------|  
|<xref:System.DateTime?displayProperty=nameWithType>|<span data-ttu-id="e414e-271">**DNIU**</span><span class="sxs-lookup"><span data-stu-id="e414e-271">**DATE**</span></span>|  
|<xref:System.Decimal?displayProperty=nameWithType>|<span data-ttu-id="e414e-272">**DOKŁADNOŚCI**</span><span class="sxs-lookup"><span data-stu-id="e414e-272">**DECIMAL**</span></span>|  
|<xref:System.Guid?displayProperty=nameWithType>|<span data-ttu-id="e414e-273">**IDENT**</span><span class="sxs-lookup"><span data-stu-id="e414e-273">**GUID**</span></span>|  
|<xref:System.Drawing.Color?displayProperty=nameWithType>|<span data-ttu-id="e414e-274">**OLE_COLOR**</span><span class="sxs-lookup"><span data-stu-id="e414e-274">**OLE_COLOR**</span></span>|  
  
 <span data-ttu-id="e414e-275">Poniższy kod przedstawia definicję niezarządzanych typów **Date**, **GUID**, **Decimal**i **OLE_COLOR** w bibliotece typów Stdole2.</span><span class="sxs-lookup"><span data-stu-id="e414e-275">The following code shows the definition of the unmanaged types **DATE**, **GUID**, **DECIMAL**, and **OLE_COLOR** in the Stdole2 type library.</span></span>  
  
#### <a name="type-library-representation"></a><span data-ttu-id="e414e-276">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e414e-276">Type library representation</span></span>  
  
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
  
 <span data-ttu-id="e414e-277">Poniższy kod przedstawia odpowiednie definicje w zarządzanym `IValueTypes` interfejsie.</span><span class="sxs-lookup"><span data-stu-id="e414e-277">The following code shows the corresponding definitions in the managed `IValueTypes` interface.</span></span>  
  
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
  
#### <a name="type-library-representation"></a><span data-ttu-id="e414e-278">Reprezentacja biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e414e-278">Type library representation</span></span>  
  
```cpp  
[…]  
interface IValueTypes : IDispatch {  
   HRESULT M1([in] DATE d);  
   HRESULT M2([in] GUID d);  
   HRESULT M3([in] DECIMAL d);  
   HRESULT M4([in] OLE_COLOR d);  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="e414e-279">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e414e-279">See also</span></span>

- [<span data-ttu-id="e414e-280">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="e414e-280">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- [<span data-ttu-id="e414e-281">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="e414e-281">Copying and Pinning</span></span>](copying-and-pinning.md)
- [<span data-ttu-id="e414e-282">Organizowanie domyślne dotyczące tablic</span><span class="sxs-lookup"><span data-stu-id="e414e-282">Default Marshaling for Arrays</span></span>](default-marshaling-for-arrays.md)
- [<span data-ttu-id="e414e-283">Domyślny marshaling dla obiektów</span><span class="sxs-lookup"><span data-stu-id="e414e-283">Default Marshaling for Objects</span></span>](default-marshaling-for-objects.md)
- [<span data-ttu-id="e414e-284">Organizowanie domyślne dotyczące ciągów</span><span class="sxs-lookup"><span data-stu-id="e414e-284">Default Marshaling for Strings</span></span>](default-marshaling-for-strings.md)
