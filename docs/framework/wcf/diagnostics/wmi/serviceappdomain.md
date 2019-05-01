---
title: ServiceAppDomain
ms.date: 03/30/2017
ms.assetid: f28e5186-a66d-46c1-abe9-b50e07f8cb4f
ms.openlocfilehash: 05be495dbfe87e7dd14b0cfbb38b30c6f8278e6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61957076"
---
# <a name="serviceappdomain"></a>ServiceAppDomain
Mapuje domenę aplikacji usługi.  
  
## <a name="syntax"></a>Składnia  
  
```csharp
class ServiceAppDomain  
{  
  Service ref;  
  AppDomainInfo ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa ServiceAppDomain nie definiuje żadnych metod.  
  
## <a name="properties"></a>Właściwości  
 Klasa ServiceAppDomain ma następujące właściwości:  
  
### <a name="ref"></a>ref  
 Typ danych: Usługa  
Kwalifikatory: Key  
  
 Typ dostępu: tylko do odczytu  
  
 Usługa ta domena aplikacji.  
  
### <a name="ref"></a>ref  
 Typ danych: AppDomainInfo  
Kwalifikatory: Key  
  
 Typ dostępu: tylko do odczytu  
  
 Zawiera właściwości domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
