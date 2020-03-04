---
title: — zaznaczone (C# opcje kompilatora)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: 44dc0fc8f50e5248ce2fca17c36f7309a6aca8d1
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239695"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="7cb7d-102">— zaznaczone (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="7cb7d-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="7cb7d-103">Opcja **-** Check określa, czy instrukcja arytmetyczna liczb całkowitych, która skutkuje wartością, która jest poza zakresem danych, i która nie jest w zakresie [zaznaczonego](../keywords/checked.md) lub [niesprawdzonego](../keywords/unchecked.md) słowa kluczowego, powoduje wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb7d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cb7d-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="7cb7d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7cb7d-105">Remarks</span></span>  
 <span data-ttu-id="7cb7d-106">Instrukcja arytmetyczna liczb całkowitych, która znajduje się w zakresie słowa kluczowego `checked` lub `unchecked`, nie podlega wpływowi opcji **-Checked** .</span><span class="sxs-lookup"><span data-stu-id="7cb7d-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="7cb7d-107">Jeśli instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w zakresie słowa kluczowego `checked` lub `unchecked`, daje w wyniku wartość spoza zakresu typu danych i **-Checked +** (lub **-Checked**) jest używana w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="7cb7d-108">Jeśli **jest** używana w kompilacji, ta instrukcja nie powoduje wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="7cb7d-109">Wartość domyślna dla tej opcji to **-Checked-**; Sprawdzanie przepełnienia jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="7cb7d-110">Czasami zautomatyzowane narzędzia, które są używane do kompilowania zestawu dużych aplikacji, są sprawdzane w programie +.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="7cb7d-111">Jednym z scenariuszy użycia-checked-jest zastąpienie globalnego domyślnego narzędzia przez określenie-checked-.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="7cb7d-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7cb7d-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="7cb7d-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="7cb7d-114">Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="7cb7d-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="7cb7d-115">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="7cb7d-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="7cb7d-116">Kliknij przycisk **Zaawansowane**.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="7cb7d-117">Zmodyfikuj właściwość **sprawdzania przepełnienia arytmetycznego** .</span><span class="sxs-lookup"><span data-stu-id="7cb7d-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="7cb7d-118">Aby programowo uzyskać dostęp do tej opcji kompilatora, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb7d-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="7cb7d-119">Example</span></span>  
 <span data-ttu-id="7cb7d-120">Poniższe polecenie kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="7cb7d-121">Użycie `-checked` w poleceniu określa, że jakakolwiek instrukcja arytmetyczna liczb całkowitych w pliku, który nie jest w zakresie `checked` lub `unchecked` słowa kluczowego, i spowoduje, że wartość jest spoza zakresu typu danych, powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7cb7d-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cb7d-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cb7d-122">See also</span></span>

- [<span data-ttu-id="7cb7d-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="7cb7d-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="7cb7d-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="7cb7d-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
