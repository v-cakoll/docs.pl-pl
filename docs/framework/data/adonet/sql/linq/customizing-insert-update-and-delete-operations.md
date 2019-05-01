---
title: Dostosowywanie operacji wstawiania, aktualizowania i usuwania
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: b4578a030300872bf4e0bab30b8daf12544be0cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032776"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="a8f3c-102">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="a8f3c-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="a8f3c-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczny język SQL, aby zaimplementować wstawiania, odczytu, aktualizacji i usuwania operacji.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="a8f3c-104">W praktyce jednak zwykle dostosować aplikację do własnych potrzeb biznesowych.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8f3c-105">Jeśli używasz programu Visual Studio, możesz użyć [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] dostosować wstawiania, aktualizowania i usuwania akcji.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-105">If you are using Visual Studio, you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="a8f3c-106">W tej sekcji tematów opisano techniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia do dostosowywania wstawiania, odczytu, aktualizacji i operacje usuwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a8f3c-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="a8f3c-107">In This Section</span></span>  
 [<span data-ttu-id="a8f3c-108">Dostosowywanie operacji: omówienie</span><span class="sxs-lookup"><span data-stu-id="a8f3c-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="a8f3c-109">W tym artykule opisano różne techniki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia do dostosowywania wstawiania, odczytu, aktualizacji i operacje usuwania.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="a8f3c-110">Operacje wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="a8f3c-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="a8f3c-111">W tym artykule opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślnych procesów dla manipulowanie danymi bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="a8f3c-112">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="a8f3c-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="a8f3c-113">Zawiera opis roli dewelopera we wdrażaniu wymagań, które nie są wymuszane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8f3c-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="a8f3c-114">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="a8f3c-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="a8f3c-115">W tym artykule opisano, jak za pomocą metod częściowych Przesłaniaj metody wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="a8f3c-115">Describes how to use partial methods to override autogenerated methods.</span></span>
