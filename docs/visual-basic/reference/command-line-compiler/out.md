---
title: /out (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d98a9f3cadc42021c302915cfc5b058b41e11ec6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="out-visual-basic"></a><span data-ttu-id="b4d92-102">/out (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4d92-102">/out (Visual Basic)</span></span>
<span data-ttu-id="b4d92-103">Określa nazwę pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="b4d92-103">Specifies the name of the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d92-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b4d92-104">Syntax</span></span>  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="b4d92-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b4d92-105">Arguments</span></span>  
  
|<span data-ttu-id="b4d92-106">Termin</span><span class="sxs-lookup"><span data-stu-id="b4d92-106">Term</span></span>|<span data-ttu-id="b4d92-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="b4d92-107">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="b4d92-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="b4d92-108">Required.</span></span> <span data-ttu-id="b4d92-109">Nazwa pliku wyjściowego, który tworzy kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b4d92-109">The name of the output file the compiler creates.</span></span> <span data-ttu-id="b4d92-110">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="b4d92-110">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d92-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4d92-111">Remarks</span></span>  
 <span data-ttu-id="b4d92-112">Określ pełną nazwę i rozszerzenie pliku do utworzenia.</span><span class="sxs-lookup"><span data-stu-id="b4d92-112">Specify the full name and extension of the file to create.</span></span> <span data-ttu-id="b4d92-113">Jeśli nie chcesz, plik .exe przyjmuje nazwy z kodu źródłowego pliku zawierającego `Sub Main` procedury i pliku dll pobiera jego nazwa pierwszego pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="b4d92-113">If you do not, the .exe file takes its name from the source-code file containing the `Sub Main` procedure, and the .dll file takes its name from the first source-code file.</span></span>  
  
 <span data-ttu-id="b4d92-114">Określ nazwę pliku bez rozszerzenia .exe lub dll, kompilator automatycznie dodaje rozszerzenia, w zależności od wartości określonej dla `/target` — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="b4d92-114">If you specify a file name without an .exe or .dll extension, the compiler automatically adds the extension for you, depending on the value specified for the `/target` compiler option.</span></span>  
  
|<span data-ttu-id="b4d92-115">Aby ustawić/out w programie Visual Studio zintegrowane środowisko deweloperskie</span><span class="sxs-lookup"><span data-stu-id="b4d92-115">To set /out in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="b4d92-116">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="b4d92-116">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="b4d92-117">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="b4d92-117">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="b4d92-118">Aby uzyskać więcej informacji, zobacz [wprowadzenie do projektanta projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="b4d92-118">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="b4d92-119">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="b4d92-119">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="b4d92-120">3.  Zmodyfikuj wartość w **nazwy zestawu** pole.</span><span class="sxs-lookup"><span data-stu-id="b4d92-120">3.  Modify the value in the **Assembly Name** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b4d92-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="b4d92-121">Example</span></span>  
 <span data-ttu-id="b4d92-122">Poniższy kod kompiluje `T2.vb` i tworzy plik wyjściowy `T2.exe`.</span><span class="sxs-lookup"><span data-stu-id="b4d92-122">The following code compiles `T2.vb` and creates output file `T2.exe`.</span></span>  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4d92-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4d92-123">See Also</span></span>  
 [<span data-ttu-id="b4d92-124">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b4d92-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="b4d92-125">/ TARGET (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4d92-125">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="b4d92-126">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="b4d92-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
