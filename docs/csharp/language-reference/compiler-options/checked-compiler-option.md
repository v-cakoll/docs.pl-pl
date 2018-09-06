---
title: -zaznaczone (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cf6fa0e87654d0f9d61f34ea9b29ad80921a5720
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802741"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="f8bab-102">-zaznaczone (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="f8bab-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="f8bab-103">**-Zaznaczone** opcja określa, czy instrukcję arytmetyczne liczba całkowita, która wynikiem jest wartość, która jest poza zakresem typu danych, a nie jest w zakresie [zaznaczone](../../../csharp/language-reference/keywords/checked.md) lub [ unchecked](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe, powoduje wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8bab-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8bab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8bab-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="f8bab-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8bab-105">Remarks</span></span>  
 <span data-ttu-id="f8bab-106">Instrukcję arytmetyczne liczba całkowita, która znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe nie podlega efekt **-zaznaczone** opcji.</span><span class="sxs-lookup"><span data-stu-id="f8bab-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="f8bab-107">Jeśli instrukcję arytmetyczne liczba całkowita, która nie znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe wyniki w wartość spoza zakresu typu danych, i **-checked +** (lub **-zaznaczone**) jest używany w Kompilacja, że instrukcja powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8bab-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="f8bab-108">Jeśli **- zaznaczone -** jest używany w kompilacji, instrukcji nie powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f8bab-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="f8bab-109">Wartość domyślna tej opcji to **- zaznaczone -**; sprawdzanie przepełnienia jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="f8bab-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="f8bab-110">Czasami zautomatyzowanych narzędzi, które są używane do budowania dużych aplikacji ustawione — sprawdzany w celu +.</span><span class="sxs-lookup"><span data-stu-id="f8bab-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="f8bab-111">Jeden scenariusz użycia, - zaznaczone — jest zastąpienie domyślnie globalne dla tego narzędzia, określając - zaznaczone —.</span><span class="sxs-lookup"><span data-stu-id="f8bab-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="f8bab-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f8bab-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="f8bab-113">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="f8bab-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="f8bab-114">Aby uzyskać więcej informacji, zobacz [Stroka kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="f8bab-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="f8bab-115">Kliknij przycisk **kompilacji** stronę właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8bab-115">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="f8bab-116">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="f8bab-116">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="f8bab-117">Modyfikowanie **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** właściwości.</span><span class="sxs-lookup"><span data-stu-id="f8bab-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="f8bab-118">Aby uzyskać dostęp do tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8bab-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8bab-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="f8bab-119">Example</span></span>  
 <span data-ttu-id="f8bab-120">Następujące polecenie kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="f8bab-121">Korzystanie z `-checked` w poleceniu Określa, że każda liczba całkowita instrukcja arytmetyczne w pliku, nie jest w zakresie `checked` lub `unchecked` — słowo kluczowe i którego wynikiem jest wartość, która znajduje się poza zakresem typu danych, powoduje wyjątek przy uruchomieniu czas.</span><span class="sxs-lookup"><span data-stu-id="f8bab-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8bab-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8bab-122">See Also</span></span>  

- [<span data-ttu-id="f8bab-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="f8bab-123">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
- [<span data-ttu-id="f8bab-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="f8bab-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
