---
title: Określanie lokalizacji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: 43cd1d0edbb607f69f27661aae3372e93564b3b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932335"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="a6db7-102">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="a6db7-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="a6db7-103">Istnieją dwa sposoby określania lokalizacji zestawu:</span><span class="sxs-lookup"><span data-stu-id="a6db7-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="a6db7-104">Używanie bazowej [ >elementu.\<](./file-schema/runtime/codebase-element.md)</span><span class="sxs-lookup"><span data-stu-id="a6db7-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="a6db7-105">Korzystanie z [ \<elementu > sondowania](./file-schema/runtime/probing-element.md) .</span><span class="sxs-lookup"><span data-stu-id="a6db7-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="a6db7-106">Można również użyć [Narzędzia konfiguracji .NET Framework (Mscorcfg. msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) , aby określić lokalizacje zestawów lub określić lokalizacje dla środowiska uruchomieniowego języka wspólnego do sondowania dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="a6db7-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="a6db7-107">\<Używanie bazowej > elementu</span><span class="sxs-lookup"><span data-stu-id="a6db7-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="a6db7-108">Można użyć  **\<bazowej >** elementu tylko w pliku konfiguracji komputera lub zasad wydawcy, który również przekieruje wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="a6db7-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="a6db7-109">Gdy środowisko uruchomieniowe określa wersję zestawu, która ma być używana, stosuje ustawienia podstawowe kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="a6db7-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="a6db7-110">Jeśli nie wskazano żadnego kodu bazowego, sondy środowiska uruchomieniowego dla zestawu w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="a6db7-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="a6db7-111">Aby uzyskać szczegółowe informacje, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a6db7-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a6db7-112">Poniższy przykład pokazuje, jak określić lokalizację zestawu.</span><span class="sxs-lookup"><span data-stu-id="a6db7-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="a6db7-113">Atrybut **Version** jest wymagany dla wszystkich zestawów o silnych nazwach, ale powinien być pominięty dla zestawów, które nie mają silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="a6db7-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="a6db7-114">**\<CodeBase>** element wymaga **href** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a6db7-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="a6db7-115">Nie można określić zakresów wersji w  **\<ścieżce bazowej >** elementu.</span><span class="sxs-lookup"><span data-stu-id="a6db7-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a6db7-116">Jeśli dostarczasz wskazówkę bazową kodu dla zestawu, który nie ma silnej nazwy, Wskazówka musi wskazywać na bazę aplikacji lub podkatalog katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6db7-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="a6db7-117">\<Używanie elementu > sondowania</span><span class="sxs-lookup"><span data-stu-id="a6db7-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="a6db7-118">Środowisko uruchomieniowe lokalizuje zestawy, które nie mają bazy kodu przy użyciu sondowania.</span><span class="sxs-lookup"><span data-stu-id="a6db7-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="a6db7-119">Aby uzyskać więcej informacji na temat sondowania, zobacz [jak środowisko uruchomieniowe lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a6db7-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="a6db7-120">Można użyć [ \<elementu > sondowania](./file-schema/runtime/probing-element.md) w pliku konfiguracyjnym aplikacji, aby określić podkatalogi, które środowisko uruchomieniowe ma przeszukiwać podczas lokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="a6db7-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="a6db7-121">Poniższy przykład pokazuje, jak określić katalogi, które mają być wyszukiwane przez środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="a6db7-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="a6db7-122">Atrybut **PrivatePath** zawiera katalogi, w których środowisko uruchomieniowe ma wyszukiwać zestawy.</span><span class="sxs-lookup"><span data-stu-id="a6db7-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="a6db7-123">Jeśli aplikacja znajduje się w katalogu C:\Program Files\MyApp, środowisko uruchomieniowe będzie szukać zestawów, które nie określają bazy kodu w folderze C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="a6db7-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="a6db7-124">Katalogi określone w **PrivatePath** muszą być podkatalogami katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6db7-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6db7-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a6db7-125">See also</span></span>

- [<span data-ttu-id="a6db7-126">Zestawy w środowisku uruchomieniowym CLR</span><span class="sxs-lookup"><span data-stu-id="a6db7-126">Assemblies in the Common Language Runtime</span></span>](../app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="a6db7-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="a6db7-127">Programming with Assemblies</span></span>](../app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="a6db7-128">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a6db7-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a6db7-129">Konfigurowanie aplikacji przy użyciu plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="a6db7-129">Configuring Apps by using Configuration Files</span></span>](index.md)
