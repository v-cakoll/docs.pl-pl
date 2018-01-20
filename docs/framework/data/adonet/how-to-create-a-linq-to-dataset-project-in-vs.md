---
title: "Porady: Tworzenie składnika LINQ to projektu DataSet w programie Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c749cdd56f0c964b84788b05470406234ef3eb0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a><span data-ttu-id="c98b7-102">Porady: Tworzenie składnika LINQ to projektu DataSet w programie Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c98b7-102">How to: Create a LINQ to DataSet Project In Visual Studio</span></span>
<span data-ttu-id="c98b7-103">Różne typy [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projekt wymaga niektórych importowane przestrzenie nazw (Visual Basic) lub `using` dyrektywy (C#) i odwołań.</span><span class="sxs-lookup"><span data-stu-id="c98b7-103">The different types of [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] projects require certain imported namespaces (Visual Basic) or `using` directives (C#) and references.</span></span> <span data-ttu-id="c98b7-104">Minimalna wymagana wartość to odwołania do System.Core.dll i `using` dyrektywy dla <xref:System.Linq>.</span><span class="sxs-lookup"><span data-stu-id="c98b7-104">The minimum requirement is a reference to System.Core.dll and a `using` directive for <xref:System.Linq>.</span></span> <span data-ttu-id="c98b7-105">Domyślnie te są dostarczane w przypadku utworzenia nowego [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="c98b7-105">By default, these are supplied if you create a new [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] project.</span></span> [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]<span data-ttu-id="c98b7-106">również wymaga odwołania do System.Data.dll i System.Data.DataSetExtensions.dll i `Imports` (Visual Basic) lub `using` — dyrektywa (C#).</span><span class="sxs-lookup"><span data-stu-id="c98b7-106"> also requires a reference to System.Data.dll and System.Data.DataSetExtensions.dll and an `Imports` (Visual Basic) or `using` (C#) directive.</span></span>  
  
 <span data-ttu-id="c98b7-107">Jeśli uaktualniasz projektu ze starszej wersji programu Visual Studio, trzeba będzie ręcznie podać te odwołania dotyczące LINQ.</span><span class="sxs-lookup"><span data-stu-id="c98b7-107">If you are upgrading a project from an earlier version of Visual Studio, you might have to supply these LINQ-related references manually.</span></span> <span data-ttu-id="c98b7-108">Ponadto może być konieczne ręczne ustawienie projekt pod kątem .NET Framework w wersji 3.5.</span><span class="sxs-lookup"><span data-stu-id="c98b7-108">You might also have to manually set the project to target the .NET Framework version 3.5.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c98b7-109">Jeśli tworzysz z wiersza polecenia, ręcznie musi odwoływać LINQ związane z bibliotek DLL w `drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span><span class="sxs-lookup"><span data-stu-id="c98b7-109">If you are building from a command prompt, you must manually reference the LINQ-related DLLs in `drive`**:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5.</span></span>  
  
### <a name="to-target-the-net-framework-35"></a><span data-ttu-id="c98b7-110">Docelowy .NET Framework 3.5</span><span class="sxs-lookup"><span data-stu-id="c98b7-110">To target the .NET Framework 3.5</span></span>  
  
1.  <span data-ttu-id="c98b7-111">W [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], Utwórz nowy projekt Visual Basic lub C#.</span><span class="sxs-lookup"><span data-stu-id="c98b7-111">In [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], create a new Visual Basic or C# project.</span></span> <span data-ttu-id="c98b7-112">Alternatywnie możesz otworzyć projekt Visual Basic lub C#, który został utworzony w programie Visual Studio 2005 i postępuj zgodnie z monitami, aby przekonwertować go na [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="c98b7-112">Alternatively, you can open a Visual Basic or C# project that was created in Visual Studio 2005 and follow the prompts to convert it to a [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="c98b7-113">Dla projektu C#, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c98b7-113">For a C# project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="c98b7-114">W **aplikacji** strony właściwości, wybierz program .NET Framework 3.5 w **platformy docelowej** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="c98b7-114">In the **Application** property page, select .NET Framework 3.5 in the **Target Framework** drop-down list.</span></span>  
  
3.  <span data-ttu-id="c98b7-115">Dla projektu Visual Basic, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **właściwości**.</span><span class="sxs-lookup"><span data-stu-id="c98b7-115">For a Visual Basic project, click the **Project** menu, and then click **Properties**.</span></span>  
  
    1.  <span data-ttu-id="c98b7-116">W **skompilować** strony właściwości, kliknij przycisk **zaawansowane opcje kompilacji** , a następnie wybierz .NET Framework 3.5 w **platformy docelowej (wszystkie konfiguracje)** listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="c98b7-116">In the **Compile** property page, click **Advanced Compile Options** and then select .NET Framework 3.5 in the **Target Framework (all configurations)** drop-down list.</span></span>  
  
4.  <span data-ttu-id="c98b7-117">Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**, kliknij przycisk **.NET** karcie, przewiń w dół do **System.Core**, kliknij go, a następnie kliknij przycisk  **OK**.</span><span class="sxs-lookup"><span data-stu-id="c98b7-117">On the **Project** menu, click **Add Reference**, click the **.NET** tab, scroll down to **System.Core**, click it, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c98b7-118">Dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla <xref:System.Linq> do pliku kodu źródłowego lub projektu.</span><span class="sxs-lookup"><span data-stu-id="c98b7-118">Add a `using` directive or imported namespace for <xref:System.Linq> to your source code file or project.</span></span>  
  
     <span data-ttu-id="c98b7-119">Aby uzyskać więcej informacji, zobacz [dyrektywa using](~/docs/csharp/language-reference/keywords/using-directive.md) lub [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c98b7-119">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
### <a name="to-enable-linq-to-dataset-functionality"></a><span data-ttu-id="c98b7-120">Aby włączyć LINQ do DataSet funkcji</span><span class="sxs-lookup"><span data-stu-id="c98b7-120">To enable LINQ to DataSet functionality</span></span>  
  
1.  <span data-ttu-id="c98b7-121">Jeśli to konieczne, wykonaj kroki opisane wcześniej w tym temacie, można dodać odwołania do System.Core.dll i `using` dyrektywy lub importowanych przestrzeni nazw dla System.Linq.</span><span class="sxs-lookup"><span data-stu-id="c98b7-121">If necessary, follow the steps earlier in this topic to add a reference to System.Core.dll and a `using` directive or imported namespace for System.Linq.</span></span>  
  
2.  <span data-ttu-id="c98b7-122">W języku C# lub Visual Basic, kliknij przycisk **projektu** menu, a następnie kliknij przycisk **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="c98b7-122">In C# or Visual Basic, click the **Project** menu, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="c98b7-123">W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **.NET** karcie, jeśli nie znajduje się na górze.</span><span class="sxs-lookup"><span data-stu-id="c98b7-123">In the **Add Reference** dialog box, click the **.NET** tab if it is not on top.</span></span> <span data-ttu-id="c98b7-124">Przewiń w dół do **system.dane** i **System.Data.DataSetExtensions** i kliknij je.</span><span class="sxs-lookup"><span data-stu-id="c98b7-124">Scroll down to **System.Data** and **System.Data.DataSetExtensions** and click on them.</span></span> <span data-ttu-id="c98b7-125">Kliknij przycisk **OK** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c98b7-125">Click the **OK** button.</span></span>  
  
4.  <span data-ttu-id="c98b7-126">Dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla <xref:System.Data> do pliku kodu źródłowego lub projektu.</span><span class="sxs-lookup"><span data-stu-id="c98b7-126">Add a `using` directive or imported namespace for <xref:System.Data> to your source code file or project.</span></span> <span data-ttu-id="c98b7-127">Aby uzyskać więcej informacji, zobacz [dyrektywa using](~/docs/csharp/language-reference/keywords/using-directive.md) lub [porady: Dodawanie lub usuwanie zaimportowane przestrzenie nazw (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c98b7-127">For more information, see [using Directive](~/docs/csharp/language-reference/keywords/using-directive.md) or [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>  
  
5.  <span data-ttu-id="c98b7-128">Dodaj odwołanie do System.Data.DataSetExtensions.dll dla technologii LINQ do Dataset funkcji.</span><span class="sxs-lookup"><span data-stu-id="c98b7-128">Add a reference to System.Data.DataSetExtensions.dll for LINQ to Dataset functionality.</span></span> <span data-ttu-id="c98b7-129">Dodaj odwołanie do System.Data.dll, jeśli jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="c98b7-129">Add a reference to System.Data.dll if it does not already exist.</span></span>  
  
6.  <span data-ttu-id="c98b7-130">Opcjonalnie dodaj `using` dyrektywy lub importowanych przestrzeni nazw dla `System.Data.Common` lub `System.Data.SqlClient`, w zależności od sposobu łączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="c98b7-130">Optionally, add a `using` directive or imported namespace for `System.Data.Common` or `System.Data.SqlClient`, depending on how you connect to the database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98b7-131">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c98b7-131">See Also</span></span>  
 [<span data-ttu-id="c98b7-132">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c98b7-132">Getting Started</span></span>](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [<span data-ttu-id="c98b7-133">Wprowadzenie do korzystania z LINQ</span><span class="sxs-lookup"><span data-stu-id="c98b7-133">Getting Started with LINQ</span></span>](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
