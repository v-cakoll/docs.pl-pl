---
title: -zasobów (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a69d0e15f9094860c4c66f3fe0a195a0a609db9
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45510311"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="124dc-102">-zasobów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="124dc-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="124dc-103">Osadza zasobów zarządzanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="124dc-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="124dc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="124dc-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="124dc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="124dc-105">Arguments</span></span>  
  
|<span data-ttu-id="124dc-106">Termin</span><span class="sxs-lookup"><span data-stu-id="124dc-106">Term</span></span>|<span data-ttu-id="124dc-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="124dc-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="124dc-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="124dc-108">Required.</span></span> <span data-ttu-id="124dc-109">Nazwa pliku zasobów do osadzenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="124dc-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="124dc-110">Domyślnie `filename` jest publiczna w zestawie.</span><span class="sxs-lookup"><span data-stu-id="124dc-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="124dc-111">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="124dc-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="124dc-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="124dc-112">Optional.</span></span> <span data-ttu-id="124dc-113">Nazwa logiczna zasobu; Nazwa używana go załadować.</span><span class="sxs-lookup"><span data-stu-id="124dc-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="124dc-114">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="124dc-114">The default is the name of the file.</span></span> <span data-ttu-id="124dc-115">Opcjonalnie można określić, czy zasób jest publicznych lub prywatnych w manifeście zestawu, zgodnie z poniższym kodem: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="124dc-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="124dc-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="124dc-116">Remarks</span></span>  
 <span data-ttu-id="124dc-117">Użyj `-linkresource` połączyć zasoby do zestawu bez pogarszania plik zasobów w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="124dc-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="124dc-118">Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw (patrz <xref:System.Resources.ResourceManager> Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="124dc-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="124dc-119">Dostęp do wszystkich innych zasobów w czasie wykonywania, użyj jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="124dc-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="124dc-120">Krótkiej formy `-resource` jest `-res`.</span><span class="sxs-lookup"><span data-stu-id="124dc-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="124dc-121">Aby uzyskać informacje o sposobie ustawiania `-resource` w programie Visual Studio IDE, zobacz [zasobów zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="124dc-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="124dc-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="124dc-122">Example</span></span>  
 <span data-ttu-id="124dc-123">Poniższy kod kompiluje `In.vb` i dołącza plik zasobów `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="124dc-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="124dc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="124dc-124">See also</span></span>

- [<span data-ttu-id="124dc-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="124dc-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
- [<span data-ttu-id="124dc-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="124dc-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
- [<span data-ttu-id="124dc-127">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="124dc-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
- [<span data-ttu-id="124dc-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="124dc-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
- [<span data-ttu-id="124dc-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="124dc-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
