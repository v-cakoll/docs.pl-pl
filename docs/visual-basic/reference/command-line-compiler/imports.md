---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 330a5e6821c9c76f3503a35a5a5eabf24c686b42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652093"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="0435e-102">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0435e-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="0435e-103">Importuje przestrzeni nazw z określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0435e-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0435e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0435e-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="0435e-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="0435e-105">Arguments</span></span>  
  
|<span data-ttu-id="0435e-106">Termin</span><span class="sxs-lookup"><span data-stu-id="0435e-106">Term</span></span>|<span data-ttu-id="0435e-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="0435e-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="0435e-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="0435e-108">Required.</span></span> <span data-ttu-id="0435e-109">Rozdzielana przecinkami lista obszarów nazw do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="0435e-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0435e-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0435e-110">Remarks</span></span>  
 <span data-ttu-id="0435e-111">`-imports` Opcja importuje przestrzeni nazw zdefiniowane w obrębie bieżącego zestawu plików źródłowych lub z dowolnej przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="0435e-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="0435e-112">Elementy członkowskie w przestrzeni nazw określony za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="0435e-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="0435e-113">Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do użycia w pliku kodu źródłowego w jednej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0435e-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="0435e-114">Aby ustawić/Import w Visual Studio zintegrowane środowisko programistyczne</span><span class="sxs-lookup"><span data-stu-id="0435e-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="0435e-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="0435e-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="0435e-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="0435e-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="0435e-117">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="0435e-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="0435e-118">3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0435e-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="0435e-119">4.  Kliknij przycisk **dodać importu użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="0435e-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0435e-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0435e-120">Example</span></span>  
 <span data-ttu-id="0435e-121">Poniższy kod kompiluje kiedy `/imports:system.globalization` jest określona.</span><span class="sxs-lookup"><span data-stu-id="0435e-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="0435e-122">Bez tego pomyślnej kompilacji wymaga albo `Imports System.Globalization` instrukcji być uwzględnione na początku pliku źródła kodu, lub że właściwość być w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="0435e-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0435e-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0435e-123">See Also</span></span>  
 [<span data-ttu-id="0435e-124">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0435e-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="0435e-125">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="0435e-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="0435e-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="0435e-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
