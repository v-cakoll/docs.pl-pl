---
title: Udostępnianie składników .NET do modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
ms.openlocfilehash: 09045fb455a2163641d6f4af0ba07520ead59f1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123487"
---
# <a name="exposing-net-components-to-com"></a><span data-ttu-id="79bc7-102">Udostępnianie składników .NET do modelu COM</span><span class="sxs-lookup"><span data-stu-id="79bc7-102">Exposing .NET components to COM</span></span>

<span data-ttu-id="79bc7-103">Pisanie typu .NET i używanie tego typu z kodu niezarządzanego to odrębne działania dla deweloperów.</span><span class="sxs-lookup"><span data-stu-id="79bc7-103">Writing a .NET type and consuming that type from unmanaged code are distinct activities for developers.</span></span> <span data-ttu-id="79bc7-104">W tej sekcji opisano kilka wskazówek dotyczących pisania kodu zarządzanego, który współdziała z klientami COM:</span><span class="sxs-lookup"><span data-stu-id="79bc7-104">This section describes several tips for writing managed code that interoperates with COM clients:</span></span>

- <span data-ttu-id="79bc7-105">[Kwalifikowanie typów .NET do międzyoperacyjności](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="79bc7-105">[Qualifying .NET types for interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

     <span data-ttu-id="79bc7-106">Wszystkie typy zarządzane, metody, właściwości, pola i zdarzenia, które mają zostać ujawnione w modelu COM, muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="79bc7-106">All managed types, methods, properties, fields, and events that you want to expose to COM must be public.</span></span> <span data-ttu-id="79bc7-107">Typy muszą mieć publiczny Konstruktor bez parametrów, który jest jedynym konstruktorem, który może być wywoływany przez COM.</span><span class="sxs-lookup"><span data-stu-id="79bc7-107">Types must have a public parameterless constructor, which is the only constructor that can be invoked through COM.</span></span>

- <span data-ttu-id="79bc7-108">[Stosowanie atrybutów międzyoperacyjnych](../../standard/native-interop/apply-interop-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="79bc7-108">[Applying interop attributes](../../standard/native-interop/apply-interop-attributes.md).</span></span>

     <span data-ttu-id="79bc7-109">Atrybuty niestandardowe w kodzie zarządzanym mogą wzmocnić współdziałanie składnika.</span><span class="sxs-lookup"><span data-stu-id="79bc7-109">Custom attributes within managed code can enhance the interoperability of a component.</span></span>

- <span data-ttu-id="79bc7-110">[Pakowanie zestawu dla modelu COM](packaging-an-assembly-for-com.md).</span><span class="sxs-lookup"><span data-stu-id="79bc7-110">[Packaging an assembly for COM](packaging-an-assembly-for-com.md).</span></span>

     <span data-ttu-id="79bc7-111">Deweloperzy COM mogą wymagać podsumowania kroków związanych z odwołującymi się i wdrażaniem zestawów.</span><span class="sxs-lookup"><span data-stu-id="79bc7-111">COM developers might require that you summarize the steps involved in referencing and deploying your assemblies.</span></span>

 <span data-ttu-id="79bc7-112">Ponadto w tej sekcji przedstawiono zadania związane z zużywaniem typu zarządzanego z klienta COM.</span><span class="sxs-lookup"><span data-stu-id="79bc7-112">Additionally, this section identifies the tasks related to consuming a managed type from a COM client.</span></span>

## <a name="to-consume-a-managed-type-from-com"></a><span data-ttu-id="79bc7-113">Aby użyć typu zarządzanego z modelu COM</span><span class="sxs-lookup"><span data-stu-id="79bc7-113">To consume a managed type from COM</span></span>

1. <span data-ttu-id="79bc7-114">[Zarejestruj zestawy przy użyciu modelu COM](registering-assemblies-with-com.md).</span><span class="sxs-lookup"><span data-stu-id="79bc7-114">[Register assemblies with COM](registering-assemblies-with-com.md).</span></span>

     <span data-ttu-id="79bc7-115">Typy w zestawie (i biblioteki typów) muszą być zarejestrowane w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="79bc7-115">Types in an assembly (and type libraries) must be registered at design time.</span></span> <span data-ttu-id="79bc7-116">Jeśli Instalator nie rejestruje zestawu, poinstruuj deweloperów COM, aby korzystali z Regasm. exe.</span><span class="sxs-lookup"><span data-stu-id="79bc7-116">If an installer does not register the assembly, instruct COM developers to use Regasm.exe.</span></span>

2. <span data-ttu-id="79bc7-117">[Odwołuj się do typów .NET z modelu COM](how-to-reference-net-types-from-com.md).</span><span class="sxs-lookup"><span data-stu-id="79bc7-117">[Reference .NET types from COM](how-to-reference-net-types-from-com.md).</span></span>

     <span data-ttu-id="79bc7-118">Deweloperzy COM mogą odwoływać się do typów w zestawie przy użyciu tych samych narzędzi i technik, których używają dzisiaj.</span><span class="sxs-lookup"><span data-stu-id="79bc7-118">COM developers can reference types in an assembly using the same tools and techniques they use today.</span></span>

3. <span data-ttu-id="79bc7-119">[Wywoływanie obiektu .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="79bc7-119">[Call a .NET object](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100)).</span></span>

     <span data-ttu-id="79bc7-120">Deweloperzy COM mogą wywoływanie metod w obiekcie .NET w taki sam sposób, jak wywoływanie metod dla dowolnego typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="79bc7-120">COM developers can call methods on the .NET object the same way they call methods on any unmanaged type.</span></span> <span data-ttu-id="79bc7-121">Na przykład interfejs API funkcji **COCREATEINSTANCE** com aktywuje obiekty .NET.</span><span class="sxs-lookup"><span data-stu-id="79bc7-121">For example, the COM **CoCreateInstance** API activates .NET objects.</span></span>

4. <span data-ttu-id="79bc7-122">[Wdróż aplikację na potrzeby dostępu do modelu COM](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="79bc7-122">[Deploy an application for COM access](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100)).</span></span>

     <span data-ttu-id="79bc7-123">Zestaw o silnej nazwie można zainstalować w globalnej pamięci podręcznej zestawów i wymaga podpisu od jego wydawcy.</span><span class="sxs-lookup"><span data-stu-id="79bc7-123">A strong-named assembly can be installed in the global assembly cache and requires a signature from its publisher.</span></span> <span data-ttu-id="79bc7-124">Zestawy, które nie mają silnej nazwy, muszą być zainstalowane w katalogu aplikacji klienta.</span><span class="sxs-lookup"><span data-stu-id="79bc7-124">Assemblies that are not strong named must be installed in the application directory of the client.</span></span>

## <a name="see-also"></a><span data-ttu-id="79bc7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79bc7-125">See also</span></span>

- [<span data-ttu-id="79bc7-126">Współdziałanie z kodem niezarządzanym</span><span class="sxs-lookup"><span data-stu-id="79bc7-126">Interoperating with Unmanaged Code</span></span>](index.md)
- [<span data-ttu-id="79bc7-127">Przykład międzyoperacyjnego modelu COM: Klient modelu COM i serwer .NET</span><span class="sxs-lookup"><span data-stu-id="79bc7-127">COM Interop Sample: COM Client and .NET Server</span></span>](com-interop-sample-com-client-and-net-server.md)
