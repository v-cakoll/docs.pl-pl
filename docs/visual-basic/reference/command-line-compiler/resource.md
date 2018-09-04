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
ms.openlocfilehash: 77c80332e663596244b35fe002218e7bcbaeb46a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523327"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="9e7d0-102">-zasobów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e7d0-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="9e7d0-103">Osadza zasobów zarządzanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e7d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e7d0-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="9e7d0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9e7d0-105">Arguments</span></span>  
  
|<span data-ttu-id="9e7d0-106">Termin</span><span class="sxs-lookup"><span data-stu-id="9e7d0-106">Term</span></span>|<span data-ttu-id="9e7d0-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="9e7d0-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="9e7d0-108">Wymagane.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-108">Required.</span></span> <span data-ttu-id="9e7d0-109">Nazwa pliku zasobów do osadzenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="9e7d0-110">Domyślnie `filename` jest publiczna w zestawie.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="9e7d0-111">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="9e7d0-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-112">Optional.</span></span> <span data-ttu-id="9e7d0-113">Nazwa logiczna zasobu; Nazwa używana go załadować.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="9e7d0-114">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-114">The default is the name of the file.</span></span> <span data-ttu-id="9e7d0-115">Opcjonalnie można określić, czy zasób jest publicznych lub prywatnych w manifeście zestawu, zgodnie z poniższym kodem: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="9e7d0-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e7d0-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e7d0-116">Remarks</span></span>  
 <span data-ttu-id="9e7d0-117">Użyj `-linkresource` połączyć zasoby do zestawu bez pogarszania plik zasobów w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="9e7d0-118">Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw (patrz <xref:System.Resources.ResourceManager> Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="9e7d0-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="9e7d0-119">Dostęp do wszystkich innych zasobów w czasie wykonywania, użyj jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="9e7d0-120">Krótkiej formy `-resource` jest `-res`.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="9e7d0-121">Aby uzyskać informacje o sposobie ustawiania `-resource` w programie Visual Studio IDE, zobacz [zasobów zarządzania aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="9e7d0-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e7d0-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e7d0-122">Example</span></span>  
 <span data-ttu-id="9e7d0-123">Poniższy kod kompiluje `In.vb` i dołącza plik zasobów `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="9e7d0-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="9e7d0-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e7d0-124">See Also</span></span>  
 [<span data-ttu-id="9e7d0-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9e7d0-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="9e7d0-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="9e7d0-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="9e7d0-127">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e7d0-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="9e7d0-128">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9e7d0-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="9e7d0-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="9e7d0-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
