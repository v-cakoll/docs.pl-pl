---
title: "Rozszerzalność powiązań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 251d89af938b4bf104ddb86689b2573856386d75
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2017
---
# <a name="binding-extensibility"></a><span data-ttu-id="f4faa-102">Rozszerzalność powiązań</span><span class="sxs-lookup"><span data-stu-id="f4faa-102">Binding Extensibility</span></span>

<span data-ttu-id="f4faa-103">Ta sekcja zawiera przykłady ilustrujące niestandardowego powiązania w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4faa-103">This section contains samples that demonstrate custom binding in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4faa-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="f4faa-104">In This Section</span></span>  
 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="f4faa-105">Pokazuje, jak implementuje powiązania, które stosów <xref:System.ServiceModel.Channels.HttpTransportBindingElement> lub <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> nad <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f4faa-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 [<span data-ttu-id="f4faa-106">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f4faa-106">WSStreamedHttpBinding</span></span>](wsstreamedhttpbinding.md)  
 <span data-ttu-id="f4faa-107">Przedstawia sposób tworzenia powiązania, które umożliwia obsługę przesyłania strumieniowego scenariuszy stosowania transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f4faa-107">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
