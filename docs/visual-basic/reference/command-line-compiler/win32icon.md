---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: afc35578f362f4a72a40fdb3d87406a8795cb59d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194868"
---
# <a name="-win32icon"></a><span data-ttu-id="3e1b5-102">-win32icon</span><span class="sxs-lookup"><span data-stu-id="3e1b5-102">-win32icon</span></span>
<span data-ttu-id="3e1b5-103">Wstawia plik .ico, w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-103">Inserts an .ico file in the output file.</span></span> <span data-ttu-id="3e1b5-104">Ten plik .ico, który reprezentuje plik wyjściowy w **Eksploratora plików**.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-104">This .ico file represents the output file in **File Explorer**.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e1b5-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e1b5-105">Syntax</span></span>  
  
```  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="3e1b5-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3e1b5-106">Arguments</span></span>  
  
|<span data-ttu-id="3e1b5-107">Termin</span><span class="sxs-lookup"><span data-stu-id="3e1b5-107">Term</span></span>|<span data-ttu-id="3e1b5-108">Definicja</span><span class="sxs-lookup"><span data-stu-id="3e1b5-108">Definition</span></span>|  
|---|---|  
|`filename`|<span data-ttu-id="3e1b5-109">Plik .ico, należy dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-109">The .ico file to add to your output file.</span></span> <span data-ttu-id="3e1b5-110">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-110">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e1b5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e1b5-111">Remarks</span></span>  
 <span data-ttu-id="3e1b5-112">Plik .ico, który można utworzyć przy użyciu kompilatora zasobów Windows firmy Microsoft (RC).</span><span class="sxs-lookup"><span data-stu-id="3e1b5-112">You can create an .ico file with the Microsoft Windows Resource Compiler (RC).</span></span> <span data-ttu-id="3e1b5-113">Kompilator zasobów jest wywoływane, gdy kompilujesz program Visual C++; plik .ico, który jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-113">The resource compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span> <span data-ttu-id="3e1b5-114">`-win32icon` i `-win32resource` opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-114">The `-win32icon` and `-win32resource` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="3e1b5-115">Zobacz [- linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów, lub [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) można dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-115">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span> <span data-ttu-id="3e1b5-116">Zobacz [-win32resource —](../../../visual-basic/reference/command-line-compiler/win32resource.md) można zaimportować plik res.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-116">See [-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) to import a .res file.</span></span>  
  
|<span data-ttu-id="3e1b5-117">Aby ustawić - win32icon w środowisku IDE programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e1b5-117">To set -win32icon in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="3e1b5-118">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="3e1b5-119">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="3e1b5-120">2.  Kliknij przycisk **aplikacji** kartę.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-120">2.  Click the **Application** tab.</span></span><br /><span data-ttu-id="3e1b5-121">3.  Zmodyfikuj wartość w **ikonę** pole.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-121">3.  Modify the value in the **Icon** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="3e1b5-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e1b5-122">Example</span></span>  
 <span data-ttu-id="3e1b5-123">Poniższy kod kompiluje `In.vb` i dołącza plik .ico `Rf.ico`.</span><span class="sxs-lookup"><span data-stu-id="3e1b5-123">The following code compiles `In.vb` and attaches an .ico file, `Rf.ico`.</span></span>  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e1b5-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e1b5-124">See Also</span></span>  
 [<span data-ttu-id="3e1b5-125">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e1b5-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="3e1b5-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="3e1b5-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
