---
title: -win32res (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606199"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="9cb9e-102">-win32res (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="9cb9e-102">-win32res (C# Compiler Options)</span></span>
<span data-ttu-id="9cb9e-103">Opcja **-win32res** wstawia zasób Win32 do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-103">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb9e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9cb9e-104">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="9cb9e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="9cb9e-105">Arguments</span></span>  
 `filename`  
 <span data-ttu-id="9cb9e-106">Plik zasobów, który chcesz dodać do pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-106">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9cb9e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9cb9e-107">Remarks</span></span>  
 <span data-ttu-id="9cb9e-108">Za pomocą [kompilatora zasobów](../../language-reference/compiler-options/resource-compiler-option.md)można utworzyć plik zasobu Win32 .</span><span class="sxs-lookup"><span data-stu-id="9cb9e-108">A Win32 resource file can be created with the [Resource Compiler](../../language-reference/compiler-options/resource-compiler-option.md).</span></span> <span data-ttu-id="9cb9e-109">Kompilator zasobów jest wywoływany podczas kompilacji programów Visual C++; plik .res jest tworzony z pliku .rc.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-109">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="9cb9e-110">Zasób Win32 może zawierać informacje o wersji lub bitmap (ikonie), które mogłyby pomóc w identyfikacji aplikacji w Eksploratorze plików.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-110">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="9cb9e-111">Jeśli nie **określisz -win32res,** kompilator wygeneruje informacje o wersji na podstawie wersji zestawu.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-111">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="9cb9e-112">Zobacz [-linkresource](./linkresource-compiler-option.md) (do odwołania) lub [-resource](./resource-compiler-option.md) (do dołączenia) plik zasobów .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-112">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="9cb9e-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9cb9e-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="9cb9e-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="9cb9e-115">Kliknij stronę **właściwości Application.**</span><span class="sxs-lookup"><span data-stu-id="9cb9e-115">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="9cb9e-116">Kliknij przycisk **Plik zasobu** i wybierz plik przy użyciu pola kombi.</span><span class="sxs-lookup"><span data-stu-id="9cb9e-116">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9cb9e-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="9cb9e-117">Example</span></span>  
 <span data-ttu-id="9cb9e-118">Skompiluj `in.cs` i dołącz plik `rf.res` zasobów `in.exe`Win32 do produkcji:</span><span class="sxs-lookup"><span data-stu-id="9cb9e-118">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="9cb9e-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9cb9e-119">See also</span></span>

- [<span data-ttu-id="9cb9e-120">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="9cb9e-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="9cb9e-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="9cb9e-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
