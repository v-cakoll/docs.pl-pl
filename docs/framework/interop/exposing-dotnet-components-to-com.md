---
title: Udostępnianie składników .NET Framework modelowi COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a6c2b755b87f6f01f08f54a2f2fc567868dbb55
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626350"
---
# <a name="exposing-net-framework-components-to-com"></a><span data-ttu-id="4b04b-102">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="4b04b-102">Exposing .NET Framework Components to COM</span></span>
<span data-ttu-id="4b04b-103">Typ architektury .NET do zapisywania i używania tego typu z niezarządzanego kodu są różne działania, dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="4b04b-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="4b04b-104">W tej sekcji opisano kilka porad dotyczących pisaniu kodu zarządzanego, który współdziała z klientami COM:</span><span class="sxs-lookup"><span data-stu-id="4b04b-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>  
  
- <span data-ttu-id="4b04b-105">[Kwalifikowanie typów .NET do międzyoperacyjności](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="4b04b-105">[Qualifying .NET types for interoperation](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).</span></span>  
  
     <span data-ttu-id="4b04b-106">Wszystkie zarządzane typy, metody, właściwości, pola i zdarzenia, które chcesz udostępnić w COM muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="4b04b-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="4b04b-107">Typy muszą mieć publicznego konstruktora domyślnego, który jest tylko konstruktorem, który może być wywoływany za pomocą modelu COM.</span><span class="sxs-lookup"><span data-stu-id="4b04b-107">Types must have a public default constructor, which is the only constructor that can be invoked through COM.</span></span>  
  
- <span data-ttu-id="4b04b-108">[Stosowanie atrybutów międzyoperacyjności](../../../docs/framework/interop/applying-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="4b04b-108">[Applying interop attributes](../../../docs/framework/interop/applying-interop-attributes.md).</span></span>  
  
     <span data-ttu-id="4b04b-109">Niestandardowe atrybuty w kodzie zarządzanym może zwiększyć współdziałanie składnika.</span><span class="sxs-lookup"><span data-stu-id="4b04b-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>  
  
- <span data-ttu-id="4b04b-110">[Pakowanie zestawu dla modelu COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="4b04b-110">[Packaging an assembly for COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).</span></span>  
  
     <span data-ttu-id="4b04b-111">Deweloperzy COM może wymagać podsumowania etapy odwołujące się do i wdrażaniu zestawów.</span><span class="sxs-lookup"><span data-stu-id="4b04b-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>  
  
 <span data-ttu-id="4b04b-112">Ponadto w tej sekcji wymieniono zadania związane z wykorzystywanie typu zarządzanego z klientem COM.</span><span class="sxs-lookup"><span data-stu-id="4b04b-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>  
  
#### <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="4b04b-113">Korzystanie z typu zarządzanego z modelu COM</span><span class="sxs-lookup"><span data-stu-id="4b04b-113">To consume a managed type from COM</span></span>  
  
1. <span data-ttu-id="4b04b-114">[Rejestrowanie zestawów z modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="4b04b-114">[Register assemblies with COM](../../../docs/framework/interop/registering-assemblies-with-com.md).</span></span>  
  
     <span data-ttu-id="4b04b-115">Typy w zestawie (i biblioteki typów) musi być zarejestrowana w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="4b04b-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="4b04b-116">Jeśli Instalator nie rejestruje zestaw, poinstruuj deweloperom COM, należy użyć Regasm.exe.</span><span class="sxs-lookup"><span data-stu-id="4b04b-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>  
  
2. <span data-ttu-id="4b04b-117">[Odwoływać się do typów .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="4b04b-117">[Reference .NET types from COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).</span></span>  
  
     <span data-ttu-id="4b04b-118">Deweloperzy COM może odwoływać się typy w zestawie przy użyciu tych samych narzędzi i technik, które używają już dziś.</span><span class="sxs-lookup"><span data-stu-id="4b04b-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>  
  
3. <span data-ttu-id="4b04b-119">[Wywołanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b04b-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>  
  
     <span data-ttu-id="4b04b-120">Deweloperzy COM może wywoływać metody dla obiektu .NET taki sam sposób mogą wywoływać metody dla dowolnego typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="4b04b-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="4b04b-121">Na przykład COM **CoCreateInstance** API aktywuje obiektów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="4b04b-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>  
  
4. <span data-ttu-id="4b04b-122">[Wdrażanie aplikacji do dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="4b04b-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>  
  
     <span data-ttu-id="4b04b-123">Zestawu z silną nazwą, można zainstalować w globalnej pamięci podręcznej i wymaga podpisu od jego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="4b04b-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="4b04b-124">Zestawy, które nie są silną nazwę muszą być zainstalowane w katalogu aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="4b04b-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b04b-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4b04b-125">See also</span></span>

- [<span data-ttu-id="4b04b-126">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="4b04b-126">Interoperating with Unmanaged Code</span></span>](../../../docs/framework/interop/index.md)
- [<span data-ttu-id="4b04b-127">Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET</span><span class="sxs-lookup"><span data-stu-id="4b04b-127">COM Interop Sample: COM Client and .NET Server</span></span>](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
