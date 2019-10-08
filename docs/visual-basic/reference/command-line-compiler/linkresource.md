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
ms.openlocfilehash: dee5384696d543442f3280b9fdb535a7d9b6f863
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005487"
---
# <a name="-linkresource-visual-basic"></a><span data-ttu-id="d61b7-102">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61b7-102">-linkresource (Visual Basic)</span></span>
<span data-ttu-id="d61b7-103">Tworzy łącze do zarządzanego zasobu.</span><span class="sxs-lookup"><span data-stu-id="d61b7-103">Creates a link to a managed resource.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d61b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d61b7-104">Syntax</span></span>  
  
```console  
-linkresource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="d61b7-105">lub</span><span class="sxs-lookup"><span data-stu-id="d61b7-105">or</span></span>  

```console
-linkres:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="d61b7-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d61b7-106">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d61b7-107">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="d61b7-107">Required.</span></span> <span data-ttu-id="d61b7-108">Plik zasobu, który ma zostać połączony z zestawem.</span><span class="sxs-lookup"><span data-stu-id="d61b7-108">The resource file to link to the assembly.</span></span> <span data-ttu-id="d61b7-109">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="d61b7-109">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
 `identifier`  
 <span data-ttu-id="d61b7-110">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="d61b7-110">Optional.</span></span> <span data-ttu-id="d61b7-111">Nazwa logiczna zasobu.</span><span class="sxs-lookup"><span data-stu-id="d61b7-111">The logical name for the resource.</span></span> <span data-ttu-id="d61b7-112">Nazwa, która jest używana do ładowania zasobu.</span><span class="sxs-lookup"><span data-stu-id="d61b7-112">The name that is used to load the resource.</span></span> <span data-ttu-id="d61b7-113">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="d61b7-113">The default is the name of the file.</span></span> <span data-ttu-id="d61b7-114">Opcjonalnie można określić, czy plik jest publiczny, czy prywatny w manifeście zestawu, na przykład: `-linkres:filename.res,myname.res,public`.</span><span class="sxs-lookup"><span data-stu-id="d61b7-114">Optionally, you can specify whether the file is public or private in the assembly manifest, for example: `-linkres:filename.res,myname.res,public`.</span></span> <span data-ttu-id="d61b7-115">Domyślnie `filename` jest publiczna w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d61b7-115">By default, `filename` is public in the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d61b7-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d61b7-116">Remarks</span></span>  
 <span data-ttu-id="d61b7-117">Opcja `-linkresource` nie osadza pliku zasobów w pliku wyjściowym; Użyj opcji `-resource`, aby to zrobić.</span><span class="sxs-lookup"><span data-stu-id="d61b7-117">The `-linkresource` option does not embed the resource file in the output file; use the `-resource` option to do this.</span></span>  
  
 <span data-ttu-id="d61b7-118">Opcja `-linkresource` wymaga jednej z opcji `-target` innej niż `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="d61b7-118">The `-linkresource` option requires one of the `-target` options other than `-target:module`.</span></span>  
  
 <span data-ttu-id="d61b7-119">Jeśli `filename` to .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w przestrzeni nazw <xref:System.Resources>.</span><span class="sxs-lookup"><span data-stu-id="d61b7-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace.</span></span> <span data-ttu-id="d61b7-120">(Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager>.) Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć metod, które zaczynają się od `GetManifestResource` w klasie <xref:System.Reflection.Assembly>.</span><span class="sxs-lookup"><span data-stu-id="d61b7-120">(For more information, see <xref:System.Resources.ResourceManager>.) To access all other resources at run time, use the methods that begin with `GetManifestResource` in the <xref:System.Reflection.Assembly> class.</span></span>  
  
 <span data-ttu-id="d61b7-121">Nazwa pliku może być dowolnym formatem pliku.</span><span class="sxs-lookup"><span data-stu-id="d61b7-121">The file name can be any file format.</span></span> <span data-ttu-id="d61b7-122">Można na przykład utworzyć natywną bibliotekę DLL zestawu, tak aby można ją było zainstalować w globalnej pamięci podręcznej zestawów i uzyskać do niej dostęp z kodu zarządzanego w zestawie.</span><span class="sxs-lookup"><span data-stu-id="d61b7-122">For example, you may want to make a native DLL part of the assembly, so that it can be installed into the global assembly cache and accessed from managed code in the assembly.</span></span>  
  
 <span data-ttu-id="d61b7-123">Krótka forma `-linkresource` jest `-linkres`.</span><span class="sxs-lookup"><span data-stu-id="d61b7-123">The short form of `-linkresource` is `-linkres`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d61b7-124">Opcja `-linkresource` nie jest dostępna w środowisku deweloperskim programu Visual Studio. jest on dostępny tylko w przypadku kompilowania z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="d61b7-124">The `-linkresource` option is not available from the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d61b7-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="d61b7-125">Example</span></span>  
 <span data-ttu-id="d61b7-126">Poniższy kod kompiluje `in.vb` i linki do pliku zasobów `rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="d61b7-126">The following code compiles `in.vb` and links to resource file `rf.resource`.</span></span>  
  
```console  
vbc -linkresource:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d61b7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d61b7-127">See also</span></span>

- [<span data-ttu-id="d61b7-128">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d61b7-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d61b7-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61b7-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="d61b7-130">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d61b7-130">-resource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/resource.md)
- [<span data-ttu-id="d61b7-131">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d61b7-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
