---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: e36e9187ab8c9c2b4950a66ff8ff3fc93adbd9c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58821481"
---
# <a name="-win32icon"></a><span data-ttu-id="7b84e-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="7b84e-102">-win32icon</span></span>
<span data-ttu-id="7b84e-103">Wstawia plik .ico, w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="7b84e-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="7b84e-104">Ten plik .ico, który reprezentuje plik wyjściowy w **Eksploratora plików**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b84e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b84e-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="7b84e-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="7b84e-106">Arguments</span></span>  
  
|<span data-ttu-id="7b84e-107">Termin</span><span class="sxs-lookup"><span data-stu-id="7b84e-107">Term</span></span>|<span data-ttu-id="7b84e-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="7b84e-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="7b84e-109">Plik .ico, należy dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="7b84e-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="7b84e-110">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="7b84e-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b84e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b84e-111">Remarks</span></span>  
 <span data-ttu-id="7b84e-112">Plik .ico, który można utworzyć przy użyciu kompilatora zasobów Windows firmy Microsoft (RC).</span><span class="sxs-lookup"><span data-stu-id="7b84e-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="7b84e-113">Kompilator zasobów jest wywoływane, gdy kompilujesz program Visual C++; plik .ico, który jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="7b84e-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="7b84e-114">`-win32icon` i `-win32resource` opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="7b84e-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="7b84e-115">Zobacz [- linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów, lub [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) można dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="7b84e-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="7b84e-116">Zobacz [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować plik res.</span><span class="sxs-lookup"><span data-stu-id="7b84e-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="7b84e-117">Aby ustawić - win32icon w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7b84e-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="7b84e-118">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="7b84e-119">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="7b84e-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="7b84e-120">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="7b84e-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="7b84e-121">3.  Zmodyfikuj wartość w **ikonę** pole.</span><span class="sxs-lookup"><span data-stu-id="7b84e-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7b84e-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="7b84e-122">Example</span></span>  
 <span data-ttu-id="7b84e-123">Poniższy kod kompiluje `In.vb` i dołącza plik .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="7b84e-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="7b84e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b84e-124">See also</span></span>

- [<span data-ttu-id="7b84e-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7b84e-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="7b84e-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="7b84e-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
