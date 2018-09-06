---
title: 'Porady: wykonywanie zapytania, które zwraca typy złożone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: 013f1980d2ea13927871719aeea293cfce38b4d5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861897"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="4707d-102">Porady: wykonywanie zapytania, które zwraca typy złożone</span><span class="sxs-lookup"><span data-stu-id="4707d-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="4707d-103">W tym temacie przedstawiono sposób wykonywania [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zwraca jednostki typu obiektów, które zawierają właściwość typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="4707d-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="4707d-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="4707d-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="4707d-105">Dodaj [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) do projektu i skonfiguruj projekt, aby użyć [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4707d-105">Add the [AdventureWorks Sales Model](https://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="4707d-106">Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreator modelu Entity Data Model](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="4707d-106">For more information, see [How to: Use the Entity Data Model Wizard](https://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="4707d-107">Na stronie kodowej dla aplikacji, Dodaj następujący kod `using` instrukcji (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="4707d-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="4707d-108">Kliknij dwukrotnie plik edmx, aby wyświetlić model w [okna przeglądarki modelu](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) Projektant jednostki.</span><span class="sxs-lookup"><span data-stu-id="4707d-108">Double click the .edmx file to display the model in the [Model Browser window](https://msdn.microsoft.com/library/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="4707d-109">Na powierzchni projektanta jednostki wybierz `Email` i `Phone` właściwości `Contact` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz pozycję **refaktoryzacji na nowy typ złożony**.</span><span class="sxs-lookup"><span data-stu-id="4707d-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="4707d-110">Nowy typ złożony z wybranym `Email` i `Phone` właściwości jest dodawany do **przeglądarka modeli**.</span><span class="sxs-lookup"><span data-stu-id="4707d-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="4707d-111">Typ złożony jest nadawana nazwa domyślna: zmiana nazwy typu, który ma `EmailPhone` w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="4707d-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="4707d-112">Ponadto nowy `ComplexProperty` właściwość została dodana do `Contact` typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="4707d-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="4707d-113">Zmień nazwę właściwości do `EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="4707d-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="4707d-114">Uzyskać informacji o tworzeniu i modyfikowaniu złożonych typów za pomocą Kreator modelu Entity Data Model, zobacz [jak: Refaktoryzuj istniejących właściwości do właściwości złożonej typu](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) i [jak: tworzenie i modyfikowanie typów złożonych](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="4707d-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://msdn.microsoft.com/library/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](https://msdn.microsoft.com/library/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4707d-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="4707d-115">Example</span></span>  
 <span data-ttu-id="4707d-116">Poniższy przykład wykonuje zapytanie, które zwraca kolekcję `Contact` obiektów i zostaną wyświetlone dwie właściwości `Contact` obiektów: `ContactID` i wartości `EmailPhoneComplexType` typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="4707d-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
