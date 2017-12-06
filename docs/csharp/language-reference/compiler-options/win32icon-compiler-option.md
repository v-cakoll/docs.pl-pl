---
title: -win32icon (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 356502b8528e22a5b5ff9a28a3f82d5f9c0a72f9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="win32icon-c-compiler-options"></a><span data-ttu-id="42d46-102">/win32icon (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="42d46-102">/win32icon (C# Compiler Options)</span></span>
<span data-ttu-id="42d46-103">**/Win32icon** opcja Wstawia plik .ico w pliku danych wyjściowych, który zawiera plik wyjściowy żądanego wyglądu w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="42d46-103">The **/win32icon** option inserts an .ico file in the output file, which gives the output file the desired appearance in the File Explorer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42d46-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="42d46-104">Syntax</span></span>  
  
```console  
/win32icon:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="42d46-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="42d46-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="42d46-106">Plik .ico, który chcesz dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="42d46-106">The .ico file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42d46-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="42d46-107">Remarks</span></span>  
 <span data-ttu-id="42d46-108">Plik .ico mogą być tworzone za pomocą [kompilator zasobów](https://msdn.microsoft.com/library/aa381042.aspx).</span><span class="sxs-lookup"><span data-stu-id="42d46-108">An .ico file can be created with the [Resource Compiler](https://msdn.microsoft.com/library/aa381042.aspx).</span></span> <span data-ttu-id="42d46-109">Kompilator zasobów jest wywoływane, gdy kompilacja programu Visual C++; plik .rc jest utworzony plik .ico.</span><span class="sxs-lookup"><span data-stu-id="42d46-109">The Resource Compiler is invoked when you compile a Visual C++ program; an .ico file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="42d46-110">Zobacz [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (do odwołania) lub [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (Aby dołączyć) plik zasobu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42d46-110">See [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (to reference) or [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span> <span data-ttu-id="42d46-111">Zobacz [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) można zaimportować pliku .res.</span><span class="sxs-lookup"><span data-stu-id="42d46-111">See [/win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) to import a .res file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="42d46-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="42d46-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="42d46-113">Otwórz projekt **właściwości** stron.</span><span class="sxs-lookup"><span data-stu-id="42d46-113">Open the project's **Properties** pages.</span></span>  
  
2.  <span data-ttu-id="42d46-114">Kliknij przycisk **aplikacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="42d46-114">Click the **Application** property page.</span></span>  
  
3.  <span data-ttu-id="42d46-115">Modyfikowanie **ikona aplikacji** właściwości.</span><span class="sxs-lookup"><span data-stu-id="42d46-115">Modify the **Application icon** property.</span></span>  
  
 <span data-ttu-id="42d46-116">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span><span class="sxs-lookup"><span data-stu-id="42d46-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="42d46-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="42d46-117">Example</span></span>  
 <span data-ttu-id="42d46-118">Kompiluj `in.cs` i Dołącz plik .ico `rf.ico` do produkcji `in.exe`:</span><span class="sxs-lookup"><span data-stu-id="42d46-118">Compile `in.cs` and attach an .ico file `rf.ico` to produce `in.exe`:</span></span>  
  
```console  
csc /win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="42d46-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="42d46-119">See Also</span></span>  
 [<span data-ttu-id="42d46-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="42d46-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="42d46-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="42d46-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
