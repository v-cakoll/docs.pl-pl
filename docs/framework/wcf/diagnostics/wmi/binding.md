---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: aaf0dd9d6918f2c248942cee3773eee8332adda9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552843"
---
# <a name="binding"></a><span data-ttu-id="9db08-102">Powiązanie</span><span class="sxs-lookup"><span data-stu-id="9db08-102">Binding</span></span>
<span data-ttu-id="9db08-103">WMI powiązania</span><span class="sxs-lookup"><span data-stu-id="9db08-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9db08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9db08-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9db08-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9db08-105">Methods</span></span>  
 <span data-ttu-id="9db08-106">Klasa powiązania nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="9db08-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="9db08-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9db08-107">Properties</span></span>  
 <span data-ttu-id="9db08-108">Klasa powiązania ma następujące właściwości.</span><span class="sxs-lookup"><span data-stu-id="9db08-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="9db08-109">Elementy BindingElements</span><span class="sxs-lookup"><span data-stu-id="9db08-109">BindingElements</span></span>  
 <span data-ttu-id="9db08-110">Typ danych: Tablica BindingElement</span><span class="sxs-lookup"><span data-stu-id="9db08-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="9db08-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-112">Kolekcja elementów powiązań implementowanych przez powiązanie.</span><span class="sxs-lookup"><span data-stu-id="9db08-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="9db08-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="9db08-113">CloseTimeout</span></span>  
 <span data-ttu-id="9db08-114">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="9db08-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="9db08-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-116">Przedział czasu przewidzianego na zakończenie operacji zamknięcia.</span><span class="sxs-lookup"><span data-stu-id="9db08-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9db08-117">Nazwa</span><span class="sxs-lookup"><span data-stu-id="9db08-117">Name</span></span>  
 <span data-ttu-id="9db08-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9db08-118">Data type: string</span></span>  
  
 <span data-ttu-id="9db08-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-120">Nazwa powiązania.</span><span class="sxs-lookup"><span data-stu-id="9db08-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="9db08-121">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9db08-121">Namespace</span></span>  
 <span data-ttu-id="9db08-122">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9db08-122">Data type: string</span></span>  
  
 <span data-ttu-id="9db08-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-124">Przestrzeń nazw XML powiązania.</span><span class="sxs-lookup"><span data-stu-id="9db08-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="9db08-125">OpenTimeout</span><span class="sxs-lookup"><span data-stu-id="9db08-125">OpenTimeout</span></span>  
 <span data-ttu-id="9db08-126">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="9db08-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="9db08-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-128">Przedział czasu przewidzianego na zakończenie operacji Otwórz.</span><span class="sxs-lookup"><span data-stu-id="9db08-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="9db08-129">ReceiveTimeout</span><span class="sxs-lookup"><span data-stu-id="9db08-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="9db08-130">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="9db08-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="9db08-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-132">Przedział czasu przewidzianego na ukończenie operacji odbierania.</span><span class="sxs-lookup"><span data-stu-id="9db08-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="9db08-133">Schemat</span><span class="sxs-lookup"><span data-stu-id="9db08-133">Scheme</span></span>  
 <span data-ttu-id="9db08-134">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="9db08-134">Data type: string</span></span>  
  
 <span data-ttu-id="9db08-135">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-136">Schemat transportu identyfikatora URI jest używany przez fabryki kanału i odbiornika, które są tworzone przez wiązanie.</span><span class="sxs-lookup"><span data-stu-id="9db08-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="9db08-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="9db08-137">SendTimeout</span></span>  
 <span data-ttu-id="9db08-138">Typ danych: Data i godzina</span><span class="sxs-lookup"><span data-stu-id="9db08-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="9db08-139">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9db08-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9db08-140">Przedział czasu przewidzianego na ukończenie operacji wysyłania.</span><span class="sxs-lookup"><span data-stu-id="9db08-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9db08-141">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9db08-141">Requirements</span></span>  
  
|<span data-ttu-id="9db08-142">MOF</span><span class="sxs-lookup"><span data-stu-id="9db08-142">MOF</span></span>|<span data-ttu-id="9db08-143">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9db08-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9db08-144">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="9db08-144">Namespace</span></span>|<span data-ttu-id="9db08-145">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9db08-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9db08-146">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9db08-146">See also</span></span>
- <xref:System.ServiceModel.Channels.Binding>
