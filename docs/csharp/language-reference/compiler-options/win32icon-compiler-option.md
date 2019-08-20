---
title: -win32icon (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606274"
---
# <a name="-win32icon-c-compiler-options"></a><span data-ttu-id="43b2c-102">-win32icon (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="43b2c-102">-win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="43b2c-103">Opcja **-win32icon** wstawia plik. ico w pliku wyjściowym, co daje plikowi wyjściowemu odpowiedni wygląd w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="43b2c-103">The **-win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43b2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43b2c-104">Syntax</span></span>  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="43b2c-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="43b2c-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="43b2c-106">Plik ICO, który ma zostać dodany do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="43b2c-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43b2c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43b2c-107">Remarks</span></span>  
 <span data-ttu-id="43b2c-108">Plik. ico można utworzyć za pomocą [kompilatora zasobów](/windows/desktop/menurc/resource-compiler).</span><span class="sxs-lookup"><span data-stu-id="43b2c-108">An .ico file can be created with the [Resource Compiler](/windows/desktop/menurc/resource-compiler).</span></span> <span data-ttu-id="43b2c-109">Kompilator zasobów jest wywoływany podczas kompilowania programu Visual C++ ; plik. ico jest tworzony na podstawie pliku. rc.</span><span class="sxs-lookup"><span data-stu-id="43b2c-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="43b2c-110">Zobacz [-linkresource —](./linkresource-compiler-option.md) (to Reference) lub [-Resource](./resource-compiler-option.md) (aby dołączyć) .NET Framework plik zasobów.</span><span class="sxs-lookup"><span data-stu-id="43b2c-110">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="43b2c-111">Aby zaimportować plik. res, zobacz temat [-win32res —](./win32res-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="43b2c-111">See [-win32res](./win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="43b2c-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="43b2c-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="43b2c-113">Otwórz strony **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="43b2c-113">Open the project's **Properties** pages.</span></span>  
  
2. <span data-ttu-id="43b2c-114">Kliknij stronę właściwości **aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="43b2c-114">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="43b2c-115">Zmodyfikuj właściwość **ikony aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="43b2c-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="43b2c-116">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="43b2c-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b2c-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="43b2c-117">Example</span></span>  
 <span data-ttu-id="43b2c-118">Kompiluj `in.cs` i Dołącz plik `rf.ico` . ico do produkcji `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="43b2c-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="43b2c-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="43b2c-119">See also</span></span>

- [<span data-ttu-id="43b2c-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="43b2c-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="43b2c-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="43b2c-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
