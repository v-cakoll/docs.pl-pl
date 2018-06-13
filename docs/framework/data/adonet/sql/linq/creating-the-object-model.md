---
title: Tworzenie modelu obiektów
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 7724d6e75b350e5c57f090d42ef1f49c4d3593b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359936"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="9eef7-102">Tworzenie modelu obiektów</span><span class="sxs-lookup"><span data-stu-id="9eef7-102">Creating the Object Model</span></span>
<span data-ttu-id="9eef7-103">Można utworzyć modelu obiektów z istniejącej bazy danych i używać modelu w stanie domyślnym.</span><span class="sxs-lookup"><span data-stu-id="9eef7-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="9eef7-104">Można również dostosować wiele aspektów modelu i jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="9eef7-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="9eef7-105">Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do utworzenia obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="9eef7-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9eef7-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="9eef7-106">In This Section</span></span>  
 [<span data-ttu-id="9eef7-107">Instrukcje: Generowanie modelu obiektu w języku Visual Basic lub C#</span><span class="sxs-lookup"><span data-stu-id="9eef7-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="9eef7-108">W tym artykule opisano sposób użycia narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="9eef7-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="9eef7-109">Również Link do [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla użytkowników programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="9eef7-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for Visual Studio users</span></span>  
  
 [<span data-ttu-id="9eef7-110">Instrukcje: Generowanie modelu obiektu jako zewnętrznego pliku</span><span class="sxs-lookup"><span data-stu-id="9eef7-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="9eef7-111">Opisuje sposób generowania pliku zewnętrznego mapowania zamiast stosowania mapowań opartych na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="9eef7-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="9eef7-112">Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="9eef7-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="9eef7-113">Opisuje sposób generowania kodu języka Visual Basic lub C# z pliku DBML metadanych.</span><span class="sxs-lookup"><span data-stu-id="9eef7-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="9eef7-114">Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania</span><span class="sxs-lookup"><span data-stu-id="9eef7-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="9eef7-115">Opisuje sposób sprawdzania poprawności mapowania plików, które zostały zmodyfikowane (zaawansowane).</span><span class="sxs-lookup"><span data-stu-id="9eef7-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="9eef7-116">Instrukcje: Umożliwianie serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="9eef7-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="9eef7-117">Opisuje sposób dodawania odpowiednie atrybuty dokonanie serializacji jednostek.</span><span class="sxs-lookup"><span data-stu-id="9eef7-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="9eef7-118">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="9eef7-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="9eef7-119">W tym artykule opisano, jak napisać własny kod mapowania lub Dostosuj kod, który został wygenerowany automatycznie za pomocą edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="9eef7-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9eef7-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="9eef7-120">Related Sections</span></span>  
 [<span data-ttu-id="9eef7-121">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9eef7-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="9eef7-122">Zawiera szczegółowe informacje na temat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obiektu modelu.</span><span class="sxs-lookup"><span data-stu-id="9eef7-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="9eef7-123">Typowe kroki dotyczące korzystania z LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="9eef7-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="9eef7-124">Opisano typowe kroki, które należy wykonać, aby zaimplementować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9eef7-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
