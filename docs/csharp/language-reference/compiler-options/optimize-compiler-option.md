---
title: -optimize (Opcje kompilatora C#)
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
ms.openlocfilehash: bec99ca582070a99fd8b734ef8a7b9e71d945488
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606601"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="bbac8-102">-optimize (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="bbac8-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="bbac8-103">Opcja **-optimize** włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby zmniejszyć, przyspieszyć i wydajniej sprawić, że plik wyjściowy będzie mniejszy, szybszy i wydajniejszy.</span><span class="sxs-lookup"><span data-stu-id="bbac8-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbac8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bbac8-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="bbac8-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bbac8-105">Remarks</span></span>  
 <span data-ttu-id="bbac8-106">**-optimize** informuje również czas wykonywania języka wspólnego do optymalizacji kodu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="bbac8-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="bbac8-107">Domyślnie optymalizacje są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="bbac8-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="bbac8-108">Określ **-optimize+,** aby włączyć optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="bbac8-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="bbac8-109">Podczas tworzenia modułu, który ma być używany przez zespół, należy użyć tych samych ustawień **optymalizowania,** co ustawienia złożenia.</span><span class="sxs-lookup"><span data-stu-id="bbac8-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="bbac8-110">**-o** jest krótką formą **-optimize**.</span><span class="sxs-lookup"><span data-stu-id="bbac8-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="bbac8-111">Możliwe jest połączenie opcji **-optimize** i [-debug.](./debug-compiler-option.md)</span><span class="sxs-lookup"><span data-stu-id="bbac8-111">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="bbac8-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bbac8-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="bbac8-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="bbac8-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="bbac8-114">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="bbac8-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="bbac8-115">**Zmodyfikuj właściwość Optymalizuj kod.**</span><span class="sxs-lookup"><span data-stu-id="bbac8-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="bbac8-116">Aby uzyskać informacje na temat programowania tej opcji <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="bbac8-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbac8-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="bbac8-117">Example</span></span>  
 <span data-ttu-id="bbac8-118">Skompiluj `t2.cs` i włącz optymalizacje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="bbac8-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="bbac8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bbac8-119">See also</span></span>

- [<span data-ttu-id="bbac8-120">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="bbac8-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="bbac8-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="bbac8-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
