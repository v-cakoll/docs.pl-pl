---
title: -langversion — (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839727"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="f945e-102">-langversion — (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f945e-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="f945e-103">Powoduje, że kompilator akceptuje tylko w przypadku składni, która znajduje się w określonej wersji języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f945e-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f945e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f945e-104">Syntax</span></span>  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="f945e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f945e-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="f945e-106">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="f945e-106">Required.</span></span> <span data-ttu-id="f945e-107">Wersja języka, który ma być używany podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f945e-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="f945e-108">Akceptowane wartości to `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` i `latest`.</span><span class="sxs-lookup"><span data-stu-id="f945e-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="f945e-109">Dowolnej liczby całkowite mogą być również określone przy użyciu `.0` jako wersję pomocniczą, na przykład `11.0`.</span><span class="sxs-lookup"><span data-stu-id="f945e-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="f945e-110">Można wyświetlić listę wszystkich możliwych wartości, określając `-langversion:?` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="f945e-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f945e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f945e-111">Remarks</span></span>  
 <span data-ttu-id="f945e-112">`-langversion` Opcja określa, jakie składni, kompilator akceptuje.</span><span class="sxs-lookup"><span data-stu-id="f945e-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="f945e-113">Na przykład jeśli określisz, że wersja językowa jest 9.0, kompilator generuje błędy składni, która jest prawidłowy tylko w wersji 10.0 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="f945e-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="f945e-114">Można użyć tej opcji, podczas tworzenia aplikacji, że kierują do różnych wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f945e-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="f945e-115">Na przykład jeśli są przeznaczone dla .NET Framework 3.5, można tę opcję, aby upewnić się, że nie używasz składnię języka w wersji 10.0.</span><span class="sxs-lookup"><span data-stu-id="f945e-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="f945e-116">Możesz ustawić `-langversion` bezpośrednio tylko przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="f945e-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="f945e-117">Aby uzyskać więcej informacji, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="f945e-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f945e-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="f945e-118">Example</span></span>  
 <span data-ttu-id="f945e-119">Poniższy kod kompiluje `sample.vb` 9.0 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f945e-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="f945e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f945e-120">See also</span></span>

- [<span data-ttu-id="f945e-121">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f945e-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f945e-122">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f945e-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="f945e-123">Określanie konkretnej wersji programu .NET Framework jako docelowej</span><span class="sxs-lookup"><span data-stu-id="f945e-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
