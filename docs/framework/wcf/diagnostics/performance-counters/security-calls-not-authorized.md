---
title: "Wywołania zabezpieczeń bez autoryzacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d66e700aa3aee0e577955a978cff0f5cedd84851
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="6c47e-102">Wywołania zabezpieczeń bez autoryzacji</span><span class="sxs-lookup"><span data-stu-id="6c47e-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="6c47e-103">Nazwa licznika: Wywołania zabezpieczeń bez autoryzacji.</span><span class="sxs-lookup"><span data-stu-id="6c47e-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="6c47e-104">Opis</span><span class="sxs-lookup"><span data-stu-id="6c47e-104">Description</span></span>  
 <span data-ttu-id="6c47e-105">Ten licznik jest zwiększany po <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metoda zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="6c47e-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="6c47e-106">Wskazuje on, że przychodzący komunikat pochodzi z prawidłowego użytkownika i odpowiednio chroniona, ale użytkownik nie ma uprawnień do wykonywania określonych zadań.</span><span class="sxs-lookup"><span data-stu-id="6c47e-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
