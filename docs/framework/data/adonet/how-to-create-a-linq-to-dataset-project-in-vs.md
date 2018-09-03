---
title: Tworzenie projektu LINQ to DataSet w programie Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 12544c6b5153a5f6300072d1646f2c119fb255a1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482181"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="b4760-102">Porady: Tworzenie projektu LINQ to DataSet w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b4760-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="b4760-103">Różne rodzaje projektów LINQ wymagają pewnych odwołania do zestawów i importowanych przestrzeni nazw (Visual Basic) lub [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy (C#).</span><span class="sxs-lookup"><span data-stu-id="b4760-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="b4760-104">Minimalne wymagania dla programu LINQ to odwołanie do *System.Core.dll* i `using` dyrektywy dla <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="b4760-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="b4760-105">Te wymagania są określane domyślnie, jeśli tworzysz nowy projekt C# console aplikacji w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="b4760-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="b4760-106">Jeśli aktualizujesz projekt z wcześniejszej wersji programu Visual Studio, trzeba ręcznie podać te odwołania dotyczące LINQ.</span><span class="sxs-lookup"><span data-stu-id="b4760-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="b4760-107">LINQ do zestawu danych wymaga dwóch dodatkowych odwołania do *System.Data.dll* i *System.Data.DataSetExtensions.dll*.</span><span class="sxs-lookup"><span data-stu-id="b4760-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="b4760-108">Jeśli kompilujesz z wiersza polecenia, należy ręcznie odwołujesz się dll związane z LINQ w *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="b4760-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="b4760-109">Aby włączyć LINQ do funkcji zestawu danych</span><span class="sxs-lookup"><span data-stu-id="b4760-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="b4760-110">Wykonaj następujące kroki w celu włączenia zapytań LINQ do funkcji zestawu danych w istniejącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="b4760-110">Follow these steps to to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="b4760-111">Dodaj odwołania do **System.Core**, **System.Data**, i **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="b4760-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="b4760-112">W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** a następnie wybierz węzeł **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="b4760-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="b4760-113">W **Menadżer odwołań** okno dialogowe, wybierz opcję **System.Core**, **System.Data**, i **System.Data.DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="b4760-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="b4760-114">Wybierz **OK**.</span><span class="sxs-lookup"><span data-stu-id="b4760-114">Select **OK**.</span></span>

1. <span data-ttu-id="b4760-115">Dodaj [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy (lub [importuje instrukcji](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) w języku Visual Basic) dla **System.Data** i **System.Linq**.</span><span class="sxs-lookup"><span data-stu-id="b4760-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="b4760-116">Opcjonalnie dodaj `using` — dyrektywa (lub `Imports` instrukcji) dla **System.Data.Common** lub **System.Data.SqlClient**, w zależności od sposobu łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="b4760-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4760-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4760-117">See also</span></span>

- [<span data-ttu-id="b4760-118">Wprowadzenie do LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="b4760-118">Get started with LINQ to DataSet</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)
