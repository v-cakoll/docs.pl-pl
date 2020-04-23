---
title: Pakowanie zestawu .NET Framework dla modelu COM
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
ms.openlocfilehash: 6866da283cc7cdd180aada252007d67bd72cd862
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124094"
---
# <a name="packaging-a-net-framework-assembly-for-com"></a><span data-ttu-id="d2ce3-102">Pakowanie zestawu .NET Framework dla modelu COM</span><span class="sxs-lookup"><span data-stu-id="d2ce3-102">Packaging a .NET Framework Assembly for COM</span></span>

<span data-ttu-id="d2ce3-103">Deweloperzy COM mogą skorzystać z następujących informacji o zarządzanych typach, które mają zostać dołączone do swojej aplikacji:</span><span class="sxs-lookup"><span data-stu-id="d2ce3-103">COM developers can benefit from the following information about the managed types they plan to incorporate in their application:</span></span>

- <span data-ttu-id="d2ce3-104">Lista typów, których mogą używać aplikacje COM</span><span class="sxs-lookup"><span data-stu-id="d2ce3-104">A list of types that COM applications can consume</span></span>

  <span data-ttu-id="d2ce3-105">Niektóre typy zarządzane są niewidoczne dla modelu COM. Niektóre są widoczne, ale nie mogą być możliwe do utworzenia; a niektóre są widoczne i możliwe do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-105">Some managed types are invisible to COM; some are visible but not creatable; and some are both visible and creatable.</span></span> <span data-ttu-id="d2ce3-106">Zestaw może składać się z dowolnej kombinacji typów niewidocznych, widocznych, niemożliwych do utworzenia i do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-106">An assembly can comprise any combination of invisible, visible, not creatable, and creatable types.</span></span> <span data-ttu-id="d2ce3-107">Aby uzyskać kompletność, zidentyfikuj typy w zestawie, które zamierzasz uwidocznić dla modelu COM, zwłaszcza gdy te typy są podzbiorem typów ujawnionych dla .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-107">For completeness, identify the types in an assembly that you intend to expose to COM, especially when those types are a subset of the types exposed to the .NET Framework.</span></span>

  <span data-ttu-id="d2ce3-108">Aby uzyskać dodatkowe informacje, zobacz [kwalifikowanie typów .NET do międzyoperacyjności](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="d2ce3-108">For additional information, see [Qualifying .NET Types for Interoperation](../../standard/native-interop/qualify-net-types-for-interoperation.md).</span></span>

- <span data-ttu-id="d2ce3-109">Instrukcje dotyczące obsługi wersji</span><span class="sxs-lookup"><span data-stu-id="d2ce3-109">Versioning instructions</span></span>

  <span data-ttu-id="d2ce3-110">Klasy zarządzane implementujące interfejs klasy (interfejs oparty na modelu COM Interop) podlegają ograniczeniom dotyczącym wersji.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-110">Managed classes that implement the class interface (a COM interop-generated interface) are subject to versioning restrictions.</span></span>

  <span data-ttu-id="d2ce3-111">Aby uzyskać wskazówki dotyczące używania interfejsu klasy, zobacz [wprowadzenie do interfejsu klasy](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span><span class="sxs-lookup"><span data-stu-id="d2ce3-111">For guidelines on using the class interface, see [Introducing the class interface](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface).</span></span>

- <span data-ttu-id="d2ce3-112">Instrukcje dotyczące wdrażania</span><span class="sxs-lookup"><span data-stu-id="d2ce3-112">Deployment instructions</span></span>

  <span data-ttu-id="d2ce3-113">Zestawy o silnych nazwach, które są podpisane przez wydawcę, można zainstalować w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-113">Strong-named assemblies that are signed by a publisher can be installed into the global assembly cache.</span></span> <span data-ttu-id="d2ce3-114">Zestawy bez znaku muszą być zainstalowane na komputerze użytkownika jako prywatne zespoły.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-114">Unsigned assemblies must be installed on the user's machine as private assemblies.</span></span>

  <span data-ttu-id="d2ce3-115">Aby uzyskać dodatkowe informacje, zobacz [zagadnienia dotyczące zabezpieczeń zestawów](../../standard/assembly/security-considerations.md).</span><span class="sxs-lookup"><span data-stu-id="d2ce3-115">For additional information, see [Assembly Security Considerations](../../standard/assembly/security-considerations.md).</span></span>

- <span data-ttu-id="d2ce3-116">Dołączanie biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-116">Type library inclusion</span></span>

  <span data-ttu-id="d2ce3-117">Większość typów wymaga biblioteki typów, gdy jest używana przez aplikację COM.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-117">Most types require a type library when consumed by a COM application.</span></span> <span data-ttu-id="d2ce3-118">Można wygenerować bibliotekę typów lub mieć deweloperów COM wykonujących to zadanie.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-118">You can generate a type library or have COM developers perform this task.</span></span> <span data-ttu-id="d2ce3-119">Windows SDK udostępnia następujące opcje generowania biblioteki typów:</span><span class="sxs-lookup"><span data-stu-id="d2ce3-119">The Windows SDK provides the following options for generating a type library:</span></span>

  - [<span data-ttu-id="d2ce3-120">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-120">Type Library Exporter</span></span>](#cpconpackagingassemblyforcomanchor1)

  - [<span data-ttu-id="d2ce3-121">Klasa TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="d2ce3-121">TypeLibConverter Class</span></span>](#cpconpackagingassemblyforcomanchor2)

  - [<span data-ttu-id="d2ce3-122">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-122">Assembly Registration Tool</span></span>](#cpconpackagingassemblyforcomanchor3)

  - [<span data-ttu-id="d2ce3-123">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="d2ce3-123">.NET Services Installation Tool</span></span>](#cpconpackagingassemblyforcomanchor4)

  <span data-ttu-id="d2ce3-124">Niezależnie od wybranego mechanizmu, tylko typy publiczne zdefiniowane w zestawie, które dostarczasz, są uwzględniane w wygenerowanej bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-124">Regardless of the mechanism you choose, only public types defined in the assembly you supply are included in the generated type library.</span></span>

<span data-ttu-id="d2ce3-125">Aby uzyskać instrukcje, zobacz [How to: embed Library Type librarys as Win32 Resources in. Aplikacje oparte na sieci](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d2ce3-125">For instructions, see [How to: Embed Type Libraries as Win32 Resources in .NET-Based Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100)).</span></span>

<a name="cpconpackagingassemblyforcomanchor1"></a>

## <a name="type-library-exporter"></a><span data-ttu-id="d2ce3-126">Eksporter biblioteki typów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-126">Type Library Exporter</span></span>

<span data-ttu-id="d2ce3-127">[Eksporter biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md) jest narzędziem wiersza polecenia, które konwertuje klasy i interfejsy zawarte w zestawie do biblioteki typów com.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-127">The [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md) is a command-line tool that converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d2ce3-128">Po udostępnieniu informacji o typie klasy klienci COM mogą utworzyć wystąpienie klasy .NET i wywoływać metody tego wystąpienia, tak jakby był to obiekt COM.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-128">Once the type information of the class is available, COM clients can create an instance of the .NET class and call the methods of the instance, just as if it were a COM object.</span></span> <span data-ttu-id="d2ce3-129">Tlbexp. exe konwertuje cały zestaw jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-129">Tlbexp.exe converts an entire assembly at one time.</span></span> <span data-ttu-id="d2ce3-130">Nie można użyć Tlbexp.exe do generowania informacji o typie dla podzbioru typów zdefiniowanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-130">You cannot use Tlbexp.exe to generate type information for a subset of the types defined in an assembly.</span></span>

<a name="cpconpackagingassemblyforcomanchor2"></a>

## <a name="typelibconverter-class"></a><span data-ttu-id="d2ce3-131">Klasa TypeLibConverter</span><span class="sxs-lookup"><span data-stu-id="d2ce3-131">TypeLibConverter Class</span></span>

<span data-ttu-id="d2ce3-132"><xref:System.Runtime.InteropServices.TypeLibConverter> Klasa znajdująca się w przestrzeni nazw **System. Runtime. Interop** konwertuje klasy i interfejsy zawarte w zestawie na bibliotekę typów com.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-132">The <xref:System.Runtime.InteropServices.TypeLibConverter> class, located in the **System.Runtime.Interop** namespace, converts the classes and interfaces contained in an assembly to a COM type library.</span></span> <span data-ttu-id="d2ce3-133">Ten interfejs API tworzy takie same informacje o typie, jak Eksporter biblioteki typów, opisany w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-133">This API produces the same type information as the Type Library Exporter, described in the previous section.</span></span>

<span data-ttu-id="d2ce3-134">**Klasa TypeLibConverter** implementuje <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-134">The **TypeLibConverter class** implements the <xref:System.Runtime.InteropServices.ITypeLibConverter>.</span></span>

<a name="cpconpackagingassemblyforcomanchor3"></a>

## <a name="assembly-registration-tool"></a><span data-ttu-id="d2ce3-135">Narzędzie rejestracji zestawów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-135">Assembly Registration Tool</span></span>

<span data-ttu-id="d2ce3-136">[Narzędzie do rejestracji zestawu (Regasm. exe)](../tools/regasm-exe-assembly-registration-tool.md) może generować i rejestrować biblioteki typów podczas stosowania opcji **/tlb:** .</span><span class="sxs-lookup"><span data-stu-id="d2ce3-136">The [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) can generate and register a type library when you apply the **/tlb:** option.</span></span> <span data-ttu-id="d2ce3-137">Klienci COM wymagają, aby biblioteki typów były zainstalowane w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-137">COM clients require that type libraries be installed in the Windows registry.</span></span> <span data-ttu-id="d2ce3-138">Bez tej opcji Regasm. exe rejestruje typy w zestawie, a nie w bibliotece typów.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-138">Without this option, Regasm.exe only registers the types in an assembly, not the type library.</span></span> <span data-ttu-id="d2ce3-139">Rejestrowanie typów w zestawie i rejestrowanie biblioteki typów to odrębne działania.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-139">Registering the types in an assembly and registering the type library are distinct activities.</span></span>

<a name="cpconpackagingassemblyforcomanchor4"></a>

## <a name="net-services-installation-tool"></a><span data-ttu-id="d2ce3-140">Narzędzie instalacji usług .NET</span><span class="sxs-lookup"><span data-stu-id="d2ce3-140">.NET Services Installation Tool</span></span>

<span data-ttu-id="d2ce3-141">[Narzędzie instalacji usług .NET (Regsvcs. exe)](../tools/regsvcs-exe-net-services-installation-tool.md) dodaje klasy zarządzane do usług składowych systemu Windows 2000 i łączy kilka zadań w ramach jednego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-141">The [.NET Services Installation Tool (Regsvcs.exe)](../tools/regsvcs-exe-net-services-installation-tool.md) adds managed classes to Windows 2000 Component Services and combines several tasks within a single tool.</span></span> <span data-ttu-id="d2ce3-142">Oprócz ładowania i rejestrowania zestawu, Regsvcs. exe może generować, rejestrować i instalować bibliotekę typów w istniejącej aplikacji COM+ 1,0.</span><span class="sxs-lookup"><span data-stu-id="d2ce3-142">In addition to loading and registering an assembly, Regsvcs.exe can generate, register, and install the type library into an existing COM+ 1.0 application.</span></span>

## <a name="see-also"></a><span data-ttu-id="d2ce3-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2ce3-143">See also</span></span>

- <xref:System.Runtime.InteropServices.TypeLibConverter>
- <xref:System.Runtime.InteropServices.ITypeLibConverter>
- [<span data-ttu-id="d2ce3-144">Udostępnianie składników .NET Framework modelowi COM</span><span class="sxs-lookup"><span data-stu-id="d2ce3-144">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="d2ce3-145">Kwalifikowanie typów .NET do międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="d2ce3-145">Qualifying .NET Types for Interoperation</span></span>](../../standard/native-interop/qualify-net-types-for-interoperation.md)
- [<span data-ttu-id="d2ce3-146">Wprowadzenie do interfejsu klasy</span><span class="sxs-lookup"><span data-stu-id="d2ce3-146">Introducing the class interface</span></span>](../../standard/native-interop/com-callable-wrapper.md#introducing-the-class-interface)
- [<span data-ttu-id="d2ce3-147">Zagadnienia dotyczące zabezpieczeń zestawów</span><span class="sxs-lookup"><span data-stu-id="d2ce3-147">Assembly Security Considerations</span></span>](../../standard/assembly/security-considerations.md)
- [<span data-ttu-id="d2ce3-148">Tlbexp. exe (Eksporter biblioteki typów)</span><span class="sxs-lookup"><span data-stu-id="d2ce3-148">Tlbexp.exe (Type Library Exporter)</span></span>](../tools/tlbexp-exe-type-library-exporter.md)
- [<span data-ttu-id="d2ce3-149">Rejestrowanie zestawów do użycia z modelem COM</span><span class="sxs-lookup"><span data-stu-id="d2ce3-149">Registering Assemblies with COM</span></span>](registering-assemblies-with-com.md)
- <span data-ttu-id="d2ce3-150">[Instrukcje: osadzanie bibliotek typów jako zasobów Win32 w aplikacjach](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d2ce3-150">[How to: Embed Type Libraries as Win32 Resources in Applications](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ww9a897z(v=vs.100))</span></span>
