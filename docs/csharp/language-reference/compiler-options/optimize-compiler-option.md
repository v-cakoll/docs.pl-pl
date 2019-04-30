---
title: -Optymalizuj (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
ms.openlocfilehash: 25a9ee1b27836dfb00dcbc72712ed068639fa2fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662585"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="6eebb-102">-Optymalizuj (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6eebb-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="6eebb-103">**— Optymalizacja** opcja włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="6eebb-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eebb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6eebb-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6eebb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6eebb-105">Remarks</span></span>  
 <span data-ttu-id="6eebb-106">**-Optymalizuj** informacje o tym, środowisko uruchomieniowe języka wspólnego do optymalizacji kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6eebb-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="6eebb-107">Domyślnie są wyłączone optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="6eebb-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="6eebb-108">Określ **— Optymalizacja +** Aby włączyć optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="6eebb-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="6eebb-109">Podczas kompilowania modułu, który będzie używany przez zespół, należy używać tego samego **— Optymalizacja** ustawienia zgodnie z tymi zestawu.</span><span class="sxs-lookup"><span data-stu-id="6eebb-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="6eebb-110">**-o** jest krótka forma **— Optymalizacja**.</span><span class="sxs-lookup"><span data-stu-id="6eebb-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="6eebb-111">Można połączyć **— Optymalizacja** i [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) opcje.</span><span class="sxs-lookup"><span data-stu-id="6eebb-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6eebb-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6eebb-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6eebb-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="6eebb-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="6eebb-114">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eebb-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6eebb-115">Modyfikowanie **Optymalizuj kod** właściwości.</span><span class="sxs-lookup"><span data-stu-id="6eebb-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="6eebb-116">Aby uzyskać informacje na temat sposobu programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="6eebb-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6eebb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="6eebb-117">Example</span></span>  
 <span data-ttu-id="6eebb-118">Skompilować `t2.cs` i włączyć optymalizacje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="6eebb-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="6eebb-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6eebb-119">See also</span></span>

- [<span data-ttu-id="6eebb-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="6eebb-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="6eebb-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="6eebb-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
