---
title: -Optymalizuj (C# opcje kompilatora)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606601"
---
# <a name="-optimize-c-compiler-options"></a><span data-ttu-id="aa325-102">-Optymalizuj (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="aa325-102">-optimize (C# Compiler Options)</span></span>
<span data-ttu-id="aa325-103">Opcja **-Optimize** włącza lub wyłącza optymalizacje wykonywane przez kompilator, aby plik wyjściowy był mniejszy, szybszy i bardziej wydajny.</span><span class="sxs-lookup"><span data-stu-id="aa325-103">The **-optimize** option enables or disables optimizations performed by the compiler to make your output file smaller, faster, and more efficient.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="aa325-104">Syntax</span></span>  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="aa325-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aa325-105">Remarks</span></span>  
 <span data-ttu-id="aa325-106">**-Optymalizuj** również informuje środowisko uruchomieniowe języka wspólnego, aby zoptymalizować kod w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="aa325-106">**-optimize** also tells the common language runtime to optimize code at runtime.</span></span>  
  
 <span data-ttu-id="aa325-107">Optymalizacje są domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="aa325-107">By default, optimizations are disabled.</span></span> <span data-ttu-id="aa325-108">Określ **-Optimize +** , aby włączyć optymalizacje.</span><span class="sxs-lookup"><span data-stu-id="aa325-108">Specify **-optimize+** to enable optimizations.</span></span>  
  
 <span data-ttu-id="aa325-109">Podczas kompilowania modułu, który ma być używany przez zestaw, należy użyć tych samych ustawień, co w przypadku zestawu.</span><span class="sxs-lookup"><span data-stu-id="aa325-109">When building a module to be used by an assembly, use the same **-optimize** settings as those of the assembly.</span></span>  
  
 <span data-ttu-id="aa325-110">**-o** jest krótką formą **optymalizacji**.</span><span class="sxs-lookup"><span data-stu-id="aa325-110">**-o** is the short form of **-optimize**.</span></span>  
  
 <span data-ttu-id="aa325-111">Istnieje możliwość połączenia opcji **-Optimize** i [-Debug](./debug-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="aa325-111">It is possible to combine the **-optimize** and [-debug](./debug-compiler-option.md) options.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="aa325-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="aa325-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="aa325-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="aa325-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="aa325-114">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="aa325-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="aa325-115">Zmodyfikuj właściwość **Optimize Code** .</span><span class="sxs-lookup"><span data-stu-id="aa325-115">Modify the **Optimize Code** property.</span></span>  
  
 <span data-ttu-id="aa325-116">Aby uzyskać informacje na temat sposobu, w jaki można programowo ustawić <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>tę opcję kompilatora, zobacz.</span><span class="sxs-lookup"><span data-stu-id="aa325-116">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa325-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa325-117">Example</span></span>  
 <span data-ttu-id="aa325-118">Kompiluj `t2.cs` i Włącz optymalizacje kompilatora:</span><span class="sxs-lookup"><span data-stu-id="aa325-118">Compile `t2.cs` and enable compiler optimizations:</span></span>  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa325-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="aa325-119">See also</span></span>

- [<span data-ttu-id="aa325-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="aa325-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="aa325-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="aa325-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
