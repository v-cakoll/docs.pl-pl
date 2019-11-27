---
title: -resource
ms.date: 03/13/2018
helpviewer_keywords:
- /resource compiler option [Visual Basic]
- -resource compiler option [Visual Basic]
- /res compiler option [Visual Basic]
- res compiler option [Visual Basic]
- -res compiler option [Visual Basic]
- resource compiler option [Visual Basic]
ms.assetid: eee2f227-91f2-4f2b-a9d6-1c51c5320858
ms.openlocfilehash: a781d543dd32ffb3d0ac0b11c544dbfd8cd5d806
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348567"
---
# <a name="-resource-visual-basic"></a><span data-ttu-id="db6d0-102">-Resource (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6d0-102">-resource (Visual Basic)</span></span>
<span data-ttu-id="db6d0-103">Osadza zasób zarządzany w zestawie.</span><span class="sxs-lookup"><span data-stu-id="db6d0-103">Embeds a managed resource in an assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6d0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db6d0-104">Syntax</span></span>  
  
```console  
-resource:filename[,identifier[,public|private]]  
```

<span data-ttu-id="db6d0-105">lub</span><span class="sxs-lookup"><span data-stu-id="db6d0-105">or</span></span>  

```console
-res:filename[,identifier[,public|private]]  
```  
  
## <a name="arguments"></a><span data-ttu-id="db6d0-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="db6d0-106">Arguments</span></span>  
  
|<span data-ttu-id="db6d0-107">Termin</span><span class="sxs-lookup"><span data-stu-id="db6d0-107">Term</span></span>|<span data-ttu-id="db6d0-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="db6d0-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="db6d0-109">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="db6d0-109">Required.</span></span> <span data-ttu-id="db6d0-110">Nazwa pliku zasobu do osadzenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="db6d0-110">The name of the resource file to embed in the output file.</span></span> <span data-ttu-id="db6d0-111">Domyślnie `filename` jest publiczna w zestawie.</span><span class="sxs-lookup"><span data-stu-id="db6d0-111">By default, `filename` is public in the assembly.</span></span> <span data-ttu-id="db6d0-112">Nazwa pliku należy ująć w cudzysłów (""), jeśli zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="db6d0-112">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
|`identifier`|<span data-ttu-id="db6d0-113">Opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="db6d0-113">Optional.</span></span> <span data-ttu-id="db6d0-114">Nazwa logiczna zasobu; Nazwa użyta do załadowania.</span><span class="sxs-lookup"><span data-stu-id="db6d0-114">The logical name for the resource; the name used to load it.</span></span> <span data-ttu-id="db6d0-115">Wartość domyślna to nazwa pliku.</span><span class="sxs-lookup"><span data-stu-id="db6d0-115">The default is the name of the file.</span></span> <span data-ttu-id="db6d0-116">Opcjonalnie można określić, czy zasób jest publiczny, czy prywatny w manifeście zestawu, tak jak w przypadku następujących: `-res:filename.res, myname.res, public`</span><span class="sxs-lookup"><span data-stu-id="db6d0-116">Optionally, you can specify whether the resource is public or private in the assembly manifest, as with the following: `-res:filename.res, myname.res, public`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db6d0-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="db6d0-117">Remarks</span></span>  
 <span data-ttu-id="db6d0-118">Użyj `-linkresource`, aby połączyć zasób z zestawem bez umieszczania pliku zasobów w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="db6d0-118">Use `-linkresource` to link a resource to an assembly without placing the resource file in the output file.</span></span>  
  
 <span data-ttu-id="db6d0-119">Jeśli `filename` to .NET Framework utworzony plik zasobów, na przykład przez [Resgen. exe (Generator plików zasobów)](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, dostęp do niego można uzyskać za pomocą elementów członkowskich w przestrzeni nazw <xref:System.Resources> (zobacz <xref:System.Resources.ResourceManager>, aby uzyskać więcej informacji).</span><span class="sxs-lookup"><span data-stu-id="db6d0-119">If `filename` is a .NET Framework resource file created, for example, by the [Resgen.exe (Resource File Generator)](../../../framework/tools/resgen-exe-resource-file-generator.md) or in the development environment, it can be accessed with members in the <xref:System.Resources> namespace (see <xref:System.Resources.ResourceManager> for more information).</span></span> <span data-ttu-id="db6d0-120">Aby uzyskać dostęp do wszystkich innych zasobów w czasie wykonywania, należy użyć jednej z następujących metod: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>lub <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span><span class="sxs-lookup"><span data-stu-id="db6d0-120">To access all other resources at run time, use one of the following methods: <xref:System.Reflection.Assembly.GetManifestResourceInfo%2A>, <xref:System.Reflection.Assembly.GetManifestResourceNames%2A>, or <xref:System.Reflection.Assembly.GetManifestResourceStream%2A>.</span></span>  
  
 <span data-ttu-id="db6d0-121">Krótka forma `-resource` jest `-res`.</span><span class="sxs-lookup"><span data-stu-id="db6d0-121">The short form of `-resource` is `-res`.</span></span>  
  
 <span data-ttu-id="db6d0-122">Aby uzyskać informacje na temat sposobu ustawiania `-resource` w środowisku IDE programu Visual Studio, zobacz [Zarządzanie zasobami aplikacji (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="db6d0-122">For information about how to set `-resource` in the Visual Studio IDE, see [Managing Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db6d0-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="db6d0-123">Example</span></span>  
 <span data-ttu-id="db6d0-124">Poniższy kod kompiluje `In.vb` i dołącza `Rf.resource`pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="db6d0-124">The following code compiles `In.vb` and attaches resource file `Rf.resource`.</span></span>  
  
```console
vbc -res:rf.resource in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="db6d0-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db6d0-125">See also</span></span>

- [<span data-ttu-id="db6d0-126">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db6d0-126">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="db6d0-127">-win32resource</span><span class="sxs-lookup"><span data-stu-id="db6d0-127">-win32resource</span></span>](../../../visual-basic/reference/command-line-compiler/win32resource.md)
- [<span data-ttu-id="db6d0-128">-linkresource — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6d0-128">-linkresource (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/linkresource.md)
- [<span data-ttu-id="db6d0-129">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db6d0-129">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="db6d0-130">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="db6d0-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
