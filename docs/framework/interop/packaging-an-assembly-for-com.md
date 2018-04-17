---
title: Pakowanie zestawu dla modelu COM
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- exposing .NET Framework components to COM
- COM interop, packaging assemblies
- packaging assemblies for COM
- Tlbexp.exe
- TypeLibConverter class
- .NET Services Installation tool
- Assembly Registration tool
- Type Library Exporter
- Reqsvcs.exe
- interoperation with unmanaged code, exposing .NET Framework components
- interoperation with unmanaged code, packaging assemblies
- COM interop, exposing COM components
- Reqasm.exe
ms.assetid: 39dc55aa-f2a1-4093-87bb-f1c0edb6e761
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5c1e3ee38f98eae46c09ec2175f3c9af01288bd2
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="1a623-102">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="1a623-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="1a623-103">COM deweloperzy mogą korzystać z następujące informacje o typach zarządzanych one ma włączenie w aplikacji:</span><span class="sxs-lookup"><span data-stu-id="1a623-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="1a623-104">Lista typów, które mogą korzystać z aplikacji modelu COM</span><span class="sxs-lookup"><span data-stu-id="1a623-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="1a623-105">Niektóre typy zarządzane są widoczne dla modelu COM; Niektóre są widoczne, ale nie jest możliwość utworzenia; i niektóre są widoczne i możliwość utworzenia.</span><span class="sxs-lookup"><span data-stu-id="1a623-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="1a623-106">Zestaw może obejmować dowolną kombinację typów niewidoczne, widoczne i nie tworzyć oraz możliwość utworzenia.</span><span class="sxs-lookup"><span data-stu-id="1a623-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="1a623-107">Aby informacje były kompletne identyfikacji typów w zestawie, który ma zostać udostępniona modelowi COM, szczególnie w przypadku tych typów są podzbiorem typy widoczne dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1a623-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="1a623-108">Aby uzyskać dodatkowe informacje, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="1a623-108">For additional information, see [Qualifying .NET Types for Interoperation](qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="1a623-109">Instrukcje kontroli wersji</span><span class="sxs-lookup"><span data-stu-id="1a623-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="1a623-110">Klasy zarządzane, które implementują interfejs klasy (wygenerowany interop interfejsu COM) obowiązują ograniczenia wersji.</span><span class="sxs-lookup"><span data-stu-id="1a623-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="1a623-111">Aby uzyskać wskazówki na temat używania interfejsu klasy, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="1a623-111">For guidelines on using the class interface, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
-   <span data-ttu-id="1a623-112">Instrukcje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="1a623-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="1a623-113">Zestawów o silnej nazwie, które są podpisane przez wydawcę może być zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1a623-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="1a623-114">Zestawy nieoznaczone musi być zainstalowany na komputerze użytkownika jako zestawy prywatne.</span><span class="sxs-lookup"><span data-stu-id="1a623-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="1a623-115">Aby uzyskać dodatkowe informacje, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="1a623-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="1a623-116">Włączenie biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="1a623-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="1a623-117">Większość typów wymagają biblioteki typów, gdy używane przez aplikację COM.</span><span class="sxs-lookup"><span data-stu-id="1a623-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="1a623-118">Można wygenerować biblioteki typów lub ma deweloperów COM wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="1a623-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="1a623-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia następujące opcje generowania biblioteki typów:</span><span class="sxs-lookup"><span data-stu-id="1a623-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="1a623-120">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="1a623-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="1a623-121">Typelibconverter — klasa</span><span class="sxs-lookup"><span data-stu-id="1a623-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="1a623-122">Assembly Registration — narzędzie</span><span class="sxs-lookup"><span data-stu-id="1a623-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="1a623-123">.NET services Installation — narzędzie</span><span class="sxs-lookup"><span data-stu-id="1a623-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="1a623-124">Niezależnie od wybranego mechanizmu tylko typy publiczne zdefiniowane w zestawie, który podasz znajdują się w bibliotece typów wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="1a623-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="1a623-125">Możesz biblioteki typów jako osobny plik pakietu lub osadzać go jako plik zasobów Win32 w. Aplikacja Asp.net.</span><span class="sxs-lookup"><span data-stu-id="1a623-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="1a623-126">Microsoft Visual Basic 6.0 wykonać tego zadania można automatycznie; Jednak przy użyciu [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], należy ręcznie osadzić biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="1a623-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="1a623-127">Aby uzyskać instrukcje, zobacz [porady: osadzanie biblioteki typów jako zasobów Win32 w. Aplikacje oparte na sieci](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="1a623-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="1a623-128">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="1a623-128">Type Library Exporter</span></span>  
 <span data-ttu-id="1a623-129">[Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) to narzędzie wiersza polecenia, który konwertuje klasy i interfejsy zawarty w zestawie do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="1a623-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="1a623-130">Po udostępnieniu informacji o typie klasy, klientów modelu COM. można utworzyć wystąpienia klasy .NET i wywołanie metody wystąpienia, tak jakby był obiektem COM.</span><span class="sxs-lookup"><span data-stu-id="1a623-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="1a623-131">Tlbexp.exe konwertuje cały zestaw w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="1a623-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="1a623-132">Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="1a623-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="1a623-133">Typelibconverter — klasa</span><span class="sxs-lookup"><span data-stu-id="1a623-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="1a623-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Klasa znajduje się w **System.Runtime.Interop** konwertuje przestrzeni nazw, klasy i interfejsy zawarty w zestawie do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="1a623-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="1a623-135">Ten interfejs API zapewnia te same informacje typu jako eksporter biblioteki typów opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1a623-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="1a623-136">**Typelibconverter — klasa** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="1a623-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="1a623-137">Assembly Registration — narzędzie</span><span class="sxs-lookup"><span data-stu-id="1a623-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="1a623-138">[Narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) można wygenerować i zarejestrować biblioteki typów, po zastosowaniu **/TLB:** opcji.</span><span class="sxs-lookup"><span data-stu-id="1a623-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="1a623-139">Klienci COM wymagają zainstalowania bibliotek typów w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="1a623-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="1a623-140">Bez tej opcji Regasm.exe tylko rejestruje typów w zestawie nie biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="1a623-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="1a623-141">Rejestrowanie typów w zestawie i rejestrowania biblioteki typów są różne działania.</span><span class="sxs-lookup"><span data-stu-id="1a623-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="1a623-142">.NET services Installation — narzędzie</span><span class="sxs-lookup"><span data-stu-id="1a623-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="1a623-143">[Narzędzie instalacji usług .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje do usługi składnika systemu Windows 2000 zarządzanej klasy i łączy kilka zadań w ramach jednego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1a623-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="1a623-144">Oprócz ładowania i rejestrowanie zestawu, Regsvcs.exe można wygenerować, zarejestrować, a następnie zainstaluj bibliotekę typów do istniejącej aplikacji COM + 1.0.</span><span class="sxs-lookup"><span data-stu-id="1a623-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a623-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a623-145">See Also</span></span>  
 <xref:System.Runtime.InteropServices.TypeLibConverter>  
 <xref:System.Runtime.InteropServices.ITypeLibConverter>  
 [<span data-ttu-id="1a623-146">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="1a623-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)  
 [<span data-ttu-id="1a623-147">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="1a623-147">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)  
 [<span data-ttu-id="1a623-148">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="1a623-148">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)  
 [<span data-ttu-id="1a623-149">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="1a623-149">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)  
 [<span data-ttu-id="1a623-150">Tlbexp.exe (eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="1a623-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)  
 [<span data-ttu-id="1a623-151">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="1a623-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)  
 <span data-ttu-id="1a623-152">[Porady: osadzanie biblioteki typów jako zasobów Win32 w aplikacjach](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1a623-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span></span>
