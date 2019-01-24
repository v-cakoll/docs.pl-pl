---
title: Pakowanie zestawu dla modelu COM
ms.date: 03/30/2017
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
ms.openlocfilehash: 453ace4af7ce07c8d81b6d7ece71140e04bfa9bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531515"
---
# <a name="packaging-an-assembly-for-com"></a><span data-ttu-id="e7deb-102">Pakowanie zestawu dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="e7deb-102">Packaging an Assembly for COM</span></span>
<span data-ttu-id="e7deb-103">COM, deweloperzy mogą korzystać z następujące informacje na temat typów zarządzanych, ich planowanie, które należy uwzględnić w swoich aplikacji:</span><span class="sxs-lookup"><span data-stu-id="e7deb-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>  
  
-   <span data-ttu-id="e7deb-104">Lista typów, które mogą używać aplikacje COM</span><span class="sxs-lookup"><span data-stu-id="e7deb-104">A list of types that COM applications can consume</span></span>  
  
     <span data-ttu-id="e7deb-105">Niektóre typy zarządzane są niewidoczne dla modelu COM; Niektóre z nich są widoczne, ale nie jest możliwość utworzenia; a niektóre są widoczne i możliwe do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="e7deb-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="e7deb-106">Zestaw może zawierać dowolną kombinację typów niewidoczna, nie możliwe do utworzenia, przejrzyste i możliwe do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="e7deb-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="e7deb-107">Aby informacje były kompletne identyfikacji typów w zestawie, który chcesz udostępnić w COM, szczególnie w przypadku, gdy te typy są podzbiorem typy widoczne dla programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e7deb-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>  
  
     <span data-ttu-id="e7deb-108">Aby uzyskać więcej informacji, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](qualifying-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="e7deb-108">For additional information, see [Qualifying .NET Types for Interoperation](qualifying-net-types-for-interoperation.md).</span></span>  
  
-   <span data-ttu-id="e7deb-109">Instrukcje obsługi wersji</span><span class="sxs-lookup"><span data-stu-id="e7deb-109">Versioning instructions</span></span>  
  
     <span data-ttu-id="e7deb-110">Klasy zarządzane, które implementują interfejs klasy (generowany międzyoperacyjności interfejsu COM) podlegają przechowywanie wersji ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="e7deb-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>  
  
     <span data-ttu-id="e7deb-111">Aby uzyskać wskazówki na temat korzystania z interfejsu klasy, zobacz [wprowadzenie interfejsu klasy](com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="e7deb-111">For guidelines on using the class interface, see [Introducing the class interface](com-callable-wrapper.md#introducing-the-class-interface).</span></span>  
  
-   <span data-ttu-id="e7deb-112">Instrukcje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="e7deb-112">Deployment instructions</span></span>  
  
     <span data-ttu-id="e7deb-113">Zestawy o silnych nazwach, które są podpisane przez wydawcę, można zainstalować w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="e7deb-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="e7deb-114">Zestawy nieoznaczone musi być zainstalowany na komputerze użytkownika jako zestawy prywatne.</span><span class="sxs-lookup"><span data-stu-id="e7deb-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>  
  
     <span data-ttu-id="e7deb-115">Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../app-domains/assembly-security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="e7deb-115">For additional information, see [Assembly Security Considerations](../app-domains/assembly-security-considerations.md).</span></span>  
  
-   <span data-ttu-id="e7deb-116">Włączenie biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e7deb-116">Type library inclusion</span></span>  
  
     <span data-ttu-id="e7deb-117">Większość typów wymagają bibliotekę typów, gdy jest używane przez aplikacji modelu COM.</span><span class="sxs-lookup"><span data-stu-id="e7deb-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="e7deb-118">Możesz wygenerować bibliotekę typów lub masz deweloperów COM wykonania tego zadania.</span><span class="sxs-lookup"><span data-stu-id="e7deb-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="e7deb-119">[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] Udostępnia następujące opcje podczas generowania biblioteki typów:</span><span class="sxs-lookup"><span data-stu-id="e7deb-119">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] provides the following options for generating a type library:</span></span>  
  
    -   [<span data-ttu-id="e7deb-120">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e7deb-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)  
  
    -   [<span data-ttu-id="e7deb-121">Typelibconverter — klasa</span><span class="sxs-lookup"><span data-stu-id="e7deb-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)  
  
    -   [<span data-ttu-id="e7deb-122">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="e7deb-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)  
  
    -   [<span data-ttu-id="e7deb-123">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="e7deb-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)  
  
     <span data-ttu-id="e7deb-124">Niezależnie od wybranego mechanizmu tylko typy publiczne zdefiniowane w zestawie, który podasz znajdują się w wygenerowanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="e7deb-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>  
  
     <span data-ttu-id="e7deb-125">Można bibliotekę typów w osobnym pliku pakietu lub osadzenie go jako plik zasobów Win32 w ciągu. Aplikacja oparta na sieci.</span><span class="sxs-lookup"><span data-stu-id="e7deb-125">You can package a type library as a separate file or embed it as Win32 resource file within a .NET-based application.</span></span> <span data-ttu-id="e7deb-126">Microsoft Visual Basic 6.0 wykonać to zadanie dla Ciebie automatycznie. Jednakże korzystając z [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], należy ręcznie osadzić biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="e7deb-126">Microsoft Visual Basic 6.0 performed this task for you automatically; however, when using [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)], you must embed your type library manually.</span></span> <span data-ttu-id="e7deb-127">Aby uzyskać instrukcje, zobacz [jak: Osadzanie bibliotek typu jako zasobów Win32 w. Aplikacje oparte na NET](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e7deb-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100)).</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor1"></a>   
## <a name="type-library-exporter"></a><span data-ttu-id="e7deb-128">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="e7deb-128">Type Library Exporter</span></span>  
 <span data-ttu-id="e7deb-129">[Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) jest narzędziem wiersza polecenia, który konwertuje klasy i interfejsy, które są zawarte w zestawie do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="e7deb-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="e7deb-130">Po udostępnieniu informacji o typie klasy klientów modelu COM można utworzyć wystąpienia klasy .NET i wywołać metodę wystąpienia, tak, jakby był to obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="e7deb-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="e7deb-131">Tlbexp.exe konwertuje cały zespół w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="e7deb-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="e7deb-132">Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="e7deb-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor2"></a>   
## <a name="typelibconverter-class"></a><span data-ttu-id="e7deb-133">Typelibconverter — klasa</span><span class="sxs-lookup"><span data-stu-id="e7deb-133">TypeLibConverter Class</span></span>  
 <span data-ttu-id="e7deb-134"><xref:System.Runtime.InteropServices.TypeLibConverter> Klasy, z siedzibą na terenie **System.Runtime.Interop** konwertuje przestrzeni nazw, klasy i interfejsy, które są zawarte w zestawie do biblioteki typów COM.</span><span class="sxs-lookup"><span data-stu-id="e7deb-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="e7deb-135">Ten interfejs API zapewnia te same informacje o typie, eksporter biblioteki typów, opisanych w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="e7deb-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>  
  
 <span data-ttu-id="e7deb-136">**Typelibconverter — klasa** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="e7deb-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor3"></a>   
## <a name="assembly-registration-tool"></a><span data-ttu-id="e7deb-137">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="e7deb-137">Assembly Registration Tool</span></span>  
 <span data-ttu-id="e7deb-138">[Narzędzie rejestracji zestawów (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) można wygenerować i zarejestrować bibliotekę typów, po zastosowaniu **/TLB:** opcji.</span><span class="sxs-lookup"><span data-stu-id="e7deb-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="e7deb-139">Klienci COM wymagają zainstalowania biblioteki typów w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="e7deb-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="e7deb-140">Bez tej opcji Regasm.exe rejestruje typy tylko w zestawie nie biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="e7deb-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="e7deb-141">Rejestrowanie typów w zestawie i rejestrowania biblioteki typów są różne działania.</span><span class="sxs-lookup"><span data-stu-id="e7deb-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>  
  
<a name="cpconpackagingassemblyforcomanchor4"></a>   
## <a name="net-services-installation-tool"></a><span data-ttu-id="e7deb-142">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="e7deb-142">.NET Services Installation Tool</span></span>  
 <span data-ttu-id="e7deb-143">[Narzędzie instalacji usług .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje klas zarządzanych do usługi składników systemu Windows 2000 i łączy kilka zadań w ramach jednego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="e7deb-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="e7deb-144">Oprócz ładowania i zarejestrowaniu zestawu, Regsvcs.exe wygenerować, rejestrowanie i zainstalować biblioteki typów do istniejącej aplikacji COM + 1.0.</span><span class="sxs-lookup"><span data-stu-id="e7deb-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7deb-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7deb-145">See also</span></span>
- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="e7deb-146">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="e7deb-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="e7deb-147">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="e7deb-147">Qualifying .NET Types for Interoperation</span></span>](qualifying-net-types-for-interoperation.md)
- [<span data-ttu-id="e7deb-148">Wprowadzenie interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="e7deb-148">Introducing the class interface</span></span>](com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="e7deb-149">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="e7deb-149">Assembly Security Considerations</span></span>](../app-domains/assembly-security-considerations.md)
- [<span data-ttu-id="e7deb-150">Tlbexp.exe (eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="e7deb-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="e7deb-151">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="e7deb-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="e7deb-152">[Instrukcje: Osadzanie bibliotek typu jako zasobów Win32 w aplikacjach](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="e7deb-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://msdn.microsoft.com/library/c97b4b8c-2ab7-4ac7-8fc8-0ba5c5d59c44(v=vs.100))</span></span>
