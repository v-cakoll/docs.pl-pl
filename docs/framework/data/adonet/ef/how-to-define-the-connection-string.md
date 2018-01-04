---
title: "Porady: Definiowanie parametrów połączenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6027335d-4e26-420d-9151-6523289b1989
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e42fba03b50c0ffd765bbe25ef60b3317ed1b307
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="2b48b-102">Porady: Definiowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="2b48b-102">How to: Define the Connection String</span></span>
<span data-ttu-id="2b48b-103">W tym temacie przedstawiono sposób zdefiniowanie ciągu połączenia, używaną podczas nawiązywania połączenia z modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="2b48b-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="2b48b-104">W tym temacie jest oparta na [sprzedaży AdventureWorks](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="2b48b-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/en-us/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="2b48b-105">Model sprzedaży AdventureWorks jest używany w tematach dotyczących zadań w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="2b48b-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="2b48b-106">W tym temacie założono, że została już skonfigurowana [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i zdefiniowane AdventureWorks modelu sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="2b48b-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b48b-107">Aby uzyskać więcej informacji, zobacz [porady: ręczne definiowanie modelu i mapowania plików](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span><span class="sxs-lookup"><span data-stu-id="2b48b-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/en-us/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="2b48b-108">Procedury przedstawione w tym temacie znajdują się również w [porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span><span class="sxs-lookup"><span data-stu-id="2b48b-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2b48b-109">Jeśli używasz [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kreatora w [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu, automatycznie generuje plik edmx i konfiguruje projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2b48b-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="2b48b-110">Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="2b48b-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="2b48b-111">Aby określić parametry połączenia programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2b48b-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="2b48b-112">Otwórz plik konfiguracji projektu aplikacji (app.config) i dodaj następujące parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="2b48b-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="2b48b-113">Jeśli projekt nie ma pliku konfiguracji aplikacji, możesz dodać kategorię, wybierając **Dodaj nowy element** z **projektu** menu, wybierając **ogólne** kategorii, Wybieranie **pliku konfiguracji aplikacji**, a następnie klikając pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="2b48b-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b48b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b48b-114">See Also</span></span>  
 [<span data-ttu-id="2b48b-115">Szybki start</span><span class="sxs-lookup"><span data-stu-id="2b48b-115">Quickstart</span></span>](http://msdn.microsoft.com/en-us/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="2b48b-116">Porady: Tworzenie nowego pliku edmx</span><span class="sxs-lookup"><span data-stu-id="2b48b-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="2b48b-117">ADO.NET Entity Data Model Tools</span><span class="sxs-lookup"><span data-stu-id="2b48b-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)
