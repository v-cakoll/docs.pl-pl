---
title: 'Instrukcje: Wykonywanie zapytania, które zwraca typy złożone'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2209fdb-70ef-4dea-8bb8-097fe96f5563
ms.openlocfilehash: b08b220e969ad1c400413978c85b2f107d64a688
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854642"
---
# <a name="how-to-execute-a-query-that-returns-complex-types"></a><span data-ttu-id="cf855-102">Instrukcje: Wykonywanie zapytania, które zwraca typy złożone</span><span class="sxs-lookup"><span data-stu-id="cf855-102">How to: Execute a Query that Returns Complex Types</span></span>
<span data-ttu-id="cf855-103">W tym temacie pokazano, jak wykonać [!INCLUDE[esql](../../../../../includes/esql-md.md)] zapytanie, które zwraca obiekty typu jednostki, które zawierają właściwość typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="cf855-103">This topic shows how to execute an [!INCLUDE[esql](../../../../../includes/esql-md.md)] query that returns entity type objects that contain a property of a complex type.</span></span>  
  
### <a name="to-run-the-code-in-this-example"></a><span data-ttu-id="cf855-104">Aby uruchomić kod w tym przykładzie</span><span class="sxs-lookup"><span data-stu-id="cf855-104">To run the code in this example</span></span>  
  
1. <span data-ttu-id="cf855-105">Dodaj [model sprzedaży AdventureWorks](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) do projektu i skonfiguruj projekt tak, aby korzystał z Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cf855-105">Add the [AdventureWorks Sales Model](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks) to your project and configure your project to use the Entity Framework.</span></span> <span data-ttu-id="cf855-106">Aby uzyskać więcej informacji, zobacz [jak: Użyj kreatora](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100))Entity Data Model.</span><span class="sxs-lookup"><span data-stu-id="cf855-106">For more information, see [How to: Use the Entity Data Model Wizard](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738677(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="cf855-107">Na stronie kodowej aplikacji Dodaj następujące `using` instrukcje (`Imports` w Visual Basic):</span><span class="sxs-lookup"><span data-stu-id="cf855-107">In the code page for your application, add the following `using` statements (`Imports` in Visual Basic):</span></span>  
  
     [!code-csharp[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#namespaces)]
     [!code-vb[DP EntityServices Concepts#Namespaces](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#namespaces)]  
  
3. <span data-ttu-id="cf855-108">Kliknij dwukrotnie plik. edmx, aby wyświetlić model w [oknie przeglądarki modeli](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) Entity Designer.</span><span class="sxs-lookup"><span data-stu-id="cf855-108">Double click the .edmx file to display the model in the [Model Browser window](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738483(v=vs.100)) of the Entity Designer.</span></span> <span data-ttu-id="cf855-109">Na powierzchni Entity Designer wybierz `Email` właściwości `Contact` i `Phone` typu jednostki, a następnie kliknij prawym przyciskiem myszy i wybierz opcję **refaktoryzacji do nowego typu złożonego**.</span><span class="sxs-lookup"><span data-stu-id="cf855-109">On the Entity Designer surface, select the `Email` and `Phone` properties of the `Contact` entity type, then right-click and select **Refactor into New Complex Type**.</span></span>  
  
4. <span data-ttu-id="cf855-110">Nowy typ złożony z wybranymi `Email` i `Phone` właściwościami zostanie dodany do **przeglądarki modelu**.</span><span class="sxs-lookup"><span data-stu-id="cf855-110">A new complex type with the selected `Email` and `Phone` properties is added to the **Model Browser**.</span></span> <span data-ttu-id="cf855-111">Typ złożony otrzymuje nazwę domyślną: Zmień nazwę typu na `EmailPhone` w oknie **Właściwości** .</span><span class="sxs-lookup"><span data-stu-id="cf855-111">The complex type is given a default name: rename the type to `EmailPhone` in the **Properties** window.</span></span> <span data-ttu-id="cf855-112">Ponadto nowa `ComplexProperty` właściwość jest dodawana `Contact` do typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="cf855-112">Also, a new `ComplexProperty` property is added to the `Contact` entity type.</span></span> <span data-ttu-id="cf855-113">Zmień nazwę właściwości na`EmailPhoneComplexType.`</span><span class="sxs-lookup"><span data-stu-id="cf855-113">Rename the property to `EmailPhoneComplexType.`</span></span>  
  
     <span data-ttu-id="cf855-114">Informacje o tworzeniu i modyfikowaniu typów złożonych przy użyciu kreatora Entity Data Model można znaleźć w [temacie How to: Refaktoryzacja istniejących właściwości do właściwości](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) typu złożonego i [instrukcje: Tworzenie i modyfikowanie typów](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100))złożonych.</span><span class="sxs-lookup"><span data-stu-id="cf855-114">For information about creating and modifying complex types by using the Entity Data Model Wizard, see [How to: Refactor Existing Properties into a Complex Type Property](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456814(v=vs.100)) and [How to: Create and Modify Complex Types](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd456820(v=vs.100)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf855-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf855-115">Example</span></span>  
 <span data-ttu-id="cf855-116">Poniższy przykład wykonuje zapytanie, `Contact` które zwraca kolekcję obiektów i wyświetla dwie właściwości `Contact` obiektów: `ContactID` oraz wartości `EmailPhoneComplexType` typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="cf855-116">The following example executes a query that returns a collection of `Contact` objects and displays two properties of the `Contact` objects: `ContactID` and the values of the `EmailPhoneComplexType` complex type.</span></span>  
  
 [!code-csharp[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/source.cs#complextypewithentitycommand)]
 [!code-vb[DP EntityServices Concepts#ComplexTypeWithEntityCommand](../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp entityservices concepts/vb/source.vb#complextypewithentitycommand)]
