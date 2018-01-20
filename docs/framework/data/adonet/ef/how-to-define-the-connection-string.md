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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 355d313fd607ccf85ba55b09b9ece4d9c88e298f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-the-connection-string"></a><span data-ttu-id="82f5a-102">Porady: Definiowanie parametrów połączenia</span><span class="sxs-lookup"><span data-stu-id="82f5a-102">How to: Define the Connection String</span></span>
<span data-ttu-id="82f5a-103">W tym temacie przedstawiono sposób zdefiniowanie ciągu połączenia, używaną podczas nawiązywania połączenia z modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="82f5a-103">This topic shows how to define the connection string that is used when connecting to a conceptual model.</span></span> <span data-ttu-id="82f5a-104">W tym temacie jest oparta na [sprzedaży AdventureWorks](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="82f5a-104">This topic is based on the [AdventureWorks Sales](http://msdn.microsoft.com/library/f16cd988-673f-4376-b034-129ca93c7832) conceptual model.</span></span> <span data-ttu-id="82f5a-105">Model sprzedaży AdventureWorks jest używany w tematach dotyczących zadań w [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="82f5a-105">The AdventureWorks Sales Model is used throughout the task-related topics in the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] documentation.</span></span> <span data-ttu-id="82f5a-106">W tym temacie założono, że została już skonfigurowana [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] i zdefiniowane AdventureWorks modelu sprzedaży.</span><span class="sxs-lookup"><span data-stu-id="82f5a-106">This topic assumes that you have already configured the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] and defined the AdventureWorks Sales Model.</span></span> <span data-ttu-id="82f5a-107">Aby uzyskać więcej informacji, zobacz [porady: ręczne definiowanie modelu i mapowania plików](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span><span class="sxs-lookup"><span data-stu-id="82f5a-107">For more information, see [How to: Manually Define the Model and Mapping Files](http://msdn.microsoft.com/library/d4fd6864-f2a1-48f0-aa32-1e318775a99a).</span></span> <span data-ttu-id="82f5a-108">Procedury przedstawione w tym temacie znajdują się również w [porady: ręczne konfigurowanie projektu programu Entity Framework](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span><span class="sxs-lookup"><span data-stu-id="82f5a-108">The procedures in this topic are also included in [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/library/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82f5a-109">Jeśli używasz [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] kreatora w [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] projektu, automatycznie generuje plik edmx i konfiguruje projektu do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="82f5a-109">If you use the [!INCLUDE[adonet_edm](../../../../../includes/adonet-edm-md.md)] Wizard in a [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] project, it automatically generates an .edmx file and configures the project to use the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span> <span data-ttu-id="82f5a-110">Aby uzyskać więcej informacji, zobacz [porady: Użyj Kreatora modelu danych jednostki](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span><span class="sxs-lookup"><span data-stu-id="82f5a-110">For more information, see [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/library/dadb058a-c5d9-4c5c-8b01-28044112231d)</span></span>  
  
### <a name="to-define-the-entity-framework-connection-string"></a><span data-ttu-id="82f5a-111">Aby określić parametry połączenia programu Entity Framework</span><span class="sxs-lookup"><span data-stu-id="82f5a-111">To define the Entity Framework connection string</span></span>  
  
-   <span data-ttu-id="82f5a-112">Otwórz plik konfiguracji projektu aplikacji (app.config) i dodaj następujące parametry połączenia:</span><span class="sxs-lookup"><span data-stu-id="82f5a-112">Open the project's application configuration file (app.config) and add the following connection string:</span></span>  
  
  
  
     <span data-ttu-id="82f5a-113">Jeśli projekt nie ma pliku konfiguracji aplikacji, możesz dodać kategorię, wybierając **Dodaj nowy element** z **projektu** menu, wybierając **ogólne** kategorii, Wybieranie **pliku konfiguracji aplikacji**, a następnie klikając pozycję **Dodaj**.</span><span class="sxs-lookup"><span data-stu-id="82f5a-113">If your project does not have an application configuration file, you can add one by selecting **Add New Item** from the **Project** menu, selecting the **General** category, selecting **Application Configuration File**, and then clicking **Add**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82f5a-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="82f5a-114">See Also</span></span>  
 [<span data-ttu-id="82f5a-115">Szybki start</span><span class="sxs-lookup"><span data-stu-id="82f5a-115">Quickstart</span></span>](http://msdn.microsoft.com/library/0bc534be-789f-4819-b9f6-76e51d961675)  
 [<span data-ttu-id="82f5a-116">Porady: Tworzenie nowego pliku edmx</span><span class="sxs-lookup"><span data-stu-id="82f5a-116">How to: Create a New .edmx File</span></span>](http://msdn.microsoft.com/library/beb8189e-e51c-4051-839c-9902c224abf2)  
 [<span data-ttu-id="82f5a-117">ADO.NET Entity Data Model Tools</span><span class="sxs-lookup"><span data-stu-id="82f5a-117">ADO.NET Entity Data Model  Tools</span></span>](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)
