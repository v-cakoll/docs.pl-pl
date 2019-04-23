---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979163"
---
# <a name="binding"></a><span data-ttu-id="5897e-102">Wiązanie</span><span class="sxs-lookup"><span data-stu-id="5897e-102">Binding</span></span>
<span data-ttu-id="5897e-103">WMI powiązania</span><span class="sxs-lookup"><span data-stu-id="5897e-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5897e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5897e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="5897e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5897e-105">Methods</span></span>  
 <span data-ttu-id="5897e-106">Klasa powiązania nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="5897e-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5897e-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5897e-107">Properties</span></span>  
 <span data-ttu-id="5897e-108">Klasa powiązania ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="5897e-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="5897e-109">Elementy BindingElements</span><span class="sxs-lookup"><span data-stu-id="5897e-109">BindingElements</span></span>  
 <span data-ttu-id="5897e-110">Typ danych: Tablica BindingElement</span><span class="sxs-lookup"><span data-stu-id="5897e-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="5897e-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-112">Kolekcja elementów powiązań implementowanych przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="5897e-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="5897e-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="5897e-113">CloseTimeout</span></span>  
 <span data-ttu-id="5897e-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5897e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="5897e-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-116">Przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="5897e-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="5897e-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="5897e-117">Name</span></span>  
 <span data-ttu-id="5897e-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5897e-118">Data type: string</span></span>  
  
 <span data-ttu-id="5897e-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-120">Nazwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="5897e-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="5897e-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5897e-121">Namespace</span></span>  
 <span data-ttu-id="5897e-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5897e-122">Data type: string</span></span>  
  
 <span data-ttu-id="5897e-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-124">Przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="5897e-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="5897e-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="5897e-125">OpenTimeout</span></span>  
 <span data-ttu-id="5897e-126">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5897e-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="5897e-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-128">Przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="5897e-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="5897e-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="5897e-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="5897e-130">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5897e-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="5897e-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-132">Przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="5897e-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="5897e-133">Schemat</span><span class="sxs-lookup"><span data-stu-id="5897e-133">Scheme</span></span>  
 <span data-ttu-id="5897e-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="5897e-134">Data type: string</span></span>  
  
 <span data-ttu-id="5897e-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-136">Schemat transportu identyfikatora URI jest używany przez fabryki kanału i odbiornika, które są tworzone przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="5897e-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="5897e-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="5897e-137">SendTimeout</span></span>  
 <span data-ttu-id="5897e-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="5897e-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="5897e-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="5897e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5897e-140">Przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="5897e-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5897e-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5897e-141">Requirements</span></span>  
  
|<span data-ttu-id="5897e-142">MOF</span><span class="sxs-lookup"><span data-stu-id="5897e-142">MOF</span></span>|<span data-ttu-id="5897e-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5897e-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5897e-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="5897e-144">Namespace</span></span>|<span data-ttu-id="5897e-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5897e-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5897e-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5897e-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
