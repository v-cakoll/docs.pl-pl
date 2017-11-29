---
title: -warnaserror (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /warnaserror
helpviewer_keywords:
- /warnaserror compiler option [C#]
- -warnaserror compiler option [C#]
- warnaserror compiler option [C#]
ms.assetid: 04680ec3-08d6-4e2e-a274-38310e10e33c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28c2cdc26d32d98e617a0c4b8cd282d2fbc87f4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="warnaserror-c-compiler-options"></a><span data-ttu-id="62cce-102">/warnaserror (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="62cce-102">/warnaserror (C# Compiler Options)</span></span>
<span data-ttu-id="62cce-103">**/Warnaserror+** opcji traktuje wszystkie ostrzeżenia jako błędy</span><span class="sxs-lookup"><span data-stu-id="62cce-103">The **/warnaserror+** option treats all warnings as errors</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62cce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62cce-104">Syntax</span></span>  
  
```console  
/warnaserror[<U>+</U> | -][:warning-list]  
```  
  
## <a name="remarks"></a><span data-ttu-id="62cce-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62cce-105">Remarks</span></span>  
 <span data-ttu-id="62cce-106">Komunikaty, które zazwyczaj będzie zgłaszane jako ostrzeżenia zamiast tego są raportowane klientowi jako błędy, a proces kompilacji zostało zatrzymane (żadne dane wyjściowe są tworzone pliki).</span><span class="sxs-lookup"><span data-stu-id="62cce-106">Any messages that would ordinarily be reported as warnings are instead reported as errors, and the build process is halted (no output files are built).</span></span>  
  
 <span data-ttu-id="62cce-107">Domyślnie **/warnaserror-** obowiązują, co powoduje, że ostrzeżenia dotyczące zapobiega generowaniu pliku wyjściowego.</span><span class="sxs-lookup"><span data-stu-id="62cce-107">By default, **/warnaserror-** is in effect, which causes warnings to not prevent the generation of an output file.</span></span> <span data-ttu-id="62cce-108">**/ warnaserror**, która jest taka sama jak **/warnaserror+**, powoduje, że ostrzeżenia, które będą traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="62cce-108">**/warnaserror**, which is the same as **/warnaserror+**, causes warnings to be treated as errors.</span></span>  
  
 <span data-ttu-id="62cce-109">Opcjonalnie Jeśli chcesz tylko kilka konkretne ostrzeżenia, które będą traktowane jako błędy mogą określić rozdzielana przecinkami lista numerów ostrzeżeń, które mają być traktowane jako błędy.</span><span class="sxs-lookup"><span data-stu-id="62cce-109">Optionally, if you want only a few specific warnings to be treated as errors, you may specify a comma-separated list of warning numbers to treat as errors.</span></span>  
  
 <span data-ttu-id="62cce-110">Użyj [/ warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) określa poziom ostrzeżeń, które mają kompilatora do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="62cce-110">Use [/warn](../../../csharp/language-reference/compiler-options/warn-compiler-option.md) to specify the level of warnings that you want the compiler to display.</span></span> <span data-ttu-id="62cce-111">Użyj [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) Aby wyłączyć określone ostrzeżenia.</span><span class="sxs-lookup"><span data-stu-id="62cce-111">Use [/nowarn](../../../csharp/language-reference/compiler-options/nowarn-compiler-option.md) to disable certain warnings.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="62cce-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="62cce-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="62cce-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="62cce-113">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="62cce-114">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="62cce-114">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="62cce-115">Modyfikowanie **Traktuj ostrzeżenia jako błędy** właściwości.</span><span class="sxs-lookup"><span data-stu-id="62cce-115">Modify the **Treat Warnings As Errors** property.</span></span>  
  
     <span data-ttu-id="62cce-116">Aby ustawić tę opcję kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span><span class="sxs-lookup"><span data-stu-id="62cce-116">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.TreatWarningsAsErrors%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62cce-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="62cce-117">Example</span></span>  
 <span data-ttu-id="62cce-118">Kompiluj `in.cs` i mieć kompilatora wyświetlane nie ostrzeżenia:</span><span class="sxs-lookup"><span data-stu-id="62cce-118">Compile `in.cs` and have the compiler display no warnings:</span></span>  
  
```console  
csc /warnaserror in.cs  
csc /warnaserror:642,649,652 in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="62cce-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62cce-119">See Also</span></span>  
 [<span data-ttu-id="62cce-120">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="62cce-120">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="62cce-121">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="62cce-121">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
