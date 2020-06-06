---
title: 'Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
ms.openlocfilehash: 6fa864f814d6a9ce04f2bce92c61cd0075ab5145
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "69913001"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="2512a-102">Instrukcje: Lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="2512a-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="2512a-103">Deweloperzy mogą chcieć upewnić się, że kompiluje się zestaw współużytkowany działa prawidłowo z wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="2512a-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="2512a-104">Zamiast ciągłego umieszczania zestawu w globalnej pamięci podręcznej zestawów podczas cyklu projektowania, deweloper może utworzyć zmienną środowiskową DEVPATH, która wskazuje katalog wyjściowy kompilacji dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="2512a-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="2512a-105">Załóżmy na przykład, że tworzysz zestaw współużytkowany o nazwie MySharedAssembly, a katalog wyjściowy to C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="2512a-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="2512a-106">Możesz umieścić C:\MySharedAssembly\Debug w zmiennej DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2512a-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="2512a-107">Następnie należy określić [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="2512a-107">You must then specify the [\<developmentMode>](./file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="2512a-108">Ten element zawiera informacje o tym, że środowisko uruchomieniowe języka wspólnego używa DEVPATH do lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="2512a-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="2512a-109">Zestaw współużytkowany musi być wykrywalny przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="2512a-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="2512a-110">Aby określić katalog prywatny do rozpoznawania odwołań do zestawów, użyj [ \<codeBase> elementu](./file-schema/runtime/codebase-element.md) lub [ \<probing> elementu](./file-schema/runtime/probing-element.md) w pliku konfiguracji, zgodnie z opisem w temacie [Określanie lokalizacji zestawu](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="2512a-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](./file-schema/runtime/codebase-element.md) or [\<probing> Element](./file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>  <span data-ttu-id="2512a-111">Możesz również umieścić zestaw w podkatalogu katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2512a-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="2512a-112">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="2512a-112">For more information, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2512a-113">Jest to zaawansowana funkcja przeznaczona tylko do programowania.</span><span class="sxs-lookup"><span data-stu-id="2512a-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="2512a-114">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe wyszukuje zestawy w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2512a-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2512a-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="2512a-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="2512a-116">To ustawienie domyślnie ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="2512a-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2512a-117">Tego ustawienia należy używać tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="2512a-117">Use this setting only at development time.</span></span> <span data-ttu-id="2512a-118">Środowisko uruchomieniowe nie sprawdza wersji w zestawach o silnej nazwie znalezionych w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="2512a-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="2512a-119">Po prostu używa pierwszego zestawu, który znajdzie.</span><span class="sxs-lookup"><span data-stu-id="2512a-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2512a-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2512a-120">See also</span></span>

- [<span data-ttu-id="2512a-121">Konfigurowanie aplikacji za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2512a-121">Configuring Apps by using Configuration Files</span></span>](index.md)
