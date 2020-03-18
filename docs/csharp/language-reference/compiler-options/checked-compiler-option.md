---
title: -checked (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /checked
helpviewer_keywords:
- checked compiler option [C#]
- -checked compiler option [C#]
- /checked compiler option [C#]
ms.assetid: fb7475d3-e6a6-4e6d-b86c-69e7a74c854b
ms.openlocfilehash: cb4dbadfa4efd0750ffd3dea88a3f661e2f85a8e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173773"
---
# <a name="-checked-c-compiler-options"></a><span data-ttu-id="6a38a-102">-checked (Opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="6a38a-102">-checked (C# Compiler Options)</span></span>
<span data-ttu-id="6a38a-103">**Opcja -checked** określa, czy instrukcja arytmetyczna liczby całkowitej, która powoduje wartość, która znajduje się poza zakresem typu danych, a która nie znajduje się w zakresie [zaznaczonego](../keywords/checked.md) lub [niezaznaczonego](../keywords/unchecked.md) słowa kluczowego, powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a38a-103">The **-checked** option specifies whether an integer arithmetic statement that results in a value that is outside the range of the data type, and that is not in the scope of a [checked](../keywords/checked.md) or [unchecked](../keywords/unchecked.md) keyword, causes a run-time exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a38a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6a38a-104">Syntax</span></span>  
  
```console  
-checked[+ | -]  
```  
  
## <a name="remarks"></a><span data-ttu-id="6a38a-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a38a-105">Remarks</span></span>  
 <span data-ttu-id="6a38a-106">Instrukcja arytmetyczna liczby całkowitej, która `checked` znajduje `unchecked` się w zakresie lub słowa kluczowego, nie podlega efektowi opcji **-checked.**</span><span class="sxs-lookup"><span data-stu-id="6a38a-106">An integer arithmetic statement that is in the scope of a `checked` or `unchecked` keyword is not subject to the effect of the **-checked** option.</span></span>  
  
 <span data-ttu-id="6a38a-107">Jeśli instrukcja arytmetyczna liczby całkowitej, która `checked` nie `unchecked` znajduje się w zakresie lub słowa kluczowego powoduje wartość spoza zakresu typu danych i **-checked+** (lub **-checked)** jest używany w kompilacji, ta instrukcja powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a38a-107">If an integer arithmetic statement that is not in the scope of a `checked` or `unchecked` keyword results in a value outside the range of the data type, and **-checked+** (or **-checked**) is used in the compilation, that statement causes an exception at run time.</span></span> <span data-ttu-id="6a38a-108">Jeśli **-checked-** jest używany w kompilacji, że instrukcja nie powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a38a-108">If **-checked-** is used in the compilation, that statement does not cause an exception at run time.</span></span>  
  
 <span data-ttu-id="6a38a-109">Domyślną wartością dla tej opcji jest **-checked-**; kontrola przepełnienia jest wyłączona.</span><span class="sxs-lookup"><span data-stu-id="6a38a-109">The default value for this option is **-checked-**; overflow checking is disabled.</span></span>

 <span data-ttu-id="6a38a-110">Czasami zautomatyzowane narzędzia, które są używane do tworzenia dużych aplikacji set -checked do +.</span><span class="sxs-lookup"><span data-stu-id="6a38a-110">Sometimes, automated tools that are used to build large applications set -checked to +.</span></span> <span data-ttu-id="6a38a-111">Jednym ze scenariuszy użycia -checked- jest zastąpienie globalnego domyślnego narzędzia, określając -checked-.</span><span class="sxs-lookup"><span data-stu-id="6a38a-111">One scenario for using -checked- is to override the tool's global default by specifying -checked-.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="6a38a-112">Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6a38a-112">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="6a38a-113">Otwórz stronę **Właściwości** projektu.</span><span class="sxs-lookup"><span data-stu-id="6a38a-113">Open the project's **Properties** page.</span></span> <span data-ttu-id="6a38a-114">Aby uzyskać więcej informacji, zobacz [Tworzenie strony, Projektant projektu (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span><span class="sxs-lookup"><span data-stu-id="6a38a-114">For more information, see [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).</span></span>  
  
2. <span data-ttu-id="6a38a-115">Kliknij stronę **Właściwości kompilacji.**</span><span class="sxs-lookup"><span data-stu-id="6a38a-115">Click the **Build** property page.</span></span>  
  
3. <span data-ttu-id="6a38a-116">Kliknij przycisk **Zaawansowane.**</span><span class="sxs-lookup"><span data-stu-id="6a38a-116">Click the **Advanced** button.</span></span>  
  
4. <span data-ttu-id="6a38a-117">Zmodyfikuj właściwość **Sprawdź przepełnienie arytmetyczne.**</span><span class="sxs-lookup"><span data-stu-id="6a38a-117">Modify the **Check for arithmetic overflow** property.</span></span>  
  
 <span data-ttu-id="6a38a-118">Aby programowo uzyskać dostęp do <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>tej opcji kompilatora, zobacz .</span><span class="sxs-lookup"><span data-stu-id="6a38a-118">To access this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.CheckForOverflowUnderflow%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6a38a-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="6a38a-119">Example</span></span>  
 <span data-ttu-id="6a38a-120">Następujące polecenie kompiluje `t2.cs`.</span><span class="sxs-lookup"><span data-stu-id="6a38a-120">The following command compiles `t2.cs`.</span></span> <span data-ttu-id="6a38a-121">Użycie `-checked` w poleceniu określa, że każda instrukcja arytmetyczna całkowita w `checked` pliku, która nie znajduje się w zakresie lub `unchecked` słowa kluczowego, a która powoduje wartość, która znajduje się poza zakresem typu danych, powoduje wyjątek w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="6a38a-121">The use of `-checked` in the command specifies that any integer arithmetic statement in the file that is not in the scope of a `checked` or `unchecked` keyword, and that results in a value that is outside the range of the data type, causes an exception at run time.</span></span>  
  
```console  
csc t2.cs -checked  
```  
  
## <a name="see-also"></a><span data-ttu-id="6a38a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6a38a-122">See also</span></span>

- [<span data-ttu-id="6a38a-123">Opcje kompilatora Języka C#</span><span class="sxs-lookup"><span data-stu-id="6a38a-123">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="6a38a-124">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="6a38a-124">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
