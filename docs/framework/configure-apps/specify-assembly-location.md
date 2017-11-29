---
title: "Określenie zestawu &#39; s lokalizacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration [.NET Framework], applications
- application configuration [.NET Framework]
- assemblies [.NET Framework], specifying location
ms.assetid: 1cb92bd7-6bab-44cf-8fd3-36303ce84fea
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f747d921e9c131edaa8a1749c5adc5eae14623c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="specifying-an-assembly39s-location"></a><span data-ttu-id="9162c-102">Określenie zestawu &#39; s lokalizacji</span><span class="sxs-lookup"><span data-stu-id="9162c-102">Specifying an Assembly&#39;s Location</span></span>
<span data-ttu-id="9162c-103">Istnieją dwa sposoby, aby określić lokalizację zestawu:</span><span class="sxs-lookup"><span data-stu-id="9162c-103">There are two ways to specify an assembly's location:</span></span>  
  
-   <span data-ttu-id="9162c-104">Przy użyciu [ \<codeBase >](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9162c-104">Using the [\<codeBase>](../../../docs/framework/configure-apps/file-schema/runtime/codebase-element.md) element.</span></span>  
  
-   <span data-ttu-id="9162c-105">Przy użyciu [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="9162c-105">Using the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element.</span></span>  
  
 <span data-ttu-id="9162c-106">Można również użyć [narzędzia konfiguracji programu .NET Framework (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) do określenia lokalizacji zestawu lub określić inną lokalizację dla plików wykonywalnych języka sondowania dla zestawów.</span><span class="sxs-lookup"><span data-stu-id="9162c-106">You can also use the [.NET Framework Configuration Tool (Mscorcfg.msc)](http://msdn.microsoft.com/en-us/a7106c52-68da-490e-b129-971b2c743764) to specify assembly locations or specify locations for the common language runtime to probe for assemblies.</span></span>  
  
## <a name="using-the-codebase-element"></a><span data-ttu-id="9162c-107">Przy użyciu \<codeBase > — Element</span><span class="sxs-lookup"><span data-stu-id="9162c-107">Using the \<codeBase> Element</span></span>  
 <span data-ttu-id="9162c-108">Można użyć  **\<codeBase >** elementu tylko w maszynie konfiguracji lub wydawcy pliki zasad, które również przekierować wersja zestawu.</span><span class="sxs-lookup"><span data-stu-id="9162c-108">You can use the **\<codeBase>** element only in machine configuration or publisher policy files that also redirect the assembly version.</span></span> <span data-ttu-id="9162c-109">Środowisko uruchomieniowe określa wersji zestawu do użycia, stosuje się ustawienie baza kodu z pliku, który określa wersję.</span><span class="sxs-lookup"><span data-stu-id="9162c-109">When the runtime determines which assembly version to use, it applies the code base setting from the file that determines the version.</span></span> <span data-ttu-id="9162c-110">Jeśli wskazuje nie ścieżki bazowej kodu środowiska uruchomieniowego sondy dla zestawu w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="9162c-110">If no code base is indicated, the runtime probes for the assembly in the normal way.</span></span> <span data-ttu-id="9162c-111">Aby uzyskać więcej informacji, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9162c-111">For details, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="9162c-112">Poniższy przykład przedstawia sposób określenia lokalizacji zestawu.</span><span class="sxs-lookup"><span data-stu-id="9162c-112">The following example shows how to specify an assembly's location.</span></span>  
  
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
  
 <span data-ttu-id="9162c-113">**Wersji** atrybut jest wymagany dla wszystkich zestawów o silnych nazwach, ale należy pominąć dla zestawów, które są nie o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="9162c-113">The **version** attribute is required for all strong-named assemblies but should be omitted for assemblies that are not strong-named.</span></span> <span data-ttu-id="9162c-114">**\<CodeBase >** wymaga elementu **href** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="9162c-114">The **\<codeBase>** element requires the **href** attribute.</span></span> <span data-ttu-id="9162c-115">Nie można określić wersji zakresów w  **\<codeBase >** elementu.</span><span class="sxs-lookup"><span data-stu-id="9162c-115">You cannot specify version ranges in the **\<codeBase>** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9162c-116">Jeśli są udostępnia podstawowe wskazówkę dla zestawu, który nie jest o silnych nazwach, wskazówka musi wskazywać baza aplikacji lub podkatalogu podstawowego katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9162c-116">If you are supplying a code base hint for an assembly that is not strong-named, the hint must point to the application base or a subdirectory of the application base directory.</span></span>  
  
## <a name="using-the-probing-element"></a><span data-ttu-id="9162c-117">Przy użyciu \<sondowanie > — Element</span><span class="sxs-lookup"><span data-stu-id="9162c-117">Using the \<probing> Element</span></span>  
 <span data-ttu-id="9162c-118">Środowisko uruchomieniowe lokalizuje zestawy, które nie mają bazy kodu przez sondowanie.</span><span class="sxs-lookup"><span data-stu-id="9162c-118">The runtime locates assemblies that do not have a code base by probing.</span></span> <span data-ttu-id="9162c-119">Aby uzyskać więcej informacji na temat sondowania, zobacz [jak zestawy środowiska wykonawczego lokalizuje](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="9162c-119">For more information about probing, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="9162c-120">Można użyć [ \<sondowanie >](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) elementu w pliku konfiguracji aplikacji, aby określić podkatalogi środowiska uruchomieniowego powinna przeszukać podczas lokalizowania zestawów.</span><span class="sxs-lookup"><span data-stu-id="9162c-120">You can use the [\<probing>](../../../docs/framework/configure-apps/file-schema/runtime/probing-element.md) element in the application configuration file to specify subdirectories the runtime should search when locating an assembly.</span></span> <span data-ttu-id="9162c-121">Poniższy przykład pokazuje, jak można określić katalogi, które powinna przeszukać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9162c-121">The following example shows how to specify directories the runtime should search.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 <span data-ttu-id="9162c-122">**PrivatePath** atrybut zawiera katalogi, które środowiska uruchomieniowego ma poszukiwać zestawów.</span><span class="sxs-lookup"><span data-stu-id="9162c-122">The **privatePath** attribute contains the directories that the runtime should search for assemblies.</span></span> <span data-ttu-id="9162c-123">Jeśli aplikacja znajduje się w lokalizacji C:\Program Files\MyApp, zestawy, które nie zostanie określona ścieżka bazowa kodu w C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin i C:\Program Files\MyApp\Bin3 będzie szukać środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9162c-123">If the application is located at C:\Program Files\MyApp, the runtime will look for assemblies that do not specify a code base in C:\Program Files\MyApp\Bin, C:\Program Files\MyApp\Bin2\Subbin, and C:\Program Files\MyApp\Bin3.</span></span> <span data-ttu-id="9162c-124">Katalogach określonych w **privatePath** musi być podkatalogi podstawowego katalogu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9162c-124">The directories specified in **privatePath** must be subdirectories of the application base directory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9162c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9162c-125">See Also</span></span>  
 [<span data-ttu-id="9162c-126">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="9162c-126">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 [<span data-ttu-id="9162c-127">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="9162c-127">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [<span data-ttu-id="9162c-128">Jak lokalizuje zestawów przez środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="9162c-128">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="9162c-129">Konfigurowanie aplikacji programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9162c-129">Configuring .NET Framework Apps</span></span>](http://msdn.microsoft.com/en-us/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
