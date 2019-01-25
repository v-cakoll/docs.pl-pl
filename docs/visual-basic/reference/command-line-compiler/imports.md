---
title: -imports (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: 9e5adcce85c4ca4863d28784a7d7f61c441a06c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54588447"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="d8103-102">-imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d8103-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="d8103-103">Importuje przestrzenie nazw z określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8103-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8103-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d8103-104">Syntax</span></span>  
  
```  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="d8103-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="d8103-105">Arguments</span></span>  
  
|<span data-ttu-id="d8103-106">Termin</span><span class="sxs-lookup"><span data-stu-id="d8103-106">Term</span></span>|<span data-ttu-id="d8103-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="d8103-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="d8103-108">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="d8103-108">Required.</span></span> <span data-ttu-id="d8103-109">Rozdzielana przecinkami lista przestrzeni nazw do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="d8103-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d8103-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d8103-110">Remarks</span></span>  
 <span data-ttu-id="d8103-111">`-imports` Opcja importuje dowolnego obszaru nazw, zdefiniowany w ramach bieżącego zestawu plików źródłowych lub z dowolnym przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d8103-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="d8103-112">Członkowie w przestrzeni nazw określony za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d8103-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="d8103-113">Użyj [Importy — instrukcja (.NET Namespace i Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) do korzystania z przestrzeni nazw w pliku kodu źródłowego w jednym.</span><span class="sxs-lookup"><span data-stu-id="d8103-113">Use the [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="d8103-114">Aby ustawić/Import w programie Visual Studio zintegrowanego środowiska programistycznego</span><span class="sxs-lookup"><span data-stu-id="d8103-114">To set /imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="d8103-115">1.  Projekt wybrany w **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="d8103-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="d8103-116">Na **projektu** menu, kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="d8103-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="d8103-117">2.  Kliknij przycisk **odwołania** kartę.</span><span class="sxs-lookup"><span data-stu-id="d8103-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="d8103-118">3.  Wprowadź nazwę przestrzeni nazw w polu obok **dodać Import użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d8103-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="d8103-119">4.  Kliknij przycisk **dodać Import użytkownika** przycisku.</span><span class="sxs-lookup"><span data-stu-id="d8103-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d8103-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="d8103-120">Example</span></span>  
 <span data-ttu-id="d8103-121">Poniższy kod kompiluje, kiedy `/imports:system.globalization` jest określony.</span><span class="sxs-lookup"><span data-stu-id="d8103-121">The following code compiles when `/imports:system.globalization` is specified.</span></span> <span data-ttu-id="d8103-122">Bez tego pomyślnej kompilacji wymaga obu `Imports System.Globalization` instrukcja być uwzględniona na początku pliku kodu źródłowego, lub właściwości można w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name`.</span><span class="sxs-lookup"><span data-stu-id="d8103-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span> 
  
 [!code-vb[imports example](codesnippet/VisualBasic/imports_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d8103-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d8103-123">See also</span></span>
- [<span data-ttu-id="d8103-124">Kompilator wiersza polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d8103-124">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="d8103-125">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="d8103-125">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="d8103-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="d8103-126">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
