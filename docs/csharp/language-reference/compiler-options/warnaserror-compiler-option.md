---
title: -warnaserror (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 7d43941629e933ac5a9e9c9d6a1388b6194f8d99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503478"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="e8fce-102">-warnaserror (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="e8fce-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="e8fce-103">Opcja **-warnaserror+** traktuje wszystkie ostrzeżenia jako błędy</span><span class="sxs-lookup"><span data-stu-id="e8fce-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8fce-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="e8fce-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8fce-105">Remarks</span></span>  
 <span data-ttu-id="e8fce-106">Wszelkie komunikaty, które zwykle są zgłaszane jako ostrzeżenia są zgłaszane jako błędy, a proces kompilacji jest zatrzymany (nie są tworzone żadne pliki wyjściowe).</span><span class="sxs-lookup"><span data-stu-id="e8fce-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="e8fce-107">Domyślnie **-warnaserror-** jest w mocy, co powoduje ostrzeżenia, aby nie zapobiec generowaniu pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="e8fce-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="e8fce-108">**-warnaserror**, który jest taki sam jak **-warnaserror +**, powoduje, że ostrzeżenia są traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="e8fce-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="e8fce-109">Opcjonalnie, jeśli chcesz, aby tylko kilka określonych ostrzeżeń było traktowanych jako błędy, możesz określić oddzieloną przecinkami listę numerów ostrzeżeń, które należy traktować jako błędy.</span><span class="sxs-lookup"><span data-stu-id="e8fce-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span> <span data-ttu-id="e8fce-110">Zestaw wszystkich ostrzeżeń nullability można określić za pomocą skrótu **nullable.**</span><span class="sxs-lookup"><span data-stu-id="e8fce-110">The set of all nullability warnings can be specified with the **nullable** shorthand.</span></span>
  
 <span data-ttu-id="e8fce-111">Użyj [-warn,](./warn-compiler-option.md) aby określić poziom ostrzeżeń, które mają być wyświetlane przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="e8fce-111">Use [-warn](./warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="e8fce-112">Użyj [-nowarn,](./nowarn-compiler-option.md) aby wyłączyć niektóre ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="e8fce-112">Use [-nowarn](./nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="e8fce-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e8fce-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="e8fce-114">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="e8fce-114">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="e8fce-115">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="e8fce-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="e8fce-116">Zmodyfikuj **właściwości Treat Warnings As Errors.**</span><span class="sxs-lookup"><span data-stu-id="e8fce-116">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="e8fce-117">Aby programowo ustawić tę opcję <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="e8fce-117">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8fce-118">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8fce-118">Example</span></span>  
 <span data-ttu-id="e8fce-119">Skompiluj `in.cs` i mają kompilator a nie wyświetlać żadnych ostrzeżeń:</span><span class="sxs-lookup"><span data-stu-id="e8fce-119">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652,nullable in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8fce-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e8fce-120">See also</span></span>

- [<span data-ttu-id="e8fce-121">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="e8fce-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="e8fce-122">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="e8fce-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
