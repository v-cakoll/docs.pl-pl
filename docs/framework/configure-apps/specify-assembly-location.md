---
title: Określanie lokalizacji zestawu
description: Zapoznaj się z tematem jak określić lokalizację zestawu w programie .NET przy użyciu elementu codeBase lub elementu do sondowania w pliku konfiguracyjnym XML.
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: e14bdc12598d0aa6cdd2789b09a04ab8ed134169
ms.sourcegitcommit: 6219b1e1feccb16d88656444210fed3297f5611e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2020
ms.locfileid: "85141707"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="95b0d-103">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="95b0d-103">Specifying an Assembly's Location</span></span>
<span data-ttu-id="95b0d-104">Istnieją dwa sposoby określania lokalizacji zestawu:</span><span class="sxs-lookup"><span data-stu-id="95b0d-104">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="95b0d-105">Przy użyciu [\<codeBase>](./file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="95b0d-105">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="95b0d-106">Przy użyciu [\<probing>](./file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="95b0d-106">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="95b0d-107">Można również użyć [Narzędzia konfiguracji .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) , aby określić lokalizacje zestawów lub określić lokalizacje dla środowiska uruchomieniowego języka wspólnego do sondowania dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="95b0d-107">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="95b0d-108">Korzystanie z \<codeBase> elementu</span><span class="sxs-lookup"><span data-stu-id="95b0d-108">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="95b0d-109">Można używać **\<codeBase>** elementu tylko w plikach konfiguracji komputera lub zasad wydawcy, które również przekierują wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="95b0d-109">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="95b0d-110">Gdy środowisko uruchomieniowe określa wersję zestawu, która ma być używana, stosuje ustawienia podstawowe kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="95b0d-110">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="95b0d-111">Jeśli nie wskazano żadnego kodu bazowego, sondy środowiska uruchomieniowego dla zestawu w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="95b0d-111">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="95b0d-112">Aby uzyskać szczegółowe informacje, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="95b0d-112">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="95b0d-113">Poniższy przykład pokazuje, jak określić lokalizację zestawu.</span><span class="sxs-lookup"><span data-stu-id="95b0d-113">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="95b0d-114">Atrybut **Version** jest wymagany dla wszystkich zestawów o silnych nazwach, ale powinien być pominięty dla zestawów, które nie mają silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="95b0d-114">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="95b0d-115">**\<codeBase>** Element wymaga atrybutu **href** .</span><span class="sxs-lookup"><span data-stu-id="95b0d-115">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="95b0d-116">Nie można określić zakresów wersji w **\<codeBase>** elemencie.</span><span class="sxs-lookup"><span data-stu-id="95b0d-116">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95b0d-117">Jeśli dostarczasz wskazówkę bazową kodu dla zestawu, który nie ma silnej nazwy, Wskazówka musi wskazywać na bazę aplikacji lub podkatalog katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95b0d-117">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="95b0d-118">Korzystanie z \<probing> elementu</span><span class="sxs-lookup"><span data-stu-id="95b0d-118">Using the \<probing> Element</span></span>  
 <span data-ttu-id="95b0d-119">Środowisko uruchomieniowe lokalizuje zestawy, które nie mają bazy kodu przy użyciu sondowania.</span><span class="sxs-lookup"><span data-stu-id="95b0d-119">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="95b0d-120">Aby uzyskać więcej informacji na temat sondowania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="95b0d-120">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="95b0d-121">Można użyć [\<probing>](./file-schema/runtime/probing-element.md) elementu w pliku konfiguracji aplikacji do określenia podkatalogów, które środowisko uruchomieniowe ma przeszukiwać podczas lokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="95b0d-121">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="95b0d-122">Poniższy przykład pokazuje, jak określić katalogi, które mają być wyszukiwane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="95b0d-122">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="95b0d-123">Atrybut **PrivatePath** zawiera katalogi, w których środowisko uruchomieniowe ma wyszukiwać zestawy.</span><span class="sxs-lookup"><span data-stu-id="95b0d-123">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="95b0d-124">Jeśli aplikacja znajduje się w katalogu C:\Program Files\MyApp, środowisko uruchomieniowe będzie szukać zestawów, które nie określają bazy kodu w folderze C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="95b0d-124">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="95b0d-125">Katalogi określone w **PrivatePath** muszą być podkatalogami katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="95b0d-125">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b0d-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95b0d-126">See also</span></span>

- [<span data-ttu-id="95b0d-127">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="95b0d-127">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="95b0d-128">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="95b0d-128">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="95b0d-129">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="95b0d-129">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="95b0d-130">Konfigurowanie aplikacji za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="95b0d-130">Configuring Apps by using Configuration Files</span></span>](index.md)
