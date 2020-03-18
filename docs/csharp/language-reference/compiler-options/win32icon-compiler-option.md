---
title: -win32icon (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606274"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="6e32a-102">-win32icon (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6e32a-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="6e32a-103">Opcja **-win32icon** wstawia plik .ico w pliku wyjściowym, co nadaje plikowi wyjściowemu pożądany wygląd w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="6e32a-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e32a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6e32a-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e32a-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="6e32a-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="6e32a-106">Plik .ico, który chcesz dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="6e32a-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e32a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6e32a-107">Remarks</span></span>  
 <span data-ttu-id="6e32a-108">Plik .ico można utworzyć za pomocą [kompilatora zasobów](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="6e32a-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="6e32a-109">Kompilator zasobów jest wywoływany podczas kompilowania programu Visual C++; plik .ico jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="6e32a-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="6e32a-110">Zobacz [-linkresource](./linkresource-compiler-option.md) (do odwołania) lub [-resource](./resource-compiler-option.md) (do dołączenia) plik zasobów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6e32a-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="6e32a-111">Zobacz [-win32res,](./win32res-compiler-option.md) aby zaimportować plik .res.</span><span class="sxs-lookup"><span data-stu-id="6e32a-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6e32a-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6e32a-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6e32a-113">Otwórz strony **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="6e32a-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="6e32a-114">Kliknij stronę **właściwości Application.**</span><span class="sxs-lookup"><span data-stu-id="6e32a-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="6e32a-115">Zmodyfikuj właściwość **Ikona aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="6e32a-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="6e32a-116">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="6e32a-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e32a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6e32a-117">Example</span></span>  
 <span data-ttu-id="6e32a-118">Skompiluj `in.cs` i dołącz `rf.ico` plik `in.exe`.ico do produkcji:</span><span class="sxs-lookup"><span data-stu-id="6e32a-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e32a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e32a-119">See also</span></span>

- [<span data-ttu-id="6e32a-120">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="6e32a-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6e32a-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="6e32a-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
