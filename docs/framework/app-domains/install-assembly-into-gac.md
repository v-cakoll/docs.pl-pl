---
title: 'Instrukcje: instalowanie zestawu w globalnej pamięci podręcznej zestawów'
description: Zainstaluj zestaw w globalnej pamięci podręcznej zestawów (GAC) w programie .NET, aby mógł być współużytkowany przez wiele aplikacji. Użyj Instalator Windows lub narzędzia GAC.
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 08a5475d74327265f28b65676ae56be15afb57d3
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104675"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="47801-104">Instrukcje: instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="47801-104">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="47801-105">Global Assembly Cache (GAC) przechowuje zestawy, które są udostępniane przez kilka aplikacji.</span><span class="sxs-lookup"><span data-stu-id="47801-105">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="47801-106">Zainstaluj zestaw w [globalnej pamięci podręcznej zestawów](gac.md) przy użyciu jednego z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="47801-106">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="47801-107">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="47801-107">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="47801-108">Narzędzie globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="47801-108">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="47801-109">Można zainstalować tylko zestawy o silnych nazwach w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="47801-109">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="47801-110">Aby uzyskać informacje na temat sposobu tworzenia zestawu o silnej nazwie, zobacz [How to: Sign a Assembly with silnej nazwy](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="47801-110">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="47801-111">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="47801-111">Windows Installer</span></span>

<span data-ttu-id="47801-112">[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="47801-112">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="47801-113">Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="47801-113">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="47801-114">Aby utworzyć pakiet Instalatora dla Instalator Windows, użyj rozszerzenia zestawu [narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="47801-114">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="47801-115">Narzędzie globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="47801-115">Global Assembly Cache tool</span></span>

<span data-ttu-id="47801-116">Aby dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów, można użyć [Narzędzia do globalnej pamięci podręcznej zestawów .NET (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="47801-116">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="47801-117">*Gacutil.exe* służy tylko do celów deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="47801-117">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="47801-118">Nie należy używać go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="47801-118">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="47801-119">Składnia *gacutil.exe* służąca do instalowania zestawu w pamięci podręcznej GAC jest następująca:</span><span class="sxs-lookup"><span data-stu-id="47801-119">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="47801-120">W tym poleceniu *\<assembly name>* jest nazwą zestawu, który ma zostać zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="47801-120">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="47801-121">Jeśli *gacutil.exe* nie znajduje się w ścieżce systemu, należy użyć [wiersza polecenia dewelopera *\<version>* dla programu vs ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="47801-121">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="47801-122">Poniższy przykład instaluje zestaw z nazwą pliku *hello.dll* w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="47801-122">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="47801-123">We wcześniejszych wersjach .NET Framework rozszerzenie powłoki Windows *Shfusion.dll* pozwala na instalowanie zestawów przez przeciąganie ich do Eksploratora plików.</span><span class="sxs-lookup"><span data-stu-id="47801-123">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="47801-124">Począwszy od .NET Framework 4 *Shfusion.dll* jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="47801-124">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="47801-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="47801-125">See also</span></span>

- [<span data-ttu-id="47801-126">Pracuj z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="47801-126">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="47801-127">Instrukcje: usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="47801-127">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="47801-128">Gacutil.exe (Narzędzie globalnej pamięci podręcznej zestawów)</span><span class="sxs-lookup"><span data-stu-id="47801-128">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="47801-129">Instrukcje: podpisywanie zestawu za pomocą silnej nazwy</span><span class="sxs-lookup"><span data-stu-id="47801-129">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
