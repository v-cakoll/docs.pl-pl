---
title: Operation — klasa
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165083"
---
# <a name="operation-class"></a><span data-ttu-id="f6541-102">Operation — klasa</span><span class="sxs-lookup"><span data-stu-id="f6541-102">Operation class</span></span>
<span data-ttu-id="f6541-103">Operacja</span><span class="sxs-lookup"><span data-stu-id="f6541-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6541-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6541-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f6541-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f6541-105">Methods</span></span>  
 <span data-ttu-id="f6541-106">Klasa Operation nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="f6541-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f6541-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f6541-107">Properties</span></span>  
 <span data-ttu-id="f6541-108">Klasa Operation ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="f6541-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="f6541-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="f6541-109">Action</span></span>  
 <span data-ttu-id="f6541-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f6541-110">Data type: string</span></span>  
  
 <span data-ttu-id="f6541-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-112">Akcja WS-Addressing komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="f6541-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="f6541-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="f6541-113">AsyncPattern</span></span>  
 <span data-ttu-id="f6541-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f6541-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="f6541-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-116">Wskazuje, że operacja jest wykonywane asynchronicznie za pomocą `Begin`[/ zamykającego nawiasy kątowe] i `End`pary — metoda [nawiasy otwarte i zamknięte] w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="f6541-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="f6541-117">Zachowania</span><span class="sxs-lookup"><span data-stu-id="f6541-117">Behaviors</span></span>  
 <span data-ttu-id="f6541-118">Typ danych: Zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="f6541-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="f6541-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-120">Zachowania skojarzone z tą operacją.</span><span class="sxs-lookup"><span data-stu-id="f6541-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="f6541-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="f6541-121">IsCallback</span></span>  
 <span data-ttu-id="f6541-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f6541-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f6541-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-124">Wartość true, gdy operacja jest operacji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f6541-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="f6541-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="f6541-125">IsInitiating</span></span>  
 <span data-ttu-id="f6541-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f6541-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="f6541-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-128">Wskazuje, czy metoda implementuje operację, która może zainicjować sesję na serwerze.</span><span class="sxs-lookup"><span data-stu-id="f6541-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="f6541-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="f6541-129">IsOneWay</span></span>  
 <span data-ttu-id="f6541-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f6541-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="f6541-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-132">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f6541-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="f6541-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="f6541-133">IsTerminating</span></span>  
 <span data-ttu-id="f6541-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="f6541-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="f6541-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-136">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="f6541-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="f6541-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="f6541-137">MethodSignature</span></span>  
 <span data-ttu-id="f6541-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f6541-138">Data type: string</span></span>  
  
 <span data-ttu-id="f6541-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-140">Podpis metody operacji.</span><span class="sxs-lookup"><span data-stu-id="f6541-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f6541-141">Nazwa</span><span class="sxs-lookup"><span data-stu-id="f6541-141">Name</span></span>  
 <span data-ttu-id="f6541-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f6541-142">Data type: string</span></span>  
  
 <span data-ttu-id="f6541-143">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-144">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="f6541-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="f6541-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="f6541-145">ParameterTypes</span></span>  
 <span data-ttu-id="f6541-146">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="f6541-146">Data type: string array</span></span>  
  
 <span data-ttu-id="f6541-147">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-148">Typy parametrów operacji.</span><span class="sxs-lookup"><span data-stu-id="f6541-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="f6541-149">Parametr ReplyAction</span><span class="sxs-lookup"><span data-stu-id="f6541-149">ReplyAction</span></span>  
 <span data-ttu-id="f6541-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f6541-150">Data type: string</span></span>  
  
 <span data-ttu-id="f6541-151">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-152">Wartość Akcja SOAP komunikat odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="f6541-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="f6541-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="f6541-153">ReturnType</span></span>  
 <span data-ttu-id="f6541-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="f6541-154">Data type: string</span></span>  
  
 <span data-ttu-id="f6541-155">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="f6541-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f6541-156">Zwracany typ operacji.</span><span class="sxs-lookup"><span data-stu-id="f6541-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6541-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6541-157">Requirements</span></span>  
  
|<span data-ttu-id="f6541-158">MOF</span><span class="sxs-lookup"><span data-stu-id="f6541-158">MOF</span></span>|<span data-ttu-id="f6541-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f6541-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f6541-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="f6541-160">Namespace</span></span>|<span data-ttu-id="f6541-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f6541-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6541-162">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6541-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
