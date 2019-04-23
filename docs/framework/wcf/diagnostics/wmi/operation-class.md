---
title: Operation — klasa
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973203"
---
# <a name="operation-class"></a><span data-ttu-id="d84ad-102">Operation — klasa</span><span class="sxs-lookup"><span data-stu-id="d84ad-102">Operation class</span></span>
<span data-ttu-id="d84ad-103">Operacja</span><span class="sxs-lookup"><span data-stu-id="d84ad-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d84ad-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="d84ad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d84ad-105">Methods</span></span>  
 <span data-ttu-id="d84ad-106">Klasa Operation nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="d84ad-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d84ad-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d84ad-107">Properties</span></span>  
 <span data-ttu-id="d84ad-108">Klasa Operation ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="d84ad-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="d84ad-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="d84ad-109">Action</span></span>  
 <span data-ttu-id="d84ad-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d84ad-110">Data type: string</span></span>  
  
 <span data-ttu-id="d84ad-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-112">Akcja WS-Addressing komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="d84ad-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="d84ad-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="d84ad-113">AsyncPattern</span></span>  
 <span data-ttu-id="d84ad-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d84ad-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d84ad-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-116">Wskazuje, że operacja jest wykonywane asynchronicznie za pomocą `Begin`[/ zamykającego nawiasy kątowe] i `End`pary — metoda [nawiasy otwarte i zamknięte] w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="d84ad-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="d84ad-117">Zachowania</span><span class="sxs-lookup"><span data-stu-id="d84ad-117">Behaviors</span></span>  
 <span data-ttu-id="d84ad-118">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="d84ad-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="d84ad-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-120">Zachowania skojarzone z tą operacją.</span><span class="sxs-lookup"><span data-stu-id="d84ad-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="d84ad-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="d84ad-121">IsCallback</span></span>  
 <span data-ttu-id="d84ad-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d84ad-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d84ad-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-124">Wartość true, gdy operacja jest operacji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="d84ad-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="d84ad-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="d84ad-125">IsInitiating</span></span>  
 <span data-ttu-id="d84ad-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d84ad-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d84ad-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-128">Wskazuje, czy metoda implementuje operację, która może zainicjować sesję na serwerze.</span><span class="sxs-lookup"><span data-stu-id="d84ad-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="d84ad-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="d84ad-129">IsOneWay</span></span>  
 <span data-ttu-id="d84ad-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d84ad-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="d84ad-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-132">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d84ad-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="d84ad-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="d84ad-133">IsTerminating</span></span>  
 <span data-ttu-id="d84ad-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="d84ad-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="d84ad-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-136">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="d84ad-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="d84ad-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="d84ad-137">MethodSignature</span></span>  
 <span data-ttu-id="d84ad-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d84ad-138">Data type: string</span></span>  
  
 <span data-ttu-id="d84ad-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-140">Podpis metody operacji.</span><span class="sxs-lookup"><span data-stu-id="d84ad-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d84ad-141">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d84ad-141">Name</span></span>  
 <span data-ttu-id="d84ad-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d84ad-142">Data type: string</span></span>  
  
 <span data-ttu-id="d84ad-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-144">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="d84ad-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="d84ad-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="d84ad-145">ParameterTypes</span></span>  
 <span data-ttu-id="d84ad-146">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="d84ad-146">Data type: string array</span></span>  
  
 <span data-ttu-id="d84ad-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-148">Typy parametrów operacji.</span><span class="sxs-lookup"><span data-stu-id="d84ad-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="d84ad-149">Parametr ReplyAction</span><span class="sxs-lookup"><span data-stu-id="d84ad-149">ReplyAction</span></span>  
 <span data-ttu-id="d84ad-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d84ad-150">Data type: string</span></span>  
  
 <span data-ttu-id="d84ad-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-152">Wartość Akcja SOAP komunikat odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="d84ad-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="d84ad-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="d84ad-153">ReturnType</span></span>  
 <span data-ttu-id="d84ad-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="d84ad-154">Data type: string</span></span>  
  
 <span data-ttu-id="d84ad-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="d84ad-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d84ad-156">Zwracany typ operacji.</span><span class="sxs-lookup"><span data-stu-id="d84ad-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84ad-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d84ad-157">Requirements</span></span>  
  
|<span data-ttu-id="d84ad-158">MOF</span><span class="sxs-lookup"><span data-stu-id="d84ad-158">MOF</span></span>|<span data-ttu-id="d84ad-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d84ad-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d84ad-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="d84ad-160">Namespace</span></span>|<span data-ttu-id="d84ad-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d84ad-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d84ad-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d84ad-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
