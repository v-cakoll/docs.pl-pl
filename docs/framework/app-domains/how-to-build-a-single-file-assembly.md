---
title: 'Porady: kompilacja zestawu jednoplikowego'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80fa584a21a3bdfb9392021959d777139daafd04
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="d6a87-102">Porady: kompilacja zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="d6a87-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="d6a87-103">Zestawu pojedynczego pliku, który jest najprostsza rodzaju zestawu, zawiera informacje o typie i wdrażania, jak również [manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="d6a87-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="d6a87-104">Kompilatory w wierszu polecenia można użyć lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] można utworzyć zestawu pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="d6a87-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="d6a87-105">Domyślnie kompilator tworzy plik zestawu z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="d6a87-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]<span data-ttu-id="d6a87-106"> C# i Visual Basic można użyć tylko w celu utworzenia zestawy jednoplikowe.</span><span class="sxs-lookup"><span data-stu-id="d6a87-106"> for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="d6a87-107">Jeśli chcesz utworzyć zestawy wieloplikowe, należy użyć kompilatory w wierszu polecenia lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] w języku Visual C++.</span><span class="sxs-lookup"><span data-stu-id="d6a87-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="d6a87-108">Poniższe procedury pokazują, jak utworzyć zestawy jednoplikowe przy użyciu kompilatory w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d6a87-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="d6a87-109">Można utworzyć zestawu z rozszerzeniem .exe</span><span class="sxs-lookup"><span data-stu-id="d6a87-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="d6a87-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d6a87-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d6a87-111">\<*polecenie kompilatora*> \<*nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="d6a87-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="d6a87-112">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d6a87-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="d6a87-113">Poniższy przykład tworzy zestaw o nazwie `myCode.exe` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="d6a87-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```console
csc myCode.cs  
```  

```console
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="d6a87-114">Aby utworzyć zestaw z rozszerzeniem .exe i określ nazwę pliku wyjściowego</span><span class="sxs-lookup"><span data-stu-id="d6a87-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="d6a87-115">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d6a87-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d6a87-116">\<*polecenie kompilatora*> **/out:**\<*nazwę pliku*> \<*nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="d6a87-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="d6a87-117">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu *nazwę pliku* to nazwa pliku wyjściowego i *nazwy modułu* jest nazwą Moduł kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d6a87-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="d6a87-118">Poniższy przykład tworzy zestaw o nazwie `myAssembly.exe` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="d6a87-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```console  
csc -out:myAssembly.exe myCode.cs  
```  
  
```console
vbc -out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="d6a87-119">Tworzenie zestawów biblioteki</span><span class="sxs-lookup"><span data-stu-id="d6a87-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="d6a87-120">Zestaw biblioteki jest podobny do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="d6a87-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="d6a87-121">Zawiera typy, które będzie odwoływać się do innych zestawów, ale nie żaden punkt wejścia, aby rozpocząć wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d6a87-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="d6a87-122">Aby utworzyć zestaw biblioteki</span><span class="sxs-lookup"><span data-stu-id="d6a87-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="d6a87-123">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d6a87-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d6a87-124">\<*polecenie kompilatora*> **- t: Biblioteka** \< *nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="d6a87-124">\<*compiler command*> **-t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="d6a87-125">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d6a87-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="d6a87-126">Umożliwia także inne opcje kompilatora, takich jak **-out:** opcji.</span><span class="sxs-lookup"><span data-stu-id="d6a87-126">You can also use other compiler options, such as the **-out:** option.</span></span>  
  
 <span data-ttu-id="d6a87-127">Poniższy przykład tworzy zestaw biblioteczny o nazwie `myCodeAssembly.dll` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="d6a87-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```console  
csc -out:myCodeLibrary.dll -t:library myCode.cs  
```  
  
```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6a87-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d6a87-128">See Also</span></span>  
 [<span data-ttu-id="d6a87-129">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="d6a87-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="d6a87-130">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="d6a87-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="d6a87-131">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="d6a87-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="d6a87-132">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="d6a87-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
