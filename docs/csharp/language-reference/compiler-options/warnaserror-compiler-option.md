---
title: -warnaserror (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
ms.openlocfilehash: 2ae555c2e049e687f508e62b5b46fd8a744e827f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329106"
---
# <a name="-warnaserror-c-compiler-options"></a><span data-ttu-id="1b2cc-102">-warnaserror (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1b2cc-102">-warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="1b2cc-103">**- Warnaserror +** opcji traktuje wszystkie ostrzeżenia jako błędy</span><span class="sxs-lookup"><span data-stu-id="1b2cc-103">The **-warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b2cc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1b2cc-104">Syntax</span></span>  
  
```console  
-warnaserror[+ | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="1b2cc-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1b2cc-105">Remarks</span></span>  
 <span data-ttu-id="1b2cc-106">Wszystkie komunikaty, które zazwyczaj będzie zgłaszane jako ostrzeżenia zamiast tego są zgłaszane jako błędy, a proces kompilacji jest zatrzymana (Brak danych wyjściowych, które są tworzone pliki).</span><span class="sxs-lookup"><span data-stu-id="1b2cc-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="1b2cc-107">Domyślnie **- warnaserror —** obowiązują, co powoduje, że ostrzeżenia nie uniemożliwia generowanie pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-107">By default, **-warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="1b2cc-108">**-warnaserror**, która jest taka sama jak **- warnaserror +**, powoduje, że ostrzeżenia są traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-108">**-warnaserror**, which is the same as **-warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="1b2cc-109">Opcjonalnie Jeśli chcesz tylko kilka określone ostrzeżenia są traktowane jako błędy, można określić przecinkami lista numerów ostrzeżeń do traktowania jako błędy, które.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="1b2cc-110">Użyj [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) określa poziom ostrzeżeń, które mają kompilatora do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-110">Use [-warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="1b2cc-111">Użyj [- nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) można wyłączyć niektórych ostrzeżeń.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-111">Use [-nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1b2cc-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b2cc-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="1b2cc-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-113">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="1b2cc-114">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-114">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="1b2cc-115">Modyfikowanie **Traktuj ostrzeżenia jako błędy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
 <span data-ttu-id="1b2cc-116">Aby programowo ustawić tę opcję kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span><span class="sxs-lookup"><span data-stu-id="1b2cc-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b2cc-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b2cc-117">Example</span></span>  
 <span data-ttu-id="1b2cc-118">Skompilować `in.cs` i pozwolić kompilatorowi wyświetlane nie ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="1b2cc-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc -warnaserror in.cs  
csc -warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="1b2cc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1b2cc-119">See also</span></span>

- [<span data-ttu-id="1b2cc-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="1b2cc-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="1b2cc-121">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1b2cc-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
