---
title: Pakowanie zestawu .NET Framework dla modelu COM
description: Pakowanie zestawu .NET dla modelu COM. Zbierz listę typów, których mogą używać aplikacje COM, instrukcje dotyczące obsługi wersji i wdrażania oraz bibliotekę typów.
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
ms.openlocfilehash: 4963892419fd1caec4483123f820d62967a87dd6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620836"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="fcf7f-104">Pakowanie zestawu .NET Framework dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="fcf7f-104">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="fcf7f-105">Deweloperzy COM mogą skorzystać z następujących informacji o zarządzanych typach, które mają zostać dołączone do swojej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="fcf7f-105">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="fcf7f-106">Lista typów, których mogą używać aplikacje COM</span><span class="sxs-lookup"><span data-stu-id="fcf7f-106">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="fcf7f-107">Niektóre typy zarządzane są niewidoczne dla modelu COM. Niektóre są widoczne, ale nie mogą być możliwe do utworzenia; a niektóre są widoczne i możliwe do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-107">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="fcf7f-108">Zestaw może składać się z dowolnej kombinacji typów niewidocznych, widocznych, niemożliwych do utworzenia i do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-108">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="fcf7f-109">Aby uzyskać kompletność, zidentyfikuj typy w zestawie, które zamierzasz uwidocznić dla modelu COM, zwłaszcza gdy te typy są podzbiorem typów ujawnionych dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-109">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="fcf7f-110">Aby uzyskać dodatkowe informacje, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="fcf7f-110">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="fcf7f-111">Instrukcje dotyczące obsługi wersji</span><span class="sxs-lookup"><span data-stu-id="fcf7f-111">Versioning instructions</span></span>

  <span data-ttu-id="fcf7f-112">Klasy zarządzane implementujące interfejs klasy (interfejs oparty na modelu COM Interop) podlegają ograniczeniom dotyczącym wersji.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-112">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="fcf7f-113">Aby uzyskać wskazówki dotyczące używania interfejsu klasy, zobacz [wprowadzenie do interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="fcf7f-113">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="fcf7f-114">Instrukcje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="fcf7f-114">Deployment instructions</span></span>

  <span data-ttu-id="fcf7f-115">Zestawy o silnych nazwach, które są podpisane przez wydawcę, można zainstalować w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-115">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="fcf7f-116">Zestawy bez znaku muszą być zainstalowane na komputerze użytkownika jako prywatne zespoły.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-116">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="fcf7f-117">Aby uzyskać dodatkowe informacje, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="fcf7f-117">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="fcf7f-118">Dołączanie biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-118">Type library inclusion</span></span>

  <span data-ttu-id="fcf7f-119">Większość typów wymaga biblioteki typów, gdy jest używana przez aplikację COM.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-119">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="fcf7f-120">Można wygenerować bibliotekę typów lub mieć deweloperów COM wykonujących to zadanie.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-120">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="fcf7f-121">Windows SDK udostępnia następujące opcje generowania biblioteki typów:</span><span class="sxs-lookup"><span data-stu-id="fcf7f-121">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="fcf7f-122">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-122">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="fcf7f-123">Klasa TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="fcf7f-123">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="fcf7f-124">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-124">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="fcf7f-125">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="fcf7f-125">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="fcf7f-126">Niezależnie od wybranego mechanizmu, tylko typy publiczne zdefiniowane w zestawie, które dostarczasz, są uwzględniane w wygenerowanej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-126">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="fcf7f-127">Aby uzyskać instrukcje, zobacz [How to: embed Library Type librarys as Win32 Resources in. Aplikacje oparte na sieci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="fcf7f-127">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="fcf7f-128">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-128">Type Library Exporter</span></span>

<span data-ttu-id="fcf7f-129">[Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) to narzędzie wiersza polecenia, które konwertuje klasy i interfejsy zawarte w zestawie do biblioteki typów com.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-129">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="fcf7f-130">Po udostępnieniu informacji o typie klasy klienci COM mogą utworzyć wystąpienie klasy .NET i wywoływać metody tego wystąpienia, tak jakby był to obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-130">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="fcf7f-131">Tlbexp.exe konwertuje cały zestaw jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-131">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="fcf7f-132">Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-132">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="fcf7f-133">Klasa TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="fcf7f-133">TypeLibConverter Class</span></span>

<span data-ttu-id="fcf7f-134"><xref:System.Runtime.InteropServices.TypeLibConverter>Klasa znajdująca się w przestrzeni nazw **System. Runtime. Interop** konwertuje klasy i interfejsy zawarte w zestawie na bibliotekę typów com.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-134">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="fcf7f-135">Ten interfejs API tworzy takie same informacje o typie, jak Eksporter biblioteki typów, opisany w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-135">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="fcf7f-136">**Klasa TypeLibConverter** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter> .</span><span class="sxs-lookup"><span data-stu-id="fcf7f-136">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="fcf7f-137">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-137">Assembly Registration Tool</span></span>

<span data-ttu-id="fcf7f-138">[Narzędzie do rejestracji zestawu (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) może generować i rejestrować biblioteki typów w przypadku zastosowania opcji **/tlb:** .</span><span class="sxs-lookup"><span data-stu-id="fcf7f-138">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="fcf7f-139">Klienci COM wymagają, aby biblioteki typów były zainstalowane w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-139">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="fcf7f-140">Bez tej opcji Regasm.exe rejestruje typy w zestawie, a nie w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-140">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="fcf7f-141">Rejestrowanie typów w zestawie i rejestrowanie biblioteki typów to odrębne działania.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-141">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="fcf7f-142">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="fcf7f-142">.NET Services Installation Tool</span></span>

<span data-ttu-id="fcf7f-143">[Narzędzie instalacji usług .NET (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje klasy zarządzane do usług składników systemu Windows 2000 i łączy kilka zadań w ramach jednego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-143">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="fcf7f-144">Oprócz ładowania i rejestrowania zestawu, Regsvcs.exe mogą generować, rejestrować i instalować bibliotekę typów w istniejącej aplikacji COM+ 1,0.</span><span class="sxs-lookup"><span data-stu-id="fcf7f-144">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="fcf7f-145">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fcf7f-145">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="fcf7f-146">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="fcf7f-146">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="fcf7f-147">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="fcf7f-147">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="fcf7f-148">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="fcf7f-148">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="fcf7f-149">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="fcf7f-149">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="fcf7f-150">Tlbexp.exe (Eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="fcf7f-150">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="fcf7f-151">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="fcf7f-151">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="fcf7f-152">[Instrukcje: osadzanie bibliotek typów jako zasobów Win32 w aplikacjach](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="fcf7f-152">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
