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
ms.openlocfilehash: ab5593455546e65bdd760d9e60532031dc1f12a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654440"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="72516-102">-zasobów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72516-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="72516-103">Osadza zarządzanego zasobu w zestawie.</span><span class="sxs-lookup"><span data-stu-id="72516-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72516-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72516-104">Syntax</span></span>  
  
```  
-resource:filename[,identifier[,public|private]]  
' -or-  
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="72516-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="72516-105">Arguments</span></span>  
  
|<span data-ttu-id="72516-106">Termin</span><span class="sxs-lookup"><span data-stu-id="72516-106">Term</span></span>|<span data-ttu-id="72516-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="72516-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="72516-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="72516-108">Required.</span></span> <span data-ttu-id="72516-109">Nazwa pliku zasobu do osadzenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="72516-109">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="72516-110">Domyślnie `filename` jest publiczny w zestawie.</span><span class="sxs-lookup"><span data-stu-id="72516-110">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="72516-111">Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="72516-111">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="72516-112">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="72516-112">Optional.</span></span> <span data-ttu-id="72516-113">Nazwa logiczna zasobu; Nazwa używana go załadować.</span><span class="sxs-lookup"><span data-stu-id="72516-113">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="72516-114">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="72516-114">The default is the name of the file.</span></span> <span data-ttu-id="72516-115">Opcjonalnie można określić, czy zasób jest publicznych lub prywatnych w manifeście zestawu następującym kodem: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="72516-115">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72516-116">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72516-116">Remarks</span></span>  
 <span data-ttu-id="72516-117">Użyj `-linkresource` połączyć zasób zestawu bez wprowadzania do pliku zasobów w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="72516-117">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="72516-118">Jeśli `filename` jest [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] zasobów utworzonym pliku, na przykład przez [Resgen.exe (Generator pliku zasobów)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) lub w środowisku programistycznym, jest dostępny z elementami członkowskimi w <xref:System.Resources> przestrzeni nazw (zobacz <xref:System.Resources.ResourceManager> Aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="72516-118">If `filename` is a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file created, for example, by the [Resgen.exe (Resource File Generator)](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="72516-119">Aby uzyskać dostęp do innych zasobów w czasie wykonywania, użyj jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="72516-119">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="72516-120">Krótka forma z `-resource` jest `-res`.</span><span class="sxs-lookup"><span data-stu-id="72516-120">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="72516-121">Aby uzyskać informacje dotyczące sposobu konfigurowania `-resource` w programie Visual Studio IDE, zobacz [zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="72516-121">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="72516-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="72516-122">Example</span></span>  
 <span data-ttu-id="72516-123">Poniższy kod kompiluje `In.vb` i dołącza plik zasobu `Rf.resource`.</span><span class="sxs-lookup"><span data-stu-id="72516-123">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="72516-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72516-124">See Also</span></span>  
 [<span data-ttu-id="72516-125">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72516-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="72516-126">-win32resource</span><span class="sxs-lookup"><span data-stu-id="72516-126">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)  
 [<span data-ttu-id="72516-127">-linkresource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72516-127">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)  
 [<span data-ttu-id="72516-128">-docelowego (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72516-128">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="72516-129">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="72516-129">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
