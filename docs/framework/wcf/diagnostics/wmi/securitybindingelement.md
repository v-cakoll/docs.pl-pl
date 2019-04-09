---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153858"
---
# <a name="securitybindingelement"></a><span data-ttu-id="39c85-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="39c85-102">SecurityBindingElement</span></span>
<span data-ttu-id="39c85-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="39c85-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39c85-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="39c85-104">Syntax</span></span>  
  
```csharp
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="39c85-105">Metody</span><span class="sxs-lookup"><span data-stu-id="39c85-105">Methods</span></span>  
 <span data-ttu-id="39c85-106">Klasa elementu SecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="39c85-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="39c85-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="39c85-107">Properties</span></span>  
 <span data-ttu-id="39c85-108">Klasa elementu SecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="39c85-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="39c85-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="39c85-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="39c85-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="39c85-110">Data type: string</span></span>  
  
 <span data-ttu-id="39c85-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-112">Określa algorytmów do użycia dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="39c85-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="39c85-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="39c85-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="39c85-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="39c85-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="39c85-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-116">Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="39c85-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="39c85-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="39c85-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="39c85-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="39c85-118">Data type: string</span></span>  
  
 <span data-ttu-id="39c85-119">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-120">Źródło entropia używana do tworzenia kluczy.</span><span class="sxs-lookup"><span data-stu-id="39c85-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="39c85-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="39c85-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="39c85-122">Typ danych: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="39c85-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="39c85-123">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-124">Właściwości zabezpieczeń powiązania dla lokalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="39c85-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="39c85-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="39c85-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="39c85-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="39c85-126">Data type: string</span></span>  
  
 <span data-ttu-id="39c85-127">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-128">Wersja używana do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="39c85-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="39c85-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="39c85-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="39c85-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="39c85-130">Data type: string</span></span>  
  
 <span data-ttu-id="39c85-131">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="39c85-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="39c85-132">Kolejność elementów w nagłówku zabezpieczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="39c85-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39c85-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="39c85-133">Requirements</span></span>  
  
|<span data-ttu-id="39c85-134">MOF</span><span class="sxs-lookup"><span data-stu-id="39c85-134">MOF</span></span>|<span data-ttu-id="39c85-135">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="39c85-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="39c85-136">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="39c85-136">Namespace</span></span>|<span data-ttu-id="39c85-137">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="39c85-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39c85-138">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="39c85-138">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
