---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a>Kontrakt
Kontrakt  
  
## <a name="syntax"></a>Składnia  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa kontraktu nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa kontraktu ma następujące właściwości:  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator domeny aplikacji obsługującej kontrakt.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Zachowania skojarzone z tym kontraktem.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa kontraktu w języku WSDL.  
  
### <a name="namespace"></a>Przestrzeń nazw  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Przestrzeń nazw `portType` elementu w języku WSDL.  
  
### <a name="operations"></a>Operacje  
 Typ danych: operacja tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Operacje tego kontraktu.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator procesu obsługującego kontrakt procesu.  
  
### <a name="ref"></a>ref  
 Typ danych: kontraktu  
  
 Dostęp typu: tylko do odczytu  
  
 Typ wywołania zwrotnego w przypadku kontraktu dupleksowego.  
  
### <a name="sessionmode"></a>SessionMode  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Wskazuje, czy kontrakt wymaga powiązanie skojarzone z tym kontraktem, aby używać sesji kanału.  
  
### <a name="type"></a>Typ  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Description.ContractDescription>
