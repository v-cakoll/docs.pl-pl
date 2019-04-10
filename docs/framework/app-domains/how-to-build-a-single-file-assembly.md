---
title: 'Instrukcje: Kompilacja zestawu jednoplikowego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a73b2d8948c9a046fd77c02f1bcc87f5738105d9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304002"
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="761e0-102">Instrukcje: Kompilacja zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="761e0-102">How to: Build a Single-File Assembly</span></span>

<span data-ttu-id="761e0-103">Zestawu pojedynczego pliku to najprostszy rodzaj zestawów, zawiera informacje o typie i wdrażania, jak również [manifestu zestawu](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="761e0-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="761e0-104">Można użyć kompilatorów wiersza polecenia lub programu Visual Studio, można utworzyć zestawu pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="761e0-104">You can use command-line compilers or Visual Studio to create a single-file assembly.</span></span> <span data-ttu-id="761e0-105">Domyślnie kompilator tworzy plik zestawu z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="761e0-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>

> [!NOTE]
> <span data-ttu-id="761e0-106">Program Visual Studio dla języka C# i Visual Basic mogą służyć tylko do tworzenia zespołów pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="761e0-106">Visual Studio for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="761e0-107">Jeśli chcesz utworzyć zestawy wieloplikowe, należy użyć kompilatorów wiersza polecenia lub programu Visual C++.</span><span class="sxs-lookup"><span data-stu-id="761e0-107">If you want to create multifile assemblies, you must use command-line compilers or Visual C++.</span></span>

<span data-ttu-id="761e0-108">Poniższe procedury przedstawiają sposób tworzenia zespołów pojedynczego pliku za pomocą kompilatorów wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="761e0-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>

## <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="761e0-109">Aby utworzyć zestaw z rozszerzeniem .exe</span><span class="sxs-lookup"><span data-stu-id="761e0-109">To create an assembly with an .exe extension</span></span>

1. <span data-ttu-id="761e0-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="761e0-110">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="761e0-111">\<*polecenie kompilatora*> \<*Nazwa modułu*></span><span class="sxs-lookup"><span data-stu-id="761e0-111">\<*compiler command*> \<*module name*></span></span>

     <span data-ttu-id="761e0-112">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, i *Nazwa modułu* to nazwa modułu kodu, aby skompilować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="761e0-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="761e0-113">Poniższy przykład tworzy zestaw o nazwie `myCode.exe` moduł kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="761e0-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="761e0-114">Aby utworzyć zestaw z rozszerzeniem .exe i określ nazwę pliku wyjściowego</span><span class="sxs-lookup"><span data-stu-id="761e0-114">To create an assembly with an .exe extension and specify the output file name</span></span>

1. <span data-ttu-id="761e0-115">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="761e0-115">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="761e0-116">\<*polecenie kompilatora*> **/out:**\<*nazwy pliku*> \<*Nazwa modułu*></span><span class="sxs-lookup"><span data-stu-id="761e0-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>

     <span data-ttu-id="761e0-117">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, *nazwy pliku* jest nazwa pliku wyjściowego i *Nazwa modułu* nazywa się Moduł kodu, aby skompilować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="761e0-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>

 <span data-ttu-id="761e0-118">Poniższy przykład tworzy zestaw o nazwie `myAssembly.exe` moduł kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="761e0-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a><span data-ttu-id="761e0-119">Tworzenie zestawów biblioteki</span><span class="sxs-lookup"><span data-stu-id="761e0-119">Creating Library Assemblies</span></span>
 <span data-ttu-id="761e0-120">W zestawie biblioteki jest podobny do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="761e0-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="761e0-121">Zawiera typy, które będzie używane przez inne zestawy, ale go nie ma punktu wejścia do rozpoczęcia wykonywania.</span><span class="sxs-lookup"><span data-stu-id="761e0-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>

### <a name="to-create-a-library-assembly"></a><span data-ttu-id="761e0-122">Można utworzyć zestawu biblioteki</span><span class="sxs-lookup"><span data-stu-id="761e0-122">To create a library assembly</span></span>

1. <span data-ttu-id="761e0-123">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="761e0-123">At the command prompt, type the following command:</span></span>

     <span data-ttu-id="761e0-124">\<*polecenie kompilatora*> **- t: Biblioteka** \< *Nazwa modułu*></span><span class="sxs-lookup"><span data-stu-id="761e0-124">\<*compiler command*> **-t:library** \<*module name*></span></span>

     <span data-ttu-id="761e0-125">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu, i *Nazwa modułu* to nazwa modułu kodu, aby skompilować do zestawu.</span><span class="sxs-lookup"><span data-stu-id="761e0-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="761e0-126">Umożliwia także inne opcje kompilatora, takich jak **-out:** opcji.</span><span class="sxs-lookup"><span data-stu-id="761e0-126">You can also use other compiler options, such as the **-out:** option.</span></span>

 <span data-ttu-id="761e0-127">Poniższy przykład tworzy zestaw biblioteki o nazwie `myCodeAssembly.dll` moduł kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="761e0-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a><span data-ttu-id="761e0-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="761e0-128">See also</span></span>

- [<span data-ttu-id="761e0-129">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="761e0-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)
- [<span data-ttu-id="761e0-130">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="761e0-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)
- [<span data-ttu-id="761e0-131">Instrukcje: Kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="761e0-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [<span data-ttu-id="761e0-132">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="761e0-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)