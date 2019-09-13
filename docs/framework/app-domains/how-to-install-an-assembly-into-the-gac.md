---
title: 'Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 02/05/2019
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
ms.openlocfilehash: 8e2d051cda9861da1af2caa65160b6e753b24bd1
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926517"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="2210a-102">Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="2210a-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="2210a-103">Global Assembly Cache (GAC) przechowuje zestawy, które są udostępniane przez kilka aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2210a-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="2210a-104">Zainstaluj zestaw w [globalnej pamięci podręcznej zestawów](gac.md) przy użyciu jednego z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="2210a-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span> 

- [<span data-ttu-id="2210a-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="2210a-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="2210a-106">Narzędzie globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="2210a-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="2210a-107">Do pamięci podręcznej GAC można zainstalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="2210a-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="2210a-108">Informacje o sposobie tworzenia zestawu o silnej nazwie można znaleźć w temacie [How to: Podpisz zestaw silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="2210a-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="2210a-109">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="2210a-109">Windows Installer</span></span>

<span data-ttu-id="2210a-110">[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2210a-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="2210a-111">Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="2210a-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="2210a-112">Aby utworzyć pakiet Instalatora dla Instalator Windows, użyj rozszerzenia zestawu [narzędzi WIX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="2210a-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="2210a-113">Narzędzie globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="2210a-113">Global assembly cache tool</span></span>

<span data-ttu-id="2210a-114">Aby dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów, można użyć [Narzędzia globalnej pamięci podręcznej zestawów (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) .</span><span class="sxs-lookup"><span data-stu-id="2210a-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="2210a-115">*Gacutil. exe* służy tylko do celów deweloperskich.</span><span class="sxs-lookup"><span data-stu-id="2210a-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="2210a-116">Nie należy używać go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2210a-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="2210a-117">Składnia programu *Gacutil. exe* do zainstalowania zestawu w pamięci podręcznej jest następująca:</span><span class="sxs-lookup"><span data-stu-id="2210a-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="2210a-118">W tym poleceniu  *\<nazwa zestawu >* jest nazwą zestawu, który ma zostać zainstalowany w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2210a-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="2210a-119">Jeśli *Gacutil. exe* nie znajduje się w ścieżce systemowej, użyj [wiersz polecenia dla deweloperów dla programu vs  *\<version >* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="2210a-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="2210a-120">Poniższy przykład instaluje zestaw z nazwą pliku *Hello. dll* w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="2210a-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="2210a-121">We wcześniejszych wersjach .NET Framework rozszerzenie powłoki systemu Windows *Shfusion. dll* umożliwia instalowanie zestawów przez przeciąganie ich do Eksploratora plików.</span><span class="sxs-lookup"><span data-stu-id="2210a-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="2210a-122">Począwszy od .NET Framework 4 *Shfusion. dll* jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="2210a-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="2210a-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2210a-123">See also</span></span>

- [<span data-ttu-id="2210a-124">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="2210a-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="2210a-125">Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="2210a-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="2210a-126">Gacutil. exe (Narzędzie globalnej pamięci podręcznej zestawów)</span><span class="sxs-lookup"><span data-stu-id="2210a-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="2210a-127">Instrukcje: Podpisz zestaw silną nazwą</span><span class="sxs-lookup"><span data-stu-id="2210a-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)
