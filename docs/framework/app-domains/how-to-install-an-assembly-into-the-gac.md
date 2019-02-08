---
title: 'Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej'
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
ms.openlocfilehash: adeaaa6626a1c9e9e4543613a8fa9e94d2b67e89
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826840"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="81400-102">Instrukcje: Instalowanie zestawu w globalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="81400-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="81400-103">Zestawy, które mają kilka aplikacji są przechowywane w globalnej pamięci podręcznej zestawów (GAC).</span><span class="sxs-lookup"><span data-stu-id="81400-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="81400-104">Instalowanie zestawu w [globalnej pamięci podręcznej](https://docs.microsoft.com/en-us/dotnet/framework/app-domains/gac) przy użyciu jednego z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="81400-104">Install an assembly into the [global assembly cache](https://docs.microsoft.com/en-us/dotnet/framework/app-domains/gac) with one of the following components:</span></span> 
- [<span data-ttu-id="81400-105">Windows Installer</span><span class="sxs-lookup"><span data-stu-id="81400-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="81400-106">Narzędzie Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="81400-106">Global assembly cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="81400-107">Pamięci podręcznej GAC można instalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="81400-107">You can install only strong-named assemblies into the GAC.</span></span> <span data-ttu-id="81400-108">Aby uzyskać informacje o sposobie tworzenia zestawu z silną nazwą, zobacz [jak: Podpisywanie zestawu silną nazwą](how-to-sign-an-assembly-with-a-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="81400-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](how-to-sign-an-assembly-with-a-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="81400-109">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="81400-109">Windows Installer</span></span>

<span data-ttu-id="81400-110">[Instalator Windows](https://docs.microsoft.com/en-us/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji Windows jest zalecany sposób dodawania zestawów do globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="81400-110">[Windows Installer](https://docs.microsoft.com/en-us/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="81400-111">Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej i inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="81400-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="81400-112">Aby utworzyć pakiet instalacyjny Instalatora Windows, użyj [WiX rozszerzenia narzędzi programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="81400-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="81400-113">Narzędzie Global assembly cache</span><span class="sxs-lookup"><span data-stu-id="81400-113">Global assembly cache tool</span></span>

<span data-ttu-id="81400-114">Możesz użyć [narzędzie global assembly cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) dodawania zestawów do globalnej pamięci podręcznej oraz wyświetlanie zawartości globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="81400-114">You can use the [global assembly cache tool (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="81400-115">*Gacutil.exe* jest tylko do celów programowania.</span><span class="sxs-lookup"><span data-stu-id="81400-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="81400-116">Nie jest używany do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="81400-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="81400-117">Składnia przy użyciu *gacutil.exe* instalować zestawów w globalnej pamięci podręcznej zestawów jest następująca:</span><span class="sxs-lookup"><span data-stu-id="81400-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```console
gacutil -i <assembly name>
```

<span data-ttu-id="81400-118">W tym poleceniu  *\<Nazwa zestawu >* to nazwa zestawu, aby zainstalować w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="81400-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="81400-119">Jeśli *gacutil.exe* nie znajduje się w ścieżce systemowej, użyj [wiersz polecenia programisty dla programu VS  *\<wersji >*](https://docs.microsoft.com/en-us/dotnet/framework/tools/developer-command-prompt-for-vs).</span><span class="sxs-lookup"><span data-stu-id="81400-119">If *gacutil.exe* isn't in your system path, use the [Developer Command Prompt for VS *\<version>*](https://docs.microsoft.com/en-us/dotnet/framework/tools/developer-command-prompt-for-vs).</span></span>

<span data-ttu-id="81400-120">Poniższy przykład instaluje zestaw o nazwie pliku *hello.dll* w globalnej pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="81400-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```console
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="81400-121">We wcześniejszych wersjach programu .NET Framework *Shfusion.dll* rozszerzenie powłoki Windows umożliwiają instalowanie zestawów, przeciągając je do Eksploratora plików.</span><span class="sxs-lookup"><span data-stu-id="81400-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="81400-122">Począwszy od programu .NET Framework 4, *Shfusion.dll* jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="81400-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="81400-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81400-123">See also</span></span>

- [<span data-ttu-id="81400-124">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="81400-124">Working with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="81400-125">Instrukcje: Usuwanie zestawu z globalnej pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="81400-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="81400-126">Gacutil.exe (narzędzie Global assembly cache)</span><span class="sxs-lookup"><span data-stu-id="81400-126">Gacutil.exe (Global assembly cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="81400-127">Instrukcje: Podpisywanie zestawu silną nazwą</span><span class="sxs-lookup"><span data-stu-id="81400-127">How to: Sign an assembly with a strong name</span></span>](how-to-sign-an-assembly-with-a-strong-name.md)