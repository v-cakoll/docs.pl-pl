---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 67366e13e4dceea4772d0730222413cb25b4e8b7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352389"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="0f56c-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f56c-102">-out (Visual Basic)</span></span>
<span data-ttu-id="0f56c-103">Określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="0f56c-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f56c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0f56c-104">Syntax</span></span>  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0f56c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0f56c-105">Arguments</span></span>  
  
|<span data-ttu-id="0f56c-106">Termin</span><span class="sxs-lookup"><span data-stu-id="0f56c-106">Term</span></span>|<span data-ttu-id="0f56c-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="0f56c-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="0f56c-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0f56c-108">Required.</span></span> <span data-ttu-id="0f56c-109">Nazwa pliku wyjściowego tworzonego przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="0f56c-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="0f56c-110">Jeśli nazwa pliku zawiera spację, należy ująć ją w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="0f56c-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f56c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0f56c-111">Remarks</span></span>  
 <span data-ttu-id="0f56c-112">Określ pełną nazwę i rozszerzenie pliku do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="0f56c-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="0f56c-113">W przeciwnym razie plik. exe przyjmuje swoją nazwę z pliku kodu źródłowego zawierającego procedurę `Sub Main`, a plik. dll przyjmuje swoją nazwę z pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0f56c-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="0f56c-114">Jeśli określisz nazwę pliku bez rozszerzenia exe lub dll, kompilator automatycznie doda rozszerzenie dla Ciebie, w zależności od wartości określonej dla opcji kompilatora `-target`.</span><span class="sxs-lookup"><span data-stu-id="0f56c-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="0f56c-115">Aby skonfigurować w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0f56c-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0f56c-116">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="0f56c-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0f56c-117">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0f56c-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0f56c-118">2. Kliknij kartę **aplikacja** .</span><span class="sxs-lookup"><span data-stu-id="0f56c-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="0f56c-119">3. Zmodyfikuj wartość w polu **Nazwa zestawu** .</span><span class="sxs-lookup"><span data-stu-id="0f56c-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0f56c-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0f56c-120">Example</span></span>  
 <span data-ttu-id="0f56c-121">Poniższy kod kompiluje `T2.vb` i tworzy `T2.exe`pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="0f56c-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="0f56c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0f56c-122">See also</span></span>

- [<span data-ttu-id="0f56c-123">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f56c-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0f56c-124">-Target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f56c-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="0f56c-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0f56c-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
