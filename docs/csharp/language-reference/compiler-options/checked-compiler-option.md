---
title: -zaznaczone (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c0a8cc66609fe542fc7db166cd208cfcedb204b8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="ca2f2-102">-zaznaczone (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="ca2f2-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="ca2f2-103">**-Zaznaczone** opcja określa, czy instrukcji arytmetyczne liczba całkowita, których wynikiem jest wartość, która jest poza zakresem typu danych, a nie jest w zakresie [zaznaczone](../../../csharp/language-reference/keywords/checked.md) lub [ Zaznaczenie opcji](../../../csharp/language-reference/keywords/unchecked.md) — słowo kluczowe, powoduje, że wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../../../csharp/language-reference/keywords/checked.md) or [unchecked](../../../csharp/language-reference/keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca2f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ca2f2-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="ca2f2-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ca2f2-105">Remarks</span></span>  
 <span data-ttu-id="ca2f2-106">Instrukcję arytmetyczne liczba całkowita, która znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe nie podlega efekt **-zaznaczone** opcji.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="ca2f2-107">Jeśli instrukcja arytmetyczne liczba całkowita, która nie znajduje się w zakresie `checked` lub `unchecked` — słowo kluczowe wynikiem jest wartość spoza zakresu typu danych i **-checked +** (**-zaznaczone**) jest używany w Kompilacja, że instrukcja powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (**-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="ca2f2-108">Jeśli **- zaznaczone -** jest używany w kompilacji, instrukcji nie powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="ca2f2-109">Wartość domyślna dla tej opcji to **- zaznaczone -**.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-109">The default value for this option is **-checked-**.</span></span> <span data-ttu-id="ca2f2-110">Jeden scenariusz użycia **- zaznaczone -** Trwa tworzenie dużych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-110">One scenario for using **-checked-** is in building large applications.</span></span> <span data-ttu-id="ca2f2-111">Niekiedy automatycznego narzędzia są używane do tworzenia takich aplikacji, a takie narzędzie może automatycznie ustawiony **-zaznaczone** do +.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-111">Sometimes automated tools are used to build such applications, and such a tool might automatically set **-checked** to +.</span></span> <span data-ttu-id="ca2f2-112">Domyślny globalny tego narzędzia można zastąpić, określając **- zaznaczone -**.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-112">You can override the tool's global default by specifying **-checked-**.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="ca2f2-113">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ca2f2-113">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="ca2f2-114">Otwórz projekt **właściwości** strony.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-114">Open the project's **Properties** page.</span></span> <span data-ttu-id="ca2f2-115">Aby uzyskać więcej informacji, zobacz [strona kompilacji, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="ca2f2-115">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2.  <span data-ttu-id="ca2f2-116">Kliknij przycisk **kompilacji** strony właściwości.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="ca2f2-117">Kliknij przycisk **zaawansowane** przycisku.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="ca2f2-118">Modyfikowanie **sprawdzaj przepełnienie/niedopełnienie arytmetyczne** właściwości.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-118">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="ca2f2-119">Aby uzyskać dostęp do tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-119">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca2f2-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="ca2f2-120">Example</span></span>  
 <span data-ttu-id="ca2f2-121">Następujące polecenie kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-121">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="ca2f2-122">Korzystanie z `-checked` w poleceniu Określa, że każda instrukcja arytmetyczne całkowitą w pliku nie jest w zakresie `checked` lub `unchecked` — słowo kluczowe i którego wynikiem jest wartość, która jest poza zakresem typu danych powoduje zgłoszenie wyjątku przy uruchomieniu czas.</span><span class="sxs-lookup"><span data-stu-id="ca2f2-122">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="ca2f2-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ca2f2-123">See Also</span></span>  
 [<span data-ttu-id="ca2f2-124">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="ca2f2-124">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="ca2f2-125">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="ca2f2-125">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
