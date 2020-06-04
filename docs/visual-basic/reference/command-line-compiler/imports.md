---
title: -imports
ms.date: 03/10/2018
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
ms.openlocfilehash: cc9fc222843bdfe8e49d2d291dc36ff3e0c63fc2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408598"
---
# <a name="-imports-visual-basic"></a><span data-ttu-id="e3280-102">-Imports (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3280-102">-imports (Visual Basic)</span></span>
<span data-ttu-id="e3280-103">Importuje przestrzenie nazw z określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="e3280-103">Imports namespaces from a specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3280-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3280-104">Syntax</span></span>  
  
```console  
-imports:namespaceList  
```  
  
## <a name="arguments"></a><span data-ttu-id="e3280-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="e3280-105">Arguments</span></span>  
  
|<span data-ttu-id="e3280-106">Termin</span><span class="sxs-lookup"><span data-stu-id="e3280-106">Term</span></span>|<span data-ttu-id="e3280-107">Definicja</span><span class="sxs-lookup"><span data-stu-id="e3280-107">Definition</span></span>|  
|---|---|  
|`namespaceList`|<span data-ttu-id="e3280-108">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="e3280-108">Required.</span></span> <span data-ttu-id="e3280-109">Rozdzielana przecinkami lista przestrzeni nazw do zaimportowania.</span><span class="sxs-lookup"><span data-stu-id="e3280-109">Comma-delimited list of namespaces to be imported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3280-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e3280-110">Remarks</span></span>  
 <span data-ttu-id="e3280-111">`-imports`Opcja importuje wszystkie przestrzenie nazw zdefiniowane w bieżącym zestawie plików źródłowych lub z dowolnego zestawu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="e3280-111">The `-imports` option imports any namespace defined within the current set of source files or from any referenced assembly.</span></span>  
  
 <span data-ttu-id="e3280-112">Elementy członkowskie w przestrzeni nazw określonej za pomocą `-imports` są dostępne dla wszystkich plików kodu źródłowego w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e3280-112">The members in a namespace specified with `-imports` are available to all source-code files in the compilation.</span></span> <span data-ttu-id="e3280-113">Użyj [instrukcji Imports (przestrzeń nazw i typ .NET)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) , aby użyć przestrzeni nazw w jednym pliku kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="e3280-113">Use the [Imports Statement (.NET Namespace and Type)](../../language-reference/statements/imports-statement-net-namespace-and-type.md) to use a namespace in a single source-code file.</span></span>  
  
|<span data-ttu-id="e3280-114">Aby ustawić Importy w zintegrowanym środowisku programistycznym programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="e3280-114">To set -imports in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="e3280-115">1. zaznaczono projekt w **Eksplorator rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="e3280-115">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="e3280-116">W menu **projekt** kliknij polecenie **Właściwości**.</span><span class="sxs-lookup"><span data-stu-id="e3280-116">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="e3280-117">2. Kliknij kartę **odwołania** .</span><span class="sxs-lookup"><span data-stu-id="e3280-117">2.  Click the **References** tab.</span></span><br /><span data-ttu-id="e3280-118">3. Wprowadź nazwę przestrzeni nazw w polu obok przycisku **Dodaj użytkownika importowania** .</span><span class="sxs-lookup"><span data-stu-id="e3280-118">3.  Enter the namespace name in the box beside the **Add User Import** button.</span></span><br /><span data-ttu-id="e3280-119">4. kliknij przycisk **Dodaj Import użytkownika** .</span><span class="sxs-lookup"><span data-stu-id="e3280-119">4.  Click the **Add User Import** button.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e3280-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3280-120">Example</span></span>  
 <span data-ttu-id="e3280-121">Poniższy kod kompiluje, kiedy `-imports:system.globalization` jest określony.</span><span class="sxs-lookup"><span data-stu-id="e3280-121">The following code compiles when `-imports:system.globalization` is specified.</span></span> <span data-ttu-id="e3280-122">Bez tej operacji kompilacja wymaga, aby `Imports System.Globalization` instrukcja była uwzględniona na początku pliku kodu źródłowego lub że właściwość jest w pełni kwalifikowana jako `System.Globalization.CultureInfo.CurrentCulture.Name` .</span><span class="sxs-lookup"><span data-stu-id="e3280-122">Without it, successful compilation requires either that an `Imports System.Globalization` statement be included at the beginning of the source code file, or that the property be fully qualified as `System.Globalization.CultureInfo.CurrentCulture.Name`.</span></span>

```vb
Module Example
   Public Sub Main()
      Console.WriteLine($"The current culture is {CultureInfo.CurrentCulture.Name}")
   End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="e3280-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3280-123">See also</span></span>

- [<span data-ttu-id="e3280-124">Kompilator wiersza polecenia Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3280-124">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="e3280-125">Referencje i instrukcja Imports</span><span class="sxs-lookup"><span data-stu-id="e3280-125">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="e3280-126">Przykłady kompilacji — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="e3280-126">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
