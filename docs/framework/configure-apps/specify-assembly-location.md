---
title: Określanie zestawu&#39;lokalizacji s
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 8fedec60b6152e77d6f99bf55cf11ec909fa8f80
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47083718"
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="f5a1d-102">Określanie zestawu&#39;lokalizacji s</span><span class="sxs-lookup"><span data-stu-id="f5a1d-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="f5a1d-103">Istnieją dwa sposoby, aby określić lokalizację zestawu:</span><span class="sxs-lookup"><span data-stu-id="f5a1d-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="f5a1d-104">Za pomocą [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="f5a1d-105">Za pomocą [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="f5a1d-106">Można również użyć [narzędzia .NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) Aby określić inną lokalizację zestawu lub określić inną lokalizację dla środowiska uruchomieniowego języka wspólnego sondowania dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://msdn.microsoft.com/library/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="f5a1d-107">Za pomocą \<codeBase > Element</span><span class="sxs-lookup"><span data-stu-id="f5a1d-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="f5a1d-108">Możesz użyć  **\<codeBase >** elementu tylko w konfiguracji lub wydawcy zasad plików maszyny, które również przekierowanie wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="f5a1d-109">Środowisko wykonawcze określa, jakiego zestawu należy użyć, stosuje się ustawienie baza kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="f5a1d-110">Jeśli nie baza kodu jest zaznaczone, środowisko uruchomieniowe sondy dla zestawu w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="f5a1d-111">Aby uzyskać więcej informacji, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f5a1d-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="f5a1d-112">Poniższy przykład pokazuje sposób określania lokalizacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-112">The following example shows how to specify an assembly's location.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <codeBase version="2.0.0.0"  
                   href="http://www.litwareinc.com/myAssembly.dll"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f5a1d-113">**Wersji** atrybut jest wymagany dla wszystkich zestawów o silnej nazwie, ale należy pominąć dla zestawów, które są nie o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="f5a1d-114">**\<CodeBase >** element wymaga **href** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="f5a1d-115">Nie można określić wersji zakresów w  **\<codeBase >** elementu.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5a1d-116">Jeśli są podawania wskazówką podstawowego kodu dla zestawu, który nie jest, o silnych nazwach, wskazówka musi wskazywać podstawy aplikacji lub podkatalogiem katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="f5a1d-117">Za pomocą \<sondowanie > Element</span><span class="sxs-lookup"><span data-stu-id="f5a1d-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="f5a1d-118">Środowisko uruchomieniowe lokalizuje zestawy, które nie mają kodu bazowego sondowanie.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="f5a1d-119">Aby uzyskać więcej informacji na temat badania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="f5a1d-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="f5a1d-120">Możesz użyć [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu w pliku konfiguracyjnym aplikacji, aby określić środowisko uruchomieniowe ma poszukiwać podczas lokalizowania zestawu podkatalogów.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="f5a1d-121">Poniższy przykład pokazuje, jak można określić katalogi, których środowisko uruchomieniowe ma wyszukiwać.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="f5a1d-122">**PrivatePath** atrybut zawiera katalogi, które środowisko wykonawcze powinno poszukać zestawów.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="f5a1d-123">Jeśli aplikacja znajduje się w lokalizacji C:\Program Files\MyApp, środowisko uruchomieniowe będzie szukać zestawów, które nie określisz bazy kodu w C:\Program Files\MyApp\Bin C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="f5a1d-124">Katalogi określone w **privatePath** musi być podkatalogi katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f5a1d-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5a1d-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f5a1d-125">See Also</span></span>  
 [<span data-ttu-id="f5a1d-126">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="f5a1d-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="f5a1d-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="f5a1d-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="f5a1d-128">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="f5a1d-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="f5a1d-129">Konfigurowanie aplikacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f5a1d-129">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
