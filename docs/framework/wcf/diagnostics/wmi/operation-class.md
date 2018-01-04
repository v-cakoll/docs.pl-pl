---
title: "Operation — klasa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a><span data-ttu-id="65be2-102">Operation — klasa</span><span class="sxs-lookup"><span data-stu-id="65be2-102">Operation class</span></span>
<span data-ttu-id="65be2-103">Operacja</span><span class="sxs-lookup"><span data-stu-id="65be2-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65be2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65be2-104">Syntax</span></span>  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="65be2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="65be2-105">Methods</span></span>  
 <span data-ttu-id="65be2-106">Klasa operacji nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="65be2-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="65be2-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="65be2-107">Properties</span></span>  
 <span data-ttu-id="65be2-108">Klasa operacja ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="65be2-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="65be2-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="65be2-109">Action</span></span>  
 <span data-ttu-id="65be2-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="65be2-110">Data type: string</span></span>  
  
 <span data-ttu-id="65be2-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-112">Akcja WS-Addressing komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="65be2-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="65be2-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="65be2-113">AsyncPattern</span></span>  
 <span data-ttu-id="65be2-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65be2-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="65be2-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-116">Wskazuje, że operacja jest zaimplementowana asynchronicznie za pomocą `Begin`[otwierającego/zamykającego nawiasu ostrego] i `End`[otwierającego/zamykającego nawiasu ostrego] pary metod w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="65be2-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="65be2-117">Zachowania</span><span class="sxs-lookup"><span data-stu-id="65be2-117">Behaviors</span></span>  
 <span data-ttu-id="65be2-118">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="65be2-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="65be2-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-120">Zachowania skojarzone z tą operacją.</span><span class="sxs-lookup"><span data-stu-id="65be2-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="65be2-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="65be2-121">IsCallback</span></span>  
 <span data-ttu-id="65be2-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65be2-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="65be2-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-124">Wartość PRAWDA, jeśli operacja jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="65be2-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="65be2-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="65be2-125">IsInitiating</span></span>  
 <span data-ttu-id="65be2-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65be2-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="65be2-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-128">Wskazuje, czy metoda implementuje operację umożliwiającą inicjację sesji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="65be2-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="65be2-129">Ustawienie właściwości IsOneWay</span><span class="sxs-lookup"><span data-stu-id="65be2-129">IsOneWay</span></span>  
 <span data-ttu-id="65be2-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65be2-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="65be2-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-132">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="65be2-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="65be2-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="65be2-133">IsTerminating</span></span>  
 <span data-ttu-id="65be2-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="65be2-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="65be2-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-136">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="65be2-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="65be2-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="65be2-137">MethodSignature</span></span>  
 <span data-ttu-id="65be2-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="65be2-138">Data type: string</span></span>  
  
 <span data-ttu-id="65be2-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-140">Podpis metody operacji.</span><span class="sxs-lookup"><span data-stu-id="65be2-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="65be2-141">Nazwa</span><span class="sxs-lookup"><span data-stu-id="65be2-141">Name</span></span>  
 <span data-ttu-id="65be2-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="65be2-142">Data type: string</span></span>  
  
 <span data-ttu-id="65be2-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-144">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="65be2-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="65be2-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="65be2-145">ParameterTypes</span></span>  
 <span data-ttu-id="65be2-146">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="65be2-146">Data type: string array</span></span>  
  
 <span data-ttu-id="65be2-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-148">Typy parametrów operacji.</span><span class="sxs-lookup"><span data-stu-id="65be2-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="65be2-149">Parametr ReplyAction</span><span class="sxs-lookup"><span data-stu-id="65be2-149">ReplyAction</span></span>  
 <span data-ttu-id="65be2-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="65be2-150">Data type: string</span></span>  
  
 <span data-ttu-id="65be2-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-152">Wartość akcji SOAP dla komunikatu odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="65be2-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="65be2-153">Obiekt ReturnType</span><span class="sxs-lookup"><span data-stu-id="65be2-153">ReturnType</span></span>  
 <span data-ttu-id="65be2-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="65be2-154">Data type: string</span></span>  
  
 <span data-ttu-id="65be2-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="65be2-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65be2-156">Zwracany typ operacji.</span><span class="sxs-lookup"><span data-stu-id="65be2-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65be2-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65be2-157">Requirements</span></span>  
  
|<span data-ttu-id="65be2-158">MOF</span><span class="sxs-lookup"><span data-stu-id="65be2-158">MOF</span></span>|<span data-ttu-id="65be2-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="65be2-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="65be2-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="65be2-160">Namespace</span></span>|<span data-ttu-id="65be2-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="65be2-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="65be2-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65be2-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
