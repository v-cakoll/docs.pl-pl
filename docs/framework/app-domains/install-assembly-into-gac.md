---
title: 'Jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów'
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
- windows installer, global assembly cache
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
ms.openlocfilehash: 64878a795a7c5b790c8991064e32b82505685c0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155566"
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a><span data-ttu-id="8533a-102">Jak: Instalowanie zestawu w globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="8533a-102">How to: Install an assembly into the global assembly cache</span></span>

<span data-ttu-id="8533a-103">Globalna pamięć podręczna zestawów (GAC) przechowuje zestawy współużytkowane przez kilka aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8533a-103">The global assembly cache (GAC) stores assemblies that several applications share.</span></span> <span data-ttu-id="8533a-104">Zainstaluj zespół w [globalnej pamięci podręcznej zestawów](gac.md) z jednym z następujących składników:</span><span class="sxs-lookup"><span data-stu-id="8533a-104">Install an assembly into the [global assembly cache](gac.md) with one of the following components:</span></span>

- [<span data-ttu-id="8533a-105">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="8533a-105">Windows Installer</span></span>](#windows-installer)
- [<span data-ttu-id="8533a-106">Narzędzie Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="8533a-106">Global Assembly Cache tool</span></span>](#global-assembly-cache-tool)

> [!IMPORTANT]
> <span data-ttu-id="8533a-107">W globalnej pamięci podręcznej zestawów można zainstalować tylko zestawy o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="8533a-107">You can install only strong-named assemblies into the global assembly cache.</span></span> <span data-ttu-id="8533a-108">Aby uzyskać informacje dotyczące tworzenia zestawu o silnej nazwie, zobacz [Jak: Podpisz zestaw o silnej nazwie](../../standard/assembly/sign-strong-name.md).</span><span class="sxs-lookup"><span data-stu-id="8533a-108">For information about how to create a strong-named assembly, see [How to: Sign an assembly with a strong name](../../standard/assembly/sign-strong-name.md).</span></span>

## <a name="windows-installer"></a><span data-ttu-id="8533a-109">Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="8533a-109">Windows Installer</span></span>

<span data-ttu-id="8533a-110">[Instalator Windows](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), aparat instalacji systemu Windows, jest zalecanym sposobem dodawania zestawów do globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8533a-110">[Windows Installer](/windows/desktop/Msi/installation-of-assemblies-to-the-global-assembly-cache), the Windows installation engine, is the recommended way to add assemblies to the global assembly cache.</span></span> <span data-ttu-id="8533a-111">Instalator Windows zapewnia zliczanie odwołań zestawów w globalnej pamięci podręcznej zestawów i inne korzyści.</span><span class="sxs-lookup"><span data-stu-id="8533a-111">Windows Installer provides reference counting of assemblies in the global assembly cache and other benefits.</span></span> <span data-ttu-id="8533a-112">Aby utworzyć pakiet instalacyjny dla Instalatora Windows, użyj [rozszerzenia zestawu narzędzi WiX dla programu Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span><span class="sxs-lookup"><span data-stu-id="8533a-112">To create an installer package for Windows Installer, use the [WiX toolset extension for Visual Studio 2017](https://marketplace.visualstudio.com/items?itemName=RobMensching.WixToolsetVisualStudio2017Extension).</span></span>

## <a name="global-assembly-cache-tool"></a><span data-ttu-id="8533a-113">Narzędzie Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="8533a-113">Global Assembly Cache tool</span></span>

<span data-ttu-id="8533a-114">Za pomocą [narzędzia .NET Global Assembly Cache (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) można dodać zestawy do globalnej pamięci podręcznej zestawów i wyświetlić zawartość globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8533a-114">You can use the [.NET Global Assembly Cache utility (gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add assemblies to the global assembly cache and to view the contents of the global assembly cache.</span></span>

   > [!NOTE]
   > <span data-ttu-id="8533a-115">*Gacutil.exe* służy wyłącznie do celów rozwojowych.</span><span class="sxs-lookup"><span data-stu-id="8533a-115">*Gacutil.exe* is for development purposes only.</span></span> <span data-ttu-id="8533a-116">Nie używaj go do instalowania zestawów produkcyjnych w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8533a-116">Don't use it to install production assemblies into the global assembly cache.</span></span>

<span data-ttu-id="8533a-117">Składnia za pomocą *gacutil.exe* do zainstalowania zestawu w gac jest następująca:</span><span class="sxs-lookup"><span data-stu-id="8533a-117">The syntax for using *gacutil.exe* to install an assembly in the GAC is as follows:</span></span>

```cmd
gacutil -i <assembly name>
```

<span data-ttu-id="8533a-118">W tym \* \<poleceniu nazwa zestawu>\* jest nazwą zestawu do zainstalowania w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8533a-118">In this command, *\<assembly name>* is the name of the assembly to install in the global assembly cache.</span></span>

<span data-ttu-id="8533a-119">Jeśli *pliku gacutil.exe* nie ma w ścieżce systemowej, użyj [wiersza polecenia Deweloper dla wersji programu VS \* \<>\* ](../tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8533a-119">If *gacutil.exe* isn't in your system path, use the [Developer command prompt for VS *\<version>*](../tools/developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="8533a-120">Poniższy przykład instaluje zestaw o nazwie pliku *hello.dll* w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="8533a-120">The following example installs an assembly with the file name *hello.dll* into the global assembly cache.</span></span>

```cmd
gacutil -i hello.dll
```

> [!NOTE]
> <span data-ttu-id="8533a-121">We wcześniejszych wersjach programu .NET Framework rozszerzenie powłoki *shfusion.dll* systemu Windows umożliwia instalowanie zestawów przez przeciąganie ich do Eksploratora plików.</span><span class="sxs-lookup"><span data-stu-id="8533a-121">In earlier versions of the .NET Framework, the *Shfusion.dll* Windows shell extension let you install assemblies by dragging them to File Explorer.</span></span> <span data-ttu-id="8533a-122">Począwszy od programu .NET Framework 4, *shfusion.dll* jest przestarzały.</span><span class="sxs-lookup"><span data-stu-id="8533a-122">Beginning with .NET Framework 4, *Shfusion.dll* is obsolete.</span></span>

## <a name="see-also"></a><span data-ttu-id="8533a-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8533a-123">See also</span></span>

- [<span data-ttu-id="8533a-124">Praca z zestawami i globalną pamięcią podręczną zestawów</span><span class="sxs-lookup"><span data-stu-id="8533a-124">Work with assemblies and the global assembly cache</span></span>](working-with-assemblies-and-the-gac.md)
- [<span data-ttu-id="8533a-125">Jak: Usuwanie zestawu z globalnej pamięci podręcznej zestawów</span><span class="sxs-lookup"><span data-stu-id="8533a-125">How to: Remove an assembly from the global assembly cache</span></span>](how-to-remove-an-assembly-from-the-gac.md)
- [<span data-ttu-id="8533a-126">Gacutil.exe (narzędzie Globalna pamięć podręczna zestawów)</span><span class="sxs-lookup"><span data-stu-id="8533a-126">Gacutil.exe (Global Assembly Cache tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="8533a-127">Jak: Podpisz zestaw o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="8533a-127">How to: Sign an assembly with a strong name</span></span>](../../standard/assembly/sign-strong-name.md)
