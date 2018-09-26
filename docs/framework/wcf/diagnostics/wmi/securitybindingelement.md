---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069977"
---
# <a name="securitybindingelement"></a><span data-ttu-id="4d000-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4d000-102">SecurityBindingElement</span></span>
<span data-ttu-id="4d000-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="4d000-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d000-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d000-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4d000-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d000-105">Methods</span></span>  
 <span data-ttu-id="4d000-106">Klasa elementu SecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="4d000-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d000-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4d000-107">Properties</span></span>  
 <span data-ttu-id="4d000-108">Klasa elementu SecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="4d000-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="4d000-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="4d000-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="4d000-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d000-110">Data type: string</span></span>  
  
 <span data-ttu-id="4d000-111">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-112">Określa algorytmów do użycia dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="4d000-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="4d000-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="4d000-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="4d000-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="4d000-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4d000-115">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-116">Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="4d000-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="4d000-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="4d000-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="4d000-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d000-118">Data type: string</span></span>  
  
 <span data-ttu-id="4d000-119">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-120">Źródło entropia używana do tworzenia kluczy.</span><span class="sxs-lookup"><span data-stu-id="4d000-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="4d000-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4d000-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="4d000-122">Typ danych: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4d000-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="4d000-123">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-124">Właściwości zabezpieczeń powiązania dla lokalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="4d000-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="4d000-125">właściwości messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="4d000-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="4d000-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d000-126">Data type: string</span></span>  
  
 <span data-ttu-id="4d000-127">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-128">Wersja używana do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="4d000-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="4d000-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="4d000-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="4d000-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="4d000-130">Data type: string</span></span>  
  
 <span data-ttu-id="4d000-131">Dostęp do typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4d000-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d000-132">Kolejność elementów w nagłówku zabezpieczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="4d000-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d000-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d000-133">Requirements</span></span>  
  
|<span data-ttu-id="4d000-134">PLIK MOF</span><span class="sxs-lookup"><span data-stu-id="4d000-134">MOF</span></span>|<span data-ttu-id="4d000-135">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4d000-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d000-136">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="4d000-136">Namespace</span></span>|<span data-ttu-id="4d000-137">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d000-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d000-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d000-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
