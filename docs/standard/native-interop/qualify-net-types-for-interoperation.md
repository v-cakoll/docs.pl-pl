---
title: Kwalifikowanie typów .NET do współdziałania z modelem COM
description: Ten artykuł zawiera wskazówki ułatwiające uwidocznienie typów w zestawie .NET w aplikacjach COM dla współdziałania z modelem COM.
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
ms.openlocfilehash: 5e8d604c8152d37475bf93e3b5687f24cfebfa02
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84285966"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="5d5a2-103">Kwalifikowanie typów .NET do współdziałania z modelem COM</span><span class="sxs-lookup"><span data-stu-id="5d5a2-103">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="5d5a2-104">Jeśli zamierzasz uwidocznić typy w zestawie w aplikacjach COM, weź pod uwagę wymagania międzyoperacyjności modelu COM w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="5d5a2-105">Typy zarządzane (Klasa, interfejs, struktura i Wyliczenie) bezproblemowo integrują się z typami COM w przypadku przestrzegania następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="5d5a2-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="5d5a2-106">Klasy powinny jawnie implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="5d5a2-107">Chociaż usługa międzyoperacyjna modelu COM zapewnia mechanizm automatycznego generowania interfejsu zawierającego wszystkie elementy członkowskie klasy i elementy członkowskie swojej klasy podstawowej, znacznie lepiej jest zapewnić jawne interfejsy.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="5d5a2-108">Wygenerowany automatycznie interfejs jest nazywany interfejsem klasy.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="5d5a2-109">Aby uzyskać wskazówki, zobacz [wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="5d5a2-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="5d5a2-110">Można użyć Visual Basic, C# i C++ do dołączania definicji interfejsu w kodzie, zamiast konieczności używania języka definicji interfejsu (IDL) lub jego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="5d5a2-111">Aby uzyskać szczegółowe informacje na temat składni, zobacz dokumentację języka.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="5d5a2-112">Typy zarządzane muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="5d5a2-113">Tylko typy publiczne w zestawie są rejestrowane i eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="5d5a2-114">W efekcie tylko typy publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="5d5a2-115">Zarządzane typy ujawniają funkcje w innym zarządzanym kodzie, który może nie być ujawniony w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="5d5a2-116">Na przykład, konstruktory sparametryzowane, metody statyczne i pola stałe nie są widoczne dla klientów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="5d5a2-117">Ponadto, ponieważ środowisko uruchomieniowe prowadzi dane do i z typu, dane mogą być kopiowane lub przekształcane.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="5d5a2-118">Metody, właściwości, pola i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="5d5a2-119">Elementy członkowskie typów publicznych muszą być również publiczne, jeśli mają być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="5d5a2-120">Można ograniczyć widoczność zestawu, typu publicznego lub publicznych składowych typu publicznego przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute> .</span><span class="sxs-lookup"><span data-stu-id="5d5a2-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="5d5a2-121">Domyślnie wszystkie typy publiczne i członkowie są widoczne.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="5d5a2-122">Typy muszą mieć publiczny Konstruktor bez parametrów, który ma być aktywowany z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="5d5a2-123">Typy zarządzane i publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="5d5a2-124">Niemniej jednak, jeśli nie ma publicznego konstruktora bez parametrów (Konstruktor bez argumentów), klienci COM nie mogą utworzyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="5d5a2-125">Klienci modelu COM nadal mogą używać typu, jeśli jest aktywowany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="5d5a2-126">Typy nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="5d5a2-127">Żaden klient COM ani klient .NET nie mogą tworzyć typów abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="5d5a2-128">Po eksportowaniu do modelu COM Hierarchia dziedziczenia typu zarządzanego jest spłaszczona.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="5d5a2-129">Przechowywanie wersji różni się również między środowiskami zarządzanymi i niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="5d5a2-130">Typy ujawnione dla modelu COM nie mają takich samych cech wersji jak inne typy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="5d5a2-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5a2-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d5a2-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="5d5a2-132">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="5d5a2-132">Exposing .NET Framework Components to COM</span></span>](../../framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="5d5a2-133">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="5d5a2-133">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="5d5a2-134">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="5d5a2-134">Applying Interop Attributes</span></span>](apply-interop-attributes.md)
- [<span data-ttu-id="5d5a2-135">Pakowanie zestawu .NET Framework dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="5d5a2-135">Packaging a .NET Framework Assembly for COM</span></span>](../../framework/interop/packaging-an-assembly-for-com.md)
