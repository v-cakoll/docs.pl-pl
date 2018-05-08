---
title: Punkt końcowy
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="endpoint"></a>Punkt końcowy
Punkt końcowy  
  
## <a name="syntax"></a>Składnia  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a>Metody  
 Klasa punktu końcowego definiuje następującą metodę.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|Pobiera nazwę wystąpienia licznika wydajności operacji|  
  
## <a name="properties"></a>Właściwości  
 Klasa punkt końcowy ma następujące właściwości:  
  
### <a name="address"></a>Adres  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator URI zawierający adres punktu końcowego.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Typ danych: tablicy ciągów  
  
 Dostęp typu: tylko do odczytu  
  
 Kolekcja nagłówków adresu przyłączonych do tego punktu końcowego.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Tożsamość punktu końcowego.  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator domeny aplikacji obsługującej punkt końcowy.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: zachowanie tablicy  
  
 Dostęp typu: tylko do odczytu  
  
 Kolekcja zachowań implementowanych przez ten punkt końcowy.  
  
### <a name="binding"></a>Powiązanie  
 Typ danych: powiązanie  
  
 Dostęp typu: tylko do odczytu  
  
 Powiązanie używane przez ten punkt końcowy.  
  
### <a name="contractname"></a>ContractName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Ciąg określający, który kontrakt jest ujawniany ten punkt końcowy.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Nazwa wystąpienia liczników wydajności punktu końcowego.  
  
### <a name="listenuri"></a>Identyfikator ListenUri  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator Uri punktu końcowego nasłuchuje.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Dostęp typu: tylko do odczytu  
  
 Unikatowa nazwa tego punktu końcowego.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Dostęp typu: tylko do odczytu  
  
 Identyfikator procesu obsługującego punkt końcowy procesu.  
  
### <a name="ref"></a>ref  
 Typ danych: kontraktu  
  
 Dostęp typu: tylko do odczytu  
  
 Kontrakt ujawniany jest ten punkt końcowy.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowany w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowany w root\ServiceModel|
