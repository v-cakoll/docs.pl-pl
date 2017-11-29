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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="327d1-102">Operation — klasa</span><span class="sxs-lookup"><span data-stu-id="327d1-102">Operation class</span></span>
<span data-ttu-id="327d1-103">Operacja</span><span class="sxs-lookup"><span data-stu-id="327d1-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327d1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="327d1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="327d1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="327d1-105">Methods</span></span>  
 <span data-ttu-id="327d1-106">Klasa operacji nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="327d1-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="327d1-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="327d1-107">Properties</span></span>  
 <span data-ttu-id="327d1-108">Klasa operacja ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="327d1-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="327d1-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="327d1-109">Action</span></span>  
 <span data-ttu-id="327d1-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="327d1-110">Data type: string</span></span>  
  
 <span data-ttu-id="327d1-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-112">Akcja WS-Addressing komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="327d1-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="327d1-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="327d1-113">AsyncPattern</span></span>  
 <span data-ttu-id="327d1-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="327d1-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="327d1-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-116">Wskazuje, że operacja jest zaimplementowana asynchronicznie za pomocą `Begin`[otwierającego/zamykającego nawiasu ostrego] i `End`[otwierającego/zamykającego nawiasu ostrego] pary metod w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="327d1-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="327d1-117">Zachowania</span><span class="sxs-lookup"><span data-stu-id="327d1-117">Behaviors</span></span>  
 <span data-ttu-id="327d1-118">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="327d1-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="327d1-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-120">Zachowania skojarzone z tą operacją.</span><span class="sxs-lookup"><span data-stu-id="327d1-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="327d1-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="327d1-121">IsCallback</span></span>  
 <span data-ttu-id="327d1-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="327d1-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="327d1-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-124">Wartość PRAWDA, jeśli operacja jest wywołaniem zwrotnym.</span><span class="sxs-lookup"><span data-stu-id="327d1-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="327d1-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="327d1-125">IsInitiating</span></span>  
 <span data-ttu-id="327d1-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="327d1-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="327d1-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-128">Wskazuje, czy metoda implementuje operację umożliwiającą inicjację sesji na serwerze.</span><span class="sxs-lookup"><span data-stu-id="327d1-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="327d1-129">Ustawienie właściwości IsOneWay</span><span class="sxs-lookup"><span data-stu-id="327d1-129">IsOneWay</span></span>  
 <span data-ttu-id="327d1-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="327d1-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="327d1-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-132">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="327d1-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="327d1-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="327d1-133">IsTerminating</span></span>  
 <span data-ttu-id="327d1-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="327d1-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="327d1-135">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-136">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="327d1-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="327d1-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="327d1-137">MethodSignature</span></span>  
 <span data-ttu-id="327d1-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="327d1-138">Data type: string</span></span>  
  
 <span data-ttu-id="327d1-139">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-140">Podpis metody operacji.</span><span class="sxs-lookup"><span data-stu-id="327d1-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="327d1-141">Nazwa</span><span class="sxs-lookup"><span data-stu-id="327d1-141">Name</span></span>  
 <span data-ttu-id="327d1-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="327d1-142">Data type: string</span></span>  
  
 <span data-ttu-id="327d1-143">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-144">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="327d1-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="327d1-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="327d1-145">ParameterTypes</span></span>  
 <span data-ttu-id="327d1-146">Typ danych: tablicy ciągów</span><span class="sxs-lookup"><span data-stu-id="327d1-146">Data type: string array</span></span>  
  
 <span data-ttu-id="327d1-147">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-148">Typy parametrów operacji.</span><span class="sxs-lookup"><span data-stu-id="327d1-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="327d1-149">Parametr ReplyAction</span><span class="sxs-lookup"><span data-stu-id="327d1-149">ReplyAction</span></span>  
 <span data-ttu-id="327d1-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="327d1-150">Data type: string</span></span>  
  
 <span data-ttu-id="327d1-151">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-152">Wartość akcji SOAP dla komunikatu odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="327d1-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="327d1-153">Obiekt ReturnType</span><span class="sxs-lookup"><span data-stu-id="327d1-153">ReturnType</span></span>  
 <span data-ttu-id="327d1-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="327d1-154">Data type: string</span></span>  
  
 <span data-ttu-id="327d1-155">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="327d1-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="327d1-156">Zwracany typ operacji.</span><span class="sxs-lookup"><span data-stu-id="327d1-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="327d1-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="327d1-157">Requirements</span></span>  
  
|<span data-ttu-id="327d1-158">MOF</span><span class="sxs-lookup"><span data-stu-id="327d1-158">MOF</span></span>|<span data-ttu-id="327d1-159">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="327d1-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="327d1-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="327d1-160">Namespace</span></span>|<span data-ttu-id="327d1-161">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="327d1-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="327d1-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="327d1-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
