---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396851"
---
# <a name="securitybindingelement"></a><span data-ttu-id="07e1f-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="07e1f-102">SecurityBindingElement</span></span>
<span data-ttu-id="07e1f-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="07e1f-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e1f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07e1f-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="07e1f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="07e1f-105">Methods</span></span>  
 <span data-ttu-id="07e1f-106">Klasa elementu SecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="07e1f-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07e1f-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="07e1f-107">Properties</span></span>  
 <span data-ttu-id="07e1f-108">Klasa elementu SecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="07e1f-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="07e1f-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="07e1f-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="07e1f-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07e1f-110">Data type: string</span></span>  
  
 <span data-ttu-id="07e1f-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-112">Określa algorytmów do użycia dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="07e1f-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="07e1f-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="07e1f-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="07e1f-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="07e1f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="07e1f-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-116">Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="07e1f-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="07e1f-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="07e1f-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="07e1f-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07e1f-118">Data type: string</span></span>  
  
 <span data-ttu-id="07e1f-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-120">Źródło entropia używana do tworzenia kluczy.</span><span class="sxs-lookup"><span data-stu-id="07e1f-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="07e1f-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="07e1f-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="07e1f-122">Typ danych: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="07e1f-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="07e1f-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-124">Właściwości zabezpieczeń powiązania dla lokalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="07e1f-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="07e1f-125">właściwości messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="07e1f-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="07e1f-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07e1f-126">Data type: string</span></span>  
  
 <span data-ttu-id="07e1f-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-128">Wersja używana do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="07e1f-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="07e1f-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="07e1f-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="07e1f-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07e1f-130">Data type: string</span></span>  
  
 <span data-ttu-id="07e1f-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07e1f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07e1f-132">Kolejność elementów w nagłówku zabezpieczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="07e1f-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e1f-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07e1f-133">Requirements</span></span>  
  
|<span data-ttu-id="07e1f-134">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="07e1f-134">MOF</span></span>|<span data-ttu-id="07e1f-135">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07e1f-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07e1f-136">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="07e1f-136">Namespace</span></span>|<span data-ttu-id="07e1f-137">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07e1f-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07e1f-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07e1f-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
