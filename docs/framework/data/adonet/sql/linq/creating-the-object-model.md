---
title: Tworzenie modelu obiektu
ms.date: 03/30/2017
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
ms.openlocfilehash: 7724d6e75b350e5c57f090d42ef1f49c4d3593b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032451"
---
# <a name="creating-the-object-model"></a><span data-ttu-id="86127-102">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="86127-102">Creating the Object Model</span></span>
<span data-ttu-id="86127-103">Można utworzyć modelu obiektu z istniejącej bazy danych i używania tego modelu w stanie domyślnym.</span><span class="sxs-lookup"><span data-stu-id="86127-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="86127-104">Można również dostosować wiele aspektów modelu i jego zachowanie.</span><span class="sxs-lookup"><span data-stu-id="86127-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="86127-105">Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] do tworzenia modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="86127-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86127-106">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="86127-106">In This Section</span></span>  
 [<span data-ttu-id="86127-107">Instrukcje: Generowanie modelu obiektu w języku Visual Basic lubC#</span><span class="sxs-lookup"><span data-stu-id="86127-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="86127-108">W tym artykule opisano sposób użycia narzędzia wiersza polecenia SQLMetal.</span><span class="sxs-lookup"><span data-stu-id="86127-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="86127-109">Udostępnia także link do [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dla użytkowników programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="86127-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for Visual Studio users</span></span>  
  
 [<span data-ttu-id="86127-110">Instrukcje: Generowanie modelu obiektu jako zewnętrznego pliku</span><span class="sxs-lookup"><span data-stu-id="86127-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="86127-111">Opisuje sposób generowania pliku mapowanie zewnętrzne zamiast mapowanie oparte na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="86127-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="86127-112">Instrukcje: Generowanie kodu dostosowane przez zmodyfikowanie pliku DBML</span><span class="sxs-lookup"><span data-stu-id="86127-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="86127-113">W tym artykule opisano sposób generowania kodu języka Visual Basic lub C# kodu z pliku metadanych DBML.</span><span class="sxs-lookup"><span data-stu-id="86127-113">Describes how to generate Visual Basic or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="86127-114">Instrukcje: Weryfikacja DBML i zewnętrznych plików mapowania</span><span class="sxs-lookup"><span data-stu-id="86127-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="86127-115">W tym artykule opisano sposób sprawdzania poprawności mapowania plików, które zostały zmodyfikowane (zaawansowane).</span><span class="sxs-lookup"><span data-stu-id="86127-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="86127-116">Instrukcje: Umożliwianie serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="86127-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="86127-117">W tym artykule opisano sposób dodawania odpowiednich atrybutów, które mają umożliwianie serializacji jednostek.</span><span class="sxs-lookup"><span data-stu-id="86127-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="86127-118">Instrukcje: Dostosowywanie klas jednostek za pomocą edytora kodu</span><span class="sxs-lookup"><span data-stu-id="86127-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="86127-119">W tym artykule opisano sposób używania edytora kodu do pisania własnego kodu mapowania lub dostosować program code, który został wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="86127-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86127-120">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="86127-120">Related Sections</span></span>  
 [<span data-ttu-id="86127-121">Model obiektu LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="86127-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="86127-122">Zawiera szczegółowe informacje na temat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] modelu obiektów.</span><span class="sxs-lookup"><span data-stu-id="86127-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="86127-123">Typowe kroki dotyczące korzystania z LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="86127-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="86127-124">Opisano typowe czynności, które należy wykonać, aby zaimplementować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="86127-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
