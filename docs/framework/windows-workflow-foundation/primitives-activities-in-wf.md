---
title: Elementy podstawowe działania w WF
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513378"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="1df29-102">Elementy podstawowe działania w WF</span><span class="sxs-lookup"><span data-stu-id="1df29-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="1df29-103"> udostępnia kilka dostarczane przez system działań, które zapewniają wygodną mechanizm wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="1df29-103"> provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="1df29-104">Działanie</span><span class="sxs-lookup"><span data-stu-id="1df29-104">Activity</span></span>|<span data-ttu-id="1df29-105">Opis</span><span class="sxs-lookup"><span data-stu-id="1df29-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="1df29-106">Przypisuje wartość do zmiennej w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="1df29-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="1df29-107">Umieszcza jedną ścieżkę wykonywania w stanie bezczynności, prawdopodobnie dzięki czemu można zwolnić przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="1df29-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="1df29-108">Wykonuje delegata, która jest pochodną <xref:System.Activities.ActivityDelegate> i jest udostępniany jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="1df29-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="1df29-109">Wykonuje publiczną metodę obiektu CLR.</span><span class="sxs-lookup"><span data-stu-id="1df29-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="1df29-110">Zapisuje określony ciąg w konsoli lub określonej <xref:System.IO.TextWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1df29-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
