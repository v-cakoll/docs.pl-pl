---
title: /linkresource (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e51f844695985485210a1e4bedfef7ac968326c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linkresource-visual-basic"></a><span data-ttu-id="d5a83-102">/linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a83-102">/linkresource (Visual Basic)</span></span>
<span data-ttu-id="d5a83-103">Tworzy łącze do zasobów zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="d5a83-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5a83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5a83-104">Syntax</span></span>  
  
```  
/linkresource:filename[,identifier[,public|private]]  
' -or-  
/linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5a83-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d5a83-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d5a83-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d5a83-106">Required.</span></span> <span data-ttu-id="d5a83-107">Plik zasobu, aby utworzyć łącze do zestawu.</span><span class="sxs-lookup"><span data-stu-id="d5a83-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="d5a83-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="d5a83-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="d5a83-109">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d5a83-109">Optional.</span></span> <span data-ttu-id="d5a83-110">Nazwa logiczna zasobu.</span><span class="sxs-lookup"><span data-stu-id="d5a83-110">The logical name for the resource.</span></span> <span data-ttu-id="d5a83-111">Nazwa, która jest używana do załadowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="d5a83-111">The name that is used to load the resource.</span></span> <span data-ttu-id="d5a83-112">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="d5a83-112">The default is the name of the file.</span></span> <span data-ttu-id="d5a83-113">Opcjonalnie można określić, czy plik jest publicznych lub prywatnych w manifeście zestawu, na przykład: `/linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="d5a83-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `/linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="d5a83-114">Domyślnie `filename` jest publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d5a83-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5a83-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5a83-115">Remarks</span></span>  
 <span data-ttu-id="d5a83-116">`/linkresource` Opcja nie jest możliwe osadzanie pliku zasobów w pliku wyjściowym; użyj `/resource` opcję, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d5a83-116">The `/linkresource` option does not embed the resource file in the output file; use the `/resource` option to do this.</span></span>  
  
 <span data-ttu-id="d5a83-117">`/linkresource` Opcja wymaga jednego z `/target` opcje inne niż `/target:module`.</span><span class="sxs-lookup"><span data-stu-id="d5a83-117">The `/linkresource` option requires one of the `/target` options other than `/target:module`.</span></span>  
  
 <span data-ttu-id="d5a83-118">Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d5a83-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="d5a83-119">(Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Aby uzyskać dostęp do innych zasobów w czasie wykonywania, należy użyć metody, które zaczynają się od `GetManifestResource` w <xref:System.Reflection.Assembly> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5a83-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="d5a83-120">Nazwa pliku może być dowolnym formacie pliku.</span><span class="sxs-lookup"><span data-stu-id="d5a83-120">The file name can be any file format.</span></span> <span data-ttu-id="d5a83-121">Na przykład można ustawić natywnej biblioteki DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej zestawów i dostępne z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d5a83-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="d5a83-122">Krótka forma z `/linkresource` jest `/linkres`.</span><span class="sxs-lookup"><span data-stu-id="d5a83-122">The short form of `/linkresource` is `/linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5a83-123">`/linkresource` Opcja nie jest dostępny w środowisku programowania Visual Studio; będzie dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d5a83-123">The `/linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5a83-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5a83-124">Example</span></span>  
 <span data-ttu-id="d5a83-125">Poniższy kod kompiluje `In.vb` i łącza do pliku zasobów `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="d5a83-125">The following code compiles `In.vb` and links to resource file `Rf.resource`.</span></span>  
  
```  
vbc /linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5a83-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5a83-126">See Also</span></span>  
 [<span data-ttu-id="d5a83-127">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d5a83-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d5a83-128">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a83-128">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="d5a83-129">/ Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d5a83-129">/resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)  
 [<span data-ttu-id="d5a83-130">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d5a83-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
