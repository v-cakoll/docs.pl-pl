---
title: Dostosowywanie operacji wstawiania, aktualizowania i usuwania
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: 114447fd45806e567b4fde8e9e74138c096bff07
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743571"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="92827-102">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="92827-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="92827-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generuje dynamiczny język SQL, aby zaimplementować wstawiania, odczytu, aktualizacji i usuwania operacji.</span><span class="sxs-lookup"><span data-stu-id="92827-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="92827-104">W praktyce jednak zwykle dostosować aplikację do własnych potrzeb biznesowych.</span><span class="sxs-lookup"><span data-stu-id="92827-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92827-105">Jeśli używasz programu Visual Studio umożliwia Object Relational Designer dostosować wstawiania, aktualizowania i usuwania działań.</span><span class="sxs-lookup"><span data-stu-id="92827-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="92827-106">W tej sekcji tematów opisano techniki, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia do dostosowywania wstawiania, odczytu, aktualizacji i operacje usuwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="92827-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92827-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="92827-107">In This Section</span></span>  
 [<span data-ttu-id="92827-108">Dostosowywanie operacji: omówienie</span><span class="sxs-lookup"><span data-stu-id="92827-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="92827-109">W tym artykule opisano różne techniki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapewnia do dostosowywania wstawiania, odczytu, aktualizacji i operacje usuwania.</span><span class="sxs-lookup"><span data-stu-id="92827-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="92827-110">Operacje wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="92827-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="92827-111">W tym artykule opisano [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] domyślnych procesów dla manipulowanie danymi bazy danych.</span><span class="sxs-lookup"><span data-stu-id="92827-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="92827-112">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="92827-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="92827-113">Zawiera opis roli dewelopera we wdrażaniu wymagań, które nie są wymuszane przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92827-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="92827-114">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="92827-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="92827-115">W tym artykule opisano, jak za pomocą metod częściowych Przesłaniaj metody wygenerowany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="92827-115">Describes how to use partial methods to override autogenerated methods.</span></span>
