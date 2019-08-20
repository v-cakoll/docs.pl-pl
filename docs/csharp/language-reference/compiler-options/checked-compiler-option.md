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
ms.openlocfilehash: 4e07698e7abdad00983b61412fa2a57e651d4d46
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606988"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="3e28c-102">— zaznaczone (C# opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="3e28c-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="3e28c-103">Opcja **-** Check określa, czy instrukcja arytmetyczna liczb całkowitych, która skutkuje wartością, która jest poza zakresem danych, i która nie jest w zakresie [zaznaczonego](../keywords/checked.md) lub niesprawdzonego słowa [](../keywords/unchecked.md) kluczowego, powoduje wyjątek czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e28c-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e28c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3e28c-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="3e28c-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3e28c-105">Remarks</span></span>  
 <span data-ttu-id="3e28c-106">Instrukcja arytmetyczna liczb całkowitych, która znajduje się w `checked` zakresie `unchecked` słowa kluczowego or, nie podlega wpływowi opcji **-Checked** .</span><span class="sxs-lookup"><span data-stu-id="3e28c-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="3e28c-107">Jeśli instrukcja arytmetyczna liczb całkowitych, która nie znajduje się w `checked` zakresie `unchecked` słowa kluczowego lub, powoduje użycie wartości spoza zakresu typu danych i **-Checked +** (lub **-Checked**) jest używana w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e28c-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="3e28c-108">Jeśli jest używana w kompilacji, ta instrukcja nie powoduje wyjątku w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3e28c-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="3e28c-109">Wartość domyślna dla tej opcji to **-Checked-** ; Sprawdzanie przepełnienia jest wyłączone.</span><span class="sxs-lookup"><span data-stu-id="3e28c-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>
 
 <span data-ttu-id="3e28c-110">Czasami zautomatyzowane narzędzia, które są używane do kompilowania zestawu dużych aplikacji, są sprawdzane w programie +.</span><span class="sxs-lookup"><span data-stu-id="3e28c-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="3e28c-111">Jednym z scenariuszy użycia-checked-jest zastąpienie globalnego domyślnego narzędzia przez określenie-checked-.</span><span class="sxs-lookup"><span data-stu-id="3e28c-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>
 
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="3e28c-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e28c-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="3e28c-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="3e28c-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="3e28c-114">Aby uzyskać więcej informacji, zobacz [stronę Kompilacja, Projektant projektuC#()](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="3e28c-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="3e28c-115">Kliknij stronę właściwości **kompilacja** .</span><span class="sxs-lookup"><span data-stu-id="3e28c-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="3e28c-116">Kliknij przycisk **Zaawansowane** .</span><span class="sxs-lookup"><span data-stu-id="3e28c-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="3e28c-117">Zmodyfikuj **Sprawdzanie dla właściwości przeciążenia/** niedopełnienie.</span><span class="sxs-lookup"><span data-stu-id="3e28c-117">Modify the **Check for arithmetic overflow/underflow** property.</span></span>  
  
 <span data-ttu-id="3e28c-118">Aby programowo uzyskać dostęp do tej opcji kompilatora <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>, zobacz.</span><span class="sxs-lookup"><span data-stu-id="3e28c-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e28c-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e28c-119">Example</span></span>  
 <span data-ttu-id="3e28c-120">Następujące polecenie kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="3e28c-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="3e28c-121">Użycie `-checked` w poleceniu określa, że wszystkie liczby całkowite arytmetyczne w pliku, który nie znajduje się w zakresie `checked` słowa kluczowego `unchecked` or, i powoduje, że wartość jest poza zakresem typu danych, powoduje wyjątek w uruchomieniu pierwszym.</span><span class="sxs-lookup"><span data-stu-id="3e28c-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="3e28c-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e28c-122">See also</span></span>

- [<span data-ttu-id="3e28c-123">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="3e28c-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="3e28c-124">Zarządzanie właściwościami projektu i rozwiązania</span><span class="sxs-lookup"><span data-stu-id="3e28c-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
