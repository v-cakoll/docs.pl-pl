---
title: Działanie ukończenia wystąpienia
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 646015fbcdb7c734ae8584c7ca3979d64b81339f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791121"
---
# <a name="instance-completion-action"></a><span data-ttu-id="8e23a-102">Działanie ukończenia wystąpienia</span><span class="sxs-lookup"><span data-stu-id="8e23a-102">Instance Completion Action</span></span>
<span data-ttu-id="8e23a-103">**Działanie ukończenia wystąpienia** właściwość Store wystąpienia przepływu pracy SQL pozwala określić, czy dane i metadane wystąpienia przepływu pracy jest usuwane z bazy danych trwałości po ukończeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8e23a-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="8e23a-104">Dozwolone wartości dla tej właściwości to **DeleteAll** i **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="8e23a-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="8e23a-105">Na poniższej liście opisano te opcje:</span><span class="sxs-lookup"><span data-stu-id="8e23a-105">The following list describes these options:</span></span>  
  
- <span data-ttu-id="8e23a-106">**DeleteAll (ustawienie domyślne).**</span><span class="sxs-lookup"><span data-stu-id="8e23a-106">**DeleteAll (default).**</span></span> <span data-ttu-id="8e23a-107">Jeśli wartość właściwości jest równa DeleteAll, danych i metadanych wystąpienia przepływu pracy został usunięty z bazy danych trwałości po ukończeniu wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="8e23a-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>  
  
- <span data-ttu-id="8e23a-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="8e23a-108">**DeleteNothing.**</span></span> <span data-ttu-id="8e23a-109">Jeśli wartość właściwości jest równa DeleteNothing, danych i metadanych wystąpienia przepływu pracy jest przechowywana w bazie danych trwałości mimo wystąpienia są wykonywane.</span><span class="sxs-lookup"><span data-stu-id="8e23a-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="8e23a-110">Przechowywanie informacji o stanie wystąpienie po ukończone przyczyny wystąpienia bazy danych trwałości zwiększanie się rozmiaru.</span><span class="sxs-lookup"><span data-stu-id="8e23a-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="8e23a-111">Wzrostem rozmiaru bazy danych operacji bazy danych, wykonywanych przez podsystem trwałości trwać dłużej, warto je Wyczyść informacje o stanie wystąpienie z bazy danych trwałości okresowo, aby ma wykonywać na poziomie usług integracji, które spełniają Twoje wymagań dotyczących wydajności.</span><span class="sxs-lookup"><span data-stu-id="8e23a-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
