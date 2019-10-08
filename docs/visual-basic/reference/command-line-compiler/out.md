---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 6b005ac26e3fffad350cb4ce52f7757c9fff2ac1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005335"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="f6bf0-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6bf0-102">-out (Visual Basic)</span></span>
<span data-ttu-id="f6bf0-103">Określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6bf0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6bf0-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="f6bf0-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="f6bf0-105">Arguments</span></span>  
  
|<span data-ttu-id="f6bf0-106">Termin</span><span class="sxs-lookup"><span data-stu-id="f6bf0-106">Term</span></span>|<span data-ttu-id="f6bf0-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="f6bf0-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="f6bf0-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-108">Required.</span></span> <span data-ttu-id="f6bf0-109">Nazwa pliku wyjściowego tworzonego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="f6bf0-110">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="f6bf0-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6bf0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6bf0-111">Remarks</span></span>  
 <span data-ttu-id="f6bf0-112">Określ pełną nazwę i rozszerzenie pliku do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="f6bf0-113">W przeciwnym razie plik. exe przyjmuje swoją nazwę z pliku kodu źródłowego zawierającego procedurę `Sub Main`, a plik. dll przyjmuje swoją nazwę z pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="f6bf0-114">Jeśli określisz nazwę pliku bez rozszerzenia exe lub dll, kompilator automatycznie doda rozszerzenie dla Ciebie, w zależności od wartości określonej dla opcji kompilatora `-target`.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="f6bf0-115">Aby skonfigurować w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f6bf0-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="f6bf0-116">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="f6bf0-117">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="f6bf0-118">2. Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="f6bf0-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="f6bf0-119">3. Zmodyfikuj wartość w polu **Nazwa zestawu** .</span><span class="sxs-lookup"><span data-stu-id="f6bf0-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f6bf0-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="f6bf0-120">Example</span></span>  
 <span data-ttu-id="f6bf0-121">Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="f6bf0-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6bf0-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6bf0-122">See also</span></span>

- [<span data-ttu-id="f6bf0-123">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f6bf0-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="f6bf0-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6bf0-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="f6bf0-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="f6bf0-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
