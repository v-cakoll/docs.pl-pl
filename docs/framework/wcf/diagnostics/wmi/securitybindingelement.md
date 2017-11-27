---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: b567c173c5a04421bce57585d96b8b45144c5625
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="securitybindingelement"></a><span data-ttu-id="07cf8-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="07cf8-102">SecurityBindingElement</span></span>
<span data-ttu-id="07cf8-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="07cf8-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07cf8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="07cf8-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="07cf8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="07cf8-105">Methods</span></span>  
 <span data-ttu-id="07cf8-106">Klasa obiektu SecurityBindingElement nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="07cf8-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="07cf8-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="07cf8-107">Properties</span></span>  
 <span data-ttu-id="07cf8-108">Klasa obiektu SecurityBindingElement ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="07cf8-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="07cf8-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="07cf8-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="07cf8-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07cf8-110">Data type: string</span></span>  
  
 <span data-ttu-id="07cf8-111">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-112">Określa algorytmy używane z powiązaniem.</span><span class="sxs-lookup"><span data-stu-id="07cf8-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="07cf8-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="07cf8-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="07cf8-114">Typ danych: wartość logiczna</span><span class="sxs-lookup"><span data-stu-id="07cf8-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="07cf8-115">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-116">Wartość logiczna określająca, czy każdy komunikat zawiera sygnaturę czasową.</span><span class="sxs-lookup"><span data-stu-id="07cf8-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="07cf8-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="07cf8-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="07cf8-118">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07cf8-118">Data type: string</span></span>  
  
 <span data-ttu-id="07cf8-119">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-120">Źródło entropii używane do tworzenia kluczy.</span><span class="sxs-lookup"><span data-stu-id="07cf8-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="07cf8-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="07cf8-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="07cf8-122">Typ danych: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="07cf8-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="07cf8-123">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-124">Powiązania właściwości zabezpieczeń lokalnej usługi.</span><span class="sxs-lookup"><span data-stu-id="07cf8-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="07cf8-125">Właściwości MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="07cf8-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="07cf8-126">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07cf8-126">Data type: string</span></span>  
  
 <span data-ttu-id="07cf8-127">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-128">Wersja używana do zabezpieczenia komunikatów.</span><span class="sxs-lookup"><span data-stu-id="07cf8-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="07cf8-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="07cf8-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="07cf8-130">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="07cf8-130">Data type: string</span></span>  
  
 <span data-ttu-id="07cf8-131">Dostęp typu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="07cf8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="07cf8-132">Kolejność elementów nagłówka zabezpieczeń dla tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="07cf8-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07cf8-133">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07cf8-133">Requirements</span></span>  
  
|<span data-ttu-id="07cf8-134">MOF</span><span class="sxs-lookup"><span data-stu-id="07cf8-134">MOF</span></span>|<span data-ttu-id="07cf8-135">Zadeklarowany w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="07cf8-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="07cf8-136">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="07cf8-136">Namespace</span></span>|<span data-ttu-id="07cf8-137">Zdefiniowany w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="07cf8-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="07cf8-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="07cf8-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>
