---
title: -optimize (opcje kompilatora C#)
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
ms.openlocfilehash: 86c8ebb2d2061085be4c00e8ac95448e1c341161
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212465"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="7084a-102">-optimize (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="7084a-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="7084a-103">**-Zoptymalizować** opcja włącza lub wyłącza wykonywanie optymalizacji przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="7084a-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7084a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7084a-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="7084a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7084a-105">Remarks</span></span>  
 <span data-ttu-id="7084a-106">**-optimize** również informuje środowisko uruchomieniowe języka wspólnego do optymalizacji kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7084a-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="7084a-107">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7084a-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="7084a-108">Określ **-zoptymalizować +** do włączenia optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="7084a-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="7084a-109">Podczas kompilowania modułu używanego przez zespół, należy używać tego samego **-zoptymalizować** ustawienia jak zestawu.</span><span class="sxs-lookup"><span data-stu-id="7084a-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="7084a-110">**-o** jest krótka forma **-zoptymalizować**.</span><span class="sxs-lookup"><span data-stu-id="7084a-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="7084a-111">Istnieje możliwość łączenia **— zoptymalizować** i [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) opcje.</span><span class="sxs-lookup"><span data-stu-id="7084a-111">It is possible to combine the **-optimize** and [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7084a-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7084a-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="7084a-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="7084a-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="7084a-114">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="7084a-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="7084a-115">Modyfikowanie **Optymalizuj kod** właściwości.</span><span class="sxs-lookup"><span data-stu-id="7084a-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="7084a-116">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="7084a-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7084a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="7084a-117">Example</span></span>  
 <span data-ttu-id="7084a-118">Kompiluj `t2.cs` i Włącz optymalizacje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="7084a-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="7084a-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7084a-119">See Also</span></span>  
 [<span data-ttu-id="7084a-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7084a-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="7084a-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7084a-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
