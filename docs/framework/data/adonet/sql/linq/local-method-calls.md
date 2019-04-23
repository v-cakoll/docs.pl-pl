---
title: Wywoływania metody lokalnej
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34b5012-aee9-4994-9364-1d99d12b7463
ms.openlocfilehash: c8a4c29b1faa3c05f2cf32e9a60104b43a9b1c40
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074550"
---
# <a name="local-method-calls"></a><span data-ttu-id="30791-102">Wywoływania metody lokalnej</span><span class="sxs-lookup"><span data-stu-id="30791-102">Local Method Calls</span></span>
<span data-ttu-id="30791-103">Wywołanie metody lokalnej jest taki, który jest wykonywany w ramach modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="30791-103">A local method call is one that is executed within the object model.</span></span> <span data-ttu-id="30791-104">Wywołanie metody zdalnej jest jeden, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] przekłada się na SQL i przesyła je do aparatu bazy danych w celu wykonania.</span><span class="sxs-lookup"><span data-stu-id="30791-104">A remote method call is one that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] translates to SQL and transmits to the database engine for execution.</span></span> <span data-ttu-id="30791-105">Wywoływania metody lokalnej są wymagane podczas [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie może tłumaczyć wywołań do SQL.</span><span class="sxs-lookup"><span data-stu-id="30791-105">Local method calls are needed when [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] cannot translate the call into SQL.</span></span> <span data-ttu-id="30791-106">W przeciwnym razie <xref:System.InvalidOperationException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="30791-106">Otherwise, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="30791-107">Przykład 1</span><span class="sxs-lookup"><span data-stu-id="30791-107">Example 1</span></span>  
 <span data-ttu-id="30791-108">W poniższym przykładzie `Order` klasy jest mapowany do tabeli zamówienia w bazie danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="30791-108">In the following example, an `Order` class is mapped to the Orders table in the Northwind sample database.</span></span> <span data-ttu-id="30791-109">Metoda wystąpienia lokalnego, dodano do klasy.</span><span class="sxs-lookup"><span data-stu-id="30791-109">A local instance method has been added to the class.</span></span>  
  
 <span data-ttu-id="30791-110">Zapytanie 1, Konstruktor `Order` klasy jest wykonywana lokalnie.</span><span class="sxs-lookup"><span data-stu-id="30791-110">In Query 1, the constructor for the `Order` class is executed locally.</span></span> <span data-ttu-id="30791-111">W zapytania 2, jeśli [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] próbował tłumaczenie `LocalInstanceMethod()`w bazie SQL, próba zakończy się niepowodzeniem i <xref:System.InvalidOperationException> będzie zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="30791-111">In Query 2, if [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tried to translate `LocalInstanceMethod()`into SQL, the attempt would fail and an <xref:System.InvalidOperationException> exception would be thrown.</span></span> <span data-ttu-id="30791-112">Ale ponieważ [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia obsługę wywoływania metody lokalnej kwerenda2 nie spowoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="30791-112">But because [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides support for local method calls, Query2 will not throw an exception.</span></span>  
  
 [!code-csharp[DlinqLocalMethodCall#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/Program.cs#1)]
 [!code-vb[DlinqLocalMethodCall#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/Module1.vb#1)]  
  
 [!code-csharp[DlinqLocalMethodCall#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqLocalMethodCall/cs/northwind.cs#2)]
 [!code-vb[DlinqLocalMethodCall#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqLocalMethodCall/vb/northwind.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="30791-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="30791-113">See also</span></span>

- [<span data-ttu-id="30791-114">Informacje uzupełniające</span><span class="sxs-lookup"><span data-stu-id="30791-114">Background Information</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
