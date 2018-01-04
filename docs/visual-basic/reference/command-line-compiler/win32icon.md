---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4fc5210d2dcf30d9c4603b67b890c78510af1338
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="win32icon"></a><span data-ttu-id="445e3-102">/win32icon</span><span class="sxs-lookup"><span data-stu-id="445e3-102">/win32icon</span></span>
<span data-ttu-id="445e3-103">Wstawia plik .ico w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="445e3-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="445e3-104">Ten plik .ico reprezentuje plik wyjściowy w **Eksploratora plików**.</span><span class="sxs-lookup"><span data-stu-id="445e3-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="445e3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="445e3-105">Syntax</span></span>  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="445e3-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="445e3-106">Arguments</span></span>  
  
|<span data-ttu-id="445e3-107">Termin</span><span class="sxs-lookup"><span data-stu-id="445e3-107">Term</span></span>|<span data-ttu-id="445e3-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="445e3-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="445e3-109">Plik .ico, aby dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="445e3-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="445e3-110">Nazwę pliku należy ująć w cudzysłów ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="445e3-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="445e3-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="445e3-111">Remarks</span></span>  
 <span data-ttu-id="445e3-112">Można utworzyć plik .ico z kompilatora zasobów systemu Windows (RC) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="445e3-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="445e3-113">Kompilator zasobów jest wywoływane, gdy kompilacja programu Visual C++; plik .rc jest utworzony plik .ico.</span><span class="sxs-lookup"><span data-stu-id="445e3-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="445e3-114">`/win32icon` i `/win32resource` wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="445e3-114">The `/win32icon` and `/win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="445e3-115">Zobacz [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu lub [/Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobu.</span><span class="sxs-lookup"><span data-stu-id="445e3-115">See [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="445e3-116">Zobacz [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować pliku .res.</span><span class="sxs-lookup"><span data-stu-id="445e3-116">See [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="445e3-117">Aby ustawić/win32icon w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="445e3-117">To set /win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="445e3-118">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="445e3-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="445e3-119">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="445e3-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="445e3-120">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="445e3-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="445e3-121">3.  Zmodyfikuj wartość w **ikona** pole.</span><span class="sxs-lookup"><span data-stu-id="445e3-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="445e3-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="445e3-122">Example</span></span>  
 <span data-ttu-id="445e3-123">Poniższy kod kompiluje `In.vb` i dołącza plik .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="445e3-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="445e3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="445e3-124">See Also</span></span>  
 [<span data-ttu-id="445e3-125">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="445e3-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="445e3-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="445e3-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
