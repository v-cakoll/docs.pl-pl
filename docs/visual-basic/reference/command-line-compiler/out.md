---
title: -out (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 5dcf9dc5cc0987e965aba7fd2b8821252e19a655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58815995"
---
# <a name="-out-visual-basic"></a><span data-ttu-id="d30e1-102">-out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d30e1-102">-out (Visual Basic)</span></span>
<span data-ttu-id="d30e1-103">Określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d30e1-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d30e1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d30e1-104">Syntax</span></span>  
  
```  
-out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d30e1-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d30e1-105">Arguments</span></span>  
  
|<span data-ttu-id="d30e1-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d30e1-106">Term</span></span>|<span data-ttu-id="d30e1-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d30e1-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="d30e1-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d30e1-108">Required.</span></span> <span data-ttu-id="d30e1-109">Nazwa pliku wyjściowego, kompilator tworzy.</span><span class="sxs-lookup"><span data-stu-id="d30e1-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="d30e1-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w znaki cudzysłowu ("").</span><span class="sxs-lookup"><span data-stu-id="d30e1-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d30e1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d30e1-111">Remarks</span></span>  
 <span data-ttu-id="d30e1-112">Podaj pełną nazwę i rozszerzenie pliku do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="d30e1-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="d30e1-113">Jeśli tego nie zrobisz, plik .exe przyjmuje nazwy z kodu źródłowego pliku zawierającego `Sub Main` procedury i plik .dll pobiera jego nazwę pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="d30e1-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="d30e1-114">Jeśli określisz nazwę pliku bez rozszerzenia .exe lub .dll, kompilator automatycznie dodaje rozszerzenia, w zależności od wartości określonej dla `-target` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d30e1-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `-target` compiler option.</span></span>  
  
|<span data-ttu-id="d30e1-115">Aby ustawić - out w programie Visual Studio zintegrowanego środowiska programistycznego</span><span class="sxs-lookup"><span data-stu-id="d30e1-115">To set -out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d30e1-116">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d30e1-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d30e1-117">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d30e1-117">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d30e1-118">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="d30e1-118">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="d30e1-119">3.  Zmodyfikuj wartość w **nazwy zestawu** pole.</span><span class="sxs-lookup"><span data-stu-id="d30e1-119">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d30e1-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d30e1-120">Example</span></span>  
 <span data-ttu-id="d30e1-121">Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="d30e1-121">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="d30e1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d30e1-122">See also</span></span>

- [<span data-ttu-id="d30e1-123">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d30e1-123">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d30e1-124">-target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d30e1-124">-target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
- [<span data-ttu-id="d30e1-125">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d30e1-125">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
