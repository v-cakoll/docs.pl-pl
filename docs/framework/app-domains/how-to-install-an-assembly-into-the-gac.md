---
title: Instalowanie zestawu w GAC
ms.date: 09/20/2018
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d365ac77fe6cd7fc4fca36705729ec12b06d6830
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584584"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="6772a-102">Porady: Instalowanie zestawu w globalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="6772a-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="6772a-103">Istnieją dwa sposoby instalacji zestawu o silnej nazwie do globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="6772a-103">There are two ways to install a strong-named assembly into the global assembly cache (GAC).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6772a-104">W pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="6772a-104">Only strong-named assemblies can be installed into the GAC.</span></span> <span data-ttu-id="6772a-105">Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [porady: podpisywanie zestawu za pomocą silnej nazwy](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="6772a-105">For information about how to create a strong-named assembly, see [How to: Sign an Assembly with a Strong Name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="6772a-106">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="6772a-106">Windows Installer</span></span>

<span data-ttu-id="6772a-107">[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji Windows jest zalecany sposób dodawania zestawów do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6772a-107">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="6772a-108">Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej i inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="6772a-108">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="6772a-109">Możesz użyć [zestaw narzędzi WiX rozszerzenia programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) do utworzenia pakietu Instalatora dla Instalatora Windows.</span><span class="sxs-lookup"><span data-stu-id="6772a-109">You can use the [WiX Toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension) to create an installer package for Windows Installer.</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="6772a-110">Narzędzie Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="6772a-110">Global assembly cache tool</span></span>

<span data-ttu-id="6772a-111">Możesz użyć [narzędzie Global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) dodać zestawy o silnej nazwie do globalnej pamięci podręcznej oraz wyświetlanie zawartości globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6772a-111">You can use the [Global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add strong-named assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="6772a-112">Narzędzie Gacutil.exe jest przeznaczone tylko do celów deweloperskich i nie powinno być używane do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="6772a-112">Gacutil.exe is only for development purposes and should not be used to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="6772a-113">Składnia gacutil jest następująca:</span><span class="sxs-lookup"><span data-stu-id="6772a-113">The syntax for gacutil is as follows:</span></span>

```shell
gacutil -i <assembly name>
```

<span data-ttu-id="6772a-114">W tym poleceniu *nazwy zestawu* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6772a-114">In this command, *assembly name* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="6772a-115">Poniższy przykład instaluje zestaw o nazwie pliku `hello.dll` w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6772a-115">The following example installs an assembly with the file name `hello.dll` into the global assembly cache.</span></span>

```shell
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="6772a-116">We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki Windows Shfusion.dll umożliwia instalację zestawów przez przeciąganie ich **Eksploratora plików**.</span><span class="sxs-lookup"><span data-stu-id="6772a-116">In earlier versions of the .NET Framework, the Shfusion.dll Windows shell extension enabled you to install assemblies by dragging them in **File Explorer**.</span></span> <span data-ttu-id="6772a-117">Począwszy od programu .NET Framework 4, biblioteka Shfusion.dll jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="6772a-117">Beginning with the .NET Framework 4, Shfusion.dll is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="6772a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6772a-118">See also</span></span>

- [<span data-ttu-id="6772a-119">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="6772a-119">Working with Assemblies and the Global Assembly Cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="6772a-120">Instrukcje: usuwanie zestawu z pamięci Global Assembly Cache</span><span class="sxs-lookup"><span data-stu-id="6772a-120">How to: Remove an Assembly from the Global Assembly Cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="6772a-121">Gacutil.exe (narzędzie Global Assembly Cache)</span><span class="sxs-lookup"><span data-stu-id="6772a-121">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="6772a-122">Instrukcje: podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="6772a-122">How to: Sign an Assembly with a Strong Name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)