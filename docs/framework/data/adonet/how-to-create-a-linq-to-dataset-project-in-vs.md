---
title: Tworzenie projektu LINQ to DataSet w programie Visual Studio
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783780"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="326ad-102">Instrukcje: Tworzenie projektu LINQ to DataSet w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="326ad-102">How to: Create a LINQ to DataSet project In Visual Studio</span></span>

<span data-ttu-id="326ad-103">Różne typy projektów LINQ wymagają niektórych odwołań zestawów i importowanych przestrzeni nazw (Visual Basic [) lub dyrektyw](../../../csharp/language-reference/keywords/using-directive.md) (C#).</span><span class="sxs-lookup"><span data-stu-id="326ad-103">The different types of LINQ projects require certain assembly references and imported namespaces (Visual Basic) or [using](../../../csharp/language-reference/keywords/using-directive.md) directives (C#).</span></span> <span data-ttu-id="326ad-104">Minimalne wymaganie dla LINQ to odwołanie do *System. Core. dll* i `using` dyrektywy for <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="326ad-104">The minimum requirement for LINQ is a reference to *System.Core.dll* and a `using` directive for <xref:System.Linq>.</span></span>

<span data-ttu-id="326ad-105">Te wymagania są udostępniane domyślnie w przypadku tworzenia nowego C# projektu aplikacji konsolowej w programie Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="326ad-105">These requirements are supplied by default if you create a new C# console app project in Visual Studio 2017.</span></span> <span data-ttu-id="326ad-106">Jeśli uaktualniasz projekt ze starszej wersji programu Visual Studio, może być konieczne ręczne podanie tych odwołań związanych z LINQ.</span><span class="sxs-lookup"><span data-stu-id="326ad-106">If you're upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span>

<span data-ttu-id="326ad-107">LINQ to DataSet wymaga dwóch dodatkowych odwołań do plików *System. Data. dll* i *System. Data. DataSetExtensions. dll*.</span><span class="sxs-lookup"><span data-stu-id="326ad-107">LINQ to DataSet requires two additional references to *System.Data.dll* and *System.Data.DataSetExtensions.dll*.</span></span>

> [!NOTE]
> <span data-ttu-id="326ad-108">W przypadku kompilowania z poziomu wiersza polecenia należy ręcznie odwoływać się do bibliotek DLL związanych z LINQ w *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span><span class="sxs-lookup"><span data-stu-id="326ad-108">If you're building from a command prompt, you must manually reference the LINQ-related DLLs in *%ProgramFiles%\Reference Assemblies\Microsoft\Framework\v3.5*.</span></span>

## <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="326ad-109">Aby włączyć funkcję LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="326ad-109">To enable LINQ to DataSet functionality</span></span>

<span data-ttu-id="326ad-110">Wykonaj następujące kroki, aby włączyć funkcję LINQ to DataSet w istniejącym projekcie.</span><span class="sxs-lookup"><span data-stu-id="326ad-110">Follow these steps to enable LINQ to DataSet functionality in an existing project.</span></span>

1. <span data-ttu-id="326ad-111">Dodaj odwołania do system **. Core**, **System. Data**i **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="326ad-111">Add references to **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span>

   <span data-ttu-id="326ad-112">W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** i wybierz polecenie **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="326ad-112">In **Solution Explorer**, right-click on the **References** node and select **Add Reference**.</span></span> <span data-ttu-id="326ad-113">W oknie dialogowym **Menedżer odwołań** wybierz kolejno pozycje **System. Core**, **System. Data**i **System. Data. DataSetExtensions**.</span><span class="sxs-lookup"><span data-stu-id="326ad-113">In the **Reference Manager** dialog box, select **System.Core**, **System.Data**, and **System.Data.DataSetExtensions**.</span></span> <span data-ttu-id="326ad-114">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="326ad-114">Select **OK**.</span></span>

1. <span data-ttu-id="326ad-115">Dodaj dyrektywy [using](../../../csharp/language-reference/keywords/using-directive.md) (lub [importuje instrukcje](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) w Visual Basic) dla elementu **System. Data** i **System. LINQ**.</span><span class="sxs-lookup"><span data-stu-id="326ad-115">Add [using](../../../csharp/language-reference/keywords/using-directive.md) directives (or [Imports statements](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) in Visual Basic) for **System.Data** and **System.Linq**.</span></span>

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. <span data-ttu-id="326ad-116">Opcjonalnie Dodaj `using` dyrektywę (lub `Imports` instrukcję) dla elementu **System. Data. Common** lub **System. Data. SqlClient**, w zależności od sposobu łączenia się z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="326ad-116">Optionally, add a `using` directive (or `Imports` statement) for **System.Data.Common** or **System.Data.SqlClient**, depending on how you connect to the database.</span></span>

## <a name="see-also"></a><span data-ttu-id="326ad-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="326ad-117">See also</span></span>

- [<span data-ttu-id="326ad-118">Wprowadzenie do LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="326ad-118">Get started with LINQ to DataSet</span></span>](getting-started-linq-to-dataset.md)
