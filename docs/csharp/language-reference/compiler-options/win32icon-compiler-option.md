---
title: -win32icon (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45588610"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="d5165-102">-win32icon (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d5165-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="d5165-103">**-Win32icon** opcja Wstawia plik .ico, w pliku danych wyjściowych, który nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="d5165-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5165-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5165-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="d5165-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d5165-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="d5165-106">Plik .ico, który chcesz dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="d5165-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5165-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5165-107">Remarks</span></span>  
 <span data-ttu-id="d5165-108">Plik .ico, mogą być tworzone za pomocą [kompilator zasobów](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="d5165-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="d5165-109">Kompilator zasobów jest wywoływane, gdy kompilujesz program Visual C++; plik .ico, który jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="d5165-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="d5165-110">Zobacz [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plikiem zasobów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d5165-110">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="d5165-111">Zobacz [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) można zaimportować plik res.</span><span class="sxs-lookup"><span data-stu-id="d5165-111">See [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="d5165-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d5165-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="d5165-113">Otwórz projekt **właściwości** stron.</span><span class="sxs-lookup"><span data-stu-id="d5165-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="d5165-114">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5165-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="d5165-115">Modyfikowanie **ikony aplikacji** właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5165-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="d5165-116">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5165-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5165-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5165-117">Example</span></span>  
 <span data-ttu-id="d5165-118">Skompilować `in.cs` i dołączyć plik .ico `rf.ico` do produkcji `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="d5165-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5165-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5165-119">See Also</span></span>  

- [<span data-ttu-id="d5165-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d5165-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="d5165-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="d5165-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
