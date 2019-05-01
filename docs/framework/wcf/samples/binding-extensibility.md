---
title: Rozszerzalność wiązań
ms.date: 03/30/2017
ms.assetid: cabdd583-ddf5-493e-9dba-c6c31cde8f65
ms.openlocfilehash: af9736a1011c3de6e1add51e8a913745cfd6756d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61944095"
---
# <a name="binding-extensibility"></a><span data-ttu-id="38102-102">Rozszerzalność wiązań</span><span class="sxs-lookup"><span data-stu-id="38102-102">Binding Extensibility</span></span>

<span data-ttu-id="38102-103">Ta sekcja zawiera przykłady pokazujące, niestandardowego powiązania w Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="38102-103">This section contains samples that demonstrate custom binding in Windows Communication Foundation (WCF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38102-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="38102-104">In This Section</span></span>  
 <xref:System.ServiceModel.NetHttpBinding>  
 <span data-ttu-id="38102-105">Demonstruje sposób implementacji powiązanie, które stosów <xref:System.ServiceModel.Channels.HttpTransportBindingElement> lub <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> w górnej części <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="38102-105">Demonstrates how to implement a binding that stacks <xref:System.ServiceModel.Channels.HttpTransportBindingElement> or the <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> on top of the <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>.</span></span>  
  
 [<span data-ttu-id="38102-106">WSStreamedHttpBinding</span><span class="sxs-lookup"><span data-stu-id="38102-106">WSStreamedHttpBinding</span></span>](wsstreamedhttpbinding.md)  
 <span data-ttu-id="38102-107">Pokazuje, jak można utworzyć powiązania, który jest przeznaczony do obsługi transmisji strumieniowej scenariuszy stosowania transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="38102-107">Demonstrates how to create a binding that is designed to support streaming scenarios when the HTTP transport is used.</span></span>  
