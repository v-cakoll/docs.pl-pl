---
title: Elementy podstawowe działania w WF
ms.date: 03/30/2017
ms.assetid: 8e9009d1-236e-4d8e-86fc-e43132bf6dfc
ms.openlocfilehash: d87125d8d85fa33a49651dfabb840881b0e216ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780708"
---
# <a name="primitives-activities-in-wf"></a><span data-ttu-id="8cb89-102">Elementy podstawowe działania w WF</span><span class="sxs-lookup"><span data-stu-id="8cb89-102">Primitives Activities in WF</span></span>
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="8cb89-103">zawiera kilka działań dostarczane przez system, które zapewniają wygodny mechanizm do wykonywania typowych zadań.</span><span class="sxs-lookup"><span data-stu-id="8cb89-103">provides several system-provided activities that provide a convenient mechanism for performing common tasks.</span></span>  
  
|<span data-ttu-id="8cb89-104">Działanie</span><span class="sxs-lookup"><span data-stu-id="8cb89-104">Activity</span></span>|<span data-ttu-id="8cb89-105">Opis</span><span class="sxs-lookup"><span data-stu-id="8cb89-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Assign>|<span data-ttu-id="8cb89-106">Przypisuje wartość do zmiennej w bieżącym zakresie.</span><span class="sxs-lookup"><span data-stu-id="8cb89-106">Assigns a value to a variable at the current scope.</span></span>|  
|<xref:System.Activities.Statements.Delay>|<span data-ttu-id="8cb89-107">Umieszcza jednej ścieżki wykonywania w stanie bezczynności, potencjalnie umożliwiając przepływ pracy, aby zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="8cb89-107">Puts one path of execution into an idle state, possibly allowing the workflow to be unloaded.</span></span>|  
|<xref:System.Activities.Statements.InvokeDelegate>|<span data-ttu-id="8cb89-108">Wykonuje delegata, która pochodzi od klasy <xref:System.Activities.ActivityDelegate> i jest udostępniany jako właściwość.</span><span class="sxs-lookup"><span data-stu-id="8cb89-108">Executes a delegate that derives from <xref:System.Activities.ActivityDelegate> and is exposed as a property.</span></span>|  
|<xref:System.Activities.Statements.InvokeMethod>|<span data-ttu-id="8cb89-109">Wykonuje publiczną metodę obiektu CLR.</span><span class="sxs-lookup"><span data-stu-id="8cb89-109">Executes a public method of a CLR object.</span></span>|  
|<xref:System.Activities.Statements.WriteLine>|<span data-ttu-id="8cb89-110">Zapisuje określony ciąg na konsoli lub określonym <xref:System.IO.TextWriter> obiektu.</span><span class="sxs-lookup"><span data-stu-id="8cb89-110">Writes a specified string to the console or a specified <xref:System.IO.TextWriter> object.</span></span>|
