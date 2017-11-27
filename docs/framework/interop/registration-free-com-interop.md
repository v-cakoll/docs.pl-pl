---
title: "Współdziałanie z modelem COM bez rejestrowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], interop
- COM interop, registration-free COM interop
- registration-free COM interop
- manifests [.NET Framework]
- registration-free activation
- object activation
- registration-free COM interop, about registration-free COM interop
ms.assetid: 90f308b9-82dc-414a-bce1-77e0155e56bd
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 28ecb3419bddcc8e9a192b240a7bf90474314c1f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="registration-free-com-interop"></a><span data-ttu-id="5ebca-102">Współdziałanie z modelem COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="5ebca-102">Registration-Free COM Interop</span></span>
<span data-ttu-id="5ebca-103">Współdziałanie z COM bez rejestrowania aktywuje składnika bez za pomocą rejestru systemu Windows do przechowywania informacji o zestawie.</span><span class="sxs-lookup"><span data-stu-id="5ebca-103">Registration-free COM interop activates a component without using the Windows registry to store assembly information.</span></span> <span data-ttu-id="5ebca-104">Zamiast zarejestrować składników na komputerze podczas wdrażania, można tworzyć pliki manifestu Win32 stylu w czasie projektowania, zawierających informacje o powiązaniu i aktywacji.</span><span class="sxs-lookup"><span data-stu-id="5ebca-104">Instead of registering a component on a computer during deployment, you create Win32-style manifest files at design time that contain information about binding and activation.</span></span> <span data-ttu-id="5ebca-105">Te pliki manifestu, zamiast klucze rejestru, bezpośrednie aktywacji obiektu.</span><span class="sxs-lookup"><span data-stu-id="5ebca-105">These manifest files, rather than registry keys, direct the activation of an object.</span></span>  
  
 <span data-ttu-id="5ebca-106">Przy użyciu aktywacji bez rejestracji dla ponownie zestawy zamiast zarejestrować ich podczas wdrażania oferuje dwie zalety:</span><span class="sxs-lookup"><span data-stu-id="5ebca-106">Using registration-free activation for your assemblies instead of registering them during deployment offers two advantages:</span></span>  
  
-   <span data-ttu-id="5ebca-107">Można kontrolować, która wersja biblioteki DLL jest aktywowany, gdy więcej niż jedna wersja jest zainstalowany na komputerze.</span><span class="sxs-lookup"><span data-stu-id="5ebca-107">You can control which DLL version is activated when more than one version is installed on a computer.</span></span>  
  
-   <span data-ttu-id="5ebca-108">Umożliwia użytkownikom XCOPY lub FTP można skopiować aplikacji do odpowiedniego katalogu na swoim komputerze.</span><span class="sxs-lookup"><span data-stu-id="5ebca-108">End users can use XCOPY or FTP to copy your application to an appropriate directory on their computer.</span></span> <span data-ttu-id="5ebca-109">Aplikacja może następnie uruchamiana z tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="5ebca-109">The application can then be run from that directory.</span></span>  
  
 <span data-ttu-id="5ebca-110">W tej sekcji opisano dwa typy manifestów potrzebne do międzyoperacyjności z modelem COM bez rejestrowania: manifestów aplikacji i składnika.</span><span class="sxs-lookup"><span data-stu-id="5ebca-110">This section describes the two types of manifests needed for registration-free COM interop: application and component manifests.</span></span> <span data-ttu-id="5ebca-111">Te manifesty są plikami XML.</span><span class="sxs-lookup"><span data-stu-id="5ebca-111">These manifests are XML files.</span></span> <span data-ttu-id="5ebca-112">Manifest aplikacji, który jest tworzony przez dewelopera aplikacji, zawiera metadane opisujące zestawów i zależności zestawu.</span><span class="sxs-lookup"><span data-stu-id="5ebca-112">An application manifest, which is created by an application developer, contains metadata that describes assemblies and assembly dependencies.</span></span> <span data-ttu-id="5ebca-113">Manifestu składnika, utworzonych przez dewelopera składnika zawiera informacje, w przeciwnym razie znajduje się w rejestrze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="5ebca-113">A component manifest, created by a component developer, contains information otherwise located in the Windows registry.</span></span>  
  
### <a name="requirements-for-registration-free-com-interop"></a><span data-ttu-id="5ebca-114">Wymagania dotyczące współdziałanie z COM bez rejestrowania</span><span class="sxs-lookup"><span data-stu-id="5ebca-114">Requirements for registration-free COM interop</span></span>  
  
1.  <span data-ttu-id="5ebca-115">Obsługa współdziałanie z COM bez rejestrowania różni się nieco w zależności od typu biblioteki zestawu; w szczególności czy zestaw jest niezarządzane (COM side-by-side) lub zarządzanych (. NET-based).</span><span class="sxs-lookup"><span data-stu-id="5ebca-115">Support for registration-free COM interop varies slightly depending on the type of library assembly; specifically, whether the assembly is unmanaged (COM side-by-side) or managed (.NET-based).</span></span> <span data-ttu-id="5ebca-116">W poniższej tabeli przedstawiono wymagania dotyczące wersji .NET Framework dla każdego typu zestawu i system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="5ebca-116">The following table shows the operating system and .NET Framework version requirements for each assembly type.</span></span>  
  
    |<span data-ttu-id="5ebca-117">Typ zestawu</span><span class="sxs-lookup"><span data-stu-id="5ebca-117">Assembly type</span></span>|<span data-ttu-id="5ebca-118">System operacyjny</span><span class="sxs-lookup"><span data-stu-id="5ebca-118">Operating system</span></span>|<span data-ttu-id="5ebca-119">Wersja programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5ebca-119">.NET Framework version</span></span>|  
    |-------------------|----------------------|----------------------------|  
    |<span data-ttu-id="5ebca-120">COM side-by-side</span><span class="sxs-lookup"><span data-stu-id="5ebca-120">COM side-by-side</span></span>|<span data-ttu-id="5ebca-121">Microsoft Windows XP</span><span class="sxs-lookup"><span data-stu-id="5ebca-121">Microsoft Windows XP</span></span>|<span data-ttu-id="5ebca-122">Nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="5ebca-122">Not required.</span></span>|  
    |<span data-ttu-id="5ebca-123">. Na podstawie NET</span><span class="sxs-lookup"><span data-stu-id="5ebca-123">.NET-based</span></span>|<span data-ttu-id="5ebca-124">Windows XP z dodatkiem SP2</span><span class="sxs-lookup"><span data-stu-id="5ebca-124">Windows XP with SP2</span></span>|<span data-ttu-id="5ebca-125">NET Framework w wersji 1.1 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="5ebca-125">NET Framework version 1.1 or later.</span></span>|  
  
     <span data-ttu-id="5ebca-126">System Windows Server 2003 obsługuje również współdziałanie COM bez rejestrowania dla. Zestawy opartych na sieci.</span><span class="sxs-lookup"><span data-stu-id="5ebca-126">The Windows Server 2003 family also supports registration-free COM interop for .NET-based assemblies.</span></span>  
  
     <span data-ttu-id="5ebca-127">Aby uzyskać. Oparte na sieci klasy, aby był zgodny z rejestru bez aktywacji z modelu COM, klasa musi mieć konstruktora domyślnego i muszą być publiczne.</span><span class="sxs-lookup"><span data-stu-id="5ebca-127">For a .NET-based class to be compatible with registry-free activation from COM, the class must have a default constructor and must be public.</span></span>  
  
### <a name="configuring-com-components-for-registration-free-activation"></a><span data-ttu-id="5ebca-128">Konfigurowanie aktywacji bez rejestracji składników COM</span><span class="sxs-lookup"><span data-stu-id="5ebca-128">Configuring COM components for registration-free activation</span></span>  
  
1.  <span data-ttu-id="5ebca-129">Dla składnika modelu COM o uczestnictwie w aktywacji bez rejestracji musi być wdrożony jako zestawu side-by-side.</span><span class="sxs-lookup"><span data-stu-id="5ebca-129">For a COM component to participate in registration-free activation, it must be deployed as a side-by-side assembly.</span></span> <span data-ttu-id="5ebca-130">Zestawy Side-by-side są niezarządzane zestawów.</span><span class="sxs-lookup"><span data-stu-id="5ebca-130">Side-by-side assemblies are unmanaged assemblies.</span></span>  <span data-ttu-id="5ebca-131">Aby uzyskać więcej informacji, zobacz [używanie zestawów Side-by-side](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ebca-131">For more information, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
     <span data-ttu-id="5ebca-132">Używanie zestawów side-by-side COM,. Deweloper aplikacji opartych na sieci należy podać manifest aplikacji, który zawiera informacje o powiązaniu i aktywacji.</span><span class="sxs-lookup"><span data-stu-id="5ebca-132">To use COM side-by-side assemblies, a .NET-based application developer must provide an application manifest, which contains the binding and activation information.</span></span> <span data-ttu-id="5ebca-133">Obsługa niezarządzane zestawy side-by-side jest wbudowane w system operacyjny Windows XP.</span><span class="sxs-lookup"><span data-stu-id="5ebca-133">Support for unmanaged side-by-side assemblies is built into the Windows XP operating system.</span></span> <span data-ttu-id="5ebca-134">COM środowiska uruchomieniowego, obsługiwane przez system operacyjny skanuje manifest aplikacji, aby uzyskać informacje dotyczące aktywacji, gdy składnik aktywowane nie jest w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="5ebca-134">The COM runtime, supported by the operating system, scans an application manifest for activation information when the component being activated is not in the registry.</span></span>  
  
     <span data-ttu-id="5ebca-135">Aktywacja bez rejestrowania jest opcjonalne dla składników modelu COM w systemie Windows XP.</span><span class="sxs-lookup"><span data-stu-id="5ebca-135">Registration-free activation is optional for COM components installed on Windows XP.</span></span> <span data-ttu-id="5ebca-136">Aby uzyskać szczegółowe instrukcje dotyczące dodawania zestawu side-by-side do aplikacji, zobacz [używanie zestawów Side-by-side](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span><span class="sxs-lookup"><span data-stu-id="5ebca-136">For detailed instructions on adding a side-by-side assembly to an application, see [Using Side-by-side Assemblies](https://msdn.microsoft.com/library/windows/desktop/aa376618.aspx).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ebca-137">Wykonanie Side-by-side jest funkcja .NET Framework, która umożliwia wielu wersji środowiska uruchomieniowego i wiele wersji aplikacji i składników, których używana jest wersja środowiska uruchomieniowego, do uruchamiania na tym samym komputerze, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="5ebca-137">Side-by-side execution is a .NET Framework feature that enables multiple versions of the runtime, and multiple versions of applications and components that use a version of the runtime, to run on the same computer at the same time.</span></span> <span data-ttu-id="5ebca-138">Wykonanie Side-by-side i zestawy side-by-side są różne mechanizmy dostarczanie side-by-side funkcji.</span><span class="sxs-lookup"><span data-stu-id="5ebca-138">Side-by-side execution and side-by-side assemblies are different mechanisms for providing side-by-side functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ebca-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ebca-139">See Also</span></span>  
 [<span data-ttu-id="5ebca-140">Porady: Konfigurowanie aktywacji bez rejestracji składników COM opartych na Framework .NET</span><span class="sxs-lookup"><span data-stu-id="5ebca-140">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>](../../../docs/framework/interop/configure-net-framework-based-com-components-for-reg.md)
