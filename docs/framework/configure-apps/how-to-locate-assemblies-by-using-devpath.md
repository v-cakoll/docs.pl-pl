---
title: 'Porady: lokalizowanie zestawów za pomocą DEVPATH'
ms.date: 03/30/2017
helpviewer_keywords:
- DEVPATH
- .NET Framework application configuration, assemblies
- application configuration files, specifying assembly's location
- app.config files, assembly locations
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 44d2eadf-7eec-443c-a2ac-d601fd919e17
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 3a9ae9c60ad7de80d04f16984b3b2fb048421cc2
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037329"
---
# <a name="how-to-locate-assemblies-by-using-devpath"></a><span data-ttu-id="437c1-102">Porady: lokalizowanie zestawów za pomocą DEVPATH</span><span class="sxs-lookup"><span data-stu-id="437c1-102">How to: Locate Assemblies by Using DEVPATH</span></span>
<span data-ttu-id="437c1-103">Deweloperzy mogą chcą upewnij się, że zestaw współużytkowany, które trwają prace działa poprawnie z wieloma aplikacjami.</span><span class="sxs-lookup"><span data-stu-id="437c1-103">Developers might want to make sure that a shared assembly they are building works correctly with multiple applications.</span></span> <span data-ttu-id="437c1-104">Zamiast ciągle umieszczenie zestawu w globalnej pamięci podręcznej podczas cyklu rozwoju, deweloper można utworzyć zmiennej środowiskowej DEVPATH, który wskazuje na katalog wyjściowy kompilacji dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="437c1-104">Instead of continually putting the assembly in the global assembly cache during the development cycle, the developer can create a DEVPATH environment variable that points to the build output directory for the assembly.</span></span>  
  
 <span data-ttu-id="437c1-105">Załóżmy na przykład, który jest kompilowany zestaw współużytkowany o nazwie MySharedAssembly i katalog wyjściowy jest C:\MySharedAssembly\Debug.</span><span class="sxs-lookup"><span data-stu-id="437c1-105">For example, assume that you are building a shared assembly called MySharedAssembly and the output directory is C:\MySharedAssembly\Debug.</span></span> <span data-ttu-id="437c1-106">C:\MySharedAssembly\Debug można umieścić w zmiennej DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="437c1-106">You can put C:\MySharedAssembly\Debug in the DEVPATH variable.</span></span> <span data-ttu-id="437c1-107">Następnie należy określić [ \<developmentmode — >](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) elementu w pliku konfiguracji komputera.</span><span class="sxs-lookup"><span data-stu-id="437c1-107">You must then specify the [\<developmentMode>](../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md) element in the machine configuration file.</span></span> <span data-ttu-id="437c1-108">Środowisko uruchomieniowe języka wspólnego lokalizowanie zestawów za pomocą DEVPATH zawiera informacje dla tego elementu.</span><span class="sxs-lookup"><span data-stu-id="437c1-108">This element tells the common language runtime to use DEVPATH to locate assemblies.</span></span>  
  
 <span data-ttu-id="437c1-109">Zestaw współużytkowany musi być wykrywalny przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="437c1-109">The shared assembly must be discoverable by the runtime.</span></span>  <span data-ttu-id="437c1-110">Aby określić katalog prywatnej rozpoznawania zestawu odwołania do użycia [ \<codeBase > Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) lub [ \<sondowanie > Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) w pliku konfiguracji, zgodnie z opisem w [Określanie lokalizacji zestawu](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="437c1-110">To specify a private directory for resolving assembly references use the [\<codeBase> Element](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) or [\<probing> Element](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) in a configuration file, as described in [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  <span data-ttu-id="437c1-111">Możesz również umieścić zestaw w podkatalogu katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="437c1-111">You can also put the assembly in a subdirectory of the application directory.</span></span> <span data-ttu-id="437c1-112">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="437c1-112">For more information, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="437c1-113">Jest to zaawansowana funkcja przeznaczonych tylko w celach deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="437c1-113">This is an advanced feature, intended only for development.</span></span>  
  
 <span data-ttu-id="437c1-114">Poniższy przykład pokazuje, jak spowodować, że środowisko uruchomieniowe do przeszukania pod kątem zestawów w katalogach określonych przez zmienną środowiskową DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="437c1-114">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="437c1-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="437c1-115">Example</span></span>  
  
```xml  
<configuration>  
  <runtime>  
    <developmentMode developerInstallation="true"/>  
  </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="437c1-116">To ustawienie, wartość domyślna to false.</span><span class="sxs-lookup"><span data-stu-id="437c1-116">This setting defaults to false.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="437c1-117">Użyj tego ustawienia w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="437c1-117">Use this setting only at development time.</span></span> <span data-ttu-id="437c1-118">Środowisko wykonawcze nie sprawdza obecności wersje zestawów o silnych nazwach, znaleziono w DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="437c1-118">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="437c1-119">Po prostu używa pierwszego zestawu, który odnajdzie.</span><span class="sxs-lookup"><span data-stu-id="437c1-119">It simply uses the first assembly it finds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="437c1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="437c1-120">See Also</span></span>  
 [<span data-ttu-id="437c1-121">Konfigurowanie aplikacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="437c1-121">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
