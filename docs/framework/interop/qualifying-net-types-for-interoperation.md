---
title: Kwalifikowanie typów .NET do międzyoperacyjności
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e57ec1a70aaae384f73b1ffdbf92e93fc0a7bdd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648559"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="25bdf-102">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="25bdf-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="25bdf-103">Jeśli zamierzasz ujawnić typy w zestawie, do aplikacji modelu COM, należy wziąć pod uwagę wymagania Usługa międzyoperacyjna modelu COM w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="25bdf-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="25bdf-104">Typy zarządzane (klasy, interfejsu, struktury i wyliczenia) bezproblemowo integrują się z typów modelu COM podczas przestrzegać następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="25bdf-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="25bdf-105">Klasy należy jawnie implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="25bdf-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="25bdf-106">Chociaż usługa międzyoperacyjna modelu COM udostępnia mechanizm do automatycznego generowania interfejs zawierający wszystkie elementy członkowskie klasy i składowych klasy bazowej, jest znacznie lepiej podać jawne interfejsy.</span><span class="sxs-lookup"><span data-stu-id="25bdf-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="25bdf-107">Automatycznie generowanego interfejsu nosi nazwę interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="25bdf-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="25bdf-108">Aby uzyskać wskazówki, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="25bdf-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="25bdf-109">Visual Basic, można użyć C#i C++, funkcje definicji interfejsu w kodzie, nie trzeba używać języka definicji interfejsu (IDL) lub jej odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="25bdf-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="25bdf-110">Szczegóły składni na ten temat można znaleźć w dokumentacji języka.</span><span class="sxs-lookup"><span data-stu-id="25bdf-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="25bdf-111">Typy zarządzane muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="25bdf-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="25bdf-112">Tylko typy publiczne w zestawie są rejestrowane i wyeksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="25bdf-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="25bdf-113">W rezultacie tylko typy publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="25bdf-114">Zarządzane typy udostępniają funkcje do innego kodu zarządzanego, który nie może być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="25bdf-115">Na przykład konstruktory sparametryzowane, metody statyczne i stałe pola nie są widoczne dla klientów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="25bdf-116">Co więcej jak środowisko uruchomieniowe kieruje danych do i z typu, dane mogą zostać skopiowane lub przekształcone.</span><span class="sxs-lookup"><span data-stu-id="25bdf-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="25bdf-117">Metody, właściwości, pola i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="25bdf-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="25bdf-118">Elementów członkowskich typów publicznych również muszą być publiczne, jeśli mają być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="25bdf-119">Widoczność zestaw, typ publiczny lub publiczne elementy członkowskie typu publicznego można ograniczyć, stosując <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25bdf-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="25bdf-120">Domyślnie wszystkie typy publiczne i elementy członkowskie są widoczne.</span><span class="sxs-lookup"><span data-stu-id="25bdf-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="25bdf-121">Typy muszą mieć publicznego konstruktora domyślnego aktywacji z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="25bdf-122">Typy zarządzane, publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="25bdf-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="25bdf-123">Jednak bez publicznego konstruktora domyślnego (Konstruktor bez argumentów), klienci COM nie można utworzyć typu.</span><span class="sxs-lookup"><span data-stu-id="25bdf-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="25bdf-124">Klienci COM można nadal używać typu, jeśli jest aktywna w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="25bdf-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="25bdf-125">Typy nie może być abstrakcyjna.</span><span class="sxs-lookup"><span data-stu-id="25bdf-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="25bdf-126">Klienci COM ani klientów programu .NET nie można utworzyć typów abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="25bdf-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="25bdf-127">Podczas eksportowania dla modelu COM, jest spłaszczany hierarchii dziedziczenia typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="25bdf-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="25bdf-128">Przechowywanie wersji różni się między środowiskami zarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="25bdf-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="25bdf-129">Typy widoczne dla modelu COM nie mają takie same charakterystyki przechowywania wersji, jak inne zarządzane typy.</span><span class="sxs-lookup"><span data-stu-id="25bdf-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25bdf-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25bdf-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="25bdf-131">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="25bdf-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="25bdf-132">Wprowadzenie interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="25bdf-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="25bdf-133">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="25bdf-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="25bdf-134">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="25bdf-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
