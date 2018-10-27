---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50033836"
---
# <a name="binding"></a><span data-ttu-id="abb21-102">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="abb21-102">Binding</span></span>
<span data-ttu-id="abb21-103">WMI powiązania</span><span class="sxs-lookup"><span data-stu-id="abb21-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abb21-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="abb21-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="abb21-105">Metody</span><span class="sxs-lookup"><span data-stu-id="abb21-105">Methods</span></span>  
 <span data-ttu-id="abb21-106">Klasa powiązania nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="abb21-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="abb21-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="abb21-107">Properties</span></span>  
 <span data-ttu-id="abb21-108">Klasa powiązania ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="abb21-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="abb21-109">Elementy BindingElements</span><span class="sxs-lookup"><span data-stu-id="abb21-109">BindingElements</span></span>  
 <span data-ttu-id="abb21-110">Typ danych: tablica BindingElement</span><span class="sxs-lookup"><span data-stu-id="abb21-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="abb21-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-112">Kolekcja elementów powiązań implementowanych przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="abb21-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="abb21-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="abb21-113">CloseTimeout</span></span>  
 <span data-ttu-id="abb21-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="abb21-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="abb21-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-116">Przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="abb21-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="abb21-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="abb21-117">Name</span></span>  
 <span data-ttu-id="abb21-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-118">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-120">Nazwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="abb21-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="abb21-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="abb21-121">Namespace</span></span>  
 <span data-ttu-id="abb21-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-122">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-124">Przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="abb21-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="abb21-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="abb21-125">OpenTimeout</span></span>  
 <span data-ttu-id="abb21-126">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="abb21-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="abb21-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-128">Przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="abb21-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="abb21-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="abb21-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="abb21-130">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="abb21-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="abb21-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-132">Przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="abb21-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="abb21-133">Schemat</span><span class="sxs-lookup"><span data-stu-id="abb21-133">Scheme</span></span>  
 <span data-ttu-id="abb21-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="abb21-134">Data type: string</span></span>  
  
 <span data-ttu-id="abb21-135">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-136">Schemat transportu identyfikatora URI jest używany przez fabryki kanału i odbiornika, które są tworzone przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="abb21-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="abb21-137">Właściwości SendTimeout</span><span class="sxs-lookup"><span data-stu-id="abb21-137">SendTimeout</span></span>  
 <span data-ttu-id="abb21-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="abb21-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="abb21-139">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="abb21-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abb21-140">Przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="abb21-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb21-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="abb21-141">Requirements</span></span>  
  
|<span data-ttu-id="abb21-142">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="abb21-142">MOF</span></span>|<span data-ttu-id="abb21-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="abb21-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="abb21-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="abb21-144">Namespace</span></span>|<span data-ttu-id="abb21-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="abb21-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abb21-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="abb21-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
