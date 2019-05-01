---
title: Punkt końcowy
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 4562481e8b0b18c0ea0d9df0af3427ffe6419821
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963608"
---
# <a name="endpoint"></a>Punkt końcowy
Punkt końcowy  
  
## <a name="syntax"></a>Składnia  
  
```csharp
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
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator URI, który zawiera adres punktu końcowego.  
  
### <a name="addressheaders"></a>AddressHeaders  
 Typ danych: tablica ciągów  
  
 Typ dostępu: tylko do odczytu  
  
 Kolekcja nagłówków adresowych, dołączony do tego punktu końcowego.  
  
### <a name="addressidentity"></a>AddressIdentity  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Tożsamość punktu końcowego.  
  
### <a name="appdomainid"></a>AppDomainId  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator elementu appdomain punktu końcowego.  
  
### <a name="behaviors"></a>Zachowania  
 Typ danych: Zachowanie tablicy  
  
 Typ dostępu: tylko do odczytu  
  
 Kolekcja zachowań implementowanych przez ten punkt końcowy.  
  
### <a name="binding"></a>Wiązanie  
 Typ danych: Wiązanie  
  
 Typ dostępu: tylko do odczytu  
  
 Wiązanie używane przez ten punkt końcowy.  
  
### <a name="contractname"></a>ContractName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Ciąg, który określa, który kontrakt tego punktu końcowego jest uwidaczniany.  
  
### <a name="counterinstancename"></a>CounterInstanceName  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Nazwa wystąpienia liczników wydajności punktu końcowego.  
  
### <a name="listenuri"></a>ListenUri  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Identyfikator Uri punktu końcowego nasłuchuje.  
  
### <a name="name"></a>Nazwa  
 Typ danych: ciąg  
  
 Typ dostępu: tylko do odczytu  
  
 Unikatowa nazwa tego punktu końcowego.  
  
### <a name="processid"></a>Identyfikator procesu  
 Typ danych: sint32  
  
 Typ dostępu: tylko do odczytu  
  
 Proces identyfikator procesu, który jest hostem punktu końcowego.  
  
### <a name="ref"></a>ref  
 Typ danych: Kontrakt  
  
 Typ dostępu: tylko do odczytu  
  
 Kontrakt tego punktu końcowego jest uwidaczniany.  
  
## <a name="requirements"></a>Wymagania  
  
|MOF|Zadeklarowana w Servicemodel.mof.|  
|---------|-----------------------------------|  
|Przestrzeń nazw|Zdefiniowane w root\ServiceModel|
