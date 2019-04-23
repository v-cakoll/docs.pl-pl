---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59976901"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="55567-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="55567-102">PeerSecuritySettings</span></span>
<span data-ttu-id="55567-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="55567-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55567-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55567-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="55567-105">Metody</span><span class="sxs-lookup"><span data-stu-id="55567-105">Methods</span></span>  
 <span data-ttu-id="55567-106">Klasa PeerSecuritySettings nie definiuje żadnych metod.</span><span class="sxs-lookup"><span data-stu-id="55567-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="55567-107">Właściwości</span><span class="sxs-lookup"><span data-stu-id="55567-107">Properties</span></span>  
 <span data-ttu-id="55567-108">Klasa PeerSecuritySettings ma następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="55567-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="55567-109">Tryb</span><span class="sxs-lookup"><span data-stu-id="55567-109">Mode</span></span>  
 <span data-ttu-id="55567-110">Typ danych: ciąg</span><span class="sxs-lookup"><span data-stu-id="55567-110">Data type: string</span></span>  
  
 <span data-ttu-id="55567-111">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="55567-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55567-112">Czy komunikatu i zabezpieczenia na poziomie transportu używanych przez punkty końcowe skonfigurowane dla tego wiązania.</span><span class="sxs-lookup"><span data-stu-id="55567-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="55567-113">Transport</span><span class="sxs-lookup"><span data-stu-id="55567-113">Transport</span></span>  
 <span data-ttu-id="55567-114">Typ danych: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="55567-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="55567-115">Typ dostępu: tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="55567-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="55567-116">Ustawienia zabezpieczeń transportu.</span><span class="sxs-lookup"><span data-stu-id="55567-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55567-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55567-117">Requirements</span></span>  
  
|<span data-ttu-id="55567-118">MOF</span><span class="sxs-lookup"><span data-stu-id="55567-118">MOF</span></span>|<span data-ttu-id="55567-119">Zadeklarowana w Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="55567-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="55567-120">Przestrzeń nazw</span><span class="sxs-lookup"><span data-stu-id="55567-120">Namespace</span></span>|<span data-ttu-id="55567-121">Zdefiniowane w root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="55567-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55567-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55567-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>
