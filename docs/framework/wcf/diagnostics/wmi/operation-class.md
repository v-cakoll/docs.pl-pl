---
title: Operation — klasa
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 16de8b25594896349ea546d3def52dd256fe5c70
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180942"
---
# <a name="operation-class"></a><span data-ttu-id="3ec4f-102">Operation — klasa</span><span class="sxs-lookup"><span data-stu-id="3ec4f-102">Operation class</span></span>
<span data-ttu-id="3ec4f-103">Operacja</span><span class="sxs-lookup"><span data-stu-id="3ec4f-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ec4f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ec4f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3ec4f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3ec4f-105">Methods</span></span>  
 <span data-ttu-id="3ec4f-106">Klasa Operation nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3ec4f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="3ec4f-107">Properties</span></span>  
 <span data-ttu-id="3ec4f-108">Klasa Operation ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="3ec4f-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="3ec4f-109">Akcja</span><span class="sxs-lookup"><span data-stu-id="3ec4f-109">Action</span></span>  
 <span data-ttu-id="3ec4f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3ec4f-110">Data type: string</span></span>  
  
 <span data-ttu-id="3ec4f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-112">Akcja WS-Addressing komunikatu żądania.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="3ec4f-113">Wzorca asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="3ec4f-113">AsyncPattern</span></span>  
 <span data-ttu-id="3ec4f-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3ec4f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ec4f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-116">Wskazuje, że operacja jest wykonywane asynchronicznie za pomocą `Begin`[/ zamykającego nawiasy kątowe] i `End`pary — metoda [nawiasy otwarte i zamknięte] w kontrakcie usługi.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="3ec4f-117">Zachowania</span><span class="sxs-lookup"><span data-stu-id="3ec4f-117">Behaviors</span></span>  
 <span data-ttu-id="3ec4f-118">Typ danych: zachowanie tablicy</span><span class="sxs-lookup"><span data-stu-id="3ec4f-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="3ec4f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-120">Zachowania skojarzone z tą operacją.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="3ec4f-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="3ec4f-121">IsCallback</span></span>  
 <span data-ttu-id="3ec4f-122">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3ec4f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ec4f-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-124">Wartość true, gdy operacja jest operacji wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="3ec4f-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="3ec4f-125">IsInitiating</span></span>  
 <span data-ttu-id="3ec4f-126">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3ec4f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ec4f-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-128">Wskazuje, czy metoda implementuje operację, która może zainicjować sesję na serwerze.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="3ec4f-129">Ustawienie właściwości IsOneWay</span><span class="sxs-lookup"><span data-stu-id="3ec4f-129">IsOneWay</span></span>  
 <span data-ttu-id="3ec4f-130">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3ec4f-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ec4f-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-132">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="3ec4f-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="3ec4f-133">IsTerminating</span></span>  
 <span data-ttu-id="3ec4f-134">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="3ec4f-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="3ec4f-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-136">Wskazuje, czy operacja zwraca komunikat odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="3ec4f-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="3ec4f-137">MethodSignature</span></span>  
 <span data-ttu-id="3ec4f-138">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3ec4f-138">Data type: string</span></span>  
  
 <span data-ttu-id="3ec4f-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-140">Podpis metody operacji.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="3ec4f-141">Nazwa</span><span class="sxs-lookup"><span data-stu-id="3ec4f-141">Name</span></span>  
 <span data-ttu-id="3ec4f-142">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3ec4f-142">Data type: string</span></span>  
  
 <span data-ttu-id="3ec4f-143">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-144">Nazwa operacji.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="3ec4f-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="3ec4f-145">ParameterTypes</span></span>  
 <span data-ttu-id="3ec4f-146">Typ danych: tablica ciągów</span><span class="sxs-lookup"><span data-stu-id="3ec4f-146">Data type: string array</span></span>  
  
 <span data-ttu-id="3ec4f-147">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-148">Typy parametrów operacji.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="3ec4f-149">Parametr ReplyAction</span><span class="sxs-lookup"><span data-stu-id="3ec4f-149">ReplyAction</span></span>  
 <span data-ttu-id="3ec4f-150">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3ec4f-150">Data type: string</span></span>  
  
 <span data-ttu-id="3ec4f-151">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-152">Wartość Akcja SOAP komunikat odpowiedzi operacji.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="3ec4f-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="3ec4f-153">ReturnType</span></span>  
 <span data-ttu-id="3ec4f-154">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="3ec4f-154">Data type: string</span></span>  
  
 <span data-ttu-id="3ec4f-155">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="3ec4f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3ec4f-156">Zwracany typ operacji.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ec4f-157">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ec4f-157">Requirements</span></span>  
  
|<span data-ttu-id="3ec4f-158">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="3ec4f-158">MOF</span></span>|<span data-ttu-id="3ec4f-159">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3ec4f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3ec4f-160">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="3ec4f-160">Namespace</span></span>|<span data-ttu-id="3ec4f-161">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3ec4f-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3ec4f-162">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3ec4f-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
