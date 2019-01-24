---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: 05dcaa18d799912d1b92685338a269a050db3f1a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703487"
---
# <a name="-win32resource"></a><span data-ttu-id="0d614-102">-win32resource</span><span class="sxs-lookup"><span data-stu-id="0d614-102">-win32resource</span></span>
<span data-ttu-id="0d614-103">Wstawia plik zasobów Win32 w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="0d614-103">Inserts a Win32 resource file in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d614-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d614-104">Syntax</span></span>  
  
```  
-win32resource:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="0d614-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0d614-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="0d614-106">Nazwa pliku zasobów, aby dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="0d614-106">The name of the resource file to add to your output file.</span></span> <span data-ttu-id="0d614-107">Nazwę pliku należy ująć w znaki cudzysłowu ("") zawiera spację.</span><span class="sxs-lookup"><span data-stu-id="0d614-107">Enclose the file name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d614-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0d614-108">Remarks</span></span>  
 <span data-ttu-id="0d614-109">Plik zasobów Win32 można utworzyć przy użyciu kompilatora zasobów Windows firmy Microsoft (RC).</span><span class="sxs-lookup"><span data-stu-id="0d614-109">You can create a Win32 resource file with the Microsoft Windows Resource Compiler (RC).</span></span>  
  
 <span data-ttu-id="0d614-110">Zasób Win32 może zawierać wersji lub informacje mapy bitowej (ikonę), które pomaga w identyfikacji aplikacji na platformie **Eksploratora plików**.</span><span class="sxs-lookup"><span data-stu-id="0d614-110">A Win32 resource can contain version or bitmap (icon) information that helps identify your application in **File Explorer**.</span></span> <span data-ttu-id="0d614-111">Jeśli nie określisz `-win32resource`, kompilator generuje informacje o wersji, w zależności od używanej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="0d614-111">If you do not specify `-win32resource`, the compiler generates version information based on the assembly version.</span></span> <span data-ttu-id="0d614-112">`-win32resource` i `-win32icon` opcje wykluczają się wzajemnie.</span><span class="sxs-lookup"><span data-stu-id="0d614-112">The `-win32resource` and `-win32icon` options are mutually exclusive.</span></span>  
  
 <span data-ttu-id="0d614-113">Zobacz [- linkresource — (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) do odwołania [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów, lub [-zasobów (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) można dołączyć [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="0d614-113">See [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) to reference a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file, or [-resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) to attach a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] resource file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d614-114">`-win32resource` Opcja nie jest dostępne w środowisku programowania Visual Studio; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="0d614-114">The `-win32resource` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d614-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d614-115">Example</span></span>  
 <span data-ttu-id="0d614-116">Poniższy kod kompiluje `In.vb` i dołącza plik zasobów Win32 `Rf.res`:</span><span class="sxs-lookup"><span data-stu-id="0d614-116">The following code compiles `In.vb` and attaches a Win32 resource file, `Rf.res`:</span></span>  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="0d614-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d614-117">See also</span></span>
- [<span data-ttu-id="0d614-118">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d614-118">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="0d614-119">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0d614-119">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
