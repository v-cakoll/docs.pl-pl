---
title: "Porady: kwerenda zwraca typów złożonych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9bdd2ba859e97be12cfc4049c73c33ce1402e355
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="bc15e-102">Porady: kwerenda zwraca typów złożonych</span><span class="sxs-lookup"><span data-stu-id="bc15e-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="bc15e-103">W tym temacie przedstawiono sposób wykonania [!INCLUDE[esql](../../../../../includes/esql-md.md)] kwerendę, która zwraca jednostki typu obiektów, które zawierają właściwość typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="bc15e-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="bc15e-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="bc15e-104">To run the code in this example</span></span>  
  
1.  <span data-ttu-id="bc15e-105">Dodaj [modelu sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) do projektu i konfigurowanie projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc15e-105">Add the [AdventureWorks Sales Model](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) to your project and configure your project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="bc15e-106">Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span><span class="sxs-lookup"><span data-stu-id="bc15e-106">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).</span></span>  
  
2.  <span data-ttu-id="bc15e-107">Na stronie kodu aplikacji, Dodaj następujący `using` instrukcje (`Imports` w języku Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="bc15e-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3.  <span data-ttu-id="bc15e-108">Kliknij dwukrotnie plik edmx do wyświetlenia w modelu [okna przeglądarki modelu](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) programu Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="bc15e-108">Double click the .edmx file to display the model in the [Model Browser window](http://msdn.microsoft.com/en-us/94e836e8-a5ea-47ff-aa3e-599d8a02ebfd) of the Entity Designer.</span></span> <span data-ttu-id="bc15e-109">Na powierzchni Projektanta obiektów wybierz `Email` i `Phone` właściwości `Contact` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz **Refaktoryzuj na nowy typ złożony**.</span><span class="sxs-lookup"><span data-stu-id="bc15e-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4.  <span data-ttu-id="bc15e-110">Nowy typ złożony z wybranym `Email` i `Phone` właściwości jest dodawane do **przeglądarki modelu**.</span><span class="sxs-lookup"><span data-stu-id="bc15e-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="bc15e-111">Typ złożony podano nazwę domyślną: Zmień nazwę typu do `EmailPhone` w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="bc15e-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="bc15e-112">Ponadto nowy `ComplexProperty` właściwość została dodana do `Contact` typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="bc15e-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="bc15e-113">Zmień nazwę właściwości`EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="bc15e-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="bc15e-114">Uzyskać informacji o tworzeniu i modyfikowaniu typów złożonych za pomocą Kreatora modelu danych jednostki, zobacz [porady: Refaktoryzuj istniejącej właściwości w złożonych właściwości typu](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb) i [jak: utworzyć i zmodyfikować typów złożonych](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span><span class="sxs-lookup"><span data-stu-id="bc15e-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](http://msdn.microsoft.com/en-us/5b2eb3b3-693d-42cb-b43a-405812d677eb) and [How to: Create and Modify Complex Types](http://msdn.microsoft.com/en-us/afb8e206-0ffe-4597-b6d4-6ab566897e1d).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc15e-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="bc15e-115">Example</span></span>  
 <span data-ttu-id="bc15e-116">Poniższy przykład wykonuje zapytanie zwraca kolekcję `Contact` obiekty i wyświetla dwie właściwości `Contact` obiektów: `ContactID` i wartości `EmailPhoneComplexType` typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="bc15e-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
