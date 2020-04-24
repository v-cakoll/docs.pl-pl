---
title: Określanie lokalizacji zestawu
ms.date: 03/30/2017
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
ms.openlocfilehash: ead69d1e850050214c15295134c06ff6f66e9760
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646029"
---
# <a name="specifying-an-assemblys-location"></a><span data-ttu-id="b35de-102">Określanie lokalizacji zestawu</span><span class="sxs-lookup"><span data-stu-id="b35de-102">Specifying an Assembly's Location</span></span>
<span data-ttu-id="b35de-103">Istnieją dwa sposoby określania lokalizacji zestawu:</span><span class="sxs-lookup"><span data-stu-id="b35de-103">There are two ways to specify an assembly's location:</span></span>  
  
- <span data-ttu-id="b35de-104">Za pomocą [ \<codeBase>](./file-schema/runtime/codebase-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b35de-104">Using the [\<codeBase>](./file-schema/runtime/codebase-element.md) element.</span></span>  
  
- <span data-ttu-id="b35de-105">Za pomocą [ \<sondowania>](./file-schema/runtime/probing-element.md) element.</span><span class="sxs-lookup"><span data-stu-id="b35de-105">Using the [\<probing>](./file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="b35de-106">Narzędzia [konfiguracji programu .NET Framework Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) można również użyć do określenia lokalizacji zestawu lub określenia lokalizacji środowiska wykonawczego języka wspólnego do sondowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="b35de-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/2bc0cxhc(v=vs.100)) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="b35de-107">Korzystanie \<z elementu codeBase></span><span class="sxs-lookup"><span data-stu-id="b35de-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="b35de-108">Można użyć \*\* \<codeBase>\*\* element tylko w konfiguracji komputera lub plików zasad wydawcy, które również przekierowywać wersję zestawu.</span><span class="sxs-lookup"><span data-stu-id="b35de-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="b35de-109">Gdy środowisko wykonawcze określa, która wersja zestawu do użycia, stosuje ustawienie podstawowe kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="b35de-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="b35de-110">Jeśli nie ma podstawy kodu, sondy środowiska wykonawczego dla zestawu w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="b35de-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="b35de-111">Aby uzyskać szczegółowe informacje, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b35de-111">For details, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="b35de-112">W poniższym przykładzie pokazano, jak określić lokalizację zestawu.</span><span class="sxs-lookup"><span data-stu-id="b35de-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="b35de-113">Atrybut **wersji** jest wymagany dla wszystkich zestawów o silnej nazwie, ale należy go pominąć w przypadku zestawów, które nie mają silnej nazwy.</span><span class="sxs-lookup"><span data-stu-id="b35de-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="b35de-114">Element \*\* \<codeBase>\*\* wymaga atrybutu **href.**</span><span class="sxs-lookup"><span data-stu-id="b35de-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="b35de-115">Nie można określić zakresów wersji w \*\* \<elemencie codeBase>.\*\*</span><span class="sxs-lookup"><span data-stu-id="b35de-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b35de-116">Jeśli dostarczasz wskazówkę podstawową kodu dla zestawu, który nie ma silnej nazwy, wskazówka musi wskazywać na bazę aplikacji lub podkatalog katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b35de-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="b35de-117">Korzystanie \<z elementu> sondowania</span><span class="sxs-lookup"><span data-stu-id="b35de-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="b35de-118">Środowisko wykonawcze lokalizuje zestawy, które nie mają podstawy kodu przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="b35de-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="b35de-119">Aby uzyskać więcej informacji na temat sondowania, zobacz [Jak środowisko wykonawcze lokalizuje zestawy](../deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="b35de-119">For more information about probing, see [How the Runtime Locates Assemblies](../deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="b35de-120">Można użyć [ \<sondowania>](./file-schema/runtime/probing-element.md) element w pliku konfiguracji aplikacji, aby określić podkatalogów środowiska wykonawczego należy szukać podczas lokalizowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="b35de-120">You can use the [\<probing>](./file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="b35de-121">W poniższym przykładzie pokazano, jak określić katalogi, które należy przeszukać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b35de-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="b35de-122">Atrybut **privatePath** zawiera katalogi, które środowisko wykonawcze powinno wyszukiwać zestawy.</span><span class="sxs-lookup"><span data-stu-id="b35de-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="b35de-123">Jeśli aplikacja znajduje się w folderze C:\Program Files\MyApp, środowisko wykonawcze będzie szukać zestawów, które nie określają bazy kodu w folderze C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3.</span><span class="sxs-lookup"><span data-stu-id="b35de-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="b35de-124">Katalogi określone w **privatePath** muszą być podkatalogami katalogu podstawowego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b35de-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b35de-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b35de-125">See also</span></span>

- [<span data-ttu-id="b35de-126">Zestawy w środowisku .NET</span><span class="sxs-lookup"><span data-stu-id="b35de-126">Assemblies in .NET</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="b35de-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="b35de-127">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="b35de-128">Sposoby lokalizowania zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b35de-128">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="b35de-129">Konfigurowanie aplikacji za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b35de-129">Configuring Apps by using Configuration Files</span></span>](index.md)
