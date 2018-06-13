---
title: 'Porady: wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 68589cf8906e35313e261e373cf87017ffe6f8f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32760508"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="d5bf9-102">Porady: wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="d5bf9-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="d5bf9-103">W tym temacie pokazano, jak wykonać procedurę składowaną z parametrami przy użyciu <xref:System.Data.EntityClient.EntityCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="d5bf9-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="d5bf9-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="d5bf9-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="d5bf9-105">Dodaj [modelu służbowe](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) do projektu i konfigurowanie projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5bf9-105">Add the [School Model](http://msdn.microsoft.com/library/859a9587-81ea-4a45-9bc0-f8d330e1adac) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="d5bf9-106">Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="d5bf9-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="d5bf9-107">Na stronie kodu aplikacji, Dodaj następujący `using` instrukcje (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="d5bf9-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="d5bf9-108">Importuj `GetStudentGrades` procedury składowanej i określ `CourseGrade` jednostki jako typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="d5bf9-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="d5bf9-109">Uzyskać informacje o sposobie importowania procedury składowanej, zobacz [porady: importowanie procedurę składowaną](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span><span class="sxs-lookup"><span data-stu-id="d5bf9-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](http://msdn.microsoft.com/library/24e68bf4-bd6d-428d-bc35-92d7b8e3736d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5bf9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d5bf9-110">Example</span></span>  
 <span data-ttu-id="d5bf9-111">Poniższy kod wykonuje `GetStudentGrades` procedury składowanej gdzie `StudentId` jest wymagany parametr.</span><span class="sxs-lookup"><span data-stu-id="d5bf9-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="d5bf9-112">Wyniki są następnie odczytywane przez <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="d5bf9-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="d5bf9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d5bf9-113">See Also</span></span>  
 [<span data-ttu-id="d5bf9-114">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d5bf9-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
