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
ms.openlocfilehash: 8b2e14a7508d4a5e8069a3b98dee38a0ac62750c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363985"
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="327c3-102">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="327c3-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="327c3-103">Jeśli zamierzasz uwidocznić typy w zestawie w aplikacjach COM, weź pod uwagę wymagania międzyoperacyjności modelu COM w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="327c3-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="327c3-104">Typy zarządzane (Klasa, interfejs, struktura i Wyliczenie) bezproblemowo integrują się z typami COM w przypadku przestrzegania następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="327c3-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="327c3-105">Klasy powinny jawnie implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="327c3-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="327c3-106">Chociaż usługa międzyoperacyjna modelu COM zapewnia mechanizm automatycznego generowania interfejsu zawierającego wszystkie elementy członkowskie klasy i elementy członkowskie swojej klasy podstawowej, znacznie lepiej jest zapewnić jawne interfejsy.</span><span class="sxs-lookup"><span data-stu-id="327c3-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="327c3-107">Wygenerowany automatycznie interfejs jest nazywany interfejsem klasy.</span><span class="sxs-lookup"><span data-stu-id="327c3-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="327c3-108">Aby uzyskać wskazówki, zobacz [wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="327c3-108">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="327c3-109">Można użyć Visual Basic, C#, i C++ , aby uwzględnić definicje interfejsu w kodzie, zamiast korzystać z języka definicji interfejsu (IDL) lub jego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="327c3-109">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="327c3-110">Aby uzyskać szczegółowe informacje na temat składni, zobacz dokumentację języka.</span><span class="sxs-lookup"><span data-stu-id="327c3-110">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="327c3-111">Typy zarządzane muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="327c3-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="327c3-112">Tylko typy publiczne w zestawie są rejestrowane i eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="327c3-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="327c3-113">W efekcie tylko typy publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="327c3-114">Zarządzane typy ujawniają funkcje w innym zarządzanym kodzie, który może nie być ujawniony w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="327c3-115">Na przykład, konstruktory sparametryzowane, metody statyczne i pola stałe nie są widoczne dla klientów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="327c3-116">Ponadto, ponieważ środowisko uruchomieniowe prowadzi dane do i z typu, dane mogą być kopiowane lub przekształcane.</span><span class="sxs-lookup"><span data-stu-id="327c3-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="327c3-117">Metody, właściwości, pola i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="327c3-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="327c3-118">Elementy członkowskie typów publicznych muszą być również publiczne, jeśli mają być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="327c3-119">Można ograniczyć widoczność zestawu, typu publicznego lub publicznych składowych typu publicznego przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="327c3-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="327c3-120">Domyślnie wszystkie typy publiczne i członkowie są widoczne.</span><span class="sxs-lookup"><span data-stu-id="327c3-120">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="327c3-121">Typy muszą mieć publiczny Konstruktor bez parametrów, który ma być aktywowany z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-121">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="327c3-122">Typy zarządzane i publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="327c3-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="327c3-123">Niemniej jednak, jeśli nie ma publicznego konstruktora bez parametrów (Konstruktor bez argumentów), klienci COM nie mogą utworzyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="327c3-123">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="327c3-124">Klienci modelu COM nadal mogą używać typu, jeśli jest aktywowany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="327c3-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="327c3-125">Typy nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="327c3-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="327c3-126">Żaden klient COM ani klient .NET nie mogą tworzyć typów abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="327c3-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="327c3-127">Po eksportowaniu do modelu COM Hierarchia dziedziczenia typu zarządzanego jest spłaszczona.</span><span class="sxs-lookup"><span data-stu-id="327c3-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="327c3-128">Przechowywanie wersji różni się również między środowiskami zarządzanymi i niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="327c3-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="327c3-129">Typy ujawnione dla modelu COM nie mają takich samych cech wersji jak inne typy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="327c3-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327c3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="327c3-130">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="327c3-131">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="327c3-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="327c3-132">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="327c3-132">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="327c3-133">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="327c3-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)
- [<span data-ttu-id="327c3-134">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="327c3-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
