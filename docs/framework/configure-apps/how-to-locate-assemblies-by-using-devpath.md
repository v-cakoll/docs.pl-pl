---
title: 'Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH'
description: Sprawdź, czy zestaw współużytkowany działa prawidłowo z wieloma aplikacjami w programie .NET przy użyciu pliku konfiguracji komputera XML i zmiennej środowiskowej DEVPATH.
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 50b61eedddabd660b1834565a61738f460ae9ff9
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105380"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="0eb2f-103">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="0eb2f-103">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="0eb2f-104">Deweloperzy mogą chcieć upewnić się, że kompiluje się zestaw współużytkowany działa prawidłowo z wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-104">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="0eb2f-105">Zamiast ciągłego umieszczania zestawu w globalnej pamięci podręcznej zestawów podczas cyklu projektowania, deweloper może utworzyć zmienną środowiskową DEVPATH, która wskazuje katalog wyjściowy kompilacji dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-105">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="0eb2f-106">Załóżmy na przykład, że tworzysz zestaw współużytkowany o nazwie MySharedAssembly, a katalog wyjściowy to C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-106">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="0eb2f-107">Możesz umieścić C:\MySharedAssembly\Debug w zmiennej DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-107">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="0eb2f-108">Następnie należy określić [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-108">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="0eb2f-109">Ten element zawiera informacje o tym, że środowisko uruchomieniowe języka wspólnego używa DEVPATH do lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-109">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="0eb2f-110">Zestaw współużytkowany musi być wykrywalny przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-110">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="0eb2f-111">Aby określić katalog prywatny do rozpoznawania odwołań do zestawów, użyj [ \<codeBase> elementu](./file-schema/runtime/codebase-element.md) lub [ \<probing> elementu](./file-schema/runtime/probing-element.md) w pliku konfiguracji, zgodnie z opisem w temacie [Określanie lokalizacji zestawu](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="0eb2f-111">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="0eb2f-112">Możesz również umieścić zestaw w podkatalogu katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-112">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="0eb2f-113">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="0eb2f-113">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0eb2f-114">Jest to zaawansowana funkcja przeznaczona tylko do programowania.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-114">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="0eb2f-115">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-115">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0eb2f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="0eb2f-116">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="0eb2f-117">To ustawienie domyślnie ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-117">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0eb2f-118">Tego ustawienia należy używać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-118">Use this setting only at development time.</span></span> <span data-ttu-id="0eb2f-119">Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-119">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="0eb2f-120">Po prostu używa pierwszego zestawu, który znajdzie.</span><span class="sxs-lookup"><span data-stu-id="0eb2f-120">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb2f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0eb2f-121">See also</span></span>

- [<span data-ttu-id="0eb2f-122">Konfigurowanie aplikacji za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="0eb2f-122">Configuring Apps by using Configuration Files</span></span>](index.md)
