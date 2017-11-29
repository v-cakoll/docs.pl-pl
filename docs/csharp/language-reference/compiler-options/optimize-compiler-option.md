---
title: -optimize (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d74a338336d5878cb8d6f212076bb9f1eb7ef768
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="optimize-c-compiler-options"></a><span data-ttu-id="e5cbb-102">/optimize (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="e5cbb-102">/optimize (C# Compiler Options)</span></span>
<span data-ttu-id="e5cbb-103">**/ Optimize** opcja włącza lub wyłącza wykonywanie optymalizacji przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-103">The **/optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5cbb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e5cbb-104">Syntax</span></span>  
  
```console  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e5cbb-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e5cbb-105">Remarks</span></span>  
 <span data-ttu-id="e5cbb-106">**/ optimize** również informuje środowisko uruchomieniowe języka wspólnego do optymalizacji kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-106">**/optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="e5cbb-107">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="e5cbb-108">Określ **/ optimize +** do włączenia optymalizacji.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-108">Specify **/optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="e5cbb-109">Podczas kompilowania modułu używanego przez zespół, należy używać tego samego **/ optimize** ustawienia jak zestawu.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-109">When building a module to be used by an assembly, use the same **/optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="e5cbb-110">**/o** jest krótka forma **/ optimize**.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-110">**/o** is the short form of **/optimize**.</span></span>  
  
 <span data-ttu-id="e5cbb-111">Istnieje możliwość łączenia **/ optimize** i [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) opcje.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-111">It is possible to combine the **/optimize** and [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e5cbb-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e5cbb-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="e5cbb-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="e5cbb-114">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="e5cbb-115">Modyfikowanie **Optymalizuj kod** właściwości.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="e5cbb-116">Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span><span class="sxs-lookup"><span data-stu-id="e5cbb-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5cbb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="e5cbb-117">Example</span></span>  
 <span data-ttu-id="e5cbb-118">Kompiluj `t2.cs` i Włącz optymalizacje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="e5cbb-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5cbb-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e5cbb-119">See Also</span></span>  
 [<span data-ttu-id="e5cbb-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="e5cbb-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="e5cbb-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="e5cbb-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
