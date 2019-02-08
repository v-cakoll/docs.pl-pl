---
title: 'Instrukcje: Wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4f5639bf-bb7f-4982-bb1d-c7caa4348888
ms.openlocfilehash: 0e7479ee166ba0b90eacdd0ea865374f70167bc9
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/07/2019
ms.locfileid: "55826385"
---
# <a name="how-to-execute-a-parameterized-stored-procedure-using-entitycommand"></a><span data-ttu-id="8a8e4-102">Instrukcje: Wykonaj procedurę składowaną z parametrami przy użyciu EntityCommand</span><span class="sxs-lookup"><span data-stu-id="8a8e4-102">How to: Execute a Parameterized Stored Procedure Using EntityCommand</span></span>
<span data-ttu-id="8a8e4-103">W tym temacie pokazano, jak wykonać procedurę składowaną z parametrami przy użyciu <xref:System.Data.EntityClient.EntityCommand> klasy.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-103">This topic shows how to execute a parameterized stored procedure by using the <xref:System.Data.EntityClient.EntityCommand> class.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="8a8e4-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="8a8e4-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="8a8e4-105">Dodaj [modelu School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a8e4-105">Add the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="8a8e4-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj Kreatora modelu danych jednostki](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8a8e4-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="8a8e4-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="8a8e4-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="8a8e4-108">Importuj `GetStudentGrades` procedury składowanej, a następnie określ `CourseGrade` jednostki jako typ zwracany.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-108">Import the `GetStudentGrades` stored procedure and specify `CourseGrade` entities as a return type.</span></span> <span data-ttu-id="8a8e4-109">Aby uzyskać informacje o sposobie importowania procedury składowanej, zobacz [jak: Importowanie procedury składowanej](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="8a8e4-109">For information on how to import a stored procedure, see [How to: Import a Stored Procedure](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896231(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a8e4-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="8a8e4-110">Example</span></span>  
 <span data-ttu-id="8a8e4-111">Poniższy kod wykonuje `GetStudentGrades` procedury składowanej gdzie `StudentId` jest wymaganym parametrem.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-111">The following code executes the `GetStudentGrades` stored procedure where `StudentId` is a required parameter.</span></span> <span data-ttu-id="8a8e4-112">Wyniki są następnie odczytywane przez <xref:System.Data.EntityClient.EntityDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8a8e4-112">The results are then read by an <xref:System.Data.EntityClient.EntityDataReader>.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#storedprocwithentitycommand)]
 [!code-vb[DP EntityServices Concepts#StoredProcWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#storedprocwithentitycommand)]  
  
## <a name="see-also"></a><span data-ttu-id="8a8e4-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a8e4-113">See also</span></span>
- [<span data-ttu-id="8a8e4-114">Dostawca EntityClient dla programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="8a8e4-114">EntityClient Provider for the Entity Framework</span></span>](../../../../../docs/framework/data/adonet/ef/entityclient-provider-for-the-entity-framework.md)
