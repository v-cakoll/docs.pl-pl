---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: 5f59f1c4c269a52131a324bbd2bfbe817ab794a4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197088"
---
# <a name="-langversion-visual-basic"></a><span data-ttu-id="637d6-102">-langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="637d6-102">-langversion (Visual Basic)</span></span>
<span data-ttu-id="637d6-103">Powoduje, że kompilator akceptuje tylko składnię, która jest uwzględniona w określonej Visual Basic wersji językowej.</span><span class="sxs-lookup"><span data-stu-id="637d6-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="637d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="637d6-104">Syntax</span></span>  
  
```console  
-langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="637d6-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="637d6-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="637d6-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="637d6-106">Required.</span></span> <span data-ttu-id="637d6-107">Wersja języka do użycia podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="637d6-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="637d6-108">Akceptowane wartości to `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` i `latest`.</span><span class="sxs-lookup"><span data-stu-id="637d6-108">Accepted values are `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` and `latest`.</span></span>

 <span data-ttu-id="637d6-109">Wszystkie liczby całkowite można także określić przy użyciu `.0` jako wersji pomocniczej, na przykład `11.0`.</span><span class="sxs-lookup"><span data-stu-id="637d6-109">Any of the whole numbers may also be specified using `.0` as the minor version, for example, `11.0`.</span></span>

 <span data-ttu-id="637d6-110">Możesz wyświetlić listę wszystkich możliwych wartości, określając `-langversion:?` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="637d6-110">You can see the list of all possible values by specifying `-langversion:?` on the command line.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="637d6-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="637d6-111">Remarks</span></span>  
 <span data-ttu-id="637d6-112">Opcja `-langversion` określa składnię akceptowaną przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="637d6-112">The `-langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="637d6-113">Na przykład jeśli określisz, że wersja językowa to 9,0, kompilator generuje błędy dla składni, która jest prawidłowa tylko w wersji 10,0 lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="637d6-113">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="637d6-114">Tej opcji można użyć podczas tworzenia aplikacji przeznaczonych dla różnych wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="637d6-114">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="637d6-115">Na przykład jeśli jesteś celem .NET Framework 3,5, możesz użyć tej opcji, aby upewnić się, że nie używasz składni z wersji językowej 10,0.</span><span class="sxs-lookup"><span data-stu-id="637d6-115">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="637d6-116">Można ustawić wartość `-langversion` bezpośrednio tylko przy użyciu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="637d6-116">You can set `-langversion` directly only by using the command line.</span></span> <span data-ttu-id="637d6-117">Aby uzyskać więcej informacji, zobacz [Określanie konkretnej wersji .NET Framework](/visualstudio/ide/visual-studio-multi-targeting-overview).</span><span class="sxs-lookup"><span data-stu-id="637d6-117">For more information, see [Targeting a Specific .NET Framework Version](/visualstudio/ide/visual-studio-multi-targeting-overview).</span></span>  
  
## <a name="example"></a><span data-ttu-id="637d6-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="637d6-118">Example</span></span>  
 <span data-ttu-id="637d6-119">Poniższy kod kompiluje `sample.vb` dla Visual Basic 9,0.</span><span class="sxs-lookup"><span data-stu-id="637d6-119">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="637d6-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="637d6-120">See also</span></span>

- [<span data-ttu-id="637d6-121">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="637d6-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="637d6-122">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="637d6-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="637d6-123">Określanie konkretnej wersji programu .NET Framework jako docelowej</span><span class="sxs-lookup"><span data-stu-id="637d6-123">Targeting a Specific .NET Framework Version</span></span>](/visualstudio/ide/visual-studio-multi-targeting-overview)
