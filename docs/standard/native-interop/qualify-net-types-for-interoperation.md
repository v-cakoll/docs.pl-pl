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
ms.openlocfilehash: 5b122befffbcad39258393462c75ac20431d9136
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420503"
---
# <a name="qualifying-net-types-for-com-interoperation"></a><span data-ttu-id="3262e-103">Kwalifikowanie typów .NET do współdziałania z modelem COM</span><span class="sxs-lookup"><span data-stu-id="3262e-103">Qualifying .NET Types for COM Interoperation</span></span>
<span data-ttu-id="3262e-104">Jeśli zamierzasz uwidocznić typy w zestawie w aplikacjach COM, weź pod uwagę wymagania międzyoperacyjności modelu COM w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="3262e-104">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="3262e-105">Typy zarządzane (Klasa, interfejs, struktura i Wyliczenie) bezproblemowo integrują się z typami COM w przypadku przestrzegania następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="3262e-105">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
- <span data-ttu-id="3262e-106">Klasy powinny jawnie implementować interfejsy.</span><span class="sxs-lookup"><span data-stu-id="3262e-106">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="3262e-107">Chociaż usługa międzyoperacyjna modelu COM zapewnia mechanizm automatycznego generowania interfejsu zawierającego wszystkie elementy członkowskie klasy i elementy członkowskie swojej klasy podstawowej, znacznie lepiej jest zapewnić jawne interfejsy.</span><span class="sxs-lookup"><span data-stu-id="3262e-107">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="3262e-108">Wygenerowany automatycznie interfejs jest nazywany interfejsem klasy.</span><span class="sxs-lookup"><span data-stu-id="3262e-108">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="3262e-109">Aby uzyskać wskazówki, zobacz [wprowadzenie do interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="3262e-109">For guidelines, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
     <span data-ttu-id="3262e-110">Można użyć Visual Basic, C# i C++ do dołączania definicji interfejsu w kodzie, zamiast konieczności używania języka definicji interfejsu (IDL) lub jego odpowiednika.</span><span class="sxs-lookup"><span data-stu-id="3262e-110">You can use Visual Basic, C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="3262e-111">Aby uzyskać szczegółowe informacje na temat składni, zobacz dokumentację języka.</span><span class="sxs-lookup"><span data-stu-id="3262e-111">For syntax details, see your language documentation.</span></span>  
  
- <span data-ttu-id="3262e-112">Typy zarządzane muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="3262e-112">Managed types must be public.</span></span>  
  
     <span data-ttu-id="3262e-113">Tylko typy publiczne w zestawie są rejestrowane i eksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="3262e-113">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="3262e-114">W efekcie tylko typy publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-114">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="3262e-115">Zarządzane typy ujawniają funkcje w innym zarządzanym kodzie, który może nie być ujawniony w modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-115">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="3262e-116">Na przykład, konstruktory sparametryzowane, metody statyczne i pola stałe nie są widoczne dla klientów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-116">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="3262e-117">Ponadto, ponieważ środowisko uruchomieniowe prowadzi dane do i z typu, dane mogą być kopiowane lub przekształcane.</span><span class="sxs-lookup"><span data-stu-id="3262e-117">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
- <span data-ttu-id="3262e-118">Metody, właściwości, pola i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="3262e-118">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="3262e-119">Elementy członkowskie typów publicznych muszą być również publiczne, jeśli mają być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-119">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="3262e-120">Można ograniczyć widoczność zestawu, typu publicznego lub publicznych składowych typu publicznego przez zastosowanie <xref:System.Runtime.InteropServices.ComVisibleAttribute> .</span><span class="sxs-lookup"><span data-stu-id="3262e-120">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="3262e-121">Domyślnie wszystkie typy publiczne i członkowie są widoczne.</span><span class="sxs-lookup"><span data-stu-id="3262e-121">By default, all public types and members are visible.</span></span>  
  
- <span data-ttu-id="3262e-122">Typy muszą mieć publiczny Konstruktor bez parametrów, który ma być aktywowany z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-122">Types must have a public parameterless constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="3262e-123">Typy zarządzane i publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="3262e-123">Managed, public types are visible to COM.</span></span> <span data-ttu-id="3262e-124">Niemniej jednak, jeśli nie ma publicznego konstruktora bez parametrów (Konstruktor bez argumentów), klienci COM nie mogą utworzyć tego typu.</span><span class="sxs-lookup"><span data-stu-id="3262e-124">However, without a public parameterless constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="3262e-125">Klienci modelu COM nadal mogą używać typu, jeśli jest aktywowany w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="3262e-125">COM clients can still use the type if it is activated by some other means.</span></span>  
  
- <span data-ttu-id="3262e-126">Typy nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="3262e-126">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="3262e-127">Żaden klient COM ani klient .NET nie mogą tworzyć typów abstrakcyjnych.</span><span class="sxs-lookup"><span data-stu-id="3262e-127">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="3262e-128">Po eksportowaniu do modelu COM Hierarchia dziedziczenia typu zarządzanego jest spłaszczona.</span><span class="sxs-lookup"><span data-stu-id="3262e-128">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="3262e-129">Przechowywanie wersji różni się również między środowiskami zarządzanymi i niezarządzanymi.</span><span class="sxs-lookup"><span data-stu-id="3262e-129">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="3262e-130">Typy ujawnione dla modelu COM nie mają takich samych cech wersji jak inne typy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="3262e-130">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3262e-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3262e-131">See also</span></span>

- <xref:System.Runtime.InteropServices.ComVisibleAttribute>
- [<span data-ttu-id="3262e-132">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="3262e-132">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="3262e-133">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="3262e-133">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="3262e-134">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="3262e-134">Applying Interop Attributes</span></span>](../../../docs/standard/native-interop/apply-interop-attributes.md)
- [<span data-ttu-id="3262e-135">Pakowanie zestawu .NET Framework dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="3262e-135">Packaging a .NET Framework Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
