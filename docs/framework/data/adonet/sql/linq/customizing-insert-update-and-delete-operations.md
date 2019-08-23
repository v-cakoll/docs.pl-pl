---
title: Dostosowywanie operacji wstawiania, aktualizowania i usuwania
ms.date: 03/30/2017
ms.assetid: 07eef055-8f6c-414d-850e-d323ff946cd0
ms.openlocfilehash: f75f4b4caf6b72076a83bde2f2c659aab4c9707d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912565"
---
# <a name="customizing-insert-update-and-delete-operations"></a><span data-ttu-id="49b72-102">Dostosowywanie operacji wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="49b72-102">Customizing Insert, Update, and Delete Operations</span></span>
<span data-ttu-id="49b72-103">Domyślnie [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] program generuje dynamiczny kod SQL w celu zaimplementowania operacji INSERT, Read, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="49b72-103">By default, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] generates dynamic SQL to implement insert, read, update, and delete operations.</span></span> <span data-ttu-id="49b72-104">W tym przypadku zwykle dostosowuje się do potrzeb Twojej firmy.</span><span class="sxs-lookup"><span data-stu-id="49b72-104">In practice, however, you typically customize your application to suit your business needs.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49b72-105">Jeśli używasz programu Visual Studio, możesz użyć Object Relational Designer, aby dostosować akcje insert, Update i DELETE.</span><span class="sxs-lookup"><span data-stu-id="49b72-105">If you are using Visual Studio, you can use the Object Relational Designer to customize insert, update, and delete actions.</span></span>  
  
 <span data-ttu-id="49b72-106">W tej części tematów opisano metody umożliwiające [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostosowywanie operacji wstawiania, odczytu, aktualizacji i usuwania w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="49b72-106">This section of topics describes the techniques that [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations in your application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="49b72-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="49b72-107">In This Section</span></span>  
 [<span data-ttu-id="49b72-108">Operacje dostosowywania: omówienie</span><span class="sxs-lookup"><span data-stu-id="49b72-108">Customizing Operations: Overview</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-overview.md)  
 <span data-ttu-id="49b72-109">Opisuje różne techniki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] umożliwiające dostosowywanie operacji wstawiania, odczytu, aktualizacji i usuwania.</span><span class="sxs-lookup"><span data-stu-id="49b72-109">Describes the various techniques [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provides for customizing insert, read, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="49b72-110">Operacje wstawiania, aktualizowania i usuwania</span><span class="sxs-lookup"><span data-stu-id="49b72-110">Insert, Update, and Delete Operations</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/insert-update-and-delete-operations.md)  
 <span data-ttu-id="49b72-111">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Opisuje domyślne procesy manipulowania danymi bazy danych.</span><span class="sxs-lookup"><span data-stu-id="49b72-111">Describes the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] default processes for manipulating database data.</span></span>  
  
 [<span data-ttu-id="49b72-112">Obowiązki dewelopera podczas zastępowania domyślnego zachowania</span><span class="sxs-lookup"><span data-stu-id="49b72-112">Responsibilities of the Developer In Overriding Default Behavior</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md)  
 <span data-ttu-id="49b72-113">Opisuje rolę dewelopera w implementacji wymagań niewymuszonych przez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]program.</span><span class="sxs-lookup"><span data-stu-id="49b72-113">Describes the role of the developer in implementing requirements not enforced by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span>  
  
 [<span data-ttu-id="49b72-114">Dodawanie logiki biznesowej przy użyciu metod częściowych</span><span class="sxs-lookup"><span data-stu-id="49b72-114">Adding Business Logic By Using Partial Methods</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)  
 <span data-ttu-id="49b72-115">Opisuje sposób używania metod częściowych do przesłania metod generowanych automatycznie.</span><span class="sxs-lookup"><span data-stu-id="49b72-115">Describes how to use partial methods to override autogenerated methods.</span></span>
