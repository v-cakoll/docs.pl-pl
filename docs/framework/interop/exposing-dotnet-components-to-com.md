---
title: "Udostępnianie składników .NET Framework modelowi COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61e1dbdcf919ee6aa2150e6a57cb88a8aa859efe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="9c5f0-102">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="9c5f0-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="9c5f0-103">Typ architektury .NET do zapisu i korzystanie z tego typu z kodem niezarządzanym są różne działania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="9c5f0-104">W tej sekcji opisano kilka porady dotyczące pisania zarządzanego kodu, który współdziała z klientami COM:</span><span class="sxs-lookup"><span data-stu-id="9c5f0-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
-   <span data-ttu-id="9c5f0-105">[Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="9c5f0-106">Wszystkie zarządzane typy, metody, właściwości, pól i zdarzenia, które ma zostać udostępniona modelowi COM muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="9c5f0-107">Typy musi mieć domyślnego konstruktora publicznego, który jest jedynym Konstruktor, który można wywołać za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
-   <span data-ttu-id="9c5f0-108">[Stosowanie atrybutów międzyoperacyjności](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="9c5f0-109">Atrybuty niestandardowe w kod zarządzany może zwiększyć współdziałanie składnika.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
-   <span data-ttu-id="9c5f0-110">[Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="9c5f0-111">Deweloperzy COM może wymagać zawierają podsumowanie etapy odwołujące się do i wdrażanie z zestawów.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="9c5f0-112">Ponadto w tej sekcji wymieniono zadania związane z korzystanie z klient modelu COM typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="9c5f0-113">Aby korzystać z modelu COM typu zarządzanego</span><span class="sxs-lookup"><span data-stu-id="9c5f0-113">To consume a managed type from COM</span></span>  
  
1.  <span data-ttu-id="9c5f0-114">[Rejestrowanie zestawów w modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="9c5f0-115">Typy w zestawie (i biblioteki typów) musi być zarejestrowana w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="9c5f0-116">Jeśli Instalator nie rejestruje zestaw, poinstruuj COM deweloperom używanie Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2.  <span data-ttu-id="9c5f0-117">[Odwoływać się do typów .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="9c5f0-118">Deweloperzy COM może odwoływać się do typów w zestawie przy użyciu tego samego narzędzi i technik, których używają obecnie.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3.  <span data-ttu-id="9c5f0-119">[Wywołanie obiektu .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-119">[Call a .NET object](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33).</span></span>  
  
     <span data-ttu-id="9c5f0-120">Deweloperzy COM można wywoływać metod w obiektu .NET. ten sam sposób ich wywoływać metod w dowolnego typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="9c5f0-121">Na przykład COM **wywołanie funkcji CoCreateInstance** interfejsu API aktywuje obiekty .NET.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4.  <span data-ttu-id="9c5f0-122">[Wdrażanie aplikacji modelu COM dostępu](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span><span class="sxs-lookup"><span data-stu-id="9c5f0-122">[Deploy an application for COM access](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce).</span></span>  
  
     <span data-ttu-id="9c5f0-123">Zestawu z silną nazwą można zainstalować w pamięci podręcznej GAC i wymaga podpisu od jego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="9c5f0-124">Zestawy, które nie są silne nazwy musi być zainstalowany w katalogu aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="9c5f0-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c5f0-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9c5f0-125">See Also</span></span>  
 [<span data-ttu-id="9c5f0-126">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="9c5f0-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)  
 [<span data-ttu-id="9c5f0-127">Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET</span><span class="sxs-lookup"><span data-stu-id="9c5f0-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
