---
title: "Kwalifikowanie typów .NET do międzyoperacyjności"
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
- COM interop, qualifying .NET types
- qualifying .NET types for interoperation
- interoperation with unmanaged code, qualifying .NET types
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: 4b8afb52-fb8d-4e65-b47c-fd82956a3cdd
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b6487c151f49f6084977deb600e7f93e5eb7acee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="qualifying-net-types-for-interoperation"></a><span data-ttu-id="66622-102">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="66622-102">Qualifying .NET Types for Interoperation</span></span>
<span data-ttu-id="66622-103">Jeśli zamierzasz ujawniać typów w zestawie do aplikacji modelu COM, należy uwzględnić wymagania Usługa międzyoperacyjna modelu COM w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="66622-103">If you intend to expose types in an assembly to COM applications, consider the requirements of COM interop at design time.</span></span> <span data-ttu-id="66622-104">Typy zarządzane (klasy, interfejsu struktury i wyliczenia) są bezproblemowo integrowane z typów COM podczas stosować się do następujących wytycznych:</span><span class="sxs-lookup"><span data-stu-id="66622-104">Managed types (class, interface, structure, and enumeration) seamlessly integrate with COM types when you adhere to the following guidelines:</span></span>  
  
-   <span data-ttu-id="66622-105">Klasy powinny jawnie implementować interfejsów.</span><span class="sxs-lookup"><span data-stu-id="66622-105">Classes should implement interfaces explicitly.</span></span>  
  
     <span data-ttu-id="66622-106">Współdziałanie z COM zapewnia mechanizm do automatycznego generowania interfejs zawierający wszystkie elementy członkowskie klasy i elementów członkowskich klasy podstawowej, jednak dotychczas lepiej jest zapewnienie jawne interfejsy.</span><span class="sxs-lookup"><span data-stu-id="66622-106">Although COM interop provides a mechanism to automatically generate an interface containing all members of the class and the members of its base class, it is far better to provide explicit interfaces.</span></span> <span data-ttu-id="66622-107">Interfejs automatycznie generowanych nosi nazwę interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="66622-107">The automatically generated interface is called the class interface.</span></span> <span data-ttu-id="66622-108">Aby uzyskać wskazówki, zobacz [wprowadzenie interfejsu klasy](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span><span class="sxs-lookup"><span data-stu-id="66622-108">For guidelines, see [Introducing the Class Interface](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024).</span></span>  
  
     <span data-ttu-id="66622-109">Można użyć [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C# i C++ włączenie definicji interfejsów w kodzie, zamiast używać języka definicji interfejsu (IDL) lub jego odpowiednik.</span><span class="sxs-lookup"><span data-stu-id="66622-109">You can use [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++ to incorporate interface definitions in your code, instead of having to use Interface Definition Language (IDL) or its equivalent.</span></span> <span data-ttu-id="66622-110">Szczegółowe informacje składni zobacz dokumentację języka.</span><span class="sxs-lookup"><span data-stu-id="66622-110">For syntax details, see your language documentation.</span></span>  
  
-   <span data-ttu-id="66622-111">Typy zarządzane muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="66622-111">Managed types must be public.</span></span>  
  
     <span data-ttu-id="66622-112">Tylko typy publiczne w zestawie są rejestrowane i wyeksportowane do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="66622-112">Only public types in an assembly are registered and exported to the type library.</span></span> <span data-ttu-id="66622-113">W związku z tym tylko typy publiczne są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="66622-113">As a result, only public types are visible to COM.</span></span>  
  
     <span data-ttu-id="66622-114">Zarządzane typy Uwidacznianie funkcji do innych kod zarządzany, które nie mogą zostać udostępnione modelowi COM.</span><span class="sxs-lookup"><span data-stu-id="66622-114">Managed types expose features to other managed code that might not be exposed to COM.</span></span> <span data-ttu-id="66622-115">Na przykład stałej pola, metody statyczne i konstruktory sparametryzowane nie są widoczne dla klientów modelu COM.</span><span class="sxs-lookup"><span data-stu-id="66622-115">For instance, parameterized constructors, static methods, and constant fields are not exposed to COM clients.</span></span> <span data-ttu-id="66622-116">Co więcej ponieważ środowisko uruchomieniowe marshals danych do i z typem, danych może skopiowane lub przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="66622-116">Further, as the runtime marshals data in and out of a type, the data might be copied or transformed.</span></span>  
  
-   <span data-ttu-id="66622-117">Metody, właściwości, pól i zdarzenia muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="66622-117">Methods, properties, fields, and events must be public.</span></span>  
  
     <span data-ttu-id="66622-118">Elementy członkowskie typów publicznych również muszą być publiczne, jeśli mają być widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="66622-118">Members of public types must also be public if they are to be visible to COM.</span></span> <span data-ttu-id="66622-119">Można ograniczyć widoczność zestawu, typu publicznego lub publiczne elementy członkowskie typu publicznego, stosując <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span><span class="sxs-lookup"><span data-stu-id="66622-119">You can restrict the visibility of an assembly, a public type, or public members of a public type by applying the <xref:System.Runtime.InteropServices.ComVisibleAttribute>.</span></span> <span data-ttu-id="66622-120">Domyślnie wszystkie typy publiczne i elementy członkowskie są widoczne.</span><span class="sxs-lookup"><span data-stu-id="66622-120">By default, all public types and members are visible.</span></span>  
  
-   <span data-ttu-id="66622-121">Typy muszą mieć publicznego konstruktora domyślnego do aktywacji z modelu COM.</span><span class="sxs-lookup"><span data-stu-id="66622-121">Types must have a public default constructor to be activated from COM.</span></span>  
  
     <span data-ttu-id="66622-122">Typy zarządzane, public są widoczne dla modelu COM.</span><span class="sxs-lookup"><span data-stu-id="66622-122">Managed, public types are visible to COM.</span></span> <span data-ttu-id="66622-123">Jednak bez publicznego konstruktora domyślnego (konstruktora bez argumentów), klienci COM nie można utworzyć typu.</span><span class="sxs-lookup"><span data-stu-id="66622-123">However, without a public default constructor (a constructor with no arguments), COM clients cannot create the type.</span></span> <span data-ttu-id="66622-124">Klienci COM można nadal używać typu, jeśli jest aktywowany przy użyciu innych metod.</span><span class="sxs-lookup"><span data-stu-id="66622-124">COM clients can still use the type if it is activated by some other means.</span></span>  
  
-   <span data-ttu-id="66622-125">Typy nie mogą być abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="66622-125">Types cannot be abstract.</span></span>  
  
     <span data-ttu-id="66622-126">Klienci COM ani klientów platformy .NET nie można utworzyć typy abstrakcyjne.</span><span class="sxs-lookup"><span data-stu-id="66622-126">Neither COM clients nor .NET clients can create abstract types.</span></span>  
  
 <span data-ttu-id="66622-127">Podczas eksportowania dla modelu COM, właściwości jest spłaszczona hierarchii dziedziczenia typu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="66622-127">When exported to COM, the inheritance hierarchy of a managed type is flattened.</span></span> <span data-ttu-id="66622-128">Przechowywanie wersji różni się między środowiskami zarządzane i niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="66622-128">Versioning also differs between managed and unmanaged environments.</span></span> <span data-ttu-id="66622-129">Typy widoczne dla modelu COM nie mają takie same charakterystyki przechowywania wersji, jak inne typy zarządzane.</span><span class="sxs-lookup"><span data-stu-id="66622-129">Types exposed to COM do not have the same versioning characteristics as other managed types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66622-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="66622-130">See Also</span></span>  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>  
 [<span data-ttu-id="66622-131">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="66622-131">Exposing .NET Framework Components to COM</span></span>](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="66622-132">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="66622-132">Introducing the Class Interface</span></span>](http://msdn.microsoft.com/en-us/733c0dd2-12e5-46e6-8de1-39d5b25df024)  
 [<span data-ttu-id="66622-133">Stosowanie atrybutów międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="66622-133">Applying Interop Attributes</span></span>](../../../docs/framework/interop/applying-interop-attributes.md)  
 [<span data-ttu-id="66622-134">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="66622-134">Packaging an Assembly for COM</span></span>](../../../docs/framework/interop/packaging-an-assembly-for-com.md)
