---
title: "Opcja kodowania wystąpienia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="0ae1f-102">Opcja kodowania wystąpienia</span><span class="sxs-lookup"><span data-stu-id="0ae1f-102">Instance Encoding Option</span></span>
<span data-ttu-id="0ae1f-103">**Opcji kodowanie wystąpienia** właściwość w magazynie wystąpień przepływu pracy SQL umożliwia określenie, czy dostawca trwałości SQL należy skompresować informacji stanu wystąpienia przepływu pracy przy użyciu algorytmu GZip przed zapisaniem informacje w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="0ae1f-104">Dozwolone wartości dla tej właściwości: GZip i brak.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="0ae1f-105">Wartość domyślna to Brak.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-105">The default value is None.</span></span> <span data-ttu-id="0ae1f-106">Poniższa lista zawiera opis tych opcji.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="0ae1f-107">**GZip**.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-107">**GZip**.</span></span> <span data-ttu-id="0ae1f-108">Dostawca trwałości koduje informacje o stanie przy użyciu algorytmu GZip przed wprowadzeniem trwałych informacje o stanie w bazie danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="0ae1f-109">**Brak**.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-109">**None**.</span></span> <span data-ttu-id="0ae1f-110">Dostawca trwałości nie przeprowadza kodowania informacje o stanie przed zapisaniem informacji do bazy danych trwałości.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="0ae1f-111">Kodowanie informacji stanu wystąpienia przepływu pracy za pomocą GZip zmniejsza zużycie pamięci w bazie danych SQL i zmniejsza zużycie sieciowych, jeśli baza danych znajduje się na innym komputerze w sieci z komputera, na którym jest hosta usługi przepływu pracy uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="0ae1f-112">Ogólne wskazówki jest skonfigurowanie **opcji kodowanie wystąpienia** właściwości **Brak** Jeśli stanu wystąpienia przepływu pracy jest mała.</span><span class="sxs-lookup"><span data-stu-id="0ae1f-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
