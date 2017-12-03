---
title: "Wystąpienie zakończenia działania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a><span data-ttu-id="05d03-102">Wystąpienie zakończenia działania</span><span class="sxs-lookup"><span data-stu-id="05d03-102">Instance Completion Action</span></span>
<span data-ttu-id="05d03-103">**Wystąpienia ukończenia akcji** właściwość w magazynie wystąpień przepływu pracy SQL umożliwia określenie, czy dane i metadane wystąpienia przepływu pracy są usuwane z bazy danych trwałości po ukończeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="05d03-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="05d03-104">Dozwolone wartości dla tej właściwości **DeleteAll** i **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="05d03-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="05d03-105">Poniższa lista zawiera opis tych opcji:</span><span class="sxs-lookup"><span data-stu-id="05d03-105">The following list describes these options:</span></span>  
  
-   <span data-ttu-id="05d03-106">**DeleteAll (ustawienie domyślne).**</span><span class="sxs-lookup"><span data-stu-id="05d03-106">**DeleteAll (default).**</span></span> <span data-ttu-id="05d03-107">Jeśli wartość właściwości jest równa DeleteAll, dane i metadane wystąpienia przepływu pracy został usunięty z bazy danych trwałości po ukończeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="05d03-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
-   <span data-ttu-id="05d03-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="05d03-108">**DeleteNothing.**</span></span> <span data-ttu-id="05d03-109">Jeśli wartość właściwości jest równa DeleteNothing, dane i metadane wystąpienia przepływu pracy jest przechowywana w bazie danych trwałości nawet po zakończeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="05d03-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="05d03-110">Przechowywanie informacji o stanie wystąpienia po ukończone przyczyny wystąpienia bazy danych trwałości zwiększa się rozmiar.</span><span class="sxs-lookup"><span data-stu-id="05d03-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="05d03-111">Jak operacje bazy danych, które wykonuje podsystemu trwałości zwiększania rozmiaru bazy danych trwać dłużej, więc należy przeczyścić informacje o stanie wystąpienia z bazy danych trwałości okresowo, aby wykonać na poziomie usług, spełniających użytkownika wymagania związane z wydajnością.</span><span class="sxs-lookup"><span data-stu-id="05d03-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
