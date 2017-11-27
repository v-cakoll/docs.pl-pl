---
title: "&#39; &lt;eventname&gt;&#39; jest zdarzeniem i nie można bezpośrednio wywołać"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32022
- vbc32022
helpviewer_keywords: BC32022
ms.assetid: 4dcfcb8d-a9fa-46a7-a034-29d9ff3a59b3
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bb987c957a28aa37c40ad975b945c20da4690f6e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="39lteventnamegt39-is-an-event-and-cannot-be-called-directly"></a><span data-ttu-id="87802-102">&#39; &lt;eventname&gt;&#39; jest zdarzeniem i nie można bezpośrednio wywołać</span><span class="sxs-lookup"><span data-stu-id="87802-102">&#39;&lt;eventname&gt;&#39; is an event, and cannot be called directly</span></span>
<span data-ttu-id="87802-103">"<`eventname`>" jest zdarzeniem i dlatego nie można wywołać bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="87802-103">'<`eventname`>' is an event, and so cannot be called directly.</span></span> <span data-ttu-id="87802-104">Użyj `RaiseEvent` instrukcji, aby wywołać zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="87802-104">Use a `RaiseEvent` statement to raise an event.</span></span>  
  
 <span data-ttu-id="87802-105">Wywołanie procedury określa zdarzenie dla Nazwa procedury.</span><span class="sxs-lookup"><span data-stu-id="87802-105">A procedure call specifies an event for the procedure name.</span></span> <span data-ttu-id="87802-106">Program obsługi zdarzeń jest procedurą, ale sam zdarzenia jest sygnalizowania urządzenia, które muszą być wywoływane i obsługi.</span><span class="sxs-lookup"><span data-stu-id="87802-106">An event handler is a procedure, but the event itself is a signaling device, which must be raised and handled.</span></span>  
  
 <span data-ttu-id="87802-107">**Identyfikator błędu:** BC32022</span><span class="sxs-lookup"><span data-stu-id="87802-107">**Error ID:** BC32022</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="87802-108">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="87802-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="87802-109">Użyj `RaiseEvent` instrukcji sygnału zdarzenia i wywoływać procedury lub procedury, które ją obsługują.</span><span class="sxs-lookup"><span data-stu-id="87802-109">Use a `RaiseEvent` statement to signal an event and invoke the procedure or procedures that handle it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87802-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="87802-110">See Also</span></span>  
 [<span data-ttu-id="87802-111">RaiseEvent — instrukcja</span><span class="sxs-lookup"><span data-stu-id="87802-111">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
