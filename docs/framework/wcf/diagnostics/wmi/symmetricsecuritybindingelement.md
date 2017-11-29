---
title: SymmetricSecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b2e182b6-c041-4d80-a926-6058068d9f79
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ab341f55947bfcfbc776143e3bbc33e125da89c8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="symmetricsecuritybindingelement"></a>SymmetricSecurityBindingElement
SymmetricSecurityBindingElement  
  
## <a name="syntax"></a>Składnia  
  
```  
class SymmetricSecurityBindingElement : SecurityBindingElement  
{  
  string MessageProtectionOrder;  
  boolean RequireSignatureConfirmation;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa element SymmetricSecurityBindingElement nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa SymmetricSecurityBindingElement ma następujące właściwości:  
  
### <a name="messageprotectionorder"></a>messageProtectionOrder  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Kolejność szyfrowania i podpisywania dla tego powiązania komunikatu.  
  
### <a name="requiresignatureconfirmation"></a>requireSignatureConfirmation  
 Typ danych: wartość logiczna  
  
 Dostęp typu: tylko do odczytu  
  
 Określa, czy powiązanie wymaga potwierdzenia podpisu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
