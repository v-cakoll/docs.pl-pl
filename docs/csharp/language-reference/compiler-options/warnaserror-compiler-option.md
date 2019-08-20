---
title: -warnaserror — (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 66c78ee56c9d5153b5b878b2e695ad4ee6bffe0b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606253"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="ba49a-102">-warnaserror — (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="ba49a-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="ba49a-103">Opcja **-warnaserror — +** traktuje wszystkie ostrzeżenia jako błędy</span><span class="sxs-lookup"><span data-stu-id="ba49a-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba49a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba49a-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ba49a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba49a-105">Remarks</span></span>  
 <span data-ttu-id="ba49a-106">Wszystkie komunikaty, które zwykle są raportowane jako ostrzeżenia, są raportowane jako błędy, a proces kompilacji jest zatrzymany (nie skompilowano plików wyjściowych).</span><span class="sxs-lookup"><span data-stu-id="ba49a-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="ba49a-107">Domyślnie **— warnaserror — —** obowiązuje, co powoduje, że ostrzeżenia nie uniemożliwiają generowania pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="ba49a-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="ba49a-108">**-warnaserror —** , która jest taka sama jak **-warnaserror — +** , powoduje, że ostrzeżenia są traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="ba49a-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="ba49a-109">Opcjonalnie, jeśli chcesz, aby tylko kilka określonych ostrzeżeń było traktowane jako błędy, możesz określić rozdzieloną przecinkami listę numerów ostrzeżeń, które będą traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="ba49a-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="ba49a-110">Użyj [-warn](./warn-compiler-option.md) , aby określić poziom ostrzeżeń, które mają być wyświetlane w kompilatorze.</span><span class="sxs-lookup"><span data-stu-id="ba49a-110">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="ba49a-111">Użyj [-nowarn](./nowarn-compiler-option.md) , aby wyłączyć niektóre ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="ba49a-111">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ba49a-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ba49a-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="ba49a-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="ba49a-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="ba49a-114">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="ba49a-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="ba49a-115">Zmodyfikuj właściwość **Traktuj ostrzeżenia jako błędy** .</span><span class="sxs-lookup"><span data-stu-id="ba49a-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="ba49a-116">Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="ba49a-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba49a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba49a-117">Example</span></span>  
 <span data-ttu-id="ba49a-118">Kompiluj `in.cs` i czy kompilator nie wyświetli żadnych ostrzeżeń:</span><span class="sxs-lookup"><span data-stu-id="ba49a-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba49a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba49a-119">See also</span></span>

- [<span data-ttu-id="ba49a-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ba49a-120">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="ba49a-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ba49a-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
