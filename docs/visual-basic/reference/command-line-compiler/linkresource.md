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
ms.openlocfilehash: d92b0d08daf660880b648875c67c3b78069143d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924858"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="75b2f-102">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b2f-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="75b2f-103">Tworzy łącze do zarządzanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="75b2f-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75b2f-104">Syntax</span></span>  
  
```  
-linkresource:filename[,identifier[,public|private]]  
' -or-  
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="75b2f-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="75b2f-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="75b2f-106">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="75b2f-106">Required.</span></span> <span data-ttu-id="75b2f-107">Plik zasobu, który ma zostać połączony z zestawem.</span><span class="sxs-lookup"><span data-stu-id="75b2f-107">The resource file to link to the assembly.</span></span> <span data-ttu-id="75b2f-108">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="75b2f-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="75b2f-109">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="75b2f-109">Optional.</span></span> <span data-ttu-id="75b2f-110">Nazwa logiczna zasobu.</span><span class="sxs-lookup"><span data-stu-id="75b2f-110">The logical name for the resource.</span></span> <span data-ttu-id="75b2f-111">Nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="75b2f-111">The name that is used to load the resource.</span></span> <span data-ttu-id="75b2f-112">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="75b2f-112">The default is the name of the file.</span></span> <span data-ttu-id="75b2f-113">Opcjonalnie można określić, czy plik jest publiczny, czy prywatny w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="75b2f-113">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="75b2f-114">Domyślnie `filename` jest on publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="75b2f-114">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75b2f-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="75b2f-115">Remarks</span></span>  
 <span data-ttu-id="75b2f-116">Opcja nie osadza pliku zasobów w pliku wyjściowym; Użyj opcji, `-resource` aby to zrobić. `-linkresource`</span><span class="sxs-lookup"><span data-stu-id="75b2f-116">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="75b2f-117">Opcja wymaga jednej `-target` z opcji innych niż `-target:module`. `-linkresource`</span><span class="sxs-lookup"><span data-stu-id="75b2f-117">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="75b2f-118">Jeśli `filename` jest .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać <xref:System.Resources> za pomocą elementów członkowskich w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="75b2f-118">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="75b2f-119">(Aby uzyskać więcej informacji, <xref:System.Resources.ResourceManager>Zobacz.) Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć metod, `GetManifestResource` które zaczynają <xref:System.Reflection.Assembly> się od klasy.</span><span class="sxs-lookup"><span data-stu-id="75b2f-119">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="75b2f-120">Nazwa pliku może być dowolnym formatem pliku.</span><span class="sxs-lookup"><span data-stu-id="75b2f-120">The file name can be any file format.</span></span> <span data-ttu-id="75b2f-121">Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="75b2f-121">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="75b2f-122">Krótka forma `-linkresource` to `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="75b2f-122">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75b2f-123">Ta `-linkresource` opcja jest niedostępna w środowisku deweloperskim programu Visual Studio. jest ona dostępna tylko podczas kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="75b2f-123">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75b2f-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="75b2f-124">Example</span></span>  
 <span data-ttu-id="75b2f-125">Poniższy kod kompiluje `in.vb` i łączy się z plikiem `rf.resource`zasobów.</span><span class="sxs-lookup"><span data-stu-id="75b2f-125">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="75b2f-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75b2f-126">See also</span></span>

- [<span data-ttu-id="75b2f-127">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="75b2f-127">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="75b2f-128">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b2f-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="75b2f-129">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75b2f-129">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="75b2f-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="75b2f-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
