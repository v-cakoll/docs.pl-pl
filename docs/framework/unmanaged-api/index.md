---
title: Niezarządzany wykaz interfejsów API
ms.date: 11/06/2017
helpviewer_keywords:
- runtime, unmanaged APIs
- common language runtime, unmanaged APIs
- native API reference [.NET Framework]
- unmanaged API reference [.NET Framework]
ms.assetid: 9aa000ee-c04c-492c-ae4f-83ecdf4fdbbe
ms.openlocfilehash: f7dd78b889129998dee31a22f5dd23325613b8ea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092024"
---
# <a name="unmanaged-api-reference"></a><span data-ttu-id="41652-102">Niezarządzany wykaz interfejsów API</span><span class="sxs-lookup"><span data-stu-id="41652-102">Unmanaged API Reference</span></span>
<span data-ttu-id="41652-103">Ta sekcja zawiera informacje dotyczące niezarządzanych interfejsów API, które mogą być używane przez aplikacje związane z kodem zarządzanym, takie jak hosty środowiska uruchomieniowego, kompilatory, deasemblery, elementy zasłaniające, debugery i pliki.</span><span class="sxs-lookup"><span data-stu-id="41652-103">This section includes information on unmanaged APIs that can be used by managed-code-related applications, such as runtime hosts, compilers, disassemblers, obfuscators, debuggers, and profilers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="41652-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="41652-104">In This Section</span></span>  
 [<span data-ttu-id="41652-105">Standardowe typy danych</span><span class="sxs-lookup"><span data-stu-id="41652-105">Common Data Types</span></span>](common-data-types-unmanaged-api-reference.md)  
 <span data-ttu-id="41652-106">Wyświetla listę typowych typów danych, które są używane, szczególnie w niezarządzanych interfejsy API profilowania i debugowania.</span><span class="sxs-lookup"><span data-stu-id="41652-106">Lists the common data types that are used, particularly in the unmanaged profiling and debugging APIs.</span></span>  
  
 [<span data-ttu-id="41652-107">ALink</span><span class="sxs-lookup"><span data-stu-id="41652-107">ALink</span></span>](./alink/index.md)  
 <span data-ttu-id="41652-108">Opisuje interfejs API ALink, który obsługuje tworzenie zestawów .NET Framework i niezwiązanych modułów.</span><span class="sxs-lookup"><span data-stu-id="41652-108">Describes the ALink API, which supports the creation of .NET Framework assemblies and unbound modules.</span></span>  
  
 [<span data-ttu-id="41652-109">Authenticode</span><span class="sxs-lookup"><span data-stu-id="41652-109">Authenticode</span></span>](./authenticode/index.md)  
 <span data-ttu-id="41652-110">Obsługuje moduł tworzenia i weryfikacji licencji XrML Authenticode.</span><span class="sxs-lookup"><span data-stu-id="41652-110">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
 [<span data-ttu-id="41652-111">Stałe</span><span class="sxs-lookup"><span data-stu-id="41652-111">Constants</span></span>](constants-unmanaged-api-reference.md)  
 <span data-ttu-id="41652-112">Opisuje stałe, które są zdefiniowane w CorSym. idl.</span><span class="sxs-lookup"><span data-stu-id="41652-112">Describes the constants that are defined in CorSym.idl.</span></span>  
  
 <span data-ttu-id="41652-113">[Niestandardowe atrybuty interfejsu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="41652-113">[Custom Interface Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms231946(v=vs.100))</span></span>  
 <span data-ttu-id="41652-114">Opisuje atrybuty niestandardowego interfejsu COM (Component Object Model).</span><span class="sxs-lookup"><span data-stu-id="41652-114">Describes component object model (COM) custom interface attributes.</span></span>  
  
 [<span data-ttu-id="41652-115">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="41652-115">Debugging</span></span>](./debugging/index.md)  
 <span data-ttu-id="41652-116">Opisuje interfejs API debugowania, który umożliwia debugerowi Debugowanie kodu, który jest uruchamiany w środowisku środowiska uruchomieniowego języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="41652-116">Describes the debugging API, which enables a debugger to debug code that runs in the common language runtime (CLR) environment.</span></span>  
  
 [<span data-ttu-id="41652-117">Magazyn symboli diagnostycznych</span><span class="sxs-lookup"><span data-stu-id="41652-117">Diagnostics Symbol Store</span></span>](./diagnostics/index.md)  
 <span data-ttu-id="41652-118">Opisuje interfejs API magazynu symboli diagnostyki, który umożliwia kompilatorowi generowanie informacji o symbolach do użycia przez debuger.</span><span class="sxs-lookup"><span data-stu-id="41652-118">Describes the diagnostics symbol store API, which enables a compiler to generate symbol information for use by a debugger.</span></span>  
  
 [<span data-ttu-id="41652-119">Łączenie</span><span class="sxs-lookup"><span data-stu-id="41652-119">Fusion</span></span>](./fusion/index.md)  
 <span data-ttu-id="41652-120">Opisuje interfejs API Fusion, który umożliwia hostowi środowiska uruchomieniowego dostęp do właściwości zasobów aplikacji w celu zlokalizowania odpowiednich wersji tych zasobów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41652-120">Describes the fusion API, which enables a runtime host to access the properties of an application's resources in order to locate the correct versions of those resources for the application.</span></span>  
  
 [<span data-ttu-id="41652-121">Hosting</span><span class="sxs-lookup"><span data-stu-id="41652-121">Hosting</span></span>](./hosting/index.md)  
 <span data-ttu-id="41652-122">Opisuje interfejs API hostingu, który umożliwia niezarządzanym hostom integrację środowiska CLR z aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="41652-122">Describes the hosting API, which enables unmanaged hosts to integrate the CLR into their applications.</span></span>  
  
 [<span data-ttu-id="41652-123">Metadane</span><span class="sxs-lookup"><span data-stu-id="41652-123">Metadata</span></span>](./metadata/index.md)  
 <span data-ttu-id="41652-124">Opisuje interfejs API metadanych, który umożliwia klientowi, takim jak kompilator, generowanie metadanych składnika lub uzyskiwanie do nich dostępu bez typów ładowanych przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="41652-124">Describes the metadata API, which enables a client such as a compiler to generate or access a component's metadata without the types being loaded by the CLR.</span></span>  
  
 [<span data-ttu-id="41652-125">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="41652-125">Profiling</span></span>](./profiling/index.md)  
 <span data-ttu-id="41652-126">Opisuje Profiling API, który umożliwia profilerowi monitorowanie wykonywania programu przez środowisko CLR.</span><span class="sxs-lookup"><span data-stu-id="41652-126">Describes the profiling API, which enables a profiler to monitor a program's execution by the CLR.</span></span>  
  
 [<span data-ttu-id="41652-127">Silne nazewnictwo</span><span class="sxs-lookup"><span data-stu-id="41652-127">Strong Naming</span></span>](./strong-naming/index.md)  
 <span data-ttu-id="41652-128">Opisuje interfejs API silnego nazewnictwa, który umożliwia klientowi administrowanie podpisywaniem silnych nazw dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="41652-128">Describes the strong naming API, which enables a client to administer strong name signing for assemblies.</span></span>  

 [<span data-ttu-id="41652-129">Usługi WMI i liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="41652-129">WMI and Performance Counters</span></span>](wmi/index.md)  
 <span data-ttu-id="41652-130">Opisuje interfejsy API, które zawijają wywołania do bibliotek Instrumentacja zarządzania Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="41652-130">Describes the APIs that wrap calls to Windows Management Instrumentation (WMI) libraries.</span></span>
  
 [<span data-ttu-id="41652-131">Tlbexp, funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="41652-131">Tlbexp Helper Functions</span></span>](./tlbexp/index.md)  
 <span data-ttu-id="41652-132">Opisuje dwie funkcje pomocnika i interfejs używany przez eksportera biblioteki typów (Tlbexp. exe) podczas procesu konwersji zestawu na typ biblioteki.</span><span class="sxs-lookup"><span data-stu-id="41652-132">Describes the two helper functions and interface used by the Type Library Exporter (Tlbexp.exe) during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="41652-133">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="41652-133">Related Sections</span></span>  
 [<span data-ttu-id="41652-134">Podręcznik programowania</span><span class="sxs-lookup"><span data-stu-id="41652-134">Development Guide</span></span>](../../../docs/framework/development-guide.md)  
