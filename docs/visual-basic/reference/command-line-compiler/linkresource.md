---
title: -linkresource — (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /linkresource compiler option [Visual Basic]
- -linkresource compiler option [Visual Basic]
- linkresource compiler option [Visual Basic]
- /linkres compiler option [Visual Basic]
- linkres compiler option [Visual Basic]
- -linkres compiler option [Visual Basic]
ms.assetid: cf4dcad8-17b7-404c-9184-29358aa05b15
ms.openlocfilehash: 5555f83107a40b40c7f05c7cc5729f721727f67c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793942"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="0269d-102">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0269d-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="0269d-103">Tworzy łącze do zarządzanego zasobem.</span><span class="sxs-lookup"><span data-stu-id="0269d-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0269d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0269d-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="0269d-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0269d-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0269d-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0269d-106">Required.</span></span> <span data-ttu-id="0269d-107">Plik zasobów, aby utworzyć łącze do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0269d-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="0269d-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="0269d-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="0269d-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="0269d-109">Optional.</span></span> <span data-ttu-id="0269d-110">Nazwa logiczna zasobu.</span><span class="sxs-lookup"><span data-stu-id="0269d-110">The logical name for the resource.</span></span> <span data-ttu-id="0269d-111">Nazwa która jest używana do ładowania zasobów.</span><span class="sxs-lookup"><span data-stu-id="0269d-111">The name that is used to load the resource.</span></span> <span data-ttu-id="0269d-112">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="0269d-112">The default is the name of the file.</span></span> <span data-ttu-id="0269d-113">Opcjonalnie można określić, czy plik jest publicznych lub prywatnych w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="0269d-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="0269d-114">Domyślnie `filename` jest publiczna w zestawie.</span><span class="sxs-lookup"><span data-stu-id="0269d-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0269d-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0269d-115">Remarks</span></span>  
 <span data-ttu-id="0269d-116">`-linkresource` Opcja nie jest możliwe osadzanie pliku zasobów w pliku wyjściowym; użyj `-resource` opcję, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="0269d-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="0269d-117">`-linkresource` Opcja wymaga jednej z `-target` opcji innych niż `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="0269d-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="0269d-118">Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0269d-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="0269d-119">(Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Dostęp do wszystkich innych zasobów w czasie wykonywania, użyj metody, które zaczynają się od `GetManifestResource` w <xref:System.Reflection.Assembly> klasy.</span><span class="sxs-lookup"><span data-stu-id="0269d-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="0269d-120">Nazwa pliku może być dowolnym formacie pliku.</span><span class="sxs-lookup"><span data-stu-id="0269d-120">The file name can be any file format.</span></span> <span data-ttu-id="0269d-121">Na przykład można wprowadzić natywną DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej i dostępne z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="0269d-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="0269d-122">Krótkiej formy `-linkresource` jest `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="0269d-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0269d-123">`-linkresource` Opcja nie jest dostępna z poziomu środowiska projektowego programu Visual Studio; jest dostępna tylko podczas kompilacji z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="0269d-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0269d-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="0269d-124">Example</span></span>  
 <span data-ttu-id="0269d-125">Poniższy kod kompiluje `in.vb` i łącza do pliku zasobów `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="0269d-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0269d-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0269d-126">See also</span></span>

- [<span data-ttu-id="0269d-127">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0269d-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0269d-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0269d-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="0269d-129">-zasobów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0269d-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="0269d-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0269d-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
