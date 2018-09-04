---
title: -win32res (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 96b0b089843495d35a54db43018688dbb4ffba2b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507513"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="72f18-102">-win32res (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="72f18-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="72f18-103">**-Win32res** Opcja wstawia zasób Win32 w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="72f18-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72f18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72f18-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="72f18-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="72f18-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="72f18-106">Plik zasobów, który chcesz dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="72f18-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72f18-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72f18-107">Remarks</span></span>  
 <span data-ttu-id="72f18-108">Plik zasobów Win32 mogą być tworzone za pomocą [kompilator zasobów](../../language-reference/compiler-options/resource-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="72f18-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="72f18-109">Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="72f18-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="72f18-110">Zasób Win32 może zawierać wersji lub informacje mapy bitowej (ikonę), które może pomóc zidentyfikować aplikację w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="72f18-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="72f18-111">Jeśli nie określisz **-win32res**, kompilator wygeneruje informacje o wersji, w zależności od używanej wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="72f18-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="72f18-112">Zobacz [- linkresource —](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plikiem zasobów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="72f18-112">See [-linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="72f18-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="72f18-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="72f18-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="72f18-114">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="72f18-115">Kliknij przycisk **aplikacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="72f18-115">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="72f18-116">Kliknij pozycję **pliku zasobów** przycisku i wybierz plik za pomocą pola kombi.</span><span class="sxs-lookup"><span data-stu-id="72f18-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72f18-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="72f18-117">Example</span></span>  
 <span data-ttu-id="72f18-118">Skompilować `in.cs` i dołączyć plik zasobów Win32 `rf.res` do produkcji `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="72f18-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="72f18-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72f18-119">See Also</span></span>  

- [<span data-ttu-id="72f18-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="72f18-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="72f18-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="72f18-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
