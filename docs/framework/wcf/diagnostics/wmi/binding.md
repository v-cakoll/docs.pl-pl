---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9e44d161e1229db9145f4ed7e337396bbd98c68
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="binding"></a><span data-ttu-id="93d45-102">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="93d45-102">Binding</span></span>
<span data-ttu-id="93d45-103">WMI powiązania</span><span class="sxs-lookup"><span data-stu-id="93d45-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d45-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93d45-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="93d45-105">Metody</span><span class="sxs-lookup"><span data-stu-id="93d45-105">Methods</span></span>  
 <span data-ttu-id="93d45-106">Klasa powiązania nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="93d45-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="93d45-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="93d45-107">Properties</span></span>  
 <span data-ttu-id="93d45-108">Klasa powiązania ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="93d45-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="93d45-109">Elementy BindingElements</span><span class="sxs-lookup"><span data-stu-id="93d45-109">BindingElements</span></span>  
 <span data-ttu-id="93d45-110">Typ danych: tablica BindingElement</span><span class="sxs-lookup"><span data-stu-id="93d45-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="93d45-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-112">Kolekcja elementów powiązań implementowanych przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="93d45-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="93d45-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="93d45-113">CloseTimeout</span></span>  
 <span data-ttu-id="93d45-114">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="93d45-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="93d45-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-116">Interwał przeznaczony na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="93d45-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="93d45-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="93d45-117">Name</span></span>  
 <span data-ttu-id="93d45-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="93d45-118">Data type: string</span></span>  
  
 <span data-ttu-id="93d45-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-120">Nazwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="93d45-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="93d45-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="93d45-121">Namespace</span></span>  
 <span data-ttu-id="93d45-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="93d45-122">Data type: string</span></span>  
  
 <span data-ttu-id="93d45-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-124">Przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="93d45-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="93d45-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="93d45-125">OpenTimeout</span></span>  
 <span data-ttu-id="93d45-126">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="93d45-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="93d45-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-128">Interwał przeznaczony na zakończenie operacji otwarcia.</span><span class="sxs-lookup"><span data-stu-id="93d45-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="93d45-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="93d45-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="93d45-130">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="93d45-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="93d45-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-132">Interwał przeznaczony na zakończenie operacji odbioru.</span><span class="sxs-lookup"><span data-stu-id="93d45-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="93d45-133">Schemat</span><span class="sxs-lookup"><span data-stu-id="93d45-133">Scheme</span></span>  
 <span data-ttu-id="93d45-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="93d45-134">Data type: string</span></span>  
  
 <span data-ttu-id="93d45-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-136">Schemat transportu identyfikatora URI, który jest używany przez fabryki kanału i odbiornika zbudowane na podstawie powiązania.</span><span class="sxs-lookup"><span data-stu-id="93d45-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="93d45-137">właściwości sendTimeout</span><span class="sxs-lookup"><span data-stu-id="93d45-137">SendTimeout</span></span>  
 <span data-ttu-id="93d45-138">Typ danych: daty i godziny</span><span class="sxs-lookup"><span data-stu-id="93d45-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="93d45-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="93d45-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="93d45-140">Interwał przeznaczony na zakończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="93d45-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d45-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93d45-141">Requirements</span></span>  
  
|<span data-ttu-id="93d45-142">MOF</span><span class="sxs-lookup"><span data-stu-id="93d45-142">MOF</span></span>|<span data-ttu-id="93d45-143">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="93d45-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="93d45-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="93d45-144">Namespace</span></span>|<span data-ttu-id="93d45-145">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="93d45-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="93d45-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93d45-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
