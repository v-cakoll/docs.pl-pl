---
title: Działanie ukończenia wystąpienia
ms.date: 03/30/2017
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
ms.openlocfilehash: 698ac0ed5a7cbd4f6a5623cf8d9b6fbea1128d0a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044340"
---
# <a name="instance-completion-action"></a><span data-ttu-id="022ec-102">Działanie ukończenia wystąpienia</span><span class="sxs-lookup"><span data-stu-id="022ec-102">Instance Completion Action</span></span>

<span data-ttu-id="022ec-103">Właściwość **Akcja ukończenia wystąpienia** usługi SQL Workflow Store umożliwia określenie, czy dane i metadane wystąpień przepływów pracy są usuwane z bazy danych trwałości po zakończeniu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="022ec-103">The **Instance Completion Action** property of the SQL Workflow Instance Store lets you specify whether the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span> <span data-ttu-id="022ec-104">Dozwolone wartości tej właściwości to **DeleteAll** i **DeleteNothing**.</span><span class="sxs-lookup"><span data-stu-id="022ec-104">The allowed values for this property are **DeleteAll** and **DeleteNothing**.</span></span> <span data-ttu-id="022ec-105">Poniższa lista zawiera opis tych opcji:</span><span class="sxs-lookup"><span data-stu-id="022ec-105">The following list describes these options:</span></span>

- <span data-ttu-id="022ec-106">**DeleteAll (domyślnie).**</span><span class="sxs-lookup"><span data-stu-id="022ec-106">**DeleteAll (default).**</span></span> <span data-ttu-id="022ec-107">Jeśli wartość właściwości jest ustawiona na DeleteAll, dane i metadane wystąpień przepływów pracy są usuwane z bazy danych trwałości po zakończeniu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="022ec-107">If the value of the property is set to DeleteAll, the data and metadata of workflow instances is deleted from the persistence database after the instances are completed.</span></span>

- <span data-ttu-id="022ec-108">**DeleteNothing.**</span><span class="sxs-lookup"><span data-stu-id="022ec-108">**DeleteNothing.**</span></span> <span data-ttu-id="022ec-109">Jeśli wartość właściwości jest ustawiona na DeleteNothing, dane i metadane wystąpień przepływu pracy są przechowywane w bazie danych trwałości nawet po zakończeniu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="022ec-109">If the value of the property is set to DeleteNothing, the data and metadata of workflow instances is kept in the persistence database even after the instances are completed.</span></span>

  > [!CAUTION]
  > <span data-ttu-id="022ec-110">Zachowywanie informacji o stanie wystąpienia po zakończeniu wystąpień powoduje, że baza danych trwałości zostanie powiększona.</span><span class="sxs-lookup"><span data-stu-id="022ec-110">Keeping instance state information after the instances are completed causes the persistence database to grow in size.</span></span> <span data-ttu-id="022ec-111">Ponieważ rozmiar bazy danych powiększa operacje bazy danych wykonywane przez podsystem trwałości, w związku z czym konieczne będzie przeczyszczenie informacji o stanie wystąpienia z bazy danych trwałości okresowo, aby usługi były wykonywane na poziomie, który spełnia Twoje wymagania wymagania dotyczące wydajności.</span><span class="sxs-lookup"><span data-stu-id="022ec-111">As the size of the database grows the database operations that the persistence subsystem performs take longer, so you need to purge the instance state information from the persistence database periodically to have services perform at the level that satisfy your performance needs.</span></span>
