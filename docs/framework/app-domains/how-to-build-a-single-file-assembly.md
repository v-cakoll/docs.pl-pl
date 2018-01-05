---
title: 'Porady: kompilacja zestawu jednoplikowego'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bd9f2bab23fff1bbc4ebb521b167ac8031af3bc7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-single-file-assembly"></a><span data-ttu-id="b3c38-102">Porady: kompilacja zestawu jednoplikowego</span><span class="sxs-lookup"><span data-stu-id="b3c38-102">How to: Build a Single-File Assembly</span></span>
<span data-ttu-id="b3c38-103">Zestawu pojedynczego pliku, który jest najprostsza rodzaju zestawu, zawiera informacje o typie i wdrażania, jak również [manifest zestawu](../../../docs/framework/app-domains/assembly-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b3c38-103">A single-file assembly, which is the simplest type of assembly, contains type information and implementation, as well as the [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md).</span></span> <span data-ttu-id="b3c38-104">Kompilatory w wierszu polecenia można użyć lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] można utworzyć zestawu pojedynczego pliku.</span><span class="sxs-lookup"><span data-stu-id="b3c38-104">You can use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] to create a single-file assembly.</span></span> <span data-ttu-id="b3c38-105">Domyślnie kompilator tworzy plik zestawu z rozszerzeniem .exe.</span><span class="sxs-lookup"><span data-stu-id="b3c38-105">By default, the compiler creates an assembly file with an .exe extension.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]<span data-ttu-id="b3c38-106">C# i Visual Basic można użyć tylko w celu utworzenia zestawy jednoplikowe.</span><span class="sxs-lookup"><span data-stu-id="b3c38-106"> for C# and Visual Basic can be used only to create single-file assemblies.</span></span> <span data-ttu-id="b3c38-107">Jeśli chcesz utworzyć zestawy wieloplikowe, należy użyć kompilatory w wierszu polecenia lub [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] w języku Visual C++.</span><span class="sxs-lookup"><span data-stu-id="b3c38-107">If you want to create multifile assemblies, you must use command-line compilers or [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++.</span></span>  
  
 <span data-ttu-id="b3c38-108">Poniższe procedury pokazują, jak utworzyć zestawy jednoplikowe przy użyciu kompilatory w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="b3c38-108">The following procedures show how to create single-file assemblies using command-line compilers.</span></span>  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a><span data-ttu-id="b3c38-109">Można utworzyć zestawu z rozszerzeniem .exe</span><span class="sxs-lookup"><span data-stu-id="b3c38-109">To create an assembly with an .exe extension</span></span>  
  
1.  <span data-ttu-id="b3c38-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b3c38-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b3c38-111">\<*polecenie kompilatora*> \<*nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="b3c38-111">\<*compiler command*> \<*module name*></span></span>  
  
     <span data-ttu-id="b3c38-112">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b3c38-112">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="b3c38-113">Poniższy przykład tworzy zestaw o nazwie `myCode.exe` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="b3c38-113">The following example creates an assembly named `myCode.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a><span data-ttu-id="b3c38-114">Aby utworzyć zestaw z rozszerzeniem .exe i określ nazwę pliku wyjściowego</span><span class="sxs-lookup"><span data-stu-id="b3c38-114">To create an assembly with an .exe extension and specify the output file name</span></span>  
  
1.  <span data-ttu-id="b3c38-115">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b3c38-115">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b3c38-116">\<*polecenie kompilatora*> **/out:**\<*nazwę pliku*> \<*nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="b3c38-116">\<*compiler command*> **/out:**\<*file name*> \<*module name*></span></span>  
  
     <span data-ttu-id="b3c38-117">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu *nazwę pliku* to nazwa pliku wyjściowego i *nazwy modułu* jest nazwą Moduł kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b3c38-117">In this command, *compiler command* is the compiler command for the language used in your code module, *file name* is the output file name, and *module name* is the name of the code module to compile into the assembly.</span></span>  
  
 <span data-ttu-id="b3c38-118">Poniższy przykład tworzy zestaw o nazwie `myAssembly.exe` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="b3c38-118">The following example creates an assembly named `myAssembly.exe` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a><span data-ttu-id="b3c38-119">Tworzenie zestawów biblioteki</span><span class="sxs-lookup"><span data-stu-id="b3c38-119">Creating Library Assemblies</span></span>  
 <span data-ttu-id="b3c38-120">Zestaw biblioteki jest podobny do biblioteki klas.</span><span class="sxs-lookup"><span data-stu-id="b3c38-120">A library assembly is similar to a class library.</span></span> <span data-ttu-id="b3c38-121">Zawiera typy, które będzie odwoływać się do innych zestawów, ale nie żaden punkt wejścia, aby rozpocząć wykonywania.</span><span class="sxs-lookup"><span data-stu-id="b3c38-121">It contains types that will be referenced by other assemblies, but it has no entry point to begin execution.</span></span>  
  
#### <a name="to-create-a-library-assembly"></a><span data-ttu-id="b3c38-122">Aby utworzyć zestaw biblioteki</span><span class="sxs-lookup"><span data-stu-id="b3c38-122">To create a library assembly</span></span>  
  
1.  <span data-ttu-id="b3c38-123">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="b3c38-123">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b3c38-124">\<*polecenie kompilatora*> **Library** \< *nazwy modułu*></span><span class="sxs-lookup"><span data-stu-id="b3c38-124">\<*compiler command*> **/t:library** \<*module name*></span></span>  
  
     <span data-ttu-id="b3c38-125">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka użytego w module kodu i *nazwy modułu* to nazwa modułu kodu do kompilacji w zestawie.</span><span class="sxs-lookup"><span data-stu-id="b3c38-125">In this command, *compiler command* is the compiler command for the language used in your code module, and *module name* is the name of the code module to compile into the assembly.</span></span> <span data-ttu-id="b3c38-126">Umożliwia także inne opcje kompilatora, takich jak **/out:** opcji.</span><span class="sxs-lookup"><span data-stu-id="b3c38-126">You can also use other compiler options, such as the **/out:** option.</span></span>  
  
 <span data-ttu-id="b3c38-127">Poniższy przykład tworzy zestaw biblioteczny o nazwie `myCodeAssembly.dll` z modułu kodu o nazwie `myCode`.</span><span class="sxs-lookup"><span data-stu-id="b3c38-127">The following example creates a library assembly named `myCodeAssembly.dll` from a code module called `myCode`.</span></span>  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3c38-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c38-128">See Also</span></span>  
 [<span data-ttu-id="b3c38-129">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="b3c38-129">Creating Assemblies</span></span>](../../../docs/framework/app-domains/create-assemblies.md)  
 [<span data-ttu-id="b3c38-130">Zestawy wieloplikowe</span><span class="sxs-lookup"><span data-stu-id="b3c38-130">Multifile Assemblies</span></span>](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [<span data-ttu-id="b3c38-131">Instrukcje: kompilacja zestawów wieloplikowych</span><span class="sxs-lookup"><span data-stu-id="b3c38-131">How to: Build a Multifile Assembly</span></span>](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [<span data-ttu-id="b3c38-132">Programowanie za pomocą zestawów</span><span class="sxs-lookup"><span data-stu-id="b3c38-132">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
